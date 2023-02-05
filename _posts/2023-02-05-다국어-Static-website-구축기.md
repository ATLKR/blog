---
title: 다국어 Static website 구축기
categories:
 - 블로그
tags:
 - Korean Posts
 - Static website
 - Github Pages
---

# 시작하며

저는 항상 "배워서 남 주자"라는 생각을 많이 했던 것 같습니다. 그래서인지 예전부터 Static website 설정을 해야겠다는 생각이 있었는데요, 조금씩 준비하던 것을 이번에 드디어 어느 정도 완성하게 되었습니다. 다른 많은 분들이 가이드를 작성해 주셨듯이 좋은 방법들이 많았으나, 제가 사용하고자 하는 다국어 지원 환경을 생성하기에는 적합하지 않았습니다.
그래서 저는 다른 분들을 위해 제가 해결해야 했던 내용을 공유하려 합니다. 다만, 아직 작업중이라는 점에 대해서는 이해해주시면 감사하겠습니다.

## 서비스 정하기

Static Website 는 여러가지 서비스들이 있습니다. 지금 사용중인 Github Pages 뿐만 아니라, Netlify, Cloudflare 등 여러 가지 회사에서 서비스를 제공하고 있습니다.
제가 그럼에도 불구하고 Github 를 선택한 이유는:

* 많은 사람들이 이용한다.
* IT 직종의 사람들에게 매우 공개되어 있는 환경
* 저장 공간의 제한은 있으나, 빌드를 대부분의 경우 로컬이 아닌 서버에서 무료로 해결 가능
* 디자인이 괜찮은 다양한 테마의 제공 (블로그용 테마 뿐만 아니라 문서용 테마까지)

## 준비하기

저는 블로그 서비스 뿐만 아니라 문서를 저장하기 위한 문서 저장소까지 필요했습니다. 그래서 Github Repository를 여러 개 생성한 뒤, 각각의 도메인에 수동으로 연결해야 하는 불편함이 있었습니다. 또한 저는 제목에서 볼 수 있듯이, 국문 뿐만 아니라 영문으로 된 문서까지 작성하고자 했는데, 각기 두개의 사이트를 한 레포지토리에서 호스팅하는 것이 제일 이상적이라고 판단했습니다. 그 이유는:

* 귀찮아서 (상당히 중요함)
* 도메인 하나로 처리하고, /en, /kr 등 하위 디렉토리로 연결하는 것이 제일 멋있어 보여서

였습니다. 귀찮은 것 말고도, 제 문서용 도메인인 [docs.atlkr.com](https://docs.atlkr.com) 뿐만 아니라 [blog.atlkr.com](https://blog.atlkr.com) 과 같은 식으로 제가 사용하는 서비스 목적에 대한 도메인을 구성한 뒤, 그 하위 디렉토리에 묶는 것을 가장 중요하게 생각했습니다.

## 메인 도메인에 대한 작업

제가 가진 도메인인 [atlkr.com](https://www.atlkr.com) 에 메인 페이지를 구축하기 위해서, [atlkr/atlkr.github.io](https://github.com/atlkr/atlkr.github.io) 레포지토리에 Github Pages 를 설정한 뒤, index.html 페이지를 제 블로그 도메인인 [blog.atlkr.com](https://blog.atlkr.com) 으로 리디렉션하도록 작업했습니다.

## 블로그에 대한 작업

블로그는 지금 보고 계신 블로그의 도메인에서 아실 수 있듯이, 블로그의 경우는 그냥 [blog.atlkr.com](https://blog.atlkr.com) 으로 표시되고 있습니다. 다른 분들의 작업물들의 경우, 국문/영문 모두가 표시되도록 작업할 수 있는 [플러그인](https://github.com/kurtsson/jekyll-multiple-languages-plugin) 등이 Jekyll 용으로 많이 빌드되어 있었습니다. 다만, Github Pages 등 static website 의 경우는 데이터베이스를 로드할 수 없는 제약사항이 있기 때문에, 상당히 어려워 보여서 사용하지 않았습니다.
다른 블로그를 찾아보아도, Minimal Mistake 테마의 경우에는 딱히 제가 생각했던 것 만큼 두 개의 사이트로 분리하는 효과를 내기는 어려웠습니다.

## 블로그 두개는 포기하자...

그래서 블로그의 경우에는 당장은 포기하고, 지금 이 글을 작성한 뒤 아마 나중에 수정하게 될 것 같습니다. 다만, 다른 분들을 위해 여기에 제가 찾은 자료들을 간단한 설명과 함께 제공드립니다.

* [Build a Multilingual Jekyll Site](https://leo3418.github.io/collections/multilingual-jekyll-site/set-up-jekyll.html) 이 가이드의 경우에는 직접 빌드를 해서 HTML _site 디렉토리를 만들 수 있기에, 제가 아마 Jenkins 파이프라인을 구성한 뒤 시도할 것 같습니다. 현재로써는 제일 가능성이 높아 보입니다.

* [Configure Jekyll to be multi-language without plugins](https://juan.pallares.me/configure-jekyll-multi-language-without-plugin/) 이 분의 글도 체크해 볼 만하지만, 저는 제가 영문과 국문으로 완전히 똑같은 글을 작성하지는 않을 것이라고 생각해서, 사용하지는 않았습니다.

## 문서 저장소에 대한 작업

문서 저장소의 경우는, [docs.atlkr.com](https://docs.atlkr.com) 에서 확인하실 수 있듯이, /en 과 /kr로 분리되어 있고, 제가 원하던 구성으로 작업되어 있습니다.
이렇게 작업을 할 수 있던 이유는... 대단한 것은 아니고 그냥 폴더를 제가 옮기고, config 파일을 두 언어에 따라 따로 작성한 뒤, docs 폴더도 분리했습니다. 그리고 빌드의 경우는 수동으로 각 언어별로 빌드하고 나니, Github Actions 를 사용해서 자동으로 업로드 해주었습니다. 또 좋았던 부분은, [Material for Mkdocs](https://squidfunk.github.io/mkdocs-material/setup/changing-the-language/?h=language) 에서 확인하실 수 있듯이, 제가 문서 저장소용으로 사용하고 있는 Material for Mkdocs 테마에서 기본적으로 언어 선택 기능을 제공하는 것이었습니다. 또 그다지 크게 기능의 변경 없이, /kr /en 과 같은 서브디렉토리로의 링크만 제공하기에 오히려 더 편하게 사용할 수 있었습니다.

## 마치며...

상당히 간단한 작업을 한 것 처럼 보이지만 제 입장에서는 이번 주 주말의 대부분을 이 작업을 하며 시간을 보냈습니다. 다행히 여자친구 님께서 이해해주셨기에 컴퓨터와 씨름할 수 있었지만, 조금 더 다국어 지원이 되는 플랫폼이 늘어났으면 합니다. 정보의 공유란 건 중요하니, 더 많은 사람들이 공유할 수 있는 플랫폼이 있었으면 합니다.
제 블로그/문서 저장소 레포지토리는 포크해서 변형하셔도 되며, 제가 사용중인 Material for Mkdocs 와 Minimal Mistake 의 라이센스만 지켜주시면 됩니다.
구축하실 때 어려우신 점이 있으시다면, allen @ 이 사이트 도메인으로 이메일 주시면 제가 설명이 필요한 부분은 설명드리겠습니다(다만 질문이 들어왔던 내용은 다른 분들을 위해 개인 정보를 삭제하고 공유할 예정입니다)
읽어주셔서 감사합니다.