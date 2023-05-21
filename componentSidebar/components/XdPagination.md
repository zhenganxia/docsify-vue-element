### 分页
>内置element-pagination所有属性和方法，参考element-pagination使用方法
<div id="pagination">
    <el-pagination background layout="prev, pager, next" :total="1000" />
</div>
<script type="text/javascript">
    new Vue({
        el:'#pagination'
    })
</script>

### 使用方法
```js
 <XdPagination
  :pageInfo="pageInfo"
  :pageSizes="pageSizes"
   @change="changePage"
/>
export default {
    setup() {
        const state = reactive({
            pageInfo: {
                pageNumber: 10,
                pageIndex: 1,
                total: 0
            },
            pageSizes:[10, 20, 50, 100]
        }) 
        const changePage = (val) => {
            // val 更改的pageNumber,pageIndex
        };
    }
}
```

### 属性

| 属性      | 说明                                                         | 类型   | 可选值 | 默认值                                   |
| --------- | ------------------------------------------------------------ | ------ | ------ | ---------------------------------------- |
| pageSizes | 每页显示个数选择器的选项设置                                 | array  | ——     | [10, 20, 50, 100]                        |
| pageInfo  | pageNumber：每页条目个数<br />pageIndex：当前页<br />total：总数 | object | ——     | { pageNumber: 10,pageIndex: 1, total: 0} |

### 事件

| 事件名 | 说明                | 参数 |
| ------ | ------------------- | ---- |
| change | 页码/当前页更改触发 | ——   |

