# Event
`OBJ`가 `이동함에 따라 Event`를 발생시킬 수 있습니다. 

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|-----
funcEventSetupNode | Function | null | Node를 초기설정
funcEventSetupEdge | Function | null | Edge를 초기설정
funcEventAfterRender | Function | null | Graph를 Rendering후에
funcEventClickNode | Function | null | Node를 Click할 때
funcEventDoubleClickNode | Function | null | Node를 Double Click할 때 
funcEventDragNodeOverDistance | Function | null | Node를 일정 거리 Drag할 때
funcForCustomExtendsPanel | Function | null | ExtendsPanel을 설정할 수 있도록 할 수 있다.


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



## funcEventSetupNode
- BOX가 생성될 때 발생합니다.
    *@* *!* *@*
    ```html
    <script>
        var boxman = new BoxMan().ready(function(boxman){
            boxman.newBox({id:'boxA', content:'BOX A'});
            boxman.newBox({id:'boxB', content:'BOX B', start:function(){            
                document.getElementById('tester').innerHTML = 'Do start event!';
            }});
            boxman.newObj({id:'objA', content:'OBJ A'});
        });     
    </script>
    <body> 
        <div id="tester">TEST</div>    
    </body>
    ```
  
    *@* *!* *@*
    ```html
    <script>
        var boxman = new BoxMan().detect();     
    </script>
    <body>
        <div id="tester">TEST</div>
        <div id="boxA" data-box>BOX A</div>
        <div id="boxB" data-box data-event-start="document.getElementById('tester').innerHTML = 'Do start event!';" >BOX B</div>
        <div data-obj>OBJ A</div>    
    </body>
    ```



## funcEventSetupEdge


## funcEventAfterRender


## funcEventClickNode 


## funcEventDoubleClickNode 


## funcEventDragNodeOverDistance


## funcForCustomExtendsPanel 


