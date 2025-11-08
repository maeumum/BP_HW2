<template>
  <div>
    <ChildComponent
        :message="parentMessage"
        @custom-event="handleEvent"
    />
  </div>
</template>

<script>
// 컴포넌트 이름을 명시적으로 정의하는 별도의 스크립트 블록 (E05ParentComponent)
export default {
  name: "E05ParentComponent",
};
</script>

<script setup>
import { ref } from 'vue';
import ChildComponent from './ChildComponent.vue';

const parentMessage = ref('Hello from parent');

const handleEvent = (payload) => {
  console.log(payload);
};

// ChildComponent는 `<script setup>` 내에서 자동으로 등록됩니다.
</script>