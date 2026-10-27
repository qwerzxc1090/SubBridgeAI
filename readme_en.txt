SubBridgeAI User Guide — English
Public beta v0.1.0-beta.5 | 2026-10-27 | 안김 소프트 (Angim Soft)
한국어: readme.txt

1. About SubBridgeAI

SubBridgeAI is a Windows app for comparing and editing SRT subtitles and their
translations, then saving a new SRT with the original timecodes. You can translate
inside the app with your own Gemini or OpenAI API key. Opening, editing,
extracting, and merging SRT/TXT files can also be used without AI.

The interface is currently in Korean. Korean button names are included below.

2. Download and launch

Official repository: https://github.com/qwerzxc1090/SubBridgeAI
Official downloads: https://github.com/qwerzxc1090/SubBridgeAI/releases

- Target environment: Windows 10/11 x64. Behavior may vary during the beta.
- No installer or separate Python installation is required.
- If you download a portable ZIP, extract all files before launching the EXE.
- The package contains the EXE, readme.txt, readme_en.txt, and the license,
  privacy, and third-party component notices.
- A checksum file ending in .sha256 is provided for the ZIP and EXE. In
  PowerShell, calculate the hash and compare it with the checksum file:

  Get-FileHash .\downloaded-file.zip -Algorithm SHA256

- This public beta is not code signed. Windows may show an unknown publisher or
  SmartScreen warning. Verify the official download source and SHA-256 checksum.
  A checksum verifies file equality; it does not authenticate the publisher.
  Do not disable security software or run files of unknown origin.

3. First launch and API keys

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

4. Create a translated SRT with AI

1) Click [파일 열기] (Open file) to load the original SRT.
   The table shows index/timecode, original text, and translated text.
2) Select [AI 모델] (AI model) and the target translation language.
3) Select the subtitles to translate:
   - Range: turn off [모두 번역] (Translate all) and enter a range such as 1-10
     or a list such as 1,3,5. Up to 50 subtitles can be selected in this mode.
   - All/remaining: turn on [모두 번역] and enter a starting subtitle number.
     The app processes that subtitle through the end of the file.
4) Click [AI 번역] (AI translation) or press Ctrl+Enter.
   The request batch size is 10–100 subtitles; the default is 30. Context is sent
   together, and results are applied only when subtitle IDs and counts match.
5) Read the results. Double-click a translation cell to make corrections.
6) Click [병합하기] (Merge) or press Ctrl+S to save a new SRT.
   To keep edits made in the table, complete the merge/save operation.

A stop request in the progress window may not immediately end an API request
already in progress. Check completed results before resuming from the required
range. Translating completed subtitles again may incur additional API charges.

5. Use a translation prepared in another tool

1) Open the original SRT.
2) Use [추출하기] (Extract) to save the source text as TXT and translate it.
3) Click [번역 TXT 열기] (Open translation TXT) to load the translated text.
4) Check alignment against the original subtitles, then use [병합하기] to save.

Keep one TXT line per original subtitle, in the same order. Combining or splitting
lines can misalign later subtitles. If the app warns about a count mismatch,
correct the file so the counts match before merging.

6. Models, languages, and glossary

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

7. Review and editing

- Double-click a translation cell: apply with Enter or by clicking elsewhere;
  cancel the edit with Esc.
- Ctrl+F: search original and translated text. Use Find or Enter for the next hit.
- F4 or [검토 필요 찾기] (Find review items): move through warning items.
- The default length warning applies when an individual displayed translation
  line exceeds 45 characters. In the review settings, enable/disable this warning
  and choose a threshold from 10 to 200 characters.
- Review <빈줄> (empty line), replacement characters, and length warnings against
  the source text and correct them as needed.
- Original subtitle text over 200 characters is skipped by AI translation and
  marked [200자 초과 번역 불가] (Cannot translate: over 200 characters).
  Review it and enter the translation manually.
- Enable [작업 내용] (Activity log) to view progress and errors in the log window.
- AI output can be incorrect or incomplete. Review it before publication.

8. Keyboard shortcuts

F2                 Settings
F3                 Glossary settings
F4                 Next review item
Ctrl+Enter         AI translation
Ctrl+S             Merge and save SRT
Ctrl+F             Search
Ctrl+Z / Ctrl+Y    Undo / Redo
Up/Down, PgUp/PgDn Navigate the subtitle table

9. Files, settings, and privacy

Extracted filenames may include a language code. Merged AI translations may
include the target language and a model suffix. You can change the filename in
the save dialog. Keep the original file and save your work under a new name.

Settings, glossary, logs, and related local data are stored in:
%LOCALAPPDATA%\안김 소프트\SubBridgeAI

The actual folder name uses Korean characters: 안김 소프트. Moving the EXE to
another folder preserves settings for the same Windows user. Copying only the
EXE to another PC does not transfer settings or keys. To remove local data,
close the app and delete this user-data folder. Back up settings or glossary
data you want to keep to a safe location under your control first.

Starting AI translation sends selected subtitles, instructions, target language,
glossary, and context to Google or OpenAI. Use only content you are authorized
to transmit. The app does not automatically send feedback or usage telemetry to
the developer. See the included PRIVACY.md and the provider's policies for details.

10. Manual updates

1) Check the official GitHub Releases page for a new version and its changes.
2) Save your work and close the app.
3) Download the new ZIP, verify its checksum, and extract it into a separate folder.
4) Launch the new EXE and confirm its version and your existing settings.

Automatic downloading and replacement are not provided. Settings remain in the
same Windows user's data folder. Before reverting to an older version, back up
current settings and check compatibility with that version.

11. Troubleshooting and feedback

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

12. Terms of use

SubBridgeAI is Freeware provided by 안김 소프트 (Angim Soft). See the included
LICENSE and EULA.md for permitted uses and restrictions, and THIRD_PARTY_NOTICES.md
for component notices. You are responsible for API charges and reviewing results.

Copyright © 2026 안김 소프트. All rights reserved.
