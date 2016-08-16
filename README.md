# hello-world
import numpy as np
import matplotlib.pylab as plt

x = np.arange(2,22)

def generador(N,x,px):
    
    X = []
    u =  Cm(N)    
    Px = np.cumsum(px)    
    for index in range(N):
        for i in range (1,len(Px)):
           
            if(u[index]<Px[0] ):
                X.append(x[0])
                break
                
            if(u[index]<Px[i] and u[index]>=Px[i-1]  ):                
                X.append(x[i-1])
                break        
    return X

def Cm(Maxgenerator=1):
    nums= []
    Xn = 7
    a = 7
    c = 1
    m = 16547
    
    for iterator in range(Maxgenerator):        
        Xn_1 = (a*Xn + c)% m        
        out = float(Xn_1)/float(m)    
        nums.append(out)
        Xn = Xn_1
    return nums

def px():
    z=[]
    for i in range(1,8):
        z.append(i)
    for i in range(6):
        z.append(8)
    for j in range(7,0,-1):
        z.append(j)
    print z
    pj=[]
    for i in range(len(z)):
        pj.append(float(z[i])/float(104))

    return pj

def valorEsperado(x,px):
    e_x = []
    for index in range( len(x)):
        e_x.append(x[index]*px[index]) 
    ex = np.sum(e_x)
    
    return ex   


px = px()

N = 5000
print valorEsperado(x,px)
w= generador(N,x,px) 
%matplotlib inline
    
count, bins, ignored = plt.hist(w, 100, normed=True)
plt.plot(bins, np.ones_like(bins), linewidth=2, color='r')
plt.show()
