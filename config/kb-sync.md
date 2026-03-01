# 지식 베이스 수동 동기화 (KB Manual Sync)

지식 베이스를 수동으로 동기화합니다 (Fetcher + Processor 실행).

## 실행 순서

### 1단계: Fetcher 실행
- Bash로 실행: `cd ~/knowledge-base/scripts && /Users/sonseongjun/.nvm/versions/node/v20.18.1/bin/node fetcher.mjs 2>&1`
- 결과 출력 (수집된 항목 수)
- 에러 발생 시 사용자에게 알림 (exit code 2면 토큰 갱신 필요)

### 2단계: Processor 실행 여부 확인
- inbox/ 디렉토리에 파일이 있는지 확인
- 파일이 있으면 Processor 실행 제안
- 사용자 동의 시: `cd ~/knowledge-base/scripts && /Users/sonseongjun/.nvm/versions/node/v20.18.1/bin/node processor.mjs 2>&1`

### 3단계: 결과 요약

## 🔄 동기화 완료

### Fetcher 결과
- 메일: X건 수집
- Teams 채팅: Y건 수집
- Teams 채널: Z건 수집

### Processor 결과 (실행한 경우)
- 분류된 항목: N건
- 프로젝트별: ...

마지막 동기화: {timestamp}
