<script setup>
import { ref, onMounted } from "vue";
let adviceNum = ref(null)
let advice = ref(null)

onMounted(() => {
  getAdvice()
})

const getAdvice = () => {
  fetch('https://api.adviceslip.com/advice')
  .then((res) => res.json())
  .then((json) => (adviceNum.value = json.slip.id, advice.value = json.slip.advice))
  .catch((err) => (error.value = err))
  
}
console.log(adviceNum)

</script>

<template>
 <body class="flex justify-center h-[100vh] ">
  <div class="card p-[30px]  rounded-[30px] text-center relative w-[360px] sm:w-[400px] ">

  
  <div class="advice pb-[20px] text-[14px] pt-3 font-bold"><span id="advice">Advice: {{adviceNum}}</span></div>
  <div class="advicetest text-[18px] mb-[20px] w-[350px] font-bold mx-auto py-3" id="advicetest">
    {{ advice }}
  </div>
  <div class="devider pb-5">
   

          <img
            class="w-[95%]"
            src="../images/pattern-divider-desktop.svg" 
            alt=""
          />
   
  </div>
  <button @click="getAdvice()" class="btn cursor-pointer absolute left-[50%] bottom-[-31px] ">
    <img  src="../images/icon-dice.svg" alt="">
  </button>
</div>
 </body>

</template>

<style scoped>
*{
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}
body{
  align-items: center;
  background-color: hsl(218, 23%, 16%);
}
.card{
  background-color: hsl(217, 19%, 24%);
  align-items:center;
}
.advice{
  transform: uppercase;
  letter-spacing: 1px;
  color: hsl(150, 100%, 66%);

}
.devider img{
  width: 90%;
  margin: 0px auto;
}
.advicetest{
  color: hsl(193, 38%, 86%);
  letter-spacing: 1px;
}
.btn{
  transform: translateX(-50%);
  padding: 15px 17px;
  border: none;
  background-color: hsl(150, 100%, 66%);
  border-radius: 50px;
  
}
</style>