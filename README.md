# Vue 源码分析

版本 3.4.36，直接分析 页面中使用的 vue.js，而不是 github 上的源码

https://vuejs.org/  
https://github.com/vuejs/core  

## Vue 全局对象 各种属性

```javascript
    exports.BaseTransition = BaseTransition;
    exports.BaseTransitionPropsValidators = BaseTransitionPropsValidators;
    exports.Comment = Comment;
    exports.DeprecationTypes = DeprecationTypes;
    exports.EffectScope = EffectScope;
    exports.ErrorCodes = ErrorCodes;
    exports.ErrorTypeStrings = ErrorTypeStrings;
    exports.Fragment = Fragment;
    exports.KeepAlive = KeepAlive;
    exports.ReactiveEffect = ReactiveEffect;
    exports.Static = Static;
    exports.Suspense = Suspense;
    exports.Teleport = Teleport;
    exports.Text = Text;
    exports.TrackOpTypes = TrackOpTypes;
    exports.Transition = Transition;
    exports.TransitionGroup = TransitionGroup;
    exports.TriggerOpTypes = TriggerOpTypes;
    exports.VueElement = VueElement;
    exports.assertNumber = assertNumber;
    exports.callWithAsyncErrorHandling = callWithAsyncErrorHandling;
    exports.callWithErrorHandling = callWithErrorHandling;
    exports.camelize = camelize;
    exports.capitalize = capitalize;
    exports.cloneVNode = cloneVNode;
    exports.compatUtils = compatUtils;
    exports.compile = compileToFunction;
    exports.computed = computed;
    // 创建 app
    exports.createApp = createApp;
    exports.createBlock = createBlock;
    exports.createCommentVNode = createCommentVNode;
    exports.createElementBlock = createElementBlock;
    exports.createElementVNode = createBaseVNode;
    exports.createHydrationRenderer = createHydrationRenderer;
    exports.createPropsRestProxy = createPropsRestProxy;
    exports.createRenderer = createRenderer;
    exports.createSSRApp = createSSRApp;
    exports.createSlots = createSlots;
    exports.createStaticVNode = createStaticVNode;
    exports.createTextVNode = createTextVNode;
    exports.createVNode = createVNode;
    exports.customRef = customRef;
    exports.defineAsyncComponent = defineAsyncComponent;
    exports.defineComponent = defineComponent;
    exports.defineCustomElement = defineCustomElement;
    exports.defineEmits = defineEmits;
    exports.defineExpose = defineExpose;
    exports.defineModel = defineModel;
    exports.defineOptions = defineOptions;
    exports.defineProps = defineProps;
    exports.defineSSRCustomElement = defineSSRCustomElement;
    exports.defineSlots = defineSlots;
    exports.devtools = devtools;
    exports.effect = effect;
    exports.effectScope = effectScope;
    exports.getCurrentInstance = getCurrentInstance;
    exports.getCurrentScope = getCurrentScope;
    exports.getTransitionRawChildren = getTransitionRawChildren;
    exports.guardReactiveProps = guardReactiveProps;
    exports.h = h;
    exports.handleError = handleError;
    exports.hasInjectionContext = hasInjectionContext;
    exports.hydrate = hydrate;
    exports.initCustomFormatter = initCustomFormatter;
    exports.initDirectivesForSSR = initDirectivesForSSR;
    exports.inject = inject;
    exports.isMemoSame = isMemoSame;
    exports.isProxy = isProxy;
    exports.isReactive = isReactive;
    exports.isReadonly = isReadonly;
    exports.isRef = isRef;
    exports.isRuntimeOnly = isRuntimeOnly;
    exports.isShallow = isShallow;
    exports.isVNode = isVNode;
    exports.markRaw = markRaw;
    exports.mergeDefaults = mergeDefaults;
    exports.mergeModels = mergeModels;
    exports.mergeProps = mergeProps;
    exports.nextTick = nextTick;
    exports.normalizeClass = normalizeClass;
    exports.normalizeProps = normalizeProps;
    exports.normalizeStyle = normalizeStyle;
    exports.onActivated = onActivated;
    exports.onBeforeMount = onBeforeMount;
    exports.onBeforeUnmount = onBeforeUnmount;
    exports.onBeforeUpdate = onBeforeUpdate;
    exports.onDeactivated = onDeactivated;
    exports.onErrorCaptured = onErrorCaptured;
    exports.onMounted = onMounted;
    exports.onRenderTracked = onRenderTracked;
    exports.onRenderTriggered = onRenderTriggered;
    exports.onScopeDispose = onScopeDispose;
    exports.onServerPrefetch = onServerPrefetch;
    exports.onUnmounted = onUnmounted;
    exports.onUpdated = onUpdated;
    exports.openBlock = openBlock;
    exports.popScopeId = popScopeId;
    exports.provide = provide;
    exports.proxyRefs = proxyRefs;
    exports.pushScopeId = pushScopeId;
    exports.queuePostFlushCb = queuePostFlushCb;
    exports.reactive = reactive;
    exports.readonly = readonly;
    // ref
    exports.ref = ref;
    exports.registerRuntimeCompiler = registerRuntimeCompiler;
    exports.render = render;
    exports.renderList = renderList;
    exports.renderSlot = renderSlot;
    exports.resolveComponent = resolveComponent;
    exports.resolveDirective = resolveDirective;
    exports.resolveDynamicComponent = resolveDynamicComponent;
    exports.resolveFilter = resolveFilter;
    exports.resolveTransitionHooks = resolveTransitionHooks;
    exports.setBlockTracking = setBlockTracking;
    exports.setDevtoolsHook = setDevtoolsHook;
    exports.setTransitionHooks = setTransitionHooks;
    exports.shallowReactive = shallowReactive;
    exports.shallowReadonly = shallowReadonly;
    exports.shallowRef = shallowRef;
    exports.ssrContextKey = ssrContextKey;
    exports.ssrUtils = ssrUtils;
    exports.stop = stop;
    exports.toDisplayString = toDisplayString;
    exports.toHandlerKey = toHandlerKey;
    exports.toHandlers = toHandlers;
    exports.toRaw = toRaw;
    exports.toRef = toRef;
    exports.toRefs = toRefs;
    exports.toValue = toValue;
    exports.transformVNodeArgs = transformVNodeArgs;
    exports.triggerRef = triggerRef;
    exports.unref = unref;
    exports.useAttrs = useAttrs;
    exports.useCssModule = useCssModule;
    exports.useCssVars = useCssVars;
    exports.useModel = useModel;
    exports.useSSRContext = useSSRContext;
    exports.useSlots = useSlots;
    exports.useTransitionState = useTransitionState;
    exports.vModelCheckbox = vModelCheckbox;
    exports.vModelDynamic = vModelDynamic;
    exports.vModelRadio = vModelRadio;
    exports.vModelSelect = vModelSelect;
    exports.vModelText = vModelText;
    exports.vShow = vShow;
    exports.version = version;
    exports.warn = warn;
    exports.watch = watch;
    exports.watchEffect = watchEffect;
    exports.watchPostEffect = watchPostEffect;
    exports.watchSyncEffect = watchSyncEffect;
    exports.withAsyncContext = withAsyncContext;
    exports.withCtx = withCtx;
    exports.withDefaults = withDefaults;
    exports.withDirectives = withDirectives;
    exports.withKeys = withKeys;
    exports.withMemo = withMemo;
    exports.withModifiers = withModifiers;
    exports.withScopeId = withScopeId;

    return exports;

```



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