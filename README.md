#誰是幸運兒

https://hackmd.io/7b_uqvd2SNKUtY5p1mXxNg?view
教室大小為 n * n，每次點名輸入座號 玩大十字
重複點名，直到教室內被點到低於 3 次(不包含 3) 的學生少於5個 (不包含 5)
最後印出剩下學生的座號
```python
n=int(input()) #教室大小=n*n
a=[[0]*n for i in range(n)]  #教室圖矩陣

def main(): #老師點名後，判斷影響到的直橫排   
    while 1:        
        num=int(input()) #點名到的同學
        h=(num-1)//n #第幾橫排
        hh=(num-1)%n #第幾直排
        a=hen(h) 
        a=jj(hh) 
        a=duo(h,hh)     
        t=good()
        if type(t)==list:
            for i in range(len(t)):
                print(t[i],end=' ')
            break

def hen(h): #橫排全+1
    for i in range(n):
        a[h][i]+=1

def jj(hh): #直排全+1
    for i in range(n):
        a[i][hh]+=1

def duo(h,hh): #被點到的-1，因為重複+1兩遍
    a[h][hh]-=1
    

def good(): #算班上還有幾個同學沒點三次
    line=[] #儲存每條線尚未被點到三次的同學
    lucky=n**2
    bingo=0
    for g in range(n):
        for gg in range(n):
            if a[g][gg]>2: #被點到低於3次的同學
                lucky-=1
            else:
                line.append(n*g+1+gg)
    if lucky <5:
        bingo=1
        return line
    return bingo
main()

