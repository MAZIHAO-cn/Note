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
      isHots: {
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

  // 全局过滤器
  Vue.filter('mySlice', function(value) {
    return value.slice(0, 4)
  })

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

生命周期： 	

1. 又名：生命周期回调函数、生命周期函数、生命周期钩子。 
2. 是什么：Vue在关键时刻帮我们调用的一些特殊名称的函数。 	
3. 生命周期函数的名字不可更改，但函数的具体内容是程序员根据需求编写的。 
4. 生命周期函数中的this指向是vm 或 组件实例对象。这意味着你不能使用箭头函数来定义一个生命周期方法 (例如 created: () => this.fetchTodos())。



```html
<div id="root">
  <!-- 完整写法 -->
  <h2 :style="{opacity: opacity}">欢迎学习Vue</h2>
  <!-- ES6 增强版简写 -->
  <h2 :style="{opacity}">欢迎学习Vue</h2>
  <h2 v-if="a">你好啊</h2>
</div>

<script>
  Vue.config.productionTip = false
  new Vue({
    el: '#root',
    data: {
      a: false,
      opacity: 1
    },
    methods: {

    },
    // Vue 完成模版的解析并把初始的真实DOM元素放入页面后，（挂载完毕）调用mounted
    mounted() {
      console.log('mount', this);
      setInterval(() => {
        this.opacity -= 0.01
        if (this.opacity <= 0) {
          this.opacity = 1
        }
      }, 16);
    }
  })

  // 外部定时器（不推荐）
  // setInterval(() => {
  //     vm.opacity -= 0.01
  //     if (vm.opacity <= 0) {
  //         vm.opacity = 1
  //     }
  // }, 16);
</script>
```

#### 046_生命周期——挂载、更新、销毁

```html
<div id="root" :x="n">
  <h2 v-text="n"></h2>
  <h2>当前的n值是：{{n}}</h2>
  <button @click="add">点我n+1</button>
  <button @click="bye">点我销毁vm</button>
</div>
<script>
  Vue.config.productionTip = false;
  new Vue({
    el: '#root',
    // template: `
    // <div>
    //     <h2>当前的n值是：{{n}}</h2>
    //     <button @click="add">点我n+1</button>    
    // </div>
    // `,
    // 使用template模板，容器内就不用放入内容了，不过template模板解析的时候会将外面的root容器给覆盖掉。
    // 而且template模板只能有一个根元素，所以必须用div 将h2与button包裹起来，否则报错
    data: {
      n: 1
    },
    methods: {
      add() {
        console.log('add');
        this.n++
      },
      bye() {
        console.log('bye');
        this.$destroy()
      }
    },
    watch: {
      n() {
        console.log('n变了');
      }
    },

    // （一）挂载流程
    beforeCreate() {
      //看图：这里是指数据代理和数据监测创建之前，不是vm
      console.log('beforeCreate');
      console.log(this); // this指向vm实例对象
      // 此时打开控制台可以看到data中无数据，无methods方法
    },
    created() {
      console.log('create');
      console.log(this); // this指向vm实例对象
      // 此时打开控制台可以看到data中有数据，有add，bye方法
    },
    beforeMount() {
      console.log('beforeMount');
      console.log(this); // this指向vm实例对象
      // 元素都加载完成（未经编译），但还没有挂载上去，HTML的body结构里呈现的依然是模板
      // 在这里面操作DOM白操作，最终会被虚拟dom转换成的真实dom覆盖掉                
    },
    mounted() {
      console.log('mounted');
      console.log(this, this.$el); // this指向vm实例对象
      // 元素都加载完成（编译完成），已经挂载上去了，HTML的body结构里呈现的你想让他呈现的样子
      // 在这里面操作DOM有效，但不推荐
    },

    // （二）更新流程
    beforeUpdate() {
      console.log('beforeUpdate');
      // console.log(this.n)
      // 更新数据时调用，数据为新的，但页面还是旧的，尚未更新
    },
    updated() {
      console.log('updated');
      // console.log(this.n);
      // 数据为新的，但页面也是新的，数据与页面保持同步
    },
    beforeDestroy() {
      console.log('beforeDestroy');
      console.log(this.n);
    },
    destroyed() {
      console.log('destroyed');
      // 点击销毁vm，能打印出n，调用了add方法，但页面不再更新，即到了这个阶段，
      // 能够访问到数据，调用方法， 但所有对数据的修改不会再触发更新了。
      // 此时vm中的data methods 指令等都处于可用状态，马上要执行销毁过程，
      // 一般在此阶段：关闭定时器，取消订阅消息，解绑自定义事件等收尾操作
    }
  })
</script>
```

#### 047_生命周期总结

常用的生命周期钩子：

1. mounted: 发送ajax请求、启动定时器、绑定自定义事件、订阅消息等【初始化操作】。

2. beforeDestroy: 清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】。

关于销毁Vue实例

1. 销毁后借助Vue开发者工具看不到任何信息。

2. 销毁后自定义事件会失效，但原生DOM事件依然有效。

3. 一般不会在beforeDestroy操作数据，因为即便操作数据，也不会再触发更新流程了。

```html
<body>
  <!-- 准备好一个容器 -->
  <!-- 一个容器对应多个实例 -->
  <div id="root">
    <hello></hello>
    <h1>{{msg}}</h1>
    <hr>
    <!-- 第三步：编写组件标签 -->
    <school></school>
    <school></school>
    <hr>
    <!-- 第三步：编写组件标签 -->
    <student></student>
  </div>
  <hr>
  <hr>
  <div id="root2">
    <hello></hello>
    <student></student>
    <school></school>
  </div>
