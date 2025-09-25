# LaTeX 수학 공부 노트 작성 가이드

## 📚 기본 사용법

### 1. 문서 컴파일
한글이 포함된 경우 (권장):
```bash
xelatex filename.tex
```
또는 latexmk 사용:
```bash
latexmk -xelatex filename.tex
```
영어만 있는 경우:
```bash
pdflatex filename.tex
```

### 2. 문서 구조
- `\section{제목}` - 새로운 장
- `\subsection{제목}` - 절
- `\subsubsection{제목}` - 소절

## 🔢 자주 쓰는 수식 명령어

### 기본 수식
| 설명 | LaTeX 코드 | 결과 |
|------|-----------|------|
| 인라인 수식 | `$x + y$` | 텍스트 중간에 x + y |
| 블록 수식 | `\[ x + y \]` | 별도 줄에 표시 |
| 분수 | `\frac{a}{b}` | a/b |
| 제곱 | `x^2` | x² |
| 아래첨자 | `a_n` | aₙ |
| 제곱근 | `\sqrt{x}` | √x |

### 미적분
| 설명 | LaTeX 코드 |
|------|-----------|
| 극한 | `\lim_{x \to 0}` |
| 미분 | `\frac{df}{dx}` |
| 편미분 | `\frac{\partial f}{\partial x}` |
| 적분 | `\int_a^b f(x) dx` |
| 무한대 | `\infty` |

### 그리스 문자
| 문자 | 코드 | 문자 | 코드 |
|------|-----|------|-----|
| α | `\alpha` | β | `\beta` |
| γ | `\gamma` | δ | `\delta` |
| θ | `\theta` | λ | `\lambda` |
| π | `\pi` | σ | `\sigma` |
| Σ | `\Sigma` | Δ | `\Delta` |

### 집합과 논리
| 설명 | LaTeX 코드 |
|------|-----------|
| 포함 | `\in` |
| 부분집합 | `\subset` |
| 합집합 | `\cup` |
| 교집합 | `\cap` |
| 모든 | `\forall` |
| 존재 | `\exists` |

### 관계 기호
| 설명 | LaTeX 코드 |
|------|-----------|
| 같지 않음 | `\neq` |
| 작거나 같음 | `\leq` |
| 크거나 같음 | `\geq` |
| 근사 | `\approx` |
| 합동 | `\equiv` |

## 📝 예제 코드

### 이차방정식의 해
```latex
\begin{equation}
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{equation}
```

### 행렬
```latex
\begin{pmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{pmatrix}
```

### 여러 줄 수식 정렬
```latex
\begin{align}
f(x) &= x^2 + 2x + 1 \\
     &= (x + 1)^2
\end{align}
```

### 경우 나누기
```latex
f(x) = \begin{cases}
    x^2 & \text{if } x > 0 \\
    0   & \text{if } x = 0 \\
    -x^2 & \text{if } x < 0
\end{cases}
```

## 💡 유용한 팁

### 수식 번호 제어
1. **전체 번호 제거**
   ```latex
   \begin{align*}  % * 추가하면 전체 번호 없음
   ...
   \end{align*}
   ```

2. **특정 줄만 번호 제거**
   ```latex
   \begin{align}
   x &= a + b \\
   y &= c + d \nonumber  % 이 줄만 번호 없음
   \end{align}
   ```

3. **수동 번호 지정**
   ```latex
   \begin{align*}
   E &= mc^2 \tag{아인슈타인} \\
   F &= ma \tag{1}  % 괄호 자동 추가
   P &= \frac{F}{A} \tag*{중요}  % 괄호 없음
   \end{align*}
   ```

### 수식 참조
4. **라벨과 참조**
   ```latex
   \begin{equation}
   E = mc^2 \label{eq:einstein}
   \end{equation}

   식 \eqref{eq:einstein}에서...  % (1) 형태로 참조
   \cref{eq:einstein}에서...     % "식 (1)"로 스마트 참조
   ```

5. **여러 참조**
   ```latex
   \cref{eq:1,eq:2,eq:3}         % "식 (1), (2)과 (3)"
   \cref{eq:1,eq:2,eq:3,eq:4}    % "식 (1)에서 (4)"
   ```

