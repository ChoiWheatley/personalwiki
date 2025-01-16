---
{"dg-publish":true,"permalink":"/docs/Multiple Inheritance and mro builtin function/","title":"Multiple Inheritance and mro builtin function"}
---


<https://www.geeksforgeeks.org/method-resolution-order-in-python-inheritance/>

그거아시져, 마름모꼴로 생긴 상속관계에서 최하단의 클래스가 어느 부모의 attr를 따라야 하는지 충돌이 발생하는 경우 아주 곤란해진다고.  

<style> .container {font-family: sans-serif; text-align: center;} .button-wrapper button {z-index: 1;height: 40px; width: 100px; margin: 10px;padding: 5px;} .excalidraw .App-menu_top .buttonList { display: flex;} .excalidraw-wrapper { height: 800px; margin: 50px; position: relative;} :root[dir="ltr"] .excalidraw .layer-ui__wrapper .zen-mode-transition.App-menu_bottom--transition-left {transform: none;} </style><script src="https://cdn.jsdelivr.net/npm/react@17/umd/react.production.min.js"></script><script src="https://cdn.jsdelivr.net/npm/react-dom@17/umd/react-dom.production.min.js"></script><script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@excalidraw/excalidraw@0/dist/excalidraw.production.min.js"></script><div id="다중상속excalidraw.md1"></div><script>(function(){const InitialData={"type":"excalidraw","version":2,"source":"https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.7.4","elements":[{"id":"ia8ULXPdBe-L3LIpegBBA","type":"ellipse","x":-19.75,"y":-232.546875,"width":57,"height":85,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":{"type":2},"seed":1765544538,"version":60,"versionNonce":16429856,"isDeleted":false,"boundElements":[{"type":"text","id":"gO1srMpR"},{"id":"L1cXh3IdnOsIo8ckqLvK8","type":"arrow"},{"id":"Y78oLvIEEhuSsFcPN_gj7","type":"arrow"}],"updated":1736753028105,"link":null,"locked":false,"index":"a0","frameId":null},{"id":"gO1srMpR","type":"text","x":2.0374591775896445,"y":-215.09891320042829,"width":13.1199951171875,"height":50,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":null,"seed":1362485722,"version":8,"versionNonce":1903644448,"isDeleted":false,"boundElements":[],"updated":1736753028105,"link":null,"locked":false,"text":"\nA","rawText":"\nA","fontSize":20,"fontFamily":1,"textAlign":"center","verticalAlign":"middle","baseline":18,"containerId":"ia8ULXPdBe-L3LIpegBBA","originalText":"\nA","lineHeight":1.25,"autoResize":true,"index":"a1","frameId":null},{"id":"1eXDsIKmQXKKx_D0zgXD6","type":"ellipse","x":-131.75,"y":-129.546875,"width":57,"height":57,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":{"type":2},"seed":359233434,"version":96,"versionNonce":1232521952,"isDeleted":false,"boundElements":[{"type":"text","id":"RMCBSlyl"},{"id":"L1cXh3IdnOsIo8ckqLvK8","type":"arrow"},{"id":"xSvqQzuCihecTacA52KGn","type":"arrow"}],"updated":1736753027948,"link":null,"locked":false,"index":"a2","frameId":null},{"id":"RMCBSlyl","type":"text","x":-110.67253990688302,"y":-113.69941826381661,"width":14.539993286132812,"height":25,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":null,"seed":1298378182,"version":5,"versionNonce":1180160800,"isDeleted":false,"boundElements":[],"updated":1736753027948,"link":null,"locked":false,"text":"B","rawText":"B","fontSize":20,"fontFamily":1,"textAlign":"center","verticalAlign":"middle","baseline":18,"containerId":"1eXDsIKmQXKKx_D0zgXD6","originalText":"B","lineHeight":1.25,"autoResize":true,"index":"a3","frameId":null},{"id":"y78DPoUkgIuJcm_tSprcS","type":"ellipse","x":86.25,"y":-127.546875,"width":57,"height":57,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":{"type":2},"seed":635718406,"version":170,"versionNonce":1243246304,"isDeleted":false,"boundElements":[{"type":"text","id":"VFZxSbvk"},{"id":"Y78oLvIEEhuSsFcPN_gj7","type":"arrow"},{"id":"8Iug4B4mzFwQRHs4-GR_6","type":"arrow"}],"updated":1736753027948,"link":null,"locked":false,"index":"a4","frameId":null},{"id":"VFZxSbvk","type":"text","x":108.15746192417167,"y":-111.69941826381661,"width":12.879989624023438,"height":25,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":null,"seed":808642522,"version":5,"versionNonce":1311797024,"isDeleted":false,"boundElements":[],"updated":1736753027948,"link":null,"locked":false,"text":"C","rawText":"C","fontSize":20,"fontFamily":1,"textAlign":"center","verticalAlign":"middle","baseline":18,"containerId":"y78DPoUkgIuJcm_tSprcS","originalText":"C","lineHeight":1.25,"autoResize":true,"index":"a5","frameId":null},{"id":"TA3ZlakutVZozjoTH_Zea","type":"ellipse","x":-19.75,"y":-18.546875,"width":57,"height":57,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":{"type":2},"seed":1330881946,"version":107,"versionNonce":1051300576,"isDeleted":false,"boundElements":[{"type":"text","id":"I7onBITJ"},{"id":"xSvqQzuCihecTacA52KGn","type":"arrow"},{"id":"8Iug4B4mzFwQRHs4-GR_6","type":"arrow"}],"updated":1736753027948,"link":null,"locked":false,"index":"a6","frameId":null},{"id":"I7onBITJ","type":"text","x":0.7974613138201132,"y":-2.6994182638166055,"width":15.599990844726562,"height":25,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":null,"seed":510396550,"version":5,"versionNonce":144018208,"isDeleted":false,"boundElements":[],"updated":1736753027948,"link":null,"locked":false,"text":"D","rawText":"D","fontSize":20,"fontFamily":1,"textAlign":"center","verticalAlign":"middle","baseline":18,"containerId":"TA3ZlakutVZozjoTH_Zea","originalText":"D","lineHeight":1.25,"autoResize":true,"index":"a7","frameId":null},{"id":"L1cXh3IdnOsIo8ckqLvK8","type":"arrow","x":-87.75,"y":-126.546875,"width":75,"height":56,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":{"type":2},"seed":1869499974,"version":25,"versionNonce":1610640160,"isDeleted":false,"boundElements":[],"updated":1736753028105,"link":null,"locked":false,"points":[[0,0],[75,-56]],"lastCommittedPoint":null,"startBinding":{"elementId":"1eXDsIKmQXKKx_D0zgXD6","focus":-0.3915495634901324,"gap":1.3412466227535482},"endBinding":{"elementId":"ia8ULXPdBe-L3LIpegBBA","focus":-0.15313355355262717,"gap":1.905591591021544},"startArrowhead":null,"endArrowhead":"arrow","index":"a8","frameId":null},{"id":"Y78oLvIEEhuSsFcPN_gj7","type":"arrow","x":86.25,"y":-125.546875,"width":52,"height":54,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":{"type":2},"seed":2074465606,"version":52,"versionNonce":318251808,"isDeleted":false,"boundElements":[],"updated":1736753028105,"link":null,"locked":false,"points":[[0,0],[-52,-54]],"lastCommittedPoint":null,"startBinding":{"elementId":"y78DPoUkgIuJcm_tSprcS","focus":-0.075355136044268,"gap":10.416577444580092},"endBinding":{"elementId":"ia8ULXPdBe-L3LIpegBBA","focus":-0.04820856529540127,"gap":6.862409420173847},"startArrowhead":null,"endArrowhead":"arrow","index":"a9","frameId":null},{"id":"xSvqQzuCihecTacA52KGn","type":"arrow","x":-20.749999999999993,"y":-9.546874999999993,"width":61.00000000000001,"height":66,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":{"type":2},"seed":1386814874,"version":24,"versionNonce":1164040992,"isDeleted":false,"boundElements":[],"updated":1736753028105,"link":null,"locked":false,"points":[[0,0],[-61.00000000000001,-66]],"lastCommittedPoint":null,"startBinding":{"elementId":"TA3ZlakutVZozjoTH_Zea","focus":-0.2957418162704787,"gap":6.86240942017384},"endBinding":{"elementId":"1eXDsIKmQXKKx_D0zgXD6","focus":0.0532920896645813,"gap":4.8541601603158355},"startArrowhead":null,"endArrowhead":"arrow","index":"aA","frameId":null},{"id":"8Iug4B4mzFwQRHs4-GR_6","type":"arrow","x":43.25,"y":-5.546875,"width":50,"height":65,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"roundness":{"type":2},"seed":1267732678,"version":22,"versionNonce":1857648416,"isDeleted":false,"boundElements":[],"updated":1736753028106,"link":null,"locked":false,"points":[[0,0],[50,-65]],"lastCommittedPoint":null,"startBinding":{"elementId":"TA3ZlakutVZozjoTH_Zea","focus":0.6278951168750342,"gap":9.321951298154882},"endBinding":{"elementId":"y78DPoUkgIuJcm_tSprcS","focus":-0.011766348016397574,"gap":7.200140055747681},"startArrowhead":null,"endArrowhead":"arrow","index":"aB","frameId":null}],"appState":{"theme":"light","viewBackgroundColor":"#ffffff","currentItemStrokeColor":"#000000","currentItemBackgroundColor":"transparent","currentItemFillStyle":"hachure","currentItemStrokeWidth":1,"currentItemStrokeStyle":"solid","currentItemRoughness":1,"currentItemOpacity":100,"currentItemFontFamily":1,"currentItemFontSize":20,"currentItemTextAlign":"left","currentItemStartArrowhead":null,"currentItemEndArrowhead":"arrow","currentItemArrowType":"round","scrollX":440.5,"scrollY":385.296875,"zoom":{"value":2},"currentItemRoundness":"round","gridSize":20,"gridStep":5,"gridModeEnabled":false,"gridColor":{"Bold":"rgba(217, 217, 217, 0.5)","Regular":"rgba(230, 230, 230, 0.5)"},"colorPalette":{},"currentStrokeOptions":null,"frameRendering":{"enabled":true,"clip":true,"name":true,"outline":true},"objectsSnapModeEnabled":false,"activeTool":{"type":"selection","customType":null,"locked":false,"lastActiveTool":null}},"files":{}};InitialData.scrollToContent=true;App=()=>{const e=React.useRef(null),t=React.useRef(null),[n,i]=React.useState({width:void 0,height:void 0});return React.useEffect(()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height});const e=()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height})};return window.addEventListener("resize",e),()=>window.removeEventListener("resize",e)},[t]),React.createElement(React.Fragment,null,React.createElement("div",{className:"excalidraw-wrapper",ref:t},React.createElement(ExcalidrawLib.Excalidraw,{ref:e,width:n.width,height:n.height,initialData:InitialData,viewModeEnabled:!0,zenModeEnabled:!0,gridModeEnabled:!1})))},excalidrawWrapper=document.getElementById("다중상속excalidraw.md1");ReactDOM.render(React.createElement(App),excalidrawWrapper);})();</script>

하지만 파이썬에서는 아주 이상한 방식으로 다중상속 문제점을 해결했고, (좋은 건지는 모르겠지만) 다중상속이 허용된다. 바로 MRO (Method Resolution Order)에 근거한 원칙에 의해 다중상속이 들어가 있더라도 메서드 이름을 찾아가는 데 가장 가까운 관계의 클래스 우선 탐색한다.

`mro`는 `object`의 메서드로, 출력해보면 나의 모든 조상을 리스트의 형태로 출력한다. 그래서 attr 충돌 발생시 `mro`의 왼쪽에서부터 가장 가까운 클래스의 attr를 따라갈 수 있다...