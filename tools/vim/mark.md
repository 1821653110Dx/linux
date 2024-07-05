# show all marks
:marks

# create
- temporaly
	- m{a-z}
- permanently
	- m{A-Z}

# move
- move to the previous mark
 	- C o
- move to the next mark
	- C i
- move to mark {a-z}
	- \`{a-z}

# delete
- delete a and b
	- :delmarks a b
- delete from a to c
	- :delmarks a-c
- delete a and c-f
	- :delmarks a c-f
- delete all
	- :delmarks!
