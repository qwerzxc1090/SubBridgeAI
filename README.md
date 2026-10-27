# SubBridgeAI

> 공개 배포 전용 저장소입니다. 프로그램 소스 코드는 포함하지 않습니다.
> This repository contains downloads and user documentation only; application source code is not included.

[한국어·영어 사용 설명서 ZIP / User guides ZIP](https://github.com/qwerzxc1090/SubBridgeAI/releases/download/v0.1.0-beta.5/SubBridgeAI-v0.1.0-beta.5-user-guides-ko-en.zip)

> 릴리스 하단의 `Source code (zip/tar.gz)`는 GitHub가 자동 표시하는 저장소 문서 묶음입니다. 프로그램 소스가 아닙니다. 설명서는 위의 **사용 설명서 ZIP**을 이용하세요.
> GitHub automatically labels repository archives as `Source code`. These contain repository documents only. Use the **User guides ZIP** above for the manuals.

[한국어 사용 설명서](#한국어-사용-설명서) · [English user guide](#english-user-guide)

[공개 베타 v0.1.0-beta.5 다운로드 / Download public beta](https://github.com/qwerzxc1090/SubBridgeAI/releases/tag/v0.1.0-beta.5)

[후기·질문·개선 요청 / Community discussions](https://github.com/qwerzxc1090/SubBridgeAI/discussions) · [게시판 이용 안내 / Start here](https://github.com/qwerzxc1090/SubBridgeAI/discussions/1)

[후기 작성 / Share feedback][discussion-feedback] · [질문하기 / Ask a question][discussion-question] · [개선 제안 / Suggest an idea][discussion-idea]

## 한국어 사용 설명서

공개 베타 v0.1.0-beta.5 | 2026-10-27 | 안김 소프트

### 1. 프로그램 소개

SubBridgeAI는 SRT 자막의 원문과 번역문을 비교·편집하고, 원본 타임코드에
번역문을 결합해 새 SRT를 만드는 Windows 프로그램입니다. Gemini 또는
OpenAI의 API 키를 직접 입력하면 앱 안에서 AI 번역을 사용할 수 있습니다.
AI 없이 SRT/TXT 열기, 편집, 추출, 병합 기능도 사용할 수 있습니다.

### 2. 다운로드와 실행

공식 저장소: https://github.com/qwerzxc1090/SubBridgeAI
공식 다운로드: https://github.com/qwerzxc1090/SubBridgeAI/releases

- 대상 환경: Windows 10/11 x64. 베타 버전으로 환경별 차이가 있을 수 있습니다.
- 설치 프로그램과 Python 설치가 필요하지 않습니다.
- 포터블 ZIP을 받았다면 압축을 모두 푼 뒤 EXE를 실행합니다.
- 배포 패키지에는 EXE, readme.txt, readme_en.txt 및 이용약관·개인정보·
  제3자 구성요소 안내가 포함됩니다.
- ZIP과 EXE의 SHA-256은 해당 파일명 뒤에 .sha256이 붙은 파일로 제공합니다.
  PowerShell에서 다음 명령으로 실제 해시를 구해 체크섬 파일과 비교합니다.

```powershell
Get-FileHash .\다운로드한파일.zip -Algorithm SHA256
```

- 이번 공개 베타에는 코드 서명이 없어 Windows에 알 수 없는 게시자 또는
  SmartScreen 경고가 표시될 수 있습니다. 공식 다운로드 출처와 SHA-256을 확인하세요.
  체크섬은 파일 일치 확인용이며 게시자 신원을 인증하지 않습니다.
  보안 프로그램을 끄거나 출처를 확인하지 않은 파일을 실행하지 마세요.

### 3. 처음 실행할 때

앱의 이용약관 안내를 확인합니다. AI 번역을 사용할 경우 F2 또는 상단의
[설정]을 눌러 [보안] 탭에서 본인의 Gemini/OpenAI API 키를 입력합니다.
번역을 시작할 때 표시되는 외부 API 전송 안내도 확인하세요.

배포본에는 제작자의 공용 API 키가 들어 있지 않습니다. API 키 발급, 사용료,
할당량과 모델 접근 권한은 사용자의 공급자 계정에서 관리합니다.
Gemini 4 Argon은 Gemini API 유료 등급이 필요합니다.

키 유지 방식은 다음 중 선택할 수 있습니다.
- 1회 사용 후 삭제: 한 번의 번역 작업이 끝나면 메모리에서 제거합니다.
- 이번 실행 동안만: 앱이 실행되는 동안 유지합니다.
- 시간제한: 지정 시간이 지나면 제거합니다. 번역 중 만료되면 작업이
  완료·실패·중단될 때까지 제거를 보류합니다.
- 이 PC에 암호화 저장: Windows DPAPI로 암호화하여 현재 Windows 사용자
  계정에서 다시 사용할 수 있게 저장합니다. 다른 PC로의 키 이전용이 아닙니다.

키는 [보안] 탭에서 공급자별 또는 전체 삭제할 수 있습니다. 앱에서 지워도
공급자 계정의 키 자체가 폐기되는 것은 아닙니다. 유출이 의심되면 공급자
콘솔에서 해당 키를 폐기하고 새 키를 발급하세요.

### 4. AI 번역으로 SRT 만들기

1. [파일 열기]로 원본 SRT를 엽니다.
   표에는 순번/타임코드, 원본 텍스트, 번역 텍스트가 표시됩니다.
2. [AI 모델]과 번역 대상 언어를 선택합니다.
3. 번역할 범위를 지정합니다.
   - 구간 번역: [모두 번역]을 끄고 1-10 또는 1,3,5처럼 입력합니다.
     한 번에 지정할 수 있는 구간은 최대 50개 자막입니다.
   - 전체/나머지 번역: [모두 번역]을 켜고 시작 순번을 입력합니다.
     해당 순번부터 마지막 자막까지 처리합니다.
4. [AI 번역] 또는 Ctrl+Enter로 시작합니다.
   요청 단위는 10~100개 자막이며 기본값은 30개입니다.
   문맥을 함께 보내되 입력 순번과 자막 수가 맞는 결과를 적용합니다.
5. 결과를 읽고 번역 열을 더블클릭하여 필요한 부분을 수정합니다.
6. [병합하기] 또는 Ctrl+S로 새 SRT를 저장합니다.
   화면에서 편집한 내용을 파일로 남기려면 병합 저장을 완료해야 합니다.

진행 창에서 중단을 요청해도 이미 보낸 API 요청은 바로 끝나지 않을 수
있습니다. 완료된 번역을 확인한 뒤 필요한 범위부터 다시 시작하세요.
이미 처리한 범위를 다시 번역하면 추가 API 사용료가 발생할 수 있습니다.

### 5. 외부에서 번역한 TXT 사용하기

1. 원본 SRT를 엽니다.
2. [추출하기]로 원문을 TXT에 저장하고 외부에서 번역합니다.
3. [번역 TXT 열기]로 번역문을 불러옵니다.
4. 원문 자막과 번역문이 같은 순서로 맞는지 확인하고 [병합하기]로 저장합니다.

원본 자막 한 개와 번역 TXT 한 줄이 대응하도록 줄 수와 순서를 유지하세요.
줄을 합치거나 나누면 이후 자막이 어긋날 수 있습니다. 앱이 줄 수 차이를
경고하면 파일을 수정하여 일치시킨 뒤 병합하세요.

### 6. 모델·언어·용어집

Gemini: Gemini 4 Argon, Gemini 3.1 Pro Preview, Gemini 3.7 Flash
GPT: GPT-6.1 Sol, GPT-6 Sol, GPT-6 Luna, GPT-5.6 Sol, GPT-5.6 Terra, GPT-5.6 Luna

모델 목록에 있어도 계정·지역·요금제·공급자 정책에 따라 사용할 수 없을 수
있습니다. 번역 언어는 선택한 모델에 맞춰 최대 10개가 표시되며 한국어,
러시아어, 영어는 항상 포함됩니다. 추출용 언어 코드는 TXT 파일명에 쓰이며,
AI 번역 대상 언어는 실제 번역 언어를 지정합니다.

모델 목록 아래 [모델 노출]에서 추천(기본값), 전체, 사용자 정의를 선택합니다.
추천은 Gemini와 GPT에서 각각 3개를 표시합니다. GPT 추천은 6.1 Sol, 6 Sol,
6 Luna이며 Gemini는 현재 등록된 3개 모델입니다. 전체는 앱에 등록된 모든 모델을 표시합니다.
사용자 정의에서는 [모델 선택…]을 눌러 원하는 모델을 최소 1개 선택하고 적용하세요.
노출 방식과 사용자 정의 목록은 다음 실행에도 유지됩니다. 선택 중인 모델이 숨겨지면
같은 카테고리의 첫 표시 모델로 전환하며, 해당 카테고리가 없으면 목록 첫 모델을 선택합니다.
F2 설정의 [모델] 탭에서도 노출 방식과 사용자 정의 목록을 편집할 수 있습니다.
[확인] 또는 Ctrl+S로 저장하면 상단 목록에도 반영되며, [취소]하면 편집을 취소합니다.

번역 언어 선택 오른쪽의 ?에 마우스를 올리면 선택 모델의 지원 추론 강도와 용도를
확인할 수 있습니다. 현재 적용 강도는 ? 도움말에서만 안내하며,
모델 선택 목록에는 추론 정보를 표시하지 않습니다. 강도를 변경하는 기능은 제공하지 않습니다.

F3으로 용어집을 열고 원본단어:번역단어 형식으로 한 줄씩 입력할 수 있습니다.
용어집은 번역 지시로 전달되므로 결과에 정확히 반영됐는지 확인하세요.
상단 [프롬프트 미리보기]에서 번역 지시를 확인할 수 있습니다.

### 7. 검수와 편집

- 번역 열 더블클릭: 수정 후 Enter 또는 다른 곳 클릭으로 적용, Esc로 취소.
- Ctrl+F: 원문·번역 검색. 찾기 또는 Enter로 다음 결과로 이동.
- F4 또는 [검토 필요 찾기]: 경고 항목을 차례로 확인.
- 기본 길이 경고: 번역의 각 표시 줄이 45자를 넘으면 검토 대상으로 표시.
  설정의 검수 항목에서 길이 경고를 켜거나 끄고 기준을 10~200자로 바꿀 수 있습니다.
- `<빈줄>`, 인코딩이 깨진 문자, 길이 초과 표시가 있으면 원문과 비교해 수정하세요.
- 원본 텍스트가 200자를 넘는 자막은 AI 번역에서 제외되고
  [200자 초과 번역 불가]로 표시됩니다. 내용을 검토하여 수동으로 수정하세요.
- [작업 내용]을 켜면 진행 상황과 오류를 로그 창에서 확인할 수 있습니다.
- AI 번역 결과는 잘못되거나 누락될 수 있습니다. 게시 전에 직접 검수하세요.

### 8. 단축키

```text
F2                 설정
F3                 용어집 설정
F4                 다음 검토 항목
Ctrl+Enter         AI 번역
Ctrl+S             병합하여 SRT 저장
Ctrl+F             검색
Ctrl+Z / Ctrl+Y    되돌리기 / 다시 실행
위/아래, PgUp/PgDn 표 탐색
```

### 9. 파일 저장·설정·개인정보

추출 파일명에는 언어 코드가, AI 번역 후 병합 파일명에는 대상 언어 코드와
모델 접미사가 붙을 수 있습니다. 저장 대화상자에서 이름을 바꿀 수 있습니다.
원본 파일은 별도로 보관하고 새 이름으로 저장하는 것을 권장합니다.

설정, 용어집, 로그 등은 다음 Windows 사용자 폴더에 저장됩니다.
`%LOCALAPPDATA%\안김 소프트\SubBridgeAI`

EXE를 다른 폴더로 옮겨도 같은 Windows 계정의 설정은 유지됩니다. 다른 PC로
EXE만 복사하면 이전 PC의 설정과 키는 따라가지 않습니다. 앱 종료 후 위
폴더를 삭제하면 로컬 데이터가 제거됩니다. 필요한 설정과 용어집은 먼저
본인이 관리하는 안전한 위치에 백업하세요.

AI 번역을 시작하면 선택한 자막, 지시문, 대상 언어, 용어집과 문맥 정보가
Google 또는 OpenAI로 전송됩니다. 전송 권한이 있는 자료만 사용하세요.
앱은 피드백이나 사용 기록을 제작자에게 자동 전송하지 않습니다.
공급자의 처리 정책과 자세한 내용은 함께 제공한 PRIVACY.md를 확인하세요.

### 10. 수동 업데이트

1. 공식 GitHub Releases에서 새 버전의 변경 사항을 확인합니다.
2. 진행 중인 작업을 저장하고 앱을 종료합니다.
3. 새 ZIP을 내려받아 체크섬을 확인하고 별도 폴더에 압축을 풉니다.
4. 새 EXE를 실행하여 버전과 기존 설정을 확인합니다.

자동 다운로드·자동 교체는 제공하지 않습니다. 설정은 같은 Windows 계정의
사용자 폴더에 남습니다. 문제가 있으면 보관한 이전 버전으로 돌아가기 전에
현재 설정을 백업하고, 이전 버전과의 설정 호환성을 확인하세요.

### 11. 문제가 생겼을 때

사용 후기·질문·개선 요청은 [Discussions 게시판](https://github.com/qwerzxc1090/SubBridgeAI/discussions)에 남겨 주세요.

- [사용자 후기](https://github.com/qwerzxc1090/SubBridgeAI/discussions/categories/사용자-후기): 사용 경험과 불편한 점 공유
- [질문·답변](https://github.com/qwerzxc1090/SubBridgeAI/discussions/categories/질문-답변): 사용 방법 문의와 답변 채택
- [개선 요청](https://github.com/qwerzxc1090/SubBridgeAI/discussions/categories/개선-요청): 기능·사용성 개선 제안
- [공지·이용 안내](https://github.com/qwerzxc1090/SubBridgeAI/discussions/categories/공지-이용-안내): 업데이트와 [처음 오신 분을 위한 안내](https://github.com/qwerzxc1090/SubBridgeAI/discussions/1)

글·댓글 작성에는 GitHub 로그인이 필요합니다. 실행 오류와 재현 가능한 버그는 아래 Issues 경로를 이용하세요.

- 모델 사용 불가/403: 해당 공급자의 키, 모델 접근 권한과 결제 설정을 확인.
- 429/할당량 초과: 공급자 콘솔에서 속도 제한, 사용량과 잔액을 확인.
- 네트워크 오류: 연결 상태를 확인하고 이미 완료된 범위 이후부터 재시도.
- 병합 불가: 빈 번역과 원문/TXT 줄 수 차이를 확인.
- TXT가 어긋남: 원본 자막 수와 TXT 줄 수·순서를 다시 맞춤.
- AI 결과 오류: 번역 셀에서 수정하고 다시 병합 저장.

베타 피드백 버튼 또는 다음 주소에서 버그·개선 의견을 남길 수 있습니다.
https://github.com/qwerzxc1090/SubBridgeAI/issues/new/choose

앱 버전, Windows 버전, 재현 순서, 기대한 결과와 실제 결과를 적어 주세요.
API 키, settings.json, 개인 자막, 번역문, 개인 경로가 담긴 로그는 올리지 마세요.
보안 취약점은 다음 비공개 신고 경로를 사용하세요.
https://github.com/qwerzxc1090/SubBridgeAI/security/advisories/new

### 12. 이용 조건

SubBridgeAI는 안김 소프트의 Freeware입니다. 허용되는 이용 범위와 제한은
함께 제공한 LICENSE와 EULA.md를, 구성요소 고지는 THIRD_PARTY_NOTICES.md를
확인하세요. API 사용료와 번역 결과 검수는 사용자 책임입니다.

Copyright © 2026 안김 소프트. All rights reserved.

------------------------------

## English user guide

Public beta v0.1.0-beta.5 | 2026-10-27 | 안김 소프트 (Angim Soft)

### 1. About SubBridgeAI

SubBridgeAI is a Windows app for comparing and editing SRT subtitles and their
translations, then saving a new SRT with the original timecodes. You can translate
inside the app with your own Gemini or OpenAI API key. Opening, editing,
extracting, and merging SRT/TXT files can also be used without AI.

The interface is currently in Korean. Korean button names are included below.

### 2. Download and launch

Official repository: https://github.com/qwerzxc1090/SubBridgeAI
Official downloads: https://github.com/qwerzxc1090/SubBridgeAI/releases

- Target environment: Windows 10/11 x64. Behavior may vary during the beta.
- No installer or separate Python installation is required.
- If you download a portable ZIP, extract all files before launching the EXE.
- The package contains the EXE, readme.txt, readme_en.txt, and the license,
  privacy, and third-party component notices.
- A checksum file ending in .sha256 is provided for the ZIP and EXE. In
  PowerShell, calculate the hash and compare it with the checksum file:

```powershell
Get-FileHash .\downloaded-file.zip -Algorithm SHA256
```

- This public beta is not code signed. Windows may show an unknown publisher or
  SmartScreen warning. Verify the official download source and SHA-256 checksum.
  A checksum verifies file equality; it does not authenticate the publisher.
  Do not disable security software or run files of unknown origin.

### 3. First launch and API keys

Read the terms shown by the app. To use AI translation, press F2 or click
[설정] (Settings), then enter your own Gemini/OpenAI API key on the [보안]
(Security) tab. Read the external API transmission notice before translating.

The distribution does not include a shared developer API key. Your provider
account controls key issuance, charges, quotas, and model access. Gemini 4 Argon
requires the paid tier of the Gemini API.

Choose a key retention mode:
- [1회 사용 후 삭제] (Remove after one use): removed from memory when the
  translation job ends.
- [이번 실행 동안만] (This session only): retained while the app is running.
- [시간제한] (Time limit): removed after the selected period. Expiration is
  deferred until a running translation completes, fails, or stops.
- [이 PC에 암호화 저장] (Save encrypted on this PC): saved with Windows DPAPI
  for reuse by the same Windows user. This is not a key transfer mechanism.

Keys can be removed per provider or all at once on the Security tab. Removing a
key from the app does not revoke it at the provider. If exposure is suspected,
revoke the key in the provider console and issue a replacement.

### 4. Create a translated SRT with AI

1. Click [파일 열기] (Open file) to load the original SRT.
   The table shows index/timecode, original text, and translated text.
2. Select [AI 모델] (AI model) and the target translation language.
3. Select the subtitles to translate:
   - Range: turn off [모두 번역] (Translate all) and enter a range such as 1-10
     or a list such as 1,3,5. Up to 50 subtitles can be selected in this mode.
   - All/remaining: turn on [모두 번역] and enter a starting subtitle number.
     The app processes that subtitle through the end of the file.
4. Click [AI 번역] (AI translation) or press Ctrl+Enter.
   The request batch size is 10–100 subtitles; the default is 30. Context is sent
   together, and results are applied only when subtitle IDs and counts match.
5. Read the results. Double-click a translation cell to make corrections.
6. Click [병합하기] (Merge) or press Ctrl+S to save a new SRT.
   To keep edits made in the table, complete the merge/save operation.

A stop request in the progress window may not immediately end an API request
already in progress. Check completed results before resuming from the required
range. Translating completed subtitles again may incur additional API charges.

### 5. Use a translation prepared in another tool

1. Open the original SRT.
2. Use [추출하기] (Extract) to save the source text as TXT and translate it.
3. Click [번역 TXT 열기] (Open translation TXT) to load the translated text.
4. Check alignment against the original subtitles, then use [병합하기] to save.

Keep one TXT line per original subtitle, in the same order. Combining or splitting
lines can misalign later subtitles. If the app warns about a count mismatch,
correct the file so the counts match before merging.

### 6. Models, languages, and glossary

Gemini: Gemini 4 Argon, Gemini 3.1 Pro Preview, Gemini 3.7 Flash
GPT: GPT-6.1 Sol, GPT-6 Sol, GPT-6 Luna, GPT-5.6 Sol, GPT-5.6 Terra, GPT-5.6 Luna

A listed model may still be unavailable because of account, region, billing, or
provider policy. Up to 10 target languages are shown for the selected model;
Korean, Russian, and English are always included. The extraction language code
controls the TXT filename. The AI target language controls the translation.

Use [모델 노출] (Model visibility) below the model list to select Recommended
(default), All, or Custom. Recommended shows three models per provider: all three
registered Gemini models, and GPT 6.1 Sol, 6 Sol, and 6 Luna. All shows every model
registered in the app. In Custom mode, click [모델 선택…] (Select models), choose
at least one model, and apply. The mode and custom list are saved for the next launch.
If the selected model becomes hidden, the first visible model from the same provider
is selected, or the first model in the list if that provider has no visible models.
You can also edit the visibility mode and custom list in F2 Settings > [모델] (Models).
Click [확인] (OK) or press Ctrl+S to save and update the main list; Cancel discards edits.

Hover over ? to the right of the translation language selector to see the selected model's supported reasoning
levels and their uses. The current applied level is described only in the ? help;
the model selection list does not show reasoning information.
Reasoning levels cannot be changed in the app.

Press F3 to open the glossary. Enter one source-term:target-term pair per line.
The glossary is sent as a translation instruction; verify its use in the result.
Click [프롬프트 미리보기] (Prompt preview) to inspect the translation instructions.

### 7. Review and editing

- Double-click a translation cell: apply with Enter or by clicking elsewhere;
  cancel the edit with Esc.
- Ctrl+F: search original and translated text. Use Find or Enter for the next hit.
- F4 or [검토 필요 찾기] (Find review items): move through warning items.
- The default length warning applies when an individual displayed translation
  line exceeds 45 characters. In the review settings, enable/disable this warning
  and choose a threshold from 10 to 200 characters.
- Review `<빈줄>` (empty line), replacement characters, and length warnings against
  the source text and correct them as needed.
- Original subtitle text over 200 characters is skipped by AI translation and
  marked [200자 초과 번역 불가] (Cannot translate: over 200 characters).
  Review it and enter the translation manually.
- Enable [작업 내용] (Activity log) to view progress and errors in the log window.
- AI output can be incorrect or incomplete. Review it before publication.

### 8. Keyboard shortcuts

```text
F2                 Settings
F3                 Glossary settings
F4                 Next review item
Ctrl+Enter         AI translation
Ctrl+S             Merge and save SRT
Ctrl+F             Search
Ctrl+Z / Ctrl+Y    Undo / Redo
Up/Down, PgUp/PgDn Navigate the subtitle table
```

### 9. Files, settings, and privacy

Extracted filenames may include a language code. Merged AI translations may
include the target language and a model suffix. You can change the filename in
the save dialog. Keep the original file and save your work under a new name.

Settings, glossary, logs, and related local data are stored in:
`%LOCALAPPDATA%\안김 소프트\SubBridgeAI`

The actual folder name uses Korean characters: 안김 소프트. Moving the EXE to
another folder preserves settings for the same Windows user. Copying only the
EXE to another PC does not transfer settings or keys. To remove local data,
close the app and delete this user-data folder. Back up settings or glossary
data you want to keep to a safe location under your control first.

Starting AI translation sends selected subtitles, instructions, target language,
glossary, and context to Google or OpenAI. Use only content you are authorized
to transmit. The app does not automatically send feedback or usage telemetry to
the developer. See the included PRIVACY.md and the provider's policies for details.

### 10. Manual updates

1. Check the official GitHub Releases page for a new version and its changes.
2. Save your work and close the app.
3. Download the new ZIP, verify its checksum, and extract it into a separate folder.
4. Launch the new EXE and confirm its version and your existing settings.

Automatic downloading and replacement are not provided. Settings remain in the
same Windows user's data folder. Before reverting to an older version, back up
current settings and check compatibility with that version.

### 11. Troubleshooting and feedback

Share feedback, questions, and ideas in [Discussions](https://github.com/qwerzxc1090/SubBridgeAI/discussions).
Read the pinned [community guide / Start here](https://github.com/qwerzxc1090/SubBridgeAI/discussions/1) first.

- [사용자 후기 / User feedback](https://github.com/qwerzxc1090/SubBridgeAI/discussions/categories/사용자-후기)
- [질문·답변 / Questions and answers](https://github.com/qwerzxc1090/SubBridgeAI/discussions/categories/질문-답변)
- [개선 요청 / Feature requests](https://github.com/qwerzxc1090/SubBridgeAI/discussions/categories/개선-요청)
- [공지·이용 안내 / Announcements](https://github.com/qwerzxc1090/SubBridgeAI/discussions/categories/공지-이용-안내)

Posting and commenting require a GitHub account. Use Issues below for reproducible bugs.

- Model unavailable/403: check the correct provider key, model access, and billing.
- 429/quota exceeded: check rate limits, usage, and balance in the provider console.
- Network error: check connectivity and resume after the completed range.
- Merge blocked: check empty translations and SRT/TXT count mismatches.
- Misaligned TXT: restore the original subtitle count and line order.
- Incorrect AI output: edit the translation cell and merge/save again.

Click [베타 피드백] (Beta feedback) or visit:
https://github.com/qwerzxc1090/SubBridgeAI/issues/new/choose

Include the app version, Windows version, steps to reproduce, and expected versus
actual results. Do not attach API keys, settings.json, private subtitles,
translations, or logs containing personal paths. Report security issues privately:
https://github.com/qwerzxc1090/SubBridgeAI/security/advisories/new

### 12. Terms of use

SubBridgeAI is Freeware provided by 안김 소프트 (Angim Soft). See the included
LICENSE and EULA.md for permitted uses and restrictions, and THIRD_PARTY_NOTICES.md
for component notices. You are responsible for API charges and reviewing results.

Copyright © 2026 안김 소프트. All rights reserved.

[discussion-feedback]: https://github.com/qwerzxc1090/SubBridgeAI/discussions/new?category=%EC%82%AC%EC%9A%A9%EC%9E%90-%ED%9B%84%EA%B8%B0&title=%5B%ED%9B%84%EA%B8%B0+%2F+Feedback%5D+&body=%23%23%23+%EC%95%B1+%EB%B2%84%EC%A0%84+%2F+App+version%0A%0A%23%23%23+%EC%82%AC%EC%9A%A9+%EA%B2%BD%ED%97%98+%2F+Your+experience%0A%EC%96%B4%EB%96%A4+%EC%9E%91%EC%97%85%EC%97%90+%EC%82%AC%EC%9A%A9%ED%96%88%EA%B3%A0%2C+%EB%AC%B4%EC%97%87%EC%9D%B4+%EC%A2%8B%EC%95%98%EA%B1%B0%EB%82%98+%EB%B6%88%ED%8E%B8%ED%96%88%EB%82%98%EC%9A%94%3F+%2F+What+worked+well+or+was+difficult%3F%0A%0A%23%23%23+%EA%B0%9C%EC%84%A0%EB%90%98%EC%97%88%EC%9C%BC%EB%A9%B4+%ED%95%98%EB%8A%94+%EC%A0%90+%2F+Suggestions%0A%0AAPI+%ED%82%A4%C2%B7%EA%B0%9C%EC%9D%B8+%EC%9E%90%EB%A7%89%C2%B7%EC%84%A4%EC%A0%95+%ED%8C%8C%EC%9D%BC%EC%9D%80+%EA%B3%B5%EA%B0%9C%ED%95%98%EC%A7%80+%EB%A7%88%EC%84%B8%EC%9A%94.+%2F+Do+not+share+secrets+or+private+files.%0A
[discussion-question]: https://github.com/qwerzxc1090/SubBridgeAI/discussions/new?category=%EC%A7%88%EB%AC%B8-%EB%8B%B5%EB%B3%80&title=%5B%EC%A7%88%EB%AC%B8+%2F+Question%5D+&body=%23%23%23+%EC%95%B1+%EB%B2%84%EC%A0%84+%2F+App+version%0A%0A%23%23%23+Windows+%EB%B2%84%EC%A0%84+%2F+Windows+version%0A%0A%23%23%23+%EC%84%A0%ED%83%9D%ED%95%9C+%EB%AA%A8%EB%8D%B8+%2F+Selected+model%0A%0A%23%23%23+%EC%A7%88%EB%AC%B8%EA%B3%BC+%EC%8B%9C%EB%8F%84%ED%95%9C+%EB%B0%A9%EB%B2%95+%2F+Question+and+steps+tried%0A%EA%B8%B0%EB%8C%80%ED%95%9C+%EA%B2%B0%EA%B3%BC%EC%99%80+%EC%8B%A4%EC%A0%9C+%EA%B2%B0%EA%B3%BC%EB%A5%BC+%EC%95%8C%EB%A0%A4+%EC%A3%BC%EC%84%B8%EC%9A%94.+%2F+Include+expected+and+actual+results.%0A%0AAPI+%ED%82%A4%C2%B7%EA%B0%9C%EC%9D%B8+%EC%9E%90%EB%A7%89%C2%B7%EC%84%A4%EC%A0%95+%ED%8C%8C%EC%9D%BC%EC%9D%80+%EA%B3%B5%EA%B0%9C%ED%95%98%EC%A7%80+%EB%A7%88%EC%84%B8%EC%9A%94.+%2F+Do+not+share+secrets+or+private+files.%0A
[discussion-idea]: https://github.com/qwerzxc1090/SubBridgeAI/discussions/new?category=%EA%B0%9C%EC%84%A0-%EC%9A%94%EC%B2%AD&title=%5B%EC%A0%9C%EC%95%88+%2F+Idea%5D+&body=%23%23%23+%ED%95%B4%EA%B2%B0%ED%95%98%EA%B3%A0+%EC%8B%B6%EC%9D%80+%EB%B6%88%ED%8E%B8+%2F+Problem+to+solve%0A%0A%23%23%23+%EC%9B%90%ED%95%98%EB%8A%94+%EB%8F%99%EC%9E%91+%2F+Proposed+behavior%0A%0A%23%23%23+%EC%82%AC%EC%9A%A9+%EC%A4%91%EC%9D%B8+%EC%95%B1+%EB%B2%84%EC%A0%84+%2F+Current+app+version%0A%0AAPI+%ED%82%A4%C2%B7%EA%B0%9C%EC%9D%B8+%EC%9E%90%EB%A7%89%C2%B7%EC%84%A4%EC%A0%95+%ED%8C%8C%EC%9D%BC%EC%9D%80+%EA%B3%B5%EA%B0%9C%ED%95%98%EC%A7%80+%EB%A7%88%EC%84%B8%EC%9A%94.+%2F+Do+not+share+secrets+or+private+files.%0A
