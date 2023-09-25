<template>
  <div>
    <p>Your reaction time: {{ score }} ms</p>
    <p>
      Rank: <strong class="rank"> {{ rank }}</strong>
    </p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 150) {
      this.rank = "Radiant";
    } else if (this.score >= 150 && this.score < 250) {
      this.rank = "Immortal";
    } else if (this.score >= 250 && this.score < 350) {
      this.rank = "Diamond";
    } else {
      this.rank = "Iron";
    }
  },
};
</script>

<style scoped>
.rank {
  font-weight: 800;
  color: crimson;
}
</style>
