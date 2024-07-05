# repo
## add 上海交大源
	sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
	sudo flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub

## del
	sudo flatpak remote-delete flathub
## check
	flatpak remotes

# apps
## search
	flatpak search { app }
	
## list
	installed apps
		flatpak list --app
	installed apps and their env 	
		flatpak list
	list app can be installed
		flatpak remote-ls { repo } --app
	app info
		flatpak info { app }
		
## install
		sudo flatpak install { app }
		
## install_path 
	$HOME/.var/app/
	
## uninstall
	sudo flatpak uninstall --delete-data { app }
	sudo flatpak uninstall --unused --runtime

## update
	all apps
		sudo flatpak update
	certain app
		sudo flatpak update { app }