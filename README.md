# calculator
#mini project

from io import StringIO
import sys, numbers
import math,cmath,logging
fileHandle = open('log2.txt',"r")
last_number = fileHandle.read()
print("previous output is---" +last_number)
def func(num):
    try:
        a=(num)
        if a[0]=='+':
            solution= eval(last_number+a)

        elif a[0]=='-':
                solution= eval(last_number+a)
        elif a[0]=='*':
            number=int(a[1:])
            last_number1=int(last_number)
            solution=(last_number1*number)
        elif a[0]=='/':
            number = int(a[1:])
            last_number1 = int(last_number)
            solution = (last_number1 / number)
        else:
            solution=eval(a)
        return solution
    except SyntaxError:
        return "No expression after the the given number"
    except TypeError:
        return "invalid input"
    except ZeroDivisionError:
        return "cant divide with 0!!!!"
    except IndexError:
        return "No expression entered, Please enter something!!!!"
    except NameError:
        l=a[4:-1]
        if a[0]=='s':
            return math.sin(float(l))
        elif a[0]=='c':
            return math.cos(float(l))

        elif a[0] =='t':
            return math.tan(float(l))
        elif a[0]=='l':
            return math.log(float(l),10)




k=func(sys.argv[1])
f1=open("log2.txt","w")
f1.write(str(k))
logging.basicConfig(filename="log.txt",format='%(asctime)s %(message)s',filemode='a+')
logger = logging.getLogger()
logger.setLevel(logging.DEBUG)
handler=logging.StreamHandler(sys.stdout)
handler.setLevel(logging.DEBUG)
formatter1=logging.Formatter('%(asctime)s-%(message)s')
handler.setFormatter(formatter1)
logger.addHandler(handler)

logger.info('this is our input:'+ str(sys.argv[1]) +   'this is our output:'+str(k))

while(True):
    input1 = str(input())
    if(input1[0]=='*'):
        input2=int(input1[1:])
        k=k*input2
        print(k)
    else:
        k=k+int(input1)

        print(k)



