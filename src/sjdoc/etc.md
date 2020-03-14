# ETC
Mode 속성으로 `특정효과`를 설정할 수 있습니다.

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|-----
container | Element | null | Canvas를 담을 Container Element지정합니다.,
setDocument | DocumentElement | document | 기본이 아닌 다른 document 객체를 참조하고 싶다면 사용합니다. 
setVis | vis | null | 기본적으로 Global영역의 window에 정의된 vis를 가지고 사용하지만, ES6+ Module환경이거나 특수 한 상황에서는 `visjs network` 를 따로 설정할 필요가 있습니다.
maxDistanceWhenDragNode | Number | null | Node를 Drag할 수 있는 최대 길이
maxChildNodeCount | Number | 5 | 최대연결 노드 수

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



## container
- Test
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            // modeMakeCategoryNode: true,
            modeMakeCategoryLinkEachNode: true,
            modeTintColorByCategory: true,
            modeDrawingCategoryBackgroundBeforeDrawing: true,
            categoryRandomColorList: ['#CCCCCC', '#999999', '#555555', '#333333', '#000000']
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
        
  
  
## maxDistanceWhenDragNode


## maxChildNodeCount
