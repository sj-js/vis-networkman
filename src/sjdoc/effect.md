# Effect
Data를 통해 여러 방식으로 Node와 Edge를 생성할 수 있습니다.

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|-----
modePointAllSubLink | Boolean | false | Node Pointing시 가장 연결된 Root Node까지 선택표시할지 여부
modeSelectAllSubLink | Boolean | false | Node Select시 가장 연결된 Root Node까지 선택표시할지 여부
nodeWhenStart | Object | null | Node 초기설정 
edgeWhenStart | Object | null | Edge 초기설정
nodeWhenPoint | Object | null | Node에 마우스를 올렸을 때 설정
edgeWhenPoint | Object | null | Edge에 마우스를 올렸을 때 설정
nodeWhenSelect | Object | null | Node를 선택했을 때 설정
edgeWhenSelect | Object | null | Edge를 선택했을 때 설정

#### ※ 자동적용
- 편의를 위해서 예제에서는 다음 코드가 생략되어 있습니다.
    ```html
    <style>
        div[data-box] {width:200px; min-height:30px;}
        div[data-obj] {width:50px; height:30px;}
    </style>
    ```
    
    *@* *+prefix* *x* *@* 
    ```html
    <link rel="stylesheet" href="../boxman/boxman.css">
    <script src="../crossman/crossman.js"></script>
    <script src="../boxman/boxman.js"></script>
    <script>
        var boxman = new BoxMan();
    </script>
  
    <style>
        div[data-box] {width:200px; min-height:30px;}
        div[data-obj] {width:50px; height:30px;}
    </style>
    ```



## modePointAllSubLink
- 테스트시, 눈에 띄는 스타일로 표시할 수 있습니다. 
    *@* *!* *@*
    ```html
    <script>
        boxman.setup({modeTest: true}).detect();     
    </script>
    
    <body>
        <div data-box>BOX A</div>
        <div data-box>
            BOX B
            <div data-obj>OBJ A</div>
        </div>
    </body>
    ```
  
  추가 속성 
- testBoxClass: 테스트모드시, Box에 부여할 class
- testBoxBorderWidth: 테스트모드시, Box의 테두리 크기
- testBoxBorderColor: 테스트모드시, Box의 테두리 색
- testObjClass: 테스트모드시, Obj에 부여할class
- testObjBorderWidth: 테스트모드시, Obj의 테두리 크기
- testObjBorderColor: 테스트모드시, Obj의 테두리 색
        
  
  
## modeSelectAllSubLink
- OBJ를 다른 BOX로 옴길 때마다 복사됩니다.
    *@* *!* *@*
    ```html
    <script>
        boxman.setup({modeCopy: true}).detect();     
    </script>
    
    <body>
        <div data-box id="box">BOX A</div>
        <div data-box>
            BOX B
            <div data-obj>OBJ A</div>
        </div>
    </body>
    ```


## nodeWhenStart
- OBJ는 BOX 이외에는 이동할 수 없도록 합니다.
    *@* *!* *@*
    ```html
    <script>
        boxman.setup({modeOnlyBoxToBox: true}).detect();     
    </script>
    
    <body>
        <div data-box id="box">BOX A</div>
        <div data-box>BOX B</div>
        <div data-box>
            BOX C
            <div data-obj>OBJ A</div>
        </div>
    </body>
    ```

    *@* *!* *@*
    ```html
    <script>
        boxman.setup({modeOnlyBoxToBox: false, defaultBox: document.body, modeDefaultAbsolute:true}).detect();     
    </script>
    
    <body>
        <div data-box id="box">BOX A</div>
        <div data-box>BOX B</div>
        <div data-box>
            BOX C
            <div data-obj>OBJ A</div>
        </div>
    </body>
    ```
    
    - `defaultBox`: modeOnlyBoxToBox가 false일 때, 이 옵션값에 따라 원하는 Element로 설정할 수 있다. (Default: `document.body`)
    - `modeDefaultAbsolute`: Style속성인 position의 값을 absolute로 할 것인지를 설정한다.  (Default: `true`)

## edgeWhenStart
- OBJ를 박스 밖으로 보내면 삭제됩니다.
    *@* *!* *@*
    ```html
    <script>
        boxman.setup({modeRemoveOutOfBox: true}).detect();     
    </script>
    
    <body>
        <div data-box id="box">BOX A</div>
        <div data-box>
            BOX B
            <div data-obj>OBJ A</div>
        </div>    
    </body>
    ```
  

## nodeWhenPoint


## edgeWhenPoint



## nodeWhenSelect


## edgeWhenSelect