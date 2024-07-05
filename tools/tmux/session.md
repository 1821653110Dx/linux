# ls
	C b s
	
# rename
	C b $
	
# create
	:new

# kill
## current
	tmux kill-session
## certain
	tmux kill-session -t num
## others
	tmux kill-session -t otherSession 
## all
	tmux kill-server  

# detach/reconncect
## detach
	C b d
## reconnect
	tmux at -t  <session-name>