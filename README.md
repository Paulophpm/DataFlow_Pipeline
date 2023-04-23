# Fluxo Dados Utilizando Sharepoint e Power Data Flow

Criação de um fluxo automático de dados para um ambiente corporativo.

### Objetivo:

Criação de um fluxo automatizado de dados em nuvem que é atualizado várias vezes ao dia, sendo a fonte de dados um arquivo que tem entradas manuais imputadas por um funcionário. Sendo possível que as equipes na ponta, consiga visualizar as alterações realizadas pelo dashboard através de uma plataforma corporativa.

### Problemas:

- Como atualizar de forma contínua ou intervalada, dados de um arquivo excel que é atualizado de forma manual ?;
- Como criar um fluxo de dados automatizado com arquivos base do Sharepoint ?;
- Como tornar o fluxo de dados mais leve para carregar os dados em menos tempo ?;
- Como restringir a visualização dos dados para que cada equipe visualize apenas os seus dados ?;

### Ponto Inicial:

O arquivo inicial do projeto é uma planilha de excel (Controle_23.xlsx) que está em um ambiente de nuvem corporativa (Sharepoint), sendo essa planilha composta por abas que trazem o resultado de cada mês do referido negócio. 

A planilha é composta por inúmeras formulas que calculam diversas medidas necessárias para que as equipes na ponta consigam realizar de forma mais eficiente o andamento das suas metas.

Para deixar os dados mais leve, foi criado uma nova planilha (Base de  Dados.xlsx) que realiza uma consulta na base Controle_23.xlsx a cada 60 min. Utiliza para isso a consulta da lista do Sharepoint presente no Power Query dentro do Excel.*

* Para isso é necessário ter login e senha com autorização para acesso a referida pasta.

Obs: O Único impedimento é que a atualização entre as duas base só acontece se o arquivo a ser consultado (Controle_23.xlsx) estiver fechado, por isso o usuário terá que abrir para realizar as entradas e após imputa-las fechar o arquivo. 

Print Query Excel

Com a consulta de dados pelo query, o arquivo fica extremamente mais leve, pois a nova planilha Base de Dados.xlsx só conterá os valores do dataset original sem as formulas. 

Além disso, foi realizado o processo nas bases dos anos anteriores, com isso temos um arquivo que também contém dados histórico de uma mesma área de negócio, porém o vínculo foi quebrado, já que não há modificações dos anos anteriores.

A nova base de dados foi salva dentro ainda do mesmo ambiente nuvem.

![https://user-images.githubusercontent.com/53667656/233812878-f520cab4-b626-46cf-835a-ecf2fe7b85a0.png](https://user-images.githubusercontent.com/53667656/233812878-f520cab4-b626-46cf-835a-ecf2fe7b85a0.png)

### Power Service (Online):

Dentro do ambiente do Power Service, (sendo um usuário PRO), é possível conectar a uma base de dados a partir de uma pasta do Sharepoint. Porém ao invés de apenas conectar a base de dados, foi criado um DataFlow.

Com o DataFlow, é possível de além de se conectar com a base de dados que está na nuvem, é possível realizar as etapas de tratamento de dados na nuvem. O Power Service abrirá uma janela que será o Dax Online.

Dax Online

** Para o caso em questão todas as etapas do ETL foram feitas dentro do Power BI Desktop, assim como o visual, e após finalizado as etapas do ETL, foi dado um copia e cola no ambiente nuvem. Pois mesmo que o ambiente nuvem seja exatamente igual ao ambiente local, na nuvem o processamento das etapas acaba sendo mais lento.
