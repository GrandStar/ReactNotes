# special function

## debounce data

![](../.gitbook/assets/image%20%2832%29.png)

Operation DOM:

let temp = document.getElementsByTagName\("a"\); for \(let i of temp\) { console.log\(i.innerHTML\); }

![](../.gitbook/assets/image%20%2840%29.png)



Random array

**for \(let i = temp.length - 1; i &gt;= 0; i--\) {**

    **let j = Math.floor\(Math.random\(\) \* \(i + 1\)\);**

    **\[temp\[i\], temp\[j\]\] = \[temp\[j\], temp\[i\]\];**

**}**  


