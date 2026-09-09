---
title: '유용한 Obsidian 플러그인'
date: 2022-11-06 14:54:32 +0900
tags:
  - Obsidian
  - JS
  - Templater
excerpt: Obsidian에서 유용한 플러그인을 사용해 생산성을 높이는 방법
permalink: /useful-obsidian-plugins/
---

## Templator

### Preview
<img width="600" src="{{ '/assets/images/post_figures/useful-obsidian-plugins/Book.gif' | relative_url }}" alt="Book plugin preview">
<img width="600" src="{{ '/assets/images/post_figures/useful-obsidian-plugins/Daily.gif' | relative_url }}" alt="Daily plugin preview">

[Templater](https://github.com/SilentVoid13/Templater)

노션의 템플릿 처럼 Obsidian에서도 문서를 템플릿화 하여 생성할 수 있다.
템플릿을 만드는 방법에는 여러가지가 있는데, 기본적으로 Templator 라이브러리 설치 시 `templates` 폴더 안에 있는 템플릿들을 불러오게 되어 있다.

템플릿을 수동으로 작성하여 템플릿들을 만들 수 있는데, 예를들어 문서가 만들어지는 시간을 기준으로 문서의 내용 및 데이터를 작성할 수 있다. 템플릿을 어떻게 작성하는지는 [링크](https://silentvoid13.github.io/Templater/)를 참조하면 쉽게 알 수 있다.

아래 코드는 내가 만든 `Book` 템플릿으로, 문서 생성을 하는 시간을 기준으로 `creation date`를 설정하고, 평점과 작가를 입력받아 책 문서를 자동으로 생성해주는 템플릿 코드이다.

```
---
creation date: <% tp.file.creation_date() %>
author: <% tp.system.prompt("Please enter author") %>
rate: <% tp.system.suggester(["1", "2", "3", "4", "5"], [1, 2, 3, 4, 5]) %>
---

# <% tp.file.title %>

## Comments

## Etc



### Please put category tags below
#book

```

아래 코드는 `Daily` 템플릿으로, 내가 만든 `daily_template_script`로 부터 정보를 읽어온 뒤 문서를 자동화 해주는 템플릿이다. 간단한 JS 파일만으로 특정 요일에 어떤 to-do 리스트들을 추가할 것인지 설정할 수 있다.
```
---
creation date: <% tp.file.creation_date() %>
---

# <% tp.file.title %>

## Day Planning

### What's Non-negotiable? (Important & Urgent)
<% tp.user.daily_template_script(0) %>

### What's Important to Me? (Important & Not Urgent)
<% tp.user.daily_template_script(1) %>

### What Am I Obligated to Do? (Not Important & Urgent)
<% tp.user.daily_template_script(2) %>

### What Do I Want to Do Eventually? (Not Important & Not Urgent)
<% tp.user.daily_template_script(3) %>

## Reflections

### What Did I Do Today?
`Did I Finish Everything I Started or Do I Need to Plan to Continue Where I Left Off?`
-

### What Did I Not Finish Today?
`What Was it That Caused Me to Not Be Abled to Finish, is This Something I Can Do Something to Avoid?`
-

### What Unexpected Events Happened Today?
`Were They Good or Were They Bad? What Caused These Events?`
-

### What Did I Learn Today?
`Did I Have an Insight or an Epiphany or Was it Through Deliberate Practice?`
-

## Summary


## Plan for Tomorrow

### What to Eat?
-
### What to Do?
-


<< [[<% tp.date.now("YYYY-MM-DD", -1) %>]] | [[<% tp.date.now("YYYY-MM-DD", 1) %>]] >>

#일간일지
#todo
```

```js
const commonTodoList = [
  [],
  [
    '7시 기상',
    '12시 취침',
    '생각 정리하기',
    '30분 이상 책 읽기',
  ],
  [],
  [
    '영양제 먹기',
    '영어 섀도잉',
  ],
];

const todoList = [
  // Sun
  [
    [],
    ['알고리즘 문제 풀기'],
    [],
    ['산책 하기'],
  ],
  // Mon
  [
    ['헬스 가기'],
    [],
    [],
    [],
  ],
  // Tue
  [
    ['헬스 가기'],
    [],
    ['틔움 상태 확인'],
    ['산책 하기'],
  ],
  // Wed
  [
    [],
    [],
    [],
    [],
  ],
  // Thu
  [
    ['헬스 가기'],
    [],
    [],
    ['이불 빨래 하기', '산책 하기'],
  ],
  // Fri
  [
    ['헬스 가기'],
    [],
    [],
    [],
  ],
  // Sat
  [
    [],
    ['알고리즘 문제 풀기'],
    ['틔움 상태 확인'],
    [
      '이불 빨래 하기',
      '집 청소',
      '화장실 청소',
    ],
  ],
]

const todos = (priority) => {
  let result = '';
  commonTodoList[priority].forEach((item) => {
    result += `- [ ] ${item}\n`;
  })
  todoList[new Date().getDay()][priority].forEach((item) => {
    result += `- [ ] ${item}\n`;
  });
  result += '- [ ] \n';
  return result;
}

module.exports = todos;

```
위 템플릿에 자신이 해야하는 일들로 수정하면 자신만의 to-do 리스트 템플릿을 쉽게 만들 수 있다.

## Checklist

### Preview

<img width="600" src="{{ '/assets/images/post_figures/useful-obsidian-plugins/Checklist.gif' | relative_url }}" alt="Checklist plugin preview">

[Checklist](https://github.com/delashum/obsidian-checklist-plugin)

위 플러그인으로 템플릿을 만들었다면 이제 Checklist 플러그인으로 해야 할 일들을 간편하게 체크할 수 있다. 플러그인을 설치할 경우 우측에서 체크 리스트들을 볼 수 있고, 해야할 일과 오늘 한 일을 한눈에 볼 수 있다. (설정해서 한 일의 경우 숨김처리 할 수도 있다.)

## Calendar

### Preview
<img width="600" src="{{ '/assets/images/post_figures/useful-obsidian-plugins/Calendar.gif' | relative_url }}" alt="Calendar plugin preview">

[Calendar](https://github.com/liamcain/obsidian-calendar-plugin)

이 플러그인 또한 Daily to-do 리스트를 사용하고 있을 때 효율을 더 좋게 사용할 수 있다.
Checklist 플러그인과 마찬가지로 우측에서 달력을 확인할 수 있고 해당 날짜에 작성한 문서들을 확인하고 바로 이동할 수 있다.

## Outliner

### Preview
<img width="600" src="{{ '/assets/images/post_figures/useful-obsidian-plugins/Outliner.gif' | relative_url }}" alt="Outliner plugin preview">


[Outliner](https://github.com/vslinko/obsidian-outliner)

리스트들을 작성하다보면 리스트의 순서를 바꾸고 싶을 때가 있는데, Outliner 템플릿을 사용하면 단축키로 리스트들을 이동할 수 있다.

