# **Análise Exploratória de Dados do Covid-19 - MySQL**

 Projeto de análise de dados utilizando o SGBD **MySQL** para analisar dados reais sobre a pandemia do Covid-19, através de análise de estatísticas, agregações, relacionamentos e análise de dados ao longo do tempo.
 Os dados utilizados neste projeto estão disponíveis publicamente neste [link](https://ourworldindata.org/covid-deaths).

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

## **Criando o Schema dbcovid:**

![schema](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/01%20-%20Criando%20o%20Schema%20dbcovid.png?raw=true)

---

### **Criando a Tabela 1 (covid_mortes):**

![tabela1](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/02%20-%20Criando%20a%20tabela%20covid_mortes.png?raw=true)

---

### **Criando a Tabela 2 (covid_vacinacao):**

![tabela2](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/03%20-%20Criando%20a%20tabela%20covid_vacina%C3%A7%C3%A3o.png?raw=true)

**Obs:**
-  Os dados das tabelas foram carregados via linha de comando através do cmd, pois como é uma grande quantidade de dados, o processo de carregamento via linha de comando é bem mais rápido;
-  Todas as colunas das 2 tabelas foram criadas com o tipo **"text"** em um primeiro momento para evitar erros ao carregar os dados, e serão modificados de acordo com a nessecidade,  convertendo o tipo cada coluna (int, bigint, double, varchar(25), etc) no decorrer do projeto, a medida que for necessário para realizar alguma operação matemática.

---

#  3\. **Explorando os dados**

### **Visualizando os dados da tabela covid_mortes:**

![covid_mortes](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/04%20-%20Visualizando%20os%20dados%20covid_mortes.png?raw=true)

---

### **Visualizando os dados da tabela covid_vacinacao:**

![covid_vacinacao](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/05%20-%20Visualizando%20os%20dados%20covid_vacina%C3%A7%C3%A3o.png?raw=true)

**Obs:**
-  Algumas colunas de ambas as tabelas estão em branco pois no início da pandemia ainda não existiam registros, ou os dados não timham sido publicados na data em questão.

  ---

### **Convertendo as colunas de data para o tipo "date" com o comando str_to_date():**

 Através de uma instrução DML (Data Manipulation Linguage) as colunas do tipo "date" serão convertidas do formato "text" para o formato de data. O comando str_to_date converte a coluna para  formato de data, retornando a data no formato estipulado dentro dos parenteses, a documentação de referencia pode ser acessada clicando neste [link](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html).

 **Obs:**
-  Por não possuir nenhum tipo de filtro, todas as linhas da coluna são modificadas após o uso dessa instrução DML, por isso, em alguns SGBD's, as clausulas UPDATE e DELETE sem filtro são bloqueadas por padrão, pois a cláusula pode modificar completamente os dados, recuperando somente via Backup, ou tentando uma nova conversão para o estado anterior da coluna, por esse motivo será preciso desbloquear o SAFE UPDATE, utilizando um comando do próprio MySQL, e logo após a conversão da coluna, voltamos o SAFE UPDATE ao seu padrão original através do mesmo comando.

 Comando para desbloquear o SAFE UPDATE:
- SET SQL_SAFE_UPDATES = 0;

Comando para bloquear novamente o SAFE UPDATE:
- SET SQL_SAFE_UPDATES = 1;

![str_to_date](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/06%20-%20Convertendo%20as%20colunas%20de%20data%20-%20str%20para%20date.png?raw=true)

---

### **Selecionando as colunas mais relevantes da tabela covid_mortes para a análise:**

![colunas_relevantes](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/07%20-%20Selecionando%20colunas%20relevantes%20para%20a%20an%C3%A1lise%20dos%20dados.png?raw=true)

---

### **Análise Univariada:**

 Uma análise univariada examina e analisa uma única variável em um conjunto de dados, geralmente, essa análise é realizada para entender a distribuição, as estatísticas descritivas e as tendências dessa variável específica. Algumas das principais operações que podem ser realizadas para realizar uma análise univariada no MySQL São: 
- Contagem de registros: COUNT();
- Estatísticas descritivas: AVG(), MEDIAN(), STDDEV(), MIN() e MAX();
- Análise de tendências: YEAR(), MONTH(), DAY().

Na query abaixo calculei a média de mortos de cada país utilizando a função **AVG** na coluna **total_deaths**, e agrupando os dados pela coluna **location**, retornando assim a média de mortos de cada país. Depois fiz o mesmo processo na coluna **new_cases** para retornar a média dos novos casos de cada país. A função **ROUND()** arredonda um valor numérico para um número específico de casas decimais, nesse caso foram arredondados para duas casas.

![análise_univariada](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/08%20-%20Fazendo%20uma%20anal%C3%ADse%20univariada.png?raw=true)

---

### **Análise Multivariada:**

 Uma Análise multivariada examina e analisa a relação entre duas ou mais variáveis em um conjunto de dados. Diferentemente da análise univariada, que foca em uma única variável, a análise multivariada permite explorar as interações, associações e correlações entre múltiplas variáveis. Existem várias técnicas e operações disponíveis para realizar análises multivariadas. Algumas das principais são: 
- Matriz de correlação;
- Análise de regressão;
- Análise de clusterização;
- Análise de componentes principais (PCA);
- Análise de associação.

Na query abaixo fiz uma divisão direta entre as colunas **total_deaths** e **total_cases**, multiplicando o resultado por 100 para achar o percentual de mortes em relação ao total de casos, e filtrando somente os dados do Brasil com a cláusula WHERE, e ordenando o resultado pelas colunas **location** e **date**.

![análise_multivariada](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/09%20-%20Fazendo%20uma%20anal%C3%ADse%20multivariada.png?raw=true)

---

### **Proporção média entre o total de casos e a população de cada localidade:**

Na query abaixo calculei a média do total de casos dividido pela população, e multipliquei o resultado por 100 para encontrar a proporção média entre o total de casos e a população, agrupando pela localidade, encontrando o percentual médio de de casos de cada país.

![proporção_média](https://github.com/jaquessonoliveira/MySQL-Projeto-analise-covid/blob/main/Arquivos/10%20-%20Propor%C3%A7%C3%A3o%20m%C3%A9dia%20entre%20o%20total%20de%20casos%20e%20a%20popula%C3%A7%C3%A3o.png?raw=true)

---
