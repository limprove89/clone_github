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