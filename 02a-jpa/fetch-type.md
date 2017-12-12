---
title: FetchType
---

# FetchType
아마 @OneToMany, @ManyToOne, @OneToOne, @ManyToMany
1:1, 1:n, n:m 관계의 테이블 설정할 때 추가할 수 있는 필드이다.
* fetch = FetchType.EAGER -  바로 데이터 땡겨옴  
아마 관련된 테이블들이 많을 경우에는 성능 저하가 일어나지 않을까... 싶다.
* fetch = FetchType.Lazy - 필드를 불러올 때 땡겨옴.

각각의 어노테이션에 대한 기본값을 알아보자.
* @OneToOne - FetchType.EAGER
* @OneToMany - FetchType.LAZY
* @ManyToOne - FetchType.EAGER
* @ManyToMany - FetchType.LAZY

Many가 딸려있는 애들이 여러 테이블을 들고와야 하기 때문에 LAZY가 기본 값인 것 같다.
