<template>
  <div class="container">
    <h1>AutoAttack</h1>
    <span>quick suggestion for your comperssor's attack and release time</span>
    <div class="workSpace">
      <span class="type"
        >Type Your BPM</span
      >
      <el-input
      v-model="inputBpm"
      class="input"
      size="large"
      placeholder="Please Input Your BPM"
      maxlength="3"
      width="100px"
    />
     <el-button type="primary" class="btn" @click="GetSuggestion">Get Suggestion</el-button>
    </div>
    <div class="result" v-show="flag">
      <span class="re">AttackTime:</span> {{attack}}ms<br/>  
      <span class="re">ReleaseTime:</span> {{release}}ms<br/>  
    </div>
    <footer class="copyright">
      <span class="copy">Copyright © 2021-2023</span>&nbsp; 
      <span class="copy">AutoAttack</span>
    </footer>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
const inputBpm = ref('')
var flag = ref(false)
var attack = ref(0)
var release= ref(0)
const GetSuggestion = () => {
  var bpm : number = parseInt(inputBpm.value)
  attack.value = 60000 / (bpm * 8)
  release.value = 60000 / (bpm * 2)
  if (bpm === 0){
    flag.value = false
  }
  flag.value = true
}
</script>

<style scoped>
.container{
  text-align: center;
  margin-top: 100px;
}
h1{
  font-size: 60px;
  color:#ced4da;
}
span{
  font-size: 20px;
  color:#868e96;
}
.workSpace{
  margin: 60px auto;
  width: 500px;
  height: 200px;
  border: 1px solid #ced4da;
  border-radius: 5px;
}
.input{
  display: inline-block;
  width: 100%;
  margin: 10px;
}
.type{
  display:inline-block;
  margin: 20px;
}
.btn{
  margin: 20px;
  border-radius: 5px;
}
.result{
  justify-content: left;
  margin-bottom: 50px;
}
.copy{
  font-size: 10px;
  color:#868e96;
}
/* 放在页面正中下端 */
.copyright{
  position: fixed;
  bottom: 100px;
  left: 0;
  width: 100%;
  text-align: center;
}
.re{
  margin-left: 20px;
  color:#eee;
}
</style>