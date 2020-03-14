# vis-networkman

- **vis-network**를 확장하여 특정 기능을 쉽게 사용하기 위해 만들어졌습니다. 
- **vis-network** 버전 `6.4.7`을 기초로 만들어졌습니다.
- Data를 기준으로 자동으로      
- `vis-network`
    - **Node**와 **Edge**로 구성된 네트워크와 네트워크를 표시하는 시각화 **JavaScript Library**입니다.
    - Document: https://visjs.github.io/vis-network/docs/network/
    - Source: https://github.com/visjs/vis-network
    
- `vis-networkman`
    - **VIS Network**의 Edge와 응용기능을 쉽게 사용하기 위해 만들어졌습니다.
    - ✨ Document: https://sj-js.github.io/helppage/dist/sj-js/vis-networkman
    - ✨ Source: https://github.com/sj-js/vis-networkman
    
      

## 1. Getting Started
0. Load
    - Browser
        ```html
        <script src="https://cdn.jsdelivr.net/gh/sj-js/vis-networkman/vis-network.min.js"></script>
        <script src="https://cdn.jsdelivr.net/gh/sj-js/vis-networkman/vis-networkman.min.js"></script>
        <script>
             var visnetworkman = new VisNetworkMan();
        </script>
        ```  
    - ES6+
        ```bash
        npm install @sj-js/vis-networkman
        ```
        ```js
        require('@sj-js/vis-networkman/dist/css/vis-networkman.css');
        const VisNetworkMan = require('@sj-js/vis-networkman');
        const visnetworkman = new VisNetworkMan();
        ```       
       

1. Simple Example
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


  