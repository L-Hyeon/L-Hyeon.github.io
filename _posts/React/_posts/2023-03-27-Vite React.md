---
layout: post
title: Vite와 React
categories: React
tags: [React]
---

<img src="https://scrimba.com/articles/content/images/2022/08/Create-a-new-React-app-with-Vite-main.png" />

# Vite?

> Vite(프랑스어로 "빠르다(Quick)"를 의미합니다.)은 빠르고 간결한 모던 웹 프로젝트 개발 경험에 초점을 맞춰 탄생한 빌드 도구이며, 두 가지 컨셉을 중심으로 하고 있습니다.<br /> - Vite 공식 문서 -

Vite 자체에 대한 자세한 내용은 <a href="https://l-hyun.github.io/posts/Vite/">Vite</a>에서 확인하기!

### vs Create React App

Create React App은 Webpack을 기본적으로 사용합니다.
Vite는 Webpack보다 빠른 속도를 제공하기 때문에 큰 프로젝트에서 CRA로 생성한 프로젝트보다 빠른 빌드 속도를 제공합니다.

### Vite가 지원하는 브라우저

> 기본적으로 네이티브 ES 모듈, 네이티브 ESM의 동적 Import, 그리고 import.meta를 지원하는 브라우저를 타깃으로 빌드를 수행합니다. 레거시 브라우저는 @vitejs/plugin-legacy 플러그인을 통해 지원이 가능합니다. 이와 관련해 좀 더 자세한 사항은 프로덕션 버전으로 빌드하기 섹션에서 다룹니다. <br /> - Vite 공식 문서 -

### Vite 호환성

> Vite는 버전 14.18+ 또는 16+ 의 Node.js를 요구합니다. 다만 일부 템플릿의 경우 더 높은 버전의 Node.js를 요구할 수 있습니다.

# Vite로 프로젝트 시작하기

```bash
npm create vite@latest
yarn create vite
```

### 템플릿 생성하기

```bash
# npm 6.x
npm create vite@latest my-vue-app --template vue

# npm 7+, '--'를 반드시 붙여주세요
npm create vite@latest my-vue-app -- --template vue

# yarn
yarn create vite my-vue-app --template vue

```

또한 create-vite에서 더욱 다양한 템플릿들에 대해 다루고 있습니다: vanilla, vanilla-ts, vue, vue-ts, react, react-ts, react-swc, react-swc-ts, preact, preact-ts, lit, lit-ts, svelte, svelte-ts.
