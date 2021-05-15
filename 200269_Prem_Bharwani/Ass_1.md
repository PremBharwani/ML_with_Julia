# Bandit Submission by Prem Bharwani

#### 0->1:
get the password from the readme file and use ssh command with the given port 
#### 1->2
'-' character can't be directly used with the 'cat' command , because it is misinterpreted for stdin. We use 'cat ./-'
#### 2->3
Use cat along with : use '\' to escape the spaces in the filename OR put the filename in single quotes
#### 3->4
use '$ ls -a' and then cat
#### 4->5
`$ for FILE in *; do cat ./$FILE;echo '\n'; done`

using the above command it will loop through all the files and you can figure out the readable one :)
#### 5->6
`$ ls -alR | grep --line-number 1033`

(use this to get the line number of a file with 1033 bytes and it also matches the given description)

`$ ls -alR | head -n 131`

(Figure out the directory in which this file belongs and get your answer , use cat directly to get the passwd)
#### 6->7
Just go to the '/' and just recursively search for a file owned by bandit7 and bandit6 group

`$ ls -alR | grep --line-number 'bandit7 bandit6'`

(you get the line number that corresponds to the o/p from 'ls -alR')
So now use the head command along with the line number to get the files location 

`$ ls -aRl | head -n 160813`

#### 7->8
`$ cat data.txt | grep millionth`

Using the above command we can get it 
#### 8->9
`$ sort data.txt | uniq -u`

Using sort we can 'club' all the common occurences together . And then 'uniq' command can figure out unique the unique phrase .
#### 9->10
Extract out the printable characters using the strings command 

`$ strings data.txt | grep =`

#### 10->11
straightforward use of 'base64' command : 
`$	base64 -d data.txt`
#### 11->12
this uses the rot13 algo , we can undo this by using the 'tr' command :

$ tr 'a-mA-Mn-zN-Z' 'n-zN-Za-mA-M' < data.txt 
#### 12->13
Firstly use 'xxd' to convert the hexdump back into the file , and then use the 'file' command to understand what kind of file this is , and accordingly use 'gzip' , 'bzip2' or 'tar' at each step with maximum decompression !
Also take note that when using gzip , you have to ensure that the file name is renamed to '*.gz' kind . 

#### 13->14
Take the ssh private key to the local computer and then use ssh command with '-i' arguement to log in .
#### 14->15
Just use netcat('nc' command) to connect to the specific port ,and then supply the password for the current level.
$ nc localhost 30000
#### 15->16
Use openssl to make a secure connection to the localhost at port 30001 and submit the password .

`$ openssl s_client -connect localhost:30001`

#### 16-> 17
Firstly we’ll figure out the open ports using the nmap command :
`$ nmap -p 31000-32000 localhost`
This will give us the list of available ports , now we will use openssl to establish a ssl connection with each of the ports and give the password , you will see that one  of them returns a RSA key for the next level. Which we can use to login using ssh .
`$ openssl s_client -connect localhost:31790`

#### 17->18
Basic use of diff command
`$ diff passwords.new passwords.old`
You will find out what has changed , so use the line from the ‘passwords.new’ file.		


#### Below are the passwords I obtained for each level:
1 : boJ9jbbUNNfktd78OOpsqOltutMc3MY1
2 :CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
4 : pIwrPrtPN36QITSp3EQaw936yaFoFgAB
5 : koReBOKuIDDepwhWk7jZC0RTdopnAYKh
6 : DXjZPULLxYr17uwoI01bNLQbtFemEgo7
7 : HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
8 : cvX2JJa4CFALtqS87jk27qwqGhBM9plV
9 : UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
10 ; truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
11 : IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
12 : 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
13 : 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
-----END RSA PRIVATE KEY-----

14 : 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
15 : BfMYroe26WYalil77FoDi9qh59eK5xNr
16 : cluFn7wTiGryunymYOu4RcffSxQluehd
17 : RSA key :
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

18 : kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
