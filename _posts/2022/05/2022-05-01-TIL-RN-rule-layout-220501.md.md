---
layout: post
title: "React Native가 React와 다른 점"
categories: TIL ReactNative
---

# 제일 큰 것

- React Native는 웹을 만들기 위한 라이브러리가 아니고 앱을 만들기 위한 라이브러리
- 즉, html을 사용하지 않음.
- 따라서 jsx, tsx 부분에는 html태그가 아니라 ReactNative 컴포넌트가 들어가야 함.

# 컴포넌트

## View

- jsx에서 div와 같은 역할을 하는 컴포넌트
  - 블럭과 같은 것.
  - `react-natvie`에서 불러와서 사용.

## Text

- 글자를 입력하고 싶을 때는 `Text` 컴포넌트를 사용해야 함.
- `<Text>안녕하세요!</Text>` 이렇게 넣으면 글자가 나옴.

# 스타일 적용하기

## 컴포넌트에 style prop 넣기

- `style={속성}`을 넣어주면 CSS처럼 스타일을 적용할 수 있음.
- 하지만 CSS와 완전 일치하지 않음.
- 내부 값은 다시 Object(`{}`)로 넣어 주어야 함.
- style 속성 적용 부분을 외부 컴포넌트로 빼는 방법으로 작업하면 깔끔할 수 있는데,
- 그 경우에는 style 관련된 코드들이 자동완성되지 않음.
  - 이렇게 했을 때 장점은 스타일을 컴포넌트에 prop으로 바로 집어 넣은 것이 아니고 따로 뺐기 때문에 스타일 속성이 많은 경우 깔끔하게 정리할 수 있고, 재사용할 수 있다는 장점이 있음.
  - 하지만 몇몇 간단한 스타일 속성만 적용시킬 때는 컴포넌트에 prop을 바로 넣어서 사용하는 것이 나을 수도 있음.

## StyleSheet.create() 메서드 사용하기

- `StyleSheet.create()` 내부에 Object를 넣어서 여러 스타일 코드들을 정리할 수 있음.
- 이 메서드를 사용함으로써 IDE에 있는 Style 관련 속성 자동 완성 기능을 사용할 수 있다는 장점이 있음.

## 스타일 관련 React Native의 장점

- 웹에서는 스타일 관련 에러가 있어도 그걸 알려주지는 않는데,
- React Native에서는 스타일 관련된 에러가 있으면 바로 표시해 주어서 버그를 미리 예방하기 좋음.

# Components와 APIs

## 처음에 기본 세팅에 있는 StatusBar는?

- Expo에서 제공하는 API 중 하나
- 모바일 운영체제와 소통하여 배터리, 시계 등의 상태 창을 표시하고, 속성을 줄 수 있는 API

## Core Components

- [https://reactnative.dev/docs/components-and-apis](https://reactnative.dev/docs/components-and-apis)
- React Native에서 기본으로 제공하는 코어 컴포넌트
- 핵심 기능들만 제공함.
- 이전에는 많은 기능들을 제공했었지만, 그 기능들의 유지보수를 하는데 비용이 많이 발생하고,
- 유저가 직접 버그를 수정해야 하는 경우까지 발생하여 지금은 유저가 직접 제공하는 API를 사용하도록 유도하고 있음.
- (이전에 만들었던 컴포넌트들은 이제 React Native 팀에서는 제공하지 않음.)

## APIs(Third Party Package)

- Naviagation, Date Picker등 여러 기능을 다른 유저들이 만든 API로 삽입할 수 있음.
- [https://reactnative.dev/docs/accessibilityinfo](https://reactnative.dev/docs/accessibilityinfo)

## Expo SDK

- Expo에서는 React Native가 예전에 제공했던 것처럼 필수적인 기능들을 쉽게 사용할 수 있도록 API로 제공하고 있음.
- [https://docs.expo.dev/versions/latest/](https://docs.expo.dev/versions/latest/)
- 위 목록에서 필요한 것을 찾아서 사용하면 됨.

# Layout

## 특징

- `View` 컴포넌트는 `display: Flex`라고 생각하면 됨.
- 그런데 웹하고 다른 점이 웹에서 `Flex` 를 적용했을 때 기본이 `Row(행)`로 정렬되는데
- React Native는 `Column(열)`로 정렬 됨.
- 그리고 사이즈가 커져서 밖으로 삐져나간다고 스크롤바가 생기지는 않음 (React Native는 웹이 아님)

## 레이아웃 비율 맞추기

- 모바일은 기기마다 크기가 달라서 앱을 만들 때 직접 width, height값은 지정하지 않고 비율을 사용함
- 스타일 속성에 `flex: 1`이렇게 숫자를 주면 그게 비율이 됨 (1=100%)
- 만약에 `View`컴포넌트가 4개가 있는데 각각 스타일 속성은 `flex: 1`씩 지정해 주었다면
- View 컴포넌트 블록 하나당 25%의 크기를 차지하게 됨.
- 즉, flex의 값은 비율임

# Reference

- [https://nomadcoders.co/react-native-for-beginners](https://nomadcoders.co/react-native-for-beginners)
- [https://reactnative.dev/docs/components-and-apis](https://reactnative.dev/docs/components-and-apis)
- [https://reactnative.dev/docs/accessibilityinfo](https://reactnative.dev/docs/accessibilityinfo)
- [https://docs.expo.dev/versions/latest/](https://docs.expo.dev/versions/latest/)
