# Categorizing
Data를 통해 여러 방식으로 Node와 Edge를 생성할 수 있습니다.

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|------
modeMakeCategoryNode | Boolean | false | Category Node를 생성하고 동일 CategoryID의 Node에 Edge를 연결합니다.  
modeMakeCategoryLinkEachNode | Boolean | false | 같은 CategoryID를 갖는 Node끼리 Edge를 연결합니다.
modeTintColorByCategory | Boolean | false | Category별로 정해진 색상으로 Node에 색상을 입힙니다.
tintCondition | function | null | tint 대상Node 조건을 정의합니다.  
modeDrawingCategoryBackgroundBeforeDrawing | Boolean | false | CategoryID별 정해진 색상으로 Node의 뒤에 커다른 원으로 배경을 칠합니다.
categoryIdAndColorMap | Object | null | Category별로 구분하기 위한 노드ID별 색상 Object
categoryRandomColorList | Array | ... | Category별로 구분하기 위한 노드의 색상 목록... `['red','orange','yellow','green','blue','indigo','violet','grey','pink','skyblue']`
categoryIdField | String | categoryId | Category Node를 생성하기 위한 Category ID값을 갖는 Node데이터의 필드명
categoryLabelFiled | String | categoryName | Category Node의 Label값을 갖는 Node데이터의 필드명 

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



## modeMakeCategoryNode  
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeMakeCategoryNode: true
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
        
        
        
## modeMakeCategoryLinkEachNode
- 같은 카테고리 정보의 Node끼리 Edge로 연결합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            // modeMakeCategoryNode: true,
            modeMakeCategoryLinkEachNode: true
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



## modeTintColorByCategory
- 지정된 카테고리의 색으로 변경합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            // modeMakeCategoryNode: true,
            modeMakeCategoryLinkEachNode: true,
            modeTintColorByCategory: true
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



## modeDrawingCategoryBackgroundBeforeDrawing
- 카테고리 Node의 배경에 Canvas 작업을 합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            // modeMakeCategoryNode: true,
            modeMakeCategoryLinkEachNode: true,
            modeTintColorByCategory: true,
            modeDrawingCategoryBackgroundBeforeDrawing: true
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



## categoryIdAndColorMap
- 카테고리별로 색을 지정합니다.
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
            categoryIdAndColorMap:{'A':'#CCCCCC', 'B':'#999999', 'C':'#555555'}
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
  
  
  
## categoryRandomColorList
- 카테고리별로 임의로 색을 입힙니다.
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
  
  
  
## categoryIdField & categoryLabelFiled
- 카테고리ID와 카테고리Label에 대한 속성명을 변경합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeMakeCategoryNode: true,
            modeMakeCategoryLinkEachNode: true,
            modeTintColorByCategory: true,
            modeDrawingCategoryBackgroundBeforeDrawing: true,
            categoryIdField: 'catId',
            categoryLabelField: 'catName'
        });
        visnetworkman.renderWithDataList([
            {id:1, label:'A1', group:0, parentId:null, catId:'A', catName:'Category A'},                       
            {id:2, label:'A2', group:1, parentId:1, catId:'A', catName:'Category A'},
            {id:3, label:'A3', group:2, parentId:2, catId:'B', catName:'Category B'},
            {id:4, label:'A4', group:2, parentId:2, catId:'A', catName:'Category A'},
            {id:5, label:'A5', group:2, parentId:2, catId:'C', catName:'Category C'},
            {id:6, label:'A6', group:2, parentId:2, catId:'C', catName:'Category C'},
            {id:7, label:'A7', group:2, parentId:2, catId:'B', catName:'Category B'}
        ]);
    </script>
    ```
  
  