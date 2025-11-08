# Vue2 to Vue3 Migration Demo

Vue 2 Options API 기반 코드를 Vue 3 Composition API로 전환한 프로젝트입니다.

## 📋 프로젝트 개요

이 프로젝트는 Vue 2의 Options API로 작성된 예제들을 Vue 3의 Composition API (`<script setup>`)로 마이그레이션하여 동일한 동작을 유지하면서 최신 Vue 3 스타일로 리팩터링한 결과물입니다.

## 🚀 시작하기

### 설치
```bash
npm install
```

### 개발 서버 실행
```bash
npm run serve
```

### 프로덕션 빌드
```bash
npm run build
```

### 린트 및 수정
```bash
npm run lint
```

## 📝 마이그레이션 변경 내용

### 주요 변환 요소

| Vue 2 Options API | Vue 3 Composition API |
|-------------------|----------------------|
| `data()` | `ref()`, `reactive()` |
| `computed` | `computed()` |
| `methods` | 일반 함수 |
| `mounted`, `created` 등 | `onMounted()`, `onBeforeMount()` 등 |
| `props` | `defineProps()` |
| `$emit` | `defineEmits()` |
| `provide/inject` | `provide()`, `inject()` |

### 예제별 상세 변경 사항

#### **E-01 ~ E-04: 기본 반응성 및 바인딩**
- **파일**: `example1`, `example2`
- **변경 내용**:
    - `data()` → `ref()`, `reactive()`
    - `computed` 옵션 → `computed()` 함수
    - `mounted` 훅 → `onMounted()` 함수
    - 모든 코드를 `<script setup>` 문법으로 전환

```vue
<!-- Vue 2 -->
<script>
export default {
  data() {
    return { count: 0 }
  },
  computed: {
    double() {
      return this.count * 2
    }
  }
}
</script>

<!-- Vue 3 -->
<script setup>
import { ref, computed } from 'vue'
const count = ref(0)
const double = computed(() => count.value * 2)
</script>
```

#### **E-05: 부모-자식 컴포넌트 통신**

**ParentComponent** (`example3/ParentComponent.vue`)
- `data()`, `methods` → `ref()`, 일반 함수
- `name` 속성 유지를 위해 `<script>` 블록 추가
- 로직은 `<script setup>`으로 전환

**ChildComponent** (`example3/ChildComponent.vue`)
- `props` → `defineProps()`
- `$emit` → `defineEmits()`

```vue
<!-- Child Component - Vue 3 -->
<script setup>
const props = defineProps({
  message: String
})

const emit = defineEmits(['update'])

function handleClick() {
  emit('update', newValue)
}
</script>
```

#### **E-06: Provide/Inject 패턴**

**ParentComponent** (`example4/ParentComponent.vue`)
- Options API의 `provide` → Composition API의 `provide()` 함수
- `name` 속성 유지를 위한 별도 `<script>` 블록

```vue
<script setup>
import { provide, ref } from 'vue'
const sharedData = ref('shared value')
provide('key', sharedData)
</script>
```

#### **E-07: Options API 전체 기능 변환**

**파일**: `example5/E-07-Options-API.vue`

완전한 Options API 컴포넌트를 Composition API로 전환:
- 라이프사이클 훅: `beforeCreate`, `created`, `beforeMount`, `mounted` 등
- `watch`, `computed` → `watch()`, `computed()`
- `methods` → 일반 함수 선언
- 모든 기능을 `<script setup>` 내부로 통합

#### **E-08 ~ E-12: 고급 리팩터링**

**파일**: `example5`, `example6`
- 기존 `setup()` 함수 방식 → `<script setup>` 문법으로 전환
- `name` 옵션이 필요한 경우 별도 `<script>` 블록 사용
- 코드 간결성 및 가독성 개선

## 📂 프로젝트 구조

```
src/
├── components/
│   ├── example1/          # E-01~E-04: 기본 반응성
│   ├── example2/          # 기본 바인딩
│   ├── example3/          # E-05: Props/Emit
│   │   ├── ParentComponent.vue
│   │   └── ChildComponent.vue
│   ├── example4/          # E-06: Provide/Inject
│   ├── example5/          # E-07~E-09
│   └── example6/          # E-10~E-12 
└── App.vue
```

## 🎯 마이그레이션 핵심 포인트

1. **`<script setup>` 우선 사용**: 더 간결하고 성능이 좋은 문법
2. **반응성 API 변경**: `ref()`와 `reactive()` 적절히 활용
3. **라이프사이클 훅 변환**: `onMounted()` 등 Composition API 훅 사용
4. **컴포넌트 통신**: `defineProps()`, `defineEmits()` 사용
5. **의존성 주입**: `provide()`, `inject()` 함수 활용

## 📸 스크린샷

### Before (Vue 2)
![Vue 2 Screenshot](./screenshots/vue2-before.png)

### After (Vue 3)
![Vue 3 Screenshot](./screenshots/vue3-after.png)

> 동일한 UI/UX를 유지하면서 내부 구조만 Vue 3로 현대화

## 📌 주의사항

- 모든 예제는 기능적으로 동일하게 동작합니다
- Vue 3의 `<script setup>` 문법을 최대한 활용했습니다
- 컴포넌트 `name` 속성이 필요한 경우 별도 `<script>` 블록을 사용했습니다

## 💡 학습 포인트

이 프로젝트를 통해 다음을 학습할 수 있습니다:
- Options API에서 Composition API로의 전환 방법
- `<script setup>` 문법의 장점과 활용법
- Vue 3의 반응성 시스템 (`ref`, `reactive`, `computed`)
- 컴포넌트 간 통신 패턴의 변화
- 라이프사이클 훅의 Composition API 버전

---

**License**: MIT  
**Vue Version**: 3.x  
**Author**: [Your Name]