---
title: Algorithm 1.DP
author:
  name: osnim
  link: https://github.com/osnim
date: 2022-02-11 00:30:00 +0900
categories: [Algorithm]
tags: [BOJ, DP, Algorithm, Dynamic Programing, Python]
---

# 동적 프로그래밍, 동적 계획법 (Dynamic Programing)

### 다이나믹(Dynamic)의 유래

다이나믹 프로그래밍에서 다이나믹의 의미는 동적할당의 다이나믹과 다릅니다. 동적할당에서 다이나믹은 프로그램이 실행되는 도중에 메모리를 동적으로 할당하는 자료구조 기법으로 메모리 공간을 낭비하지 않기 위해 사용합니다.

하지만 다이나믹 프로그래밍에서 다이나믹의 의미는 크게 의미를 부여하지 않습니다. 다이나믹 프로그래밍을 먼저 만든 사람도 이름이 단지 멋있어서 다이나믹을 붙였다고 합니다.

### DP의 장점

다이나믹 프로그램이은 메모리 공간을 사용하여

### DP의 방식 2가지

1. 탑-다운 (Top-Down)

   재귀 함수를 이용해서 DP를 작성하는방법으로 큰 문제를 해결하기 위해 작은 문제를 호출하는 방식으로 메모이제이션(memoization)을 사용하여 이전에 푼 결과를 테이블이나 리스트에 저장한다.

   DP의 대표적인 문제인 피보나치 수열을 간단하게 탑 다운 방식으로 코드를 작성하면 다음과 같다.

   ```python
   dp = [0]*(n+1)

   def sol(x):

      if x == 1 or x == 2:
         return 1

      if dp[x] != 0:
         return dp[x]

      dp[x] = sol(x-1) + sol(x-2)
      return dp[x]

   print(sol(n))

   ```

2. 바텀-업 (Bottom-up)

   반복문을 이용하여 작은 문제부터 풀어 점점 큰 문제를 해결하는 방식으로 탑-다운 방식처럼 메모하는 방법을 채택하지만 바텀 업 방식에서는 메모이제이션이라는 말을 사용하는 대신 'DP 테이블' 또는 Tabulation 이라는 용어를 사용한다고 한다. 하지만 그 본질은 메모이제이션과 크게 다르지 않다.

   피보나치 수열을 바텀-업 방식으로 작성하면 다음과 같다

   ```python

   dp = [0]*(n+1)

   dp[1] = 1 #기저
   dp[2] = 1 #기저

   for i in range(3, n+1):
      dp[i] = dp[i-1] + dp[i-2]

   print(dp[n])
   ```

### DP 문제 조건

다이나믹 프로그래밍을 사용할 때는 다음과 같습니다.

1. 작은 문제의 계산들이 반복적으로 일어나고 (Overlapping Subproblems, 겹치는 부분 문제)

2. 같은 문제를 구할 때 마다 문제의 정답이 같은 경우 (Optimal Substruction 최적 부분 구조).

### DP 풀이, 접근 방법

      1.  DP를 풀 때, 먼저 규칙성을 찾습니다. 대부분 시간이나 공간의 변화에 따라 현재와 과거를 비교하여 규칙이나 변화 유형들을 찾아냅니다.

      2.  그 규칙 속에서 반복되는 계산을 찾아내고 이를 점화식으로 표현합니다.

      3.  반복되는 계산을 저장할 리스트나 배열같은 메모리 공간을 할당합니다. (Tabulation)

      4.  뒤에 오는 값은 무시하고 앞에서 계산한 결과를 이용하여 점화식을 표현합니다.

      5.  기저가 필요 할 땐 (basis, 피보나치의 dp[1], dp[2] 같은 초기 값) 먼저 선언합니다.

      6.  반복문으로 min, max, 또는 연산하여 현재 값을 리스트나 테이블에 저장합니다.

저는 최대한 DP 문제를 바텀-업 (반복문)을 이용해서 해결하려고 노력하고 있습니다. 탑-다운 (재귀함수)를 사용하면 시간복잡도가 매우 커져 제한 시간 내에 문제를 풀지 못하는 경우가 발생할 확률이 높기 때문입니다.

특히 DP 문제는 책으로 예제와 함께 기본기를 먼저 다진 후, 시간이 걸리더라도 답지 없이 스스로 점화식을 생각해내는 힘을 기르는 것이 가장 중요한 것 같습니다.