### 템플릿 활용
6. **templates.tex 사용**
   ```latex
   \documentclass{article}
   \input{templates.tex}  % 한글 설정 + cleveref 한국어화

   \begin{document}
   \Cref{eq:main}에서...  % "식 (1.1)"로 자동 한국어 출력
   \end{document}
   ```

### 기타 팁
7. **괄호 크기 자동 조절**
   ```latex
   \left( \frac{a}{b} \right)  % 분수에 맞춰 괄호 크기 조절
   ```

8. **수식 내 텍스트**
   ```latex
   x > 0 \text{ 일 때}  % 수식 안에 한글/영어 텍스트
   ```

9. **벡터 표현**
   ```latex
   \vec{v}      % 화살표 벡터
   \mathbf{v}   % 굵은 글씨 벡터
   ```

10. **합과 곱**
    ```latex
    \sum_{i=1}^{n} i      % 시그마 합
    \prod_{i=1}^{n} i     % 파이 곱
    ```

## 🎯 자주 하는 실수

1. **달러 기호 빠뜨리기**: 수식은 반드시 `$...$` 안에
2. **중괄호 사용**: 위/아래 첨자가 여러 문자일 때 `x^{10}` (중괄호 필수)
3. **띄어쓰기**: LaTeX는 수식 모드에서 띄어쓰기 무시 → `\,` `\;` `\quad` 사용
4. **특수문자**: `%`, `#`, `&` 등은 `\%`, `\#`, `\&`로 이스케이프

## 📖 문서 작성 워크플로우

### 프로젝트 구조
```
LaTexS/
├── templates.tex           # 공통 설정 파일
├── basic_template.tex       # 기본 템플릿
└── articles/
    └── 01_partial_sum_recurssion/
        └── partial_sum.tex  # 개별 문서
```

### 새 문서 만들기
1. **템플릿 활용**
   ```latex
   \documentclass[a4paper,12pt]{article}
   \input{../../templates.tex}  % 공통 설정 로드

   \title{문서 제목}
   \author{작성자}
   \date{\today}

   \begin{document}
   \maketitle
   \tableofcontents
   \newpage

   \section{새로운 주제}
   내용 작성...
   \end{document}
   ```

### iPad에서 작업하기
**Textastic + Tex Compiler**
- Textastic으로 .tex 파일 편집
- Tex Compiler 앱으로 컴파일하여 PDF 생성
- 또는 Overleaf 브라우저 사용

## 🔧 문제 해결

### 컴파일 에러
- **한글 깨짐**: `xelatex` 또는 `lualatex` 사용, `\usepackage{kotex}` 확인
- **수식 에러**: 달러 기호 `$...$` 짝이 맞는지 확인
- **PDF 생성 안됨**: 에러 메시지 확인, 보통 괄호나 환경(`\begin{...}` `\end{...}`) 닫기 누락
- **패키지 에러**: `templates.tex` 파일의 패키지 충돌 확인

### 참조 에러
- **undefined reference**: `\label{}`과 `\ref{}` 이름 일치 확인
- **cleveref 에러**: `templates.tex` 파일에 한국어 설정이 포함되어 있는지 확인
- **번호 표시 안됨**: 2번 컴파일 필요 (참조 업데이트)

## 🚀 시작하기

### 로컬에서 작업
1. `.tex` 파일 열기
2. 내용 수정/추가
3. 터미널에서 `xelatex filename.tex` 실행
4. 생성된 PDF 확인

### iPad에서 LaTeX 작업
1. **설치할 앱**
   - Textastic: 코드 편집기
   - Tex Compiler: LaTeX 컴파일러
   - Working Copy: Git 클라이언트 (선택사항)

2. **작업 방법**
   - 방법 1: Textastic에서 편집 → Tex Compiler로 컴파일
   - 방법 2: Overleaf 브라우저에서 직접 작업
   - 방법 3: GitHub에 저장 후 컴퓨터에서 컴파일

## 📱 Anki 카드 만들기 템플릿

오늘 배운 내용을 Anki로 복습하세요:

**질문**: `\tag{}`와 `\nonumber`의 차이점은?
**답안**: `\tag{}`는 수동 번호 지정, `\nonumber`는 해당 줄 번호만 제거

**질문**: iPad에서 LaTeX 작업하는 최적 조합은?
**답안**: Textastic (편집) + Tex Compiler (컴파일) 또는 Overleaf (온라인)