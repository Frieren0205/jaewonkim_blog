---
title: 카멜 케이스와 파스칼 케이스 キャメルケース・パスカルケース
published: 2025-09-19
description: 가독성과 유지보수성을 늘리는 변수명 적는 방법
image: ''
tags: [C#, Study, Develop]
category: 'C#'
draft: false 
lang: 'ko'
---

# 카멜 케이스와 파스칼 케이스란 キャメルケースとパスカルケースとは

카멜 케이스, 라스칼 케이스는 변수명, 함수명 등을 작성할 때 쓰는 표기법 중 하나.
각각의 작성법, 사용처는 다음과 같다.

## 카멜 케이스
* <b> 첫 단어는 소문자 </b>로 시작하고, 이후 각 단어의 첫 글자를 대문자로 쓰기
* 예시 : 
    * ``myVariableName``
    * ``getUserInfo``
    * ``int playerHealth = 10;``
    * ``float moveSpeed = 5.0f;``
    * ``private int healthPoints;``
    * ``private float _jumpForce;``

제일 아래의 ``private float _jumpForce`` 처럼 관례적으로``_``를 붙이는 경우도 있다고 한다.

## 파스칼 케이스
* <b>모든 단어의 첫 글자를 대문자</b>로 작성
* 예시 :
    * ``PlayerScore, UpdatePosition, IsActive``
    * ``public class PlayerController``
    * ``public struct PlayerStats``
    * ``pulbic interface IDamageable``
    * ``public void UpdatePosition()``
    * ``public bool IsActive()``
    * ``public int HealthPoints { get; set; }``
    * ``public float MoveSpeed { get; set; }``

C# / Unity에서는 위의 예시처럼 다음과 같은 곳에서 사용한다.</br>
<b>클래스</b>, <b>구조체</b>, <b>인터페이스</b>, <b>메소드</b>, <b>public 프로퍼티</b> 명 등</br>
``MonoBehaviour`` 메소드 ``Start``, ``Update``, ``OnTriggerEnter`` 등

``public`` 또는 ``[SerializeField]``가 붙은 직렬화 필드에서는 파스칼 케이스를 쓰기도 하지만</br>
팀/프로젝트마다 카멜 케이스를 사용하는 경우도 있다고 한다.

<b>요약</b></br>
C# / Unity에선
* 클래스, 메소드, 프로퍼티, 인터페이스 등 : <b>파스칼 케이스</b>
* 변수, 매개변수, private 필드 : <b>카멜 케이스</b>
* 이는 절대적인 것이 아니고, <b>일관성</b>이 중요함.
* 팀/프로젝트의 컨벤션을 따라가는 것이 좋음.