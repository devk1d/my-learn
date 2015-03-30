1. 浮点陷阱

     例子：
     
          0.1 + 0.2 = 0.30000000000000004
          3 * 0.3 = 0.8999999999999999
          0.1 + 0.3 = 0.4

     解决：
     
          (0.1*10 + 0.2*10)/10 = 0.3

2. 隐式强制类型转换

      例子：
      
          3 + true = 4
          "2" +3 = "23"
          2 + "3" = "23"

     解决：
     
        转换为同类型进行运算， 例如：
             JSON = {a_num: "1", b_num: "2"}，要进行 a_num + b_num 加运算， 
        应写：
             Number(a_num) + Number(b_num)

     提示：
     
          js中有7种假值： false、0、-0、""、NaN、null、undefinded，其他都为真值，尤其："0"
          测试一个值是否为未定义的值，应该使用typeof 或者 undefined 进行比较而不是使用真值运算

3. 尽量避免全局变量

        优秀的工程师会不断的留意程序的结构、持续地归类相关的功能以及分离不相关的组件，并将这些行为作为编程过程的一部分。
     提示：
     
     
        请尤其注意dom节点的获取、CSS命名！

4. 熟练掌握闭包和原型链

     JS允许你引用在当前函数外定义的变量
     闭包可以更新外部变量的值

         var func = function() {
              var v = 1;
              var f1 = function() ｛
                   var f2 = function() {
                        return v;
                   }
                   return f2;
              };
              return f1;
         }
    
         func()()() // undefined or 1?

5. 理解变量的声明

     代码中的变量声明会被隐式的提升到封闭的函数顶部
     避免重复声明
     使用立即调用函数表达式创建局部变量：
     
          var test = 1;
          
          (function() {
               var test = 2;
               console.log(test); // 2
          })();
          
          console.log(test); // 1

6. 理解函数的函数调用、方法调用、构造函数调用之间的不同
     
     1). 函数调用
     
          function hello() {
               return "Hello, " + this.username;
          };
          hello(); //hello, undefined

     2). 方法调用
     
          var obj = {
               hello: function() {
                    return "Hello, " + this.username
               },
               uesrname: "weixiang"
          };
          obj.hello(); //hello, weixiang
          var obj2 = {
               hello: obj.hello,
               username: "xiaowu"
          };
          obj2.hello(); // ?
          
     通常，通过某个对象调用方法，将查找该方法并将该对象作为该方法的接收者。

     3). 构造函数调用
          
          function User(username, password) {
               this.username = username;
               this.password = password;
          }
          
          var u = new User("test", "123456");
          u.username = "test"

     构造函数需要通过 new 运算符调用，并产生一个新的对象作为其接收者。

7. 熟练掌握高阶函数
     
     1). 高阶函数是那些将函数作为参数或返回值的函数。
               
          function compare(x, y) {
               if(x<y) {
                    return -1;
               }
               if(x>y) {
                    return 1;
               }
               return 0;
          }
          [3, 5, 1, 4, 9].sort(compare);
          
          [3, 5, 1, 4, 9].sort(function() {
               if(x<y) {
                    return -1;
               }
               if(x>y) {
                    return 1;
               }
               return 0;
          });
                    
     2). 熟悉掌握现有库中的高阶函数。
                    
          var names = ["weixiang", "xiangwo", "chengle"];
          var uppers = names.map(function(name) {
               return name.toUpperCase();
          });
                    
     3). 学会发现可以被高阶函数所取代的常见的编码模式。
     
          $.each(data, function(i, item) {
               // code...
          });
          
          //而不是
          for(var i=0; i<data.length; i++) {
               // code...
          }
 
8. 使用call和apply转换接收者（this）

          function hello(msg) {
               return "Hello, " + this.name + ", " + msg;
          }
          
          var msg = "Good morning";
          var obj = {
               name: "weixiang"
          };
          
          hello.call(obj, msg);  // Hello, weixiang, Good morning
          hello.apply(obj, [msg]);  // Hello, weixiang, Good morning

9. 在原型中储存方法

     将方法储存于原型中优于储存在实例对象中：

          // 1
          function User(username, password) {
               this.username = username;
               this.password = password;

               this.checkUsername = function(username) {
                    return this.username === username;
               }
          }
          
          // u1: username, password, checkUsername
          // u1.prototype: {}
          var u1 = new User(/*...*/);

          // 2
          function User() {
               this.username = username;
               this.password = password;
          }
          User.prototype = {
               checkUsername: function(username) {
                    return this.username === username;
               }
          }
          
          // u1: uesrname, password
          // u1.prototype: checkUsername
          var u1 = new User(/*...*/);

     
     提示：切勿共享可变数据
 



其他：
     1. 避免使用 eval
     2. 灵活使用 arguments
      
          1). arguments.length, arguments[0]
          2). var args = [].slice.call(arguments);  // 安全转为数组
          3).  





