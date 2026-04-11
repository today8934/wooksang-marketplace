# wooksang-marketplace

류욱상(`@today8934`)의 Claude Code 플러그인 마켓플레이스입니다. 이 repo는 **마켓플레이스 인덱스 전용**이며, 실제 플러그인 코드는 각각의 독립 repo에 있습니다.

## 🚀 설치 방법

Claude Code 세션에서:

```
/plugin marketplace add today8934/wooksang-marketplace
```

등록 후 `/plugin` 명령으로 마켓플레이스 UI를 열면 `wooksang-marketplace`가 목록에 뜨고, 그 안의 플러그인들을 설치할 수 있습니다.

## 📦 포함된 플러그인

| 이름 | 설명 | Repo |
|---|---|---|
| `overnight-market-report-plugin` | 간밤 미국 증시·국제정세를 한국장 개장 전 브리핑용 한국어 마크다운 리포트로 생성 (전문가용 + 입문자용 두 파일 자동 생성) | [`today8934/overnight-market-report-plugin`](https://github.com/today8934/overnight-market-report-plugin) |
| `arsenal-brief-plugin` | 아스날 FC 최신 뉴스·경기·부상·대회·이적 루머를 한국어로 요약 브리핑 (채팅 출력 전용) | [`today8934/arsenal-brief-plugin`](https://github.com/today8934/arsenal-brief-plugin) |

각 플러그인의 **API 키 설정·사용법·트러블슈팅**은 해당 plugin repo의 README를 참고하세요.

## 🧭 구조

```
wooksang-marketplace/
└── .claude-plugin/
    └── marketplace.json   # 인덱스 매니페스트 (외부 플러그인 repo들을 source로 참조)
```

`marketplace.json`의 각 `plugins[].source`는 `{"source": "github", "repo": "<owner>/<repo>"}` 객체로 다른 repo의 플러그인을 가리킵니다. 이 방식 덕분에 마켓플레이스는 인덱스 역할만 하고, 각 플러그인은 자기 repo에서 독립적으로 issue·PR·릴리스 관리가 가능합니다.

## ➕ 새 플러그인 추가

1. 새 플러그인을 별도 repo에 `.claude-plugin/plugin.json` 구조로 작성
2. 이 repo의 `.claude-plugin/marketplace.json`의 `plugins` 배열에 항목 추가:
   ```json
   {
     "name": "new-plugin-name",
     "source": { "source": "github", "repo": "today8934/new-plugin-repo" },
     "description": "...",
     "version": "0.1.0"
   }
   ```
3. 커밋 + push

## 📝 라이선스

MIT License (`LICENSE` 파일 참고)
