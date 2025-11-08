<template>
  <div>
    <input ref="inputField" type="text" placeholder="Click the button to focus" />
    <button @click="focusInput">Focus Input</button>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const inputField = ref(null); // DOM 요소에 대한 ref 선언

const focusInput = () => {
  // ref를 통해 DOM 요소에 접근할 때 .value 사용
  if (inputField.value) {
    inputField.value.focus();
  }
};

onMounted(() => {
  console.log(inputField.value); // 컴포넌트가 마운트된 후, inputField에 접근 가능
  if(inputField.value) {
    inputField.value.focus(); // 마운트 시 자동 포커스 기능 유지
  }
});

// `<script setup>`에서는 별도로 return 할 필요 없이 자동으로 노출됩니다.
</script>