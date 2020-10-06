<template>
    <div class="user-profile">
        <div class="user-profile_user-panel">
            <h1 class="user-profile_username">@{{user.username}}</h1>
            <div class="user-profile_admin-badge" v-if="user.isAdmin">Admin</div>
            <div class="user-profile_follower-count">
                <strong>Follower</strong>:{{followers}}
            </div>            
        </div>
        <div class="user-profile_tweets-wrapper">
            <TweetItem v-for="tweet in user.tweets" :key="tweet.id" :username="user.username" :tweet="tweet"/>
            <!-- <div class='user-profile_tweet' v-for="tweet in user.tweets" :key="tweet.id">
                {{tweet.content}} -->
            <!-- </div> -->
        </div>
    </div>

</template>



<script>

import TweetItem from "./TweetItem"

export default {
    //name of the component
    name: 'UserProfile',
    components:{TweetItem},

    //data is always going to a fx and would return the data object 
    data() {
        return {
            followers: 0,
            user: {
                id: 1,
                username: 'mini5',
                firstName: "Mini",
                lastName: "Verma",
                email: "m@gmail.com",
                isAdmin: true,
                tweets:[
                    {id:1, content:"Tweet clone is amazing!"},
                    {id:2, content:"Vue is awesome!"},
                ]
            }
        }
    },
    //watches a datapoint and when it changes you can run a fx
    watch:{
        //use same name as datapoint that you want to watch
        // so when follower(data) will change, it will do some stuff
        followers(newFollowerCount, oldCountCount){
            if(oldCountCount< newFollowerCount){
                console.log(`${this.user.username} gained a follower`)
            }
        }

    },
    //properties that are computed using existing datapoints( this could be a fx)
    computed: {
        fullName(){
            return `${this.user.firstName} ${this.user.lastName} `
        }        
    },
    //add methods here
    // addFollower mathod will add a follower to the existing follower
    //On refresh count goes back to initial follower count= 0
    methods:{
         addFollower(){
           return this.followers++
        }
    },
    //life cycle hooks; fx built in vue interface that runs during different stages of component lifecycle
    // It can be created, mounted, destroyed
    // you will notice follower count does go back to "0" after refresh
    // We see the count as "1" after reload, since mount() runs the moment page refreshes and adds the follower
    // The process is so quick that we donot see the step of updating follower
    // API data fetching is also done here
    mounted(){
        this.addFollower()
    }
}
</script>

<style>
.user-profile{
    display:grid;
    grid-template-columns:1fr 3fr;
    width:100%;
    padding:50px 5%;
}
.user-profile_user-panel{
    display:flex;
    flex-direction:column;    
    margin-right: 50px;
    padding:20px;
    background-color: white;
    border-radius: 5px;
    border:1px solid #DFE3E8;
}

.user-profile_admin-badge{
    background:rebeccapurple;
    color:white;
    border-radius:5px;
    margin-right: auto ;
    padding:0 10px;
    font-weight: bold;    
}
h1{
    margin:0;
}
.user-profile_tweet-wrapper{
    display:grid;
    grid-gap:10px;
}
</style>

