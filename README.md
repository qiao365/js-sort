## Sort()

srot()如果不带参数，是将按字母顺序对数组中的元素进行排序，也就是是按照字符编码的顺序进行排序。

    var arr1 = ['a', 'd', 'c', 'b'];
    arr.sort();  //['a', 'b', 'c', 'd']
     
    var arr2 = [10, 5, 40, 25, 100, 1];
    arr2.sort(); //[1, 10 ,100, 25, 40, 5]

为sort()中传入排序规则函数可实现自定义排序

排序函数规则：

    传两个形参
    当返回值为正数时，交换传入两形参在数组中位置

排序的内置算法：

JS中sort实现算法居然是O(n^2)的冒泡排序，所以有时候有必要自己实现那些算法，可以参考这个网址胡耀的github/sort
按照数值大小进行排序-升序

    arr.sort(function(a,b){
        return a - b;
    })

按照数值大小进行排序-降序

    arr.sort(function(a,b){
    	return b - a;
    })

按照数组中对象的某一个属性值进行排序

    var arr = [
        {name:'zopp',age:0},
        {name:'gpp',age:18},
        {name:'yjj',age:8}
    ];
    function compare(property){
        return function(a,b){
            var value1 = a[property];
            var value2 = b[property];
            return value1 - value2;
        }
    }
    console.log(arr.sort(compare('age')))

让数组乱序

    arr.sort(function(a,b){
    	return Math.random() - 0.5;
    })
--------------------- 

## 快速排序

```javascript

    以对数组[3, 2, 4, 5, 1] 进行从小到大排序为例，步骤如下：

    将数组分成[3, 2]和[4 ,5, 1]两部分。

    依次递归如下：

    var quickSort = function(arr) {

    　　if (arr.length <= 1) { return arr; }

    　　var pivotIndex = Math.floor(arr.length / 2);

    　　var pivot = arr.splice(pivotIndex, 1)[0];

    　　var left = [];

    　　var right = [];

    　　for (var i = 0; i < arr.length; i++){

    　　　　if (arr[i] < pivot) {

    　　　　　　left.push(arr[i]);

    　　　　} else {

    　　　　　　right.push(arr[i]);

    　　　　}

    　　}

    　　return quickSort(left).concat([pivot], quickSort(right));

    };

```

## 插入排序
```javascript

以对数组[3, 2, 4, 5, 1] 进行从小到大排序为例，步骤如下：

    将数组分成[3]和[2, 4, 5, 1]两部分，前者是已排序的，后者是未排序的。

    取出未排序部分的第一个元素“2”，与已排序部分最后一个元素“3”比较，因为2小于3，所以2排在3前面，整个数组变成[2, 3]和[4, 5, 1]两部分。

    取出未排序部分的第一个元素“4”，与已排序部分最后一个元素“3”比较，因为4大于3，所以4排在3后面，整个数组变成[2, 3, 4]和[5, 1]两部分。

    取出未排序部分的第一个元素“5”，与已排序部分最后一个元素“4”比较，因为5大于4，所以5排在4后面，整个数组变成[2, 3, 4, 5]和[1]两部分。

    取出未排序部分的第一个元素“1”，与已排序部分最后一个元素“5”比较，因为1小于5，所以再与前一个元素“4”比较；因为1小于4，再与前一个元素“3”比较；因为1小于3，再与前一个元素“2”比较；因为小于1小于2，所以“1”排在2的前面，整个数组变成[1, 2, 3, 4, 5]

算法的实现如下：

function insertionSort(myArray) {

    var len     = myArray.length,     // 数组的长度
        value,                      // 当前比较的值
        i,                          // 未排序部分的当前位置
        j;                          // 已排序部分的当前位置
    
    for (i=0; i < len; i++) {
    
        // 储存当前位置的值
        value = myArray[i];
        
        /*
         * 当已排序部分的当前元素大于value，
         * 就将当前元素向后移一位，再将前一位与value比较
         */
        for (j=i-1; j > -1 && myArray[j] > value; j--) {
            myArray[j+1] = myArray[j];
        }

        myArray[j+1] = value;
    }
    
    return myArray;
}

```

## 冒泡排序

```javascript

function sort(arr)
{
    for(i=0;i<arr.length-1;i++){
        for(j=0;j<arr.length-1-i;j++){
            if(arr[j]>arr[j+1]){
                var temp=arr[j];
                arr[j]=arr[j+1];
                arr[j+1]=temp;
            }
        }
    }
    return arr;
}

```
