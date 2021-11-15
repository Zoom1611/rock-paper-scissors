<template>
    <div class="win-lose-text">
        <h1>{{ message }}</h1>
    </div>
    <div>
        
    </div>
</template>

<script>
export default {
    props: ['messageBooleanObj'],
    data() {
        return {
            message: 'Give it a try!',
        }
    },
    watch: {
        messageBooleanObj: {
            deep: true,
            handler (val) {
                if (val.isDraw === true) {
                    this.message = 'Draw'
                } else if (val.showWinMessage === true && val.isDraw === false) {
                    this.message = 'You Win!'
                } else {
                    this.message = 'You Lose!'
                }
            }
        }
    },

}
</script>

<style>
.win-lose-text h1 {
    color: white;
    margin: 20px;
}
</style>