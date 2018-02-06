# typeof-
js
echo "# typeof-" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/yewenjunfighting/typeof-.git
git push -u origin master

//typeof方法的重写,null是存在栈里面的是原始值，但typeof的结果却为object这是历史遗留问题,因为以前使用null替对象占位置的
	function type(target){
		var arr = '[object Array]';
		var obj = '[object Object]';
		var num = '[object Number]';
		var str = '[object String]';
		var bol = '[object Boolean]';
		if(typeof (target) == "object"){
			if(target == null){
				console.log('this is null');
			}else if(Object.prototype.toString.call(target) == arr){
				console.log('this is array');
			}else if(Object.prototype.toString.call(target) == obj ){
				console.log('this is object');
			}else if(Object.prototype.toString.call(target) == num){
				console.log('this is Number object');
			}else if(Object.prototype.toString.call(target) == str){
				console.log('this is String object');
			}else if(Object.prototype.toString.call(target) == bol){
				console.log('this is  Boolean object');
			}
		}else console.log('this is ' + typeof(target));
	}
	//数组去重,但只对原始值有效
	Array.prototype.unique = function (){
		var arr = [],
		    obj = {},
			len = this.length;
		for(var i = 0; i < len;  i++){
			if(!obj[this[i]]){
			  obj[this[i]] = '有值了';
			  arr.push(this[i]);
			}
		}
		return arr;
	}
