# run
## run in the background
bg %jobnumber  
### excuet script every 10s in the bg  
watch -n 10 sh test.sh &  
## run in the for ground
fg %jobnumber  
# search
## ps
	cmd
		ps aux | grep 'key_word'
	argument
		STAT - status
		START - start time
		TIME - running time
	STAT types
		D - can't be interrupted and static
		R - running
		S - blocking阻塞 status
		T - suspend暂停
		< - high priority
		N - low priority
		L - memory page 内存分页 allocation is loced in memory	// physical memory is divided into fixed size block 
		
# kill
## kill by job
jobs  
kill %\<num\>  
## kill by PID
ps  
kill \<PID\>  
### efficiency
ps aux | grep \<key_word>\ | awk '{print $2}' | xargs kill  


