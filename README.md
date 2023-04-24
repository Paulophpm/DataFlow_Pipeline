## Fluxo de Dados Automatizado Utilizando Sharepoint e Power Data Flow 

Criação de um fluxo automático de dados para um ambiente nuvem corporativo.

### Objetivo:

Criação de um fluxo automatizado de dados em nuvem que é atualizado várias vezes ao dia, sendo a fonte de dados um arquivo que tem entradas manuais imputadas por um funcionário. Sendo possível que as equipes na ponta, consiga visualizar as alterações realizadas pelo dashboard através de uma plataforma corporativa.

### Problemas:

- Como atualizar de forma contínua ou intervalada, dados de um arquivo excel que é atualizado de forma manual ?;
- Como criar um fluxo de dados automatizado com arquivos base do Sharepoint ?;
- Como tornar o fluxo de dados mais leve para carregar os dados em menos tempo ?;
- Como restringir a visualização dos dados para que cada equipe visualize apenas os seus dados ?;

## 1.0 Ponto Inicial:

O arquivo inicial do projeto é uma planilha de excel (Controle_23.xlsx) que está em um ambiente de nuvem corporativa (Sharepoint), sendo essa planilha composta por abas que trazem o resultado de cada mês do referido negócio. 

A planilha é composta por inúmeras formulas que calculam diversas medidas necessárias para que as equipes na ponta consigam realizar de forma mais eficiente o andamento das suas metas.

Para deixar os dados mais leve, foi criado uma nova planilha (Base de  Dados.xlsx) que realiza uma consulta na base Controle_23.xlsx a cada 60 min. Utiliza para isso a consulta da lista do Sharepoint presente no Power Query dentro do Excel.*

* Para isso é necessário ter login e senha com autorização para acesso a referida pasta.

### 1.1 Conexão com a Base de Dados:

O início do processo começar em conectar novo arquivo da base de dados. Com o link da página inicial do Sharepoint é possível encontrar a pasta da qual se encontra o arquivo e assim conseguir conectar a fonte de dados.

Obs: Para conseguir acessar a pasta irá ser solicitado algum tipo de verificação como a conta corporativa, ou algum login e senha para conseguir acesso.

![Untitled](https://user-images.githubusercontent.com/53667656/234136717-ff5fecf2-29fe-4273-ac0b-56012e69e57a.png)

Com a consulta de dados pelo query, o arquivo fica extremamente mais leve, pois a nova planilha Base de Dados.xlsx só conterá apenas os valores do dataset original sem as formulas, além disso também é possível tratar de forma prévia os dados para que sejam carregados de forma mais rápida ao banco de dados que vai ser criado.

Porém ainda é necessário fazer com que essa consulta seja atualizada de forma constante, para isso dentro da consulta gerado, na parte de propriedades é possível configurar a atualização periódica através de um período determinado de tempo. E que mesmo assim essa consulta seja atualizada em segundo plano.

![Untitled (1)](https://user-images.githubusercontent.com/53667656/234136806-443c5b2d-911b-45a7-9b4c-3d7e57198fcc.png)


Obs: O Único impedimento é que a atualização entre as duas base só acontece se o arquivo a ser consultado (Controle_23.xlsx) estiver fechado, por isso o usuário terá que abrir para realizar as entradas ,e após imputa-las fechar o arquivo. 

Além disso, foi realizado o processo nas bases dos anos anteriores, com isso temos um arquivo que também contém dados histórico de uma mesma área de negócio, porém o vínculo foi quebrado, já que não há modificações dos anos anteriores.

A nova base de dados foi salva dentro ainda do mesmo ambiente nuvem.

![image (1)](https://user-images.githubusercontent.com/53667656/234136871-a7b29052-47b8-4346-8d3c-c842b4991fb7.png)


