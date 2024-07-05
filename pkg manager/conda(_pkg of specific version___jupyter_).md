# download anaconda
https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/?C=M&O=D

# basic config
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --remove channels defaults
```

# virtual env
## check
conda info --envs
## create
conda create -n { name } python={ python version }
> not in base env
## rm
conda remove -n { name } --all
## activate
source activate { env_name }
## deactivate
conda deactivate

# upgrade conda
```bash
conda update conda
conda update anaconda
conda update anaconda-navigator
```

# rm conda
```bash
rm -rf path/anaconda3
rm -rf path/.condarc path/.conda path/.continuum

vim ~/.bashrc, rm
	# >>> conda initialize >>>
	# !! Contents within this block are managed by 'conda init' !!
	__conda_setup="$('/home/myfreax/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
	if [ $? -eq 0 ]; then
		eval "$__conda_setup"
	else
		if [ -f "/home/myfreax/anaconda3/etc/profile.d/conda.sh" ]; then
			. "/home/myfreax/anaconda3/etc/profile.d/conda.sh"
		else
			export PATH="/home/myfreax/anaconda3/bin:$PATH"
		fi
	fi
	unset __conda_setup
	# <<< conda initialize <<<
```

# pkg
## install pkg of specific version
conda install { pkg }={ version }
## uninstall
conda uninstall { pkg }
## cache purge
conda clean -y -all
## update
conda update

# jupyter
```bash
conda activate { target env }
conda install ipykernel 
conda deactivate

conda activate base
conda install nb_conda_kernels
conda install jupyter	# skip this step if installed
jupyter notebook
```

# problems
## cmd not found
add parent_path_of_anaconda3/anaconda3/bin to env_var
> export PATH=/home/anaconda3/bin:$PATH