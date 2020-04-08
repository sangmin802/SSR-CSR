# SSR-CSR
 
## SSR(서버 사이드 렌더링) : MPA(멀티 페이지 어플리케이션)  
  * 장점
    + SEO(검색엔진환경)에 적합하다.  
    + 초기화면 로딩이 빠르다.  
  * 단점
    + 요청값이 있으면, 웹서버에서 해당 View를 새로 만들어서 보여주기때문에, 로딩(하얀)화면이있다.  
    + CSR보다 비교적 개발이 복잡해진다.  
    + 클라이언트와 서버가 상호작용하는 기능은 사라짐.(해당 내용은 개선되었음)  
  * 배포과정  
    - 기존 MPA방식  
      1. bundling(webpack)을 통해 build된 static folder가 생성됨.  
      2. 배포를 하면, 서버에서 bundle된 js파일을 통해 View화면을 생성함.  
      3. 생성된 View를 브라우저에 던져줌.  
    - SPA + SSR (서버와 클라이언트간 상호작용이 강점인 SPA 및, SEO개선을위한 SSR 병합)  
      4. 위의 3단계와 동일함.  
      5. 던져진 View화면의 bundle요청 script를 읽어옴.  
      6. SPA의 강점인 상호작용이 가능해지고, 초기에 서버에서 View화면단을 생성해서 브라우저에게 주었기 때문에, 검색엔진에 노출도 가능해짐.  
## CSR(클라이언트 사이드 렌더링) : SPA(싱글 페이지 어플리케이션)
  * 장점  
    + 브라우저 환경에서 View를 생성하고, 일부분만 수정하여 로딩되는 화면이 없다.  
    + 1번의 이유와, 이후 추가 요청 시 서버에서는 Json파일만 res해주기 때문에, 서버의 부담이 적어진다.  
    + 비교적 개발 및 배포가 수월해진다.  
  * 단점  
    + 구글을 제외한 대부분의 검색엔진에서 노출되지 않는다.  
  * 배포과정  
    1. bundling(webpack)을 통해 build된 static folder가 생성됨.  
    2. 배포를 하면, static folder의 HTML파일(static file)을 서버에서 브라우저에게 던져줌.  
    3. 해당 HTML파일에는 root가 되는 비어있는 div태그 하나만 있으며, 하단에 script호출로 bundle된 스크립트를 불러오게 되어있음.  
      - 3번의 이유로, 구글같은 경우 브라우저에서 javaScript언어를 읽어 출력할 수 있지만, 대부분의 브리우저들은 javaScript언어를 읽지못해 View화면을 생성하지 못함.(검색엔진에서는 생성된 View화면(HTML)파일을 읽고 노출시키는 특성)  
      - 따라서, View를 생성하는데에 여러 과정을 거치기 떄문에, 시간이 걸림. 만약, bundle script를 읽고 기본 셋팅을 위해 백엔드에서 갖고와야하는 값들이 있다면 더 걸리겠지?
    4. 클라이언트의 요청을 받으면, 서버에서 값만 받아와 해당 부분만 즉각 수정시킴.    
## 정리  
  * SSR, CSR 둘 다 빌드 이후, 서버로 배포(서비스)가 가능하지만, View화면을 서비스하는 방법이 다르다.  
