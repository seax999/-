# 浅谈 JSON 序列号





##### JSON 序列化-JSON.strinifly

1. 如果序列化的对象中有 toJSON 函数，则序列化的结果为 toJSON 的函数值
2. 无法序列化错误对象，错误对象会被序列化为空对象
3. 序列化只能序列化可枚举属性
4. Date 对象会被序列化为字符串
5. 循环引用的变量会抛出异常
6. NaN、null、Infinify 直接序列化会被序列化为 null
7. undefined、Symbol、函数 直接序列化返回undefined
8. undefined、Symbol、函数 对象内序列化会被忽略
9. undefined、Symbol、函数 数组内会被序列化为 null



##### JSON 序列化-JSON.parse

1. 序列化的值是 json 字符串
2. 符合 json 的数据规范