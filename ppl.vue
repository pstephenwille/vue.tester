<template id="pplTemplate">
    <div id="pplWrapper">
        <h2 v-on:click="changeName">my name is {{name}}</h2>
    </div>
</template>
<div id="yyy"></div>
<script type="text/javascript">
    new Vue({
        el:'#yyy',
        template:'#pplTemplate',
        data:{
            name:'ppl name'
        },
        beforeCreate:function(){
            window.eventBus = window.eventBus || new Vue({});
        },
        created:function(){
            console.log('....ppl created');
        },
        methods:{
        	changeName:function(){
        	    eventBus.$emit('nameChanged', {name:'XXXX name'});
        	}
        }
    });
</script>

<style scoped>
    h2{
        color: #008000;
    }
</style>

