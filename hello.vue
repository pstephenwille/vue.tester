<template id="helloTemplate">
    <div id="helloWrapper">
        <h2>hello</h2>
        <h1>world {{woot}}</h1>

        <div id="ppl"></div>
    </div>
</template>
<div id="xxx"></div>
<script type="text/javascript">
    var hello = new Vue({
        el:'#xxx',
        template:'#helloTemplate',
        data:{
            woot:'my woot text'
        },
	    beforeCreate:function(){
		    window.eventBus = window.eventBus || new Vue({data:{name:'event bus'}});
		    eventBus.$on('nameChanged', function(evt){
		        console.log('...hello namechanged evt: ', evt.name );
		        hello.woot = evt.name;
		    });
	    },
        methods:{
	        handleNameChange:function(name){
			        this.woot = 'name changed to '+ name.name;
		        }
        },
        created:function getPpl(){
	        $.get({
		        url:'ppl.vue',
		        dataType:'html',
		        success:function(data){
			        $('#ppl').append(data);
		        }
	        });
        }
    });
</script>

<style scoped>
    h2{
        color:#666;
    }
    h1{
        color:#f00;
    }
</style>
