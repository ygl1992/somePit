# JavaScript数组去重的八种方法


### Methods 1: 思路：定义一个新数组，并存放原数组的第一个元素，然后将元素组一一和新数组的元素对比，若不同则存放在新数组中。
	function unique1(arr){
	    var res = [arr[0]];
	
	    for(var i=1; i<arr.length; i++){
	        var isExist = false;
	        for(var j=0; j<res.length; j++){
	            if( arr[i] == res[j] ){
	                isExist = true;
	                break;
	            }
	        }
	
	        if( !isExist ){
	            res.push( arr[i] );
	        }
	    }
	
	    return res;
	}


### Methods 2: 思路：先将原数组排序，在与相邻的进行比较，如果不同则存入新数组。
	function unique2(arr){
        var newArr = arr.sort();
        var res = [newArr[0]];

        for(var i=1; i<arr.length; i++){
            if( arr[i] !== res[res.length-1] ){
                res.push(arr[i]);
            }
        }
        
        return res;
    }


### Methods 3: 利用对象属性存在的特性，如果没有该属性则存入新数组。
	function unique3(arr){
        var res = [];
        var obj = {};

        for(var i=0; i<arr.length; i++){
            if( !obj[arr[i]] ){
                obj[arr[i]] = 1;
                res.push(arr[i]);
            }
        }

        return res;
    }


### Methods 4: 利用数组的indexOf下标属性来查询。
	function unique4(arr){
        var res = [];
        
        for(var i=0; i<arr.length; i++){
            if( res.indexOf(arr[i]) == -1 ){
                res.push(arr[i]);
            }
        }

        return res;
    }


### Methods 5: 利用数组原型对象上的includes方法。
	function unique5(arr){
        var res = [];
        
        for(var i=0; i<arr.length; i++){
            if( !res.includes(arr[i]) ){
                res.push(arr[i]);
            }
        }

        return res;
    }


### Methods 6: 利用数组原型对象上的 filter 和 includes方法。
	function unique6(arr){
        var res = [];

        res = arr.filter((item)=>{
            return res.includes(item) ? '' : res.push(item)
        });

        return res;
    }


### Methods 7: 利用数组原型对象上的 forEach 和 includes方法。
	function unique7(arr){
        var res = [];

        arr.forEach(function(item){
            res.includes(item) ? '' : res.push(item);
        });

        return res;
    }


### Methods 8: 利用 ES6的set 方法。
	function unique8(arr){
        return Array.from( new Set(arr) );
    }


摘自[http://www.jb51.net/article/121410.htm](http://www.jb51.net/article/121410.htm)