</body>
<script type="text/javascript">
  Vue.config.productionTip = false

  // 第一步：创建一个school组件
  const school = Vue.extend({
    // el: '#root',
    // 组件定义时，一定不要写el配置项，因为最终所有的组件都要被一个vm管理，
    // 由vm决定服务于哪个容器。
    template: `
            <div>
                <h2>学校名称：{{name}}</h2>
                <h2>学校地址：{{address}}</h2> 
                <button @click="showName">点我提示学校名</button>   
  </div>
        `,
    data() {
      return {
        name: '尚硅谷',
        address: '北京'
      }
    },
    methods: {
      showName() {
        alert(this.name)
      }
    }
  })

  // 第一步：创建一个student组件
  const student = Vue.extend({
    template: `
            <div>
                <h2>学生名称：{{name}}</h2>
                <h2>学生年龄：{{age}}</h2>        
  </div>
        `,
    data() {
      return {
        name: '张三',
        age: 18
      }
    }
  })

  // 1：创建一个hello组件
  const hello = Vue.extend({
    template: `
            <div>
                <h2>你好啊! {{name}}</h2>    
  </div>
        `,
    data() {
      return {
        name: '李四'
      }
    }
  })

  // 2：全局注册组件
  Vue.component('hello', hello)

  // 创建vue实例
  new Vue({
    el: '#root',
    // 第二步： 组件注册（ 局部注册）
    components: {
      school: school,
      student: student
    },
    data: {
      msg: '你好啊！'
    }
  })

  new Vue({
    el: '#root2',
    data: {

    },
    components: {
      student,
      school
    }
  })
</script>
```

#### 048_非单文件组件使用

```html
<div id="root">
  <hello></hello>
  <h1>{{msg}}</h1>
  <hr>
  <!-- 第三步：编写组件标签 -->
  <school></school>
  <school></school>
  <hr>
  <!-- 第三步：编写组件标签 -->
  <student></student>
</div>
<hr>
<hr>
<div id="root2">
  <hello></hello>
  <student></student>
  <school></school>
</div>
<script type="text/javascript">
  Vue.config.productionTip = false

  // 第一步：创建一个school组件
  const school = Vue.extend({
    // el: '#root',
    // 组件定义时，一定不要写el配置项，因为最终所有的组件都要被一个vm管理，
    // 由vm决定服务于哪个容器。
    template: `
                <div>
                    <h2>学校名称：{{name}}</h2>
                    <h2>学校地址：{{address}}</h2> 
                    <button @click="showName">点我提示学校名</button>   
  </div>
            `,
    data() {
      return {
        name: '尚硅谷',
        address: '北京'
      }
    },
    methods: {
      showName() {
        alert(this.name)
      }
    }
  })

  // 第一步：创建一个student组件
  const student = Vue.extend({
    template: `
                <div>
                    <h2>学生名称：{{name}}</h2>
                    <h2>学生年龄：{{age}}</h2>        
  </div>
            `,
    data() {
      return {
        name: '张三',
        age: 18
      }
    }
  })

  // 1：创建一个hello组件
  const hello = Vue.extend({
    template: `
                <div>
                    <h2>你好啊! {{name}}</h2>    
  </div>
            `,
    data() {
      return {
        name: '李四'
      }
    }
  })

  // 2：全局注册组件
  Vue.component('hello', hello)

  // 创建vue实例
  new Vue({
    el: '#root',
    // 第二步： 组件注册（ 局部注册）
    components: {
      school: school,
      student: student
    },
    data: {
      msg: '你好啊！'
    }
  })

  new Vue({
    el: '#root2',
    data: {

    },
    components: {
      student,
      school
    }
  })
</script>
```

#### 049_组件的几个注意点

几个注意点：

​    1.关于组件名:

​        一个单词组成：

​            第一种写法(首字母小写)：school

​            第二种写法(首字母大写)：School

​        多个单词组成：

​            第一种写法(kebab-case命名)："my-school"

​            第二种写法(CamelCase命名)：MySchool (需要Vue脚手架支持)

​    备注：

​		1. 组件名尽可能回避HTML中已有的元素名称，例如：h2、H2都不行。

​		2. 可以使用name配置项指定组件在开发者工具中呈现的名字。

​    2.关于组件标签:

​        第一种写法：<school></school>

​        第二种写法：<school/>

​        备注：不用使用脚手架时，<school/>会导致后续组件不能渲染。

​        3.一个简写方式：

```js
 const school = Vue.extend(options) 可简写为：const school = options
