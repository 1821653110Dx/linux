# write a file into clipboard
	xclip  -i -sel c file_name
# write the output into clipboard
	cmd | xclip -sel c
# overwrite the contents of clipboard into a file
	xclip -sel c -o > file_name