## 在 CSS 中如何实现变量？



#### 已知 Sass、Less等 CSS 预处理语法可以实现变量的抽象，实际的 CSS 中是否支持声明使用变量，以及如何使用?



代码如下：

```css
<style>
	/** css3 新增属性 :root */
    :root {
        --main-theme: #ccc;
    }
    header {
        width: 100%;
        height: 200px;
        background-color: var(--main-theme);
        margin-bottom: 10px;
    }
    main {
        width: 100%;
        height: 200px;
        background-color: var(--main-theme);
    }
</style>
```

```html
<header>111</header>
<main>
    <p>222</p>
    <button id="changeTheme">xxx</button>
</main>
```

```js
<script>
    document.getElementById("changeTheme").onclick = function () {
    const root = document.querySelector(":root");
    const theme = getComputedStyle(root).getPropertyValue("--main-theme");  // #ccc
    root.style.setProperty("--main-theme", "red");
};
</script>
```

