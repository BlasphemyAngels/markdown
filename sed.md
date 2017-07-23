
### command format

* sed [option] [sed-command] [input]

&ensp;&ensp;&ensp;print the result default, use option `-n` can cancel it.

### flow of execution

### range of address

* `sed '2,5d' input.txt` 2-5
* `sed '2d' input.txt` 2
* `sed '2,+5d' input.txt` 2-7
* `sed '1~2d' input.txt` 1,3,5,7,9,...
* `sed '10,$d' input.txt` 10-end
* `sed '1~2d' input.txt` 1,3,5,7,9,...
* `n1[,n2]{sed-command}`

&ensp;&ensp;&ensp;range of address also support the regular expression

* `/caochenglong/{sed-command}`
* `/caochenglong/,/lixiaolong/{sed-command}`
* `/caochenglong/, ${sed-command}`
* `10,/caochenglong/{sed-command}`

&ensp;&ensp;&ensp;if there are multiple matches, you will rethink the flow of execution

### option

### sed-command

#### add

* single line
  * a `sed '2a i am a text' input.txt`
  * i `sed '2i i am a text' input.txt`
* multiple lines
  * a `sed '2a i am a\n text' input.txt` or enter '\n' when input order

#### delete

* single line
  * sed 'd' input.txt  delete all the content
  * sed '2d' input.txt delete the second line in the input file'

#### substitute

* c `sed '2c i am a text' input.txt` change the second line.
* s substitute the specify string.
* g the signature of the command`s`
* `sed -i 's/ / /g' input.txt`
* `sed -i 's# # #g' input.txt`
* variable substitute
```sh
x=1
y=2
echo $x, $y
```
* `sed "s#$x#$y#g" input.txt` can
* `sed 's#$x#$y#g' input.txt` can't `eval sed 's#$x#$y#g' input.txt` can
* `sed s#$x#$y#g input.txt` can
* group substitute : use the group of the regular expression
* `&`all groups `\1` first group `\2` second group ...
* `ls *.jpg | sed -r 's#(.*)_finished.*#mv & \1.jpg#g'`

#### print

* p `sed '2p' inpout.txt`
* option`-i` cancel the default output

#### change file

* `-i` use the option change the file
* `sed -i.ori 's#ccl#NB#g' person.txt` backup the file
