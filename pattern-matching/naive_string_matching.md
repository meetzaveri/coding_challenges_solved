Pseudocode :
    
    `
    // Return an array which contains all valid shifts in text (str)
       NaiveMethod(text, pattern) {
          N = length(text);
          M = length(patter,);
          limit = N-M;
          j = 0, k = 0;
          arrayOfValidShift[];
          for(i = 0; i <= limit; i++){
          j = 0;
          k = i;
            for(j = 0; j <= M AND str[k] == pat[j]; j++)
              k++;
              if(j >= M)
              Add i to arrayOfValidShift;
            }
          return arrayOfValidShift;
        }
    `
Code(Python)
```python
def searchpattern(text,pattern):
    lenoftext = len(text)
    lenofpattern = len(pattern)
    limit = lenoftext - lenofpattern
    i=0
    j=0
    arrayofshift = []
    for i in range(0,limit):
        j=0
        k=i
        if (text[k] == pattern[j]):
            for j in range(0,lenofpattern):
                if (text[k] == pattern[j]):
                    k+=1
                    print('YES')
                    if j+1>=lenofpattern:
                        arrayofshift.append(i)

    print('arrayofshift',arrayofshift)


searchpattern('the hat and pat fluff', 'at') # [5,13]
```
