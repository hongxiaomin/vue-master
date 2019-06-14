#Vue 源码解读
### 编译
编译模块分为三个阶段
1. parse  使用正则解析template中的vue的指令（v-xxx）变量等等，形成语法树AST
2. optimize 标记一些静态节点，用做后面性能优化，在diff的时候直接略过
3. generate 把第一部分生成的AST转化为渲染函数render function

### 响应式
这一块是vue最核心的内容
初始化的时候通过defineProperty进行绑定，设置通知的机制，当编译生成的渲染函数被实际渲染的时候，会触发getter进行依赖收集，在数据变化的时候，触发setter进行更新。

 