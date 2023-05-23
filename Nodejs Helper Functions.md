
### JSON Array sorter in Ascending

```node
function sortByProperty(property){  
        return function(a,b){  
           if(a[property] > b[property])  
              return 1;  
           else if(a[property] < b[property])  
              return -1;  
           return 0;  
        }  
     }
```


### Currency Formater

```node
let currencyF = new Intl.NumberFormat('en-in', {
        currency: 'INR',
        style: 'currency'
    })
```

```node
currencyF.format(10000)
```


### Check If its a Number

```node
const checkNumber = (num)=>{
    if((typeof num) === 'string'){
        let isNum = num.split('').every((ele)=>{
            if(isNaN(parseInt(ele))){
                return false
            }
            return true
        })
        return isNum
    }
    else if((typeof num) === 'number'){
        return true
    }
    else{
        return false
    }
}
```


### Sleep Function

```node
const sleep = (time) => {
  return new Promise(resolve => setTimeout(resolve, time))
}
```
