<template>
  <div class="page-index">
    <el-row>
      <el-col :span="5">
        <m-menu />
      </el-col>
      <el-col :span="10">222</el-col>
      <el-col :span="24">333</el-col>
    </el-row>
  </div>
</template>
<script>
import mMenu from '@/components/index/menu'
export default {
  components: {
    mMenu
  }
}

</script>
<style lang="scss">
@import "@/assets/css/index/index.scss";

</style>
