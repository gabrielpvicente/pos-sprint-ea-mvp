# pos-sprint-ea-mvp
Repositório de base para o MVP da Sprint de Engenharia de Dados da pós PUCRJ

# Objetivo
Na sprint de Machine Learning e Analytics eu trabalhei com um dataset criado para um projeto que tinha como objetivo contribuir com a redução do número de abandonos nos cursos universitários de Portugal.
A hipótese é que com base no histórico escolar do estudante, informações demográficas e socioeconômicas coletadas no momento da matrícula, somados à performance do aluno ao final do primeiro e segundo semestre, é possível prever a desistência ou sucesso acadêmico.
No final do trabalho eu encontrei os modelos de classificação com melhor acurácia para prever o abandono ou sucesso acadêmico com base nas variáveis contidas no dataset.
Contudo, não foram realizadas as análises descritivas e diagnósticas. Dessa forma, meu objetivo para o MVP da Sprint de Engenharia de Dados é entender quais os principais fatores que causaram o abandono dos cursos universitários em Portugal, buscando responder as seguintes questões:

1. Quais são os cursos com maior percentual de abandono?
2. Há diferença entre o número de abandonos devido ao período do curso (noturno ou diurno)?
3. O percentual de abandono de alunos estrangeiros é maior do que o percentual de abandono dos portugueses?
4. A qualificação dos pais parece interferir na taxa de abandono dos alunos?
5. A ocupação dos pais parece interferir na taxa de abandono dos alunos?
6. Alunos com notas de ingresso menores têm maior participação no número de abandonos?
7. Alunos com necessidades especiais têm maior tendência a abandonar o curso?
8. Qual o percentual de abandono por sexo?
9. O percentual de abandono de alunos com bolsa de estudos é menor?
10. A idade do aluno no momento do ingresso parece interferir no abandono do curso?

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

1. Quais são os cursos com maior percentual de abandono?
  
Criação de tabela temporária com a quantidade de registros por curso
<img width="676" alt="image" src="https://github.com/user-attachments/assets/a71319db-9f81-45c3-8922-2f077cb3ca86" />

Criação de tabela temporária com a quantidade de desistência por curso
<img width="677" alt="image" src="https://github.com/user-attachments/assets/fd2b072b-9d38-48cd-a44d-b26e7a0a329d" />

Query que calcula o percentual de desistência mostrando os 5 cursos com maior taxa de abandono
<img width="673" alt="image" src="https://github.com/user-attachments/assets/5c8f6395-40ee-42e8-91d1-b552bdc8cc32" />


2. Há diferença entre o número de abandonos devido ao período do curso (noturno ou diurno)?

Criação de tabela temporária com a quantidade de registros por período
<img width="676" alt="image" src="https://github.com/user-attachments/assets/45f25afa-b8d1-4ff3-950c-5e30b2eee3f8" />

Criação de tabela temporária com a quantidade de desistência por período
<img width="676" alt="image" src="https://github.com/user-attachments/assets/9745c416-8ad3-4e29-a18b-ae558716b877" />

Query que calcula o percentual de desistência mostrando que o período noturno (representado pelo inteiro 0) tem maior taxa de desistência se comparado ao período diurno (representado pelo inteiro 1)
<img width="678" alt="image" src="https://github.com/user-attachments/assets/8ee9fa25-d4c7-47b9-9294-528427b93a26" />


3. O percentual de abandono de alunos estrangeiros é maior do que o percentual de abandono dos portugueses?

Criação de tabela temporária com a quantidade de registros agrupados pelo campo "International"
<img width="676" alt="image" src="https://github.com/user-attachments/assets/254a0838-5b90-4fb0-a98d-5083ea3b1dd8" />

Criação de tabela temporária com a quantidade de desistência agrupadas pelo campo "International"
<img width="674" alt="image" src="https://github.com/user-attachments/assets/8194585f-2bd2-4320-9d35-2f174c8fcd37" />

Query que calcula o percentual de desistência mostrando equilíbrio entre a desistência de portugueses (representado pelo inteiro 0) e os estrangeiros (representado pelo inteiro 1). Mesmo que equilibrado, a desistência de portugueses mostrou-se ligeiramente maior do que a desistência de alunos de outros países.

<img width="674" alt="image" src="https://github.com/user-attachments/assets/ea975591-1be6-4c53-aa27-780bf11b7fac" />


4. A qualificação dos pais parece interferir na taxa de abandono dos alunos?

Criação de tabela temporária com a quantidade de registros por escolaridade da mãe
<img width="674" alt="image" src="https://github.com/user-attachments/assets/8ed3399e-307e-40ad-a703-ae817cc832bb" />

Criação de tabela temporária com a quantidade de desistência por escolaridade da mãe
<img width="674" alt="image" src="https://github.com/user-attachments/assets/4428967a-6c14-402a-ac21-170ac52b17b6" />

Query que calcula o percentual de desistência mostrando os 10 níveis de escolaridade das mães com maior percentual
<img width="675" alt="image" src="https://github.com/user-attachments/assets/ab0953dc-3784-4c5a-bb8d-8dfd4da41882" />

Criação de tabela temporária com a quantidade de registros por escolaridade do pai
<img width="676" alt="image" src="https://github.com/user-attachments/assets/80615989-835f-441a-89bb-487288fc2413" />

Criação de tabela temporária com a quantidade de desistência por escolaridade do pai
<img width="674" alt="image" src="https://github.com/user-attachments/assets/b1118224-a0f2-4c94-a625-febdbca40be8" />

