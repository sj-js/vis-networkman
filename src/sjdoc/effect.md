# Effect
Data를 통해 여러 방식으로 Node와 Edge를 생성할 수 있습니다.

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|-----
modeLoading | Boolean | true | Loading을 표시합니다.
modePointAllSubLink | Boolean | false | Node를 Pointing시 Edge로 Root Node까지 연결된 부분을 Event작동시킬지 여부
modeSelectAllSubLink | Boolean | false | Node를 Select시 Edge로 Root Node까지 연결된 부분을 Event작동시킬지 여부
nodeWhenStart | Object or Function | null | Node 초기설정 
edgeWhenStart | Object or Function | null | Edge 초기설정
nodeWhenPoint | Object or Function | null | Node에 마우스를 올렸을 때 설정
edgeWhenPoint | Object or Function | null | Edge에 마우스를 올렸을 때 설정
nodeWhenSelect | Object or Function | null | Node를 선택했을 때 설정
edgeWhenSelect | Object or Function | null | Edge를 선택했을 때 설정

#### ※ 자동적용
- 편의를 위해서 예제에서는 다음 코드가 생략되어 있습니다.
    ```html
    <script src="https://cdn.jsdelivr.net/npm/@sj-js/vis-networkman/vis-network.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@sj-js/vis-networkman/vis-networkman.min.js"></script>
    <link rel="https://cdn.jsdelivr.net/npm/@sj-js/vis-networkman/vis-networkman.min.css" />
    <script>
         var visnetworkman = new VisNetworkMan();
    </script>
    ```  

    *@* *+prefix* *x* *@* 
    ```html
    <script src="../vis-networkman/vis-network.min.js"></script>
    <script src="../vis-networkman/vis-networkman.js"></script>
    <link rel=stylesheet href="../vis-networkman/vis-networkman.css">
    <script>
         var visnetworkman = new VisNetworkMan();
    </script>
    ```



## modeLoading
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeLoading: true
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
  
  
  
## Event - Start, Point, Select
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeLoading: true,
            modePointAllSubLink: true,    //노드위에 마우스 포인터를 올렸을 때 `nodeWhenPoint`와 `edgeWhenPoint` 효과작동 여부 
            modeSelectAllSubLink: true,   //노드를 클릭했을 때 `nodeWhenSelect`와 `edgeWhenSelect` 효과작동 여부
            nodeWhenStart: {size: 40, borderWidth: 5, color:{background:'green', border:'white'}, font:{size:0}},
            nodeWhenPoint: {color:{border:'red', background:'red'}, font:{size:20}},
            nodeWhenSelect: {color: {background:'pink', border:'pink'}, font:{size:40}},
            edgeWhenStart: {color: {color:'green'}, font:{size:0}},
            edgeWhenPoint: {color: {color:'red', opacity:1}, font:{size:15}},
            edgeWhenSelect: {color: {color:'pink', opacity:1}, font:{size:15}}
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
  
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeLoading: true,
            modePointAllSubLink: true,    //노드위에 마우스 포인터를 올렸을 때 `nodeWhenPoint`와 `edgeWhenPoint` 효과작동 여부 
            modeSelectAllSubLink: true,   //노드를 클릭했을 때 `nodeWhenSelect`와 `edgeWhenSelect` 효과작동 여부
            nodeWhenStart: function(node){    //Function을 이용하여 다이나믹하게 설게 할 수 있습니다.
                return {
                    size: (node.group == 0) ? 50 : (node.group == 1) ? 40 : (node.group == 2) ? 30 : (node.group == 3) ? 20 : 10,
                    borderWidth: 2,
                    color: {background:'red', border:'white'},
                    font: {size:0}
                };
            },
            nodeWhenPoint: function(node){
                return {
                    size: node.size +20,
                    font: {size:node.font.size +35},
                };
            },
            nodeWhenSelect: {color: {background:'pink', border:'pink'}, font:{size:40}},
            edgeWhenStart: {color: {color:'green'}, font:{size:0}},
            edgeWhenPoint: {color: {color:'red', opacity:1}, font:{size:15}},
            edgeWhenSelect: {color: {color:'pink', opacity:1}, font:{size:15}}
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
  
  
  
  