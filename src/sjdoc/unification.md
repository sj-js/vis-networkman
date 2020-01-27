# Unification
Data를 통해 여러 방식으로 Node와 Edge를 생성할 수 있습니다.

#### ※ 표
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|------
modeCloneNodeWhenDuplicateLink | Boolean | false | 하나의 부모노드만 갖도록 자동으로 Clone합니다.  
modeUniqueDataInSameGroup | Boolean | false | 같은 그룹안에 같은 Data가 존재할 경우 하나로 통합합니다.
modeUniqueData | Boolean | false | 같은 Data가 여러개 존재할 경우 하나로 통합합니다.
modeOrderByGroup | Boolean | true | Group순으로 노드간 연결합니다.
orderList | Array | null | Group간 연결 순서
modePruneNodeWithoutEdge | Boolean | true | Edge정보가 없는 Node를 표시하지 않습니다.
modePruneNodeNotToRootGroup | Boolean | true | Root Node까지

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



## modeCloneNodeWhenDuplicateLink
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeCloneNodeWhenDuplicateLink: true,
        });
        visnetworkman.renderWithDataList([
          //Group0
          {id:101, label:'A1', group:0, parentId:null, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group1
          {id:201, label:'B1', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:203, label:'B3', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},          
          //Group2
          {id:301, label:'C1', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:202, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:303, label:'C3', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:304, label:'C4', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          //Group3
          {id:401, label:'D1', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:402, label:'D2', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:403, label:'D3', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:404, label:'D4', group:3, parentId:303, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:405, label:'D5', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:406, label:'D6', group:3, parentId:null, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:201, label:'B1', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group4
          {id:501, label:'E1', group:4, parentId:null, categoryId:'ㄹ', categoryName:'Category ㄹ'},
          {id:502, label:'E1', group:4, parentId:406, categoryId:'ㄹ', categoryName:'Category ㄹ'}
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
            modeCloneNodeWhenDuplicateLink: false,
        });
        visnetworkman.renderWithDataList([
          //Group0
          {id:101, label:'A1', group:0, parentId:null, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group1
          {id:201, label:'B1', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:203, label:'B3', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},          
          //Group2
          {id:301, label:'C1', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:202, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:303, label:'C3', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:304, label:'C4', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          //Group3
          {id:401, label:'D1', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:402, label:'D2', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:403, label:'D3', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:404, label:'D4', group:3, parentId:303, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:405, label:'D5', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:406, label:'D6', group:3, parentId:null, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:201, label:'B1', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group4
          {id:501, label:'E1', group:4, parentId:null, categoryId:'ㄹ', categoryName:'Category ㄹ'},
          {id:502, label:'E1', group:4, parentId:406, categoryId:'ㄹ', categoryName:'Category ㄹ'}
        ]);
    </script>
    ```
  
    
  
## modeUniqueDataInSameGroup
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeUniqueDataInSameGroup: true,
        });
        visnetworkman.renderWithDataList([
          //Group0
          {id:101, label:'A1', group:0, parentId:null, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group1
          {id:201, label:'B1', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:203, label:'B3', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},          
          //Group2
          {id:301, label:'C1', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:202, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:303, label:'C3', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:304, label:'C4', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          //Group3
          {id:401, label:'D1', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:402, label:'D2', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:403, label:'D3', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:404, label:'D4', group:3, parentId:303, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:405, label:'D5', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:406, label:'D6', group:3, parentId:null, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:201, label:'B1', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group4
          {id:501, label:'E1', group:4, parentId:null, categoryId:'ㄹ', categoryName:'Category ㄹ'},
          {id:502, label:'E1', group:4, parentId:406, categoryId:'ㄹ', categoryName:'Category ㄹ'}
        ]);
    </script>
    ```


## modeUniqueData
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeUniqueData: true,
        });
        visnetworkman.renderWithDataList([
          //Group0
          {id:101, label:'A1', group:0, parentId:null, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group1
          {id:201, label:'B1', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:203, label:'B3', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},          
          //Group2
          {id:301, label:'C1', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:202, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:303, label:'C3', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:304, label:'C4', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          //Group3
          {id:401, label:'D1', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:402, label:'D2', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:403, label:'D3', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:404, label:'D4', group:3, parentId:303, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:405, label:'D5', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:406, label:'D6', group:3, parentId:null, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:201, label:'B1', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group4
          {id:501, label:'E1', group:4, parentId:null, categoryId:'ㄹ', categoryName:'Category ㄹ'},
          {id:502, label:'E1', group:4, parentId:406, categoryId:'ㄹ', categoryName:'Category ㄹ'}
        ]);
    </script>
    ```
  
  
  
## modeOrderByGroup & orderList
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modeOrderByGroup: false,
            orderList: [0,1,2],
            // modePruneNodeWithoutEdge: true,
            // modePruneNodeNotToRootGroup: true
        });
        visnetworkman.renderWithDataList([
          //Group0
          {id:101, label:'A1', group:0, parentId:null, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group1
          {id:201, label:'B1', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:203, label:'B3', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},          
          //Group2
          {id:301, label:'C1', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:202, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:303, label:'C3', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:304, label:'C4', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          //Group3
          {id:401, label:'D1', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:402, label:'D2', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:403, label:'D3', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:404, label:'D4', group:3, parentId:303, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:405, label:'D5', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:406, label:'D6', group:3, parentId:null, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:201, label:'B1', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group4
          {id:501, label:'E1', group:4, parentId:null, categoryId:'ㄹ', categoryName:'Category ㄹ'},
          {id:502, label:'E1', group:4, parentId:406, categoryId:'ㄹ', categoryName:'Category ㄹ'}
        ]);
    </script>
    ```
  


## modePruneNodeWithoutEdge & modePruneNodeNotToRootGroup
- 카테고리 정보를 통해 카테고리Node를 자동으로 생성합니다.
    *@* *!* *@*
    ```html
    <body><div id='test-container'></div></body>
    <script>
        visnetworkman.setupExtendsOption({
            container: document.getElementById('test-container'),
            modePruneNodeWithoutEdge: true,
            modePruneNodeNotToRootGroup: true,
        });
        visnetworkman.renderWithDataList([
          //Group0
          {id:101, label:'A1', group:0, parentId:null, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group1
          {id:201, label:'B1', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:203, label:'B3', group:1, parentId:101, categoryId:'ㄱ', categoryName:'Category ㄱ'},          
          //Group2
          {id:301, label:'C1', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:201, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:302, label:'C2', group:2, parentId:202, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:303, label:'C3', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:304, label:'C4', group:2, parentId:201, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          //Group3
          {id:401, label:'D1', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:402, label:'D2', group:3, parentId:302, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:403, label:'D3', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:404, label:'D4', group:3, parentId:303, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:405, label:'D5', group:3, parentId:302, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:406, label:'D6', group:3, parentId:null, categoryId:'ㄷ', categoryName:'Category ㄷ'},
          {id:201, label:'B1', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          {id:202, label:'B2', group:3, parentId:304, categoryId:'ㄱ', categoryName:'Category ㄱ'},
          //Group4
          {id:501, label:'E1', group:4, parentId:null, categoryId:'ㄹ', categoryName:'Category ㄹ'},
          {id:502, label:'E1', group:4, parentId:406, categoryId:'ㄹ', categoryName:'Category ㄹ'}
        ]);
    </script>
    ```
  