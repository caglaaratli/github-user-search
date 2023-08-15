<template>
    <div class="user-container">
        <!-- <img :src="githubUser.avatar_url" alt="GitHub User Profile" /> -->
    
        <!-- <p>{{ githubUser.public_repos }}</p>
        <p>{{ githubUser.bio }}</p>
        <p>{{ githubUser.created_at }}</p>
        <p>{{ githubUser.followers }}</p>
        <p>{{ githubUser.following }}</p>
        <p>{{ githubUser.login }}</p>
        <p>{{ githubUser.name }}</p>
        <p>{{ githubUser.html_url }}</p>
        <p>{{ githubUser.location }}</p>
        <p>{{ githubUser.twitter_username }}</p>
        <p>{{ githubUser.company }}</p> -->
        <div class="githubHead">
            <div class="mainImg">
                <div class="githubInfo">
                    <div class="githubUserInfo">Github User Name:</div>
                    <div class="githubUserName"><a href="">@githubusername</a></div>
                    <div class="githubJoinedDate">Joined Date</div>
                </div>
            </div>
        </div>

        <div class="githubFact">
            <div class="githubBio">github bio ..</div>

            <div class="githubRepo">
                <div class="repos">
                    <div class="repoHeading">Repos</div>
                    <div class="repoTotal">0</div>
                </div>

                <div class="followers">
                    <div class="followereading">Followers</div>
                    <div class="followerTotal">0</div>
                </div>

                <div class="following">
                    <div class="followingHeading">following</div>
                    <div class="followingTotal">0</div>
                </div>
            </div>

            <div class="githubSocial">
                <div class="location">
                    <img src="@/assets/icon-location.svg">
                    <p class="locations">Location</p>
                </div>
                <div class="twitter">
                    <img src="@/assets/icon-twitter.svg">
                    <p class="twit">Twitter</p>
                </div>
                <div class="website">
                    <img src="@/assets/icon-website.svg"> 
                    <p class="websites">Website</p>
                </div>
                <div class="company">
                    <img src="@/assets/icon-company.svg">
                    <p class="companies">Company</p>
                </div>
            </div>

        </div>

    </div>

</template>

<script>
export default{
    props : {
        githubUser : {
           type: Object,
           required: true,  
        },
    
    }, 
}

</script>
