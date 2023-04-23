## Fluxo Dados Utilizando Sharepoint e Power Data Flow

Criação de um fluxo automático de dados para ambiente corporativo.

### Objetivo:

Criação de um fluxo automatizado de dados que é atualizado de forma constante e manual por um funcionário, seja automatizado para que as equipes na ponta consigam visualizar as alterações realizadas dentro da plataforma corporativa.

### Problemas:

- Como automatizar um fluxo de dados de um arquivo excel que se encontra dentro de um ambiente nuvem corporativa;
- Como tornar o fluxo de dados mais leve para carregar os dados em menos tempo;
- Como restringir a visualização dos dados para que cada equipe visualize apenas os seus dados;
- 

### Ponto Inicial:

O arquivo inicial do projeto é uma planiha de excel (.xlsx) que está em um ambiente nuvem corporativo (Sharepoint), em que existe uma planilha para cada ano do negócio e cada planilha contém abas com os dados de cada mês do respectivo ano.

Para deixar os dados mais leve, foi criado uma nova planilha que realiza uma consulta a base origianal dos dados, utiliza para isso o Power Query presente no Excel con uma consulta frequente a cada 60 min. 

Com a consulta de dados pelo query, o arquivo fica estremamente mais leve, pois a nova planilha só conterá os valores do dataset original sem as formulas. Salvando o arquivo ainda dentro de uma nova pasta, porém dentro do abmiente nuvem corporativo.

![image](https://user-images.githubusercontent.com/53667656/233812878-f520cab4-b626-46cf-835a-ecf2fe7b85a0.png)

Print Query.

Os arquivos dos anos anteriores foi realizado uma quebra de vinculo, por isso so será atualizado os valores do respectivo ano.

### Power Service:

Dentro do ambiente do Power Service, 

Dentro do Power BI 

Print Query Online

print Data Flows
 

### Portal de Dados;

Implantação 
