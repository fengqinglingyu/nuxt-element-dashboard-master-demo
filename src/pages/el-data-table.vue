<template>
  <div class="data-table">
    <el-data-table v-bind="tableConfig"></el-data-table>
  </div>
</template>

<script>
import {formatDate} from '../const/filter'

export default {
  data() {
    const url =
      'https://easy-mock.com/mock/5b586c9dfce1393a862d034d/example/img'
    const columns = [
      {type: 'selection'},
      {prop: 'code', label: '品牌编号'},
      {prop: 'name', label: '品牌名称'},
      {prop: 'alias', label: '品牌别名'},
      {
        prop: 'logoUrl',
        label: '品牌Logo',
        width: '150px'
      },
      {
        prop: 'updatedAt',
        label: '更新时间',
        formatter: row => formatDate(row.updatedAt, 'YYYY-MM-DD')
      },
      {
        prop: 'status',
        label: '状态',
        formatter: row => {
          if (row.status === 'normal') {
            return <span style="color: #52c41a">启用</span>
          }
          return <span style="color: red">禁用</span>
        }
      }
    ]
    const searchForm = [
      {
        $type: 'input',
        $id: 'name',
        label: '品牌名称',
        $el: {
          placeholder: '请输入'
        }
      },
      {
        $type: 'input',
        $id: 'alias',
        label: '品牌别名',
        $el: {
          placeholder: '请选择'
        }
      },
      {
        $type: 'select',
        $id: 'status',
        label: '状态',
        $options: [
          {label: '启用', value: 'normal'},
          {label: '禁用', value: 'forbidden'}
        ].map(v => ({label: v.label, value: v.value})),
        $el: {
          placeholder: '请选择'
        }
      }
    ]
    const form = [
      {
        $type: 'input',
        $id: 'name',
        label: '品牌名称',
        $el: {
          placeholder: '请输入'
        },
        rules: [
          {
            required: true,
            message: '请输入品牌名称',
            trigger: 'blur'
          }
        ]
      },
      {
        $type: 'input',
        $id: 'alias',
        label: '品牌别名',
        $el: {
          placeholder: '请选择'
        }
      },
      {
        $type: 'select',
        $id: 'status',
        label: '状态',
        $options: [
          {label: '启用', value: 'normal'},
          {label: '禁用', value: 'forbidden'}
        ].map(v => ({label: v.label, value: v.value})),
        $el: {
          placeholder: '请选择'
        }
      }
    ]
    const extraButtons = [
      {
        type: 'danger',
        text: '禁止',
        // row 是单行的数据
        show: row => row.status === 'normal',
        atClick: row => {
          alert('查看' + row.code)
          return Promise.resolve()
        }
      },
      {
        type: 'success',
        text: '启用',
        // row 是单行的数据
        show: row => row.status !== 'normal',
        atClick: row => {
          alert('查看' + row.code)
          return Promise.resolve()
        }
      }
    ]
    return {
      tableConfig: {
        url,
        columns,
        searchForm,
        form,
        hasView: true,
        extraButtons
      }
    }
  },
  methods: {}
}
</script>

<style lang="less">
</style>
