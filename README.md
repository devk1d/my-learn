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
     
        转换为同类型进行运算，
          例如：JSON: {a_num: "1", b_num: "2"}，要进行 a_num + b_num 加运算， 应写：Number(a_num) + Number(b_num)

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

6. 理解绑定与赋值的区别
     
     


7.





