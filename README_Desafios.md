
# Desafios Power Bi Analyst

Resolvendo os desafios de projeto do curso de Power BI Analyst do Bootcamp Santantder 2023 - Ciência de Dados com Python.

✅Status: Concluído ✅

### Tabela de Conteúdos
- [Sobre o Projeto](#Sobre-o-Projeto)
- [Criação do Relatório](#-etapa-1-:-criação-do-relatório)
- [Coleta e Transformação dos Dados](#-Etapa-2-:-Coleta-e-transformação-dos-dados)
    - [Coleta](#-coleta)
    - [Transformação](#-tranformação)
- [Ferramentas Utilizadas](#-Ferramentas-Utilizadas)


## Sobre o Projeto 
O projeto será dividido em duas partes, referentes aos dois desafios do curso. 
A primeira será a criação de um relatório de vendas baseado na sample Financials do próprio Power BI. 
O objetivo é treinar as competências relacionadas à criação de relatórios e uso da ferramenta de visualização do Powr BI.
Na segunda parte será feita a coleta, obtenção e transformação dos dados utilizando Power BI e MySQL na Azure.

## Etapa 1: Criação do relatório

O relatório criado tem duas páginas relacionadas as vendas da empresa. A primeira contém um overview, com métricas de quantidade de produtos vendidos, custos e total de vendas. E gráficos segmentando as vendas por localidade, tipo de produto e outros.
A segunda página contém um relatório mais detalhado do lucro da empresa.

## Etapa 2: Coleta e transformação dos dados

Para essa parte do projeto criei um passo a passo das alterações feitas no banco de dados. Lembre-se de sempre manter um cópia do arquivo original do banco de dados antes de fazer qualquer alteração irreversível.

### Coleta

Os dados foram obtidos através de um script de SQL passados pela prórpia professora do curso de Power BI. 
É um banco de dados teste com informações de projetos, horas trabalhadas e colaboradores de uma empresa fictícia.

O banco de dados foi criado no MySQL do Azure e posteriormente ele foi conectado ao Power BI para realizarmos as transformações necessárias. 

### Transformação
Essas foram as etapas de transformação do banco de dados com algumas justificativas do porque de cada passo.
- *Remoção de colunas:* Durante o processo de carregamento dos dados do MySQL para o Power BI, algumas colunas referentes às chaves estrangeiras são adicionas ao fim de cada tabela. Como essas colunas não são necessárias e o Power BI faz esse relacionamento sozinho, podemos excluí-las.
- *Verificação dos tipos de dados:* Todos os tipos de dados foram verificados e não foi necessário fazer modificações. 
    - Os valores de 'Ssn' foram mantidos como tipo Texto para facilitar futuras manipulações.
- *Verificando Nulos:* O único valor vazio encontrado foi na coluna _Employee_ , na coluna _Super_ssn_. Esse vazio indica que o colaborador não possui um gerente. 
    - Com o auxílio da tabela _Departments_, verificamos que esse colaborador é o gerente geral da empresa. E, por isso, faz sentido que ele não tenha um gerente.
    - Todos os demais colaboradores possuem um gerente. E não existe um departamento sem gerente.
- *Separação de Colunas Complexas:* Fiz a separação da coluna de endereço em partes separadas, sendo elas: _Address Number_, _Address_, _City_, _State_.
    - Antes de fazer a separação fiz uma substituição em um dos valores para evitar um erro durante a separação.
- *Mesclar Colunar de Nome e Sobrenome:* Para facilitar a próximas etapa mesclei as colunas _Fname_, _Minit_, _Lname_ na tabela _Employee_. 
- *Mesclar Consultas - _Employee_ & _Department_:* Utilizei a tabela _Employee_ como base e juntei com base no número do departamento. Fiz uma junção a esquerda mantendo todos os registros da tabela de colaboradores, criando uma nova consulta. 
    - Nessa nova consulta, expandi a tabela _Department_ e selecionei apenas o nome do departamento. Renomeei a consulta para "employee-dept"
- *Mesclar Consultas - _Employee_ & _Department_*: Essa mescla de consultas será feita para obter uma nova tabela com os oclaboradores e seus respectivos gerentes. Para isso fiz a mescla de tabelas duas vezes.
    - A primeira utilizando as seguintes colunas "_Manager_ssn_" e "_Ssn_". Para obter o nome de cada gerente.
    - A segunda, fiz a mescla da tabela anteiror com a tabela _Employee_ novamente. Dessa vez juntando as colunas "_Manager_ssn_" e "_Super_ssn_" para obter os gerentes relacionados a cada colaborador.
    - Exclui as demais colunas, mantendo apenas o nome dos gerentes e colaboradores.
    - Obs: O colaborador que não possuía um _Super_ssn_ atrelado ficou com um valor de gerente nulo. Já havíamos constatado que ele é o gerente geral da empresa e, por isso, essa valor vazio faz sentido. Porém, não precisamos disso na tabela atual, então vou excluir essa linha.
    - Renomeei a consulta como "manager-employee"
- *Mesclar Consultas - _Department_ & _Location_*: mesclei essas duas tabelas utilizando o número do departamento para realizar a junção. 
    - O objetivo era pegar a localização de cada departamento e criar uma nova coluna com nome do departamento + localização. Já que existem filiais e um departamento pode estar localizado em cidades diferentes.
- *Mesclar Consultas - _Department_ & _Projects_:* para obter o nome do departamento relacionado a cada projeto mesclei as tabelas utilizando a identificação de cada departamento. 
    - Após a mescla das tabelas removi as duplicatas. 

## Ferramentas Utilizadas

Foram utilizadas as seguintes ferramentas para o desenvolvimento desse projeto:
- [Power BI]()
- [MySQL]()
- [Azure]()
- [MySQL Workbench]()

Além disso, esses são os dados necessário para realização desse projeto:
- [Sample Financials]()
- [Código SQL para criação do Dataset]()




# Desafios Power Bi Analyst

Resolvendo os desafios de projeto do curso de Power BI Analyst do Bootcamp Santantder 2023 - Ciência de Dados com Python.

✅Status: Concluído ✅

### Tabela de Conteúdos
- [Sobre o Projeto](#Sobre-o-Projeto)
- [Criação do Relatório](#-etapa-1-:-criação-do-relatório)
- [Coleta e Transformação dos Dados](#-Etapa-2-:-Coleta-e-transformação-dos-dados)
    - [Coleta](#-coleta)
    - [Transformação](#-tranformação)
- [Ferramentas Utilizadas](#-Ferramentas-Utilizadas)


## Sobre o Projeto 
O projeto será dividido em duas partes, referentes aos dois desafios do curso. 
A primeira será a criação de um relatório de vendas baseado na sample Financials do próprio Power BI. 
O objetivo é treinar as competências relacionadas à criação de relatórios e uso da ferramenta de visualização do Powr BI.
Na segunda parte será feita a coleta, obtenção e transformação dos dados utilizando Power BI e MySQL na Azure.

## Etapa 1: Criação do relatório

O relatório criado tem duas páginas relacionadas as vendas da empresa. A primeira contém um overview, com métricas de quantidade de produtos vendidos, custos e total de vendas. E gráficos segmentando as vendas por localidade, tipo de produto e outros.
A segunda página contém um relatório mais detalhado do lucro da empresa.

## Etapa 2: Coleta e transformação dos dados

Para essa parte do projeto criei um passo a passo das alterações feitas no banco de dados. Lembre-se de sempre manter um cópia do arquivo original do banco de dados antes de fazer qualquer alteração irreversível.

### Coleta

Os dados foram obtidos através de um script de SQL passados pela prórpia professora do curso de Power BI. 
É um banco de dados teste com informações de projetos, horas trabalhadas e colaboradores de uma empresa fictícia.

O banco de dados foi criado no MySQL do Azure e posteriormente ele foi conectado ao Power BI para realizarmos as transformações necessárias. 

### Transformação
Essas foram as etapas de transformação do banco de dados com algumas justificativas do porque de cada passo.
- *Remoção de colunas:* Durante o processo de carregamento dos dados do MySQL para o Power BI, algumas colunas referentes às chaves estrangeiras são adicionas ao fim de cada tabela. Como essas colunas não são necessárias e o Power BI faz esse relacionamento sozinho, podemos excluí-las.
- *Verificação dos tipos de dados:* Todos os tipos de dados foram verificados e não foi necessário fazer modificações. 
    - Os valores de 'Ssn' foram mantidos como tipo Texto para facilitar futuras manipulações.
- *Verificando Nulos:* O único valor vazio encontrado foi na coluna _Employee_ , na coluna _Super_ssn_. Esse vazio indica que o colaborador não possui um gerente. 
    - Com o auxílio da tabela _Departments_, verificamos que esse colaborador é o gerente geral da empresa. E, por isso, faz sentido que ele não tenha um gerente.
    - Todos os demais colaboradores possuem um gerente. E não existe um departamento sem gerente.
- *Separação de Colunas Complexas:* Fiz a separação da coluna de endereço em partes separadas, sendo elas: _Address Number_, _Address_, _City_, _State_.
    - Antes de fazer a separação fiz uma substituição em um dos valores para evitar um erro durante a separação.
- *Mesclar Colunar de Nome e Sobrenome:* Para facilitar a próximas etapa mesclei as colunas _Fname_, _Minit_, _Lname_ na tabela _Employee_. 
- *Mesclar Consultas - _Employee_ & _Department_:* Utilizei a tabela _Employee_ como base e juntei com base no número do departamento. Fiz uma junção a esquerda mantendo todos os registros da tabela de colaboradores, criando uma nova consulta. 
    - Nessa nova consulta, expandi a tabela _Department_ e selecionei apenas o nome do departamento. Renomeei a consulta para "employee-dept"
- *Mesclar Consultas - _Employee_ & _Department_*: Essa mescla de consultas será feita para obter uma nova tabela com os oclaboradores e seus respectivos gerentes. Para isso fiz a mescla de tabelas duas vezes.
    - A primeira utilizando as seguintes colunas "_Manager_ssn_" e "_Ssn_". Para obter o nome de cada gerente.
    - A segunda, fiz a mescla da tabela anteiror com a tabela _Employee_ novamente. Dessa vez juntando as colunas "_Manager_ssn_" e "_Super_ssn_" para obter os gerentes relacionados a cada colaborador.
    - Exclui as demais colunas, mantendo apenas o nome dos gerentes e colaboradores.
    - Obs: O colaborador que não possuía um _Super_ssn_ atrelado ficou com um valor de gerente nulo. Já havíamos constatado que ele é o gerente geral da empresa e, por isso, essa valor vazio faz sentido. Porém, não precisamos disso na tabela atual, então vou excluir essa linha.
    - Renomeei a consulta como "manager-employee"
- *Mesclar Consultas - _Department_ & _Location_*: mesclei essas duas tabelas utilizando o número do departamento para realizar a junção. 
    - O objetivo era pegar a localização de cada departamento e criar uma nova coluna com nome do departamento + localização. Já que existem filiais e um departamento pode estar localizado em cidades diferentes.
- *Mesclar Consultas - _Department_ & _Projects_:* para obter o nome do departamento relacionado a cada projeto mesclei as tabelas utilizando a identificação de cada departamento. 
    - Após a mescla das tabelas removi as duplicatas. 

## Ferramentas Utilizadas

Foram utilizadas as seguintes ferramentas para o desenvolvimento desse projeto:
- [Power BI]()
- [MySQL]()
- [Azure]()
- [MySQL Workbench]()

Além disso, esses são os dados necessário para realização desse projeto:
- [Sample Financials]()
- [Código SQL para criação do Dataset]()



