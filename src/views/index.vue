<template>
    <div class="app-container home">
        <el-row :gutter="20">
            <el-col :lg="6">
              <el-card class="box-card">
                <v-chart :options="options.firstOption" autoresize></v-chart>
              </el-card>
            </el-col>
            <el-col :lg="6">
              <el-card class="box-card">
                <v-chart :options="options.firstOption" autoresize></v-chart>
              </el-card>
            </el-col>
            <el-col :lg="6">
              <el-card class="box-card">
                <v-chart :options="options.firstOption" autoresize></v-chart>
              </el-card>
            </el-col>
            <el-col :lg="6">
              <el-card class="box-card">
                <v-chart :options="options.firstOption" autoresize></v-chart>
              </el-card>
            </el-col>
        </el-row>
        <el-row :gutter="20">
            <el-col :sm="24" :lg="12" style="padding-left: 20px">
                <v-chart :options="options.secondOption" autoresize></v-chart>
            </el-col>
             <el-col :sm="24" :lg="12" style="padding-left: 20px">
                <v-chart :options="options.secondOption" autoresize></v-chart>
            </el-col>
        </el-row>
        <el-divider />
        <el-row :gutter="20">
            <!-- <el-col :xs="24" :sm="24" :md="12" :lg="8"> -->
            <el-card class="update-log">
                <v-chart :options="options.thirdOption" autoresize></v-chart>
            </el-card>
            <!-- </el-col> -->
        </el-row>
    </div>
</template>

<script>
import echarts from "echarts";
import Echarts from "vue-echarts/components/ECharts";
import "echarts/lib/chart/bar";
import "echarts/lib/component/axis";
import "echarts/lib/component/tooltip"; //这里需要引入，不然提示没效果
export default {
    name: "index",
    components: {
        "v-chart": Echarts,
    },
    data() {
        return {
            // 版本号
            version: "3.1.0",
            options: {
                firstOption: {},
                secondOption: {},
                thirdOption: {},
            },
        };
    },
    methods: {
        goTarget(href) {
            window.open(href, "_blank");
        },
        initfirstOption() {
            this.options = {
                ...this.options,
                firstOption: {
                    tooltip: {
                        trigger: "axis",
                        textStyle: {
                            fontSize: 20,
                        },
                    },
                    xAxis: {
                        type: "category",
                        data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
                    },
                    yAxis: {
                        type: "value",
                    },
                    series: [
                        {
                            data: [820, 932, 901, 934, 1290, 1330, 1320],
                            type: "line",
                            smooth: true,
                        },
                    ],
                },
            };
        },
        initSecondOption() {
            this.options = {
                ...this.options,
                secondOption: {
                    tooltip: {
                        trigger: "axis",
                        axisPointer: {
                            type: "shadow",
                        },
                    },
                    grid: {
                        left: "3%",
                        right: "4%",
                        bottom: "3%",
                        containLabel: true,
                    },
                    xAxis: [
                        {
                            type: "category",
                            data: [
                                "Mon",
                                "Tue",
                                "Wed",
                                "Thu",
                                "Fri",
                                "Sat",
                                "Sun",
                            ],
                            axisTick: {
                                alignWithLabel: true,
                            },
                        },
                    ],
                    yAxis: [
                        {
                            type: "value",
                        },
                    ],
                    series: [
                        {
                            name: "直接访问",
                            type: "bar",
                            barWidth: "60%",
                            data: [10, 52, 200, 334, 390, 330, 220],
                            itemStyle: {
                                normal: {
                                    color: "#61a0a8",
                                },
                            },
                        },
                    ],
                },
            };
        },
        initThirdOption() {
            this.options = {
                ...this.options,
                thirdOption: {
                    tooltip: {
                        trigger: "axis",
                        textStyle: {
                            fontSize: 20,
                        },
                    },
                    grid: {
                        left: "1%",
                        right: "4%",
                        bottom: "3%",
                        containLabel: true,
                    },
                    xAxis: {
                        type: "category",
                        data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
                    },
                    yAxis: {
                        type: "value",
                    },
                    series: [
                        {
                            data: [820, 932, 901, 934, 1290, 1330, 1320],
                            type: "line",
                            smooth: true,
                        },
                    ],
                },
            };
        },
    },
    created() {
        this.initfirstOption();
        this.initSecondOption();
        this.initThirdOption();
    },
};
</script>

<style scoped lang="scss">
.home {
    blockquote {
        padding: 10px 20px;
        margin: 0 0 20px;
        font-size: 17.5px;
        border-left: 5px solid #eee;
    }
    hr {
        margin-top: 20px;
        margin-bottom: 20px;
        border: 0;
        border-top: 1px solid #eee;
    }
    .col-item {
        margin-bottom: 20px;
    }

    ul {
        padding: 0;
        margin: 0;
    }

    font-family: "open sans", "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 13px;
    color: #676a6c;
    overflow-x: hidden;

    ul {
        list-style-type: none;
    }

    h4 {
        margin-top: 0px;
    }

    h2 {
        margin-top: 10px;
        font-size: 26px;
        font-weight: 100;
    }

    p {
        margin-top: 10px;

        b {
            font-weight: 700;
        }
    }

    .update-log {
        ol {
            display: block;
            list-style-type: decimal;
            margin-block-start: 1em;
            margin-block-end: 1em;
            margin-inline-start: 0;
            margin-inline-end: 0;
            padding-inline-start: 40px;
        }
    }
}
.echarts {
    // height: 896px;
    width: 100%;
}
.box-card{
  .echarts{
    height: 200px;
  }
}
</style>

