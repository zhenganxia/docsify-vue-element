### 表格
>+ 支持插槽渲染和render两种方式 
>+ 支持element-plus属性和方法
<div id="table">
    <el-table :data="tableData" id="elTable">
        <el-table-column prop="date" label="日期"></el-table-column>
        <el-table-column prop="name" label="姓名"></el-table-column>
        <el-table-column prop="address" label="地址"></el-table-column>
  </el-table>
</template>
</div>
<script type="text/javascript">
new Vue({
    el:'#table',
    data:{
        tableData :[
            {
                date: '2016-05-03',
                name: '张三',
                address: 'No. 189, Grove St, Los Angeles',
            },
            {
                date: '2016-05-02',
                name: '李四',
                address: 'No. 189, Grove St, Los Angeles',
            },
            {
                date: '2016-05-04',
                name: '王五',
                address: 'No. 189, Grove St, Los Angeles',
            },
            {
                date: '2016-05-01',
                name: '白色',
                address: 'No. 189, Grove St, Los Angeles',
            },
        ]
    },
})
</script>

### 使用方法
```js
<XdTable
    :tableData="tableData"
    :columns="columns"
    border
    :row-class-name="tableRowClassName"
  > 
    <template #enterpriseId-header><el-icon><plus /></el-icon></template>
    <template #enterpriseId="{ row ,index}">
          {{ row.name }} 
    </template>
     <template #action="{ row }">
       <el-button>查看</el-button>
    </template>
</XdTable>
import {h} from 'vue'
export default {
    setup() {
        let state = reactive({
            tableData:[
                {name:'lili',age:'18',projectNumber:'projectNumber'}
            ],
            columns: [
                {
                  label: "企业",
                  key: "name",
                  slot: "name",
                },
                 {
                  label: "图片",
                  key: "url",
                  isImage: true // 渲染图片
                },
                {
                  label: "关联权益项数量",
                  key: "projectNumber",
                  minWidth: 200,
                  render: (params) => {
                    return h(
                      "div",
                      {
                        style: {
                          height: "20px",
                          cursor: "pointer",
                        },
                        onClick: () => {
                          event(params.row);
                        },
                      },
                      params.row.projectNumber
                    );
                  },
                },
                {
                  label: "操作",
                  fixed: "right",
                  align: "center",
                  slot: "action",
                }
            ]
        })
        const event = (row)=>{
            // 处理事件
        },
        const tableRowClassName = ({
          row,
        }) => {
          if (true) {
            // 条件
            return 'ignore-elements'
          }
          return ''
        }
    }
}
```

### 属性

| 属性         | 说明                                                      | 类型   | 可选值                     | 默认值 |
| ------------ | --------------------------------------------------------- | ------ | -------------------------- | ------ |
| tableData    | 表格数据                                                  | array  | ——                         | ——     |
| columns      | 表头数据                                                  | array  | ——                         | ——     |
| animation    | 表格拖拽过渡                                              | number | ——                         | 100    |
| handle       | 表格拖拽标识（拖拽表格父级加class要和handle传参保持一致） | string | ——                         | ——     |
| type         | 对应列的类型                                              | string | selection / index / expand | ——     |
| columnsAlign | 对齐方式                                                  | string | left / center / right      | center |
| dragDateDisabled | 禁止拖拽数据信息| object | { name:'' ,// 禁止拖拽参数-用回退数据valid:'' //禁用值 } |  ——   |
| dragDate | 拖拽数据| object | —— |  ——   |

### column-内置属性

| 属性           | 说明                     | 类型             | 可选值                  | 默认值 |
| -------------- | ------------------------ | ---------------- | ----------------------- | ------ |
| render         | render函数               | function         | ——                      | ——     |
| width/minWidth | 宽度                     | number           | ——                      | ——     |
| fixed          | 列是否固定在左侧或者右侧 | string / boolean | true / 'left' / 'right' | ——     |
| isImage        | 是否渲染图片             | boolean          | true/false              | ——     |
| isLink         | 渲染链接                 | boolean          | true/false              | ——     |
| tooltip        | 文字提示                 | boolean          | true/false              | ——     |
| sortable       | 对应列是否可以排序       | boolean / string | true / false / 'custom' | ——     |

### 事件

| 事件名 | 说明                | 参数 |
| ------ | ------------------- | ---- |
| onFilter | 拖拽禁用数据触发方法（列表行需要加类.ignore-elements） | ——   |
| dragEnd | 拖拽结束触发方法 | ——   |
### 插槽

| 插槽名 | 说明                                   |
| ------ | -------------------------------------- |
| header | 自定义表头的内容（\#当前列key-header） |



### 备注：支持插槽渲染和render两种方式