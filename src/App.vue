<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="곱셉 계산기를 만들어 공부하기"/>
    <div>
      <p>문제를 맞춰주세요 !</p>
      <p>{{first}} X {{second}} 는 ?</p>
      <form v-on:submit="onSubmitForm">
        <input type="number" v-model="value">
        <button>확인</button>
      </form>
      <p>{{result}}</p>
      <p>문제를 맞춘 횟수 : {{correct}}</p>
      <p>문제를 틀린 횟수 : {{wrong}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      first: Math.ceil(Math.random() * 9),
      second: Math.ceil(Math.random() * 9),
      result: '',
      value: '',
      correct: 0,
      wrong: 0
    }
  },
  methods : {
    onSubmitForm(e) {
      e.preventDefault();
      if(this.first * this.second === parseInt(this.value))
      {
        this.result = '정답 ! 다음문제로 넘어갑니다 !';
        this.first = Math.ceil(Math.random() * 9);
        this.second = Math.ceil(Math.random() * 9);
        this.value = ''
        this.correct++;
      } else {
        this.result = '문제가 틀렸어요. 다시한번 생각해보세요 !';
        this.wrong++;
        this.value = ''
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
