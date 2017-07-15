Ionic2 
=========

### Ionic2는 타입스크립트로 작성되며 Angular2를 기반으로 한다.

========
Ionic2 프로젝트 폴더 구조
----------------------

## src 폴더의 내용이 www 폴더로 변환되는 과정
*모든 프로그래밍 작업은 src 폴더에서 진행한다.
*ionic serve로 앱을 실행하면 src폴더의 내용이 컴파일되고 합쳐져서 www 폴더로 저장된다.
*ionic serve로 앱 실행 전에는 www 폴더가 비어있다가, 첫 실행시 assets, build 폴더가 생성되고 index.html 파일등이 생성된다.
*src 폴더 내의 모든 scss 파일들이 css로 컴파일 되고 함쳐져서 www/build/main.css로 저장된다.
*src 폴더 내의 모든 ts 파일들은 js로 컴파일되고 합쳐져서 www/build/main.js로 저장된다.
*scss 파일을 추가하고자 한다면, src/pages 폴더 아래 꾸미고 싶은 탭 폴더 밑에 생성하면 된다.



Ionic import와 export
--------------------
import와 export 모두 타입스크립트 구문이다.
import는 사용하고픈 모듈이 있을시에 선언한다.
export의 경우에는 어떤 클래스를 다른 곳에서 import 해서 사용하고 싶다면,
export임을 선언해주어야 한다.

ex)
<pre><code>
import { StatusBar } from 'ionic-native';


export class MyApp{
	rootPage = HomePage;

	constructor(platform: Platform){
		platform.ready().then(() => {
			StatusBar.syleDefault();
		});
	}
}
</code></pre>



 Decorator
---------------------

@Component
*컴포넌트 : 버튼, 아이콘, 메뉴, 툴바 등과 같이 앱을 구성요소나 전반적인 로직을 말한다.
         컴포넌트는 하나의 페이지에 한개 또는 여러개가 있을 수 있다. 

Decorator(꾸며줌)  =====> 클래스 앞에 @Component를 해주면 그 클래스는 컴포넌트가 된다.
		   
ex) 
<pre><code>

    @Component() class ABC{.....} 와 같이 하면 클래스 ABC는 컴포넌트가 된다.
    유사하게 @Pipe() class EFG{.....}이 되면 EFG는 파이프가 된다.
</code></pre>

클래스 멤버 변수에도 Decoration을 사용할 수 있다.
ex)

   @Input variable1   ---> 값을 외부로부터 받는 변수
   @Output variable2  ---> 값을 외부로 내보내는 변수
</code></pre>

컴포넌트에는 하나의 객체 파라미터를 전달할 수 있는데 이를 메타데이터라고 한다.
ex)  
<pre><code>
    @Component({...........})
                 메타데이터(객체)

    @Component({
	selector:...  컴포넌트를 어디에 표시할지 결정
	template:...  컴포넌트 내용을 담는 곳
     })
     		  
</code></pre>

src/app/app.component.ts (App Component)
-----------------------------------------

App Component는 root 컴포넌트라고도 하는데 이는 가장 처음 실행되고 다른 모든 컴포넌트를 포함하기 떄문이다.

<pre><code>
import { Component } from '@angular/core';
import { Platform } from 'ionic-angular';
import { StatusBar } from '@ionic-native/status-bar';
import { SplashScreen } from '@ionic-native/splash-screen';

import { TabsPage } from '../pages/tabs/tabs';

@Component({
  templateUrl: 'app.html'
})
export class MyApp {
  rootPage:any = TabsPage;

  constructor(platform: Platform, statusBar: StatusBar, splashScreen: SplashScreen) {
    platform.ready().then(() => {
      // Okay, so the platform is ready and our plugins are available.
      // Here you can do any higher level native things you might need.
      statusBar.styleDefault();
      splashScreen.hide();
    });
  }
}

</code></pre>
