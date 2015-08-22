#Cocos2d-JS의 Hello World
이번 튜토리얼에서는, 새로운 Cocos2d-JS 프로젝트를 어떻게 설정하는지 보여줄 것입니다. 그 전에, Cocos2d-JS의 디렉토리 구조에 대한 설명을 드리려고 합니다.

## Cocos2d-JS 디렉토리 구조 개요
여기에 Cocos2d-JS 디렉토리의 구조가 있습니다:

**Figure1**

![directory](res/directorystructure.png)

###디렉토리 구조 이해하기

디렉토리 구조는 세가지 파트로 나눌 수 있습니다:

#### Part1: 엔진 관련 폴더

* **frameworks** 디렉토리는 Cocos2d-html5 엔진과 Cocos2d-x 자바스크립트 바인딩을 관찰합니다.
    * **Cocos2d-html5** 디렉토리는 엔진 코어 모듈, 오디오 모듈, 외부 물리 라이브러리, 코코스 빌더 리더, 코코스 스튜디오 리더와 기타 모듈 등 Cocos2d-html5의 모든 엔진 모듈이 위치합니. 모든 모듈은 JS에서 임플리먼트되며 웹에서 실행될 수 있습니다.
    * **js-bindings** 디렉토리는 바인딩 프로젝트 파일과 외부 프리빌트 SpiderMonkey 라이브러리 등을 Cocos2d-x 엔진을 관리합니다. 베이스 모듈은 Cpp로 임플리먼트 되며, iOS, android, Mac, win32 등 네이티브 플랫폼에서 동작할 수 있습니다.
    
#### Part2: 테스트, 샘플 게임과 템플릿

* **template** 디렉토리는는 새로운 Cocos2d-JS 프로젝트를 생성하는데 사용됩니다. HTML5 프로젝트와 네이티브 프로젝트를 기본 값으로 포함합니다. 대개 cocos console을 통해 새로운 프로젝트를 생성할 때 사용됩니다.

* **samples directory** Cocos2d-JS의 모든 테스트를 포함합니다. 또한 플레이 가능한 샘플 게임인 문워리어를 포함하고 있습니다. 모든 테스트와 게임은 cocos console에 의해 웹에서 실행되거나 자바스크립트 바인딩으로 네이티브 플랫폼에서 실행됩니다.

#### Part3: 기타

* **README** Cocos2d-JS에 대한 소개글입니다.
* **LICENSE**에 대해 말하기에 앞서, Cocos2d-JS의 라이센스는 MIT이며, Cocos2d-html5와 Cocos2d-x의 라이센스에 대하여 더 많은 정보를 얻으시려면 엔진 루트의 license 폴더를 참조하세요.
* **tools** 디렉토리는 cocos console과 bindings-generator를 포함합니다. 클로져 컴파일를 위한 설정 파일인 build.xml로 Ant를 통해 하나의 파일로 게임을 패키지할 수 있습니다.
* **build** 디렉토리는 내장 샘플을 위한 프로젝트 파일을 포함합니다.
* **docs** 디렉토리는 릴리스 노트와 자바스크립트 코딩 스타일 가이드를 포함합니다.
* **CHANGELOG**는 모든 버전의 변경 정보를 포함합니다.
* **setup.py**는 개발 환경 설정을 위한 파이썬 스크립트입니다.


## 내장 샘플 살펴보기

Cocos2d-JS를 성공적으로 다운 받고 개발 환경을 구축했다면 내장 샘플을 살펴볼 것을 강하게 추천하고 싶습니다. Cocos2d-JS 기능의 90% 이상을 커버하며 또한 현재 당신이 가질 수 있는 가장 가치있는 학습 리소스입니다.
 

### 테스트 살펴보기
**Cocos2d-JS/samples/js-tests** 디렉토리로 이동해서, cocos console로 테스트를 실행합니다. 

```
    cocos run -p web
```

Cocos2d-JS의 모든 내장 테스트를 볼 수 있습니다. 스크린샷은 다음과 같습니다:

**Figure 2**

![tests](res/tests.png)

테스트는 당신을 위한 최고의 학습용 리소스입니다. 테스트는 Cocos2d-html5의 거의 모든 기능을 보여줍니다. 이런 테스트 파일들을 수정할 수 있으며 브라우져 새로고침을 통해 즉시 피드백을 받아볼 수 있습니다. 이 방법은 방대한 문서를 읽는 거보다 Cocos2d-html5의 맛을 제대로 느끼기에 좋은 시작입니다.

당신은 또한 테스트를 iOS, Android, Mac에서 실행할 수 있습니다.

```
    cocos run -p ios|android|mac
```


### 샘플 게임 살펴보기

Cocos2d-JS에서 내장된 전체 게임 소스가 있습니다. 모든 소스 코드는 완전히 무료이며 공개되어 있습니다. 샘플 게임에 대해서 간단한 소개를 드리겠습니다.

