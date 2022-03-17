<template>
  <el-input
      v-model="textarea"
      :rows="2"
      type="textarea"
      placeholder="Please input"
  />
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>
