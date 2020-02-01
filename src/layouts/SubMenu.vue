<template functional>
  <a-sub-menu :key="props.menuInfo.path">
    <span slot="title">
      <a-icon v-if="props.menuInfo.meta.icon" :type="props.menuInfo.meta.icon" />
      <span>{{ props.menuInfo.meta.title }}</span>
    </span>
    <template v-for="item in props.menuInfo.children">
      <a-menu-item
        v-if="!item.children"
        :key="item.path"
        @click="
          () => {
            parent.$router.push({ path: item.path, query: parent.$route.query }).catch(err => {
              /* [BUGFIX] 
                处理重复点击同一路由的问题
                参考：https://stackoverflow.com/questions/57837758/navigationduplicated-navigating-to-current-location-search-is-not-allowed */
              if (err.name !== 'NavigationDuplicated') {
                throw err;
              }
            });
          }
        "
      >
        <a-icon v-if="item.meta.icon" :type="item.meta.icon" />
        <span>{{ item.meta.title }}</span>
      </a-menu-item>
      <sub-menu v-else :key="item.path" :menu-info="item" />
    </template>
  </a-sub-menu>
</template>

<script>
export default {
  props: {
    menuInfo: Object
  }
};
</script>
