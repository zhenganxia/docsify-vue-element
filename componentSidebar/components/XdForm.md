## 表单
>支持element-plus属性和方法
<div id="form">
   <el-form :model="form" label-width="120px">
    <el-form-item label="Activity name">
      <el-input v-model="form.name" />
    </el-form-item>
    <el-form-item label="Activity zone">
      <el-select v-model="form.region" placeholder="please select your zone">
        <el-option label="Zone one" value="shanghai" />
        <el-option label="Zone two" value="beijing" />
      </el-select>
    </el-form-item>
    <el-form-item label="Activity time">
      <el-col :span="11">
        <el-date-picker
          v-model="form.date1"
          type="date"
          placeholder="Pick a date"
          style="width: 100%"
        />
      </el-col>
      <el-col :span="2" class="text-center">
        <span class="text-gray-500">-</span>
      </el-col>
      <el-col :span="11">
        <el-time-picker
          v-model="form.date2"
          placeholder="Pick a time"
          style="width: 100%"
        />
      </el-col>
    </el-form-item>
    <el-form-item label="Instant delivery">
      <el-switch v-model="form.delivery" />
    </el-form-item>
    <el-form-item label="Activity type">
      <el-checkbox-group v-model="form.type">
        <el-checkbox label="Online activities" name="type" />
        <el-checkbox label="Promotion activities" name="type" />
        <el-checkbox label="Offline activities" name="type" />
        <el-checkbox label="Simple brand exposure" name="type" />
      </el-checkbox-group>
    </el-form-item>
    <el-form-item label="Resources">
      <el-radio-group v-model="form.resource">
        <el-radio label="Sponsor" />
        <el-radio label="Venue" />
      </el-radio-group>
    </el-form-item>
    <el-form-item label="Activity form">
      <el-input v-model="form.desc" type="textarea" />
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="onSubmit">Create</el-button>
      <el-button @click="cancel">cancel</el-button>
    </el-form-item>
  </el-form>
</div>
<script type="text/javascript">
    new Vue({
        el:'#form',
        data(){
            return {
              form:{
                name: '',
                region: '',
                date1: '',
                date2: '',
                delivery: false,
                type: [],
                resource: '',
                desc: '',
              }
            }
        },
        methods:{
          onSubmit() {
            alert('是否提交')
          },
          cancel() {
            alert('取消成功')
          }
        }
    })
</script>

### 使用方法
```js
<XdForm
    :formItemData="formItemData" 
    ref="formRef" 
    :formRules="formRules" 
    @submitForm="submitForm"
    v-model="formData"
    labelWidth="150"
  > 
  <template #custom>
    <el-button>除保存、重置以外自定义按钮,isText为true不展示</el-button>
  </template>
</XdForm>

export default {
    setup() {
     const validatorTimeTask = (rule, value, callback) => {
          if (!formRef.value.ruleForm.region) {
            callback(new Error("请选择任务有效性"));
          } else {
            callback();
          }
        };
        let state = reactive({
            formData:{}, // 表单绑定参数，回显需要更改这里
            formItemData: [
                {
                  key: "name",
                  formLabel: "Activity name", // 没有type默认为el-input
                },
                {
                  key: "region", // 需要保存参数
                  formLabel: "Activity zone",
                  type: "xd-select", // 需要渲染的组件-这里是自定义全局组件
                  props: { // 这里属性和element-plus  el-select属性保持一致
                    options: [
                      {
                        name: "lili",
                        id: 1
                      },
                      {
                        name: "liming",
                        id: 2
                      }
                    ]
                  }
                }
              ],
              formRules: {
                name: [
                  {
                    min: 3,
                    max: 5,
                    message: "Length should be 3 to 5",
                    trigger: ["blur", "change"]
                  }
                ],
                region: [
                  {
                    required: "true",
                    validator: validatorTimeTask, // 自定义校验
                    trigger: ["change"]
                  }
                ]
              }
            })
    }
}
```

### 属性

| 属性         | 说明                        | 类型          | 可选值 | 默认值                      |
| ------------ | --------------------------- | ------------- | ------ | --------------------------- |
| formItemData | 需要渲染的from-item数据结构 | array         | ——     | ——                          |
| formRules    | 校验规则-支持自定义校验     | object        | ——     | ——                          |
| labelWidth   | 当前form label-width        | number        | ——     | 120                         |
| isSubmit     | 是否展示保存按钮            | boolean       | ——     | true                        |
| isReset      | 是否展示重置按钮            | boolean       | ——     | false                       |
| isText       | 表格是否展示文本格式        | boolean       | ——     | false                       |
| resetText    | 重置按钮文本                | string        | ——     | 重置                        |
| submitText   | 保存按钮文本                | string        | ——     | 保存                        |
| layout       | 默认响应式布局              | object        | ——     | {xs:12,sn:6,md:8,lg:8,xl:6} |
| span         | 手动控制布局                | number/string | ——     | ——                          |
| labelWidth   | form-item  label宽度        | number/string | ——     | 80                          |

### formItemData 属性

| 属性      | 说明                                                 | 类型   | 可选值 | 默认值   |
| --------- | ---------------------------------------------------- | ------ | ------ | -------- |
| key       | 对应保存参数                                         | string | ——     | ——       |
| formLabel | 展示label                                            | string | ——     | ——       |
| type      | 当前form-item需要渲染成的组件类型                    | string | ——     | el-input |
| props     | 当前type对应类型需要属性（element-plus属性保持一致） | object | ——     | ——       |



### 方法

### 插槽

| 插槽名 | 说明           |
| ------ | -------------- |
| custom | 自定义按钮区域 |



### 备注：1.支持element-plus所有属性方法 2.placeholder如果值为空，有默认值 3. 两种格式：表格和文本格式