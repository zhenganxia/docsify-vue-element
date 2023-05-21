### 地区联动组件
>地区下拉为省市县默认有全部选项，值为‘all’,
<div id="pagination">
    <el-select v-model="state.modalParams.ownerProvinceCode"  @change="provinceControl"  placeholder="省"  size="large">
        <el-option
            v-for="item in state.provinceList"
            :key="item.id"
            :label="item.name"
            :value="item.id"
            @change="provinceControl()"
    />
    </el-select>
    <el-select v-model="state.modalParams.ownerCityCode"  @change="provinceControl"  placeholder="市"  size="large">
        <el-option
            v-for="item in state.cityList"
            :key="item.id"
            :label="item.name"
            :value="item.id"
            @change="cityControl()"
    />
    </el-select>
     <el-select v-model="state.modalParams.ownerDistrictCode"  @change="provinceControl"  placeholder="区"  size="large">
        <el-option
            v-for="item in state.districtList"
            :key="item.id"
            :label="item.name"
            :value="item.id"
    />
    </el-select>
</div>
<script type="text/javascript">
    new Vue({
        el:'#pagination',
        data(){
            return {
                value:'',
                isAllCity:false,
                isAllProvince:true,
                isAllCity:false,
                isAllDistrict:false,
                state : {
                    loading:false,
                    districtLoading:false,
                    provinceList:[
                        {
                            id: 1,
                            name: '河北',
                        }
                    ],
                    cityList:[],
                    districtList:[],
                    modalParams:{
                        ownerProvinceCode:undefined,
                        ownerCityCode:undefined,
                        ownerDistrictCode:undefined
                    }
                }
            }
        },
        methods:{
        provinceControl (id=1) {
            if(id===1) {
                setTimeout(()=>{
                     this.state.cityList = [
                    {
                        name:'保定',
                        id:3
                    }
                ]
                 this.state.districtList = [
                    {
                        name:'衡水',
                        id:8
                    }
                ]
                },0)
            }
        },
        cityControl() {}
    }
    })
</script>

### 使用方法
```js
<XdArea v-model="ruleForm.ownerProvinceCode"></XdArea>
```

| 属性          | 说明                   | 类型    | 可选值     | 默认值                                |
| ------------- | ---------------------- | ------- | ---------- | ------------------------------------- |
| isAllDistrict | 是否展示区下拉框中全部 | boolean | true/false | true                                  |
| isAllCity     | 是否展示市下拉框中全部 | boolean | true/false | true                                  |
| isAllProvince | 是否展示省下拉框中全部 | boolean | true/false | true                                  |
| defaultStyle  | 设置下拉样式           | object  | ——         | {width: '150px',marginRight: '10px',} |