#### 문워리어

샘플 게임의 이름은 문워리어입니다. **js-moonwariors**의 디렉토리의 루트로 가서 cocos console로 실행해보세요.

```
    cocos run -p web|ios|android|mac
```

Here is the screenshot, you can dive into the source code for more information:
종스크롤 슈팅 게임입니다. 이 게임 샘플에서, 타일맵, 애니메이션, 시차 배경 등 많은 유용한 게임 테크닉을 배울 수 있습니다. 소스 코드를 들여다보면 더 많은 정보를 얻을 수 있습니다. 

**Figure 3**

![moonwarrior](res/moonwarrior.png)


## 당신의 첫 프로젝트 설정하기 "Hello World"

In the future, all of these epic tutorials are about how to make a Parkour game with Cocos2d-JS.
마지막으로, 우리는 이번 튜토리얼의 마지막 가장 중요한 부분에 도달했습니다. 여기서 정말로 "Hello World" 프로젝트를 만들지는 않을 것입니다. 예제로서 달리기(Parkour) 게임을 만들 것입니다. 장차, Cocos2d-JS와 함께 어떻게 달리기 게임을 만드느냐에 대한 튜토리얼들이 계속될 것입니다.

기다릴 필요 없이 지금 바로 시작하겠습니다!

### 달리기 프로젝트 뼈대(skeletion) 만들기

말하기에 앞서, 특정한 이름으로 프로젝트를 만들 수 있습니다. 당신의 작업공간으로 이동해서 cocos console로 **Parkour** 프로젝트를 생성합니다.

```
    cocos new Parkour -l js
```

이제 WebStorm을 실행해서 Parkour 디렉토리를 열면 다음과 같은 프로젝트 네비게이터를 볼 수 있습니다:

**Figure 4**

![newnavigator](res/newnavigator.png)

**index.html**를 WebStorm에서 우클릭하고 **Debug 'index.html'**를 선택합니다. 자동으로 크롬이 열리고 성공적으로 새로운 프로젝트가 실행될 것입니다. 축하합니다! 브라우져 주소는 다음고 같습니다.

```
http://localhost:63342/Parkour/index.html
```

이 것은 전형적인 **Hello World** 스크린샷을 보여줍니다:

**Figure 5**

![helloworld](res/helloworld.png)



### 샘플 게임 템플릿 코드 분석

**template**에서 아주 많은 것을 가져왔지만, 우리는 그 것들이 어떤 것인지 알지 못합니다.

예를 들어 무엇이 템플릿 프로그램의 주요 항목일까요? 이런 파일들은 어떻게 정리되어 있을까요? 샘플 프로그램에서 각 파일은 무엇을 합니까? 이런 질문들에 대해서 설명을 하려고 합니다.

#### 프로젝트의 모든 파일 살펴보기

처음으로, Figure 4의 디렉토리 구조와 모든 파일을 살펴봅니다:

Figure 4에서 다음과 같은 내용들을 확인할 수 있습니다:

- **res** 디렉토리: 프로젝트가 필요로 하는 모든 자원 파일을 포함하고 있습니다. 현재는 샘플 사진만을 포함하고 있지만 원한다면 게임의 메타 파일이나 놀라운 게임 음악 파일을 추가할 수도 있습니다. 이 폴더에 넣으면 됩니다. 각 파일에 적절한 이름을 선택해서 이 폴더에 넣어주세요. 

- **src** 디렉토리: 모든 실제 게임 로직 코드를 포함합니다. 백개의 자바스크립트 코드 파일이 있다면, 서브 폴더를 사용해서 정리하는 것이 나을 것입니다. 현재 템플릿에는 두 개의 자바스크립트 소스 파일이 있습니다. **app.js**는 샘플의 첫번째 씬 코드를 포함합니다. **resource.js**는 리소스의 전역 변수를 정의합니다.

- **index.html** : HTML5 기반의 웹 어플리케이션의 시작 지점이 위치한 파일입니다. HTML5와 호환되며 뷰포인트와 전체화면 파라미터 등 메타 데이타를 정의합니다.

