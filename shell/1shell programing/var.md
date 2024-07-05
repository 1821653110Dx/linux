# type
- usr constomed var
- positional var(cli argument)
- predefined var
- env var
# usr constomed var
```bash
#!/usr/bin/bash

Y=hello ;   # save 'hello' to Y
x=$Y ;    # save Y to X
echo $x ;   # print X

unset x ;   # clear x
```
# positional var
```bash
$0
$1,$2,$3...
$#
$?
$*
$$
```
# env var
    HOME    the home path of usr in /etc/passwd
    IFS internal field seperator. space,tab and \n by default
    PS1,PS2 default prompt($) and newline prompt(>) 
    TERM    terminal type