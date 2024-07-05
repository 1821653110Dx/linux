# print the expected size of .iso created from all files in directory_a
```bash
mkisofs -print-size -r a/
```
# create iso
## convert all files in directory_a into a.iso
```bash
mkisofs -r -o a.iso a/
```
## conver all files except b.txt in directory_a into a.iso
```bash
mkisofs -m b.txt -r -o a.iso a/
```
## convert all files except directory_b in directory_a into a.sio
```bash
mkisofs -x b -r -o a.iso a/
```
## convert all files in directory_a into a.iso, and specify iso_creator as jack 
```bash
mkisofs -p "jack" -r -o a.iso a/
``` 
# burn iso file  
## burn CD  
### wodim  (can  be used for burning .iso into DVD as well, but that's not suggested)
```zsh
wodim -v dev=/dev/cdrom speed=4 -dao -data image.iso
# wodim = Write Optical Disk Image  
# -v = verbose, display the detailed output  
# -dao = Disc-At-Once  
```
## burn DVD (better used  for burning large amount of data ) 
### growisofs(suitable for burning large-capacity files)
#### burn iso file into dvd  
```bash
growisofs -dvd-compat -Z 'path to dev'='path to .iso'   
````
#### burn directoies into dvd
```bash
growisofs -dev-compat -z 'path to dev' -R -J 'path to directory'  
```
## xorriso
```bash
xorriso -dev 'path to dev' -map 'path to .iso' 'file name of burned .iso' -volid 'disk label' -close on -commit -eject  
```
