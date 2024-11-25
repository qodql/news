<div align="left">
<!-- logo -->
<p><img src="https://github.com/qodql/news/blob/main/public/img/news_logo.svg" width="200" height="130"/></p>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-html.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-css.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-sass.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-figma.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-swiper.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-js.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-vue.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-vuex.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-express.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-node.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-vercel.svg"/>
<img src="https://github.com/qodql/news/blob/main/public/img/readme/icon-project-git.svg"/>
</div> 

## 📝 프로젝트 소개
엔뉴스는 deepsearch API를 활용한 뉴스 정보 제공 사이트 입니다.
<br />

## 🗓 프로젝트 일정
**총 일정 2024.10.25 ~ 2024.10.25(1일), 1인**

## 🔗 배포 URL
<a href="https://news-one-eta.vercel.app/" target="_blank">https://news-one-eta.vercel.app/</a>
<br />

## 🖥 화면 구성
<img src="https://github.com/qodql/news/blob/main/public/img/readme/img-project04.jpg">

## ⚙ 기술 스택
이 프로젝트는 Vue.js기반 애플리케이션입니다.

- **VUE.js**: 프론트엔드 프레임워크, 컴포넌트 기반 UI를 구현
- **Axios**: API 통신을 위한 HTTP 클라이언트
- **SASS**: CSS 방식으로 컴포넌트 스타일링
- **Vercel**: 배포 플랫폼 (배포 사이트: [https://news-one-eta.vercel.app/](https://news-one-eta.vercel.app/))
- **GitHub**: 버전 관리 및 협업 도구
<br />

## 🛠 주요 기능 및 특징

1. **홈 화면**:
   - 홈 화면은 헤더, 메인 슬라이드, 장르별 뉴스 기사, 푸터로 구성되어 있습니다.

2. **검색 기능**:
   - 검색어 입력 시 API 요청을 보내고, 결과를 렌더링하는 기능을 Vue.js와 Vuex를 활용하여 구현했습니다.

3. **상세 팝업 기능**:
   - Vue 컴포넌트로 모달을 구현하고, 기사의 상세 정보를 API 호출로 가져와 표시하도록 했습니다.
<br />

## 🤔 기술적 이슈와 해결 과정

### 1. **드롭다운 버튼 클릭시 메인 슬라이드의 내용 변함 없음**

 - 문제: 드롭다운 버튼을 국내에서 해외로 바꾸면 기사 내용은 바뀌지만, 메인 슬라이드의 내용은 국내 기사 그대로 출력되는 문제 확인.

 -  해결: HomeView에서 MainSlide에도 props를 전송하여, 기본 기사 설정을 국내로 하고 드롭다운 버튼이 바뀔때 props 변수가 'articel' / 'global'로 바뀌게 설정하여 해결하였다.

### 2. **서버 부재로 인한 API 호출 문제**

 - 문제: Vue에서 api 요청을 보낼 때 서버가 존재하지 않아, CORS 정책 위반 오류가 발생했습니다.

 - 해결: Express 서버를 별도로 구축하고 배포하여 클라이언트(VUE)의 API 요청을 서버에서 처리하도록 변경했습니다. 클라이언트는 Express 서버로 요청을 보내고, 서버에서 API 호출을 수행한 뒤 결과를 클라이언트에 전달하는 구조로 개선함으로써 문제를 해결했습니다.


##  :file_folder: 폴더 구조
<pre class="notranslate">
<code>
📦news
 ┣ 📂public                  # 로고 및 정적 자원
 ┣ 📂src                     # 소스 코드 디렉토리
 ┃ ┣ 📂components            # 컴포넌트 폴더
 ┃ ┃ ┣ 📜MainSlide
 ┃ ┃ ┣ 📜DomesticArticle
 ┃ ┃ ┣ 📜ModalView
 ┃ ┃ ┣ 📜FooterView
 ┃ ┣ 📂views                 # 페이지 폴더
 ┃ ┃ ┣ 📜HomeView
 ┃ ┃ ┣ 📜SearchList
 ┃ ┣ 📜App.vue
 ┗ 📜README.md
 </code>
 </pre>




