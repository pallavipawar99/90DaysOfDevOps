# Day 06 – Linux Fundamentals: Read and Write Text Files

## Create a file named 
```
name : notes.txt
```
## command flow
```
1. touch notes.txt
2. echo "Line 1" > notes.txt
3. echo "Line 2" >> notes.txt
4. echo "Line 3" | tee -a notes.txt
5. cat notes.txt
6. head -n 2 notes.txt
7. tail -n 2 notes.txt
```
## Notes
- `touch` (create an empty file) 
- `cat` (read full file) 
- `head` and `tail` (read parts of a file) 
- `tee` (write and display at the same time)
- `>` overwrites the file
- `>>` appends to the file