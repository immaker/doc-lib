#Angular2 Series: 소개

최근에 angular2와 ionic2가 공개되고 있다. 우리는 훌륭한 팀과 함께 ionic의 다음 큰 버전을 발표하기 위해 노력하고 있고 그 과정에서 angular2가 돕고 있다. 나는 우리가 짧은 시간안에 그 과정을 만들었다는 사실에 믿을수 없을만큼 흥분되고, ionic 커뮤니티가 사랑받고 있는것을 알고 있다.
 angular2에 나타난 엄청난 변화를 많은 이들이 사랑한다(또는 그 사랑을 싫어함). v1(directive, anyone?)을 배우고, scopes와 digest cycles work를 이해하는 것, ngModel 이슈들을 디버깅하는 시간, 그리고 완벽한 폴더구조를 위해 너무 많은 시간이 소비되었다. 그리고 지금 대부분이 바뀌고 있다.
 나를 믿어라. 이게 최선이다.
 
 Angular2 Series
 ---
 ionic team은 큰 프로젝트를 위해 angular2를 일찍 적용한 팀중에 하나이다. 왜냐하면 우리는 복잡하고 제한적인 것에 대한 angular2의 힘을 학습할 수 있었다. 커뮤니티는 angular2를 포용할 것을 알고, 우리의 경험을 공유하고 angular2 frontend 개발자들에게 교육을 시작해야한다.
 이번주를 시작으로 angular2에 대한 짧은 포스팅 시리즈를 시작할 것이다. 이 포스트들은 angular2가 어떻게 사용되고 도움을 줄수 있는지에 대하여 다양한 부분들을 다룰것입니다.
 
 Getting started
 ---
 angular2 [quickstart guide](https://angular.io/docs/js/latest/quickstart.html) 를 따라하지만, 더 추가된 색상과 해설을 살펴보자.
 
 먼저, 프로젝트 폴더를 만들고 quickstart repo 안의 코드를 복사 :
 
     mkdir myApp
     cd myApp
     git clone git@github.com:angular/quickstart.git
     
###HTML

새로운 `index.html` 만든다 :

    <!-- index.html -->
    <html>
      <head>
        <title>Angular 2 Quickstart</title>
        <script src="/quickstart/dist/es6-shim.js"></script>
      </head>
      <body>

        <!-- The app component created in app.es6 -->
        <my-app></my-app>

        <script>
          // Rewrite the paths to load the files
          System.paths = {
            'angular2/*':'/quickstart/angular2/*.js', // Angular
            'rtts_assert/*': '/quickstart/rtts_assert/*.js', // Runtime assertions
            'app': 'app.js' // The my-app component
          };

          // Kick off the application
          System.import('app');
        </script>    
      </body>
    </html>
    
당신의 첫 반응은 아마도, "이상한 __System.*__ 으로 된 것들은 뭐야?" 일 것이다. System은 브라우저에게 es6 module 로딩을 지원한다. 이것들은 가치가 없고, 지금 angular2의 상용구들 처럼 이것도 없어질것 입니다. (or at least we will abstract it out in Ionic 2, 당신은 이것을 볼 필요가 없습니다.) 배우고, 즉시 잊으시오.

###Javascript

다음으로 우리는 몇가지 ES6을 작성해야한다!

__app.js__를 코드안에 불러온다. (그 문서들은 __.es6__을 사용한다. 그러나 나는 이런 확장스타일을 추천하지 않는다. 이것은 유행하지도 않을 것으로 보인다).

    import {Component, Template, bootstrap} from 'angular2/angular2';

    // Annotation section
    @Component({
      selector: 'my-app'
    })
    @Template({
      inline: '<h1>Hello {{ name }}</h1>'
    })
    // Component controller
    class MyAppComponent {
      constructor() {
        this.name = 'Alice'
      }
    }
    bootstrap(MyAppComponent)

이것에 대해 흥미로운 점은 우리가 응용 프로그램 구성 요소를 지정하는 방법입니다. 부트 스트랩 (MyAppComponent) 호출은 ng-app이 그랬던 것처럼, 시작하는 응용 프로그램을 알려줍니다. 이 외에, 우리는 응용 프로그램을 시작하는 실제 컨포넌트를 제공 하였다.

시작해보자!

만약 당신이 local HTTP server가 설치되어 있지 않으면,  
___npm install -g http-server___ or ___python -m SimpleHTTPServer___ 를 통해 사용할 수 있습니다.
이중 하나를 사용하는 법을 학습하는 것을 추천합니다.

	http-server

브라우저에서 ___http://localhost:8080___을 들어가면, 브라우저에 Hello Alice 를 확인할 수 있습니다.

###TypeScript?
간단화하기 위해서, 시작 프로젝트는 Traceur 에서 pre-built 버전을 사용합니다.

그러나,  the project is moving to TypeScript right as we speak, which will make the whole toolchain a lot simpler. 간단하게 말해서 당신은 Traceur을 배우거나 그 이름을 기억할 필요도 없습니다.

###Next up: Components

위의 파일에서 우리는 첫번째 컴포넌트를 만들었습니다. 컴포넌트는 angular2의 핵심이며, 우리가 알고 있던 v1의 Controllers,Scopes와 Directives의 섬세한 혼란을 대체 할 것입니다.

우리는 우리의 다음 게시물에 더 많은 구성 요소에 대해 이야기 할 것이다, 그래서 계속 지켜봐 주시기 바랍니다!



원본
---
[Angular 2 Series: Introduction](http://blog.ionic.io/angular-2-series-introduction/)