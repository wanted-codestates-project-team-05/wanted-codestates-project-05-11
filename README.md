## Description

원티드 프리온보딩 코스에서 프로젝트로 그레이비랩의 **진단 검사 페이지**를 개발하였습니다. 첫 페이지 상단 검색에서 기업명을 검색하면 기업과 사용자의 진단 점수가 아래의 두개의 그래프로 표시되어 기업과 사용자의 결과값을 나타냅니다.

## Usage(자세한 실행 방법)

1. git clone

```jsx
<과제1>
git clone https://github.com/wanted-codestates-project-team-05/wanted-codestates-project-05-11.git
```

2. 필요한 라이브러리 설치

```
npm install
```

3. 실행

```
npm run start
```

기술스택

- vue.js 사용
- 차트는 모두 vue-chart.js 라이브러리 사용
- 배포 vercel

# 배포 링크

<과제1><https://wanted-codestates-project-05-05-01.vercel.app/><br>

# 구현 내용

## <수영님>

### 구현한 내용

- vue-chart.js 라이브러리를 이용하여 펜타곤 그래프를 구현
  ![스크린샷 2022-03-08 오후 9 02 33](https://user-images.githubusercontent.com/68948735/157234601-a4545c13-63ea-443a-bc77-afe328a5a75f.png)

## <승규님>

### 구현한 내용

- vue chart를 이용하여 펜타곤 그래프를 구현하였습니다.
- chart data 조작 버튼을 구현하였습니다.

### 주요화면

<img width="493" alt="스크린샷 2022-03-08 오후 4 45 52" src="https://user-images.githubusercontent.com/22316798/157190418-5baf240f-4b64-43f2-9e01-6624cc4bff48.png ">

## <정민님>

### 구현한 내용

#### BarChartContainer.js

- 하단 bar chart 의 레이아웃을 구성하였습니다.<br>
- Vue chart를 구현 하였지만, 같은 팀원이 더 잘 구현 해주셔서 그것으로 대체하였습니다.<br>

## <성현님>

### 구현한 내용

#### src/components/bar/BarChart.vue

### vue-chartjs 사용 HorizontalBar 생성

<img width="352" alt="스크린샷 2022-03-08 오후 8 50 48" src="https://user-images.githubusercontent.com/70502670/157232887-bc51242a-d319-46d8-ac73-69935aabd6b5.png">

- 가로막대 그래프를 생성합니다.
- props로 그래프 데이터, 현재 검색되는 회사 이름, 본인/회사/모두 그래프 보여주기 조건을 받아 랜더링합니다.
- watch로 검색 회사 이름과 그래프 보여주기 조건을 감시하여, 변경데이터를 반영하도록 합니다.
- option은 고정적임으로 구현 ui 조건에 따라 작성했습니다.
- 데이터를 받아오면 changeDataFormat 메소드에서 그래프를 그릴 수 있는 데이터 포맷으로 형식을 변경해 줍니다.
  <changeDataFormat 함수>
  - 내부 함수 makeGraphData 에서는 최대점수에 맞추어 데이터를 음수, 양수로 변환하여 피그마의 가로 막대 그래프 ui처럼 랜더링 할 수 있도록 합니다.
  - 또한 모두/본인/회사 조건에 맞추어 데이터가 보이지 않도록 데이터 변수에 삼항연산자를 사용해 필터링 해주었습니다.
  - 그 외에 필요한 고정 data 세팅(색상, 두께, 라벨 등)을 포함합니다.

### src/components/bar/BarChartContainer.vue

- HomePage 에서 받아온 props 로 BarChart에서 필요한 데이터 형식을 만들고, watch로 변경사항을 반영합니다.
- maxScore 및 첫 랜더링 시 본인 그래프 보여주기 세팅 등 초기 데이터를 세팅합니다.
- 가로 막대 바의 lable 및 점수 ui 와 병합을 진행했습니다.

### src/components/home/HomePage.vue

- HomePage의 데이터로 가로 막대 바 그래프 컨테이너에 필요한 데이터를 생성, 변경하여 전달해주었습니다.
- 전달해주는 데이터가 클릭 이벤트 등의 발생으로 변경되면 변경사항을 전달할 수 있도록 watch 에 필요한 코드를 작성했습니다.

## <윤구님>

# 구현 내용

components/home/MainHeader
components/home/SearchInfo
components/home/SearchInput

헤더 및 검색 기능

- 헤더 : 뒤로가기 버튼 밑 다시 진단하기 링크를 클릭할 시 새로고침

![header](https://user-images.githubusercontent.com/85268135/157232822-ddc09021-3a96-4741-93f4-ac4e643ba9e0.gif)

- 검색기능 : 검색어 입력 후 엔터를 누르면 기업 데이터에 검색어를 이름으로 하는 회사가 있는지 확인하고 없다면 경고창을 띄움 검색어가 있다면 검색 결과에 검색어를 보여주고 x버튼 클릭시 검색어 삭제

![input](https://user-images.githubusercontent.com/85268135/157233033-15086a19-7029-462e-bac1-ef7087f30232.gif)

![dele](https://user-images.githubusercontent.com/85268135/157233217-ad8a3b5a-64cb-45e9-a609-2a7034756a67.gif)

# 구현 방법

- MainHeader : before, after 선택자를 이용해 아이콘 생성했습니다. 클릭시 a태그의 href ='/'를 이용해 새로고침합니다.
  다시 진단하기 링크도 클릭시 새로고침합니다.
- SearchInput : v-model을 이용하여 input 창에서 엔터를 누를시 keyup 이벤트로 homepage에서 props를 input value로 변경합니다. 이벤트 핸들러에서 input value를 검사하여 기업 데이터에 input value를 이름으로 가지는 데이터가 없다면 경고창을 띄웁니다. samsung, kakao는 한글로 삼성, 카카오로 검색해도 samsung, kakao로 넘어갑니다.
- SearchInfo : 검색어를 받아와 보여줍니다. x버튼 클릭시 click이벤트가 발생하여 검색결과를 지우고 homepage props에 반영됩니다.

## <승연님>

### 구현내용

- vue-chart를 이용하여 펜타곤 그래프 구현

* 주요 화면 캡쳐 사진
  <img alt="그래프" src="https://user-images.githubusercontent.com/54584337/157233057-7676e9bb-b655-4404-85ed-e47917701105.png">

# 어려웠던 점

## <수영님>

### 어려웠던 점

- vue를 처음 접해서 설정부터 막혔다.
- 새로운 라이브러리 적용시키는게 어려웠다.

## <승규님>

### 어려웠던 점

- vue, vue-chart가 처음이여서 처음 설정하는데에서 많은 어려움을 겪었습니다.
- vue의 props를 어떻게 업데이트 시켜주는지가 어려웠습니다.
- 차트 버전문제로 차트가 출력되지 않는 문제가있었습니다.

### 해결방법

- 펜타곤 그래프에 3명이 붙어서 같이 내용을 공유하며 옵션을 설정해서 해결하였습니다.
- 버전문제는 스택오버플로우를 참고해서 고쳤습니다.
- 차트 옵션 설정은 공식문서와 많은 사이트를 참고하여 고쳤습니다.

## <정민님>

### 어려웠던 점 && 해결방법

- vue를 처음 접하고 처음 써보는 chart 라이브러리 많은 어려움이 있었습니다.<br>
  그래서 유투브에 1시간 vue정복 강의를 듣고 수도 없이 많은 구글링을 통해서 한코드 한코드씩 작성해 나갔습니다.<br>
- Data 상태 관리 하는 방법이 react랑 많이 달라서 사용법에 많은 어려움이 있었습니다. 많은 구글링과 팀원들의 도움으로 해결할 수 있었습니다.<br>

<img width="843" alt="스크린샷 2022-03-08 오후 8 54 39" src="https://user-images.githubusercontent.com/56882147/157235234-60c274aa-b566-4662-9e01-7c353ed5294b.png">

## <성현님>

### 어려웠던 점 && 해결방법

- 뷰를 처음써보다 보니, 좋은 코드가 무엇인지에 대한 고민을 충분히 하지 못해서 아쉬웠다.
- 필요한 데이터를 props로 전달할 때, 객체이면 얕은 복사로 인해 상태 변화가 감지되지 않았는데 해당 내용을 알아채지 못해서 조금 헤맸다.

## <윤구님>

### 어려웠던 점

검색 결과와 검색 컴포넌트를 하나로 합쳐서 개발하고 있었으나 keyup이벤트와 click이벤트가 한 개의 컴포넌트에서 동시에 적용되지 않는 문제가 발생하였습니다.

### 해결 방법

검색 결과와 검색 컴포넌트를 따로 분리해 해결했습니다.

## <승연님>

### 어려웠던 점

- 그래프의 꼭지점마다 도형이 있어야 하는 점이 어려웠고 그래프 가운데 이미지를 넣어야 하는 것이 어려웠습니다. <br>
  - 그래프 라벨 이름과 그래프 사이에 간격을 맞추는 것이 어려웠습니다.<br>
    <br>

### 해결 방법

- chart 공식 문서를 보면서 옵션값을 설정해서 해결을 하였습니다. <br>
- 그래프 꼭지점에 있는 도형은 해결하였지만 이미지를 넣는 것은 태그를 만들고 `position: absolute`를 주어 중앙정렬을 하여 가운데 정렬을 하였습니다. <br>
- 그래프 라벨에 이름은 라벨이 배열로 들어가는데 빈 값을 추가하여 줄이 한칸이 늘어나지만 화면상에는 간격이 띄어진 것처럼 보여서 그래프와 라벨 간격을 해결하였습니다.
