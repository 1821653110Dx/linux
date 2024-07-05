# create venv
## for default python interpreter(python解释器)
    virtualenv {venv_name}
> warning: don't move venv created, otherwise some problems will occur
## for certain python interpreter
    virtualenv -p {path_to_the_python} {venv_name}

# activate venv
    source /path_to_venv/bin/activate

# exit venv
    deactivate