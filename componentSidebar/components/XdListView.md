### 列表页面整体布局
<div id="table">
    <el-select v-model="value" placeholder="请选择" size="large" style="margin-bottom:10px;">
    <el-option
      v-for="item in options"
      :key="item.id"
      :label="item.name"
      :value="item.id"
    />
  </el-select>
    <el-button  @click="reset" style="margin:10px;float:right;display:block">重置</el-button>
    <el-button type="primary" @click="search" style="margin:10px;float:right;display:block">查询</el-button>
    <el-table :data="tableData" id="elTable">
        <el-table-column prop="date" label="日期"></el-table-column>
        <el-table-column prop="name" label="姓名"></el-table-column>
        <el-table-column prop="address" label="地址"></el-table-column>
    </el-table>
    <el-pagination background layout="prev, pager, next" :total="tableData.length" style="margin:10px;float:right;display:block"/>
</template>
</div>
<script type="text/javascript">
new Vue({
    el:'#table',
    data:{
        value:'',
        options: [
            {
                id: 'Option1',
                name: '张三',
            },
            {
                id: 'Option2',
                name: '李四',
            }
        ],
        tableData :[
            {
                date: '2016-05-03',
                name: '张三',
                id: 'Option1',
                address: 'No. 189, Grove St, Los Angeles',
            },
            {
                date: '2016-05-02',
                name: '李四',
                id: 'Option2',
                address: 'No. 189, Grove St, Los Angeles',
            }
        ],
        baseData :[
            {
                date: '2016-05-03',
                name: '张三',
                id: 'Option1',
                address: 'No. 189, Grove St, Los Angeles',
            },
            {
                date: '2016-05-02',
                name: '李四',
                id: 'Option2',
                address: 'No. 189, Grove St, Los Angeles',
            }
        ]
    },
    methods:{
        reset() {
            this.value = ''
        },
        search() {
            this.tableData = this.baseData.filter(item=>item.id ===this.value)
        }
    }
})
</script>

### 使用方法
```js
<XdListView 
    :pageInfo="pageInfo"
    @gotoPage="gotoPage" 
    @reset="resetForm"
>
    <template #search>
        <el-input/>
        <el-input class="last"/>
    </template>
    <XdTable></XdTable>
</XdListView>
export default {
    setup() {
        const state = reactive({
            pageInfo: {
                pageNumber: 10,
                pageIndex: 1,
                total: 0
            }
        }) 
       const  gotoPage = (pageNumber, pageIndex)=>{
           api().then((res) => {
              if (result.code === "000000") {
                const { pageNumber, totalCount } = res;
                Object.assign(state.pageInfo, {
                  total: totalCount,
                  pageIndex: pageNumber
                })
              }
            })
       }
    }
}
```

####  属性

| 属性          | 说明                                                         | 类型    | 可选值     | 默认值                                   |
| ------------- | ------------------------------------------------------------ | ------- | ---------- | ---------------------------------------- |
| pageInfo      | pageNumber：每页条目个数<br />pageIndex：当前页<br />total：总数 | object  | ——         | { pageNumber: 10,pageIndex: 1, total: 0} |
| pageSizes     | 每页显示个数选择器的选项设置                                 | array   | ——         | [10, 20, 50, 100]                        |
| isPagination  | 是否展示分页                                                 | boolean | true/false | true                                     |
| isReset       | 是否展示重置按钮                                             | boolean | true/false | true                                     |
| searchBtnName | 查询按钮文本                                                 | string  | ——         | 查询                                     |
| loading       | 查询按钮loading                                              | boolean | true/false | false                                    |
| isMounted     | 是否默认加载onMounted                                        | boolean | true/false | true                                    |


#### 事件

| 事件名   | 说明                                  | 参数                  |
| -------- | ------------------------------------- | --------------------- |
| gotoPage | 查询按钮触发事件，默认onMounted中触发 | pageNumber, pageIndex |
| reset    | 重置按钮事件                          | ——                    |

### 插槽

| 插槽名       | 说明                       |
| ------------ | -------------------------- |
| search       | 搜索区域                   |
| customBtn    | 重置搜索按钮后添加内容区域 |
| operationBtn | 搜索区域和表格之间区域     |