```

```html
<div id="root">
        <h1>{{msg}}</h1>
        <my-school></my-school>
        <hr>
        <my-school/>
    </div>
    <script>
        Vue.config.productionTip = false

        // 传统写法：
        const s = Vue.extend({
            name: 'atguigu',
            template: `
                <div>
                    <h2>学校名称：{{name}}</h2>
                    <h2>学校地址：{{address}}</h2>    
                </div>
            `,
            data() {
                return {
                    name: '尚硅谷',
                    address: '北京'
                }
            }
        })

        // 简写：
        // const s = {
        //     name: 'atguigu',
        //     template: `
        //         <div>
        //             <h2>学校名称：{{name}}</h2>
        //             <h2>学校地址：{{address}}</h2>    
        //         </div>
        //     `,
        //     data() {
        //         return {
        //             name: '尚硅谷',
        //             address: '北京'
        //         }
        //     }
        // }

        new Vue({
            el: '#root',
            data: {
                msg: '欢迎来到尚硅谷'
            },
            components: {
                'my-school': s
            }
        })
    </script>
```

#### 050_组件的嵌套

```html
<div id="root">

</div>
<script>
  Vue.config.productionTip = false

  // 定义student组件
  const student = Vue.extend({
    template: `
                  <div>
                      <h2>学生名称：{{name}}</h2>
                      <h2>学生年龄：{{age}}</h2>    
  </div>
              `,
    data() {
      return {
        name: '张三',
        age: 18
      }
    }
  })

  // 定义school组件
  const school = Vue.extend({
    // name: 'atguigu',
    template: `
                  <div>
                      <h2>学校名称：{{name}}</h2>
                      <h2>学校地址：{{address}}</h2> 
                      <student></student>   
  </div>
              `,
    data() {
      return {
        name: '尚硅谷',
        address: '北京'
      }
    },
    components: {
      student
    }
  })

  // 定义hello组件
  const hello = Vue.extend({
    template: `
                  <h1>{{msg}}</h1>
              `,
    data() {
      return {
        msg: 'hello'
      }
    },
    components: {}
  })

  // 定义app组件
  const app = Vue.extend({
    template: `
                  <div>
                      <school></school>
                      <hello></hello>    
  </div>
              `,
    data() {
      return {}
    },
    components: {
      school,
      hello
    }
  })

  // 创建vm
  new Vue({
    template: `<app></app>`,
    el: '#root',
    data: {},
    components: {
      app
    }
  })
</script>
```

#### 051_VueComponent

关于VueComponent：

1. school组件本质是一个名为VueComponent的构造函数，且不是程序员定义的，是Vue.extend生成的。

2. 我们只需要写<school/>或<school></school>，Vue解析时会帮我们创建school组件的实例对象，

​      	即Vue帮我们执行的：new VueComponent(options)。

3. 特别注意：每次调用Vue.extend，返回的都是一个全新的VueComponent！！！！

4. 关于this指向：
   1. 组件配置中：

​      	data函数、methods中的函数、watch中的函数、computed中的函数 ，它们的this均是【VueComponent实例对象】。

​		 2.  new Vue(options)配置中：

​      	data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【Vue实例对象】。

5. VueComponent的实例对象，以后简称vc（也可称之为：组件实例对象）。

​    	Vue的实例对象，以后简称vm。vm管理着vc

```html
<div id="root">
  <school></school>
  <hello></hello>
</div>
<script>
  Vue.config.productionTip = false

  const school = Vue.extend({
    // name: 'atguigu',
    template: `
                <div>
                    <h2>学校名称：{{name}}</h2>
                    <h2>学校地址：{{address}}</h2> 
                    <button @click="showName">点我提示学校名</button>  
  </div>
            `,
    data() {
      return {
        name: '尚硅谷',
        address: '北京'
      }
    },
    methods: {
      showName() {
        alert(this.name)
      }
    }
  })

  console.log('@', school);
  /* print: ƒ VueComponent(options) {
              this._init(options);
              } */

  const test = Vue.extend({
    template: `
                <span>atguigu</span>
            `
  })

  const hello = Vue.extend({
    template: `
                <div>
                    <h2>{{msg}}</h2>
                    <test></test>  
  </div>
            `,
    data() {
      return {
        msg: 'hello'
      }
    },
    components: {
      test
    }
  })

  console.log('#', hello);

  const vm = new Vue({
    el: '#root',
    data: {

    },
    components: {
      school,
      hello
    }
  })
</script>
```

#### 052_一个重要的内置关系

1. 一个重要的内置关系：VueComponent.prototype.__proto__ === Vue.prototype

2. 为什么要有这个关系：让组件实例对象（vc）可以访问到 Vue原型上的属性、方法。



1. Vue构造函数:

Vue构造函数的prototype是Vue的原型对象

2. vm（Vue构造函数构造的实例对象）：

vm对象的原型等于其构造函数的prototype，即是Vue的prototype,即指向Vue的原型对象：vm.__proto__===Vue.prototype

3. Vue的原型对象的原型：

即Vue.prototype.__proto__等于其构造函数的prototype：Vue.prototype.__proto__===Object.prototype

4. VueComponent构造函数：

VueComponent构造函数的prototype是VueComponent的原型对象

5. vc（VueComponent构造函数构造的实例对象）：

vc对象的原型等于其构造函数的prototype，即是VueComponent的prototype,即指向VueComponent的原型对象：

6. 最后，强行改变VueComponent原型对象的.__proto__指向，让其指向从Object原型对象到Vue的原型对象

VueComponent.prototype.__proto__ === Vue.prototype

```html
<div id="root">
  <school></school>

