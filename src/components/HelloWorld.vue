<template>
  <div class="title">VUE Example</div>
  <div class="desc">trigger block:</div>
  <div class="pos-test">
    <z-robot-calibration
      mode="text"
      trigger="block"
      :customStyle="customStyleObj.style"
      @onClick="clickHandler"
      @success="validSuccess"
    ></z-robot-calibration>
  </div>

  <div class="api-test" @click="styleChange">styleChange</div>

  <div class="desc">trigger passive:</div>
  <div class="login" @click="loginClick">Login</div>
  <z-robot-calibration
    mode="text"
    trigger="passive"
    .open="open"
  ></z-robot-calibration>
</template>
<script setup>
import "../../../checkVerificationWeb/src/components/index";
// import "../test/bundle";
import { ref, reactive } from "vue";

const customStyleObj = reactive({
  style: {
    border: "1px solid #a1a1a1;",
    backgroundColor: "#ECF5FF",
  },
});

let styleFlag = false;

const styleChange = () => {
  styleFlag = !styleFlag;
  if (styleFlag) {
    customStyleObj.style = {
      border: "3px solid #ff0000",
      backgroundColor: "#333",
    };
  } else {
    customStyleObj.style = {
      border: "1px solid #a1a1a1",
      "background-color": "#ECF5FF",
    };
  }
};

const clickHandler = (val) => {
  console.log(val);
};

const validSuccess = (val) => {
  console.log(val);
};

const open = ref(false);
const loginClick = () => {
  open.value = true;
};
</script>
<style scoped>
.title {
  font-weight: bold;
  font-size: 20px;
  margin: 30px;
  text-align: center;
}
.desc {
  margin: 20px 0;
}
.pos-test {
  padding: 40px 60px 50px 60px;
}
.api-test {
  display: inline-block;
  border: 1px solid #333;
  margin: 10px 0;
  padding: 8px 30px;
  cursor: pointer;
}
.login {
  width: 100px;
  cursor: pointer;
  margin: 30px auto;
  padding: 10px 20px;
  background-color: blueviolet;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
