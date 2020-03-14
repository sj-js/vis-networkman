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



## modeExtendsPanel & modeExtendsPanelAutoHide
- Test 
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeExtendsPanel: true,
            modeExtendsPanelAutoHide: true   //Hover over it to see it.
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
  


## modeExtendsPanelSaveToLocalStorage
- Test
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeExtendsPanel: true,
            // saveKey: 'my_save_key',
            modeExtendsPanelSaveToLocalStorage: true
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

## extendsPanelToggleDefaultIndexMap
- Test
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeExtendsPanel: true,
            extendsPanelToggleDefaultIndexMap:{
                'direction':0,
                'directionMethod':0,
                'duplication':1,
                'unification':2,
                'edgeLimit':6,
            },
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



## extendsPanelShowItemList & extendsPanelHideItemList
- Test
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeExtendsPanel: true,
            extendsPanelShowItemList: ['direction', 'edgeLimit'],
            // extendsPanelHideItemList: ['direction', 'duplication']
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



## .setupExtendsPanel()
- Test
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeExtendsPanel: true
        });
        visnetworkman.setupExtendsPanel(function(panel, visnetman){
            //Button - 연관도 표시
            var buttonForShowWeight = document.createElement('button');
            visnetman.toggleman.setToggleData('test', buttonForShowWeight, {
                '연관도O': {
                    funcEventSetupEdge:function(edge){
                        //TODO: Something
                        if (edge.toNode){
                            // edge.arrows = {to: {enabled:true, scaleFactor:0.1}};
                            if (edge.toNode.relevance){
                                var maxWidth = 20, minWidth = 5;
                                edge.width = Math.max(Math.min(Math.floor(edge.toNode.relevance * maxWidth), maxWidth), minWidth);
                                //TEST - Show Relevance
                                edge.font = {color:'#ee33ff', size:10};
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
