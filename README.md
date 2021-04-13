# Baixar-bases-de-dados-do-KAGGLE-para-o-GOOGLE-DRIVE-usando-o-GOOLE-COLAB.ipynb

# Baixar imagagens do Kaggle

1 - Segue o tutorial

https://medium.com/@marcelmartinsbittar/como-importar-um-dataset-do-kaggle-para-o-google-colab-a79c47005e6d

2 - Depois de extraindo a base mova para uma pasta no seu drive


Exemplo de API da base -> kaggle datasets download -d tawsifurrahman/covid19-radiography-database



## Conectar o DRIVE com o COLAB

from google.colab import drive
drive.mount('/content/drive')

## Baixar base do KAGGLE

#!pip install kaggle; #caso seja necessário atualizar a biblioteca no google colab

from google.colab import files
files.upload() #enviar o arquivo kaggle.json Esse ARQUIVO tem ser gerado a partir da sua conta no Kaggle nos 3 do lado da foto do perfil

#antes de importar o dataset nós iremos provisionar o local de armazenamento
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
#Alterar a permissão para evitar o aviso durante a partida da ferramenta Kaggle
# This permissions change avoids a warning on Kaggle tool startup.
!chmod 600 ~/.kaggle/kaggle.json

#Aceitar a competição e copiar o endereço da API para o download do dataset
#!kaggle competitions download -c house-prices-advanced-regression-techniques

#-d api da base para baixar e -p é o diretorio no google drive
!kaggle datasets download -d tawsifurrahman/covid19-radiography-database -p /content/drive/MyDrive/Dissertação/teste


## Descompactar pasta no COLAB


#Descompactar o arquivo baixado do drive aqui no COLAB. No drive tem a opção de descompactar direto lá
!unzip /content/drive/MyDrive/Dissertação/teste/*.zip  && rm *.zip

## Mover Pasta


# move as pastas extraida aqui do colab para o drive, é demorodo um pouco demorado mais pode ajudar em algum momento
! mv COVID-19_Radiography_Dataset/ /content/drive/MyDrive/Dissertação/teste
