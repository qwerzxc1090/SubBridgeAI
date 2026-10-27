# Third-Party Notices

SubBridgeAI 자체 코드는 [Freeware License](LICENSE)를 따릅니다. 아래 제3자 구성요소는 각 프로젝트의 별도 라이선스를 따르며, 이 문서는 해당 권리를 제한하지 않습니다.

| 구성요소 | 용도 | 라이선스/공식 정보 |
|---|---|---|
| Python | 애플리케이션 런타임 | [PSF License](https://docs.python.org/3/license.html) |
| Tcl/Tk / tkinter | Windows UI | [Tcl/Tk License](https://www.tcl-lang.org/software/tcltk/license.html) |
| PyInstaller | 단일 EXE 패키징 | [PyInstaller licensing](https://pyinstaller.org/en/stable/license.html) |
| Pillow | 아이콘 및 이미지 처리 | [Pillow license](https://github.com/python-pillow/Pillow/blob/main/LICENSE) |
| Google Gen AI Python SDK | Gemini API 연결 | [Apache License 2.0](https://github.com/googleapis/python-genai/blob/main/LICENSE) |
| OpenAI Python SDK | OpenAI API 연결 | [Apache License 2.0](https://github.com/openai/openai-python/blob/main/LICENSE) |

직접 빌드 의존성은 `requirements-build.txt`에 검증 버전으로 고정되어 있습니다. 배포 직전 간접 의존성을 포함한 최종 SBOM 또는 동등한 목록을 생성하고 라이선스를 다시 확인해야 합니다.
