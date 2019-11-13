# Unification
Data를 통해 여러 방식으로 Node와 Edge를 생성할 수 있습니다.

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|------
modeCloneNodeWhenDuplicateLink | Boolean | true | 하나의 부모노드만 갖도록 자동으로 Clone합니다.  
modeUniqueDataInSameGroup | Boolean | false | 같은 그룹안에 같은 Data가 존재할 경우 하나로 통합합니다.
modeUniqueData | Boolean | false | 같은 Data가 여러개 존재할 경우 하나로 통합합니다.
modeOrderByGroup | Boolean | true | Group순으로 노드간 연결합니다.
orderList | Array | null | Group간 연결 순서
modePruneNodeWithoutEdge | Boolean | true | Edge정보가 없는 Node를 표시하지 않습니다.
modePruneNodeNotToRootGroup | Boolean | true | Root Node까지

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



## modeCloneNodeWhenDuplicateLink
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
        
  
  
## modeUniqueDataInSameGroup
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


## modeUniqueData
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

## modeOrderByGroup
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
  

## orderList


## modePruneNodeWithoutEdge



## modePruneNodeNotToRootGroup