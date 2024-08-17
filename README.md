OVERVIEW
- Implemented an efficient and lossless file compression system utilizing Huffman Coding's greedy approach to minimize storage space and improve data transmission speed. This further reduces the cost as the storage and bandwidth requirements are reduced.
- This application can be used to compress any text based file, i.e., files with extensions like .txt, .c, .cpp, .html, .js, .docx and so on!

INTRODUCTION
Huffman Coding is an optimal loss-less compression technique, i.e., on decompression, we receive the original data without any loss.
Following are the characteristics of Huffman Coding: 
  1) Variable Length Encoding - Different characters are assigned codes of different length.
  2) Greedy Approach - The most frequently occurring character has the smallest code.
  3) Prefix Requirement for Decompression - No code is a prefix of any other code.

STEPS INVOLVED (working of code)
Step - 1:	createMinHeap();
This function reads the input file to calculate the frequency of each character. It then creates a min-heap (a priority queue) of nodes, where each node contains a character and its frequency. The min-heap is structured so that the character with the smallest frequency is at the top, which is essential for building the Huffman tree.

Step - 2:	createTree();
After creating the min-heap, this function builds the Huffman tree. It repeatedly extracts the two nodes with the smallest frequencies from the min-heap, combines them into a new node (with a frequency equal to the sum of the two), and then inserts this new node back into the min-heap. This process continues until there is only one node left in the heap, which becomes the root of the Huffman tree.

Step - 3:	createCodes();
This function traverses the Huffman tree to generate unique binary codes for each character based on their path from the root to their respective leaf node. For example, moving left in the tree might correspond to adding a 0 to the code, while moving right adds a 1. This ensures that each character has a distinct binary code, and no code is a prefix of another, making the encoding unambiguous.

Step - 4:	saveEncodedFile();
Finally, this function encodes the original input file using the generated Huffman codes and saves the compressed data to an output file. It also saves the structure of the Huffman tree (as metadata) in the compressed file, which is crucial for decompression later.

Step - 5:	getTree();
This function reads the metadata (the structure of the Huffman tree) from the compressed file and reconstructs the original Huffman tree. This step is crucial because the tree is needed to decode the binary data back into characters.

Step - 6:	saveDecodedFile();
Once the Huffman tree is reconstructed, this function reads the compressed binary data from the file, uses the tree to decode it back into the original text, and then saves the decoded text into a new file. The decoding process involves traversing the Huffman tree according to the binary data, converting it back to the corresponding characters.
