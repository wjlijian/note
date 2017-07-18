			现在来实现表单提交事件的相应，添加 'handleSubmit' 如下：
```js
				<form className='comment-form' onSubmit={this.handleSubmit}>
						<input type='text' className='input' ref="content"/>
						<button type='submit' className='submit-btn' >提交</button>					
				</form>
```
				submit 提交

				handle 处理

				form 表单

	然后定义 handleSubmit  js  

	handleSubmit = () =>{}

```

	由于使用了ES6 的胖箭头函数语法，所以使用中就不需要

	this.handleSubmit.bind(this)了

```

	e.preventDefault() 在表单提交的时候阻止跳转



### 拿到input输入 ###

	首先添加 ref 如下

```js
	<input type='text' className='input' ref={value=>this.comment=value}/>
```
	上面,ref 的意思是"指针"  ，后面大括号中的内容，也就是

```
	value=>this.comment=value
```
	是一个胖箭头函数。其中 value 指当前 input 这个节点对应的 Object ,然后
```
	this.comment = value

```
	就是把 input 对象 , 赋值给一个成员变量 ， 目的是在整个 class 之内 ，可以说随处访问

	这样，如果想在 handleSubmit 函数中拿到用户输入的文本 ， 就

```js
	handleSubmit=(e)=>{
		e.preventDefault()
		console.log(this.comment.value)
	}

```
		到这里，如何从 form 的输入框中拿到字符串，这个技巧我们就掌握了。同时，这也是最简单的
		一种方式，另外，还可以通过 "受控组件" 的形式来取值 ，

### 修改state ###


	先来讨论 render() 的本性：

	> 一旦 state 变，render() 自动被重新执行

	所以，页面上由两条评论变成三条。不需要修改 html ,直接修改 state

	最后，我们还需要在提交结束后 ， 清空 input 里的字符串

	handleSubmit 里面添加

	```js
	this.comment.value=''
	```

	但是,如果一个 form 的 input 比较多，那么下面的方式可能更好(在handleSubmit里添加)

```js
	handleSubmit=()=>{
		this.myForm.reset()
	}

...
	<form ref={value => this.myForm = value}
	onSubmit={this.handleSubmit} className="comment-form">
```
