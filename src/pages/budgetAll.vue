<template>
    <div class="text-grey-7 text-bold q-mt-lg" style="font-size: 20px">
        Объем выданных средств Департаментом<br>
        по каждой субсидии и количество<br>     
        предпринимателей-получателей
    </div>
    <div class="row section q-mt-lg" style="display:flex">
        <div class="hello" ref="chartdiv1">
        </div>
        <div class="hello" ref="chartdiv2">
        </div>
    </div>
</template>

<script >
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";

am4core.useTheme(am4themes_animated);

export default {
  data() {
    return {
      budgetAll: []
    }
  },
  mounted() {
    this.$axios
        .get('https://mec.standsystematic.ru/api/budget/total/day/27.10.2021')
        .then(response => {
          this.budgetAll = response.data
        })
        .catch(error => console.log('Error', error.message))

    let chart1 = am4core.create(this.$refs.chartdiv1, am4charts.PieChart);

    chart1.dataSource.url = 'https://mec.standsystematic.ru/api/budget/total/day/27.10.2021';

    var pieSeries = chart1.series.push(new am4charts.PieSeries());
    pieSeries.dataFields.value = "total_budget";
    pieSeries.dataFields.category = "pipename";

    pieSeries.colors.list = [
      am4core.color("#fc1717"),
      am4core.color("#fc3838"),
      am4core.color("#fa5a5a"),
      am4core.color("#fc7777"),
      am4core.color("#fc8b8b"),
      am4core.color("#faa2a2"),
      am4core.color("#fabbbb"),
      am4core.color("#fc1717"),
      am4core.color("#fc3838"),
      am4core.color("#fa5a5a"),
      am4core.color("#fc7777"),
      am4core.color("#fc8b8b"),
      am4core.color("#faa2a2"),
    ];


    let chart2 = am4core.create(this.$refs.chartdiv2, am4charts.PieChart);

    chart2.dataSource.url = 'https://mec.standsystematic.ru/api/budget/total/day/27.10.2021';

    var pieSeries = chart2.series.push(new am4charts.PieSeries());
    pieSeries.dataFields.value = "amount";
    pieSeries.dataFields.category = "pipename";

    pieSeries.colors.list = [
      am4core.color("#fc1717"),
      am4core.color("#fc3838"),
      am4core.color("#fa5a5a"),
      am4core.color("#fc7777"),
      am4core.color("#fc8b8b"),
      am4core.color("#faa2a2"),
      am4core.color("#fabbbb"),
      am4core.color("#fc1717"),
      am4core.color("#fc3838"),
      am4core.color("#fa5a5a"),
      am4core.color("#fc7777"),
      am4core.color("#fc8b8b"),
      am4core.color("#faa2a2"),
    ];

    }
}
</script>

<style scoped>
.hello {
  width: 1000px;
  height: 500px;
}
</style>
