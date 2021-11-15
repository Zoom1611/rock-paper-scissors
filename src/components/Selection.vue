<template>
    <div class="container">
        <div class="rock" @click="selection('rock')">
            <img src="../assets/rock.png" alt="rock"/>
        </div>
        <div class="paper" @click="selection('paper')">
            <img src="../assets/paper.png" alt="paper">
        </div>
        <div class="scissors" @click="selection('scissors')">
            <img src="../assets/scissors.png" alt="scissors">
        </div>
    </div>
    <button @click="resetResult">Reset result</button>
</template>

<script>

export default {
    data() {
        return {
            listItems: [ 'rock', 'paper', 'scissors' ],
            myChoice: null,
            compChoice: null,
            resultUser: 0,
            resultComp: 0,
            results: { resultUser: null, resultComp: null },
            showWinMessage: false,
            isDraw: false,
            messageObj: { showWinMessage: null, isDraw: null }
        }
    },
    methods: {
        compSelection() {
            this.compChoice = this.listItems[this.listItems.length * Math.random() | 0]
        }, 
        resetResult() {
            this.results.resultUser = 0
            this.results.resultComp = 0
            this.resultUser = 0
            this.resultComp = 0
        },
        selection(choice) {
            this.myChoice = choice
            this.compSelection()
            this.checking(this.myChoice, this.compChoice)
            
            this.results.resultUser = this.resultUser
            this.results.resultComp = this.resultComp
            this.$emit('currentResult', this.results)
        	
            this.messageObj.showWinMessage = this.showWinMessage
            this.messageObj.isDraw = this.isDraw
            this.$emit('message', this.messageObj)

            this.isDraw = false
        },
        checking(myChoice, compChoice) {
            if (myChoice === 'rock' && compChoice === 'paper') {
                this.resultComp++
                this.showWinMessage = false
            } else if (myChoice === 'rock' && compChoice === 'scissors') {
                this.resultUser++
                this.showWinMessage = true
            } else if (myChoice === 'paper' && compChoice === 'rock') {
                this.resultUser++
                this.showWinMessage = true
            } else if (myChoice === 'paper' && compChoice === 'scissors') {
                this.resultComp++
                this.showWinMessage = false
            } else if (myChoice === 'scissors' && compChoice === 'rock') {
                this.resultComp++
                this.showWinMessage = false
            } else if (myChoice === 'scissors' && compChoice === 'paper') {
                this.resultUser++
                this.showWinMessage = true
            } else {
                this.isDraw = true
            }
        }
    }
}
</script>

<style>
img[alt="rock"] {
    width: 100px;
    height: 100px;
    margin: 20px 10px;
}
img[alt="paper"] {
    width: 100px;
    height: 100px;
    margin: 20px 10px;
}
img[alt="scissors"] {
    width: 100px;
    height: 100px;
    margin: 20px 10px;
}
.rock {
    border: 1px solid white;
    margin: 10px 10px;
    border-radius: 50%;
    cursor: pointer;
    height: 140px;
}
.paper {
    border: 1px solid white;
    margin: 10px 10px;
    border-radius: 50%;
    cursor: pointer;
    height: 140px;
}
.scissors {
    border: 1px solid white;
    margin: 10px 10px;
    border-radius: 50%;
    cursor: pointer;
    height: 140px;
}
.rock:hover {
    background: gray;
}
.scissors:hover {
    background: gray;
}
.paper:hover {
    background: gray;
}
.container {
    display: flex;
    flex-flow: column wrap;
    flex-flow: row nowrap;
    justify-content: center;
    align-items: flex-start;
}
button {
    margin: auto;
    border-radius: 8px;
    border: none;
    width: 100px;
    padding: 10px;
    background: black;
    color: white;
    font-weight: bold;
    cursor: pointer;
}
</style>