</div>
<script>
  Vue.config.productionTip = false;
  Vue.prototype.x = 99

  // 定义school组件
  const school = Vue.extend({
    // name: 'atguigu',
    template: `
                <div>
                    <h2>学校名称：{{name}}</h2>
                    <h2>学校地址：{{address}}</h2> 
                    <button @click="printx">点我输出x</button>
  </div>
            `,
    data() {
      return {
        name: '尚硅谷',
        address: '北京',
        // x: 99
      }
    },
    methods: {
      printx() {
        console.log(this.x);
      }
    }
  })

  // 定义一个Demo构造函数
  function Demo() {
    this.a = 1;
    this.b = 2;
  }

  // 创建一个vm
  const vm = new Vue({
    el: '#root',
    data: {
      msg: '你好'
    },
    components: {
      school
    },
  })



  console.log(school.prototype.__proto__ === Vue.prototype); // print: true


  // 创建一个Demo的实例对象
  const demo = new Demo()

  console.log(vm);

  console.log(Demo.prototype); // 显式原型属性
  console.log(demo.__proto__); // 隐式原型属性

  // 程序员通过显示原型属性操作原型对象，追加一个x属性，值为99
  Demo.prototype.x = 99;
  console.log('@', Demo.prototype.x);
  console.log('#', demo.__proto__.x);
  console.log('#', demo.x);
  console.log(Demo.prototype === demo.__proto__); // print: true
</script>
```

#### 053_单文件组件

App.vue

```vue
<template>
  <div>
      <School/>
      <Student/>
  </div>
</template>
<script>
    import School from './School.vue'
    import Student from './Student.vue'
    export default {
        name: 'App',
        components: {
            School,
            Student
        }
    }   
</script>
```

School.vue

```vue
<template>
    <div class="demo">
        <h2>学校名称：{{name}}</h2>
        <h2>学校地址：{{address}}</h2> 
        <button @click="showName">点我提示学校名</button>   
    </div>
</template>
<script>
    // 组件交互相关的代码（数据、方法等）
    // 1. 分别暴露
    // export const school = Vue.extend({
    //     data() {
    //             return {
    //                 name: '尚硅谷',
    //                 address: '北京'
    //             }
    //         },
    //     methods: {
    //         showName() {
    //             alert(this.name)
    //         }
    //     }
    // })
    // export {school} // 2. 统一暴露
    // export default school // 3. 默认暴露

    // 简写：
    export default {
        name: 'School',
        data() {
                return {
                    name: '尚硅谷',
                    address: '北京'
                }
            },
        methods: {
            showName() {
                alert(this.name)
            }
        }
    }
</script>
<style>
    /* 组件的样式 */
    .demo {
        background-color: skyblue;
    }
</style>
```

Student.vue

```vue
<template>
    <div>
        <h2>学生姓名：{{name}}</h2>
        <h2>学生年龄：{{age}}</h2> 
        <button @click="showName">点我提示学生名</button>   
    </div>
</template>
<script>
    export default {
        name: 'Student',
        data() {
            return {
                name: '张三',
                age: 18
            }
        },
        methods: {
            showName() {
                alert(this.name)
            }
        },
    }
</script>
```

index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>

  <body>
    <div id="root">
      <App></App>
    </div>
    <script src="../js/vue.js"></script>
    <script src="./main.js"></script>
  </body>
</html>
```

main.js

```js
import App from './App.vue'
new Vue({
    el: '#root',
    components: {
        App
    }
})
```

#### 054_ref属性

1. 被用来给元素或子组件注册引用信息（id的替代者）

2. 应用在html标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象（vc）

3. 使用方式：
   1. 打标识
   
   ```html
   <h1 ref="xxx">...</h1>
   // 或者
   <School ref=""></School>
   ```
   
   2. 获取
   
   ```vue
   this.$refs.xxx
   ```

#### 055_props配置

功能：让组件接受外部传过来的数据

1. 传递数据

```html
<Demo name="xxx"/>
```

2. 接收数据

   1. 第一种（只接收）

      ```vue
      props: ['name']
      ```

   2. 第二种（限制类型）

      ```vue
      props: {
      	name: String
      }
      ```

   3. 第三种（限制类型、限制必要性、指定默认值）

      ```vue
      props: {
      	name: {
      		type: String,
      		required: true,
      		default: '老王'
      	}
      }
      ```

备注：props是只读的，Vue底层会监测你对props的修改，如果进行了修改，就会发出警告，若业务需求确定需要修改，那么请复制props的内容到data中一份，然后去修改data中的数据（二者名不能一样）

#### 056_mixin（混入）

功能：可以把多个组件共用的配置提取成一个混入对象

使用方式：

 1. 第一步：定义混合，例如：

    ```vue
    {
    	data() {...},
    	methods: {...},
    	...
    }
    ```

 2. 第二步：使用混入，例如：

    1. 全局混入：

       ```vue
       Vue.mixin(xxx)
       ```

    2. 局部混入：

       ```vue
       mixins: [xxx, yyy]
       ```

#### 057_插件

功能：用于增强Vue

本质：包含install方法的一个对象，install的第一个参数是Vue，第二个以后的参数是插件使用者传递的数据。

1. 定义插件：

   ```js
   Object.install = function (Vue, option) {
   	// 1. Add global filter
   	Vue.filter(...)
   	
   	// 2. Add global directive
   	Vue.directive(...)
   	
   	// 3. Set global mixin
   	Vue.mixin(...)
   	
   	// 4. Add instance method
   	Vue.prototype.$myMethod = function() {...}
   	Vue.prototype.$myProperty = xxx
   }
   ```

