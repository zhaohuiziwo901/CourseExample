# 自己动手写MVC框架
本人2015年接触Angular，从2016年2月开始研究Angular1源码，中间经历了极其曲折的过程，一直希望能临摹一个，因此在这里虽说是自己动手写，其实思想基本上借鉴了Angular的思路，其中也加入了一些自己的观点，有什么问题欢迎提出。在此需要注意，某些版本中我故意暴露出了一些问题，从而让后期的代码的出现有所依据

[前言：为什么需要MVC](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E5%89%8D%E8%A8%80.txt)

[案例分析1：我们的本质工作其实就是写一个html编译器](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%90.html)

[案例分析2：指令的扩展——repeat指令](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%902.html)

[案例分析3：添加watch（添加监听函数）和apply（触发脏检测）方法](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%903.html)

[案例分析4：watch函数监听新旧值是否发生变化时我们通过内部简单判断以及让使用者决定的方式，改善scope继承关系和repeat指令](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%904.html)

[案例分析5：改善脏检测和repeat](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%905.html)

[案例分析6：修正watch方法在比较时的bug，引入多次脏检测直到稳定状态](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%906.html)

[案例分析7：总结完善，封装Scope构造函数，添加了一些工具方法](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%907.html)

[案例分析8：表达式编译——数字编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%908.html)

[案例分析9：表达式编译——字符串编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%909.html)

[案例分析10：表达式编译——布尔常量和null的编译 将中间空格去掉](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%9010.html)

[案例分析11：表达式编译——数组编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%9011.html)

[案例分析12：表达式编译——对象编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%9012.html)

[案例分析13：表达式编译——属性标识符编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%9013.html)

[案例分析14：表达式编译——二级属性标识符编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%9014.html)

[案例分析15：表达式编译——多级属性标识符编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%9015.html)

[案例分析16：表达式编译——方括号访问属性标识符/数组属性值编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%9016.html)

[案例分析17：表达式编译——函数调用编译](https://github.com/zhaohuiziwo901/CourseExample/blob/master/%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AE%9E%E7%8E%B0MVC%E6%A1%86%E6%9E%B6/%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%9017.html)
