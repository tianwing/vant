# Field 输入框

### 介绍

表单中的输入框组件

### 引入

``` javascript
import Vue from 'vue';
import { Field } from 'vant';

Vue.use(Field);
```

## 代码演示

### 基础用法

可以通过`v-model`双向绑定输入框的值，通过`placeholder`设置占位提示文字

```html
<!-- Field 是基于 Cell 实现的，可以使用 CellGroup 作为父元素来提供外边框。 -->
<van-cell-group>
  <van-field v-model="value" placeholder="请输入用户名" />
</van-cell-group>
```

```js
export default {
  data() {
    return {
      value: ''
    };
  }
}
```

### 自定义类型

根据`type`属性定义不同类型的输入框，默认值为`text`

```html
<!-- type="text" 可以输入任意文本 -->
<van-field v-model="text" label="文本" />

<!-- type="password" 表示输入密码 -->
<van-field v-model="password" type="password" label="密码" />

<!-- type="number" 允许输入数字和小数点，调起全键盘 -->
<van-field v-model="number" type="number" label="数字" />

<!-- type="tel" 输入手机号，调起手机号键盘 -->
<van-field v-model="tel" type="tel" label="手机号" />
```

```js
export default {
  data() {
    return {
      tel: '',
      text: '',
      number: '',
      password: ''
    };
  }
}
```

### 禁用输入框

通过`readonly`将输入框设置为只读状态，通过`disabled`将输入框设置为禁用状态

```html
<van-cell-group>
  <van-field label="文本" value="输入框只读" readonly />
  <van-field label="文本" value="输入框已禁用" disabled />
</van-cell-group>
```

### 显示图标

通过`left-icon`和`right-icon`配置输入框两侧的图标，通过设置`clearable`在输入过程中展示清除图标

```html
<van-cell-group>
  <van-field
    v-model="value1"
    label="文本"
    left-icon="smile-o"
    right-icon="warning-o"
    placeholder="显示图标"
  />
  <van-field
    v-model="value2"
    clearable
    label="文本"
    left-icon="music-o"
    placeholder="显示清除图标"
  />
</van-cell-group>
```

```js
export default {
  data() {
    return {
      value1: '',
      value2: '123'
    };
  }
};
```

### 错误提示

设置`required`属性表示这是一个必填项，可以配合`error`或`error-message`属性显示对应的错误提示

```html
<van-cell-group>
  <van-field
    v-model="username"
    error
    required
    label="用户名"
    placeholder="请输入用户名"
  />
  <van-field
    v-model="phone"
    required
    label="手机号"
    placeholder="请输入手机号"
    error-message="手机号格式错误"
  />
</van-cell-group>
```

### 插入按钮

通过 button 插槽可以在输入框尾部插入按钮

```html
<van-cell-group>
  <van-field
    v-model="sms"
    center
    clearable
    label="短信验证码"
    placeholder="请输入短信验证码"
  >
    <van-button slot="button" size="small" type="primary">发送验证码</van-button>
  </van-field>
</van-cell-group>
```

### 高度自适应

对于 textarea，可以通过`autosize`属性设置高度自适应

```html
<van-cell-group>
  <van-field
    v-model="message"
    rows="1"
    autosize
    label="留言"
    type="textarea"
    placeholder="请输入留言"
  />
</van-cell-group>
```

### 显示字数统计

设置`maxlength`和`show-word-limit`属性后会在底部显示字数统计

```html
<van-cell-group>
  <van-field
    v-model="message"
    rows="2"
    autosize
    label="留言"
    type="textarea"
    maxlength="50"
    placeholder="请输入留言"
    show-word-limit
  />
</van-cell-group>
```

## API

### Props

| 参数 | 说明 | 类型 | 默认值 | 版本 |
|------|------|------|------|------|
| label | 输入框左侧文本 | *string* | - | - |
| value | 当前输入的值 | *string \| number* | - | - |
| type | 输入框类型, 可选值为 `tel` `number`<br>`textarea` `password` 等 | *string* | `text` | - |
| size | 大小，可选值为 `large` | *string* | - | - |
| maxlength | 输入的最大字符数 | *string \| number* | - | - |
| placeholder | 占位提示文字 | *string* | - | - |
| border | 是否显示内边框 | *boolean* | `true` | - |
| disabled | 是否禁用输入框 | *boolean* | `false` | - |
| readonly | 是否只读 | *boolean* | `false` | - |
| required | 是否显示表单必填星号 | *boolean* | `false` | - |
| clearable | 是否启用清除控件 | *boolean* | `false` | - |
| clickable | 是否开启点击反馈 | *boolean* | `false` | - |
| is-link | 是否展示右侧箭头并开启点击反馈 | *boolean* | `false` | - |
| autofocus | 是否自动聚焦，iOS 系统不支持该属性 | *boolean* | `false` | - |
| show-word-limit | 是否显示字数统计，需要设置`maxlength`属性 | *boolean* | `false` | 2.2.8 |
| error | 是否将输入内容标红 | *boolean* | `false` | - |
| arrow-direction | 箭头方向，可选值为 `left` `up` `down` | *string* | - | 2.0.4 |
| error-message | 底部错误提示文案，为空时不展示 | *string* | `''` | - 
| label-class | 左侧文本额外类名 | *any* | - | - |
| label-width | 左侧文本宽度，默认单位为`px` | *string \| number* | `90px` | - |
| label-align | 左侧文本对齐方式，可选值为 `center` `right` | *string* | `left` | - |
| input-align | 输入框内容对齐方式，可选值为 `center` `right` | *string* | `left` | - |
| error-message-align | 错误提示文案对齐方式，可选值为 `center` `right` | *string* | `left` | - |
| autosize | 自适应内容高度，只对 textarea 有效，可传入对象,<br>如 { maxHeight: 100, minHeight: 50 }，单位为`px` | *boolean \| object* | `false` | - |
| left-icon | 左侧图标名称或图片链接，可选值见 [Icon 组件](#/zh-CN/icon) | *string* | - | - |
| right-icon | 右侧图标名称或图片链接，可选值见 [Icon 组件](#/zh-CN/icon) | *string* | - | - |

### Events

除下列事件外，Field 默认支持 Input 标签所有的原生事件

| 事件 | 说明 | 回调参数 |
|------|------|------|
| input | 输入框内容变化时触发 | value: 输入框当前值 |
| focus | 输入框获得焦点时触发 | event: Event |
| blur | 输入框失去焦点时触发 | event: Event |
| clear | 点击清除按钮时触发 | event: Event |
| click | 点击时触发 | event: Event |
| click-left-icon | 点击左侧图标时触发 | event: Event |
| click-right-icon | 点击右侧图标时触发 | event: Event |

### 方法

通过 [ref](https://cn.vuejs.org/v2/api/#ref) 可以获取到 Field 实例并调用实例方法

| 方法名 | 说明 | 参数 | 返回值 |
|------|------|------|------|
| focus | 获取输入框焦点 | - | - |
| blur | 取消输入框焦点 | - | - |

### Slots

| 名称 | 说明 |
|------|------|
| label | 自定义输入框标签 |
| input | 自定义输入框，使用此插槽后，与输入框相关的属性和事件将失效 |
| left-icon | 自定义输入框头部图标 |
| right-icon | 自定义输入框尾部图标 |
| button | 自定义输入框尾部按钮 |
