# Extends Panel
Mode 속성으로 `특정효과`를 설정할 수 있습니다.

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|------
modeExtendsPanel | Boolean | false | ExtendsPanel의 사용여부
modeExtendsPanelAutoHide | Boolean | false | ExtendsPanel을 자동으로 숨기고 마우스커서를 올리면 보입니다.
modeExtendsPanelSaveToLocalStorage | Boolean | false | ExtendsPanel의 Toggle정보를 저장할지 여부
saveKey | String | ... | ExtendsPanel의 Toggle 정보를 저장할 LocalStorage의 Key를 지정합니다. 기본값: `/toggleman/visnetworkman/`
extendsPanelToggleDefaultIndexMap | Object | ... | ExtendsPanel을 사용시 ToggleButton의 기본값을 설정합니다. 기본값: `{"direction":0,"directionMethod":0,"duplication":0,"unification":0,"edgeLimit":4}` 
extendsPanelShowItemList | Array | null | ExampleForAll) null   //- ExampleForNothing) []   //- ExampleForSelective) ['direction', 'edgeLimit']
extendsPanelHideItemList | Array | null | ExampleForNothing) null or []   //- ExampleForSelective) ['direction', 'edgeLimit']

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



## modeExtendsPanel
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
        
  
  
## modeExtendsPanelAutoHide
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


## modeExtendsPanelSaveToLocalStorage
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

## extendsPanelToggleDefaultIndexMap
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



## extendsPanelShowItemList



## extendsPanelHideItemList



