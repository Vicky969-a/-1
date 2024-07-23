# Vicky的秘密空间
my-personal-site/
├── index.html
├── styles.css
└── links.json
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
</body>
</html>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

header {
    background-color: #333;
    color: #fff;
    padding: 1em;
    text-align: center;
}

form {
    margin: 1em 0;
}

input {
    margin: 0.5em;
    padding: 0.5em;
    font-size: 1em;
}

button {
    padding: 0.5em 1em;
    font-size: 1em;
    color: #fff;
    background-color: #007bff;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

main {
    padding: 1em;
}

ul {
    list-style: none;
    padding: 0;
}

li {
    background: #fff;
    border: 1px solid #ddd;
    margin: 0.5em 0;
    padding: 1em;
}

a {
    text-decoration: none;
    color: #007bff;
}

a:hover {
    text-decoration: underline;
}
document.addEventListener('DOMContentLoaded', () => {
    const linkList = document.getElementById('linkList');
    const addLinkForm = document.getElementById('addLinkForm');
    const linkTitle = document.getElementById('linkTitle');
    const linkUrl = document.getElementById('linkUrl');

    // Load existing links from localStorage
    const loadLinks = () => {
        const links = JSON.parse(localStorage.getItem('links')) || [];
        linkList.innerHTML = links.map(link => `
            <li>
                <a href="${link.url}" target="_blank">${link.title}</a>
            </li>
        `).join('');
    };

    // Save a new link
    const saveLink = (title, url) => {
        const links = JSON.parse(localStorage.getItem('links')) || [];
        links.push({ title, url });
        localStorage.setItem('links', JSON.stringify(links));
    };

    // Handle form submission
    addLinkForm.addEventListener('submit', (event) => {
        event.preventDefault();
        const title = linkTitle.value.trim();
        const url = linkUrl.value.trim();
        if (title && url) {
            saveLink(title, url);
            linkTitle.value = '';
            linkUrl.value = '';
            loadLinks();
        }
    });

    // Initial load of links
    loadLinks();
});
