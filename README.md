# VIS Network Man

**VIS Network** 를 쉽게 확장하여 사용하기 위해 만들어졌습니다.
     
- `vis-network`
    - **Node**와 **Edge**로 구성된 네트워크와 네트워크를 표시하는 시각화 **JavaScript Library**입니다.
    - docs: https://visjs.github.io/vis-network/docs/network/
    - github: https://github.com/visjs/vis-network
    
- `vis-networkman`
    - **VIS Network**의 Edge와 응용기능을 쉽게 사용하기 위해 만들어졌습니다.
    - docs: https://sj-js.github.io/helppage/dist/sj-js/vis-networkman
    - github: https://github.com/sj-js/vis-networkman
    
      
        
## 0. Index
*@* **order** *@*
```
- VIS Network Man
- Unification
- Categorizing
- Effect
- Extends Panel
- ETC
- Event
- Example
```




## 1. Getting Started

### 1-1. Load Script
- 필요한 `js`파일을 load합니다.
    ```html
    <script src="https://cdn.jsdelivr.net/gh/sj-js/vis-networkman/vis-network.min.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/sj-js/vis-networkman/vis-networkman.min.js"></script>
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
   
### 1-2. Setup vis-network's option
- VIS Network의 Option을 설정합니다.
    ```javascript
    visnetworkman.setup({
        ...
    });
    ```

### 1-3. Setup vis-networkman's option
- VIS NetworkMan의 Option을 설정합니다.
    ```javascript
    visnetworkman.setupExtendsOption({
        ...
    });
    ```

### 1-4. Render
- Data들을 Array로 모아서 호출합니다. (id의 `기준은 Data`)  
    ```javascript
    visnetworkman.renderWithDataList([
        {id:0, group:0, label:"TEST01", parentId:null}
        ...
    ]);
    ```

### 1-5. Quick Tutorial
1. Test with null
    *@* *!* *@*
    ```html
    <body><!-- None --></body>
    <script>        
        var container = visnetworkman.renderWithDataList(null);
        document.body.appendChild(container);
    </script>
    ```
   
2. Test with simple datas
    *@* *!* *@*
    ```html
    <body><!-- None --></body>
    <script>        
        var container = visnetworkman.renderWithDataList([
            {id:1, label:'A1', group:0, parentId:null},                       
            {id:2, label:'A2', group:1, parentId:1},
            {id:3, label:'A3', group:2, parentId:2},
            {id:4, label:'A4', group:2, parentId:2},
            {id:5, label:'A5', group:2, parentId:2}
        ]);
        document.body.appendChild(container);
    </script>
    ```
   
3. Test with test datas
    *@* *!* *@*
    ```html
    <body><!-- None --></body>
    <script>        
        var container = visnetworkman.renderWithDataList( VisNetworkMan.loadTestDataList() );
        document.body.appendChild(container);
    </script>
    ```





## 2. Functions

### 2-1. .setup({ ... })
- `VIS Network`의 Options값을 설정합니다. (참조: https://visjs.github.io/vis-network/docs/network/)
- 가장 기본값으로 적용되며 다른 Event에 의해 변경될 수 있습니다.
    ```javascript
    visnetworkman.setup({
        nodes:{ /** REF: https://visjs.github.io/vis-network/docs/network/nodes.html# **/
            shape:'circle',
        },
        edges:{ /** REF: https://visjs.github.io/vis-network/docs/network/edges.html# **/
            width:5,
            arrows:{from: false, middle: false, to: false}
        },            
    });    
    ```

### 2-2. .setupExtendsOption({ ... })          
- `VIS NetworkMan`의 Options값을 설정합니다.
    ```javascript
    visnetworkman.setupExtendsOption({
        modePointAllSubLink: true,
        modeSelectAllSubLink: true,
        ...
    });    
    ```

### 2-3. .renderWithDataList([ {...}, ... ])
- `Data기준`의 Object Array로 Rendering합니다.
    ```javascript
    var container = visnetworkman.renderWithDataList([
    ]);
    document.body.appendChild(container);
    ```
  
### 2-4 .renderWithNodeDataList([ {...}, ... ])
- `Node기준`의 Object Array로 Rendering합니다.   
    ```javascript
    var container = visnetworkman.renderWithNodeDataList([
    ]);
    document.body.appendChild(container);
    ```  
  
  
## 3. Extends Options
  
### 3-1. Unification
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|------
modeCloneNodeWhenDuplicateLink | Boolean | true | 하나의 부모노드만 갖도록 자동으로 Clone합니다.  
modeUniqueDataInSameGroup | Boolean | false | 같은 그룹안에 같은 Data가 존재할 경우 하나로 통합합니다.
modeUniqueData | Boolean | false | 같은 Data가 여러개 존재할 경우 하나로 통합합니다.
modeOrderByGroup | Boolean | true | Group순으로 노드간 연결합니다.
orderList | Array | null | Group간 연결 순서
modePruneNodeWithoutEdge | Boolean | true | Edge정보가 없는 Node를 표시하지 않습니다.
modePruneNodeNotToRootGroup | Boolean | true | Root Node까지

### 3-2. Effect 
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

### 3-3. ExtendsPanel 
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|------
modeExtendsPanel | Boolean | false | ExtendsPanel의 사용여부
modeExtendsPanelAutoHide | Boolean | false | ExtendsPanel을 자동으로 숨기고 마우스커서를 올리면 보입니다.
modeExtendsPanelSaveToLocalStorage | Boolean | false | ExtendsPanel의 Toggle정보를 저장할지 여부
saveKey | String | ... | ExtendsPanel의 Toggle 정보를 저장할 LocalStorage의 Key를 지정합니다. 기본값: `/toggleman/visnetworkman/`
extendsPanelToggleDefaultIndexMap | Object | ... | ExtendsPanel을 사용시 ToggleButton의 기본값을 설정합니다. 기본값: `{"direction":0,"directionMethod":0,"duplication":0,"unification":0,"edgeLimit":4}` 
extendsPanelShowItemList | Array | null | ExampleForAll) null   //- ExampleForNothing) []   //- ExampleForSelective) ['direction', 'edgeLimit']
extendsPanelHideItemList | Array | null | ExampleForNothing) null or []   //- ExampleForSelective) ['direction', 'edgeLimit']

### 3-4. ETC
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|-----
container | Element | null | Canvas를 담을 Container Element지정합니다.,
maxDistanceWhenDragNode | Number | null | Node를 Drag할 수 있는 최대 길이
maxChildNodeCount | Number | 5 | 최대연결 노드 수

### 3-5. Events
옵션명 | 형식 | 기본값 | 설명
-------|------|--------|-----
funcEventSetupNode | Function | null | Node를 초기설정
funcEventSetupEdge | Function | null | Edge를 초기설정
funcEventAfterRender | Function | null | Graph를 Rendering후에
funcEventClickNode | Function | null | Node를 Click할 때
funcEventDoubleClickNode | Function | null | Node를 Double Click할 때 
funcEventDragNodeOverDistance | Function | null | Node를 일정 거리 Drag할 때
funcForCustomExtendsPanel | Function | null | ExtendsPanel을 설정할 수 있도록 할 수 있다.


  