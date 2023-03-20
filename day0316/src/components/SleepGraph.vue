<template>
  <div id="sleepGraph">
    <div id="chart">
      <apexchart
        type="rangeBar"
        height="350"
        :options="chartOptions"
        :series="series"
      ></apexchart>
    </div>
  </div>
</template>
  
<script>
import VueApexCharts from "vue-apexcharts";
const sleep_data = [
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["6:39:0", "6:43:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "얕은수면",
    time_duration: ["6:37:0", "6:39:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["6:31:0", "6:37:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["6:29:0", "6:31:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["6:28:0", "6:29:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["6:27:0", "6:28:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["6:12:0", "6:27:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["6:11:0", "6:12:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["6:6:0", "6:11:0"],
  },
  { date: "2023-3-6", stage_type: "비수면", time_duration: ["6:4:0", "6:6:0"] },
  { date: "2023-3-6", stage_type: "렘수면", time_duration: ["6:0:0", "6:4:0"] },
  {
    date: "2023-3-6",
    stage_type: "깊은수면",
    time_duration: ["5:59:0", "6:0:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["5:58:0", "5:59:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "깊은수면",
    time_duration: ["5:54:0", "5:58:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["5:35:0", "5:54:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "얕은수면",
    time_duration: ["5:0:0", "5:35:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["4:59:0", "5:0:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "얕은수면",
    time_duration: ["4:57:0", "4:59:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["4:54:0", "4:57:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["4:34:0", "4:54:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "얕은수면",
    time_duration: ["4:33:0", "4:34:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "깊은수면",
    time_duration: ["4:31:0", "4:33:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["3:52:0", "4:31:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["3:51:0", "3:52:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["3:49:0", "3:51:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["3:48:0", "3:49:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["3:41:0", "3:48:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["3:35:0", "3:41:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["3:28:0", "3:35:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["3:21:0", "3:28:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["3:18:0", "3:21:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["3:17:0", "3:18:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["3:11:0", "3:17:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["3:10:0", "3:11:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "깊은수면",
    time_duration: ["2:56:0", "3:10:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["2:37:0", "2:56:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["2:36:0", "2:37:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["2:31:0", "2:36:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["2:28:0", "2:31:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "깊은수면",
    time_duration: ["2:26:0", "2:28:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["2:18:0", "2:26:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["2:17:0", "2:18:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["2:7:0", "2:17:0"],
  },
  { date: "2023-3-6", stage_type: "비수면", time_duration: ["2:4:0", "2:7:0"] },
  { date: "2023-3-6", stage_type: "렘수면", time_duration: ["2:1:0", "2:4:0"] },
  {
    date: "2023-3-6",
    stage_type: "비수면",
    time_duration: ["1:55:0", "2:1:0"],
  },
  {
    date: "2023-3-6",
    stage_type: "렘수면",
    time_duration: ["1:37:0", "1:55:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 7:48:0", "2023-03-05 7:51:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 7:41:0", "2023-03-05 7:48:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "얕은수면",
    time_duration: ["2023-03-05 7:40:0", "2023-03-05 7:41:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 7:39:0", "2023-03-05 7:40:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "얕은수면",
    time_duration: ["2023-03-05 7:38:0", "2023-03-05 7:39:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 7:15:0", "2023-03-05 7:38:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 7:13:0", "2023-03-05 7:15:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 6:59:0", "2023-03-05 7:13:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 6:52:0", "2023-03-05 6:59:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "얕은수면",
    time_duration: ["2023-03-05 6:50:0", "2023-03-05 6:52:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 6:44:0", "2023-03-05 6:50:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "얕은수면",
    time_duration: ["2023-03-05 6:37:0", "2023-03-05 6:44:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "깊은수면",
    time_duration: ["2023-03-05 6:36:0", "2023-03-05 6:37:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 6:14:0", "2023-03-05 6:36:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "얕은수면",
    time_duration: ["2023-03-05 6:5:0", "2023-03-05 6:14:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 5:46:0", "2023-03-05 6:5:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 5:45:0", "2023-03-05 5:46:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 5:20:0", "2023-03-05 5:45:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 5:19:0", "2023-03-05 5:20:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 5:18:0", "2023-03-05 5:19:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "얕은수면",
    time_duration: ["2023-03-05 4:44:0", "2023-03-05 5:18:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 4:43:0", "2023-03-05 4:44:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 4:41:0", "2023-03-05 4:43:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 4:36:0", "2023-03-05 4:41:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 4:35:0", "2023-03-05 4:36:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 4:34:0", "2023-03-05 4:35:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 4:21:0", "2023-03-05 4:34:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 4:20:0", "2023-03-05 4:21:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 4:14:0", "2023-03-05 4:20:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 4:1:0", "2023-03-05 4:14:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 4:0:0", "2023-03-05 4:1:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 3:56:0", "2023-03-05 4:0:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 3:54:0", "2023-03-05 3:56:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 3:44:0", "2023-03-05 3:54:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 3:43:0", "2023-03-05 3:44:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "깊은수면",
    time_duration: ["2023-03-05 3:31:0", "2023-03-05 3:43:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 3:19:0", "2023-03-05 3:31:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 3:16:0", "2023-03-05 3:19:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 3:15:0", "2023-03-05 3:16:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 3:14:0", "2023-03-05 3:15:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 3:8:0", "2023-03-05 3:14:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 3:6:0", "2023-03-05 3:8:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 3:3:0", "2023-03-05 3:6:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 2:59:0", "2023-03-05 3:3:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "깊은수면",
    time_duration: ["2023-03-05 2:47:0", "2023-03-05 2:59:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 2:41:0", "2023-03-05 2:47:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "깊은수면",
    time_duration: ["2023-03-05 2:39:0", "2023-03-05 2:41:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 2:27:0", "2023-03-05 2:39:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 2:25:0", "2023-03-05 2:27:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "깊은수면",
    time_duration: ["2023-03-05 2:23:0", "2023-03-05 2:25:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 2:12:0", "2023-03-05 2:23:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "비수면",
    time_duration: ["2023-03-05 2:7:0", "2023-03-05 2:12:0"],
  },
  {
    date: "2023-3-5",
    stage_type: "렘수면",
    time_duration: ["2023-03-05 1:36:0", "2023-03-05 2:7:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "얕은수면",
    time_duration: ["2023-03-04 7:36:0", "2023-03-04 7:52:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 7:35:0", "2023-03-04 7:36:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "얕은수면",
    time_duration: ["2023-03-04 7:34:0", "2023-03-04 7:35:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 7:33:0", "2023-03-04 7:34:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "얕은수면",
    time_duration: ["2023-03-04 7:26:0", "2023-03-04 7:33:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 7:25:0", "2023-03-04 7:26:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "얕은수면",
    time_duration: ["2023-03-04 7:19:0", "2023-03-04 7:25:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 7:14:0", "2023-03-04 7:19:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 7:13:0", "2023-03-04 7:14:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 7:9:0", "2023-03-04 7:13:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 7:8:0", "2023-03-04 7:9:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 7:1:0", "2023-03-04 7:8:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "깊은수면",
    time_duration: ["2023-03-04 7:0:0", "2023-03-04 7:1:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 6:11:0", "2023-03-04 7:0:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 6:8:0", "2023-03-04 6:11:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 6:7:0", "2023-03-04 6:8:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "얕은수면",
    time_duration: ["2023-03-04 5:17:0", "2023-03-04 6:7:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 5:8:0", "2023-03-04 5:17:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 5:4:0", "2023-03-04 5:8:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 5:0:0", "2023-03-04 5:4:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "깊은수면",
    time_duration: ["2023-03-04 4:49:0", "2023-03-04 5:0:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 4:37:0", "2023-03-04 4:49:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 4:36:0", "2023-03-04 4:37:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "깊은수면",
    time_duration: ["2023-03-04 4:35:0", "2023-03-04 4:36:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 4:22:0", "2023-03-04 4:35:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 4:20:0", "2023-03-04 4:22:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 4:11:0", "2023-03-04 4:20:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "비수면",
    time_duration: ["2023-03-04 3:49:0", "2023-03-04 4:11:0"],
  },
  {
    date: "2023-3-4",
    stage_type: "렘수면",
    time_duration: ["2023-03-04 3:11:0", "2023-03-04 3:49:0"],
  },
];

export default {
  name: "SleepGraph",
  components: {
    apexchart: VueApexCharts,
  },
  data: function () {
    return {
      chartOptions: {
        chart: {
          heigth: 450,
          type: "rangeBar",
        },
        xaxis: {
          type: "datetime",
        },
        plotOptions: {
          bar: {
            horizontal: true,
            barHeight: "80%",
          },
        },
        stroke: {
          width: 1,
        },
        fill: {
          type: "solid",
          opacity: 0.6,
        },
        legend: {
          position: "top",
          horizontalAlign: "left",
        },
      },

      series: [
        {
          name: "비수면",
          data: sleep_data
            .filter((items) => items.stage_type == "비수면")
            .map((filterd_items) => {
              return {
                x: filterd_items.date,
                y: [
                  new Date(filterd_items.time_duration[0]).getTime(),
                  new Date(filterd_items.time_duration[1]).getTime(),
                ],
              };
            }),
        },
        {
          name: "렘수면",
          data: sleep_data
            .filter((items) => items.stage_type == "렘수면")
            .map((filterd_items) => {
              return {
                x: filterd_items.date,
                y: [
                  new Date(filterd_items.time_duration[0]).getTime(),
                  new Date(filterd_items.time_duration[1]).getTime(),
                ],
              };
            }),
        },
        {
          name: "깊은수면",
          data: sleep_data
            .filter((items) => items.stage_type == "깊은수면")
            .map((filterd_items) => {
              return {
                x: filterd_items.date,
                y: [
                  new Date(filterd_items.time_duration[0]).getTime(),
                  new Date(filterd_items.time_duration[1]).getTime(),
                ],
              };
            }),
        },
        {
          name: "얕은수면",
          data: sleep_data
            .filter((items) => items.stage_type == "얕은수면")
            .map((filterd_items) => {
              return {
                x: filterd_items.date,
                y: [
                  new Date(filterd_items.time_duration[0]).getTime(),
                  new Date(filterd_items.time_duration[1]).getTime(),
                ],
              };
            }),
        },
      ],

      series_example: [
        {
          name: "Bob",
          data: [
            {
              x: "Design",
              y: [
                new Date("2019-03-05").getTime(),
                new Date("2019-03-08").getTime(),
              ],
            },
            {
              x: "Code",
              y: [
                new Date("2019-03-02").getTime(),
                new Date("2019-03-05").getTime(),
              ],
            },
            {
              x: "Code",
              y: [
                new Date("2019-03-05").getTime(),
                new Date("2019-03-07").getTime(),
              ],
            },
            {
              x: "Test",
              y: [
                new Date("2019-03-03").getTime(),
                new Date("2019-03-09").getTime(),
              ],
            },
            {
              x: "Test",
              y: [
                new Date("2019-03-08").getTime(),
                new Date("2019-03-11").getTime(),
              ],
            },
            {
              x: "Validation",
              y: [
                new Date("2019-03-11").getTime(),
                new Date("2019-03-16").getTime(),
              ],
            },
            {
              x: "Design",
              y: [
                new Date("2019-03-01").getTime(),
                new Date("2019-03-03").getTime(),
              ],
            },
          ],
        },
        {
          name: "Joe",
          data: [
            {
              x: "Design",
              y: [
                new Date("2019-03-02").getTime(),
                new Date("2019-03-05").getTime(),
              ],
            },
            {
              x: "Test",
              y: [
                new Date("2019-03-06").getTime(),
                new Date("2019-03-16").getTime(),
              ],
              goals: [
                {
                  name: "Break",
                  value: new Date("2019-03-10").getTime(),
                  strokeColor: "#CD2F2A",
                },
              ],
            },
            {
              x: "Code",
              y: [
                new Date("2019-03-03").getTime(),
                new Date("2019-03-07").getTime(),
              ],
            },
            {
              x: "Deployment",
              y: [
                new Date("2019-03-20").getTime(),
                new Date("2019-03-22").getTime(),
              ],
            },
            {
              x: "Design",
              y: [
                new Date("2019-03-10").getTime(),
                new Date("2019-03-16").getTime(),
              ],
            },
          ],
        },
        {
          name: "Dan",
          data: [
            {
              x: "Code",
              y: [
                new Date("2019-03-10").getTime(),
                new Date("2019-03-17").getTime(),
              ],
            },
            {
              x: "Validation",
              y: [
                new Date("2019-03-05").getTime(),
                new Date("2019-03-09").getTime(),
              ],
              goals: [
                {
                  name: "Break",
                  value: new Date("2019-03-07").getTime(),
                  strokeColor: "#CD2F2A",
                },
              ],
            },
          ],
        },
      ],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#sleepGraph {
  width: 40rem;
  height: 400px;
  margin-top: 10rem;
  margin: auto;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
