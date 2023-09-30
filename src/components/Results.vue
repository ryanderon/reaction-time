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
  data() {
    return {
      rank: null,
    };
  },
  props: ["score"],
  mounted() {
    if (this.score > 350) {
      this.rank = "Iron";
    } else if (this.score >= 250 && this.score < 350) {
      this.rank = "Diamond";
    } else if (this.score >= 150 && this.score < 250) {
      this.rank = "Immortal";
    } else {
      this.rank = "Radiant";
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
