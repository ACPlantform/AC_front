<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item><i class="el-icon-lx-calendar"></i>数据管理</el-breadcrumb-item>
                <el-breadcrumb-item>实时数据管理</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <div class="handle-row">
                <el-col :span="10" style="padding-right:10px">
                    <Select v-model="model11" filterable>
                        <Option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                    </Select>
                </el-col>
                <el-col :span="8">
                    <el-date-picker type="date" placeholder="Select date" style="width: 200px"></el-date-picker>
                </el-col>
                <el-button type="choose">确定</el-button>
                <el-button type="out">导出</el-button>

                <el-table :data="unread" :show-header="true" style="width: 100%">
                    <el-table-column label="序号">
                        <template slot-scope="scope">
                            <span class="message-title">{{scope.row.title}}</span>
                        </template>
                    </el-table-column>
                    <el-table-column prop="age" label="采集时间" width="150"></el-table-column>
                    <el-table-column prop="date" label="date" width="150"></el-table-column>
                    <el-table-column prop="Nicknome" label="指标1" width="150"></el-table-column>
                    <el-table-column label="操作" width="120">
                        <template slot-scope="scope">
                            <el-button size="small" @click="handleRead(scope.$index)">图表展示</el-button>
                        </template>
                    </el-table-column>
                </el-table>

                <el-row :gutter="20">
                    <el-col :span="8">
                        <el-card shadow="hover" style="height:252px;">
                            <div slot="header" class="clearfix" style="border-radius:10px;">
                                <span>实时消息</span>
                            </div>
                            <span>XXX：设备A不工作了</span><br>
                            <span>XXX：设备B工作正常</span><br>
                            <span>XXX：设备C工作正常</span><br>
                            <span>XXX：设备C工作正常</span><br>
                            <span>XXX：设备C工作正常</span><br>
                            <span>XXX：设备C工作正常</span><br>
                            <span>XXX：设备C工作正常</span><br>
                        </el-card>
                    </el-col>
                    <el-card :span="16">
                        <legend>设备情况</legend>
                        <el-row :gutter="18" class="mgb20">
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px',color:'black'}" >
                                    <div class="grid-content grid-con-1">
                                        <div class="grid-cont-right">
                                            <div>设备总数量</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px'}" >
                                    <div class="grid-content grid-con-2">
                                        <div class="grid-cont-right" >
                                            <div>运行设备数量</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px'}">
                                    <div class="grid-content grid-con-3">
                                        <div class="grid-cont-right">
                                            <div>异常设备数量</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                        </el-row>
                        <legend>监测场景</legend>
                        <el-row :gutter="20" class="mgb20">
                                <el-col :span="8">
                                    <el-card shadow="hover" :body-style="{padding: '0px'}">
                                        <div class="grid-content grid-con-1">
                                            <div class="grid-cont-right">
                                                <div>海水稻</div>
                                            </div>
                                        </div>
                                    </el-card>
                                </el-col>
                                <el-col :span="8">
                                    <el-card shadow="hover" :body-style="{padding: '0px'}" >
                                        <div class="grid-content grid-con-2">
                                            <div class="grid-cont-right" >
                                                <div>鱼菜共生</div>
                                            </div>
                                        </div>
                                    </el-card>
                                </el-col>
                                <el-col :span="8">
                                    <el-card shadow="hover" :body-style="{padding: '0px'}">
                                        <div class="grid-content grid-con-3">
                                            <div class="grid-cont-right">
                                                <div>水产养殖</div>
                                            </div>
                                        </div>
                                    </el-card>
                                </el-col>
                            </el-row>
                        <legend>设备情况</legend>
                        <el-row :gutter="18" class="mgb20">
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px',color:'black'}" >
                                    <div class="grid-content grid-con-1">
                                        <div class="grid-cont-right">
                                            <div>设备总数量</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px'}" >
                                    <div class="grid-content grid-con-2">
                                        <div class="grid-cont-right" >
                                            <div>运行设备数量</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px'}">
                                    <div class="grid-content grid-con-3">
                                        <div class="grid-cont-right">
                                            <div>异常设备数量</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                        </el-row>
                        <legend>监测场景</legend>
                        <el-row :gutter="20" class="mgb20">
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px'}">
                                    <div class="grid-content grid-con-1">
                                        <div class="grid-cont-right">
                                            <div>海水稻</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px'}" >
                                    <div class="grid-content grid-con-2">
                                        <div class="grid-cont-right" >
                                            <div>鱼菜共生</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                            <el-col :span="8">
                                <el-card shadow="hover" :body-style="{padding: '0px'}">
                                    <div class="grid-content grid-con-3">
                                        <div class="grid-cont-right">
                                            <div>水产养殖</div>
                                        </div>
                                    </div>
                                </el-card>
                            </el-col>
                        </el-row>
                    </el-card>
                    <el-card :span="16">
                        <fieldset>
                            <legend>监测指标概览</legend>
                            <el-row :gutter="20">
                                <el-col :span="12">
                                    <el-card shadow="hover">
                                        <div class="content-title">柱状图</div>
                                        <schart ref="bar" class="schart" canvasId="bar" :options="options"></schart>
                                    </el-card>
                                </el-col>
                                <el-col :span="12">
                                    <el-card shadow="hover">
                                        <div class="content-title">环形图</div>
                                        <schart ref="ring" class="schart" canvasId="ring" :options="options2"></schart>
                                    </el-card>
                                </el-col>
                            </el-row>
                        </fieldset>
                    </el-card>
                </el-row>
            </div>
        </div>
    </div>
