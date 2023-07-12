# **Análise Exploratória de Dados do Covid-19 - MySQL**

> Projeto de análise de dados utilizando o SGBD **MySQL** para analisar dados reais sobre a pandemia do Covid-19, através de análise de estatísticas, agregações, relacionamentos e análise de dados ao longo do tempo.
> Os dados utilizados neste projeto estão disponíveis publicamente neste [link](https://ourworldindata.org/covid-deaths)

---

# **Tópicos**

<ol type="1">
  <li>Dados;</li>
  <li>Criando o Schema e as tabelas no MySQL;</li>
  <li>Explorando os dados;</li>
  <li>...;</li>
  <li>....</li>
</ol>

---

#  1\. **Dados**

Os dados representam informações de mortes e vacinação global durante a pandemia do Covid-19, entre 01/01/2020 e 29/06/2021, e estão divididos em 2 arquivos no formato csv: covid_mortes e covid_vacinacao.

---

#  2\. **Criando o Schema e as tabelas no MySQL**

Schema dbcovid:

![schema](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/01%20-%20Criando%20o%20Schema%20dbcovid.png?raw=true)

Tabela 1 (covid_mortes):

![tabela1](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/02%20-%20Criando%20a%20tabela%20covid_mortes.png?raw=true)

Tabela 2 (covid_vacinacao):

![tabela2](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/03%20-%20Criando%20a%20tabela%20covid_vacina%C3%A7%C3%A3o.png?raw=true)

**Obs:**
-  Os dados das tabelas foram carregados via linha de comando através do cmd, pois como é uma grande quantidade de dados, o processo de carregamento é bem mais rápido;
-  Todas as colunas das 2 tabelas foram criadas com o tipo **"text"** em um primeiro momento para evitar erros ao carregar os dados, e serão modificados de acordo com a nessecidade,  convertendo o tipo cada coluna (int, bigint, double, varchar(25), etc) no decorrer do projeto, a medida que for necessário para realizar alguma operação matemática.

---

#  3\. **Explorando os dados**

**Visualizando os dados da tabela covid_mortes:

![covid_mortes](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/04%20-%20Visualizando%20os%20dados%20covid_mortes.png?raw=true)

**Visualizando os dados da tabela covid_vacinacao:

![covid_vacinacao](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/05%20-%20Visualizando%20os%20dados%20covid_vacina%C3%A7%C3%A3o.png?raw=true)

**Obs:**
-  Algumas colunas de ambas as tabelas estão em branco pois no início da pandemia ainda não existiam registros, ou os dados não timham sido publicados na data em questão.

