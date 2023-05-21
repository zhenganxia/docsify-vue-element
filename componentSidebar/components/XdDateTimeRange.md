### 时间
>+ 支持element-plus属性和方法
>+ 默认为当前时间为开始时间，想要定义其他开始时间请定义customTime
>+ 支持element自带属性和方法
>+ 初始化回显范围时间
<div id="picker">
    <el-date-picker v-model="datePicker" type="datetimerange" placeholder="请选择时间：" style="width: 100%"
  value-format="YYYY-MM-DD HH:mm:ss" :default-time="defaultTime"
  :unlink-panels="true" />
</div>
<script type="text/javascript">
new Vue({
    el:'#picker',
    data:{
      datePicker:'',
        defaultTime : []
    }
})
</script>

### 使用方法
```js
 <xd-date-time-range
    v-model="createDateForm"
    :month="3"
    style="width: 400px"
    :clearable="false"
  />
```

| 属性          | 说明                                            | 类型          | 可选值     | 默认值 |
| ------------- | ----------------------------------------------- | ------------- | ---------- | ------ |
| month         | 按照月处理时间（负数-之前的时间 正数-之后时间） | number/string | ——         | ——     |
| day           | 按照天处理时间（负数-之前的时间 正数-之后时间   | number/string | ——         | ——     |
| isRangeDisabled | 范围外时间是否置灰                              | boolean       | true/false | false   |
| isDefaultTime | 初始化是否有回显时间                            | boolean       | true/false | true   |
| customTime    | 自定义基准时间                                  | string        | ——         | ——     |
