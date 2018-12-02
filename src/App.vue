<template>
  <div id="app">
    <div>
      <button v-show="switchState" @click.prevent="switchState=false;txt=''">time-slicing:处于开启状态</button>
      <button v-show="!switchState" @click.prevent="switchState=true;txt=''">time-slicing:处于关闭状态</button>
    </div>
    <input type="text" v-model="txt">
    <div v-if="switchState">
      <div v-for="(item,index) in 600" :key="index">
        <timeslicing-on :text="txt"></timeslicing-on>
      </div>
    </div>
    <div v-if="!switchState">
      <div v-for="(item,index) in 600" :key="index">
        <timeslicing-off :text="txt"></timeslicing-off>
      </div>
    </div>
  </div>
</template>

<script>
import TimeslicingOn from "./components/timeslicingOn";
import TimeslicingOff from "./components/timeslicingOff";

export default {
  name: "app",
  components: {
    TimeslicingOn,
    TimeslicingOff
  },
  data() {
    return {
      txt: "",
      switchState: false
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
