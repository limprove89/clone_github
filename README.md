# clone_github

클론 코딩 프로젝트 - Github

## Head

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>clone-github</title>

    <meta name="author" content="limprove">
    <meta name="description" content="Github clone project">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, maximum-scale=1, minimum-scale=1">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">

    <meta property="og:type" content="website">
    <meta property="og:site_name" content="GitHub">
    <meta property="og:title" content="Build software better, together">
    <meta property="og:description" content="GitHub clone coding / GitHub is where people build software. More than 31 million people use GitHub to discover, fork, and contribute to over 100 million projects.">
    <meta property="og:image" content="img/logo__github.png">
    <meta property="og:url" content="https://github.com">

    <!-- https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started.html -->
    <meta property="twitter:card" content="summary">
    <meta property="twitter:site" content="GitHub">
    <meta property="twitter:title" content="Build software better, together">
    <meta property="twitter:description" content="GitHub clone coding / GitHub is where people build software. More than 31 million people use GitHub to discover, fork, and contribute to over 100 million projects.">
    <meta property="twitter:image" content="img/logo__github.png">
    <meta property="twitter:url" content="https://github.com">

    <!-- <link rel="shortcut icon" type="image/x-icon" href="favicon.ico"> -->
    <link rel="icon" href="favicon.png">
    <link rel="apple-touch-icon" href="favicon.png">

    <link href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700,900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.css">
    <link rel="stylesheet" href="css/main.css">
</head>
```

### meta

- name과 content로 사이트 전반적인 정보를 기입
- og(open graph)/ twitter card의 상세 기입

### link

- icon -> png파일로 연결
- apple-touch-icon 은 ios/Android에서 앱 화면 설정
- index.html 위치 내 favicon.ico 파일이 위치되어있으면, 구형 브라우저에서도 찾아서 인식
- font cdn과 reset.css, 작성하는 css파일을 연결 (작성 css파일을 가장 하단에 위치)

## body

CSS 방법론인 BEM(Block Element Modifier)을 따르는 클래스명을 짓는다.  
body에 css 속성을 적용하는것은 비효율적이므로, body 바로 아래 body__container클래스를 생성한다. (BEM)

### common

공통된 컴포넌트 작성 (button/input)

#### button

버튼 생성 시 별도의 width값을 지정하지 않고, inline-flex를 이용하면, 내부 글자의 가로너비만큼 버튼이 생성된다.  
그리고 패딩값으로 좌우 너비를 설정하여 가운데 정렬을 한다.  
background 색상을 linear-gradient()함수를 이용하여 설정한다.
버튼 생성 시 :hover::before를 이용하여 마우스 커서 반응을 설정한다.

#### input

입력 창에는 포커스 시 알려주는 outline 속성(생각보다 제어가 까다로움)을 none으로 설정하고, 가상요소선택자 :focus를 사용하여 정의해준다.  
box-shadow는 안쪽으로 설정하는 inset을 사용하여 내부 그림자 설정을 한다.
placeholder의 css 속성을 적용하는 부분은 정식 기술로 채택되지 않음.  
브라우저 별 기술을 뜻하는 Vendor Prefix를 적용하여 개선한다.  
ex) chrome => -webkit, ie/edge => ms, firefox => moz, opera => o  

### header

헤더 섹션에서(하단 부분까지도) 내부 중요한 영역(로고/커서 등)은 중앙으로 모여 있다.  
섹션 안에서 특정한 컨텐츠들을 감싸서(container,inner,wrapper) 중앙으로 모야주는 역활을 구현한다.  
헤더 영역 또한 기본적인 section 이므로 header태그의 class를 section으로 구성한다.

#### header > 구조 파악

헤더 navbar 부분은 좌우 여백을 가지고 있으며, 컨텐츠는 중간으로 집중되어 있다. 왼쪽 메뉴바에는 logo.img와 4가지 a tag가 위치하고 있으며, 오른쪽 메뉴바에는 좌측에 비해 작은 폰트의 3가지 a tag와 input창과 2가지 버튼으로 구성되어 있다.

#### header > menu-group (좌측메뉴)

좌측 메뉴는 로고 이미지와 4개의 텍스트 메뉴로 구성되어 있다.  
.menu-group 의 클래스 안에 .logo 클래스(이미지가 아닌 div 클래스)와 .main-menu 클래스(div가 아닌 ul 클래스)를 생성하였다.  
.logo 클래스 안에 a tag를 생성하고 text content는 img 태그의 alt 기능을 대처한다. (이미지는 a태그에 background를 통해 삽입)  
a 태그의 text는 text-indent: -9999px;로 보이지 않게 설정한다.
메뉴는 div가 아닌 ul로 구성하는데, 시멘틱한 구조를 위해 ul을 사용한다. 따라서 각각의 자식요소 li안에 a tag로 메뉴를 작성한다.

#### header > sign-group (우측메뉴)

우측 메뉴는 좌측보다 상대적으로 작은 텍스트 메뉴와 input창, 공통 컴포넌트에서 제작한 버튼으로 구성되어 있다.  
HTML 작성에서 중요한 것은 순서인데, 좌우보다는 위에서 아래의 순서를 고려하여 개발한다.  
가로 사이즈를 축소하면 navbar는 햄버거 메뉴로 대처되는데 이때 순서는 버튼, input, a tag 순서이다.  
이 경우 세로 순서에 맞게 작성 후 가로는 order를 이용하여 배치시켜 준다.
input에 경우는 method를 POST방식으로 작성하고, submit 버튼을 display:none 처리 한다. 또한 form 태그로 input 전체를 감싼다.  
a tag에 경우 텍스트에만 클릭 범위를 적용하는 것은 불편하기에 padding을 줘서 영역을 크게 늘린다.  
또한 우측 두 버튼 사이의 간격은 떨어져 있으므로 display:flex를 적용 후 마진으로 조정한다.  

### visual