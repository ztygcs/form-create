<template>
  <div id="app">
    <FormCreate :config="config" :vModel="vModel"> </FormCreate>
  </div>
</template>

<script>
import FormCreate from './components/FormCreate.vue'
class Form {
  inputNumber = 2
  radio = 4
  checkbox = [3]
}
export default {
  name: 'App',
  components: {
    FormCreate
  },
  data() {
    return {
      vModel: new Form(),
      config: [
        {
          comp: 'input',
          label: '输入框',
          prop: 'input',
          rules: [
            { required: true, message: '请输入活动名称', trigger: 'blur' },
            { min: 1, max: 10, message: '长度最多 10 个字符', trigger: 'blur' }
          ],
          attributes: { type: 'text', maxlength: 10, 'show-word-limit': true, clearable: true },
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
        },
        {
          comp: 'input-number',
          label: '计数框',
          prop: 'inputNumber',
          attributes: {},
          events: {
            blur: (event) => {
              console.log(event)
            },
            focus: (event) => {
              console.log(event)
            },
            change: (currentValue, oldValue) => {
              console.log(currentValue, oldValue)
            }
          }
        },
        {
          comp: 'select',
          label: '选择框',
          prop: 'select',
          attributes: {
            clearable: true,
            multiple: false,
            filterable: true,
            remote: true,
            'remote-method': (val) => {
              console.log(val)
            }
          },
          events: {
            change: (val) => {
              console.log(val)
            },
            'visible-change': (val) => {
              console.log(val)
            },
            'remove-tag': (val) => {
              console.log(val)
            },
            clear: () => {},
            blur: (event) => {
              console.log(event)
            },
            focus: (event) => {
              console.log(event)
            }
          },
          options: [
            { label: '选项1', value: 1 },
            { label: '选项2', value: 2 },
            { label: '选项3', value: 3 },
            { label: '选项4', value: 4 }
          ]
        },
        {
          comp: 'radio',
          label: '单选框',
          prop: 'radio',
          data: [
            { text: '选项1', attributes: { label: 1, disabled: true } },
            { text: '选项2', attributes: { label: 2 } },
            { text: '选项3', attributes: { label: 3 } },
            { text: '选项4', attributes: { label: 4 } }
          ]
        },
        {
          comp: 'checkbox',
          label: '多选框',
          prop: 'checkbox',
          data: [
            { text: '选项1', attributes: { label: 1, disabled: true } },
            { text: '选项2', attributes: { label: 2 } },
            { text: '选项3', attributes: { label: 3 } },
            { text: '选项4', attributes: { label: 4 } }
          ]
        },
        {
          comp: 'switch',
          label: '开关',
          attributes: {
            'active-text': '开',
            'inactive-text': '关'
          },
          events: {
            change: (val) => {
              console.log(val)
            }
          }
        },
        // {
        //   comp: 'slider',
        //   label: 'slider',
        //   prop: 'slider',
        //   attributes: {
        //     range: true,
        //     marks: {
        //       0: '0°C',
        //       8: '8°C',
        //       37: '37°C',
        //       50: {
        //         style: {
        //           color: '#1989FA'
        //         },
        //         label: this.$createElement('strong', '50%')
        //       }
        //     }
        //   }
        // },
        {
          comp: 'time-select',
          label: '时间选择器',
          prop: 'timePicker',
          attributes: { 'picker-options': { start: '08:30', step: '00:15', end: '18:30' }, placeholder: '选择时间' }
        },
        {
          comp: 'date-picker',
          label: '日期选择器',
          prop: 'datePicker',
          attributes: { type: 'date', placeholder: '选择日期' }
        },
        {
          comp: 'date-picker',
          label: '日期范围选择器',
          prop: 'dateRangePicker',
          attributes: {
            type: 'daterange',
            'range-separator': '至',
            'start-placeholder': '开始日期',
            'end-placeholder': '结束日期'
          }
        },
        {
          comp: 'date-picker',
          label: '周选择器',
          prop: 'weekPicker',
          attributes: { type: 'week', format: 'yyyy 第 WW 周', placeholder: '选择周' }
        },
        {
          comp: 'date-picker',
          label: '月选择器',
          prop: 'monthPicker',
          attributes: { type: 'month', placeholder: '选择月' }
        },
        {
          comp: 'date-picker',
          label: '日期时间选择器',
          prop: 'dateTimePicker',
          attributes: { type: 'datetime', placeholder: '选择日期时间' }
        },
        {
          comp: 'color-picker',
          label: '颜色选择器',
          prop: 'colorPicker',
          attributes: {
            'show-alpha': true
          }
        },
        {
          comp: 'button',
          buttonText: '控制台',
          attributes: {},
          callback: () => {
            console.log(this.vModel)
          }
        },
        {
          comp: 'button',
          buttonText: '重置',
          attributes: { type: 'primary' },
          callback: () => {
            this.vModel = new Form()
          }
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped></style>
