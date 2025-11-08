<template>
  <div>
    <ChildComponent1 />
  </div>
</template>

<script>
// 컴포넌트 이름을 명시적으로 정의하는 별도의 스크립트 블록을 추가합니다.
export default {
  name: "E06ParentComponent",
};
</script>

<script setup>
import { provide } from 'vue';
import ChildComponent1 from "@/components/example4/ChildComponent1.vue";

provide('sharedMessage', 'Hello from provide');
</script>