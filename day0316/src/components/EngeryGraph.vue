<template>
  <div id="energychartdiv"></div>
</template>

<script>
import * as am5 from "@amcharts/amcharts5";
import * as am5xy from "@amcharts/amcharts5/xy";
import am5themes_Animated from "@amcharts/amcharts5/themes/Animated";

export default {
  mounted() {
    am5.ready(() => {
      const root = am5.Root.new("energychartdiv");

      root.setThemes([am5themes_Animated.new(root)]);

      const chart = root.container.children.push(
        am5xy.XYChart.new(root, {
          panX: false,
          panY: false,
          wheelX: "panX",
          wheelY: "zoomX",
        })
      );

      const cursor = chart.set(
        "cursor",
        am5xy.XYCursor.new(root, { behavior: "zoomX" })
      );
      cursor.lineY.set("visible", false);

      const xAxis = chart.xAxes.push(
        am5xy.GaplessDateAxis.new(root, {
          maxDeviation: 0,
          baseInterval: {
            timeUnit: "day",
            count: 1,
          },
          renderer: am5xy.AxisRendererX.new(root, {
            minGridDistance: 60,
          }),
          start: 0.9,
          tooltip: am5.Tooltip.new(root, {}),
        })
      );

      const yAxis = chart.yAxes.push(
        am5xy.ValueAxis.new(root, {
          renderer: am5xy.AxisRendererY.new(root, {}),
        })
      );

      const series = chart.series.push(
        am5xy.ColumnSeries.new(root, {
          name: "Series",
          xAxis: xAxis,
          yAxis: yAxis,
          valueYField: "value",
          valueXField: "date",
          tooltip: am5.Tooltip.new(root, {
            labelText: "{valueY}",
          }),
        })
      );

      series.columns.template.setAll({ strokeOpacity: 0 });

      chart.set(
        "scrollbarX",
        am5.Scrollbar.new(root, {
          orientation: "horizontal",
        })
      );

      const data = [
        { date: 1560902400000, value: 402 },
        { date: 1561161600000, value: 416 },
        { date: 1561248000000, value: 403 },
        { date: 1561334400000, value: 533 },
        { date: 1561680000000, value: 451 },
        { date: 1561766400000, value: 423 },
        { date: 1561852800000, value: 200 },
        { date: 1562198400000, value: 415 },
        { date: 1562284800000, value: 370 },
        { date: 1562371200000, value: 136 },
        { date: 1562716800000, value: 549 },
        { date: 1562803200000, value: 874 },
        { date: 1562889600000, value: 868 },
        { date: 1563235200000, value: 130 },
        { date: 1563321600000, value: 391 },
        { date: 1563408000000, value: 13 },
        { date: 1563753600000, value: 191 },
        { date: 1563840000000, value: 4 },
        { date: 1563926400000, value: 289 },
        { date: 1564012800000, value: 5 },
        { date: 1564444800000, value: 326 },
        { date: 1564531200000, value: 509 },
        { date: 1564963200000, value: 190 },
        { date: 1565481600000, value: 448 },
        { date: 1566000000000, value: 6 },
      ];

      series.data.setAll(data);

      series.appear(1000);
      chart.appear(1000, 100);
    });
  },
};
</script>

<style>
#energychartdiv {
  width: 40rem;
  height: 400px;
  margin-top: 10rem;
  margin: auto;
}
</style>