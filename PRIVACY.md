# 개인정보 및 외부 API 전송 안내

최종 수정일: 2026-08-22
프로그램/공급자: SubBridgeAI / 안김 소프트

## 처리 개요

SubBridgeAI는 별도의 안김 소프트 서버나 사용자 계정을 운영하지 않습니다. 사용자가 AI 번역을 시작할 때 선택한 자막 내용, 번역 지시, 대상 언어, 용어집 및 문맥 정보가 사용자가 선택한 Google Gemini API 또는 OpenAI API로 직접 전송됩니다.

사용자는 전송할 자막에 대한 적법한 권한이 있어야 하며 개인정보·기밀·미공개 자료를 보내기 전에 해당 API 공급자의 정책을 확인해야 합니다.

## API 키

- API 키는 사용자가 직접 입력하며 프로그램 제작자의 공용 키는 포함하지 않습니다.
- 1회·실행 중·시간제한 모드는 키를 파일에 저장하지 않습니다. 시간제한 키는 진행 중인 번역이 끝난 뒤 만료 처리합니다.
- 로컬 저장을 선택하면 Windows DPAPI로 암호화하여 현재 Windows 사용자 계정에서만 복호화할 수 있게 저장합니다.
- 설정, 암호화된 키, 용어집, 로그는 `%LOCALAPPDATA%\안김 소프트\SubBridgeAI`에 보관합니다.
- API 키는 번역 요청을 위해 실행 중 메모리에 복호화될 수 있습니다. DPAPI는 실행 중인 악성 프로그램이나 이미 침해된 Windows 계정까지 방어하지 못합니다.
- API 키와 Authorization 헤더 형태는 앱 로그에서 마스킹하며 Git/릴리스 보안 검사 대상입니다.

## 공급자별 유의사항

OpenAI API 요청은 응답 객체의 애플리케이션 상태 저장을 줄이기 위해 `store=false`를 사용합니다. 다만 OpenAI의 악용 방지 로그 등 공급자 차원의 보관에는 별도 정책이 적용될 수 있습니다. OpenAI는 API 데이터를 사용자가 명시적으로 동의하지 않는 한 모델 학습에 사용하지 않는다고 안내합니다.

Gemini API의 무상 서비스는 입력과 출력이 제품 개선에 사용되거나 사람이 검토할 수 있습니다. 민감하거나 기밀인 자료에는 유상 서비스 및 해당 계약 조건을 검토하세요. Gemini API 이용에는 공급자가 정한 연령·대상 서비스 제한이 적용됩니다.

공식 정책:

- [OpenAI API 데이터 관리](https://platform.openai.com/docs/guides/your-data)
- [Google Gemini API 추가 이용약관](https://ai.google.dev/gemini-api/terms)
- [Google Gemini API 키 보안](https://ai.google.dev/gemini-api/docs/api-key)

## 로컬 데이터와 삭제

프로그램은 설정, 용어집, 화면 배치 및 작업 로그를 로컬에 저장할 수 있습니다. 프로그램의 보안 설정에서 공급자별 키 또는 모든 키를 삭제할 수 있습니다. 전체 로컬 데이터는 프로그램 종료 후 위 Local AppData 폴더를 사용자가 직접 삭제하여 제거할 수 있습니다.

## 비용과 번역 결과

API 요금과 할당량은 사용자의 Google/OpenAI 계정에 부과됩니다. AI 번역은 부정확할 수 있으므로 게시·배포·업무 사용 전에 반드시 검수하세요.

## 문의

일반 문의는 [GitHub Issues](https://github.com/qwerzxc1090/SubBridgeAI/issues), 취약점과 민감한 신고는 [GitHub Private Vulnerability Reporting](https://github.com/qwerzxc1090/SubBridgeAI/security/advisories/new)을 사용합니다. 앱은 피드백과 사용 기록을 자동 전송하지 않습니다.
