<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6  col-md-offset-3">
        <h1>The Super Quize</h1>
        <hr>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6  col-md-offset-3">
        <transition name="flip" mode="out-in">
          <component :is="mode" @answered = "answered($event)" @confirmed=" mode = 'app-question'"></component>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Question from './components/Question.vue';
import Answer from './components/Answer.vue';
export default {
  data(){
    return{
      mode:'app-question'
    }
  },
  methods:{
    answered(isCorrect){
      if(isCorrect){
        this.mode = 'app-answer';
      }else{
        this.mode = 'app-question';
        alert('Wrong answer, try Again !');
      }
    }
  },
  components:{
    appQuestion: Question,
    appAnswer: Answer
  }
  
}
</script>

<style lang="scss">
  h1{
    padding-top: 50px;
    text-align: center;
    color:burlywood;
  }
  .flip-enter{

  }
  .flip-enter-active{
    animation: flip-in 0.5s ease-out forwards;
  }
  .flip-leave{

  }
  .flip-leave-active{
    animation: flip-out 0.5s ease-out forwards;
  }
  @keyframes flip-out {
    from{
      transform: rotateY(0deg);
    }
    to{
      transform: rotateY(90deg);
    }
  }
  @keyframes flip-in {
    from{
      transform: rotateY(90deg);
    }
    to{
      transform: rotateY(0deg);
    }
  }
</style>
