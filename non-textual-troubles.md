# Non-textual Troubles

* Realize that the text was ciphered using a constant seed. 
* Modify ```xor.py``` to reverse the cipher: 
```python
from random import seed, randrange 

seed(True, version=2) 

with open("ciphertext.txt", "r") as read, open("plaintext.txt", "w") as write: 
  plaintext = read.read() 
  
  for char in ciphertext: 
    A = ord(char) 
    B = randrange(256) 
    plaintext = chr(A ^ B) 
    write.write(ciphertext) 
```
* Run ```python xor.py```. 
