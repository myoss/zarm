# 文本框 Input

## 基本用法

```jsx
import { Input, Cell } from 'zarm';

class Demo extends React.Component {
  constructor() {
    super();
    this.state = {
      inputValue: '',
    }
  }

  handleInputChange(value) {
    this.setState({
      inputValue: value,
    })
  }

  render() {
    return (
      <div>
        <Cell title="单行文本">
          <Input
            type="text"
            placeholder="请输入"
            value={this.state.inputValue}
            onChange={this.handleInputChange.bind(this)}
            />
        </Cell>
        <Cell title="多行文本"><Input type="text" rows={3} placeholder="请输入" /></Cell>
      </div>
    )
  }
}

ReactDOM.render(<Demo />, mountNode);
```

## 输入类型

```jsx
import { Input, Cell } from 'zarm';

class Demo extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      focused: false,
      number: '',
    };
  }

  render() {
    return (
      <div>
        <Cell title="数字">
          <Input
            ref={(ref) => { this.manualFocus = ref; }}
            type="number"
            placeholder="type is number"
            value={this.state.number}
            focused={this.state.focused}
            onFocus={value => console.log(`onFocus: ${value}`)}
            onBlur={value => console.log(`onBlur: ${value}`)}
          />
        </Cell>

        <Cell title="金额">
          <Input type="price" placeholder="type is price" />
        </Cell>

        <Cell title="身份证">
          <Input type="idcard" placeholder="type is idcard" />
        </Cell>

        <Cell>
          <button onClick={() => this.manualFocus.focus()}>click to focus the first input</button>
        </Cell>
      </div>
    )
  }
}

ReactDOM.render(<Demo />, mountNode);
```



## 高度自适应

```jsx
import { Input, Cell } from 'zarm';

class Demo extends React.Component {
  render() {
    return (
      <div>
        <Cell title="多行文本"><Input autoHeight type="text" rows={3} placeholder="写点啥..." /></Cell>
      </div>
    )
  }
}

ReactDOM.render(<Demo />, mountNode);
```



## 无标签栏
```jsx
import { Input, Cell } from 'zarm';

class Demo extends React.Component {
  render() {
    return (
      <div>
        <Cell><Input type="text" placeholder="标题" /></Cell>
        <Cell><Input autoHeight type="text" rows={4} maxLength={200} placeholder="摘要" /></Cell>
      </div>
    )
  }
}

ReactDOM.render(<Demo />, mountNode);
```



## 显示输入字数
```jsx
import { Input, Cell } from 'zarm';

class Demo extends React.Component {
  render() {
    return (
      <div>
        <Cell><Input autoHeight showLength type="text" rows={4} maxLength={200} placeholder="摘要" /></Cell>
      </div>
    )
  }
}

ReactDOM.render(<Demo />, mountNode);
```



## API

| 属性 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| type | string | 'text' | 类型，可选值 `text`、`number`、`idcard`、`price`、`password`、`search` |
| value | number | string | - | 值 |
| defaultValue | number | string | - | 初始值 |
| disabled | boolean | false | 是否禁用 |
| rows | number | 2 | 多行文本时的显示行数。type为text类型时有效。 |
| autoHeight | boolean | false | 是否高度自适应 |
| maxLength | number | - | 输入字数上限 |
| showLength | boolean | false | 是否显示输入字数。多行文本（type="text"且包含rows属性）时有效。 |
| clearable | boolean | true | 是否显示清除按钮。多行文本（type="text"且包含rows属性）时无效。必须为受控组件（属性包含value、onChange）时方可生效。 |
| onChange | (value?: number \| string) => void | - | 值变化时触发的回调函数 |

