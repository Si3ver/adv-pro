<template>
  <div>
    <a-drawer title="Info" placement="right" :closable="false" @close="onClose" :visible="visible" width="300px">
      <template v-slot:handle>
        <div class="handle" @click="visible = !visible">
          <a-icon :type="visible ? 'close' : 'setting'" />
        </div>
      </template>
      <h2>整体风格定制</h2>
      <a-radio-group
        :value="$route.query.navTheme || 'dark'"
        @change="e => handleSettingChange('navTheme', e.target.value)"
      >
        <a-radio value="dark">深色</a-radio>
        <a-radio value="light">浅色</a-radio>
      </a-radio-group>
      <h2>导航模式</h2>
      <a-radio-group
        :value="$route.query.navLayout || 'left'"
        @change="e => handleSettingChange('navLayout', e.target.value)"
      >
        <a-radio value="left">左侧</a-radio>
        <a-radio value="top">顶部</a-radio>
      </a-radio-group>
    </a-drawer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      visible: false
    };
  },
  methods: {
    onClose() {
      this.visible = false;
    },
    handleSettingChange(type, value) {
      console.log(type, value);
      this.$router.push({ query: { ...this.$route.query, [type]: value } });
    }
  }
};
</script>

<style lang="less" scoped>
.handle {
  position: absolute;
  top: 240px;
  right: 300px;
  width: 48px;
  height: 48px;
  background: #1890ff;
  color: #fff;
  font-size: 20px;
  text-align: center;
  line-height: 48px;
  border-radius: 3px 0 0 3px;
}
</style>
