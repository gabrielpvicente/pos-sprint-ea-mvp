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

Criação da tabela students_dropout no database bronze e execução de SELECT para visualização de amostra dos dados.

<p align="center">
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/9e8d6662-ed03-4b10-8021-b7aeacb2b488" />
</p>

Criação da tabela de apoio marital_status no database bronze, inserção dos dados e execução de SELECT para visualização dos dados.

<p align="center">
  <img width="676" alt="image" src="https://github.com/user-attachments/assets/a51ae093-3734-4a03-8a3b-0abcd7cc7ae4" />
  <img width="676" alt="image" src="https://github.com/user-attachments/assets/2532877f-fb12-4d3e-bd5e-4eb3beeb26c9" />
  <img width="679" alt="image" src="https://github.com/user-attachments/assets/316305a2-a6e2-456f-8be9-1c2245d2d46e" />
</p>

Criação da tabela de apoio application_mode no database bronze, inserção dos dados e execução de SELECT para visualização dos dados.

<p align="center">
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/6c2f8f3f-c0e1-4d73-bfbf-2ac4164c1657" />
  <img width="676" alt="image" src="https://github.com/user-attachments/assets/6a552c90-3aa3-432a-86cf-beed438d2d82" />
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/c0533e0d-58d0-4873-96d2-9e12496b8a25" />
</p>

Criação da tabela de apoio course no database bronze, inserção dos dados e execução de SELECT para visualização dos dados.

<p align="center">
  <img width="674" alt="image" src="https://github.com/user-attachments/assets/06d90b12-485c-4dac-9123-d28972f84673" />
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/b466c812-9c58-4965-a5dc-a44318b2091e" />
  <img width="675" alt="image" src="https://github.com/user-attachments/assets/b5dd1de4-d520-4b75-97b6-6d0025c65a5a" />
</p>

Criação da tabela de apoio qualification no database bronze, inserção dos dados e execução de SELECT para visualização dos dados.

<p align="center">
  <img width="675" alt="image" src="https://github.com/user-attachments/assets/84205ae0-8b56-4e5e-a96b-b176c65227a8" />
  <img width="676" alt="image" src="https://github.com/user-attachments/assets/c4c8b6be-f3b5-4adc-b507-6d8dc96d036a" />
  <img width="678" alt="image" src="https://github.com/user-attachments/assets/6c6afc24-48f0-4bf9-9f44-6be856a3b9f7" />
</p>

Criação da tabela de apoio nationality no database bronze, inserção dos dados e execução de SELECT para visualização dos dados.

<p align="center">
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/f317eebb-da56-4f7e-a874-a01e97f3d91d" />
  <img width="679" alt="image" src="https://github.com/user-attachments/assets/0937afea-8160-4aad-931f-3202c7988dc5" />
  <img width="680" alt="image" src="https://github.com/user-attachments/assets/cfc4808b-c3b7-47e4-b272-197e58b05ebc" />
</p>

Criação da tabela de apoio occupation no database bronze, inserção dos dados e execução de SELECT para visualização dos dados.

<p align="center">
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/9510ae90-cd11-4f24-9675-0c3537fbcaad" />
  <img width="676" alt="image" src="https://github.com/user-attachments/assets/b2d62ae1-580e-42a9-ba06-313649ce140e" />
  <img width="677" alt="image" src="https://github.com/user-attachments/assets/89ebc6e0-d8d3-4656-b9a3-95ee4ac5ccc2" />
</p>


## 5. Análise
###  a. Qualidade de dados

Na página de onde o dataset foi retirado, está descrito que o mesmo passou por pré processamento para lidar com anomalias, registros atípicos (outliers) e também valores faltantes/em branco/nulos.

Abaixo estão evidenciadas algumas validações feitas para garantir a qualidade do dataset:

**Verificar Nulos:** Realiza uma contagem da quantidade de valores nulos encontrados em cada coluna.
Nenhum valor nulo encontrado em nenhuma das colunas.
<p align="center">
  <img width="676" alt="image" src="https://github.com/user-attachments/assets/5855b631-beda-4f6b-b600-7588e11d9ff9" />
</p>

**Verificar Duplicatas:** Realiza uma contagem da quantidade de vezes que cada registro apareceu e mostra aqueles que apareceram mais de uma vez.
Nenhum registro apareceu mais de 1 vez no dataset.
<p align="center">
  <img width="674" alt="image" src="https://github.com/user-attachments/assets/beacc20a-4292-489b-8511-edca758eb0cc" />
</p>


###  b. Solução do problema

- Quais são os cursos com maior percentual de abandono?
  
Criação de tabela temporária com a quantidade de registros por curso
<img width="676" alt="image" src="https://github.com/user-attachments/assets/a71319db-9f81-45c3-8922-2f077cb3ca86" />

Criação de tabela temporária com a quantidade de desistência por curso
<img width="677" alt="image" src="https://github.com/user-attachments/assets/fd2b072b-9d38-48cd-a44d-b26e7a0a329d" />

Query que calcula o percentual de desistência mostrando os 5 cursos com maior percentual
<img width="673" alt="image" src="https://github.com/user-attachments/assets/5c8f6395-40ee-42e8-91d1-b552bdc8cc32" />

- Há diferença entre o número de abandonos devido ao período do curso (noturno ou diurno)?

Criação de tabela temporária com a quantidade de registros por período
<img width="676" alt="image" src="https://github.com/user-attachments/assets/45f25afa-b8d1-4ff3-950c-5e30b2eee3f8" />

Criação de tabela temporária com a quantidade de desistência por período
<img width="676" alt="image" src="https://github.com/user-attachments/assets/9745c416-8ad3-4e29-a18b-ae558716b877" />

Query que calcula o percentual de desistência mostrando que o período noturno (representado pelo inteiro 0) tem maior percentual de desistência se comparado ao período diurno (representado pelo inteiro 1)
<img width="678" alt="image" src="https://github.com/user-attachments/assets/8ee9fa25-d4c7-47b9-9294-528427b93a26" />

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

# Autoavaliação

