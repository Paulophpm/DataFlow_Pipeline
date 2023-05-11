## Fluxo de Dados Automatizado Utilizando Sharepoint e Power Data Flow 

Criação de um fluxo automático de dados para um ambiente nuvem corporativo.

### Objetivo:

Criação de um fluxo automatizado de dados em nuvem que é atualizado várias vezes ao dia, sendo a fonte de dados um arquivo que tem entradas manuais imputadas por um funcionário. Sendo possível que as equipes na ponta, consiga visualizar as alterações realizadas pelo dashboard através de uma plataforma corporativa.

### Problemas:

- Como atualizar de forma contínua, dados de um arquivo excel que é atualizado de forma manual ?;
- Como criar um fluxo de dados automatizado com arquivos base do Sharepoint ?;
- Como tornar o fluxo de dados mais leve para carregar os dados em menos tempo ?;
- Como restringir a visualização dos dados para que cada equipe visualize apenas os seus dados ?;

## Ponto Inicial:

O arquivo inicial do projeto é uma planilha de excel (Controle_23.xlsx) que está em um ambiente de nuvem corporativa (Sharepoint), sendo essa planilha composta por abas que trazem o resultado de cada mês do referido negócio. 

A planilha é composta por inúmeras formulas que calculam diversas medidas necessárias para que as equipes na ponta consigam realizar de forma mais eficiente o andamento das suas metas.

Para deixar os dados mais leve, foi criado uma nova planilha (Base de  Dados.xlsx) que realiza uma consulta na base Controle_23.xlsx a cada 60 min. Utiliza para isso a consulta da lista do Sharepoint presente no Power Query dentro do Excel.*

* Para isso é necessário ter login e senha com autorização para acesso a referida pasta.

### Conexão com a Base de Dados:

O início do processo começar em conectar novo arquivo da base de dados. Com o link da página inicial do Sharepoint é possível encontrar a pasta da qual se encontra o arquivo e assim conseguir conectar a fonte de dados.

Obs: Para conseguir acessar a pasta irá ser solicitado algum tipo de verificação como a conta corporativa, ou algum login e senha para conseguir acesso.

![Untitled](https://user-images.githubusercontent.com/53667656/234136717-ff5fecf2-29fe-4273-ac0b-56012e69e57a.png)

Com a consulta de dados pelo query, o arquivo fica extremamente mais leve passando de x bytes do arquivo original para y bytes no arquivo destino, pois a nova planilha só conterá apenas a consulta com os valores do dataset original.

Além disso, se for necessário, é possível tratar de forma prévia os dados do arquivo original podendo até fazer uma boa parte do ETL.

Porém ainda é necessário fazer com que essa consulta seja atualizada de forma constante, para isso dentro da consulta gerado, na parte de propriedades é possível configurar a atualização periódica através de um período determinado de tempo. E que mesmo assim essa consulta seja atualizada em segundo plano.

![Untitled (1)](https://user-images.githubusercontent.com/53667656/234136806-443c5b2d-911b-45a7-9b4c-3d7e57198fcc.png)

** Obs: Obs: De acordo com a Microsoft, quando é criado uma atualização em segundo plano de uma consulta de dados, a planilha sempre atualizada no tempo estipulado, porém alguns dias após os teste a atualização entre as duas base só acontece se o arquivo a ser consultado estiver fechado, por isso o usuário terá que abrir o arquivo para realizar as entradas, e após imputa-las fechar o arquivo.

Além disso, foi realizado o processo nas bases dos anos anteriores, com isso temos um arquivo que também contém dados histórico de uma mesma área de negócio, porém o vínculo foi quebrado, já que não há modificações dos anos anteriores.

A nova base de dados foi salva dentro ainda do mesmo ambiente nuvem, pois isso é um pré-requisito, de acordo com a Microsoft, para que a atualização em segundo plano funcione

![Untitled](https://user-images.githubusercontent.com/53667656/236357077-adea5c05-81c9-454d-8150-a244013bd59f.png)

### Power Service (Online):

Dentro do Workspace do Power Service, (sendo um usuário PRO), é possível conectar a uma base de dados a partir de uma pasta do Sharepoint. Porém ao invés de apenas conectar a base de dados, foi criado a conexão através do Fluxo de Dados.

Com o Fluxo de Dados, é possível de além de se conectar com a base de dados que está na nuvem, é possível realizar as etapas de tratamento desses dados na nuvem. O Power Service abre uma janela que é exatamente igual ao DAX em que você pode realizar as mesmas etapas e os mesmos processos do Power BI Desktop.

** Para o caso em questão, todas as etapas do ETL foram feitas dentro do Power BI Desktop, assim como o visual, e após finalizado as etapas do ETL, você pode selecionar e arrastar as etapas do DAX Desktop para o DAX online. Pois mesmo que o ambiente nuvem seja exatamente igual ao ambiente local, na nuvem o processamento das etapas acaba sendo mais lento

Através do Dataflow também é possível configurar alguns parâmetros rápidos de Aprendizado de Máquina, mas que estará em outro repertório.

![Untitled (2)](https://user-images.githubusercontent.com/53667656/236357874-73f50c8d-cac8-4dd9-ac61-efad83859e15.png)

O arquivo desktop que foi criado anteriormente para que as etapas do DAX permaneceu ainda dentro do projeto, porém com o objetivo de trazer e testar novas funcionalidades para o fluxo, e trazer novas visualizações para os relatórios.

![Untitled](https://github.com/Paulophpm/DataFlow_Pipeline/assets/53667656/98700869-6e95-4148-abb2-b2f08d38a352)

Mesmo assim, ainda é necessário fazer o agendamentos das atualizações do fluxo de dados, pois da forma como está ainda não está um fluxo contínuo de dados, sendo uma atualização do Sharepoint para DataFlow e outro agendamento do Dataflow para o novo banco de dados criado.

Quando o banco de dados é atualizado, o Dashboard também é atualizado de forma automática, mesmo que existam mais de um relatório que utilize o mesmo banco de dados.

No caso em questão a empresa tem uma plataforma interna para a disponibilização de relatórios, que tem uma conexão direta com o Power Service, e logo quando se é atualizado o relatório, automaticamente o mesmo fica disponível na plataforma de dados.

### O Fluxo Final:

O Fluxo Final consiste em um esquema que une um fluxo de dados com origem do Sharepoint que é atualizado de forma periódica durante o decorrer do dia. Dessa forma foi possível resolver o problema inicial já que era necessário que a criação de um fluxo que inteligassem essas interfaces.

![Untitled (1)](https://github.com/Paulophpm/DataFlow_Pipeline/assets/53667656/bb773d3f-f8bb-4745-892f-95dd8f91b059)

