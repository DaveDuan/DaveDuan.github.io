---
layout: splash
title:  "Java Mind Map"
date:   2020-11-09 00:00:40 +0800
categories: [memo, java, mind-map]
classes: wide
---
<html>
    <head>
        <style type="text/css">
            body {
                margin: 0;
            }
            #demo_main {
                margin-top: 48px;
            }
            #main-part {
                margin-right: 8px;
                width: auto;
                margin: 0 16px;
            }
            #chart_wrapper {
                overflow: scroll;
                height:calc(100vh - 120px);
                width: 100%;
                display: inline-block;
            }
            #parent-div {
                position: relative;
                display: inline-block;
            }
            #paperjsdemocanvas {
                width: 400px;
                height: 400px;
            }
            .dynamic-textarea {
                border: 1px solid;
                outline: none;
            }
            #map_list {
                display: inline-block;
                width: 200px;
                padding: 16px;
                vertical-align: top;
            }
            #map_list a {
                text-decoration: underline;
                padding: 4px 0;
                cursor: pointer;
                display: block;
            }
            .demo {
                display: inline-block;
                border: 1px solid black;
            }
            .legend {
                padding: 4px 16px;
                align-items: center;
                background-color: black;
                color: white;
                display: flex;
                flex-direction: row;
                justify-content: space-between;
                flex-wrap: wrap;
            }
            .legend .key {
                background-color: white;
                color: black;
                margin: 0 4px;
                padding: 0 4px;
                font-weight: 900;
            }
            .legend .sc {
                margin:2px 4px;
            }
            #file{
                display: none;
            }
            .mindmap {
                display: none;
            }
        </style>
    </head>
<body>
    <div id="demo_main">
        <div id="main-part">
            <div class="demo">
                <div id="chart_wrapper">
                    <div id="parent-div" class="canvas-wrapper">
                        <canvas id="paperjsdemocanvas"></canvas>
                    </div>
                </div>
                <div class="legend">
                    <span class="sc"><span class="key">↑ ↓ ← → </span>select</span>
                    <span class="sc"><span class="key">Shift+↑ ↓</span>move</span>
                    <span class="sc"><span class="key">Enter</span>create sibling</span>
                    <span class="sc"><span class="key">Shift+Enter</span>create child</span>
                    <span class="sc"><span class="key">Shift+Space</span>expand/collapse</span>
                    <span class="sc"><span class="key">Space</span>edit</span>
                    <span class="sc"><span class="key">l</span>edit link</span>
                    <span class="sc"><span class="key">Delete</span>delete</span>
                    <span class="sc"><span class="key">Ctrl+c</span>copy</span>
                    <span class="sc"><span class="key">Ctrl+x</span>cut</span>
                    <span class="sc"><span class="key">Ctrl+v</span>paste</span>
                    <span class="sc"><span class="key">Esc</span>abort editing</span>
                    <span class="sc"><span class="key">c</span>center</span>
                    <span class="sc"><span class="key">e</span>download png</span>
                    <span class="sc"><span class="key">j</span>download json</span>
                    <span class="sc"><span class="key">i</span>import json</span>
                </div>
            </div>
            <div>此工具源代码在<a href="https://github.com/DaveDuan/demos/tree/master/paperjs-demo">GitHub</a></div>
            <input id="file" type="file" />
        </div>
    </div>
</body>
<script>
window.onbeforeunload = function (e) {
    e = e || window.event;

    // For IE and Firefox prior to version 4
    if (e) {
        e.returnValue = 'Sure?';
    }

    // For Safari
    return 'Sure?';
};
</script>

<script type="text/javascript" src="/assets/js/paper-full.min.js"></script>
<script type="text/paperscript" canvas="paperjsdemocanvas" src="/assets/js/paperdemo.js"></script>
<script type="text/javascript">
window.onload = function() {
    console.info(window.paperjsDemo);
    fetch("/assets/json/java.json").then(res => {
        res.text().then(json => window.paperjsDemo.importJSONData(json) )
    })
}


</script>
</html>