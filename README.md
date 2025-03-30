# pos-sprint-ea-mvp
Repositório de base para o MVP da Sprint de Engenharia de Dados da pós PUCRJ

# Objetivo
Na sprint de Machine Learning e Analytics eu trabalhei com um dataset criado para um projeto que tinha como objetivo contribuir com a redução do número de abandonos nos cursos universitários de Portugal.
A hipótese é que com base no histórico escolar do estudante, informações demográficas e socioeconômicas coletadas no momento da matrícula, somados à performance do aluno ao final do primeiro e segundo semestre, é possível prever a desistência ou sucesso acadêmico.
No final do trabalho eu encontrei os modelos de classificação com melhor acurácia para prever o abandono ou sucesso acadêmico com base nas variáveis contidas no dataset.
Contudo, não foram realizadas as análises descritivas e diagnósticas. Dessa forma, meu objetivo para o MVP da Sprint de Engenharia de Dados é entender quais os principais fatores que causaram o abandono dos cursos universitários em Portugal, buscando responder as seguintes questões:

- Quais são os cursos com maior percentual de abandono?
- Há diferença entre o número de abandonos devido ao período do curso (noturno ou diurno)?
- O percentual de abandono de alunos estrangeiros é maior do que o percentual de abandono dos portugueses?
- A qualificação dos pais parece interferir na taxa de abandono dos alunos?
- A ocupação dos pais parece interferir na taxa de abandono dos alunos?
- Alunos com notas de ingresso menores têm maior participação no número de abandonos?
- Alunos com necessidades especiais têm maior tendência a abandonar o curso?
- Qual o percentual de abandono por sexo?
- O percentual de abandono de alunos com bolsa de estudos é menor?
- A idade do aluno no momento do ingresso parece interferir no abandono do curso?
- Alunos com reprovações no primeiro semestre tendem a abandonar o curso?
- Alunos com reprovações no segundo semestre tendem a abandonar o curso?
- Qual o percentual de abandono com base nos índices nacionais como taxa de desemprego, inflação e PIB?

# Detalhamento
## 1. Busca pelos dados
A base de dados que será utilizada tem como título "Predict Students' Dropout and Academic Success" e foi retirada do UC Irvine Machine Learning Repository.

UC Irvine Machine Learning Repository: https://archive.ics.uci.edu/

Predict Students' Dropout and Academic Success Dataset: https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success

Os dados presentes nesse dataset são provenientes de diversos databases. Alguns dados são coletados no momento da matrícula do aluno (histórico escolar, informações demográficas e socioeconômicas) e outros dados relacionados à performance do aluno durante o curso são coletados ao final do primeiro e segundo semestre da graduação. Os dados são referentes à alunos de universidades portuguesas, porém, não há uma definição de quais ou quantas universidades contribuíram com o dataset.

O dataset em questão está licensiado sob a [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/legalcode) e pode ser compartilhado e adaptado desde que mencionada a sua origem.

## 2. Coleta
O dataset foi baixado do link referenciado na seção acima e feito o upload num repositório do github: https://github.com/gabrielpvicente/pos-sprint-ml-a-mvp/blob/main/data.csv

A coleta desse dataset e carregamento para dentro do Databricks foi realizada fazendo a leitura com a biblioteca pandas, como é possível ver na imagem abaixo:
<p align="center">
  <img width="680" alt="image" src="https://github.com/user-attachments/assets/16f941c4-d7d2-426a-a145-3d6b174bb108" />
</p>

## 3. Modelagem
O modelo de dados que será utilizado é flat, com um dataset único que foi construído e disponibilizado no UC Irvine Machine Learning Repository à partir da junção de diversas tabelas distintas com informações demográficas, socioeconômicas e histórico escolar do estudante.

Abaixo temos um Catálogo de Dados com o nome das colunas, tipo de dado, uma descrição (tradução para o português), valores esperados/possíveis e um informativo da existência ou não de registros nulos/vazios para a respectiva coluna.

Para facilitar o manuseio do dataset, várias colunas como o Curso, Grau de escolaridade e Nacionalidade, são do tipo inteiro. Dessa forma, será necessário recorrer ao Catálogo de Dados no momento da análise para correlacionar os números aos valores (Exemplo: O inteiro 9070 representa o curso de Communication Design). 

Caso necessário, a imagem abaixo está disponibilizada também em formato xlsx no seguinte link: 

https://github.com/gabrielpvicente/pos-sprint-ea-mvp/blob/main/Modelagem%20-%20MVP%20-%20Eng%20Dados.xlsx

![image](https://github.com/user-attachments/assets/df95ea03-648a-4dce-ad37-4dc2314794b3)

## 4. Carga
Execução dos comandos para deleção do database "bronze" caso o mesmo já exista e posterior criação do database.

<p align="center">
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/e46a0dfe-606e-41e9-abbf-bacf06e07a60" />
</p>

Criação de spark dataframe e exibição do schema.

<p align="center">
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/d004eba6-075b-4540-8f3c-cfb2a346b2fd" />
</p>


Renomeação das colunas para substituição de caracteres especiais que não são aceitos pelo spark em nomes de colunas no momento da criação das tabelas.

<p align="center">
  <img width="674" alt="image" src="https://github.com/user-attachments/assets/e50eb08e-e761-4e6c-9cec-496c551a3243" />
</p>

Criação da tabela no database bronze e execução de SELECT para visualização de amostra dos dados.

<p align="center">
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/9e8d6662-ed03-4b10-8021-b7aeacb2b488" />
</p>

## 5. Análise
###  a. Qualidade de dados

###  b. Solução do problema

# Autoavaliação

