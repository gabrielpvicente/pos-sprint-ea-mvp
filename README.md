# pos-sprint-ea-mvp
Repositório de base para o MVP da Sprint de Engenharia de Dados da pós PUCRJ

# Objetivo
Na sprint de Machine Learning e Analytics eu trabalhei com um dataset criado para um projeto que tinha como objetivo contribuir com a redução do número de abandonos nos cursos universitários de Portugal.
A hipótese é que com base no histórico escolar do estudante, informações demográficas e socioeconômicas coletadas no momento da matrícula, somados à performance do aluno ao final do primeiro e segundo semestre, é possível prever a desistência ou sucesso acadêmico.
No final do trabalho eu encontrei os modelos de classificação com melhor acurácia para prever o abandono ou sucesso acadêmico com base nas variáveis contidas no dataset.
Contudo, não foram realizadas as análises descritivas e diagnósticas. Dessa forma, meu objetivo para o MVP da Sprint de Engenharia de Dados é entender quais os principais fatores que causam o abandono dos cursos universitários em Portugal, buscando responder as seguintes questões:

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

Os dados presentes nesse dataset são provenientes de diversos databases. Alguns dados são coletados no momento da matrícula do aluno (histórico escolar, informações demográficas e socioeconômicas) e outros dados relacionados à performance do aluno no início do curso são coletados ao final do primeiro e segundo semestre da graduação. Os dados são referentes à alunos de universidades portuguesas, porém, não há uma definição de quais ou quantas universidades contribuíram com o dataset.

O dataset em questão está licensiado sob a [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/legalcode) e pode ser compartilhado e adaptado desde que mencionada a sua origem.

## 2. Coleta
O dataset foi baixado do link referenciado na seção acima e feito o upload num repositório meu do github: https://github.com/gabrielpvicente/pos-sprint-ml-a-mvp/blob/main/data.csv

A coleta do mesmo para dentro do Databricks foi realizada fazendo a leitura com a biblioteca pandas, como é possível ver na imagem abaixo:
<img width="680" alt="image" src="https://github.com/user-attachments/assets/16f941c4-d7d2-426a-a145-3d6b174bb108" />


## 3. Modelagem

![image](https://github.com/user-attachments/assets/d168b683-f168-4332-aedd-d3ac08bf04f3)


## 4. Carga

## 5. Análise
###  a. Qualidade de dados

###  b. Solução do problema

# Autoavaliação

