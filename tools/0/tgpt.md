https://github.com/aandrew-me/tgpt  

- Usage: tgpt [Flag] [Prompt]

- Flags:
	- s, --shell                                        
		- Generate and Execute shell commands. (Experimental) 
	- c, --code                                         
		- Generate Code. (Experimental)
	- q, --quiet                                        
		- Gives response back without loading animation
	 -w, --whole                                        
	 	- Gives response back as a whole text
	- img, --image                                      
		- Generate images from text

- Options:
	- f, --forget                                       
		- Forget Chat ID 
	- v, --version                                     
		-  Print version 
	- h, --help                                         
		- Print help message 
	- i, --interactive                                  
		- Start normal interactive mode 
	- m, --multiline                                    
		- Start multi-line interactive mode 
	- cl, --changelog                                   
		- See changelog of versions 
	- u, --update                                       
		- Update program 

- Examples:
	- tgpt "What is internet?"
	- tgpt -f
	- tgpt -m
	- tgpt -s "How to update my system?"