2. 使用插件：

   ```js
   Vue.use(plugin, param1, param2, ...)
   ```

   

#### 058_scoped样式

作用：让样式在局部生效，防止冲突

写法：<style scoped>	

#### 059_TodoList案例

##### 源码：

###### components/MyFooter.vue

```vue
<template>
    <div class="todo-footer" v-show="total">
        <label>
            <!-- <input type="checkbox" :checked="isAll" @change="checkAll"/> -->
            <input type="checkbox" v-model="isAll"/>
        </label>
        <span>
            <span>已完成{{doneTotal}}</span> / 全部{{total}}
        </span>
        <button class="btn btn-danger" @click="clear">清除已完成任务</button>
    </div>
</template>

<script>
    export default {
        name: 'MyFooter',
        props: [
            'todos',
            'checkAllTodo',
            'clearAllTodo'
        ],
        computed: {
            total() {
                return this.todos.length
            },
            doneTotal() {
                // idea 1:
                /* let count = 0
                this.todos.forEach((todo) => {
                    if(todo.done) {
                        count++
                    }
                });
                return count */

                // idea 2:
                return this.todos.reduce((pre, todo) => pre + (todo.done ? 1 : 0), 0)
                // const x = this.todos.reduce((pre, currentObj) => {
                //     console.log('@', pre);
                //     return pre + (currentObj.done ? 1 : 0)
                // }, 0)
                // console.log(x);
            },
            isAll: {
                get() {
                    return this.doneTotal === this.total && this.total > 0
                },
                set(val) {
                    // console.log(val);
                    this.checkAllTodo(val)
                }
            }
        },
        methods: {
            checkAll(e) {
                // console.log(e.target.checked);
                console.log(e.target.checked);
                this.checkAllTodo(e.target.checked)
            },
            clear() {
                this.clearAllTodo()
            }
        },
    }
</script>

<style scoped>
    /*footer*/
    .todo-footer {
        height: 40px;
        line-height: 40px;
        padding-left: 6px;
        margin-top: 5px;
    }

    .todo-footer label {
        display: inline-block;
        margin-right: 20px;
        cursor: pointer;
    }

    .todo-footer label input {
        position: relative;
        top: -1px;
        vertical-align: middle;
        margin-right: 5px;
    }

    .todo-footer button {
        float: right;
        margin-top: 5px;
    }
</style>
```

###### component/MyHeader.vue

```vue
<template>
    <div class="todo-header">
        <input type="text" placeholder="请输入你的任务名称，按回车键确认" v-model="title" @keyup.enter="add"/>
    </div>
</template>

<script>
    import {nanoid} from 'nanoid'
    export default {
        name: 'MyHeader',
        data() {
            return {
                title: ''
            }
        },
        props: ['addTodo'],
        methods: {
            add() {
                // 将用户的输入包装成为一个todo对象
                const todoObj = {
                    id: nanoid(),
                    title: this.title,
                    done: false
                }
                if(!this.title.trim()) {
                    return alert('输入不能为空，请重新输入')
                }
                console.log(todoObj);
                // console.log(this.title);
                this.addTodo(todoObj) 
                this.title = ''
            }
        },
    }
</script>

<style scoped>
    /*header*/
    .todo-header input {
        width: 560px;
        height: 28px;
        font-size: 14px;
        border: 1px solid #ccc;
        border-radius: 4px;
        padding: 4px 7px;
    }

    .todo-header input:focus {
        outline: none;
        border-color: rgba(82, 168, 236, 0.8);
        box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
    }
</style>
```

###### component/MyItem.vue

```vue
<template>
    <li>
        <label>
            <input type="checkbox" :checked="todo.done" @change="handleCheck(todo.id)"/>
            <!-- 如下代码也能实现功能，但是不推荐使用，因为违反规则，因为修改了props -->
            <!-- <input type="checkbox" v-model="todo.done"/> -->
            <span>{{todo.title}}</span>
        </label>
        <button class="btn btn-danger" @click="handleDelete(todo.id)">删除</button>
    </li>
</template>

<script>
    export default {
        name: 'MyItem',
        props: [
            'todo',
            'checkTodo',
            'deleteTodo'
        ],
        // mounted() {
        //     console.log(this.todo);
        // },  
        methods: {
            // 勾选 or 取消勾选
            handleCheck(id) {
                // console.log(id);
                this.checkTodo(id)
            },
            // 删除
            handleDelete(id) {
                // confirm() 弹出提示框，会根据布尔值判断是或否来满足用户的需求
                if(confirm('确定删除吗？')) {
                    // console.log(id);
                    this.deleteTodo(id)
                }
            }
        },
    }
</script>

<style scoped>
    /*item*/
    li {
        list-style: none;
        height: 36px;
        line-height: 36px;
        padding: 0 5px;
        border-bottom: 1px solid #ddd;
    }

    li label {
        float: left;
        cursor: pointer;
    }

    li label li input {
        vertical-align: middle;
        margin-right: 6px;
        position: relative;
    top: -1px;
    }

    li button {
        float: right;
        display: none;
        margin-top: 3px;
    }

    li:before {
        content: initial;
    }

    li:last-child {
        border-bottom: none;
    }

    li:hover{
        background-color: #ddd;
    }

    li:hover button{
        display: block;
    }
</style>
```

