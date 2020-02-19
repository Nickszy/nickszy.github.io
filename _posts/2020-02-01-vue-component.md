---
layout: post
title:  vue-组件
categories: 
  - 笔记
tags:
  - vue
excerpt: 初次尝试建立一个vue项目，感觉vue的写好非常像python 
comments: true
---

### 设计一个组件

### 将填入数据与 model 对应

1. 在 form 中加入 :model=「loginForm」  

```html
<el-form :model="loginForm" class="login_form">
```


```js
export default {
    data() {
        return {
            loginForm:{
                uname:'',
                pwd:''
            },
        }
   }
```

2. 在 data 中 加入 data

```js
export default {
    data() {
        return {
            loginForm:{
                uname:'',
                pwd:''
            },
        }
   }
```

3. 在 input 中加入 model 对应的 key

```html
<el-input v-model="loginForm.uname" prefix-icon="el-icon-user"></el-input>
```

### 给输入的字段设置规则

1. 在 form 中加入 :model=「loginForm」    

```
 <el-form :model="loginForm" :rules="rules" class="login_form">
```

2. 在 data 中 加入 data

```js
export default {
    data() {
        return {
            loginForm:{
                uname:'',
                pwd:''
            },
            rules:{

                uname:[

                    { required: true, message: '请输入昵称', trigger: 'blur' },

                    { min: 3, message: '长度在 3 个字符以上', trigger: 'blur' }

                ],

                pwd:[

                    { min: 3, message: '长度在 3 个字符以上', trigger: 'blur' }

                ]

            }
        }
   }
```

3. 在 input 中加入 model 对应的 key

```html
<el-input v-model="loginForm.uname" prefix-icon="el-icon-user"></el-input>
```
