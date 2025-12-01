<!DOCTYPE html>
<html lang="zh">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>代码效果查看器</title>
  <style>
    body {
      background-color: #e4e4e4;
      font-family: 'Courier New', Courier, monospace;
      margin: 0;
      padding: 0;
      height: 100vh;
      overflow: hidden;
    }

    /* Container for desktop view */
    .desktop {
      background-color: #2c3e50;
      height: 100%;
      display: flex;
      flex-direction: column;
    }

    /* Taskbar style */
    .taskbar {
      background-color: #34495e;
      color: white;
      height: 40px;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      padding: 0 20px;
    }

    .taskbar .start-btn {
      cursor: pointer;
      font-weight: bold;
    }

    .taskbar .open-windows {
      display: flex;
      gap: 10px;
      margin-left: 20px;
    }

    .taskbar .open-windows .window-btn {
      cursor: pointer;
      padding: 5px 10px;
      background-color: #2980b9;
      color: white;
      border-radius: 5px;
      font-size: 14px;
    }

    /* Window style */
    .window {
      background-color: white;
      border: 1px solid #ccc;
      border-radius: 8px;
      width: 80%;
      height: 80%;
      margin: 20px auto;
      position: relative;
      display: none;
      box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.1);
    }

    /* Title bar for window */
    .window .title-bar {
      background-color: #3498db;
      color: white;
      padding: 10px;
      font-size: 18px;
      text-align: center;
      cursor: move;
    }

    /* Code Editor Area */
    .window .code-editor {
      padding: 20px;
      height: calc(100% - 40px);
      display: flex;
      flex-direction: column;
      gap: 15px;
    }

    /* Textarea for the code editor */
    .window .code-editor textarea {
      width: 100%;
      height: 200px;
      border: 1px solid #ccc;
      border-radius: 8px;
      padding: 10px;
      font-family: 'Courier New', Courier, monospace;
      font-size: 14px;
      background-color: #f5f5f5;
      resize: none;
    }

    /* Button to run the code */
    .window .code-editor button {
      padding: 10px;
      background-color: #2980b9;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 16px;
    }

    /* Button hover effect */
    .window .code-editor button:hover {
      background-color: #1f78b9;
    }

    /* Output window for the code result */
    .window .output {
      padding: 15px;
      background-color: #2c3e50;
      color: white;
      height: 200px;
      border-radius: 8px;
      overflow-y: auto;
    }

    .window .output iframe {
      width: 100%;
      height: 100%;
      border: none;
    }

  </style>
</head>
<body>

  <div class="desktop">
    <!-- Taskbar -->
    <div class="taskbar">
      <div class="start-btn" onclick="toggleStartMenu()">开始</div>
      <div class="open-windows">
        <div class="window-btn" onclick="openCodeEditor()">打开代码编辑器</div>
      </div>
    </div>

    <!-- Code Editor Window -->
    <div class="window" id="codeEditorWindow">
      <div class="title-bar">代码编辑器</div>
      <div class="code-editor">
        <textarea id="htmlCode" placeholder="输入 HTML 代码"></textarea>
        <textarea id="cssCode" placeholder="输入 CSS 代码"></textarea>
        <textarea id="jsCode" placeholder="输入 JavaScript 代码"></textarea>
        <button onclick="runCode()">运行代码</button>
      </div>
      <div class="output">
        <iframe id="outputFrame"></iframe>
      </div>
    </div>

  </div>

  <script>
    function toggleStartMenu() {
      alert("开始菜单按钮被点击！");
    }

    function openCodeEditor() {
      const editorWindow = document.getElementById('codeEditorWindow');
      editorWindow.style.display = 'block';
    }

    function runCode() {
      const htmlCode = document.getElementById('htmlCode').value;
      const cssCode = document.getElementById('cssCode').value;
      const jsCode = document.getElementById('jsCode').value;

      const outputFrame = document.getElementById('outputFrame');
      const document = outputFrame.contentDocument || outputFrame.contentWindow.document;

      document.open();
      document.write(`
        <html>
          <head>
            <style>${cssCode}</style>
          </head>
          <body>
            ${htmlCode}
            <script>${jsCode}</script>
          </body>
        </html>
      `);
      document.close();
    }
  </script>

</body>
</html>
