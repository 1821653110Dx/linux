# basic
	tree -afpDhug (--noreport)
		-a all
		-f path
		-p priorities
		-D modifing date
		-h humerable size
		-u owner
		-g group owner belongs to
		--noreport not print dir and file counts

# scope
# only directory
	tree -d
## lv.2 depth
	tree -L 2
## print all \*.html
	tree -P *.html (--ignore-case)
## print all files except \*.html
	tree -I *.html (--ignore-case)
## print all result(include directory) with public
	tree -P public --matchdirs

# output to file a.md
## default
	tree -o a.md
## no color and las a list
	-ni
## XML
	-X
## JSON
	-J
## HTML
	-H

# sort by
## last modifing time
	-t
## file types
	-U
## reverse
	-r


