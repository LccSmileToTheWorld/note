typeof(exp)：返回exp的类型，返回的是字符串。有六种结果："number"、"string"、"boolean"、"object"、"function"、"undefined"。
null 返回 “object”，undefined 返回 “undefined”

判单一个变量是否为 null 或 undefined 可以使用 if(!exp)
if(!exp){
​	exp 是 null 或 undefined
}else{
​	exp 不是 null 也不是 undefined
}

