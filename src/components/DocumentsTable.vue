<script setup>
import { defineAsyncComponent } from 'vue'
import DBtnDropdown from '@/components/DBtnDropdown.vue'

const rows = [
  {
    name: 'Annual Report',
    file: 'PDF',
    category: 'Property',
    author: 'Diana Mathews',
    status: 'Send'
  },
  {
    name: 'Business Plan',
    file: 'WORD',
    category: 'Cryptocurrency',
    author: 'Philip James',
    status: 'Send'
  },
  {
    name: 'Marketing Tool',
    file: 'PDF',
    category: 'Content Creator',
    author: 'Amanda Rose',
    status: 'Pending'
  }
]

const columns = [
  {
    name: 'name',
    label: 'Name'
  },
  {
    name: 'file',
    label: 'File'
  },
  {
    name: 'category',
    label: 'Category'
  },
  {
    name: 'author',
    label: 'Author'
  },
  {
    name: 'status',
    label: 'Status',
    style: 'opacity: 0.5',
    component: defineAsyncComponent(() => import('./DChip.vue')),
    componentProps: (row) => {
      return {
        label: row.status
      }
    }
  }
]

function getComponentProps(column, row) {
  const componentProps = { row }
  if (typeof column.componentProps === 'function') {
    Object.assign(componentProps, column.componentProps(row))
  } else if (column.componentProps) {
    Object.assign(componentProps, column.componentProps)
  }
  return componentProps
}
</script>

<template>
  <div class="table-wrapper rounded column">
    <div class="row justify-between items-center mb-4 w-full" >
      <div class="">
        <h3>Document</h3>
        <small>Document tracking information</small>
      </div>

      <DBtnDropdown label="Weekly">
        <div class="p-2 column">
          <div class="cursor-pointer p-1">Daily</div>
          <div class="cursor-pointer p-1">Monthly</div>
          <div class="cursor-pointer p-1">Yearly</div>
        </div>
      </DBtnDropdown>
    </div>

    <div class="w-full overflow-auto">
      <table class="table">
        <thead>
          <tr>
            <th
              v-for="column in columns"
              :key="'column-' + column.name"
              class="text-start"
              :class="column.class"
              :style="column.style"
            >
              {{ column.label }}
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(row, i) in rows" :key="i">
            <td v-for="column in columns" :key="`row-${i}-${column.name}`" class="text-start">
              <template v-if="column.component">
                <component :is="column.component" v-bind="getComponentProps(column, row)" />
              </template>
              <template v-else>
                {{ row[column.name] }}
              </template>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style lang="scss">
.table-wrapper {
  padding: 1rem;
  background-color: white;

  h3 {
    font-weight: 600;
  }

  small {
    color: gray;
  }

  table {
    th {
      font-weight: bold;
      padding: 0.5rem;
    }

    tbody {
      td {
        font-weight: 500;
        font-size: 14px;
        padding: 0.5rem;
        width: auto;
        position: relative;
      }
    }
  }
}
</style>