Query que calcula o percentual de desistência mostrando os 10 níveis de escolaridade dos pais com maior percentual
<img width="675" alt="image" src="https://github.com/user-attachments/assets/be3a53ac-5c96-46ce-8ea2-33eb5d0484d6" />

Difícil achar relação entre a qualificação dos pais e a taxa de abandono dos alunos, especialmente por ter tido muitas qualificações variadas que apresentaram alta taxa de abandono dos alunos.

5. A ocupação dos pais parece interferir na taxa de abandono dos alunos?

A mesma lógica de criação de uma tabela temporária calculando a quantidade de registros por ocupação e depois uma tabela temporária calculando a quantidade de desistência por ocupação foi aplicado para a mãe e o pai.

Query que calcula o percentual de desistência mostrando as 10 ocupações das mães com maior percentual
<img width="675" alt="image" src="https://github.com/user-attachments/assets/5f819c1d-fba4-46b4-b12d-ad61de5f6932" />

Query que calcula o percentual de desistência mostrando os 10 ocupações dos pais com maior percentual
<img width="674" alt="image" src="https://github.com/user-attachments/assets/7e861a73-886f-4c0d-b450-0610132f5878" />

Alunos com pais sem ocupação ou estudantes apresentaram maior taxa de abandono.

6. Alunos com notas de ingresso menores têm maior participação no número de abandonos?

Query que obtém as 10 menores notas

<img width="674" alt="image" src="https://github.com/user-attachments/assets/85e25f7e-5d3b-4aba-8645-99d69a3b75e4" />

Query que obtém as 10 maiores notas

<img width="673" alt="image" src="https://github.com/user-attachments/assets/e36fa542-a817-480f-a892-4966ac73f832" />

Query que calcula o percentual de desistência mostrando as 10 notas com maior percentual. É possível verificar uma maior incidência de notas mais baixas nessa listagem.
<img width="676" alt="image" src="https://github.com/user-attachments/assets/4b4e5623-90d9-417c-b2b9-b39e4ee2b49f" />


7. Alunos com necessidades especiais têm maior tendência a abandonar o curso?

Query que calcula o percentual de desistência mostrando equilíbrio entre a desistência de alunos com necessidades especiais (representado pelo inteiro 1) e os alunos que não possuem necessidades especiais (representado pelo inteiro 0). Mesmo que equilibrado, a desistência de alunos com necessidades especiais mostrou-se ligeiramente maior.

<img width="674" alt="image" src="https://github.com/user-attachments/assets/3d2249ad-21d0-48bd-8e25-ae87cdb35ad7" />


8. Qual o percentual de abandono por sexo?

Query que calcula o percentual de desistência por sexo mostrando equilíbrio maior taxa de desistência do sexo masculo (representado pelo inteiro 1) do que pelo sexo feminino (representado pelo inteiro 0). Diferença de quase 20%.

<img width="675" alt="image" src="https://github.com/user-attachments/assets/ebc0b371-acbd-40d4-8172-ba18f7d6654d" />


9. O percentual de abandono de alunos com bolsa de estudos é menor?

Query que calcula o percentual de desistência mostrando maior desistência de alunos não bolsistas (representado pelo inteiro 0) do que de alunos bolsistas (representado pelo inteiro 1). Diferença de mais de 25%.
<img width="674" alt="image" src="https://github.com/user-attachments/assets/759b788e-16f3-4d39-b1f1-fb6f5c5d2796" />


10. A idade do aluno no momento do ingresso parece interferir no abandono do curso?

Query que obtém as 10 idades mais baixas no momento de ingresso

<img width="673" alt="image" src="https://github.com/user-attachments/assets/c06c9db3-6154-4f49-a541-f0d7420b342d" />

Query que obtém as 10 idades mais altas no momento de ingresso

<img width="674" alt="image" src="https://github.com/user-attachments/assets/450c14b9-5428-42ad-b8ad-ce3c942efd79" />

Query que calcula o percentual de desistência mostrando as 10 idades com maior percentual. É possível observar predominança de alunos mais velhos com maior taxa de abandono.
<img width="675" alt="image" src="https://github.com/user-attachments/assets/14078aa4-2ad8-49b8-a9fb-d0c92595b7f1" />


# Autoavaliação
Foi possível analisar e buscar respostas para as 10 questões levantadas na seção de Objetivos. Nem todas as perguntas tiveram respostas diretas, devido a complexidade e proximidade dos números obtidos, como por exemplo a pergunta 4 (A qualificação dos pais parece interferir na taxa de abandono dos alunos?). Mas o levantamento das qualificações tanto de pai quanto de mãe que apresentaram maior incidência nos abandonos foi realizado, assim como todos os levantamentos necessários para as demais perguntas.

Como mencionado na seção de Modelagem, o modelo de dados utilizado era flat, ou seja, um único arquivo que já continha todas as informações e correlações necessárias. Porém, muitas dessas informações eram representadas por IDs (números inteiros). No momento de executar a etapa de Análise e Solução do Problema, não mostrou-se factível obter esses IDs para representar valores de Curso, Grau de escolaridade e Nacionalidade, tendo que buscar o real valor no catálogo de dados. Por esse motivo, foram criadas tabelas auxiliares que ao serem utilizadas, possibilitaram a obtenção dos valores diretamente na execução das queries, sem necessidade de consulta no catálogo.

Como o dataset obtido já havia passado por um pré processamento e tratamentos necessários, não utilizamos nesse trabalho a estratégia de criar as tabelas num database raw e depois evoluí-las para camadas mais especializadas. As tabelas foram criadas e utilizadas todas num único database nomeado de bronze.

Um próximo passo interessante para esse trabalho seria a criação de gráficos para uma melhor visualização das análises realizadas.
