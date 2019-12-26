<template>
    <div class="">
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item><i class="el-icon-lx-copy"></i>消息界面</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <el-tabs v-model="message">
                <el-tab-pane :label="`未读消息(${unread.length})`" name="first">
                    <el-table :data="unread" :show-header="true" style="width: 100%">
                        <el-table-column label="Name">
                            <template slot-scope="scope">
                                <span class="message-title">{{scope.row.title}}</span>
                            </template>
                        </el-table-column>
                        <el-table-column prop="age" label="age" width="150"></el-table-column>
                        <el-table-column prop="Nicknome" label="Nicknome" width="150"></el-table-column>
                        <el-table-column prop="date" label="date" width="150"></el-table-column>
                        <el-table-column label="Employee" width="120">
                            <template slot-scope="scope">
                                <el-button size="small" @click="handleRead(scope.$index)">标为已读</el-button>
                            </template>
                        </el-table-column>
                    </el-table>
                    <div class="handle-row">
                        <el-button type="primary">全部标为已读</el-button>
                    </div>
                </el-tab-pane>
                <el-tab-pane :label="`已读消息(${read.length})`" name="second">
                    <template v-if="message === 'second'">
                        <el-table :data="read" :show-header="true" style="width: 100%">
                            <el-table-column label="Name">
                                <template slot-scope="scope">
                                    <span class="message-title">{{scope.row.title}}</span>
                                </template>
                            </el-table-column>
                            <el-table-column prop="age" label="age" width="150"></el-table-column>
                            <el-table-column prop="Nicknome" label="Nicknome" width="150"></el-table-column>
                            <el-table-column prop="date" label="date" width="210"></el-table-column>
                            <el-table-column width="120">
                                <template slot-scope="scope">
                                    <el-button type="danger" @click="handleDel(scope.$index)">删除</el-button>
                                </template>
                            </el-table-column>
                        </el-table>
                        <div class="handle-row">
                            <el-button type="danger">删除全部</el-button>
                        </div>
                    </template>
                </el-tab-pane>
                <el-tab-pane :label="`回收站(${recycle.length})`" name="third">
                    <template v-if="message === 'third'">
                        <el-table :data="recycle" :show-header="true" style="width: 100%">
                            <el-table-column lable="Name">
                                <template slot-scope="scope">
                                    <span class="message-title">{{scope.row.title}}</span>
                                </template>
                            </el-table-column>
                            <el-table-column prop="age" label="age" width="150"></el-table-column>
                            <el-table-column prop="Nicknome" label="Nicknome" width="150"></el-table-column>
                            <el-table-column prop="date" label="date" width="210"></el-table-column>
                            <el-table-column width="120">
                                <template slot-scope="scope">
                                    <el-button @click="handleRestore(scope.$index)">还原</el-button>
                                </template>
                            </el-table-column>
                        </el-table>
                        <div class="handle-row">
                            <el-button type="danger">清空回收站</el-button>
                        </div>
                    </template>
                </el-tab-pane>
            </el-tabs>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'tabs',
        data() {
            return {
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
                read: [{
                    age: '21',
                    Nicknome: 'huahua',
                    date: '2018-04-19 20:00:00',
                    title: 'Kindsome',
                }],
                recycle: [{
                    age: '43',
                    Nicknome: 'hongri',
                    date: '2018-04-19 20:00:00',
                    title: 'Kindnameese',
                }]
            }
        },
        methods: {
            handleRead(index) {
                const item = this.unread.splice(index, 1);
                console.log(item);
                this.read = item.concat(this.read);
            },
            handleDel(index) {
                const item = this.read.splice(index, 1);
                this.recycle = item.concat(this.recycle);
            },
            handleRestore(index) {
                const item = this.recycle.splice(index, 1);
                this.read = item.concat(this.read);
            }
        },
        //更新未读信息条数
        computed: {
            unreadNum(){
                return this.unread.length;
            }
        }
    }

</script>

<style>
    .message-title{
        cursor: pointer;
    }
    .handle-row{
        margin-top: 30px;

    }
</style>

