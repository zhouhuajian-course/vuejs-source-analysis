# Vue 源码分析

版本 3.4.36，直接分析 页面中使用的 vue.js，而不是 github 上的源码

https://vuejs.org/  
https://github.com/vuejs/core  

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