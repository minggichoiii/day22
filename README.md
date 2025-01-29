# day22
def min_operations(N):
    # dp 배열 초기화 (0부터 N까지 연산 횟수 저장)
    dp = [0] * (N + 1)

    # dp[1]은 0으로 설정 (1은 이미 목표이므로 연산이 필요 없음)
    for i in range(2, N + 1):
        dp[i] = dp[i - 1] + 1  # 기본적으로 1을 빼는 연산

        # 2로 나눠지면, dp[i]를 최소값으로 업데이트
        if i % 2 == 0:
            dp[i] = min(dp[i], dp[i // 2] + 1)

        # 3으로 나눠지면, dp[i]를 최소값으로 업데이트
        if i % 3 == 0:
            dp[i] = min(dp[i], dp[i // 3] + 1)

    # N에 대한 최소 연산 횟수를 반환
    return dp[N]

# 입력 받기
N = int(input())

# 결과 출력
print(min_operations(N))
