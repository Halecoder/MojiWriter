<!-- 主页 -->
<template>
    <TitleBlock></TitleBlock>
    <SidebarLeft></SidebarLeft>
    <HomeContent></HomeContent>
    <!-- 主题按钮 -->
    <div class="theme" title="更换主题">
        <a-trigger trigger="click" :popup-translate="[-130, -10]">
            <a-button class="btn" type="primary">
                <template #icon>
                    <icon-skin />
                </template>
            </a-button>
            <template #content>
                <ThemeContainer></ThemeContainer>
            </template>
        </a-trigger>
    </div>
</template>

<script setup lang="ts">
import { useRoute } from 'vue-router';
import TitleBlock from '../components/TitleBlock.vue';
import SidebarLeft from '../components/SidebarLeft.vue';
import HomeContent from '../components/HomeContent.vue';
import ThemeContainer from '../components/widget/ThemeContainer.vue';
import { IconSkin } from "@arco-design/web-vue/es/icon";
import useCurrentInstance from '../utils/useCurrentInstance';

/*----根据路由参数弹出提示信息----*/
const route = useRoute(), { proxy } = useCurrentInstance();
if (route.query.Message) {
    proxy.$message.success(route.query.Message);
}

</script>

<style lang="scss" scoped>
.theme {
    @include theme;
}
</style>