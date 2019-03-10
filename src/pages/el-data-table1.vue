<template>
  <div class="data-table">
    <el-data-table v-bind="tableConfig"></el-data-table>
  </div>
</template>

<script>
import url from '../const/api'
import data from '../const/test-data'

export default {
  data() {
    return {
      tableConfig: {
        url,
        data,
        columns: [
          {type: 'selection'},
          {
            prop: 'name',
            label: '组件名称'
          },
          {
            prop: 'type',
            label: '分类'
          },
          {
            prop: 'version',
            label: '版本'
          },
          {
            prop: 'lang',
            label: '开发语言'
          },
          {
            prop: 'updateOn',
            label: '最后更新的时间'
          },
          {
            prop: 'status',
            label: '状态'
          }
        ],
        searchForm: [
          {
            $type: 'input',
            $id: 'name',
            label: '用户名',
            $el: {
              placeholder: '请输入'
            }
          },
          {
            $type: 'select',
            $id: 'type',
            label: '分类',
            $el: {
              placeholder: '请选择'
            }
          },
          {
            $type: 'select',
            $id: 'status',
            label: '状态',
            $el: {
              placeholder: '请选择'
            }
          }
        ],
        form: [
          {
            $type: 'input',
            $id: 'name',
            label: '组件名称',
            $el: {
              placeholder: '请输入'
            },
            rules: [
              {
                required: true,
                message: '请输入组件名',
                trigger: 'blur'
              }
            ]
          },
          {
            $type: 'select',
            $id: 'type',
            label: '分类',
            $el: {
              placeholder: '请选择'
            }
          },
          {
            $type: 'select',
            $id: 'status',
            label: '状态',
            $el: {
              placeholder: '请选择'
            }
          }
        ]
      }
    }
  },
  methods: {}
}
</script>

<style lang="less">
</style>
