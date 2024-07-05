```bash
#!/usr/bin/bash

## echo 'Input your name', let usr input a str | save to username
echo "Input your name: \c";
read username ;

echo "Your name is $username"   # print"Your name is { username }"

## echo 'Input date with format yyyy mm dd: ', let usr input "{ year } { month } { day }" | save to year, month, day
echo "Input date with format yyyy mm dd: \c" ;
read year month day ;

echo "Today is $year/$month/$day"   # print"Today is { year }/{ month }/{ day }\n"
```