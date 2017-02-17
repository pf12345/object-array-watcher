# object-array-watcher
参考vue watch array and object 的原理及相关逻辑，封装用于单独监控数组数据变化，包括通过push、pop、shift、unshift、splice、sort及reverse方法引起数组变化；

也能深度监控对象、数组中的对象的属性变化；

数组变化通过配置回调：arrayCb 处理变化后操作
对象属性变化通过配置回调：propertyCb 处理变化后操作

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="./index.js"></script>
</head>
<body>

<script>
    var a = [1,2,3];
    new Watcher({
        arrayCb: function (method) {
           console.log(method)
        },
        propertyCb: function (obj, key, newVal) {
            console.log(key);
        }
    }).observe(a);
    a.push({a: 1});
    a[3].a = 10;
</script>
</body>
</html>

```
