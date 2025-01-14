---
{"excalidraw-plugin":"parsed","tags":["excalidraw"],"dg-publish":true,"permalink":"/docs/assets/argument-passing.excalidraw/","dgPassFrontmatter":true}
---
<style> .container {font-family: sans-serif; text-align: center;} .button-wrapper button {z-index: 1;height: 40px; width: 100px; margin: 10px;padding: 5px;} .excalidraw .App-menu_top .buttonList { display: flex;} .excalidraw-wrapper { height: 800px; margin: 50px; position: relative;} :root[dir="ltr"] .excalidraw .layer-ui__wrapper .zen-mode-transition.App-menu_bottom--transition-left {transform: none;} </style><script src="https://cdn.jsdelivr.net/npm/react@17/umd/react.production.min.js"></script><script src="https://cdn.jsdelivr.net/npm/react-dom@17/umd/react-dom.production.min.js"></script><script type="text/javascript" src="https://cdn.jsdelivr.net/npm/@excalidraw/excalidraw@0/dist/excalidraw.production.min.js"></script><div id="argument-passingexcalidraw.md"></div><script>(function(){const InitialData={"type":"excalidraw","version":2,"source":"https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.7.4","elements":[{"type":"rectangle","version":120,"versionNonce":2089628916,"isDeleted":false,"id":"vY3s0Yoa0ASziw2getBYL","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":2,"opacity":60,"angle":0,"x":-417.5079952478409,"y":-60.76210021972656,"strokeColor":"transparent","backgroundColor":"#b2f2bb","width":1058.5003967285156,"height":115.55221557617188,"seed":1713998384,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"index":"a0"},{"type":"rectangle","version":88,"versionNonce":1170457676,"isDeleted":false,"id":"WVsu9X_bCMHTDRQ4dK7u9","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":2,"opacity":60,"angle":0,"x":-417.5079952478409,"y":-246.73088073730472,"strokeColor":"transparent","backgroundColor":"#ffc9c9","width":1058.5003967285156,"height":170.00561523437503,"seed":2068630736,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"index":"a1"},{"type":"text","version":77,"versionNonce":1015182964,"isDeleted":false,"id":"Y9B0CUsM","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-390.7998958826065,"y":-242.8039093017578,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":215.9999237060547,"height":45,"seed":276107472,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"fontSize":36,"fontFamily":1,"text":"main thread:","rawText":"main thread:","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"main thread:","lineHeight":1.25,"baseline":32,"autoResize":true,"index":"a2"},{"type":"text","version":16,"versionNonce":467491532,"isDeleted":false,"id":"Qwb67qny","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-393.0414425134659,"y":-177.06480407714844,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":46.875,"height":24,"seed":926578384,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"main","rawText":"main","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"main","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"a3"},{"type":"text","version":62,"versionNonce":525567988,"isDeleted":false,"id":"xtWBYooG","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-241.9983822107315,"y":-178.38169860839844,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":128.90625,"height":24,"seed":1818434768,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"run_actions","rawText":"run_actions","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"run_actions","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"a4"},{"type":"text","version":64,"versionNonce":1468014924,"isDeleted":false,"id":"NWx1okts","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":0.5399173498153687,"y":-178.69105529785156,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":93.9453125,"height":24,"seed":25625296,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"run_task","rawText":"run_task","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"run_task","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"a5"},{"type":"text","version":112,"versionNonce":2030463348,"isDeleted":false,"id":"KDLWUP0k","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":168.39111363887787,"y":-178.69105529785156,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":234.375,"height":24,"seed":1430137040,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"process_create_initd","rawText":"process_create_initd","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"process_create_initd","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"a6"},{"type":"text","version":169,"versionNonce":1342576588,"isDeleted":false,"id":"nqn2xr0U","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":459.0144656896591,"y":-178.69105529785156,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":152.34375,"height":24,"seed":857771728,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"RDJNar61WMOt336esRU6-","type":"arrow"}],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"thread_create","rawText":"thread_create","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"thread_create","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"a7"},{"type":"text","version":200,"versionNonce":752950004,"isDeleted":false,"id":"up6uGoQs","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":459.0144656896591,"y":-110.71711730957031,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":140.8984375,"height":24,"seed":868627664,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"process_wait","rawText":"process_wait","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"process_wait","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"a8"},{"type":"arrow","version":81,"versionNonce":1636384332,"isDeleted":false,"id":"BCaWMT6ZgLtO8w55zsY5S","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":-336.38223230838776,"y":-166.75987243652344,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":86.69232177734375,"height":0,"seed":482810576,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"focus":-0.14125569661458334,"gap":9.784210205078125,"elementId":"Qwb67qny"},"endBinding":{"focus":0.031514485677083336,"gap":7.6915283203125,"elementId":"xtWBYooG"},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[86.69232177734375,0]],"index":"a9"},{"type":"arrow","version":126,"versionNonce":1164549236,"isDeleted":false,"id":"RkO9fShShWdtGtLF6nwDU","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":-101.29632532596588,"y":-166.75987243652344,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":86.69232177734375,"height":0,"seed":1086013648,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"focus":-0.031514485677083336,"gap":11.795806884765625,"elementId":"xtWBYooG"},"endBinding":{"focus":0.005734761555989583,"gap":15.1439208984375,"elementId":"NWx1okts"},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[86.69232177734375,0]],"index":"aA"},{"type":"arrow","version":266,"versionNonce":1424200908,"isDeleted":false,"id":"kjB8EEBb2PEJTk9shZOAv","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":102.73345983028412,"y":-166.75987243652344,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":57.39947509765625,"height":0,"seed":1597679312,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"focus":-0.005734761555989583,"gap":8.44354248046875,"elementId":"NWx1okts"},"endBinding":{"focus":0.005734761555989583,"gap":8.2581787109375,"elementId":"KDLWUP0k"},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[57.39947509765625,0]],"index":"aB"},{"type":"arrow","version":438,"versionNonce":208006644,"isDeleted":false,"id":"I_JbaPVBlr2PsmaXfdfNh","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":410.2135623693466,"y":-166.75987243652344,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":40.00860595703125,"height":0,"seed":81611984,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":null,"endBinding":{"focus":0.005734761555989583,"gap":8.79229736328125,"elementId":"nqn2xr0U"},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[40.00860595703125,0]],"index":"aC"},{"type":"arrow","version":522,"versionNonce":1202658124,"isDeleted":false,"id":"hlmOV257uJWO9w_mN-ExM","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":408.4583133459091,"y":-165.1130828857422,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":37.56182861328125,"height":68.14346313476562,"seed":1799041744,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"focus":-0.9855236047277146,"gap":5.69219970703125,"elementId":"KDLWUP0k"},"endBinding":{"focus":-1.0954536285911458,"gap":12.99432373046875,"elementId":"up6uGoQs"},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[37.56182861328125,68.14346313476562]],"index":"aD"},{"type":"text","version":128,"versionNonce":584847220,"isDeleted":false,"id":"objbW5Vw","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-390.7998958826065,"y":-55.386971724660725,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":219.6719207763672,"height":45,"seed":1031103024,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"fontSize":36,"fontFamily":1,"text":"user thread:","rawText":"user thread:","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"user thread:","lineHeight":1.25,"baseline":32,"autoResize":true,"index":"aE"},{"type":"text","version":61,"versionNonce":340120012,"isDeleted":false,"id":"AmAx3NNz","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-393.0414425134659,"y":10.035842895507812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":58.59375,"height":24,"seed":1318291504,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"lmPTNwy4elbC5c96jVGn8","type":"arrow"},{"id":"RDJNar61WMOt336esRU6-","type":"arrow"}],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"initd","rawText":"initd","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"initd","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"aF"},{"type":"text","version":117,"versionNonce":420610292,"isDeleted":false,"id":"oODzxtWW","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-241.9983822107315,"y":8.718948364257812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":141.259765625,"height":24,"seed":5967408,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"VjmYtiDKzSZg3fYTv6Led","type":"arrow"}],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"process_exec","rawText":"process_exec","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"process_exec","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"aG"},{"type":"arrow","version":236,"versionNonce":968996940,"isDeleted":false,"id":"lmPTNwy4elbC5c96jVGn8","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":-324.66348230838776,"y":20.340774536132812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":74.97357177734375,"height":0,"seed":674875440,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"focus":-0.14125569661458334,"gap":9.784210205078125,"elementId":"AmAx3NNz"},"endBinding":{"focus":0.031514485677083336,"gap":7.6915283203125,"elementId":"oODzxtWW"},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[74.97357177734375,0]],"index":"aH"},{"type":"text","version":546,"versionNonce":109953652,"isDeleted":false,"id":"ToWCLg4b","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":-11.257568001747131,"y":8.718948364257812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":82.03125,"height":24,"seed":62757005,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"LUFuCeT9ueQLCJb1-097l","type":"arrow"}],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"do_iret","rawText":"do_iret","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"do_iret","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"aI"},{"type":"arrow","version":1096,"versionNonce":1140641484,"isDeleted":false,"id":"VjmYtiDKzSZg3fYTv6Led","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":-93.92266809940338,"y":20.340774536132812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":74.97357177734375,"height":0,"seed":1727332077,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"focus":-0.031514485677083336,"gap":7.450714111328125,"elementId":"oODzxtWW"},"endBinding":{"focus":0.031514485677083336,"gap":7.6915283203125,"elementId":"ToWCLg4b"},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[74.97357177734375,0]],"index":"aJ"},{"type":"arrow","version":90,"versionNonce":571823092,"isDeleted":false,"id":"RDJNar61WMOt336esRU6-","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":2,"opacity":60,"angle":0,"x":450.73349034786224,"y":-164.6107940673828,"strokeColor":"#f08c00","backgroundColor":"transparent","width":812.4368591308594,"height":167.1312255859375,"seed":1923817008,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"elementId":"nqn2xr0U","focus":0.5526983993335116,"gap":8.280975341796875},"endBinding":{"elementId":"AmAx3NNz","focus":-1.0592821526366774,"gap":7.515411376953125},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[-812.4368591308594,167.1312255859375]],"index":"aK"},{"type":"text","version":612,"versionNonce":865146188,"isDeleted":false,"id":"1wELq3Od","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":158.07380792341735,"y":8.718948364257812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":70.3125,"height":24,"seed":618371587,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"O-794BlCyDjdiZ_uJqa9z","type":"arrow"}],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"_start","rawText":"_start","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"_start","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"aL"},{"type":"arrow","version":1232,"versionNonce":1504621940,"isDeleted":false,"id":"LUFuCeT9ueQLCJb1-097l","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":75.4087078257611,"y":20.340774536132812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":74.97357177734375,"height":0,"seed":452944291,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"focus":-0.03151448567708332,"gap":4.63502582750823,"elementId":"ToWCLg4b"},"endBinding":{"focus":0.03151448567708333,"gap":7.6915283203125,"elementId":"1wELq3Od"},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[74.97357177734375,0]],"index":"aM"},{"type":"text","version":682,"versionNonce":1708690380,"isDeleted":false,"id":"k8Zx7W5m","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":320.7599330262134,"y":8.718948364257812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":46.875,"height":24,"seed":1469554224,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[{"id":"O-794BlCyDjdiZ_uJqa9z","type":"arrow"}],"updated":1736753008563,"link":null,"locked":false,"fontSize":20,"fontFamily":3,"text":"main","rawText":"main","textAlign":"left","verticalAlign":"top","containerId":null,"originalText":"main","lineHeight":1.2,"baseline":18,"autoResize":true,"index":"aN"},{"type":"arrow","version":1376,"versionNonce":1788864244,"isDeleted":false,"id":"O-794BlCyDjdiZ_uJqa9z","fillStyle":"hachure","strokeWidth":2,"strokeStyle":"solid","roughness":0,"opacity":100,"angle":0,"x":238.09483292855714,"y":20.340774536132812,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":74.97357177734375,"height":0,"seed":560513744,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1736753008563,"link":null,"locked":false,"startBinding":{"elementId":"1wELq3Od","focus":-0.03151448567708333,"gap":9.70852500513979},"endBinding":{"elementId":"k8Zx7W5m","focus":0.031514485677083336,"gap":7.6915283203125},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[74.97357177734375,0]],"index":"aO"}],"appState":{"theme":"light","viewBackgroundColor":"#ffffff","currentItemStrokeColor":"transparent","currentItemBackgroundColor":"#b2f2bb","currentItemFillStyle":"hachure","currentItemStrokeWidth":2,"currentItemStrokeStyle":"solid","currentItemRoughness":2,"currentItemOpacity":60,"currentItemFontFamily":3,"currentItemFontSize":36,"currentItemTextAlign":"left","currentItemStartArrowhead":null,"currentItemEndArrowhead":"arrow","currentItemArrowType":"round","scrollX":445.3631213123863,"scrollY":455.82609085088353,"zoom":{"value":1.602031},"currentItemRoundness":"round","gridSize":null,"gridStep":5,"gridModeEnabled":false,"gridColor":{"Bold":"rgba(217, 217, 217, 0.5)","Regular":"rgba(230, 230, 230, 0.5)"},"currentStrokeOptions":null,"frameRendering":{"enabled":true,"clip":true,"name":true,"outline":true},"objectsSnapModeEnabled":false,"activeTool":{"type":"selection","customType":null,"locked":false,"lastActiveTool":null}},"files":{}};InitialData.scrollToContent=true;App=()=>{const e=React.useRef(null),t=React.useRef(null),[n,i]=React.useState({width:void 0,height:void 0});return React.useEffect(()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height});const e=()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height})};return window.addEventListener("resize",e),()=>window.removeEventListener("resize",e)},[t]),React.createElement(React.Fragment,null,React.createElement("div",{className:"excalidraw-wrapper",ref:t},React.createElement(ExcalidrawLib.Excalidraw,{ref:e,width:n.width,height:n.height,initialData:InitialData,viewModeEnabled:!0,zenModeEnabled:!0,gridModeEnabled:!1})))},excalidrawWrapper=document.getElementById("argument-passingexcalidraw.md");ReactDOM.render(React.createElement(App),excalidrawWrapper);})();</script>