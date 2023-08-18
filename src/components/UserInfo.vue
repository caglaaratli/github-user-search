<template>
    <div class="user-container" :class="darkMode ? 'dark' : 'light'">
         <div class="githubHead"  >
            <div class="mainImg" :class="darkMode ? 'dark' : 'light'" ><img :src="githubUser.avatar_url" alt="GitHub User Profile" /></div>
            <div class="githubInfo">
                <div class="githubUserInfo" :class="darkMode ? 'dark' : 'light'" >{{githubUser.name}}</div>
                <div class="githubUserName" :class="darkMode ? 'dark' : 'light'"><a :href="githubUser.html_url" target="blank_">@{{ githubUser.login}}</a></div>
                <div class="githubJoinedDate" :class="darkMode ? 'dark' : 'light'">Joined {{ githubUser.created_at.slice(0,githubUser.created_at.length-10) }}</div>
             </div>
            
        </div>

        <div class="githubFact" >
             <div class="githubBio" :class="darkMode ? 'dark' : 'light'">{{ githubUser.bio === '' || githubUser.bio=== null ? "This profile has no bio" : githubUser.bio}}</div> 
            <!-- <div class="githubBio">
s                <div v-else>{{ githubUser.bio }}</div>
            </div> -->

            <div class="githubRepo" :class="darkMode ? 'dark' : 'light'" >
                <div class="repos" >
                    <div class="repoHeading" :class="darkMode ? 'dark' : 'light'" >Repos</div>
                    <div class="repoTotal" :class="darkMode ? 'dark' : 'light'" >{{githubUser.public_repos}}</div>
                </div>

                <div class="followers" >
                    <div class="followerHeading" :class="darkMode ? 'dark' : 'light'" >Followers</div>
                    <div class="followerTotal" :class="darkMode ? 'dark' : 'light'" >{{githubUser.followers}}</div>
                </div>

                <div class="following"  >
                    <div class="followingHeading"  :class="darkMode ? 'dark' : 'light'">Following</div>
                    <div class="followingTotal"  :class="darkMode ? 'dark' : 'light'" >{{githubUser.following}}</div>
                </div>
            </div>

            <div class="githubSocial"  :class="darkMode ? 'dark' : 'light'">
                <div class="location" >
                    <img src="@/assets/icon-location.svg">
                    <p class="locations">{{ githubUser.location === '' || githubUser.location=== null ? "No location" : githubUser.location}}</p>
                </div>
                <div class="twitter" >
                    <img src="@/assets/icon-twitter.svg">
                    <p class="twit">{{ githubUser.twitter_username=== '' || githubUser.twitter_username=== null ? "No twitter username" : githubUser.twitter_username}}</p>
                </div>
                <div class="website" >
                    <img src="@/assets/icon-website.svg"> 
                    <p class="websites">{{ githubUser.blog === '' || githubUser.blog=== null ? "No website url" : githubUser.blog}}</p>
                </div>
                <div class="company">
                    <img src="@/assets/icon-company.svg">
                    <p class="companies">{{ githubUser.company === '' || githubUser.company=== null ? "No company info" : githubUser.company}}</p>
                </div>
            </div>

        </div> 

    </div> 

</template>

<script>

export default{
    props : {
        darkMode: {
            types:Boolean,
            required:true, 
        },
        
        githubUser : {
           type: Object,
           required: true,  
        },
    
    }, 

}

</script>

<style>
.user-container{
  width:730px;
   height:419px;
  border-radius:15px;
  margin-top:20px; 
  display:flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--search-bg-color);
 

}


.user-container .mainImg{
    width:117px;
    height:117px;
    border:1px solid var(--black); /*white */
    border-radius:117px;
    object-fit: contain;
}
.user-container .mainImg img{
    object-fit: contain;
    width:117px;
    height:117px;
    border-radius:117px;
}

.githubHead{
    display:flex;
    align-items: center;
    justify-content: space-between;
    width:650px;
    margin-top:30px;

}

.githubInfo{
    height:100%;
    width:480px;
    position:relative;

}

.githubUserInfo{
    font-size:23px;
    font-weight: bold;
    color:var(--search-color);
}

.githubJoinedDate{
    position:absolute;
    top:7px;
    right:0;
    font-size:15px;
    color:var(--search-color);
}
.githubUserName{
    color:#0079ff;
    margin-top:5px;
}

.githubUserName a{
    font-size:16px;
    color:#0079ff;
    text-decoration:none;
}

.githubFact{
    width:650px;
    display:flex;
    flex-direction: column;
    align-items: flex-end;
}

.githubBio{
    width:480px;
    height:25px;
    color:var(--search-color);
    margin-top:-30px;
    margin-bottom:30px;

}

.githubRepo{
    display: flex;
    align-items: center;
    justify-content: space-around;
    background-color: var(--body-bg-color);
    height:85px;
    width:480px;
    border-radius: 10px;
}

.repoHeading ,
.followerHeading,
.followingHeading{
    font-size:13px;
    color:var(--black); /* white */
}

.repoTotal ,
.followerTotal,
.followingTotal{
    font-size:22px;
    color:var(--search-color);
    font-weight: bold;
}

.githubSocial{
    display: grid;
    grid-template-columns: 240px 240px;
    row-gap:1.2em;
    color:var(--black);
    margin-top:30px;
}

.location,
.website,
.twitter,
.company {
    display:flex;
    align-items: center;
    font-size: 15px;
}

.location img,
.website img,
.twitter img,
.company img {
   margin-right:10px;
}

@media screen and (max-width:769px){
.user-container{
    width:573px;
    height:481px;
}
.githubHead,
.githubRepo,
.githubSocial{
    width:493px;
}

.githubInfo{
    width:350px;

}

.githubJoinedDate{
    top:70px;
    left:0;
}


.githubFact{
    width:493px;
    align-items: flex-start;
    margin-top:25px;
}

}

@media screen and (max-width:415px){
.user-container{
    width:327px;

}
.githubHead,
.githubFact{
    width:279px;
}
.user-container .mainImg{
    width:60px;
    height:60px;
}
.user-container .mainImg img{
    width:60px;
    height:60px;
}

.githubInfo{
    width:200px;

}
.githubUserInfo{
    font-size:18px;
}
.githubUserName{
    margin-top:-5px;
}
.githubJoinedDate{
    top:48px;
    
}

.githubUserName a ,
.githubJoinedDate,
.githubBio{
    margin-top:25px;
}

.githubRepo{
    width:279px;
}

.githubSocial{
    grid-template-columns: 279px;
}

.repoTotal,
.followerTotal,
.followingTotal{
    text-align: center;
}

} 



</style>