</template>

<script>
    import Schart from 'vue-schart';
    import bus from '../common/bus';
    export default {
        data () {
            return {
                cityList: [
                    {
                        value: '传感器',
                        label: '传感器'
                    },
                    {
                        value: 'London',
                        label: 'London'
                    },
                    {
                        value: 'Sydney',
                        label: 'Sydney'
                    },
                    {
                        value: 'Ottawa',
                        label: 'Ottawa'
                    },
                    {
                        value: 'Paris',
                        label: 'Paris'
                    },
                    {
                        value: 'Canberra',
                        label: 'Canberra'
                    }
                ],
                model11: '',
                message: 'first',
                showHeader: true,
                unread: [{
                    age: '40',
                    Nicknome: 'Peldi',
                    date: '2018-04-19 20:00:00',
                    title: 'Giacomo Guilizzoni',
                },{
                    age: '38',
                    Nicknome: '',
                    date: '2018-04-19 20:00:00',
                    title: 'Mareo Botton',
                }, {
                    age: '33',
                    Nicknome: 'Patato',
                    date: '2018-04-19 20:00:00',
                    title: 'Better Haif',
                },{
                    age: '41',
                    Nicknome: 'Monitor',
                    date: '2018-04-19 20:00:00',
                    title: 'Han Nan',
                }],
                options: {
                    type: 'bar',
                    title: {
                        text: '最近一周各品类销售图'
                    },
                    xRorate: 25,
                    labels: ['周一', '周二', '周三', '周四', '周五'],
                    datasets: [
                        {
                            label: '家电',
                            data: [234, 278, 270, 190, 230]
                        },
                        {
                            label: '百货',
                            data: [164, 178, 190, 135, 160]
                        },
                        {
                            label: '食品',
                            data: [144, 198, 150, 235, 120]
                        }
                    ]
                },
                options2: {
                    type: 'line',
                    title: {
                        text: '最近几个月各品类销售趋势图'
                    },
                    labels: ['6月', '7月', '8月', '9月', '10月'],
                    datasets: [
                        {
                            label: '家电',
                            data: [234, 278, 270, 190, 230]
                        },
                        {
                            label: '百货',
                            data: [164, 178, 150, 135, 160]
                        },
                        {
                            label: '食品',
                            data: [74, 118, 200, 235, 90]
                        }
                    ]
                }
            }
        },
        components: {
            Schart
        }
    }
</script>
<style scoped>
    .schart {
        width: 100%;
        height: 300px;
    }
</style>
