<img src="https://i.imgur.com/R2wksCG.png" width="400"/>



# 📮 vue-state-store

📬 분산된 뷰 전용 상태관리 모듈 체계 (발행-구독 모델 기반)

> 완전히 타입스크립트를 지원하는 간단한 상태관리 체계



## 😊 쉬운 사용! & 강력한 응용!

`vue-state-store` 는 기존의 `vue` 에서 많이 사용되던 `vuex` 모듈을 완전히 대체하기 위해서 나온 모듈입니다. 이 모듈은  <u>**타입스크립트의 효율을 200% 로 사용해서 상태관리를 매우 쉽게 만드는 것을 목표로 합니다.**</u>



### 💡 vuex 와 비교하였을때 장점 요약

- **낮은 러닝커브** - 간단한 발행 & 구독 모델 사용
- **Typescript Intellisense** 지원 - <u>상태</u> & <u>액션</u>& <u>뮤테이션</u> & <u>템플릿 내 변수 사용 시</u>
- **자동 바인딩 함수** - 간편한 vue template 바인딩 가능
- **순수 타입스크립트 클래스 기반 정의** - mix-in 사용 불필요
- **일원화 된 액션 구조** - Action 과 Mutation 구별 없이 유연한 사용 가능
- **유연한 상태 사용 허용** - Mutation 을 생략하면 Getters 로 사용 가능

------



### 💬 설치방법

> (Vue2, Vue3, Nuxt 를 지원하며, Composition API 에서 자동 바인딩 함수 `.bind()` 를 지원합니다.)

```
npm i vue-state-store
```



### 📬 발행 & 구독 모델 설명

> vue-state-store 는 발행 & 구독 디자인 패턴을 사용합니다.

`vue-state-store` 는 값을 저장한 메모리 상에 존재하는 저장소입니다. `.subscribe(callback)` 함수를 통해서 저장소 안의 값이 변경될 때 콜백으로 변경된 값을 전달 받을 수 있으며, `.set(newValue)` 과 `.update((data) => data)` 를 통해 저장소 안의 값을 업데이트 할 수 있습니다.



## 😎 기본적인 사용방법

>  `vue-state-store` 는 함수 또는 클래스를 통해 <u>상태</u> & <u>액션</u> & <u>뮤테이션</u>을 모두 쉽게 관리할 수 있습니다.



### 📮 기본타입 발행 & 구독

> 기본 타입은 다섯가지 기본 **타입** (Number, String, Boolean, null, undefined) 을 뜻합니다.

![](https://i.imgur.com/dfaprvQ.png)



### 📮 객체 타입 발행 & 구독

> 아래를 보시면 위와 사용법 차이가 거의 없다는 것을 확인하실 수 있습니다.
>
>  `store(vaule)` 에서 value 는 <u>기본 타입</u> 또는 <u>객체</u>가 될 수 있습니다.

![](https://i.imgur.com/D8I76ax.png)



### 📮 상태 및 내장된 액션 생성

> `vue-state-store` 는 클래스를 상속함으로써 내장된 액션을 정의가능합니다.

`vue-state-store` 에서는 Action 과 Mutation 의 구별이 필요하지 않습니다.

- 클래스에 임의의 함수를 생성함으로써 <u>**내장된 액션(Embedded Action)**</u> 의 구성이 가능합니다.
- 클래스에 내장되지 않은채로 상태를 변형하는 모든 함수는 **<u>외부 액션(Outsidde Action)</u>** 으로 명칭합니다.

![](https://i.imgur.com/Tjs6PiM.png)



### 📮 Vue 템플릿 내에서의 바인딩

> `vue-state-store`는 vue template 태그에 저장소를 쉽게 바인딩할 수 있으며, 바인딩 된 스토어는 템플릿 태그 내에서도 Typescript Intellisense 가 계속 지원됩니다. 또한 <script> 태그 내에서 저장소에 내장된 액션을 사용시에도 Typescript Intellisense 가 지원됩니다.

-  `import` 를 통해서 상태를 불러오는 것만으로 내장된 액션의 호출이 가능합니다.
- `.bind() 함수를 통해서` 저장소를 템플릿 내로 자동으로 바인딩할 수 있습니다.
  - `return { $vote: vote.bind() }` 와 같이 기존 저장소 명 앞에 `$` 를 붙이는 것을 네이밍 규칙으로 권장합니다.
  - `.bind()` 함수는 <u>**@vue/composition-api**</u> 의 `setup` 함수 내에서 사용하는 것이 권장됩니다.

![](https://i.imgur.com/XbLIQzy.png)



## 🚀 고급 사용법 설명



### ⏳ 비동기 사용 방법

> `.update()` 함수와 `.set()` 함수는 Promise 를 반환합니다.



- await 을 통해 저장소 값을 갱신할 때 해당 갱신 작업이 완료된 다음 특정 로직이 실행되도록 할 수 있습니다. 

![](https://i.imgur.com/aKrhrFQ.png)



- update 함수에 전달되는 콜백을 async 로 정의할 수도 있습니다.

![](https://i.imgur.com/B4oHDnG.png)



### 💡 vscode 인텔리센스 적용방법

>  vscode 에서 vue 와 typescript 를 동시에 사용 시 인텔리센스를 지원받으려면 아래 모듈을 받으시면 됩니다.

[Vetur]: https://marketplace.visualstudio.com/items?itemName=octref.vetur

vetur 설치후 템플릿 내 인텔리센스를 지원받기 위해서 아래의 옵션을 vscode 설정에 추가해주어햐아 합니다.

```json
"vetur.experimental.templateInterpolationService": true
```



## 🤔 Q&A



### 🧲 Q. vuex 처럼 모든 상태 저장소들을 다 가지고 있는 $store는 없나요?

>  A. 네 없습니다. 비 권장 패턴입니다.

임의의 index.ts 파일을 만든 후 `import { vote } from '~/store` 와 같이 일부 스토어만 가져와서 사용하는 것이 권장됩니다. `vue-state-store` 는 분산된 구조를 가지며, 각 저장소가 필요한 경우에만 개별적으로 서로를 참조할 수 있습니다.

 `.bind()` 함수를 통해서 vue 템플릿 태그 내에서 사용되기 전까지 `vue-state-store` 는 `vue` 와 완전히 분리된 상태로 구성됩니다.



### 👀 Q. `.bind()` 된 값이 변경되면 변경된 값이 다시 렌더링되나요?

> A. 네 vue의 ref 를 통해서 변경된 저장소 값이 실시간으로 템플릿 태그를 통해 DOM에 반영됩니다. 





## 📔 라이센스

> Copyright @ 2020 AhaOfficial (a-ha.io)

**MIT Licensed**
