# open file
## before loding vim
- open multiple files in multiple horizontal windows 
	- vim -o file1 file2
- open multiple files in multiple vertical windows 	
	- vim -O file1 file2
## have loded vim
- open a new file at current panel
    - `edit {file}`
- open a new file at a new vertical panel
    - `vs {file}`
- open a new file at a new horizontal panel
    - 'sp {file}'
	
# quit
- save and quit all files
	- :wqall
- others
	- C w, o
	- 
# split
- remain the current panel only = :only
- close current panel = C w,c

- split the screen horizontally = C w, s
- split the screen vertically = C w, v

# move current panel
## to a new tag
	C w, T
## clockwise
	C w, r
## to left/right/down/up
	C w, H/L/J/K
	
	
# size
- all panels are the same size
	- : C w, =
- increase by one row 
	-  C w, +
- increase by n rows
	- C w, + n
- increase by one column
	- C w, >
- current panel is n rows high
	- : resize n
