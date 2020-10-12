<template>
  <a-layout id="components-layout-demo-top-side">
    <a-layout-header class="header">
      <div class="logo" />
      <a-menu
        theme="dark"
        mode="horizontal"
        v-model:selectedKeys="selectedKeys"
        :style="{ lineHeight: '64px' }"
      >
        <a-menu-item key="/">
          <router-link to="/">首页</router-link>
        </a-menu-item>
        <a-menu-item key="/about">
          <router-link to="/about">时间计划</router-link>
        </a-menu-item>
      </a-menu>
    </a-layout-header>
    <a-layout-content style="padding: 0 50px">
      <a-layout style="padding: 24px 0; background: #fff">
        <a-layout-content :style="{ padding: '0 24px', minHeight: '280px' }">
          <a-row>
            <a-col :span="6">
              <a-card
                title="计划总用时是:"
                :bordered="false"
                style="width: 300px"
              >
                <p>总共计划时长是:{{ allTime }}</p>
              </a-card>
            </a-col>
            <a-col :span="18">
              <router-view></router-view>
            </a-col>
          </a-row>

        </a-layout-content>
      </a-layout>
    </a-layout-content>
  </a-layout>
</template>
<script>
import { reactive, toRefs, computed, ref } from "vue";
import { useRoute } from "vue-router";
import { useStore } from "vuex";
export default {
  setup(props, context) {
    // 默认只执行一次
    console.log(props);
    console.log(context);

    const route = useRoute();
    const store = useStore();
    const state = reactive({
      selectedKeys: computed(() => {
        return [route.path];
      }),
      a: 0,
      allTime: ref(store.getters.allTime),
    });

    return {
      ...toRefs(state),
    };
  },
  mounted() {
    console.log("mounted");
  },
};
</script>
<style>
#components-layout-demo-top-side .logo {
  width: 120px;
  height: 31px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px 28px 16px 0;
  float: left;
}
</style>

