# JavaScript 变量

## 目录
1. [变量基础](#变量基础)
2. [声明方式对比](#声明方式对比)
3. [命名规范](#命名规范)
4. [最佳实践](#最佳实践)

---

## 变量基础

### 什么是变量？
变量是用来存储数据的容器，就像给数据贴上标签，方便后续使用。

### 基本语法
```javascript
let 变量名 = 值;
```

---

## 声明方式对比

### `var` - 不推荐使用

```javascript
var name = "张三";
var age = 25;
```

**缺点：**
- 函数作用域（整个函数内可见）或全局作用域（整个文件/全局都可见），容易造成变量污染
- 可以重复声明，容易出错
- 存在变量提升，行为不直观

### `let` - 推荐使用

```javascript
let userName = "李四";
let userAge = 30;

// 可以修改
userAge = 31;
```

**优点：**
- 块级作用域 `{}`
- 不能重复声明
- 值可以修改

**使用场景：** 需要改变的变量

### `const` - 推荐使用

```javascript
const PI = 3.14159;
const API_URL = "https://api.example.com";
```

**优点：**
- 块级作用域 `{}`
- 声明后不能修改（引用不变）
- 代码更安全、意图更明确

**使用场景：** 不需要改变的值

**特殊说明：** 对象和数组的内容可以修改
```javascript
const user = { name: "王五" };
user.name = "赵六";  // 可以修改属性
user.age = 25;       // 可以添加属性

const colors = ["red", "blue"];
colors.push("green");  // 可以修改数组内容
```

---

## 命名规范

### 基本规则（强制）

| 规则 | 说明 | 示例 |
|------|------|------|
| 允许的字符 | 字母、数字、`_`、`# JavaScript 变量完全指南
| 不能数字开头 | 首字符不能是数字 | `123user` |
| 不能用关键字 | 不能使用保留字 | `let`、`const`、`if` |
| 区分大小写 | `name` ≠ `Name` | `userName` vs `UserName` |
| 不能有空格 | 单词间不能空格 | `user name` |

### 命名风格（推荐）

#### 1. 驼峰命名法 `camelCase` （小驼峰）
**用途：** 变量、函数名

```javascript
let firstName = "张三";
let userAge = 25;
let isLoggedIn = true;

function getUserInfo() {}
function calculateTotalPrice() {}
```

#### 2. 帕斯卡命名法 `PascalCase` （大驼峰）
**用途：** 类名、构造函数

```javascript
class UserAccount {}
class ShoppingCart {}
class ProductManager {}
```

#### 3. 全大写下划线 `UPPER_SNAKE_CASE`
**用途：** 常量

```javascript
const MAX_USER_COUNT = 1000;
const API_BASE_URL = "https://api.example.com";
const DEFAULT_TIMEOUT = 5000;
```

#### 4. 下划线前缀 `_variable`
**用途：** 私有变量（约定）

```javascript
let _privateData = "内部使用";
let _internalCounter = 0;

class User {
    constructor() {
        this._id = 123;  // 表示私有属性
    }
}
```

### 语义化命名原则

#### 糟糕的命名
```javascript
let a = 25;           // 完全不知道是什么
let x = "张三";       // 没有意义
let temp = true;      // 太模糊
let data = [];        // 太泛化
```

#### 优秀的命名
```javascript
let userAge = 25;           // 清晰明了
let userName = "张三";      // 一目了然
let isAuthenticated = true; // 表意准确
let productList = [];       // 描述具体
```

### 常用命名模式

#### 布尔值
```javascript
// 使用 is、has、can、should 等前缀
let isVisible = true;
let hasPermission = false;
let canEdit = true;
let shouldUpdate = false;
```

#### 数组/列表
```javascript
// 使用复数形式或 List 后缀
let users = ["张三", "李四"];
let productList = [];
let itemArray = [];
```

#### 函数命名
```javascript
// 使用动词开头
function getUser() {}          // 获取
function setUserName() {}      // 设置
function calculateTotal() {}   // 计算
function validateEmail() {}    // 验证
function deleteProduct() {}    // 删除
function updateProfile() {}    // 更新
```

#### 事件处理函数
```javascript
// 使用 handle 或 on 前缀
function handleClick() {}
function handleSubmit() {}
function onUserLogin() {}
function onDataLoad() {}
```

#### 数字相关
```javascript
// 明确表示数量、索引、ID等
let userCount = 10;      // 数量
let maxLength = 100;     // 最大值
let currentIndex = 0;    // 索引
let userId = 12345;      // ID
let itemPrice = 99.99;   // 价格
```

---

## 最佳实践

### 1. 优先使用 `const`，需要修改才用 `let`
```javascript
// 推荐
const maxSize = 100;
const apiKey = "abc123";

// 只在需要重新赋值时用 let
let counter = 0;
counter++;
```

### 2. 一行一个变量
```javascript
// 不推荐
let a = 1, b = 2, c = 3;

// 推荐
let firstName = "张";
let lastName = "三";
let fullName = firstName + lastName;
```

### 3. 变量声明靠近使用处
```javascript
// 推荐
function processUser() {
    // 在需要时才声明
    const userId = getUserId();
    
    // 使用 userId...
    
    const userName = getUserName();
    
    // 使用 userName...
}
```

### 4. 避免魔法数字
```javascript
// 不推荐
if (user.age > 18) {}

// 推荐：使用常量让代码更易理解
const ADULT_AGE = 18;
if (user.age > ADULT_AGE) {}
```

### 5. 避免使用缩写（除非广为人知）
```javascript
// 不清晰
let usrNm = "张三";
let cnt = 10;

// 清晰
let userName = "张三";
let count = 10;

// 可接受的缩写
let id = 123;
let url = "https://example.com";
let html = "<div></div>";
```

---

## 记忆要点

1. 默认用 `const`，需要修改才用 `let`，避免用 `var`
2. 驼峰命名法用于变量和函数，帕斯卡命名法用于类名，全大写下划线用于常量
3. 名字要有意义，让代码自解释
4. 保持一致性，遵循团队规范

---