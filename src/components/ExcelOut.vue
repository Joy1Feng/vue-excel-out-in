<template>
    <div>
        <table>
            <thead>
                <tr>
                    <td>姓名</td>
                    <td>性别</td>
                    <td>年龄</td>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, index) in tabList" :key="index">
                    <td>{{item.name}}</td>
                    <td>{{item.gender}}</td>
                    <td>{{item.age}}</td>
                </tr>
            </tbody>
        </table>
        <input type="text" v-model="filename" placeholder="请输入导出的名字">
        <button @click="excelDow">导出</button>
    </div>
</template>

<script>
    export default {
        name: "ExcelOut",
        data() {
            return {
                tabList: [
                    {name: '张三', gender: '男', age: 23},
                    {name: '李四', gender: '男', age: 24},
                    {name: 'tom', gender: '男', age: 21},
                ],
                autoWidth: true,
                bookType: 'xls',
                filename: ''
            }
        },
        methods: {
            excelDow() {
                import('../vendor/Export2Excel.js').then(moudle => {
                    const tHeader = ['姓名', '性别', '年龄']  // 自定义表头
                    const filterVal = Object.keys(this.tabList[0])  // 获得键名
                    const list = this.tabList
                    const data = this.formatJson(filterVal, list)
                    moudle.export_json_to_excel({
                        header: tHeader,
                        data,
                        filename: this.filename === '' ? 'filename' : this.filename,
                        autoWidth: this.autoWidth,
                        bookType: this.bookType
                    })
                })
            },
            formatJson(filterVal, jsonData) {
                return jsonData.map(v => filterVal.map(j => v[j]))
            }
        }
    }
</script>

<style scoped>
    table{
        border-collapse: collapse;
        margin: 0 auto;
    }
    th, td{
        border: 1px solid red;
        width: 80px;
        height: 30px;
    }
</style>
