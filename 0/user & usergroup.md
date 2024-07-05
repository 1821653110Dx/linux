# user
## switch to root
    su root
## add
    useradd -m user_name  
## delete
    deluser -rf user_name  
## modify attribute
	change name
		usermod  –d  /home/newname  –m  –l  newname  oldname

# user group
## add
	addgroup  groupname
## del
	delgroup  groupname
## add users to the sudo user group
    su root
    nano /etc/sudoers
        add the internal at the end of the file:
            {user_name} ALL=(ALL:ALL) ALL
        save and exit
    logout and login

