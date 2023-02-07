```javascript
let name = {
  firstname: "ssd",
  lastname: "ds"
}

let printName = function (hometown, state, country) {
  console.log(this.firstname + " " + this.lastname + " , " + hometown + ", " + state + ", " + country);
}

let printMyName = printName.bind(name, "xx", "yy");
printMyName( "df");

Function.prototype.mybind = function(...args){
//we'll get this from printName
  let obj = this,
    params = args.slice(1);
    //we sliced this, except first element params will have other elemeents now
  return function (...args2) {
  //...args2 will have arguments passed from myname2 where as args will have parmas passed from mybind
    obj.apply(args[0], [...params, ...args2]);
  }
}

let printMyName2 = printName.mybind(name, "xx", "yy");
printMyName2( "zz");



et fruits = [1,2,34,5,4]
//map
Array.prototype.customMap = function(callback){
    let arr = [];
    console.log(this);
    for(i=0; i< this.length; i++){
        arr.push(callback(this[i]))
    }
    return arr;
}
let fruitsOutput = fruits.customMap(function(element){

    return element*element;
})
console.log(fruitsOutput)

//for-each
Array.prototype.customForEach = function(callback){
      for(i=0; i<this.length; i++){
          callback(this[i])
      }
  }
fruits.customForEach(function(element){
    console.log(element)
  })
  
  Array.prototype.customFilter = function(callback, context){
    var arr = [];
    for(i=0; i< this.length; i++){
        if(callback.call(context, this[i], i, this)){
            arr.push(this[i])
        }
    }
    return arr
}

fruits.customFilter(function(element){
    if(element.price > 100){
        console.log(element)
    }
})



Array.prototype.myReduce = function(cb) {
    let value = this[0];
    for (let i = 1; i < this.length; i++) {
      value = cb(value,this[i])
    }
    return value;
  }
  
  
  
  
  const sum1 = arrayOfNumbers.myReduce(function(accumulator, currentValue) {
   
  console.log(accumulator, currentValue)
    return accumulator + currentValue;
  
  });
  console.log(sum1);
  
  const a = [1, 2, 3, 4, 5, 6, 7];

Array.prototype.myReduce = function(callback, initialvaluee) {
console.log(callback)
  let acc = initialvaluee;
  for (let i = 0; i < this.length; i++) {
    if (acc === undefined) {
      acc = this[i];
      continue;
    }
		acc = callback(acc, this[i], i, this)
  }
  return acc;
}

const s = a.myReduce((acc, current) => acc+current,0);
console.log(s)

  
```
