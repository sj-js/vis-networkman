# Event
`OBJ`가 `이동함에 따라 Event`를 발생시킬 수 있습니다. 

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|-----
funcEventSetupNode | Function | null | Node를 초기설정 (`nodeWhenStart`와 비슷하지만 사용법이 다르며 보다 나중에 추가로 작용한다.)
funcEventHoverNode | Function | null | Node위로 마우스를 올릴 때
funcEventBlurNode | Function | null |  Node위에서 마우스가 벗어날 때
funcEventHoverNodeAndMove | Function | null | Node위로 마우스를 올리거나 그 위에서 움직일 때
funcEventSetupEdge | Function | null | Edge를 초기설정 (`edgeWhenStart`와 비슷하지만 사용법이 다르며 보다 나중에 추가로 작용한다.)
funcEventHoverEdge | Function | null | Edge위에서 마우스를 올릴 때
funcEventBlurEdge | Function | null | Edge위에서 마우스가 벗어날 때
funcEventHoverEdgeAndMove | Function | null | Edge위로 마우스를 올리거나 그 위에서 움직일 때
funcEventClickNode | Function | null | Node를 Click할 때
funcEventDoubleClickNode | Function | null | Node를 Double Click할 때 
funcEventDragNodeOverDistance | Function | null | Node를 일정 거리 Drag할 때
funcEventAfterRender | Function | null | Graph를 Rendering한 후에
funcEventSetupWhenFinishRender | Function | null | 최초 Rendering한 후에 
funcForCustomExtendsPanel | Function | null | ExtendsPanel을 설정할 수 있도록 할 수 있다.

#### ※ 자동적용
- 편의를 위해서 예제에서는 다음 코드가 생략되어 있습니다.
    ```html
    <script src="https://cdn.jsdelivr.net/npm/@sj-js/vis-networkman/vis-network.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@sj-js/vis-networkman/vis-networkman.min.js"></script>
    <script>
         var visnetworkman = new VisNetworkMan();
    </script>
    ```

    *@* *+prefix* *x* *@* 
    ```html
    <script src="../vis-networkman/vis-network.min.js"></script>
    <script src="../vis-networkman/vis-networkman.js"></script>
    <script>
         var visnetworkman = new VisNetworkMan();
    </script>
    ```



## Event - funcEventSetupNode & funcEventSetupEdge
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            funcEventSetupNode: function(node){
                switch (node.group){
                    case 0:
                        node.color = {background:'black', size:50};
                        break;
                    default:
                        node.color = {background:'yellow', size:30};
                        break; 
                }               
            },
            funcEventSetupEdge: function(edge){
                var toNode = edge.toNode;
                edge.width = Math.max(toNode.rate, .1) * 50;
            }
        });
        visnetworkman.renderWithDataList([
            {id:1, label:'A1', group:0, parentId:null, categoryId:'A', categoryName:'Category A'},                       
            {id:2, label:'A2', group:1, parentId:1, categoryId:'A', categoryName:'Category A', rate:1},
            {id:3, label:'A3', group:2, parentId:2, categoryId:'B', categoryName:'Category B', rate:.13},
            {id:4, label:'A4', group:2, parentId:2, categoryId:'A', categoryName:'Category A', rate:.51},
            {id:5, label:'A5', group:2, parentId:2, categoryId:'C', categoryName:'Category C', rate:.86},
            {id:6, label:'A6', group:2, parentId:2, categoryId:'C', categoryName:'Category C', rate:1},
            {id:7, label:'A7', group:2, parentId:2, categoryId:'B', categoryName:'Category B', rate:.92}
        ]);
    </script>
    ```



## Event - hover, move, blur 
- funcEventSetupWhenFinishRender
- funcEventHoverNode
- funcEventHoverNodeAndMove
- funcEventBlurNode
- funcEventHoverEdge
- funcEventHoverEdgeAndMove
- funcEventBlurEdge
- 예)
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            funcEventSetupWhenFinishRender: function(visnetworkman){
                var container = visnetworkman.cachedDataWhenLastUserSetup.container;
                var popman = visnetworkman.customPopman = new PopMan();
                //TODO: 메이비 이거 안씀 ==> 지우기
                popman.add(popman.new({
                    id: 'pop-metadata',
                    exp: '5(300)',
                    modeDark: false,
                    closebyesc: true,
                    closebyclickout: false,
                    target: container,
                    modeAnimation: true,
                    add: function(data){
                        data.element.innerHTML = 'TEST';
                    }
                }));
            },
            funcEventHoverNode: function(node){
            },
            funcEventHoverNodeAndMove: function(node){
            },
            funcEventBlurNode: function(node){
            },
            funcEventHoverEdge: function(edge){
            },
            funcEventHoverEdgeAndMove: function(edge){
            },
            funcEventBlurEdge: function(edge){
            }
        });
        visnetworkman.renderWithDataList([
            {id:1, label:'A1', group:0, parentId:null, categoryId:'A', categoryName:'Category A'},                       
            {id:2, label:'A2', group:1, parentId:1, categoryId:'A', categoryName:'Category A'},
            {id:3, label:'A3', group:2, parentId:2, categoryId:'B', categoryName:'Category B'},
            {id:4, label:'A4', group:2, parentId:2, categoryId:'A', categoryName:'Category A'},
            {id:5, label:'A5', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:6, label:'A6', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:7, label:'A7', group:2, parentId:2, categoryId:'B', categoryName:'Category B'}
        ]);
    </script>
    ```



