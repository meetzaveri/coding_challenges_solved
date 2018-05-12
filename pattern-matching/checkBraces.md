Check braces in particular order as compiler checks in its way. Return an array with yes or no values indicating that pattern is valid or not

### Input
2
{[()]}
[{]}

### Output
['YES','NO']

Is this solution optimal? No. But I have put effor and will reach the boundaries where it can work with all test cases 

### Code

```js
function checkBraces(values){
  var resultArr = [];
  values.forEach((item,index) => {
    var tempResultantArr = [];
    var braceExampleArr = item.split('');
    // console.log('braceExample ',braceExampleArr);
    braceExampleArr.forEach((item_i,index_i)=>{
      // console.log('Item_i',item_i);

      // For facing 'starting' tag, we will look if there is no ] or } immediately
      // after it
      if(item_i === '{'){
        if(braceExampleArr[index_i+1] === ']' || braceExampleArr[index_i+1] === ')'){
          tempResultantArr.push('NO');
        } else{

          // Seeing that if there is an ending tag over the array or not
          var remainingEle = braceExampleArr;
          remainingEle.splice(index_i,1);
          console.log('remainingEle }',remainingEle)

          let i = 0;
          let ifOccuredAnyTime = false;

          //  just a middleware to escape from recursive callbacks
          function middleware(){
            console.log('Middleware logged')
          }

          // Recursively performs at two step at a time
           // deciding whether ending } or ] or ) occurs after 2 elements like {[]}
           // or after 4 elements like {[()]}
          function recurseRemainingEle(i){
            console.log('i at every instance',i)

            if(remainingEle[i] ==='}'){
              // If once ending tag occured, then set boolean value to true 
              ifOccuredAnyTime = true;
              

              //for last element check
              if(i > remainingEle.length - 1){
                if(ifOccuredAnyTime){
                  tempResultantArr.push('YES');
                  return middleware();
                } else{
                  tempResultantArr.push('NO');
                  return middleware();
                }
                
              } else{
                // recurse after incrementing it to 2 
                i=i+2;
                console.log('i after every match',i)
                recurseRemainingEle(i);
              }
            } else{
              console.log('remaining',i,remainingEle.length - 1)
              if(i > remainingEle.length - 1){
                if(ifOccuredAnyTime){
                  tempResultantArr.push('YES');
                  return middleware();
                } else{
                  tempResultantArr.push('NO');
                  return middleware();
                }
              } else{
                // recurse after incrementing it to 2 
                i=i+2;
                console.log('i after every match',i)
                recurseRemainingEle(i);
              }
            }
          }
          recurseRemainingEle(i);


          
        }
      } else if(item_i === '['){
        if(braceExampleArr[index_i+1] === '}' || braceExampleArr[index_i+1] === ')'){
          tempResultantArr.push('NO');
        } else{

           // Seeing that if there is an ending tag over the array or not
          var remainingEle = braceExampleArr;
          remainingEle.splice(index_i,1);
          console.log('remainingEle ]',remainingEle)
 
          let i = 0;
          let ifOccuredAnyTime = false;

          //  just a middleware to escape from recursive callbacks
          function middleware(){
            console.log('Middleware logged')
          }
           // Recursively performs at two step at a time
           // deciding whether ending } or ] or ) occurs after 2 elements like {[]}
           // or after 4 elements like {[()]}
           function recurseRemainingEle(i){
             console.log('i at every instance',i)
 
             if(remainingEle[i] ===']'){
               // If once ending tag occured, then set boolean value to true 
               ifOccuredAnyTime = true;
               //for last element check
               if(i > remainingEle.length - 1){
 
                 if(ifOccuredAnyTime){
                   tempResultantArr.push('YES');
                   return middleware();
                 } else{
                   tempResultantArr.push('NO');
                   return middleware();
                 }
                 
               } else{
                 // recurse after incrementing it to 2 
                 i=i+2;
                 console.log('i after every match',i)
                 recurseRemainingEle(i);
               }
             } else{
               console.log('remaining',i,remainingEle.length - 1)
               if(i > remainingEle.length - 1){
                 if(ifOccuredAnyTime){
                   tempResultantArr.push('YES');
                   return middleware();
                 } else{
                   tempResultantArr.push('NO');
                   return middleware();
                 }
               } else{
                 // recurse after incrementing it to 2 
                i=i+2;
                console.log('i after every match',i)
                recurseRemainingEle(i);
              }
             }
           }
           recurseRemainingEle(i);
          
        }
      } else if(item_i === '('){
        if(braceExampleArr[index_i+1] === '}' || braceExampleArr[index_i+1] === ']'){
          tempResultantArr.push('NO');

        } else{

          
           // Seeing that if there is an ending tag over the array or not
           var remainingEle = braceExampleArr;
           remainingEle.splice(index_i,1);
           console.log('remainingEle ]',remainingEle)
  
           let i = 0;
           let ifOccuredAnyTime = false;
 
           //  just a middleware to escape from recursive callbacks
           function middleware(){
             console.log('Middleware logged')
           }
            // Recursively performs at two step at a time
            // deciding whether ending } or ] or ) occurs after 2 elements like {[]}
            // or after 4 elements like {[()]}
            function recurseRemainingEle(i){
              console.log('i at every instance',i)
  
              if(remainingEle[i] ===')'){
                // If once ending tag occured, then set boolean value to true 
                ifOccuredAnyTime = true;
                //for last element check
                if(i > remainingEle.length - 1){
  
                  if(ifOccuredAnyTime){
                    tempResultantArr.push('YES');
                    return middleware();
                  } else{
                    tempResultantArr.push('NO');
                    return middleware();
                  }
                  
                } else{
                  // recurse after incrementing it to 2 
                  i=i+2;
                  console.log('i after every match',i)
                  recurseRemainingEle(i);
                }
              } else{
                console.log('remaining',i,remainingEle.length - 1)
                if(i > remainingEle.length - 1){
                  if(ifOccuredAnyTime){
                    tempResultantArr.push('YES');
                    return middleware();
                  } else{
                    tempResultantArr.push('NO');
                    return middleware();
                  }
                } else{
                  // recurse after incrementing it to 2 
                 i=i+2;
                 console.log('i after every match',i)
                 recurseRemainingEle(i);
               }
              }
            }
            recurseRemainingEle(i);
        }
      }
      
      // If its last element then push result into main Array
      if(index_i === braceExampleArr.length - 1){
        // es6 duplicate values removal through set
        var uniqueArray = tempResultantArr.filter(function(item, pos, self) {
          var temp = [];
          if(item === 'NO'){
            return 'NO';
          } else{
            console.log(pos,tempResultantArr.length - 1)
            if(pos === tempResultantArr.length - 1){
              temp.push(item);
              return temp[0];
            } else{
              temp.push(item);
            }
          }
          
        })
        resultArr.push(uniqueArray);
      }
      
    })
    
    
  })
  
  console.log('resultArr',resultArr)

}

checkBraces(['{[()]}','{}','[{]}']);
```
