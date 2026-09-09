---
title: 'Gatsby를 이용하여 나만의 블로그 만들기 (세팅 편)'
date: 2022-10-22 20:54:32 +0900
tags:
  - Gatsby
  - Blog
  - GitHub Pages
excerpt: Gatsby 프레임워크와 템플릿을 이용하여 나만의 블로그를 만드는 방법
permalink: /posting-blog-using-gatsby/
---

## Gatsby란?

```
Gatsby is a free and open source framework based on React that helps developers build blazing fast websites and apps. It combines the control and scalability of dynamically rendered sites with the speed of static-site generation, creating a whole new web of possibilities.

Gatsby는 개발자들이 엄청나게 빠른 웹사이트와 앱을 만드는 것을 돕는 React 기반의 자유롭고 오픈 소스 프레임워크이다. 동적으로 렌더링된 사이트의 제어 및 확장성과 정적 사이트 생성 속도를 결합하여 완전히 새로운 가능성의 웹을 만듭니다. (Translated by Papago)
```

React를 통해 새로운 사이트를 만드려면 많은 개발 리소스와 시간이 필요하다. 하지만 개인 블로그와 같은 사이트를 만들기 위해 많은 노력을 쏟는다면 블로그의 원래 목적인 정보 공유의 목적을 달성하는데 어려움을 겪을 수 있다. 그래서 사람들은 큰 노력을 들이지 않고 사이트를 만들거나 적은 노력을 들이고도 구조적으로 깔끔한 어플리케이션을 만들기 위해 React를 활용해 여러 프레임워크들(ex: Chakra UI, Gatsby, Next.js 등등)을 만들었는데, Gatsby는 이 이 프레임워크 중 하나이다.
([개발자들이 사용하는 7가지 리액트 기반 프레임워크](https://plainenglish.io/blog/react-frameworks-for-developers-69ee636034c))

이 여러가지 프레임워크들 중에서 우리는 오늘 `Gatsby` 프레임워크를 활용하여 나만의 블로그를 간단하게 만들어볼 예정이다.

## Gatsby를 이용해서 나만의 블로그 만드는 방법
아래 순서는 Gatsby [공식 문서](https://www.gatsbyjs.com/docs/tutorial/)를 참고하였다.
1. [`gatsby-cli` 설치](https://www.gatsbyjs.com/docs/tutorial/part-0/)
    - Gatsby를 사용하기 위해서는 기본적으로 아래 목록들을 설치해야 한다. 만약 본인의 컴퓨터에 기본적으로 설치되어 있다면 넘어가도 된다.
        1. [Node.js](https://www.gatsbyjs.com/docs/tutorial/part-0/#nodejs) (v14.15 이상)
        2. [Git](https://www.gatsbyjs.com/docs/tutorial/part-0/#git)
        3. [Visual Studio Code](https://www.gatsbyjs.com/docs/tutorial/part-0/#visual-studio-code) (Optional)
    - 위 목록들이 설치되었다면, `npm install -g gatsby-cli` 명령어를 통해 `gatsby-cli` 패키지를 설치하면 된다. 설치 후에는 `gatsby --version` 명령어를 사용하여 v3 이상인지 확인하자.
  - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/1.png' | relative_url }})
2. 템플릿을 사용하여 새로운 Gatsby 프로젝트 만들기
    - Gatsby에서는 기본적으로 여러가지 템플릿들을 제공해주고 있다.
    - 만약 새로운 사이트를 만드는 목적이 블로그 사이트를 만드는 것이라면 `blog` 템플릿을 사용해 손쉽게 블로그 페이지를 세팅할 수 있고, 포트폴리오 사이트를 만드는 것이 목적이라면 `gatsby-starter-portfolio-cara`와 같은 템플릿들을 사용하여 목적에 맞춰 손쉽게 블로그를 세팅할 수 있다.
    - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/2.png' | relative_url }})
    - 이번 포스팅에서는 나만의 블로그를 만드는것이 목적이므로, 인기있는 템플릿 중 하나인 `blog` 템플릿을 사용해 나만의 블로그를 손쉽게 만들어볼 예정이다.
    - `blog` 템플릿의 경우 아래와 같은 기능들을 기본적으로 제공해주고 있으니, 참고하자
        - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/3.png' | relative_url }})
    - `npx gatsby new '블로그 이름' https://github.com/gatsbyjs/gatsby-starter-blog` 명령어를 터미널에 입력해서 블로그 템플릿 Gatsby 프로젝트를 생성하자.
    - 프로젝트 생성 후에 `cd '블로그 이름' && gatsby develop` 명령어를 실행시킨 뒤 http://localhost:8000/ 에 접속해서 정상적으로 블로그가 뜨는지 확인하자.
3. 첫 포스팅 작성하기
    - 블로그 템플릿 [깃허브](https://github.com/gatsbyjs/gatsby-starter-blog)를 확인하면 프로젝트 구조에 대한 설명을 확인할 수 있다.
        - .
        - ├── node_modules
        - ├── src
        - ├── .gitignore
        - ├── .prettierrc
        - ├── gatsby-browser.js
        - ├── gatsby-config.js
        - ├── gatsby-node.js
        - ├── gatsby-ssr.js
        - ├── LICENSE
        - ├── package-lock.json
        - ├── package.json
        - └── README.md
    - 위 파일들 중 우리가 포스팅을 작성하기 위해 필요한 파일은 아래와 같다
        - `gatsby-config.js`: 이것은 개츠비 사이트의 기본 구성 파일로, 여기서 사이트 제목 및 설명, Gatsby가 포함할 플러그인 등과 같은 사이트(메타데이터)에 대한 정보를 지정할 수 있다.
        - `src/images/profile-pic.png`: 웹 사이트에서 나오는 프로필 이미지로, 해당 파일을 수정해야 본인의 프로필 이미지로 볼 수 있다.
        - `content/blog`: 실제 포스팅들이 저장되는 폴더로, 해당 폴더에 새로운 폴더를 만들어서 포스팅들을 작성할 수 있다.
    1. `gatsby-config.js`
        - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/4.png' | relative_url }})
        - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/5.png' | relative_url }})
        - 첫 번째 사진과 두 번째 사진을 비교해보면 어느곳을 수정했을 때 어떻게 바뀌는지 예상하기 쉬울 것이다. 해당 파일에 본인의 정보를 입력해주면 된다.
            - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/6.png' | relative_url }})
        - 위 사진을 보면 `You should follow them on Twitter` 부분이 있는데, 나는 트위터를 하지 않으므로 해당 문장을 삭제하고 싶다. 이럴 경우 어떤 파일에 해당 문장이 있는지 VSCode를 통해 검색하면 찾기 수월하다.
            - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/7.png' | relative_url }})
        - `src/components/bio` 파일에 해당 문장이 있는걸 확인했고, `bio.js` 파일을 아래와 같이 바꿔주었다.
            - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/8.png' | relative_url }})
        - 바꿔준 후 정상적으로 나의 정보가 정상적으로 표시되는것을 확인할 수 있다
            - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/9.png' | relative_url }})
    2. `src/images/profile-pic.png`
        - 기본적으로 설정되어 있는 남자의 프로필 사진을 자신의 프로필 사진으로 바꾸어주면 된다.
            - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/10.png' | relative_url }})
    3. `content/blog`
        - 해당 폴더에 있는 `hello-world/index.md` 파일과 실제 포스팅 결과를 확인해 보면 어떤 마크다운 문법을 썼을 때 웹 페이지 상에서 어떻게 보이는지 쉽게 확인할 수 있다.
        - `content/blog` 폴더에 자신이 포스팅하고 싶은 내용을 추가하면 새로운 포스팅이 생긴것을 확인할 수 있다. (기존에 존재하는 파일들을 참고하면 손쉽게 추가할 수 있다.)
    - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/11.png' | relative_url }})
4. 배포를 통해 나만의 블로그 배포하기
    - `yarn run build` 코멘드를 이용하면 포스팅한 내용들을 빌드 할 수 있다.
    - `yarn run build` 코멘드를 이용해 `public` 폴더 생성 후, public 폴더 안에서 `git init` 명령어를 통해 깃을 세팅 해주자.
    - 깃허브에서 `본인의 닉네임/본인의 닉네임.github.io` 레포지토리를 새로 생성할 경우 깃허브 페이지를 새로 생성할 수 있다. ([참고 링크](https://pages.github.com/))
    - ![]({{ '/assets/images/post_figures/posting-blog-using-gatsby/12.png' | relative_url }})
    - 터미널의 `public` 폴더 안에서 `git remote add master '깃 레포지토리 주소'` 명령어를 통해 `public` 디렉토리에 깃허브 페이지 주소를 추가하자.
    - `git add .; git commit -m "커밋 내용"; git push origin master` 명령어를 통해 빌드한 내용을 푸시할 수 있다.
    - 푸시 후 블로그 주소에 들어가보면 (ex: https://mgpocky.github.io/) 정상적으로 블로그가 올라간것을 확인할 수 있다.
        - 푸시 후 페이지가 생성 및 로딩되기까지 최대 3분정도 걸릴 수 있다.
    - 이제 자동화를 통해서 손쉽게 블로그를 포스팅 해보자.
    - `package.json` 파일에 들어간 뒤 `scripts` 안에 해당 코멘드를 붙여넣어보자..
        - `"deploy-public": "yarn build && cd public && git pull master && git add . && git commit -m \"$(date +%F)\" && git push master",`
        - 위 코멘드는 빌드 후, 날짜에 맞게 변화된 내용들을 커밋한 후 빌드한 내용들을 푸시해주는 명령어이다.
    - 위 코멘드를 추가한 뒤 `yarn run deploy-public` 코멘드를 입력할 경우 자동으로 빌드 & 커밋 & 푸시를 해준다.