## Event - funcEventAfterRender
- 예)
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            funcEventAfterRender: function(node){
            }
        });
        visnetworkman.renderWithDataList([
            {id:1, label:'A1', group:0, parentId:null, categoryId:'A', categoryName:'Category A'},                       
            {id:2, label:'A2', group:1, parentId:1, categoryId:'A', categoryName:'Category A'},
            {id:3, label:'A3', group:2, parentId:2, categoryId:'B', categoryName:'Category B'},
            {id:4, label:'A4', group:2, parentId:2, categoryId:'A', categoryName:'Category A'},
            {id:5, label:'A5', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:6, label:'A6', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:7, label:'A7', group:2, parentId:2, categoryId:'B', categoryName:'Category B'}
        ]);
    </script>
    ```



## Event - funcEventClickNode & funcEventDoubleClickNode 
- 예)
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            funcEventClickNode: function(node){
                alert( '[Click] ' + node.label );
            },
            funcEventDoubleClickNode: function(node){
                alert( '[Double Click] ' + node.label );
            }
        });
        visnetworkman.renderWithDataList([
            {id:1, label:'A1', group:0, parentId:null, categoryId:'A', categoryName:'Category A'},                       
            {id:2, label:'A2', group:1, parentId:1, categoryId:'A', categoryName:'Category A'},
            {id:3, label:'A3', group:2, parentId:2, categoryId:'B', categoryName:'Category B'},
            {id:4, label:'A4', group:2, parentId:2, categoryId:'A', categoryName:'Category A'},
            {id:5, label:'A5', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:6, label:'A6', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:7, label:'A7', group:2, parentId:2, categoryId:'B', categoryName:'Category B'}
        ]);
    </script>
    ```
  
  

## Event - funcEventDragNodeOverDistance
- 예)
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            maxDistanceWhenDragNode: 100,
            funcEventDragNodeOverDistance:function(node){
                switch (node.group){
                    case 1: break;
                    case 2: boxman.newObjToPointer({content:'📦', class:'jelly-viewer-result-item', modeRemoveOutOfBox:true, 'data-obj-type':'product'}); break;
                    case 3: break;
                    default: break;
                }
            }
        });
        visnetworkman.renderWithDataList([
            {id:1, label:'A1', group:0, parentId:null, categoryId:'A', categoryName:'Category A'},                       
            {id:2, label:'A2', group:1, parentId:1, categoryId:'A', categoryName:'Category A'},
            {id:3, label:'A3', group:2, parentId:2, categoryId:'B', categoryName:'Category B'},
            {id:4, label:'A4', group:2, parentId:2, categoryId:'A', categoryName:'Category A'},
            {id:5, label:'A5', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:6, label:'A6', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:7, label:'A7', group:2, parentId:2, categoryId:'B', categoryName:'Category B'}
        ]);
    </script>
    ```
  
  
## Event - funcForCustomExtendsPanel 
- 예)
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeExtendsPanel: true,
            funcForCustomExtendsPanel: function(panel, visnetman){
                //Button - 연관도 표시
                var buttonForShowWeight = document.createElement('button');
                visnetman.toggleman.setToggleData('test', buttonForShowWeight, {
                    '연관도O': {
                        funcEventSetupEdge:function(edge){
                            //TODO: Something
                            if (edge.toNode){
                                // edge.arrows = {to: {enabled:true, scaleFactor:0.1}};
                                if (edge.toNode.relevance){
                                    var maxWidth = 40, minWidth = 5;
                                    edge.width = Math.max(Math.min(Math.floor(edge.toNode.relevance * maxWidth), maxWidth), minWidth);
                                    //TEST - Show Relevance
                                    edge.font = {color:'#ee33ff', size:20};
                                    edge.label = '' +edge.toNode.weight+ ' (' +Math.floor(edge.toNode.relevance *100)+ '%)';
                                    //TEST - Highlight Edge with Relevance
                                    edge.color = {opacity: Math.min(edge.toNode.relevance *1.35, 1)};
                                }
                            }
                        }
                    },
                    '연관도X':{}
                });
                panel.appendChild(buttonForShowWeight);
           }
        });
        visnetworkman.renderWithDataList([
            {id:1, label:'A1', group:0, parentId:null, categoryId:'A', categoryName:'Category A'},                       
            {id:2, label:'A2', group:1, parentId:1, categoryId:'A', categoryName:'Category A'},
            {id:3, label:'A3', group:2, parentId:2, categoryId:'B', categoryName:'Category B'},
            {id:4, label:'A4', group:2, parentId:2, categoryId:'A', categoryName:'Category A'},
            {id:5, label:'A5', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:6, label:'A6', group:2, parentId:2, categoryId:'C', categoryName:'Category C'},
            {id:7, label:'A7', group:2, parentId:2, categoryId:'B', categoryName:'Category B'}
        ]);
    </script>
    ```

