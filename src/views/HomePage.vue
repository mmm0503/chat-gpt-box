<script setup lang="ts">
import {nextTick, ref} from "vue";
import SideBarBlock from "@/components/sidebar/SideBarBlock.vue";
import ChatContentBlock from "@/components/chat/block/ChatContentBlock.vue";
import {ChatInfo} from "@/types/Store.ts";

const chatContentBlockRefs = ref<InstanceType<typeof ChatContentBlock> | null>(null);
const changeChatClick = (chatInfo: ChatInfo) => {
  nextTick(() => {
    if (!chatContentBlockRefs.value) return;
    chatContentBlockRefs.value.changeChat(chatInfo);
  });
};
</script>

<template>
  <div class="w-full h-full flex flex-row box-border">
    <SideBarBlock class="hidden 3xl:flex" @changeChatClick="changeChatClick"/>
    <ChatContentBlock class="flex-1" ref="chatContentBlockRefs"/>
  </div>
</template>
