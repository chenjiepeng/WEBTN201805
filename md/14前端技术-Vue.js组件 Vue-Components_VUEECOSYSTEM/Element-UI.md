# ElementUI

---

## Element-UI

* Element,一套为开发者、设计师和产品经理准备的基于 Vue 2.0 的桌面端组件库
* Element 特点：
  * 一致性 Consistency
  * 效率 Efficiently
  * 可控 Controllability

# 使用 Element-UI

---

## 搭建Element-UI运行环境

* 方式一：安装独立的Element-UI

  ```bash
  npm i element-ui -S
  ```

* 方式二：使用客户端加载Element-UI

  ```js
  <!-- import Vue before Element -->
  <script src="https://unpkg.com/vue/dist/vue.js"></script>
  <!-- import JavaScript -->
  <script src="https://unpkg.com/element-ui/lib/index.js"></script>
  ```

## 第一个 Element-UI 示例

**如何使用Element-UI示例**
（1）运行NPM安装 Element-UI
（2）注册到 Element-UI中并且创建Vuex实例
（3）Element-UI调用

### 示例：Element-UI 按钮

## 第一个 Element-UI 示例

**如何使用Element-UI示例**
（1）运行NPM安装 Element-UI
（2）注册到 Element-UI中并且创建Vuex实例
（3）Element-UI调用

## 运行NPM 安装 Element-UI

## 使用NPM方式安装 element-ui 组件

```bash
npm i element-ui -S
```

-S -save #dependencies 生产环境 -D -save-dev #devDependencies 开发环境

## 第一个 Element-UI 示例

**如何使用Element-UI示例**
（1）运行NPM安装 Element-UI
（2）注册到 Element-UI中并且创建Vuex实例
（3）Element-UI调用

## 注册到 Element-UI中并且创建Vuex实例

在入口文件main.js 引入 Element-UI

``` vuew
import ElementUI from 'element-ui'
import'element-ui/lib/theme-chalk
index.css'

Vue.use(ElementUI)
```

## 第一个 Element-UI 示例

**如何使用Element-UI示例**
（1）运行NPM安装 Element-UI
（2）注册到 Element-UI中并且创建Vuex实例
（3）*模板中 Element-UI 元素调用*

## 模板中 Element-UI 元素调用

App.vue

```vue
<el-row>
    <el-button>默认按钮</el-buuton>
    <el-button type="primary">主要按钮</el-buuton>
    <el-button type="success">成功按钮</el-buuton>
    <el-button type="info">信息按钮</el-buuton>
    <el-button type="warning">警告按钮</el-buuton>
    <el-button type="danger">危险按钮</el-buuton>
</el-row>
```

```vue
<el-row>
    <el-button plain>朴素按钮</el-buuton>
    <el-button type="primary">主要按钮</el-buuton>
    <el-button type="success">成功按钮</el-buuton>
    <el-button type="info">信息按钮</el-buuton>
    <el-button type="warning">警告按钮</el-buuton>
    <el-button type="danger">危险按钮</el-buuton>
</el-row>
```

```vue
<el-row>
    <el-button round>圆角按钮</el-buuton>
    <el-button type="primary">主要按钮</el-buuton>
    <el-button type="success">成功按钮</el-buuton>
    <el-button type="info">信息按钮</el-buuton>
    <el-button type="warning">警告按钮</el-buuton>
    <el-button type="danger">危险按钮</el-buuton>
</el-row>
```

### 示例：时间选择器

## 模板中 时间选择器

App.vue

```vue
<el-time-select
v-model="value1"
:picker-options="{
    start:'08:30',
    step:'00:15',
    end:'18:30'
}"
placeholder="选择时间">
</el-time-select>
```

```js
<script>
export default {
    data(){
        return {
            value1:''
        }
    }
}
</script>
```

### 示例：Rate 评分

## 模板中 Rate 评分 元素调用

App.vue

```vue
<div class="block">
    <span class="demostration">默认不区分颜色</span>
    <el-rate v-model="value1"></el-rate>
</div>
<div class="block">
    <span class="demonstration">区分颜色</span>
    <el-rate
    v-model="value2"
    :colors="['#99A9BF','#F7BA2A','#FF9900']">
    </el-rate>
</div>
```

```js
<script>
    export default {
        data(){
            return{
                value1:null,
                value2:null
            }
        }
    }
</script>
```