# xargs
## 3 columns each row
cat test.txt | xargs -n3  
## appoint 'X' as the delimeter
echo 'nameXnameXnameXname' | xargs -dX -n2  
# relocate
## multi-line writing
cat > test.txt << -EOF  
\> 123  
\> 345  
\> -EOF  
## append追加 multiple lines of txt
cat >> test.txt << -EOF  
\> 123  
\> 345  
\> -EOF  


