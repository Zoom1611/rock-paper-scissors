<template>
    <div class="result">
        <h1 class="result-text">
            <span class="result-user">{{ initialScoreUser || 0 }}</span>
            <span>:</span>
            <span class="result-comp">{{ initialScoreComp || 0}}</span>
        </h1>
    <div class="user">
        <span class="user-text">user</span>
    </div>
        <div class="comp">
            <span class="comp-text">comp</span>
        </div>
    </div>
</template>

<script>
export default {
    props:['currentScore'],
    data() {
        return {
        }
    },
    computed: {
        initialScoreUser: function() {
            return this.currentScore.resultUser
        },
        initialScoreComp: function() {
            return this.currentScore.resultComp
        }
    }
}
</script>

<style>
.result {
    border: 4px solid white;
    border-radius: 8px;
    width: 250px;
    margin: 20px auto;
}
span {
    color: white;
    font-weight: bold;
    position: relative;
}
.user {
    position: absolute;
    background: rgb(112, 112, 245);
    width: 70px;
    margin-top: -49px;
    margin-left: -37px;
    border-radius: 4px;
}
.comp {
    position: absolute;
    background: rgb(54, 197, 54);
    width: 70px;
    margin-left: 217px;
    margin-top: -49px;
    border-radius: 4px;
}

</style>