#### 1.unshift() 方法

​	将新项添加到数组起始位置 [参考链接](https://www.runoob.com/jsref/jsref-unshift.html)

```javascript
			methods: {
					onSubmit() {
						// console.log(this.todo);
						fetch("http://jsonplaceholder.typicode.com/todos", {
							method: "POST",
							body: JSON.stringify(this.todo), //用于将 JavaScript 值转换为 JSON 字符串。
							headers: {
								'Content-Type': 'application/json'
							}
						}).then(res => {
							return res.json();
						}).then(todo => {
							// console.log(todo);
							this.todos.unshift(todo);
						}); 
					}
				},
                    
   var fruits = ["Banana", "Orange", "Apple", "Mango"];
   fruits.unshift("Lemon","Pineapple");
   //输出结果
   Lemon,Pineapple,Banana,Orange,Apple,Mango

```



#### 2.pop方法

pop() 方法用于删除数组的最后一个元素并返回删除的元素。

```javascript
  data() {
    return {
      // users: ["小猪佩奇", "大象艾美莉", "小羊苏西"],
      // users: [
      //   { name: "小猪佩奇", age: 28, show: false },
      //   { name: "大象艾美莉", age: 22, show: false },
      //   { name: "小羊苏西", age: 21, show: false },
      // ],
    };
  },
  methods:{
    deleteUser(){
      this.users.pop();
    }
  }

var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.pop();
//输出结果
Banana,Orange,Apple
```



#### 3.filter方法与push方法

filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。
push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度。

```javascript
//根据isHave的值判断订单列表中是否已经有此商品
	if (isHave) {
        //存在就进行数量添加
        let arr = this.tableData.filter((o) => o.goodsId == goods.goodsId);
        arr[0].count++;
        //console.log(arr);
      } else {
        //不存在就推入数组
        let newGoods = { goodsId: goods.goodsId, goodsName: goods.goodsName, price: goods.price, count: 1 };
        this.tableData.push(newGoods);
      }


var ages = [32, 33, 16, 40]; 
function checkAdult(age) {
    return age >= 18;
} 
function myFunction() {
    document.getElementById("demo").innerHTML = ages.filter(checkAdult);
}
//输出结果
32,33,40

var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.push("Kiwi")
//输出结果
Banana,Orange,Apple,Mango,Kiwi
```

