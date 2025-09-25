# LaTeX 수학 공부 노트 작성 가이드

## 📚 기본 사용법

### 1. 문서 컴파일
```bash
pdflatex math_notes.tex
```
또는 한글이 포함된 경우:
```bash
xelatex math_notes.tex
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

1. **괄호 크기 자동 조절**
   ```latex
   \left( \frac{a}{b} \right)  % 분수에 맞춰 괄호 크기 조절
   ```

2. **수식 내 텍스트**
   ```latex
   x > 0 \text{ 일 때}  % 수식 안에 한글/영어 텍스트
   ```

3. **수식 번호 제거**
   ```latex
   \begin{align*}  % * 추가하면 번호 없음
   ...
   \end{align*}
   ```

4. **벡터 표현**
   ```latex
   \vec{v}      % 화살표 벡터
   \mathbf{v}   % 굵은 글씨 벡터
   ```

5. **합과 곱**
   ```latex
   \sum_{i=1}^{n} i      % 시그마 합
   \prod_{i=1}^{n} i     % 파이 곱
   ```

## 🎯 자주 하는 실수

1. **달러 기호 빠뜨리기**: 수식은 반드시 `$...$` 안에
2. **중괄호 사용**: 위/아래 첨자가 여러 문자일 때 `x^{10}` (중괄호 필수)
3. **띄어쓰기**: LaTeX는 수식 모드에서 띄어쓰기 무시 → `\,` `\;` `\quad` 사용
4. **특수문자**: `%`, `#`, `&` 등은 `\%`, `\#`, `\&`로 이스케이프

## 📖 문서에 내용 추가하기

1. `math_notes.tex` 파일을 열어서
2. 원하는 섹션 아래에 내용 추가
3. 저장 후 컴파일

예시:
```latex
\section{새로운 주제}
여기에 내용 작성...

\subsection{세부 내용}
수식: $f(x) = x^2$
```

## 🔧 문제 해결

- **한글 깨짐**: `xelatex` 사용 또는 `\usepackage{kotex}` 확인
- **수식 에러**: 달러 기호 짝이 맞는지 확인
- **PDF 생성 안됨**: 에러 메시지 확인, 보통 괄호나 환경 닫기 누락

## 🚀 시작하기

1. `math_notes.tex` 파일 열기
2. 내용 수정/추가
3. 터미널에서 `pdflatex math_notes.tex` 실행
4. 생성된 `math_notes.pdf` 확인