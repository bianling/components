<template>
  <div
    class="progress"
    :style="{
      width: progressWidth + 'px',
      height: progressHeight + 'px',
      background: progressColor[0],
      borderRadius: borderRound + 'px',
    }"
    ref="progress"
  >
    <span>{{ progressSonWidth + "%" }}</span>
    <div
      ref="progressSon"
      :style="{
        width: progressSonWidth + '%',
        borderRadius: borderRound + 'px',
        background: progressColor[1],
      }"
    ></div>
  </div>
</template>

<script>
export default {
  name: "ProgressBar",
  data() {
    return {
      progressSonWidth: 0,
      borderRound: "",
    };
  },

  props: {
    progressOffset: {
      type: [Number, String],
      request: true,
    },
    progressColor: {
      type: Array,
      default: ["pink", "skyblue"],
    },
    round: {
      type: String,
    },
    progressWidth: {
      type: [Number, String],
    },
    progressHeight: {
      type: [Number, String],
    },
  },

  created() {
    if (this.round === "") {
      this.$nextTick(() => {
        const w = this.$refs.progress.clientWidth;
        const h = this.$refs.progress.clientHeight;
        if (w > h) {
          this.borderRound = h / 2;
        } else {
          this.borderRound = w / 2;
        }
      });
    }
  },

  mounted() {
    this.progressAdd(this.progressOffset);
  },

  methods: {
    progressAdd(percentage) {
      if (this.progressSonWidth === 100) {
        this.$emit("changeOut");
      }
      setTimeout(() => {
        if (this.progressSonWidth >= percentage) return;
        this.progressSonWidth = this.progressSonWidth + 1;
        this.progressAdd(percentage);
      }, 40);
    },
  },
};
</script>

<style scoped>
.progress {
  position: relative;
  width: 600px;
  height: 30px;
  background-color: pink;
}
.progress div {
  height: 100%;
  background-color: skyblue;
}
.progress span {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%);
  transform: translateY(-50%);
}
</style>
