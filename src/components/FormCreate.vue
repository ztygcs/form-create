<template>
  <div class="main">
    <el-card shadow="always">
      <el-form :model="vModel" :label-width="labelWidth" :inline="inline">
        <template v-for="item in config">
          <!-- 按钮 -->
          <template v-if="item.comp === 'button'">
            <el-form-item :key="item.prop">
              <el-button v-bind="item.attributes" @click="item.callback()">
                {{ item.buttonText }}
              </el-button>
            </el-form-item>
          </template>
          <!-- 其他表单项 -->
          <template v-else>
            <el-form-item :key="item.prop" :label="item.label" :prop="item.prop" :rules="item.rules">
              <!-- 选择框 -->
              <template v-if="item.comp === 'select'">
                <el-select v-model="vModel[item.prop]" v-bind="item.attributes" v-on="item.events">
                  <el-option
                    v-for="optionItem in item.options"
                    :key="optionItem.value"
                    :label="optionItem.label"
                    :value="optionItem.value"
                  ></el-option>
                </el-select>
              </template>
              <!-- 单选框 -->
              <template v-else-if="item.comp === 'radio'">
                <el-radio
                  v-for="radioItem in item.data"
                  :key="radioItem.label"
                  v-model="vModel[item.prop]"
                  v-bind="radioItem.attributes"
                >
                  {{ radioItem.text }}
                </el-radio>
              </template>
              <!-- 多选框 -->
              <template v-else-if="item.comp === 'checkbox'">
                <el-checkbox-group v-model="vModel[item.prop]">
                  <el-checkbox
                    v-for="checkboxItem in item.data"
                    :key="checkboxItem.label"
                    v-bind="checkboxItem.attributes"
                  >
                    {{ checkboxItem.text }}
                  </el-checkbox>
                </el-checkbox-group>
              </template>
              <!-- el-input、el-input-number、el-switch、el-slider、el-time-select、el-date-picker -->
              <template v-else>
                <component
                  v-bind:is="`el-${item.comp}`"
                  v-model="vModel[item.prop]"
                  v-bind="item.attributes"
                  v-on="item.events"
                ></component>
              </template>
            </el-form-item>
          </template>
        </template>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'FormCreate',
  props: {
    config: { type: Array, default: () => [] },
    vModel: { type: Object, default: () => ({}) },
    labelWidth: { type: String, default: '110px' },
    inline: { type: Boolean, default: false }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main {
  .el-input {
    width: 220px;
  }
}
</style>
