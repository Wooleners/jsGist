###截取字符串
```javascript
function cutstr(str, len) {
    var temp,
        icount = 0,
        patrn = /[^\x00-\xff]/，
        strre = "";
    for (var i = 0; i < str.length; i++) {
        if (icount < len - 1) {
            temp = str.substr(i, 1);
                if (patrn.exec(temp) == null) {
                   icount = icount + 1
            } else {
                icount = icount + 2
            }
            strre += temp
            } else {
            break;
        }
    }
    return strre + "..."
}
```
###替换全部
```javascript
String.prototype.replaceAll = function(s1, s2) {
    return this.replace(new RegExp(s1, "gm"), s2)
}
```
###清除空格
```javascript
String.prototype.trim = function() {
    var reExtraSpace = /^\s*(.*?)\s+$/;
    return this.replace(reExtraSpace, "$1")
}
```
###清除左空格/右空格
```javascript
function ltrim(s){ return s.replace( /^(\s*|　*)/, ""); } 
function rtrim(s){ return s.replace( /(\s*|　*)$/, ""); }
```
###判断是否由某个字符串开头
```javascript
String.prototype.startWith = function (s) {
    return this.indexOf(s) == 0
}
```
###转义HTML标签
```javascript
function HtmlEncode(text) {
    return text.replace(/&/g, '&').replace(/\"/g, '"').replace(/</g, '<').replace(/>/g, '>')
}
```
###对象扩展[旧版本IE无法遍历名为valueOf、toString]
```javascript
function extend(des, source){
	for(var prop in source)
		des[prop] = source[prop];
	return des;
}
```
###对象扩展增强版
```javascript
function mix(target, source){
	var args = [].slice.call(arguments), i = 1, key,
		ride = typeof args[args.length - 1] == "boolean" ? args.pop() : true;
	if(args.length === 1){
		target == !this.window ? this : {};
		i = 0;
	}
	while( (soure = args[i++]) ){
		for(key in source){
			if(ride || !(key in target)){
				target[key] = source[key];
			}
		}
	}
	return target;
}
```