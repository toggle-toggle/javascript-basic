# DOM & BOM

## 목차

- [DOM과 BOM의 차이점에 대해 설명해주세요.](#1)
- [렌더링(엔진)이란 무엇이고, 브라우저 렌더링은 어떻게 동작하는가?](#2)
- [리플로우와 리페인트의 차이는 무엇인가?](#3)
- [window와 document의 차이점은 무엇인가요?](#4)
- [NodeList와 HTMLCollection에 대해 아는대로 설명해보세요.](#5)
- [DOM을 조작하는 메서드를 2가지 이상 말하고, 각각의 특징을 비교해서 설명해주세요.](#6)

---

## <a name="1"></a>DOM과 BOM의 차이점에 대해서 설명해주세요.

- DOM과 BOM은 모두 브라우저의 요소들과 자바스크립트 엔진, 그리고 모든 변수를 담고 있는 전역 객체인 window에 속한 객체 모델들입니다.
  DOM은 Document Object Model의 약자로 웹 페이지에 대한 인터페이스를 의미한다면
  BOM은 Browser Object Model의 약자로 문서 객체 모델(DOM)과는 달리 W3C의 표준 객체 모델은 아니지만, Document 문서 이외의 모든 것을 제어하기 위해 브라우저가 제공하는 추가 객체를 말합니다.
  DOM은 자바스크립트와 같은 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법(DOM API)을 제공하여 그들이 문서 구조, 스타일, 내용 등을 변경할 수 있게 돕고,
  BOM은 자바스크립트가 웹 브라우저의 버튼, URL 주소 입력 창, 타이틀 바 등 웹브라우저 윈도우 및 웹페이지의 일부분을 제어할수 있게하는 역할을 합니다.
  요약하자면 window 객체에서 브라우저 창에 표시되는 내용에 해당하는 문서(document)를 담당하는 것은 DOM, 브라우저를 담당하는 것은 BOM이라고 말할 수 있습니다.

- DOM이란 어떠한 document(열려진 페이지에 대한 정보)에 대한 모든 내용을 담고있는 객체입니다.

  좀 더 자세히 말하자면, 텍스트 파일 형태의 웹 문서를 브라우저에 렌더링하려면, 웹 문서를 브라우저가 이해할 수 있는 구조로 변경하여 메모리에 올려야하는데요. 이를 위해 브라우저 렌더링 엔진은 웹 문서를 load하고 parsing하여 알맞은 형태의 객체로 변경하는데, 이러한 객체가 DOM입니다.

  BOM이란 앞서 말한 document 이외에 모든 것들을 제어하기 위해 `브라우저가 제공하는 객체`입니다. 즉, BOM은 브라우저에 대한 모든 내용으로 뒤로가기, 북마크, 즐겨찾기, 히스토리, URL 등을 담고 있는 객체입니다.

- DOM과 BOM 모두 웹페이지를 조작하는 기능을 제공하는 객체 모델이다.

  DOM은 모든 html 요소, 어트리뷰트, 텍스트 요소를 트리 형태로 제공하는 객체 모델이다.

  BOM은 자바스크립트로 브라우저와 소통할 수 있는 방법을 제공한다. 브라우저에 대한 정보 뿐만 아니라 url 정보, 히스토리, screen 정보 등과 조작할 수 있는 메서드들을 제공한다.

- 사용자가 만든 문서(Html)를 조작 가능하게 하는 객체 모델을 `DOM`, 브라우저 환경을 제어하는 객체 모델을 `BOM`이라고 합니다.

  `DOM`은 `Document Object Model`의 약자로, JavaScript 를 사용하여 문서에 대한 조작이 가능하게 하는 프로그래밍 인터페이스입니다.
  브라우저는 브라우저가 이해할 수 있도록, 우리가 작성한 HTML 파일 한줄 한줄을 읽으면서 DOM Tree 로 변환합니다.

  `BOM`는 `Browser Object Model`의 약자로 웹 브라우저 환경의 다양한 기능을 객체처럼 다루는 모델입니다. 웹 브라우저의 버튼, URL 주소 입력 창, 타이틀 바 등 웹브라우저 윈도우 및 웹페이지의 일부분을 제어할 수 있게 해주며, `window` 객체를 통해서 접근이 가능합니다.

- DOM Document Object Model의 약자로 문서에 대한 모든 내용을 담고 있는 객체 모델입니다. DOM은 텍스트 파일로 만들어진 문서를 브라우저가 이해할 수 있는 구조로 구성한 것으로, HTML 요소 간의 부자 관계를 반영하여 모든 노드들이 트리 구조로 구성되어 있는 것이 특징입니다. 노드의 종류에 대해서 좀 더 자세히 살펴보면, 노드는 DOM 트리의 최상단에 있으며, document 객체를 가리키는 document 노드, HTML 요소를 가리키는 객체인 element 노드, HTML 요소의 속성을 가리키는 객체인 attribute 노드, HTML 요소의 텍스트를 가리키는 객체인 text 노드가 있습니다. BOM은 Browser Object Model의 약자로 웹 브라우저 환경의 다양한 기능을 객체처럼 다루는 모델입니다. 대부분의 브라우저에서 구현되어 있지만, 정의된 표준이 없어 브라우저 제작사마다 세부 사항이 다릅니다. 즉, DOM이 BOM에 포함되는 형태를 띄고 있습니다.

- "DOM"
  문서에 대한 모든 내용을 담고 있는 객체입니다.
  객체화된 모델을 이용해 동적 HTML을 제어할 수 있습니다.
  elements에 대한 접근을 통해 HTML과 CSS의 내용을 변경 가능합니다.

  "BOM" Browser Object Model
  브라우저에 대한 모든 내용을 담고 있는 객체입니다.
  뒤로가기 북마크 즐겨찾기 히스토리 URL 정보 등을 포함합니다.
  브라우저가 가지고 있는 정보를 따로 객체화 시켜서 관리합니다.

## <a name="2"></a>렌더링(엔진)이란 무엇이고, 브라우저 렌더링은 어떻게 동작하는가?

- 렌더링이란, 요청한 콘텐츠를 화면에 표시하는 것입니다. 예를 들어, HTML을 요청하면 HTML과 CSS를 파싱하여 화면에 표시합니다. 각 브라우저는 이 렌더링을 수행하는 렌더링 엔진을 가지는데 사파리는 webkit 엔진을, 파이어폭스는 gecko 엔진을, 크롬은 블링크 엔진을 사용합니다.
  브라우저 렌더링 동작 과정에 대해 말씀드리면, 브라우저는 읽어들인 문서를 파싱하여 웹 페이지에 어떤 내용을 최종적으로 렌더링할 지 결정합니다. 브라우저는 그 결정된 내용으로 렌더링을 수행하는데 그 과정에서 HTML 요소들의 구조화된 표현인 DOM과 그 요소들과 연관된 스타일 정보의 구조화된 표현인 CSSOM 모델 2가지로 '렌더트리'를 생성합니다. 브라우저 뷰포트에는 이 DOM과 CSSOM의 조합인 '렌더 트리'가 보여지는 것입니다.
  위와 같은 일련의 과정들은 동기적으로 진행되지는 않습니다. 브라우저는 HTML을 파싱할 때까지 기다리지 않고 렌더 트리 배치와 그리기 과정을 시작하는데 자세한 동작 과정은 각 렌더링 엔진에 따라 약간씩 다르다고 합니다.

- HTML, CSS, JS 등 개발자가 작성한 코드 파일을 브라우저에 출력하는 과정을 `렌더링`이라하고, 이러한 역할을 하는 엔진을 `렌더링 엔진`이라 합니다.

  렌더링 엔진의 동작 과정은 다음과 같습니다.

  가장 먼저, 요청에 대한 응답으로 받은 HTML문서를 파싱하여 DOM 객체를 생성해 나갑니다. 그렇게 HTML 문서를 파싱하다가, link 태그를 만나면 CSS파일과 style 요소를 파싱하여 CSSOM을 생성하는데요. 렌더링 엔진은 이렇게 생성된 DOM 객체와 CSSOM 객체를 합쳐서 render tree를 생성합니다. 그리고나서 render tree를 통해 각 노드를 화면에 표시하도록 배치합니다. 배치가 완성되면, UI 백엔드에서 render tree의 각 노드를 가로지르며 화면에 그리게 되고, 우리는 그렇게 브라우저에서 우리가 원하는 화면을 볼 수 있게됩니다. 추가로 <script> 태그를 만나면 렌더링 엔진은 자바스크립트 엔진을 실행하면서 자바스크립트 코드를 파싱하여 동적인 화면을 유저에게 보여줍니다.

- 렌더링은 응답받은 문서를 브라우저에 보여주는 작업을 의미한다.

  렌더링 과정은 다음과 같다.

  1. 브라우저에 웹페이지를 요청하고 성공적으로 응답을 받으면 필요한 문서와 리소스들이 다운로드된다.
  2. 문서가 다운로드 되면 브라우저는 html파일을 파싱한다. 이때, link와 script태그를 만나면 각각 css와 js파일을 로드한다.
  3. html과 css 파일을 파싱하면서 DOM과 CSSOM이 구성된다.
  4. DOM과 CSSOM을 병합하여 렌더트리를 구성한다. 이때, 실제 화면에 영역을 차지하게 될 요소들만 포함한다.
  5. 요소들이 배치될 위치와 실제 크기가 계산된다. 이 과정을 레이아웃 혹은 플로우(리플로우) 과정이라고 한다.
  6. 각 요소를 픽셀 단위로 맵핑한다. 이때, 각 레이어 별로 처리되며 이 과정을 페인트(리페인트) 과정이라고 한다.
  7. 픽셀단위로 준비된 각 레이어를 병합해 실제 뷰포트에 보여준다. 이 과정을 컴포지팅이라고한다.

  참고 : https://developers.google.com/web/updates/2018/09/inside-browser-part3?hl=ko

- 큰 의미의 렌더링은 Html, CSS, JavaScript 등의 문서를 브라우저에서 볼 수 있는 형태로 출력하는 것을 의미합니다.
  각각의 브라우저는 렌더링을 수행하기 위해 렌더링 엔진을 사용하는데, 각 브라우저 별로 엔진이 다르기 때문에 지원하는 범위나 성능이 조금씩 상이합니다. 대표적으로 파이어폭스는 게코를, 사파리는 웹킷을 사용합니다.

  렌더링의 과정은 다음과 같습니다.

  1. 브라우저에게 웹페이지를 요청하고 응답하는 `request`, `response` 단계
  2. 성공적으로 요청과 응답이 이루어졌다면 `Html`을 `DOM` 요소로 변환하고, `CSS` 파일을 `CSSOM`으로 변환하는 `scripting` 단계
  3. `DOM`과 `CSSOM`에서 실제 화면에 그려질 부분에 대한 `Render Tree`를 형성하는 `rendering` 단계
  4. 각각의 요소들이 어떤 위치에 어떻게 배치될 것인지를 계산하는 `layout` 단계 (또는`reflow` 단계)
  5. 각 레이어별로 보여질 이미지를 비트맵 단위로 준비하는 `painting` 단계
  6. 준비한 레이어를 쌓아서 실제 사용자에게 보여주는 `composition` 단계

- 렌더링이란 브라우저에 나타나는 것을 말합니다. 브라우저가 렌더링하는 과정은 다음과 같습니다. 먼저 브라우저는 HTML, CSS, 자바스크립, 이미지, 폰트 파일 등 렌더링에 필요한 리소스를 요청하고 서버로부터 응답을 받습니다. 이후, 브라우저 렌더링 엔진은 서버로부터 응답된 HTML과 CSS를 파싱하여 DOM과 CSSOM(Javascript에서 CSS를 조작할 수 있는 API 집합)을 생성하고 이들을 결합하여 렌더 트리(이건 또 뭐냐)를 생성합니다. 브라우저의 자바스크립트 엔진은 서버로부터 응답된 자바스크립트를 파싱하여 AST(Abstract Syntax Tree)를 생성하고 바이트코드로 변환하여 실행합니다. 이때 자바스크립트는 DOM API를 통해 DOM이나 CSSOM을 변경할 수 있습니다. 변경된 DOM과 CSSOM은 다시 렌더 트리로 결합됩니다. 마지막으로 렌더 트리는 기반으로 HTML 요소의 레이아웃(위치와 크기)을 계산하고 브라우저 화면에 HTML 요소를 페인팅합니다.

- 렌더링이란 response받은 문서를 브라우저에 보여주는 것을 의미합니다. 렌더링 과정은 아래와 같습니다.
  [ DOM Tree 구축을 위한 HTML 파싱 → 렌더 트리 구축 → 렌더 트리 배치 → 렌더트리 그리기 ]
  렌더링 엔진은 HTML 문서를 파싱하고 "콘텐츠 트리" 내부에서 태그를 DOM 노드로 변환합니다. 그 다음 외부 CSS 파일과 함께 포함된 스타일 요소도 파싱한다. 스타일 정보와 HTML 표시 규칙은 "렌더 트리"라고 부르는 또 다른 트리를 생성합니다. 렌더 트리는 색상 또는 면적과 같은 시각적 속성이 있는 사각형을 포함하고 있는데 정해진 순서대로 화면에 표시됩니다. 렌더 트리의 생성이 끝나면 배치가 시작되는데 이것은 각 노드가 화면의 정확한 위치에 표시되는 것을 의미합니다.

## <a name="3"></a>리플로우와 리페인트의 차이는 무엇인가?

- 웹페이지를 처음 표시하면서 브라우저 렌더링이 일어난 후에도 어떤 액션이나 이벤트에 의해 렌더 트리에 변화가 일어나는데요. 이때 발생하는 것이 Reflow(Layout)와 Repaint입니다.
  Reflow란, HTMl 요소의 크기나 위치가 수정될 경우 그에 영향을 받는 렌더 트리의 각 요소들의 크기와 위치를 다시 계산하게 되는 과정을 말합니다. Reflow는 대표적으로 DOM 노드의 추가 및 삭제, DOM 노드의 위치 이동 및 애니메이션, 스크롤, display none 처리, 폰트 변경 등에 의해 일어납니다.
  Repaint란, Reflow가 수행되어 변화된 렌더트리를 화면에 다시 그려주는 과정입니다. 하지만 Reflow가 일어날 때에만 Repaint가 일어나는 것은 아니며, 레이아웃에 변경이 없는 background-color, visibility등의 스타일 속성이 변경된 경우에는 Repaint만 단독으로 수행됩니다.
  리플로우와 리페인트는 부하가 높기 때문에, 사용자 경험(UX)을 안좋게 하고 UI의 반응이 느려지는 원인이 되는데요. 앞서 말했듯이 Reflow가 일어나면 Repaint는 동반 수행되기 때문에 조금이라도 부하를 줄이기 위해서는 Repaint만 발생하는 스타일 속성을 사용하는 편이 좋으며,
  Reflow가 일어나는 경우에도, 트리의 아래쪽 노드를 건드린다면 위의 노드들은 재계산되지 않을 수 있지만 위쪽에서 높이 변화 등이 일어나면 아래 노드들까지 전체적으로 영향을 미칠 가능성이 높아 그만큼 Reflow 범위가 커진다는 것도 항상 염두에 두어야 합니다.

- 질문이 조금 수정되면 좋겠다고 생각을 하는데요. 왜냐하면 리렌더링을 하는 과정 중 하나가 리플로우 이기 때문입니다. 변경된 코드로 DOM 트리 변경됨에 따라, 브라우저는 리렌더링을 하게 됩니다. 그러한 과정에서, 한 노드 즉, 한 엘리먼트의 크기나 위치 등 레이아웃과 관련된 부분이 변경되었다면, 이를 전부 계산하여 변경된 부분이 render tree에 반영되는데, 이를 리플로우라고 합니다.

- 리플로우는 뷰포트 내 실제로 요소가 배치될 위치와 크기를 계산하는 과정이다.

  리페인트는 리플로우를 마친 후 각 요소를 픽셀단위로 맵핑하는 과정이다.

- `리플로우`는 형성된 `Render Tree`를 기반으로 기기의 뷰포트 내에서 어떤 요소가 어떠한 위치에 배치될 것인지를 계산하는 과정을 의미합니다. CSS 스타일이나 `DOM` 요소를 추가, 삭제, 수정을 할 때 다시 화면에 그려주어야 하는 요소들을 계산해야하기 때문에 리플로우가 발생할 수 있습니다.

  `리페인트`는 레이아웃 단계를 마친 요소들을 레이어 별로 컴퓨터가 이해할 수 있는 비트맵으로 잘라서 준비하는 단계를 의미합니다. CSS 스타일을 변경함에 따라 레이아웃이 달라지면 리페인트가 발생할 수 있습니다.

- 자바스크립트 코드에서 DOM이나 CSSOM을 변경하는 DOM API가 사용된 경우 DOM이나 CSSOM이 변경되는데, 변경된 DOM과 CSSOM은 다시 렌더 트리로 결합되고 변경된 렌더 트리를 기반으로 레이아웃과 페인트 과정을 거쳐 브라우저의 화면에 다시 렌더링합니다. 여기서 리플로우는 다시 레이아웃을 계산하는 과정을 말하며, 노드의 추가/삭제, 요소의 크기/위치 변경, 윈도우 리사이징 등 레이아웃에 영향을 주는 변경이 발생한 경우에만 실행됩니다. 리페인트란 재결합된 렌더 트리를 기반으로 다시 그리는 것을 말합니다. 여기서 리플로우와 리페인트가 반드시 순차적으로 동시에 실행되는 것은 아니라는 것입니다. 레이아웃에 영향이 없는 변경은 리플로우 없이 리페인트만 실행됩니다.

- 이 두가지는 모두 우리가 만든 웹 문서를 브라우저에 렌더링할 때 발생합니다.

  Reflow
  모든 엘리먼트의 위치와 길이 등을 다시 계산하는 과정에서 발생합니다. 그리고 DOM의 일부 혹은 전체 렌더링 시, CSS 스타일의 추가, 제거나 변경, 혹은 Animation, Transition이 생길 때 발생합니다.

  Repaint
  실제 보이는 것들 즉 가시성에 영향을 주는 엘리먼트가 변경되면 발생합니다. (background, display 등등) 보통 Reflow가 발생하면 Repaint가 발생합니다. 브라우저가 DOM Tree에 있는 다른 노드들의 가시성을 모두 확인해야해서 Reflow보다 Repaint가 비용이 더 많이 듭니다.

## <a name="4"></a>window와 document의 차이점은 무엇인가요?

- Document는 Window 안에 포함됩니다.
  우선, window는 모든 객체의 조상, 전역객체(글로벌객체)입니다. 모든 객체를 포함하고 있기 때문에 window는 생략하고 사용할 수 있고, 함수 안에서 선언한 변수를 제외한다면, 개인이 만든 변수도 모두 window 객체 안에 등록됩니다.
  이렇게 window는 글로벌 변수, 글로벌 기능, 위치, 내역 등을 저장하는 global object이며, setTimeout, ajax 호출(XMLHttpRequest), console, localStorage 또한 window의 일부입니다.
  이렇게 브라우저 전체를 담당하는 것이 Window 객체라면, 그중에서 웹페이지만 담당하는 것이 Document 객체입니다. Document가 Window 객체 안에 포함되는 것인데요. 저희가 Document.getElementById로 흔히 사용하는 것도 사실 Window.Document.getElementById입니다.
  또, Document에서 이렇게 getElementById 또는 addEventListener를 사용할 수 있는 이유는 모든 노드가 Document의 일부이기 때문입니다. 웹 페이지 그 자체를 의미하는 Document 객체는 HTML 요소의 선택, 생성, 이벤트 핸들러 추가, HTML 객체의 선택 등 HTML 요소와 관련된 작업을 도와주는 다양한 메서드를 제공합니다.
- `window객체`는 브라우저를 시작할 때 가장 처음 생성되는 객체로, 브라우저 탭에 존재하는 자바스크립트 전역 최상위 객체입니다. 따라서, `window 객체`는 어디서든 접근 가능합니다.이러한 `window 객체` 안에는 `document 객체`가 존재하는데요. 이 `document 객체`는 현재 표시된 웹페이지의 객체 모델로, DOM이라고도 합니다.여기서 `document.addEventListener` 를 할 수 있는 이유는, `event target object` -> `Node` -> `documnet` 의 순으로 상속을 받기 때문이고, 따라서 `document 객체` 안에 포함된 모든 노드들에 이벤트를 걸 수 있습니다.
- window객체는 브라우저에서 동작하는 자바스크립트의 전역 객체이다. document 객체는 DOM에 따라 각 html 노드를 트리로 구조화 한 객체이다. window가 전역 객체이므로 document객체는 window객체에 포함된다.
- 브라우저가 시행되면 전역 객체로 `window`가 생성된다. 그리고 이 안에 우리가 작성한 문서 영역(`Html`)에 해당하는 `document` 객체가 포함된다.브라우저는 이 `doucment`를 이해할 수 있도록 한줄 한줄 읽으면서 `DOM tree`를 만든다. `DOM`은 `Node` 타입의 트리로 구성되어 있고, `Node` 객체는 `EventTarget` 을 상속받기 때문에 `DOM` 요소에 대한 이벤트 조작이 가능하다.
- window는 각각의 브라우저 탭에서 자바스크립트에 대한 실행 컨텍스트 및 전역 객체입니다. Window 객체의 프로퍼티로는 document와 screen이 있으며, 전역 변수, 전역 함수, location, history, setTimeout, console 또는 localStorage 등을 가지고 있습니다. document 객체는 앞에서 말했던 것처럼 window 객체의 프로퍼티입니다. document는 window 객체가 먼저 브라우저에 로드된 이후, window 객체 안에 로드되는 객체입니다. 프로퍼티로는 title, URL, cookie 등이 있습니다. 모든 노드들은 document에 속하므로, `getElementById` 나 `addEventListener` 등을 사용할 수 있습니다.
- window는 DOM문서를 담은 창, Document속성이 창에 불러온 DOM 문서입니다.
  브라우저 전체를 담당하는게 Window 객체이고, 모든 객체의 조상, 그리고 생략가능합니다.
  모든 자료형을 포함하고있고, 우리가 만든 전역 변수들도 모두 window 객체 안에 등록됩니다.
  document는 window에 포함되며, 웹사이트만 담당합니다.

## <a name="5"></a>NodeList와 HTMLCollection에 대해 아는대로 설명해보세요.

- 기본적으로 NodeList와 HTMLCollection은 모두 복수의 결과값을 반환하기 위한 node의 컬렉션 객체라는 점에서 공통점을 가집니다. 하지만 몇 가지 차이점이 있기 때문에 이를 중심으로 비교해보겠습니다.
  우선, HTML Collection은 getElementsByTagName, getElementsByClassName 사용 시 리턴되는 형태입니다. TagName과 ClassName 모두 '복수'의 실행 결과를 리턴하기 때문에 HTML Collection인 것이며, getElementsById는 고유한 Id로 '단일'의 실행 결과를 리턴하기 때문에 HTML Collection이 아닌 HTML Elements인 것입니다.
  HTML Collection은 유사 배열이기 때문에 배열 객체에서 사용하는 메서드인 forEach는 사용할 수 없습니다. NodeList의 프로토타입에는 forEach, map이 없고, Array의 프로토타입에만 존재하기 때문입니다. Map을 사용하기 위해서는 Array.from(), Spread syntax 등을 이용해 사용할 수 있습니다.
  NodeList 객체는 일반적으로 element.childNodes와 같은 속성(property)과 document.querySelectorAll과 같은 메서드에 의해 반환되는 노드의 콜렉션입니다.
  NodeList도 Array가 아니지만, 프로토타입에 forEach()가 포함되어 있기 때문에 forEach를 사용할 수 있습니다. 하지만 역시 map, filter 등의 메서드를 사용할 수 없어서 Array.from() 등을 사용해 배열로 바꿔줘야 합니다. 그런데, Array.from은 IE에서는 사용할 수 없는데 그 때는 배열의 얕은 복사본을 새로운 배열 객체로 반환하는 slice를 이용하면 됩니다.
  또 한 가지 차이점은 DOM의 변경 사항이 실시간으로 변경되냐, 그렇지 않느냐인데요.
  HTMLCollection은 라이브 컬렉션입니다. 엘리먼트 중 하나를 변화시키면 그 즉시 컬렉션에 반영됩니다. 그래서 요소 하나하나를 순회하며 무언가를 처리하는데, 이 과정에서 변화가 일어나 순회하는 기준에서 빠져나가게 되면 원하는 결과를 얻지 못하게 되거나 버그를 만날 가능성이 있습니다.
  반면, document.querySelectorAll() 메소드에 의해 반환되는 NodeList는 정적(Static) 콜렉션인데요. static 이란 대응되는 새로운 요소가 페이지에 추가되더라도 리스트가 갱신되지 않는다는 뜻입니다. 따라서 DOM의 변경 사항이 실시간으로 반영되지 않습니다. 따라서, NodeList의 항목(items)을 순회(iterate)하거나, 특히 리스트의 길이를 캐시(cache)해야 할 때는 querySelectorAll을 사용하는 것이 좋습니다.

- `getElementsByClassName(), getElementsByTagName(), children` 메소드의 반환값은 `HTMLCollection(live)` 객체입니다. 이는 반환값이 복수인 경우 HTMLElement의 리스트를 담아 반환하는 객체입니다. 배열과 비슷한 사용법을 가지지만 배열은 아닌 `유사배열(array-like object)` 이고, 실시간으로 Node의 상태 변경을 하는 `라이브 컬렉션` 입니다.

  반면, `querySelectorAll, childNodes` 메소드의 반환값은 `NodeList(non-live)` 객체입니다. `NodeList(non-live)` 역시 유사 배열이지만, 실시간으로 Node의 상태 변경을 하지 않는 `정적 콜렉션`입니다.

- Answer

  1. HTMLCollection

     - getElementsByTagName, getElementsByClassName의 반환값 혹은 엘리먼트의 children 프로퍼티로 얻을 수 있다.

     - 유사 배열이다. (forEach 불가능)

     - 엘리먼트만 취급한다. 즉, children프로퍼티를 통해 얻을 수 있는건 자식 엘리먼트로 제한된다.

     - live object이다.

     - namedItem 메서드를 사용할 수 있다.

       → 인덱스가 아는 name 어트리뷰트를 통해 엘리먼트에 접근할 수 있다.

  2. NodeList

     - querySelectorAll의 반환 값 혹은 엘리먼트의 childNodes 프로퍼티로 얻을 수 있다.
     - 유사 배열이지만 forEach를 사용할 수 있다.
     - 모든 노드를 포함한다. 즉, childNodes는 텍스트 노드도 포함한다.
     - childNodes는 live Object, querySelectorAll의 결과만 non-live이다.

- `NodeList`와 `HTMLCollection` 모두 리턴 값이 복수인 경우에 반환되는 객체다. 유사배열로 배열과 비슷한 사용방법을 가지고 있지만, 배열은 아니다. `Array.from()`을 사용하여 배열로 변환하여 사용하면 배열의 메소드를 사용할 수 있다.

  NodeList
  \- `querySelectorAll` 을 사용했을 때 리턴되는 형태이다.
  \- `NodeList` 는 유사배열이지만, `forEach()` 를 이용하여 반복할 수 있다.
  \- 이용 가능한 메서드에는 `entries()`, `keys()`, `values()`가 있다.
  \- `querySelectorAll`을 통해 반환되는 값은 **정적 콜렉션**으로, DOM이 변경되어도 collection의 내용에는 영향을 주지 않는다.

  HTMLCollection
  \- `getElementsByTagName`, `getElementsByClassName`을 사용했을 때 리턴되는 형태이다.
  \- 유사배열이기 때문에 `forEach()`나 `map()`을 사용할 수 없다.
  \- 문서가 바뀔 때 **실시간으로 업데이트**가 된다.

- NodeList 객체는 일반적으로 element.childNodes와 같은 속성(property)과 document.querySelectorAll 와 같은 메서드에 의해 반환되는 노드의 콜렉션입니다. NodeList가 Array 는 아니지만, forEach() 를 사용하여 반복할 수 있습니다. 또한 Array.from() 을 사용하여 Array 로 변환 할 수도 있습니다. DOM의 변경 사항을 정적으로 콜렉션에 반영합니다. 하지만 Node.childNodes는 실시간으로 반영합니다. HTML Collection : `getElementsByTagName`, `getElementsByClassName` 사용 시 리턴되는 형태는 **HTMLCollection** 객체를 반환합니다. HTMLCollection 인터페이스는 요소의 문서 내 순서대로 정렬된 일반 컬렉션(arguments처럼 배열과 유사한 객체)을 나타내며 리스트에서 선택할 때 필요한 메서드와 속성을 제공합니다. 여기서 주의할 점은 HTMLCollection 은 배열과 유사한 객체 라는 것이라는 점입니다.. 배열 객체에서 데이터 순회 시 사용하는 `forEach` 같은 함수는 사용할 수 없습니다.

- Answer

  - HTMLCollection

    - `getElementsByTagName`, `getElementsByClassName` 같은 메서드 또는 element.children과 같은 속성에 의해 반환된다.
    - 유사배열이다 (`forEach()`나 `map()`을 사용할 수 없다).
    - 실시간(Live)으로 업데이트된다.

  - NodeList
    - `querySelectorAll` 과 같은 메서드에 의해 반환된다.
    - 유사배열이지만, `forEach()` 를 이용하여 반복할 수 있다.
    - NodeList는 정적(static) 콜렉션으로, DOM의 변경 사항이 실시간으로 반영되지 않는다.

## <a name="6"></a>DOM을 조작하는 메서드를 2가지 이상 말하고, 각각의 특징을 비교해서 설명해주세요.

- DOM 조작 메서드에는 removeChild(), append(), appendChild(), insertBefore(), cloneNode(), replaceChild(), closest() 등이 있습니다.
  이중에서 부모 노드에 자식 노드를 추가하는 메서드인 append와 appendChild의 특징을 비교해서 설명드리겠습니다.
  append 메서드는 ParentNode의 마지막 자식 뒤에 Node 객체 또는 DOMString 객체를 삽입하는 메서드입니다.
  매개변수로는 노드의 객체나 DOM String이 올 수 있고, 여러 개의 매개변수를 한 번에 전달하여 여러개의 자식 요소를 추가할 수도 있습니다.
  appendChild 메서드는 한 노드를 특정 부모 노드의 자식 노드 리스트 중 마지막 자식으로 붙이는 메서드인데요. append와는 달리 오직 node 객체만 매개변수로 받을 수 있고, 한 번에 여러 개의 노드를 받아 추가하는 것도 불가능합니다.
  append와 appendChild의 또다른 차이점 하나는 return 값의 유무인데요. append는 return값을 반환하지 않는 메서드라면, appendChild는 추가한 Node 객체를 반환합니다.

- `appendChild()` 와 `insetAdacentHTML()` 을 비교해보겠습니다.

  `appendChild()` 는 기준 노드의 가장 마지막 자식 요소로 새로운 노드를 삽입할 수 있습니다. 반면, `insetAdacentHTML()` 은 기준 노드 주위 원하는 위치에 새로운 노드를 삽입할 수 있습니다.

  `appendChild()` 의 경우 문자열이 아닌 노드 자체를 생성하여 삽입해야 하므로, 코드의 양이 다소 많고 복잡해 보일 수 있습니다. 반면에 `insetAdacentHTML()` 은 간단히 문자열로 노드를 작성하면 되므로 훨씬 편리합니다. 하지만, XSS공격에 취약하므로 사용자로부터 직접 입력 받는 콘텐츠를 추가할 때는 주위하여 사용하여야합니다.

- DOM요소들은 내부 요소를 조작 하는 여러 메서드를 제공한다. 대표적으로 다음의 두 가지를 들 수 있다.

  - insertAdjacentHTML
  - appendChild

  두 메서드 모두 자식 엘리먼트를 추가하는 기능을 제공한다. 먼저 insertAdjacentHTML은 두개의 인자를 받는다. 첫 번째 인자로 요소를 추가할 위치를 받는다. 이때 해당 위치는 현재 엘리먼트의 여는 태그와 닫는 태그를 기준으로 설정한다. 두 번째 인자로 추가할 엘리먼트를 받는다. 주목할 만한 점은 인자로 엘리먼트 자체가 아닌 문자열을 받는다는 것이다. html 태그로 구성된 문자열을 통해 추가하고자 하는 요소를 전달한다. 이러한 특징 덕에 겪는 문제가 필연적으로 존재한다. insertAdjacentHTML과 같이 문자열을 통해 요소를 전달하는 방법은 xss 공격에 취약하다.

  appendChild도 마찬가지로 자식 요소를 추가하는데 사용된다. 앞선 메서드와 다른점은 엘리먼트 자체를 인자로 받는다. 따라서 xss 공격에 대해 비교적 안전하다. 이름에서 알 수 있듯 인자로 받은 요소를 마지막 자식으로 추가하게 된다.

- DOM 요소를 생성하는 메서드에는 `createElement()`가 있습니다. 또 텍스트만을 인자로 받아서 텍스트노드를 생성하는 `createTextNode()`가 있습니다.

  DOM요소를 삽입하는 메서드에는 호출된 노드의 가장 마지막 자식으로 노드를 추가하는 `appendChild()`, 원하는 위치에 요소를 삽입할 수 있는 `insertAdjectionHtml()`, 기존의 모든 요소를 삭제하고 쉽게 새로운 요소를 추가할 수 있는 `innerHTML`이 있습니다.

  `insertAdjectionHtml()`은 원하는 위치에 요소를 추가해야 하기 때문에, element의 어느 위치에 값을 넣을지 `beforebegin`, `afterbegin`, `beforeend`, `afterend`의 position에 대한 인자를 첫번째로 받아야하고, 두번째 인자로 DOM String을 받습니다. 하지만, 기존의 모든 요소를 삭제하고 새로운 요소를 넣는 innerHTML의 경우에는 Html 문자열을 직접 할당해줍니다.

  DOM요소를 삭제하는 메서드에는 `removeChild()`가 있습니다. 이는 선택할 노드를 인자로 받습니다.
  DOM요소를 수정하는 메서드는 `replaceChild(newChild, oldChild)`가 있습니다. 이는 특정 부모의 바꾸고 싶은 노드를 다른 노드로 교체합니다.

- DOM을 조작하는 메서드로 `innerHTML`와 `appendChild`가 있습니다.

  `innerHTML`을 사용하는 경우는, 브라우저가 element의 현재 모든 자식 노드를 삭제하고 String을 해석한 후 element의 자식으로 해석한 string을 할당합니다. `innerHTML`의 특징으로는 string을 해석하는 과정에서 속도가 느릴 수 있다는 점입니다. 규격에 맞지 않은 html을 가지고 있는 경우, 브라우저가 string을 해석하는는 과정에서 처리해야하기 때문입니다.

  다음으로 `appendChild`가 있습니다. `appendChild`는 새로운 element를 만듭니다. 이 과정에서 브라우저는 string을 해석하지 않아도 됩니다. 간단하게 자식을 넘기면 부모에 추가됩니다.

- DOM을 조작하는 메서드로는 `querySelectorAll`, `getElementsByClassName`이 있습니다.
  querySelectorAll의 Element.childNodes는 NodeList 객체를 반환하지만 정적 콜렉션이고, getElementsByClassName으로 가져온 리스트는 Live Collection으로 DOM의 변경사항이 실시간으로 적용되는 차이가 있습니다.
