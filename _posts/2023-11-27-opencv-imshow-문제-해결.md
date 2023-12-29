---
layout: post
title: OpenCV imshow 문제 해결
date: 2023-11-27 09:12 +0900
category: [Python, OpenCV]
tags: [Python, OpenCV, Computer Vision]
---

## 문제

![OpenCV imshow가 시작됨](assets/img/posts/231127-1.png)

위 처럼 OpenCV imshow가 시작되었지만, 아무 반응이 없는 모습이다.

![OpenCV 오류](assets/img/posts/231127-2.png)

이 후 조금 기다리면 위와 같은 오류가 나타나게 된다.

## 해결

결론부터 작성하자면, OpenCV imshow를 사용할 때는 `cv2.waitKey()` 함수를 **무조건** 사용해야 한다.

`cv2.destoryAllWindows()` 함수는 선택이지만, `cv2.waitKey()` 함수가 없다면 imshow가 제대로 작동하지 않는다.

![수정된 코드](assets/img/posts/231127-3.png)

위와 같이 코드를 수정하면 정상적으로 작동한다.

나의 경우에는 VideoCapture Release와 destoryAllWindows를 별도의 Exit 로직에서 구현하느라, imshow를 사용하는 부분에서는 `cv2.waitKey()` 함수를 사용하지 않았는데, 이 부분을 수정하니 정상적으로 작동하였다.

## 사용된 코드

<https://github.com/suk-6/walking-assistance>
