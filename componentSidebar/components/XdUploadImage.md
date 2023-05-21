### 上传图片
<div id="pagination">
     <el-upload action="#" list-type="picture-card" :auto-upload="false">
      <i class="el-icon-plus"></i>
    <template #file="{ file }">
      <div>
        <img class="el-upload-list__item-thumbnail" :src="file.url" alt="" />
        <span class="el-upload-list__item-actions">
          <span
            class="el-upload-list__item-preview"
            @click="handlePictureCardPreview(file)"
          >
            <el-icon><zoom-in /></el-icon>
          </span>
          <span
            v-if="!disabled"
            class="el-upload-list__item-delete"
            @click="handleDownload(file)"
          >
            <el-icon><Download /></el-icon>
          </span>
          <span
            v-if="!disabled"
            class="el-upload-list__item-delete"
            @click="handleRemove(file)"
          >
            <el-icon><Delete /></el-icon>
          </span>
        </span>
      </div>
    </template>
  </el-upload>

  <el-dialog v-model="dialogVisible">
    <img w-full :src="dialogImageUrl" alt="Preview Image" />
  </el-dialog>
</template>
</div>
<script type="text/javascript">
    new Vue({
        el:'#pagination',
        data(){
            return {
                dialogImageUrl :'',
                dialogVisible :false,
                disabled:false
                // options: [
                //     {
                //         id: 'Option1',
                //         name: 'Option1',
                //     },
                //     {
                //         id: 'Option2',
                //         name: 'Option2',
                //     }
                // ] 
            }
        }
    })
</script>

### 使用方法
```vue
<XdUploadImage
  @getData="updateDataCategoryUrl"
  :imageStyle="{
    width: 120,
    height: 120,
    unValidate:true
  }"
  :imageUrl="imageUrl"
/>
```

```js
export default {
    setup() {
        const state = reactive({
            imageUrl: []
        }) 
       const  updateDataCategoryUrl = ()=>{
          // 处理图片逻辑
       }
    }
}
```

### 属性

| 属性       | 说明               | 类型    | 可选值     | 默认值               |
| ---------- | ------------------ | ------- | ---------- | -------------------- |
| multiple   | 是否上传多张       | boolean | true/false | false                |
| imageStyle | 自定义图片宽高     | object  | ——         | {width:80,height:80} |
| iconText   | 上传图标下文字展示 | string  | ——         | ——                   |
| imageUrl   | 回显图片集合       | array   | ——         | ——                   |
| unValidate | 是否校验图片宽高   | boolean | true/false | true                 |
| limitSize  | 图片大小           | number  | ——         | 5                    |
| disabled   | 不可操作图片       | boolean | true/false | false                |
| title      | 放大图片标题       | string  | ——         | ——                   |
| imageLimit | 图片限制上传数量   | number  | ——         | 1                    |
| isBig      | 不展示放大图标     | boolean | true/false | true                 |

### 事件

| 事件名  | 说明       | 参数 |
| ------- | ---------- | ---- |
| getData | 上传成功图 | ——   |

### 备注：现在功能比较单一，如果有其他需求请根据需求添加