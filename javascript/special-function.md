# special function

## debounce data

![](../.gitbook/assets/image%20%2838%29.png)

Operation DOM:

let temp = document.getElementsByTagName\("a"\); for \(let i of temp\) { console.log\(i.innerHTML\); }

![](../.gitbook/assets/image%20%2846%29.png)



Random array

**for \(let i = temp.length - 1; i &gt;= 0; i--\) {**

    **let j = Math.floor\(Math.random\(\) \* \(i + 1\)\);**

    **\[temp\[i\], temp\[j\]\] = \[temp\[j\], temp\[i\]\];**

**}**  


## 7 ways to flip two varibles

a = "hello", b = "bye";

1. var c = a; a = b; b = c;
2.  a = a + b; b = a - b; a = a - b;        -------- a = a - b; b = a + b; a = b - a;
3. a ^= b; b ^= a; a ^= b;          a = \(b^=a^=b\)^a;
4. a = {a:b,b:a}; b = a.b; a = a.a;
5. a = \[a,b\]; b = a\[0\]; a = a\[1\];
6. a = \[b,b=a\]\[0\];                   -------     

   ```text
   b = [a, a = b][0];

   a = b + (b = a, "");
   ```

7. \[a,b\] = \[b,a\];



