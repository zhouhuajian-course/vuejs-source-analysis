# Vue 源码分析

版本 3.4.36，直接分析 页面中使用的 vue.js，而不是 github 上的源码

https://vuejs.org/  
https://github.com/vuejs/core  

## 挂载时，会用容器的CSS选择器，例如#app，获取容器元素

```javascript
        app.mount = (containerOrSelector) => {
            // normalizeContainer 容器正常化
            const container = normalizeContainer(containerOrSelector);
            if (!container) return;
            // ...
        };
```

```javascript
    // 例如传 #app
    function normalizeContainer(container) {
        // 判断是字符串
        if (isString(container)) {
            // 使用 querySelector 拿到容器元素
            const res = document.querySelector(container);
            if (!res) {
                warn(
                    `Failed to mount app: mount target selector "${container}" returned null.`
                );
            }
            // 返回容器元素
            return res;
        }
        if (window.ShadowRoot && container instanceof window.ShadowRoot && container.mode === "closed") {
            warn(
                `mounting on a ShadowRoot with \`{mode: "closed"}\` may lead to unpredictable bugs`
            );
        }
        return container;
    }
```

## 容器内容清空前，会把innerHTML设置为组件的template

```javascript
        app.mount = (containerOrSelector) => {
            const container = normalizeContainer(containerOrSelector);
            if (!container) return;
            // app的组件
            const component = app._component;
            if (!isFunction(component) && !component.render && !component.template) {
                // 组件的template = 容器的innerHTML
                component.template = container.innerHTML;
            }
            // 清空容器内的HTML
            container.innerHTML = "";
            const proxy = mount(container, false, resolveRootNamespace(container));
            if (container instanceof Element) {
                container.removeAttribute("v-cloak");
                container.setAttribute("data-v-app", "");
            }
            return proxy;
        };
```

## 容器的内容会先被清空

```javascript
    const createApp = (...args) => {
        // 调用任何可用的调试功能，例如设置断点
        debugger
        const app = ensureRenderer().createApp(...args);
        {
            injectNativeTagCheck(app);
            injectCompilerOptionsCheck(app);
        }
        const { mount } = app;
        // 挂载时 容器的内容会先被清空
        app.mount = (containerOrSelector) => {
            const container = normalizeContainer(containerOrSelector);
            if (!container) return;
            const component = app._component;
            if (!isFunction(component) && !component.render && !component.template) {
                component.template = container.innerHTML;
            }
            // 清空容器的内容
            container.innerHTML = "";
            const proxy = mount(container, false, resolveRootNamespace(container));
            if (container instanceof Element) {
                container.removeAttribute("v-cloak");
                container.setAttribute("data-v-app", "");
            }
            return proxy;
        };
        return app;
    };

```