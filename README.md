# Vue 2 Options API -> Vue 3 Composition API 전환 프로젝트 (BP_HW2)

제공된 Vue 2 Options API 기반 예제 코드를 Vue 3의 **Composition API**와 **`<script setup>`** 문법을 활용하여 전환 및 리팩터링했습니다. 모든 컴포넌트는 기존과 동일한 동작과 화면을 유지하며, Vue 3의 최신 개발 표준에 맞게 코드를 개선했습니다.

---

## 🛠️ 프로젝트 설정 및 실행

### Project setup
```bash
npm install

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

컴포넌트,파일 경로,변경 내용 요약,Vue 2 Options API 요소,Vue 3 Composition API 요소
E-01-instance,example1/E-01-instance.vue,Options API의 data()를 **ref**로 전환,data(),ref (<script setup>)
E-02-reactive,example1/E-02-reactive.vue,"data(), computed, mounted를 **ref, computed, onMounted**로 전환","data(), computed, mounted","ref, computed, onMounted"
E-03-binding,example1/E-03-binding.vue,양방향 바인딩을 **ref**로 구현,"data(), v-model","ref, v-model"
E-04-directives,example2/E-04-directives.vue,Options API의 data()를 **ref**로 전환,data(),ref
E-05ParentComponent,example3/ParentComponent.vue,name 유지를 위해 별도 <script> 블록 추가. data()/methods는 <script setup>으로 전환.,"data(), methods, name","<script>, <script setup>"
E-05 ChildComponent,example3/ChildComponent.vue,props 및 $emit을 <script setup> 스타일로 전환,"props, $emit","defineProps, defineEmits"
E-06ParentComponent,example4/ParentComponent.vue,name 유지를 위해 별도 <script> 블록 추가. provide는 Composition API로 전환.,"provide, name","provide, inject, <script>"
E-07-Options-API,example5/E-07-Options-API.vue,Options API의 모든 기능을 Composition API 훅스로 완벽 전환.,전체 Options API,전체 Composition API (<script setup>)
E-08-composition-api,example5/E-08-composition-api.vue,기존 setup() 함수 스타일을 권장되는 <script setup> 문법으로 단순화.,setup() 함수,<script setup>
E-09-composition-API2,example5/E-09-composition-API2.vue,이미 <script setup> 스타일로 작성되어 기능적 변경 없음.,해당 없음,<script setup>
E-10-ref,example6/E-10-ref.vue,Composition API(setup() 함수)를 <script setup> 문법으로 리팩토링하여 단순화.,setup() 함수,<script setup>
E-11-reactive,example6/E-11-reactive.vue,Composition API(setup() 함수)를 <script setup> 문법으로 리팩토링하여 단순화.,setup() 함수,<script setup>
E-12-ref-component,example6/E-12-ref-component.vue,Composition API(setup() 함수)를 <script setup> 문법으로 리팩토링하여 단순화. (템플릿 Refs),"setup(), name",<script setup>

