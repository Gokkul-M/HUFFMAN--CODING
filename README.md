# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:

### Step1:
Get the input string

### Step2:
Create tree nodes

### Step3:
Main function to implement huffman coding

### Step4:
calculate frequency of occurence

### Step5:
print the characters and its huffmancode
 
## Program:

``` Python
class NodeTree:
    def __init__(self, char=None, left=None, right=None):
        self.char = char
        self.left = left
        self.right = right

    def is_leaf(self):
        return not self.left and not self.right

def huffman_code_tree(node, binString=''):
    if node.is_leaf():
        return {node.char: binString}
    huffman_code = {}
    huffman_code.update(huffman_code_tree(node.left, binString + '0'))
    huffman_code.update(huffman_code_tree(node.right, binString + '1'))
    return huffman_code

def calculate_frequency(string):
    freq = {}
    for char in string:
        if char in freq:
            freq[char] += 1
        else:
            freq[char] = 1
    return freq

def build_tree(frequencies):
    nodes = [[NodeTree(char=char), freq] for char, freq in frequencies.items()]
    while len(nodes) > 1:
        nodes = sorted(nodes, key=lambda x: x[1])
        left = nodes.pop(0)
        right = nodes.pop(0)
        merged_node = NodeTree(left=left[0], right=right[0])
        nodes.append([merged_node, left[1] + right[1]])
    return nodes[0][0]

string = "hello huffman"
frequencies = calculate_frequency(string)
huffman_tree = build_tree(frequencies)
huffman_codes = huffman_code_tree(huffman_tree)

print(' Char | Huffman code ')
for char, code in huffman_codes.items():
    print(f' {char!r}   | {code}')


```
## Output:

### Print the characters and its huffmancode
![image](https://github.com/user-attachments/assets/8ab996d1-e177-4072-9a33-ab7dc5a12d01)

## Result
Thus the huffman coding was implemented to compress the data using python programming.
