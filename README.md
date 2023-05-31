# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Get the input String.

### Step2:
Create tree nodes.

### Step3:
Main function to implement huffman coding.

### Step4:
Calculate frequency of occurrence.

### Step5:
Print the characters and its huffmancode.
 
## Program:

``` Python
#Name : S.ABHISHEK
#Reg. no.: 212221230002
# Get the input String
s=input()

# Create tree nodes
class NodeTree(object):
    def __init__(self,left=None,right=None):
        self.left=left
        self.right=right
    def children(self):
        return (self.left,self.right)
    



# Main function to implement huffman coding
def hct(node,left=True,bins=''):
    if type(node) is str:
        return {node:bins}
    (l,r)=node.children()
    d=dict()
    d.update(hct(l,True,bins+'0'))
    d.update(hct(r,False,bins+'1'))
    return d

# Calculate frequency of occurrence
f={}
for c in s:
    if c in f:
        f[c]+=1
    else:
        f[c]=1
f=sorted(f.items(),key=lambda x: x[1], reverse=True)
nodes=f

while len(nodes) >1:
    (key1,c1) = nodes[-1]
    (key2,c2) = nodes[-2]
    nodes=nodes[:-2]
    node=NodeTree(key1,key2)
    nodes.append((node,c1+c2))
    
    nodes=sorted(nodes,key=lambda x: x[1],reverse=True)


# Print the characters and its huffmancode
hc=hct(nodes[0][0])
print('Char | Huffman code')
print('---------------')
for (char,f) in f:
    print(' %-4r |%12s'%(char,hc[char]))




```
## Output:

### Print the characters and its huffmancode
![image](https://github.com/S-ABHISHEK-1905/Huffman-Coding/assets/66360846/4237134a-a938-40b1-829c-7b28bf147b36)



## Result
Thus the huffman coding was implemented to compress the data using python programming.
