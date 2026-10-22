# 매일성경 선교적 묵상 도우미

성서유니온 매일성경 읽기표나 지정한 성경 본문을 따라 선교적으로 묵상하는 Codex 스킬입니다. 본문의 문맥을 살피고 하나님의 선교, 오늘의 실천, 짧은 기도로 이어갑니다.

A Korean-language missional Bible meditation skill for Codex, with daily reading-plan lookup and prayer.

## 묵상 방식

성경을 삼위 하나님의 사랑과 통치, 부르심과 보내심의 이야기 안에서 읽습니다. 성경의 권위와 하나님의 주권, 은혜를 중시하는 개혁주의 신학을 따릅니다.

본문이 당시 사람들에게 어떤 의미였는지 살핀 뒤, 성경 전체의 이야기와 예수 그리스도의 사역에 연결합니다. 모든 구약 인물과 사물을 예수의 직접적인 상징으로 바꾸지 않으며, 본문에서 근거를 찾을 수 있는 실천을 제안합니다.

날짜별 요청에는 공식 읽기표에서 확인한 날짜와 구절 범위, 본문 링크를 제공합니다. 성경 구절을 직접 지정하면 해당 본문으로 묵상합니다. 기본 출력은 연결된 문단으로 쓴 묵상과 짧은 기도문입니다.

## 설치

Codex에서 다음과 같이 요청하세요.

```text
$skill-installer https://github.com/imtseoul/missional-bible-meditation/tree/main/skills/missional-bible-meditation 를 설치해 줘.
```

직접 설치하려면 저장소를 복제한 뒤 스킬 폴더를 사용자 스킬 경로에 복사합니다. Git이 필요하며, 대상 폴더가 이미 있으면 중단합니다.

```sh
git clone https://github.com/imtseoul/missional-bible-meditation.git
cd missional-bible-meditation
(
  set -eu
  skill_target="$HOME/.agents/skills/missional-bible-meditation"
  if [ -e "$skill_target" ] || [ -L "$skill_target" ]; then
    printf '%s\n' '이미 설치된 스킬이 있습니다. 기존 폴더를 확인하세요.' >&2
    exit 1
  fi
  mkdir -p "$HOME/.agents/skills"
  cp -R skills/missional-bible-meditation "$skill_target"
)
```

설치 후 `$missional-bible-meditation`으로 호출합니다. 목록에 나타나지 않으면 Codex를 다시 시작하세요. 설치 경로와 호출 방식은 [OpenAI 스킬 문서](https://learn.chatgpt.com/docs/build-skills)에서 확인할 수 있습니다.

## 사용

```text
$missional-bible-meditation 으로 오늘 매일성경 본문을 확인하고 선교적 묵상과 기도문을 작성해 줘.
```

```text
$missional-bible-meditation 으로 2026-10-22 매일성경 본문을 표준 분량으로 묵상해 줘.
```

```text
$missional-bible-meditation 으로 누가복음 10:25-37을 간략하게 묵상하고 기도문을 써 줘.
```

```text
$missional-bible-meditation 으로 내가 제공한 번역의 요한복음 20:19-23을 심층 분량으로 묵상해 줘. 지역교회의 이웃 돌봄에 적용해 줘.
```

| 분량 | 묵상 권장 길이 |
| --- | --- |
| 간략 | 약 500-900자 |
| 표준, 기본값 | 약 1,200-2,000자 |
| 심층 | 약 2,500-4,000자 |

공백을 포함한 대략적인 한국어 분량이며 성경 인용과 기도문은 별도입니다. 본문 길이와 요청에 따라 조정할 수 있습니다.

[2026-10-22 야고보서 4:1-12 묵상](examples/2026-10-22-james-4-1-12.md)에서 출력 예시를 읽을 수 있습니다.

## 읽기표와 본문 자료

매일성경 읽기표는 [성서유니온 오늘의 묵상](https://sum.su.or.kr:8888/bible/today)에서 확인합니다. 날짜별 조회에는 웹에 접근할 수 있는 실행 환경이 필요합니다. 접근할 수 없으면 구절 범위나 읽기표를 제공해 주세요.

이 스킬에는 성경 번역본이나 성서유니온 해설 전문이 포함되어 있지 않습니다. 성경 인용에는 번역명을 명시하며, 전문을 제공하려면 사용자가 본문을 제공하거나 재배포가 허용된 자료를 사용할 수 있어야 합니다.

읽기표 제공: 한국성서유니온선교회. 선교적 묵상 지침: 사단법인 미셔널신학연구소의 매일성경 선교적 묵상 도우미.

## 파일

- [SKILL.md](skills/missional-bible-meditation/SKILL.md): 본문 읽기, 선교적 묵상, 기도문 지침
- [읽기표 확인 안내](skills/missional-bible-meditation/references/reading-plan.md): 날짜와 구절 범위를 확인하는 경로
- [agents/openai.yaml](skills/missional-bible-meditation/agents/openai.yaml): Codex 표시 이름과 기본 호출 문구
- [묵상 예시](examples/2026-10-22-james-4-1-12.md): 야고보서 4:1-12

절별 분석과 학술 주해가 필요하면 [충성된 성경 주해봇](https://github.com/imtseoul/faithful-bible-exegesis)을 사용할 수 있습니다.

## 라이선스와 기관

스킬 지침과 저장소 문서는 [MIT License](LICENSE)로 이용할 수 있습니다. 외부 링크의 성경 번역과 해설에는 해당 자료의 이용 조건이 적용됩니다.

[미셔널신학연구소](https://www.imt.or.kr/) · [연구소 후원](https://www.imt.or.kr/give)