- **project.json** : 프로젝트의 설정 파일입니다. [project.json](http://www.cocos2d-x.org/docs/manual/framework/html5/v3/project-json/en)를 보시면 자세한 정보를 확인하실 수 있습니다.

- **main.js** : 브라우져에서 첫 게임 씬을 생성하고 보여주도록 합니다. 또한 해상도 정책을 정의하고 음악, 이미지 등 리소스를 사전 불러오기(preload)합니다.

당신은 기본적인 프로젝트의 파일과 디렉토리에 대해 알게 되었습니다. 이제 실행 경로와 소스 코드를 이해할 차례입니다.

#### 프로젝트 실행 경로 분석

프로그램의 실행 경로를 아는 것은 매우 중요합니다.

Then it moves to **frameworks/Cocos2d-html5/CCBoot.js**.  from the project.json file.
프로젝트는 브라우져를 통해 index.html을 불러옵니다. 그리고 **frameworks/Cocos2d-html5/CCBoot.js**. 이 파일에서, project.json 파일을 통해 프로젝트 설정을 불러옵니다.

```
{
    "project_type": "javascript",

    "debugMode" : 1,
    "showFPS" : true,
    "frameRate" : 60,
    "id" : "gameCanvas",
    "renderMode" : 0,
    "engineDir":"frameworks/cocos2d-html5",

    "modules" : ["cocos2d"],

    "jsList" : [
        "src/resource.js",
        "src/app.js"
    ]
}

```

코드를 보면, **engineDir**라는 오브젝트 속성 이름을 가진 프로그램의 실행경로를 결정하는 키포인트를 찾을 수 있습니다. 이런 기본 케이스에서는, 이미 engineDir이 정해져 있습니다.

**frameworks/Cocos2d-html5/CCBoot.js**이 실행된 후에 main.js가 실행되며 설정을 초기화하고 **modules**과 **jsList**에 정의된 모든 자바스크립트 파일을 불러옵니다.

### 프로젝트 약간 수정하기

이전 섹션에서 알아본대로, 실제 코드 작업을 하기에 앞서서 약간의 수정 작업을 거쳐야 합니다.

#### 게임 씬의 좌측 코너의 FPS 숨기기

이 부분은 아주 사소할 수 있습니다. 우리는 **project.json**의 **showFPS** 속성을 **false**로 바꿈으로서 아주 쉽게 FPS를 숨길 수 있습니다.

코드:

```
{
    "project_type": "javascript",

    "debugMode" : 1,
    "showFPS" : false,
    "frameRate" : 60,
    "id" : "gameCanvas",
    "renderMode" : 0,
    "engineDir":"frameworks/Cocos2d-html5",

    "modules" : ["cocos2d"],

    "jsList" : [
        "src/resource.js",
        "src/app.js"
    ]
}
```

우리가 수정할 수 있는 많은 오브젝트 속성들이 있습니다. 여기에 속성 테이블이 있습니다.

property name | options | explanation
------------ | ------------- | ------------
debugMode | 0,1,2,3,4,5,6  | 0: close all 1: info level 2: warn level 3: error level 4: info level with web page 5: warn level with web page 6: error level with web page
showFPS | true 또는 false  | FPS 표시 여부
id | "gameCanvas"  | cocos2d가 실행될 DOM 요
frameRate | 24 이상을 추천, 대개 60-30  | 게임의 프레임 속도를 조정
renderMode | 0,1,2 | 렌더 모드 선택: 0(기본), 1(캔버스), 2(WebGL)
engineDir | 프로젝트에서 사용할 엔진 디렉토리  | specify the directory the engine code  
modules | 엔진 모듈  | 사용할 엔진을 모듈에 의해 커스터마이즈할 수 있습니다. **frameorks/Cocos2d-html5** 디렉토리의 moduleConfig.json을 보시면 모듈에 대해 알 수 있습니다.
 jsList | 게임 소스 코드 리스트  | myApp.js 다음에 사용할 파일 리스트 추가
 
 

#### 해상도 변경하기

Cocos2d-JS는 웹 브라우져에서 게임 캔버스의 전체화면을 보여줍니다. iOS와 안드로이드가 자바스크립트 바인딩 테크닉에 의해 균일하게 실행되도록 하기 위해서 캔버스 사이즈가 수동으로 조절될 필요가 없습니다. 해상도를 480*320으로 변경하기 위해서 main.js 파일의 **cc.game.onStart** 함수의 해상도를 480, 320으로 변경합니다.

그리고 해상도 정책을 **SHOW_ALL**로 바꿔줍니다.:

```
    cc.view.setDesignResolutionSize(480, 320, cc.ResolutionPolicy.SHOW_ALL);
```

이에 대해서 궁금하신 점이 있으시다면 [Resolution Policy Design for Cocos2d-html5](http://www.cocos2d-x.org/docs/manual/framework/html5/v2/resolution-policy-design/ko)를 보시면 더욱 상세한 정보를 확인하실 수 있습니다.

## 요약

이번 튜토리얼에서,  우리는 Cocos2d-JS의 디렉토리 구조와 빌트인 테스트와 샘플 게임에 대해 이야기했습니다. 또한 Cocos2d-JS가 제공하는 템플릿 기반으로 첫 프로젝트를 생성하고 마지막으로 템플릿의 파일과 코드 구조에 대해 분석했습니다.

## 다음은?

다음 튜토리얼에서는, 게임 메인 메뉴씬을 설정하는 법을 보여주려고 합니다. Cocos2d-JS와 함께 더 많은 코딩을 할 것입니다.
