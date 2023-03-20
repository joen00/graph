<template>
  <div id="stresschartdiv"></div>
</template>

<script>
import * as am5 from "@amcharts/amcharts5";
import * as am5xy from "@amcharts/amcharts5/xy";
import * as am5radar from "@amcharts/amcharts5/radar";
import am5themes_Animated from "@amcharts/amcharts5/themes/Animated";

export default {
  mounted() {
    am5.ready(() => {
      var root = am5.Root.new("stresschartdiv");
      root.setThemes([am5themes_Animated.new(root)]);
      var chart = root.container.children.push(
        am5radar.RadarChart.new(root, {
          panX: false,
          panY: false,
          wheelX: "none",
          wheelY: "none",
          startAngle: -84,
          endAngle: 264,
          innerRadius: am5.percent(40),
        })
      );

      const cursor = chart.set(
        "cursor",
        am5radar.RadarCursor.new(root, {
          behavior: "zoomX",
        })
      );
      cursor.lineY.set("forceHidden", true);

      // Add scrollbar
      // https://www.amcharts.com/docs/v5/charts/xy-chart/scrollbars/
      chart.set(
        "scrollbarX",
        am5.Scrollbar.new(root, {
          orientation: "horizontal",
          exportable: false,
          // start: 7,
        })
      );

      // Create axes
      // https://www.amcharts.com/docs/v5/charts/xy-chart/axes/
      var xRenderer = am5radar.AxisRendererCircular.new(root, {
        minGridDistance: 30,
      });

      xRenderer.grid.template.set("forceHidden", true);

      var xAxis = chart.xAxes.push(
        am5xy.CategoryAxis.new(root, {
          maxDeviation: 7,
          categoryField: "category",
          // renderer: xRenderer,
          renderer: xRenderer,
        })
      );

      var yRenderer = am5radar.AxisRendererRadial.new(root, {});
      yRenderer.labels.template.set("centerX", am5.p50);

      var yAxis = chart.yAxes.push(
        am5xy.ValueAxis.new(root, {
          maxDeviation: 0.3,
          min: 0,
          renderer: yRenderer,
        })
      );

      // Add series
      // https://www.amcharts.com/docs/v5/charts/xy-chart/series/
      var series = chart.series.push(
        am5radar.RadarColumnSeries.new(root, {
          name: "Series 1",
          sequencedInterpolation: true,
          xAxis: xAxis,
          yAxis: yAxis,
          valueYField: "value",
          categoryXField: "category",
        })
      );

      // Rounded corners for columns
      series.columns.template.setAll({
        cornerRadius: 5,
        tooltipText: "{categoryX}: {valueY}",
      });

      // Make each column to be of a different color
      series.columns.template.adapters.add("fill", function (fill, target) {
        return chart.get("colors").getIndex(series.columns.indexOf(target));
      });

      series.columns.template.adapters.add("stroke", function (stroke, target) {
        return chart.get("colors").getIndex(series.columns.indexOf(target));
      });

      // Set data
      var data = [
        { category: "19.06.19", value: 70 },
        { category: "19.06.22", value: 46 },
        { category: "19.06.23", value: 73 },
        { category: "19.06.28", value: 41 },
        { category: "19.06.24", value: 3 },
        { category: "19.06.29", value: 23 },
        { category: "19.06.30", value: 20 },
        { category: "19.07.04", value: 15 },
        { category: "19.07.05", value: 70 },
        { category: "19.07.06", value: 36 },
        { category: "19.07.10", value: 49 },
        { category: "19.07.11", value: 74 },
        { category: "19.07.12", value: 68 },
        { category: "19.07.16", value: 30 },
        { category: "19.07.17", value: 91 },
        { category: "19.07.18", value: 13 },
        { category: "19.07.22", value: 91 },
        { category: "19.07.23", value: 4 },
        { category: "19.07.24", value: 89 },
        { category: "19.07.25", value: 5 },
        { category: "19.07.30", value: 26 },
        { category: "19.07.31", value: 9 },
        { category: "19.08.05", value: 19 },
        { category: "19.08.11", value: 48 },
        { category: "19.08.17", value: 6 },
      ];

      // for (var i = 1; i < 10; i++) {
      //   data.push({ category: i, value: Math.round(Math.random() * 100) });
      // }

      xAxis.data.setAll(data);
      series.data.setAll(data);

      // Make stuff animate on load
      // https://www.amcharts.com/docs/v5/concepts/animations/
      series.appear(1000);
      chart.appear(1000, 100);
    });
  },
};
</script>

<style>
#stresschartdiv {
  width: 40rem;
  height: 400px;
  margin-top: 10rem;
  margin: auto;
}
</style>