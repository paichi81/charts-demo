<template lang="pug">
  v-container(fluid).ApexChartsPage

    // 単純な棒グラフ バーチャート
    v-row
      v-col(cols="12" md="8" ).d-flex.flex-wrap
        v-card.flex
          v-card-title Bar Chart
          v-card-text
            apexchart(
              width="500"
              type="bar"
              :options="computed_options_bar1"
              :series="series1"
            )
        v-card.flex
          v-card-title Stack Chart
          v-card-text
            apexchart(
              width="500"
              type="bar"
              :options="computed_options_bar1"
              :series="series2"
            )
      v-col(cols="12" md="4")
        v-switch(v-model="horizontal" label="水平")
        v-switch(v-model="barStack" label="積み上げ")
        v-switch(v-model="showToolbar" label="ツールバー表示")
        v-switch(v-model="enableZoom" label="ズーム")
        v-select(v-model="selectedThemeMode" :items="themeModes" label="モード")
        v-select(v-model="selectedTheme" :items="palettes" label="パレット")

    // タイムラインチャート
    v-row
      v-col(cols="12" md="8" ).d-flex.flex-wrap
        v-card.flex
          v-card-title Timeline Chart
          v-card-text
            apexchart(
              type="rangeBar"
              :options="computed_options_timeline1"
              :series="series_timeline1"
            )

</template>

<script>

    export default {
        name: "ApexChartsPage",
        data() {
            return {
                palettes: [
                    'palette1',
                    'palette2',
                    'palette3',
                    'palette4',
                    'palette5',
                    'palette6',
                    'palette7',
                    'palette8',
                    'palette9',
                    'palette10',
                ],
                themeModes: [
                  'light',
                  'dark'
                ],
                selectedThemeMode: 'light',
                selectedTheme: null,
                horizontal: false,
                barStack: true,
                showToolbar: true,
                enableZoom: true,
                series1: [{
                    name: 'series-1',
                    data: [30, 40, 45, 50, 49, 60, 70, 91]
                }],
                series2: [
                    {
                        name: '要素A',
                        data: [30, 40, 45, 50, 49, 60, 70, 91]
                    },
                    {
                        name: '要素B',
                        data: [11, 45, 14, 8, 10, 10, 0, 81]
                    }
                ],
                series_timeline1: [
                    {
                        name: 'Bob',
                        data: [
                            {
                                x: 'Design',
                                y: [
                                    new Date('2019-03-05').getTime(),
                                    new Date('2019-03-08').getTime()
                                ]
                            },
                            {
                                x: 'Code',
                                y: [
                                    new Date('2019-03-02').getTime(),
                                    new Date('2019-03-05').getTime()
                                ]
                            },
                            {
                                x: 'Code',
                                y: [
                                    new Date('2019-03-05').getTime(),
                                    new Date('2019-03-07').getTime()
                                ]
                            },
                            {
                                x: 'Test',
                                y: [
                                    new Date('2019-03-03').getTime(),
                                    new Date('2019-03-09').getTime()
                                ]
                            },
                            {
                                x: 'Test',
                                y: [
                                    new Date('2019-03-08').getTime(),
                                    new Date('2019-03-11').getTime()
                                ]
                            },
                            {
                                x: 'Validation',
                                y: [
                                    new Date('2019-03-11').getTime(),
                                    new Date('2019-03-16').getTime()
                                ]
                            },
                            {
                                x: 'Design',
                                y: [
                                    new Date('2019-03-01').getTime(),
                                    new Date('2019-03-03').getTime()
                                ]
                            }
                        ]
                    },
                    {
                        name: 'Joe',
                        data: [
                            {
                                x: 'Design',
                                y: [
                                    new Date('2019-03-02').getTime(),
                                    new Date('2019-03-05').getTime()
                                ]
                            },
                            {
                                x: 'Test',
                                y: [
                                    new Date('2019-03-06').getTime(),
                                    new Date('2019-03-16').getTime()
                                ]
                            },
                            {
                                x: 'Code',
                                y: [
                                    new Date('2019-03-03').getTime(),
                                    new Date('2019-03-07').getTime()
                                ]
                            },
                            {
                                x: 'Deployment',
                                y: [
                                    new Date('2019-03-20').getTime(),
                                    new Date('2019-03-22').getTime()
                                ]
                            },
                            {
                                x: 'Design',
                                y: [
                                    new Date('2019-03-10').getTime(),
                                    new Date('2019-03-16').getTime()
                                ]
                            }
                        ]
                    },
                    {
                        name: 'Dan',
                        data: [
                            {
                                x: 'Code',
                                y: [
                                    new Date('2019-03-10').getTime(),
                                    new Date('2019-03-17').getTime()
                                ]
                            },
                            {
                                x: 'Validation',
                                y: [
                                    new Date('2019-03-05').getTime(),
                                    new Date('2019-03-09').getTime()
                                ]
                            },
                        ]
                    }
                ],
                dum: null
            }
        },
        mounted() {
        },
        computed: {
            computed_options_bar1() {
                return {
                    chart: {
                        id: 'vuechart-example',
                        stacked: this.barStack,
                        toolbar: {
                            show: this.showToolbar
                        },
                        zoom: {
                            enabled: this.enableZoom
                        }
                    },
                    xaxis: {
                        categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998]
                    },
                    theme: {
                        mode: this.selectedThemeMode,
                        palette: this.selectedTheme
                    },
                    plotOptions: {
                        bar: {
                            horizontal: this.horizontal,
                            startingShape: 'flat',
                            endingShape: 'flat',
                            columnWidth: '70%',
                            barHeight: '70%',
                            distributed: false,
                            rangeBarOverlap: true,
                            colors: {
                                ranges: [{
                                    from: 0,
                                    to: 0,
                                    color: undefined
                                }],
                                backgroundBarColors: [],
                                backgroundBarOpacity: 1,
                                backgroundBarRadius: 0,
                            },
                            dataLabels: {
                                position: 'top',
                                maxItems: 100,
                                hideOverflowingLabels: true,
                                orientation: 'horizontal'
                            }
                        }
                    }
                }
            },
            // opt2
            computed_options_timeline1() {
                return {
                    chart: {
                        height: 450,
                        type: 'rangeBar',
                        toolbar: {
                            show: this.showToolbar
                        },
                        zoom: {
                            enabled: this.enableZoom
                        }
                    },
                    theme: {
                        mode: this.selectedThemeMode,
                        palette: this.selectedTheme
                    },
                    plotOptions: {
                        bar: {
                            horizontal: true, // this.horizontal <= ng
                            barHeight: '80%'
                        }
                    },
                    xaxis: {
                        type: 'datetime'
                    },
                    stroke: {
                        width: 1
                    },
                    fill: {
                        type: 'solid',
                        opacity: 0.6
                    },
                    legend: {
                        position: 'top',
                        horizontalAlign: 'left'
                    }
                }
            }
        },
        methods: {
        }

    }
</script>

<style scoped>

</style>