###### component/MyList.vue

```vue
<template>
    <div>
        <ul class="todo-main">
            <MyItem v-for="todoObj in todos" 
                :key="todoObj.id" 
                :todo="todoObj" 
                :checkTodo="checkTodo"
                :deleteTodo="deleteTodo"
            />
        </ul>
    </div>
</template>

<script>
    import MyItem from './MyItem.vue'
    export default {
        name: 'MyList',
        components: {
            MyItem
        },
        props: [
            'todos', 
            'checkTodo', 
            'deleteTodo'
        ]
    }
</script>

<style scoped>
    /*main*/
    .todo-main {
        margin-left: 0px;
        border: 1px solid #ddd;
        border-radius: 2px;
        padding: 0px;
    }

    .todo-empty {
        height: 40px;
        line-height: 40px;
        border: 1px solid #ddd;
        border-radius: 2px;
        padding-left: 5px;
        margin-top: 10px;
    }
</style>
```

###### App.vue

```vue
<template>
<div id="root">
  <div class="todo-container">
    <div class="todo-wrap">
      <MyHeader :addTodo="addTodo"/>
      <MyList :todos="todos" 
              :checkTodo="checkTodo"
              :deleteTodo="deleteTodo"
              />
      <MyFooter :todos="todos" :checkAllTodo="checkAllTodo" :clearAllTodo="clearAllTodo"/>
  </div>
  </div>
  </div>
</template>

<script>
  import MyHeader from './components/MyHeader.vue'
  import MyFooter from './components/MyFooter.vue'
  import MyList from './components/MyList.vue'
  export default {
    name: 'App',
    components: {
      MyHeader,
      MyFooter,
      MyList
    },
    data() {
      return {
        todos: JSON.parse(localStorage.getItem('todos')) || []
      }
    },
    methods: {
      // 添加一个todo
      addTodo(todoObj) {
        console.log('App组件收到了数据', todoObj);
        this.todos.unshift(todoObj)
      },
      // 勾选or取消勾选一个todo
      checkTodo(id) {
        this.todos.forEach((todo) => {
          if(todo.id === id) {
            todo.done = !todo.done
          }
        });
      },
      // 删除一个todo
      deleteTodo(id) {
        this.todos = this.todos.filter(todo => {
          return todo.id !== id
        })
      },
      // 全选 or 取消全选
      checkAllTodo(done) {
        this.todos.forEach(todo => {
          todo.done = done
        })
      },
      clearAllTodo() {
        this.todos = this.todos.filter((todo) => {
          return !todo.done
        })
      }

    },
    watch: {
      todos: {
        deep: true,
        handler(value) {
          localStorage.setItem('todos', JSON.stringify(value)) 
        }
      }
    }
  }
</script>

<style>
  /* base */
  body {
    background: #fff;
  }
  .btn {
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
    border-radius: 4px;
  }
  .btn-danger {
    color: #fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
  }
  .btn-danger:hover {
    color: #fff;
    background-color: #bd362f;
  }
  .btn:focus {
    outline: none;
  }
  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>
```

###### main.js

```js
import Vue from 'vue'
import App from './App.vue'
Vue.config.productionTip = false

new Vue({
    el: '#app',
    render: h => h(App)
})
```

###### vue.config.js

```js
module.exports = {
    pages: {
        index: {
            entry: 'src/main.js'
        },
    },
    lintOnSave: false
}
```

##### 总结：

1. 组件化编码流程：
   1. 拆分静态组件：组件要按照功能点拆分，命名不要与html元素冲突
   2. 实现动态组件：考虑好数据的存放位置，数据是一个组件在用，还是一堆组件在用：
      1. 一个组件在用：放在组件自身即可
      2. 一堆组件在用：放在他们共用的父组件上（状态提升）
   3. 实现交互：从绑定事件开始
2. props适用于：
   1. 父组件===>子组件 通信
   2. 子组件===>父组件 通信 （要求父先给子一个函数）

3. 使用v-model时要切记：v-model绑定的值不能是props传过来的值，因为props是不可以修改的
4. props传过来的若是对象类型的值，修对象中的属性时Vue不会报错，但不推荐这么做

#### 060_浏览器本地存储

1. 存储内容大小一般支持5MB左右（不同浏览器可能还不一样）

2. 浏览器端通过 Window.sessionStorage 和 Window.localStorage 属性来实现本地存储机制。

3. 相关API

   1. ```xxxxxStorage.setItem('key', 'value');```

      ​	该方法接受一个键和值作为参数，会把键值对添加到存储中，如果键名存在，则更新其对应的值。

      ​	值为字符串，如果存入的值为对象，则将其转换为字符串后存入

   2. ```xxxxxStorage.getItem('person');```

      ​    该方法接受一个键名作为参数，返回键名对应的值。对象转字符串后存入，取出后需将其重新转化为对象

   3. ```xxxxxStorage.removeItem('key');```

      ​    该方法接受一个键名作为参数，并把该键名从存储中删除。

   4. ``` xxxxxStorage.clear()```

      ​    该方法会清空存储中的所有数据。

