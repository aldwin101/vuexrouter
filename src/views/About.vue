<template>
  <div id='choices'>
    <p>{{result}}</p>
    <img @click="select('rock')" src="@/assets/rock.png" alt="rock_hand">
    <img @click="select('paper')" src="@/assets/scissor.png" alt="scissor_hand">
    <img @click="select('scissors')" src="@/assets/paper.png" alt="paper_hand">
  </div>

</template>

<script>
  export default {
    name: 'Game',
    data: function () {
    return {
      userScore: 0,
      compScore: 0,
    }
  },
  props: {
    result: String
  },
  methods: {
    select(choice){
      this.userSelected = choice;
      let options = ['rock', 'paper', 'scissors'];
      this.compSelected = options[Math.floor(Math.random() * options.length)];
      this.gameResult();
    },

    
    gameResult() {
      if (this.userSelected == 'rock') {
        if (this.compSelected == 'paper') {
          this.result = 'You lose';
        } else if (this.compSelected == 'scissors') {
          this.result = 'You win';
        } else {
          this.result = 'Draw';
        }
      } else if (this.userSelected == 'paper') {
        if (this.compSelected == 'rock') {
          this.result = 'You win';
        } else if (this.compSelected == 'scissors') {
          this.result = 'You lose';
        } else {
          this.result = 'Draw';
        }
      } else {
        if (this.compSelected == 'rock') {
          this.result = 'You lose';
        } else if (this.compSelected == 'paper') {
          this.result = 'You win';
        } else {
          this.result = 'Draw';
        }
      }
    }
  },
};
</script>

<style scoped>
#choices {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  width: 30vw;
}

img {
  box-sizing: border-box;
  width: 50px;
}
</style>