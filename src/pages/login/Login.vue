<template>
  <div>Login</div>
</template>

<script lang="ts">
  import { defineComponent, reactive, toRefs, onMounted } from 'vue'

  interface DataProps {}

  export default defineComponent({
    name: 'LoginPage',
    setup() {
      const data: DataProps = reactive({})
      onMounted(() => {
        console.log('组件挂载到页面之后执行-------onMounted')
      })
      const refData = toRefs(data)
      return {
        ...refData
      }
    }
  })
</script>

<style lang="scss" scoped></style>