4. 备注：

   1. SessionStorage存储的内容会随着浏览器窗口关闭而消失。
   2. LocalStorage存储的内容，需要手动清除才会消失。
   3. ```xxxxxStorage.getItem(xxx)```如果xxx对应的value获取不到，那么getItem的返回值是null。
   4. ```JSON.parse(null)```的结果依然是null。
   5. 这两者的API用法一致

```html
<h2>sessionStorage</h2>
<button onclick="saveData()">点我保存一个数据</button>
<button onclick="readData()">点我读取一个数据</button>
<button onclick="deleteData()">点我删除一个数据</button>
<button onclick="clearData()">点我清空一个数据</button>

<script>
  let p = {
    name: '张三',
    age: 18
  }

  function saveData() {
    sessionStorage.setItem('msg', 'hello!!')
    sessionStorage.setItem('msg2', 666)
    sessionStorage.setItem('person', JSON.stringify(p))
  }

  function readData() {
    console.log(sessionStorage.getItem('msg'));
    const result = sessionStorage.getItem('person')
    console.log(JSON.parse(result));
    console.log(sessionStorage.getItem('msg2'));
  }

  function deleteData() {
    sessionStorage.removeItem('msg2')
  }

  function clearData() {
    sessionStorage.clear()
  }
</script>
```

```html
<h2>LocalStorage</h2>
<button onclick="saveData()">点我保存一个数据</button>
<button onclick="readData()">点我读取一个数据</button>
<button onclick="deleteData()">点我删除一个数据</button>
<button onclick="clearData()">点我清空一个数据</button>

<script>
  let p = {
    name: '张三',
    age: 18
  }

  function saveData() {
    localStorage.setItem('msg', 'hello!!')
    localStorage.setItem('msg2', 666)
    localStorage.setItem('person', JSON.stringify(p))
  }

  function readData() {
    console.log(localStorage.getItem('msg'));
    const result = localStorage.getItem('person')
    console.log(JSON.parse(result));
    console.log(localStorage.getItem('msg3'));
  }

  function deleteData() {
    localStorage.removeItem('msg2')
  }

  function clearData() {
    localStorage.clear()
  }
</script>
```

#### 061_组件的自定义事件——绑定

App.vue

```vue
<template>
<div class="app">
  <h1>{{msg}}</h1>
  <!-- 通过父组件给子组件绑定一个自定义事件实现：子给父传递数据 -->
  <!-- <Student v-on:atguigu="getStudentName"/> -->
  <Student @atguigu.once="getStudentName"/>

  <!-- 通过父组件给子组件传递函数类型的props实现：子给父传递数据（第一种写法，使用@或v-on） -->
  <Student ref="student"/>
  <hr>
  <!-- 通过父组件给子组件传递函数类型的props实现：子给父传递数据（第二种写法，使用ref） -->
  <School :getSchoolName="getSchoolName"/>
  </div>
</template>

<script>
  import School from './components/School.vue'
  import Student from './components/Student.vue'
  export default {
    name: 'App',
    components: {
      Student,
      School
    },
    data() {
      return {
        msg: '你好啊'
      }
    },
    methods: {
      getSchoolName(name) {
        console.log('App收到了学校名：', name);
      },
      getStudentName(name, ...param) {
        console.log('App收到了学生名：', name, param);
      }
    },
    mounted() {
      // this.$refs.student.$on('atguigu', this.getStudentName) // 绑定自定义事件

      // setTimeout(()=>{
      //     this.$refs.student.$on('atguigu', this.getStudentName)
      // },3000)

      this.$refs.student.$once('atguigu', this.getStudentName) // 绑定自定义事件（一次性）
    },
  }
</script>
<style scoped> 
  .app{
    background-color: gray;
    padding: 5px;
  }
</style>
```

School.vue

```html
<template>
  <div class="school">
    <h2>学校名称：{{name}}</h2>
    <h2>学校地址：{{address}}</h2>
    <button @click="sendSchoolName">把学校名给App</button>
  </div>
</template>

<script>
  export default {
    name: 'Student',
    props: ['getSchoolName'],
    data() {
      return {
        name: '尚硅谷atguigu',
        address: '北京',
      }
    },
    methods: {
      sendSchoolName() {
        this.getSchoolName(this.name)
      }
    },
  }
</script>

<style scoped>
  .school {
    background-color: skyblue;
    padding: 5px;
    margin-top: 30px;
  }

</style>
```

Student.vue

```vue
<template>
<div class="student">
  <h2>学生姓名：{{name}}</h2>
  <h2>学生性别：{{sex}}</h2>
  <button @click="sendStudentName">把学生名给App</button>
  </div>
</template>

<script>
  export default {
    name: 'Student',
    data() {
      return {
        name: '张三',
        sex: '男'
      }
    },
    methods: {
      sendStudentName() {
        // 触发Student组件的实例身上的atguigu事件
        this.$emit('atguigu', this.name, 777, 888, 999)
      }
    },
  }
</script>

<style lang="less">
  .student {
    background-color: orange;
    padding: 5px;
  }
</style>
```

#### 062_组件的自定义事件——解绑

App.vue

