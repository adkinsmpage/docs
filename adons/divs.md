# 常用 Element

下列所有的元素都是 CSS 选择器，可以使用 `document.querySelector()` 查找。

## #cover1.cover1

这个元素是 pop Item  的父元素，可以这样插入一个 pop：

```js
let pName = "HelloWorld";
let StringContent = `
            <div class="popUp" id="pop${pName}">
                <span class="btnClose" onclick="closePop(pop${pName})"></span>
                <div class="pTitle">${pName}</div>
                <div class="pContent">
                hi
                </div>
            </div>`;
document
    .querySelector("#cover1.cover1")
    .insertAdjacentHTML("beforeend", StringContent);

let image = document.createElement("img");
document.querySelector("#laupad .icons .icon_top").append(image);

image.src =
    "https://img.icons8.com/material-two-tone/48/000000/screensharing.png";
image.alt = pName;
image.addEventListener("click", () => {
    showPop("pop" + pName);
});

```

## #right-menu.right-menu

这是右键菜单 Item 的父元素，其 HTML 结构如下：

```html
	<div class="right-menu" id="right-menu">
		<div class="list">
			<div>xxx...</div>
		</div>
	</div>
```

## #laupad .icons .icon_top

这是启动台 Item 的父元素。

目前支持插入 `svg` `img`.

## .dropdown

这是主菜单 Item 的父元素。其结构如下：

```html
	<div class="dropdown">
		<div class="item">
			<button class="dropbtn">Dev</button>
			<div class="dropdown-content">
				<a id="dropdownHeaderReloadDevBtn">Reload</a>
				<a id="dropdownHeaderToolsDevBtn">Dev Tools</a>
			</div>
		</div>
		<div class="item">
			<button class="dropbtn">Plugins</button>
			<div class="dropdown-content">
				<a id="dropdownHeaderInstallPluginsBtn">Install Plugin From JSON File...</a>
				<a id="dropdownHeaderUninstallAllPluginsBtn">Uninstall All Plugins</a>
			</div>
		</div>
	</div>
```

## #consoleCentre .centreCon

这是控制中心的 div 。其结构如下：

```html
		<div class="centreCon">
			<div class="centreItem">
				<img src="./settings.svg" onclick="showPop('popSettings')" alt="" />
			</div>
		</div>
```
