<template>
  <div id="app">
    <ProgressBar
      :progressOffset="100"
      :progressColor="['pink', 'skyblue']"
      @changeOut="fn"
      round
      :progressWidth="1500"
      :progressHeight="50"
    />
    <br />
    <ProgressBar
      progressOffset="60"
      :progressColor="['yellow', '#000']"
      @changeOut="fn"
      :progressWidth="700"
      :progressHeight="50"
    />
    <br />
    <ProgressBar
      progressOffset="11"
      :progressColor="['#456be8', '#15ac68']"
      @changeOut="fn"
      round
    />
  </div>
</template>

<script>
import ProgressBar from "@/components/ProgressBar.vue";
export default {
  name: "App",
  data() {
    return {};
  },

  created() {},

  methods: {
    fn() {
      console.log("进度条满了");
    },
  },

  computed: {},

  components: {
    ProgressBar,
  },
};
</script>

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column;
  width: 100%;
  height: 100vh;
}
</style>
