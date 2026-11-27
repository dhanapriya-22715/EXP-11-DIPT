# Exp-11- Record-IMPLEMENTATION OF HUFFMAN CODING
## Name : Dhanappriya S
## Reg NO :212224230056
## Aim:

To write and execute a Python program that implements the Huffman Coding algorithm to generate variable-length prefix codes for each character in a given input string based on its frequency.

---

## Procedure:

1. **Initialize the Input:** Define the input string (`"Dhanappriya s"`) that needs to be encoded.
2. **Calculate Character Frequencies:** Iterate through the string using a dictionary to count and store the frequency of each unique character.
3. **Create Leaf Nodes:** Convert the character-frequency pairs into a list of nodes (`[character, frequency]`).
4. **Build the Huffman Tree:**
* Repeatedly sort the list of nodes in ascending order of their frequencies.
* Extract the two nodes with the smallest frequencies (`left` and `right`).
* Combine them into a new internal node with a frequency equal to the sum of both nodes, and append it back to the list.
* Repeat until only one root node (the complete Huffman tree) remains.


5. **Generate Huffman Codes:** Traverse the Huffman tree recursively from the root—appending `"0"` for every left branch and `"1"` for every right branch—until reaching each leaf node to assign its binary code.
6. **Display Output:** Print the resulting table mapping each character to its generated Huffman code.
   
## CODE:
```python
# Step 1: Get the input string
input_string = "Dhanappriya s"  # Example input string
# Step 2: Calculate frequency of each character in the input string
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1
# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]
# Step 4: Main function to implement Huffman coding
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
huffman_tree = nodes[0]
# Step 5: Generate Huffman codes
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):  # If it's a leaf node
        huffman_codes[tree[0]] = code
    else:  # If it's an internal node, recurse
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)
# Step 6: Print the characters and their Huffman codes
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```
## Output:
<img width="522" height="221" alt="image" src="https://github.com/user-attachments/assets/72f70e86-59e6-4425-927b-a9a0a726a7c8" />

## Result:
Thus To write and execute a Python program that implements the Huffman Coding algorithm to generate variable-length prefix codes for each character in a given input string based on its frequency was verified successfully.

