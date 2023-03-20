<template>
  <div class="home">
    <!-- <div class="graph">
      <h1>체중 그래프</h1>
      <WeightGraph />
    </div> -->
    <div class="graph">
      <h1>체중 그래프</h1>
      <Weight1Graph />
    </div>
    <div class="graph">
      <h1>걸음수 그래프</h1>
      <WalkGraph />
    </div>
    <div class="graph">
      <h1>활동에너지 그래프</h1>
      <EngeryGraph />
    </div>
    <div class="graph">
      <h1>심박수 그래프</h1>
      <HeartGraph />
    </div>
    <div class="graph">
      <h1>스트레스 그래프</h1>
      <StressGraph />
    </div>
    <div class="graph">
      <h1>수면 그래프</h1>
      <SleepGraph />
    </div>
  </div>
</template>

<script>
// import WeightGraph from "@/components/WeightGraph.vue";
import WalkGraph from "@/components/WalkGraph.vue";
import EngeryGraph from "@/components/EngeryGraph.vue";
import HeartGraph from "@/components/HeartGraph.vue";
import StressGraph from "@/components/StressGraph.vue";
import Weight1Graph from "@/components/Weight1Graph.vue";
import SleepGraph from "@/components/SleepGraph.vue";

export default {
  name: "HomeView",
  components: {
    // WeightGraph,
    WalkGraph,
    EngeryGraph,
    HeartGraph,
    StressGraph,
    Weight1Graph,
    SleepGraph,
  },
};
</script>

<style scoped>
.graph {
  margin-top: 5rem;
}
</style>
