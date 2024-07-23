# Vicky的秘密空间

<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的收藏夹</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>我的收藏夹</h1>
        <form id="addLinkForm">
            <input type="text" id="linkTitle" placeholder="链接标题" required>
            <input type="url" id="linkUrl" placeholder="链接地址" required>
            <button type="submit">添加链接</button>
        </form>
    </header>
    <main>
        <ul id="linkList">
            <!-- 链接列表将会在这里生成 -->
        </ul>
    </main>
    <script src="script.js"></script>