```vue
<template>
<div class="app">
  <h1>{{msg}}，学生名是：{{studentName}}</h1>
  <!-- 通过父组件给子组件绑定一个自定义事件实现：子给父传递数据 -->
  <!-- <Student v-on:atguigu="getStudentName"/> -->
  <!-- <Student @atguigu="getStudentName"  @demo="m1"/> -->

  <!-- 通过父组件给子组件传递函数类型的props实现：子给父传递数据（第一种写法，使用@或v-on） -->
  <Student ref="student" @click.native="show"/>
  <hr>
  <!-- 通过父组件给子组件传递函数类型的props实现：子给父传递数据（第二种写法，使用ref） -->
  <School :getSchoolName="getSchoolName"/>
  </div>
</template>

<script>
  import School from './components/School.vue'
  import Student from './components/Student.vue'
  export default {
    name: 'App',
    components: {
      Student,
      School
    },
    data() {
      return {
        msg: '你好啊',
        studentName: ''
      }
    },
    methods: {
      getSchoolName(name) {
        console.log('App收到了学校名：', name);
      },
      getStudentName(name, ...param) {
        console.log('App收到了学生名：', name, param);
        this.studentName = name
      },
      m1() {
        console.log('demo事件被触发了');
      },
      show() {
        alert(123)
      }
    },
    mounted() {
      this.$refs.student.$on('atguigu', this.getStudentName)    // 绑定自定义事件
      // this.$refs.student.$on('atguigu', ((name, param)=>{
      //    console.log('App收到了学生名：', name, param); 
      //    this.studentName = name
      // })) 

      // setTimeout(()=>{
      //     this.$refs.student.$on('atguigu', this.getStudentName)
      // },3000)

      // this.$refs.student.$once('atguigu', this.getStudentName) // 绑定自定义事件（一次性）
    },
  }
</script>
<style scoped> 
  .app{
    background-color: gray;
    padding: 5px;
  }
</style>
```

Student.vue

```vue
<template>
  <div class="student">
      <h2>学生姓名：{{name}}</h2>
      <h2>学生性别：{{sex}}</h2>
      <h2>当前求和为{{number}}</h2>
      <button @click="add">点我number++</button>
      <button @click="sendStudentName">把学生名给App</button>
      <button @click="unbind">解绑atguigu事件</button>
      <button @click="death">销毁当前Student组件的实例对象(vc)</button>
  </div>
</template>

<script>
    export default {
        name: 'Student',
        data() {
            return {
                name: '张三',
                sex: '男',
                number: 0,

            }
        },
        methods: {
            add() {
                console.log('add回调被调用了');
                this.number++
            },
            sendStudentName() {
                // 触发Student组件的实例身上的atguigu事件
                this.$emit('atguigu', this.name, 777, 888, 999)
                // this.$emit('demo')
                // this.$emit('click')
            },
            unbind() {
                this.$off('atguigu')    // 只适合解绑一个自定义事件
                // this.$off(['atguigu', 'demo'])  // 解绑多个自定义事件
                // this.$off() // 解绑所有自定义事件
            },
            death() {
                this.$destroy() // 销毁了当前Student组件的实例，销毁后所有Student实例的自定义事件全部不奏效
            }
        },
    }
</script>

<style lang="less">
    .student {
        background-color: orange;
        padding: 5px;
    }
</style>
```

School.vue

```vue
<template>
<div class="school">
  <h2>学校名称：{{name}}</h2>
  <h2>学校地址：{{address}}</h2>
  <button @click="sendSchoolName">把学校名给App</button>
  </div>
</template>

<script>
  export default {
    name: 'Student',
    props: ['getSchoolName'],
    data() {
      return {
        name: '尚硅谷atguigu',
        address: '北京',
      }
    },
    methods: {
      sendSchoolName() {
        this.getSchoolName(this.name)
      }
    },
  }
</script>

<style scoped>
  .school {
    background-color: skyblue;
    padding: 5px;
    margin-top: 30px;
  }

</style>
```

main.js

```js
import Vue from 'vue'
import App from './App.vue'
Vue.config.productionTip = false
new Vue({
  el: '#app',
  render: h => h(App),
  // 验证子组件是否被销毁
  // mounted() {
  //     setTimeout(() => {
  //         this.$destroy()
  //     }, 1000)
  // },
})
```

#### 063_总结自定义组件

1. 一种组件间通信的方式，适用于：**<span style='color: red;font-size:16px;'> 子组件 ===> 父组件 </span> **

2. 使用场景：A是父组件，B是子组件，B想给A传数据，那么就要在A中给B绑定自定义事件（<span style='color: red;font-size:16px;'> 事件的回调在A中 </span> ）。

3. 绑定自定义事件：

   1. 第一种方式，在父组件中：`<Demo @atguigu="test"/>`  或 `<Demo v-on:atguigu="test"/>`

   2. 第二种方式，在父组件中：

      ```vue
      <Demo ref="demo"/>
      ......
      mounted(){
         this.$refs.xxx.$on('atguigu',this.test)
      }
      ```

   3. 若想让自定义事件只能触发一次，可以使用`once`修饰符，或`$once`方法。

4. 触发自定义事件：`this.$emit('atguigu',数据)`

5. 解绑自定义事件`this.$off('atguigu')`

6. 组件上也可以绑定原生DOM事件，需要使用`native`修饰符,否则会被当成自定义事件。

7. 注意：通过`this.$refs.xxx.$on('atguigu',回调)`绑定自定义事件时，回调<span style='color: red;font-size:16px;'> <span style='color: red;font-size:16px;'> 事件的回调在A中 </span>  </span> ，否则this指向会出问题！
