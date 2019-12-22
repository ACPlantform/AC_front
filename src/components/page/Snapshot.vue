//实时数据管理
<template>
    <div class="crumbs">
        <el-breadcrumb separator="/">
            <el-breadcrumb-item><i class="el-icon-rank"></i>实时数据管理</el-breadcrumb-item>
        </el-breadcrumb>
    </div>
    <div class="container">
        <div class="handle-box">
            <!--选择传感器-->
            <el-select v-model="query.address" placeholder="传感器" class="handle-select mr10">
                <el-option key="1" label="传感器1" value="传感器1"></el-option>
                <el-option key="2" label="传感器2" value="传感器2"></el-option>
                <el-option key="3" label="传感器3" value="传感器3"></el-option>
                <el-option key="4" label="传感器4" value="传感器4"></el-option>
                <el-option key="5" label="传感器5" value="传感器5"></el-option>
            </el-select>
            <el-input v-model="query.name" placeholder="用户名" class="handle-input mr10"></el-input>
            <el-button
                    type="primary"
                    icon="el-icon-delete"
                    class="handle-del mr10"
                    @click="delAllSelection"
            >确定</el-button>
            <el-button
                    type="primary"
                    icon="el-icon-delete"
                    class="handle-del mr10"
                    @click="delAllSelection"
            >删除</el-button>
        </div>
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
        </el-tabs>
    </div>
</template>

<script>
    import { fetchData } from '../../api/index';
    export default {
        name: 'Snapshot',
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
                }]
            };
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
              },
                delAllSelection()
                {
                    const length = this.multipleSelection.length;
                    let str = '';
                    this.delList = this.delList.concat(this.multipleSelection);
                    for (let i = 0; i < length; i++) {
                        str += this.multipleSelection[i].name + ' ';
                    }
                    this.$message.error(`删除了${str}`);
                    this.multipleSelection = [];
                }
        },
        //更新未读信息条数
        computed: {
            unreadNum(){
                return this.unread.length;
            }
        }
     };
</script>

<style scoped>
    .handle-box {
        margin-bottom: 20px;
    }

    .handle-select {
        width: 120px;
    }

    .handle-input {
        width: 300px;
        display: inline-block;
    }
    .table {
        width: 100%;
        font-size: 14px;
    }
    .red {
        color: #ff0000;
    }
    .mr10 {
        margin-right: 10px;
    }
    .table-td-thumb {
        display: block;
        margin: auto;
        width: 40px;
        height: 40px;
    }
</style>