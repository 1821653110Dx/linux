# save a macro to register a
	qa
	input cmd
	q
> clear register a
> > :let @a = ''
# use
## use previous macro
	@@
## use macro saved in register a
	@a