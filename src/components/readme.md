# 自定义表单生成组件

## 基础用法

```html
<FormCreate :config="config" :vModel="vModel"> </FormCreate>
```

```js
data() {
    return {
      vModel: {},
      config: [
        {
          comp: 'input',
          label: '输入框',
          prop: 'input',
          rules: [
            { required: true, message: '请输入活动名称', trigger: 'blur' },
            { min: 1, max: 10, message: '长度最多 10 个字符', trigger: 'blur' }
          ],
          attributes: { type: 'text', maxlength: 10, 'show-word-limit': true },
          events: {
            blur: (event) => {
              console.log(event)
            },
            focus: (event) => {
              console.log(event)
            },
            change: (value) => {
              console.log(value)
            },
            input: (value) => {
              console.log(value)
            },
            clear: () => {
              console.log('clear')
            }
          }
        }
      ]
    }
  }
```

## 说明

> vModel 为表单数据绑定对象，config 用于配置表单项；
> vModel 对象为 config 数组每一项元素 prop 字段对应值的集合；
> config 数组中的每一项元素对应表单的每一项表单内容，comp 字段：定义哪种表单组件（用于前端判断条件渲染，例'input'渲染为'el-input'），prop 字段：与后端同步字段名（用于与后端交互），rules：表单校验数组，attributes：属性对象，添加的每一项内容会通过 v-bind（:xxx="xxx"） 绑定到对应的表单组件上，events：事件对象，添加的每一项内容会通过 v-on（@xxx="xxx"）绑定到对应的组件上。 具体的属性和事件配置项参考[element-ui](https://element.eleme.cn/#/zh-CN)官网

|    字段    |  类型  |                                     说明                                     |
| :--------: | :----: | :--------------------------------------------------------------------------: |
|   label    | String |                               表单前的标签                               |
|    comp    | String |     定义哪种表单组件（用于前端判断条件渲染，例'input'渲染为'el-input'）      |
|    prop    | String |                      与后端同步字段名（用于与后端交互）                      |
|   rules    | Array  |                                 表单校验数组                                 |
| attributes | Object | 属性对象，添加的每一项内容会通过 v-bind（:xxx="xxx"） 绑定到对应的表单组件上 |
|   events   | Object |    事件对象，添加的每一项内容会通过 v-on（@xxx="xxx"）绑定到对应的表单组件上     |
