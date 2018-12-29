<template>
  <el-scrollbar wrap-class="scrollbar-wrapper" style="box-shadow: rgb(0, 0, 0) 0px 0px 7px 0px;">
    <div class="logo">111</div>
    <el-menu
      :show-timeout="200"
      :default-active="$route.path"
      :collapse="isCollapse"
      mode="vertical"
      background-color="#304156"
      text-color="#bfcbd9"
      active-text-color="#409EFF"
    >
      <sidebar-item
        v-for="route in permission_routers"
        :key="route.path"
        :item="route"
        :base-path="route.path"
      />
    </el-menu>
  </el-scrollbar>
</template>

<script>
import { mapGetters } from 'vuex'
import SidebarItem from './SidebarItem'

export default {
  components: { SidebarItem },
  computed: {
    ...mapGetters(['permission_routers', 'sidebar']),
    isCollapse() {
      return !this.sidebar.opened
    }
  },
  mounted: function() {
    console.log(this.$store.getters)
    console.log(this.permission_routers)
  }
}
</script>
<style scoped>
.logo{
  width:100%;
  height:80px;
}
</style>
