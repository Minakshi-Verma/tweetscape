<template>
<h1 class="tweet-title">Tweetscape</h1>
<div id="app">
    <UserProfile />
</div>   
</template>

<script>
// import the component
import UserProfile from './components/UserProfile'

export default {
    //name of the component
    name: 'App',
    //list of imported components
    components:{
        UserProfile
    } 
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;    
    color: #2c3e50;
    min-height:100vh;background-color:#F3F5FA;    
}
.tweet-title{
font-size: 40px;
background: rebeccapurple;
text-align: center;
color: white;
margin-top:1%;
padding:0.7% 0;
}
</style>
