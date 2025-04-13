# Log

## 📅 **03/04/2025**

### ✅ **Tarefas Realizadas**

- Importei os dados do arquivo "DatasetRH.csv"
	- Alterei  o nome da tabela de "DatasetRH" para "DadosRH"
	- Criei o [[Projetos/Power BI/RH/Dicionário de Dados]] do dataset
		- Alguns dados são necessários questionar o seu significado (`Indice_Envolvimento_Trabalho`, `Aval_Performance`, `Numero_Treinamentos_Ano_Anterior`)
			- Após algumas pesquisas a descrição desses atributos foi preenchida
	- Verifiquei se a coluna `Id_Funcionario` havia duplicatas (negativo)
	- Ao observar os dados não identifiquei nenhuma inconsistência. 

- Criei uma nova tabela chamada "Medidas" para armazenar as medidas que eu criar.

- Criei a medida "Total de Funcionários" abaixo para responder a primeira pergunta de negócio
  ```DAX
  Total de Funcionários = COUNTROWS(DadosRH)
	```
	- Criei um **Cartão** e atribui ao seu campo essa medida. O valor do **total de funcionários** é **1400**.

- Criei a medida "Tempo Médio de Experiência" abaixo para responde a segunda pergunta de negócio
  ```DAX
  Tempo Médio de Experiência = AVERAGE(DadosRH[Anos_Experiencia])
	```
	- Criei um **Cartão** e atribui ao seu campo essa medida. O **tempo médio de experiência dos funcionário** (em anos) é de **11,29 anos**.

- Criei um **Gráfico de Rosca** para apresentar o total e percentual de funcionários do gênero masculino e feminino.
	- **Valores:** Medida "Total de Funcionários"
	- **Legenda:** Atributo "Genero"

- Criei a medida "Média Salarial Mensal" abaixo para responder a primeira pergunta de negócio
  ```DAX
  Média Salarial Mensal = AVERAGE(DadosRH[Salario_Mensal])
	```
	- Criei um **Cartão** e atribui ao seu campo essa medida. A **média salarial mensal** dos funcionários é **6,93 mil**.

- Criei um **Gráfico de barras empilhadas** para apresentar o total de funcionários por função.
	- **Eixo Y:** Atributo "Funcao"
	- **Eixo X:** Medida "Total de Funcionários"

- Criei um **Gráfico de Pizza** para apresentar o percentual de funcionários disponíveis para fazer hora extra.
	- **Valores:** Medida "Total de Funcionários"
	- **Legenda:** Atributo "Disponivel_Hora_Extra"

- Criei um **Gráfico de colunas empilhadas** para apresentar o nível de envolvimento dos funcionários no trabalho.
	- **Eixo X:** Atributo "Indice_Envolvimento_Trabalho"
	- **Eixo Y:** Medida "Total de Funcionários"

- Criei a medida "Devem Receber Promoção" abaixo para responder a oitava pergunta de negócio
  ```DAX
  Devem Receber Promoção = CALCULATE(
  COUNT(DadosRH[Id_Funcionario]),
  DadosRH[Anos_Desde_Ultima_Promocao] >= 5)
	```

### 📊 **Próximos Passos**

- Modificar os valores/campos que forem necessários para tornar o dashboard mais compreensível.
- Ajustar o estilo dos dashboards. Posicionamento na tela. Cores.

---
## 📅 **08/04/2025**

### ✅ **Tarefas Realizadas**

- Organizando os visuais no dashboard e formatando a visualização.

- Substituí os valores "N" por "Não" e "S" por "Sim" na coluna "Disponivel_Hora_Extra".

- Alterei o tipo da coluna "Indice_Envolvimento_Trabalho" de **Número Inteiro** para **Texto**.
- Na coluna "Indice_Envolvimento_Trabalho", substituí os valores:
	- "1" por "Ruim"
	- "2" por "Baixo"
	- "3" por "Médio"
	- "4" por "Alto"

- Definição da paleta de cores dos gráficos
	- `#0056B2` → **Azul Royal**
	- `#66AFFF` → **Azul Céu Claro**
- Definição da cor da tela de fundo
	- `#EAEFF7` → **Azul Neblina**

Estilização final do dashboard

![image](https://github.com/user-attachments/assets/99724e7e-d8cd-4eac-b989-603b2343617b)

### 📊 **Próximos Passos**

- Documentação do dashboard

---
## 📅 **09/04/2025**

### ✅ **Tarefas Realizadas**

- Mudança de nomes de medidas:
  "Total de Funcionários" -> "Total Funcionários"
  "Tempo Médio de Experiência" -> "Experiência Média (Anos)"
  "Média Salarial Mensal" -> "Salário Médio"

- Remoção da medida "Devem Receber Promoção" e Coluna Condicional adicionada
	- A coluna condicional "StatusPromo" representa a condição de promoção do funcionário, ou seja, se a sua promoção deve ser considerada ou não. A condição para essa promoção é dita pela regra imposta na pergunta 8.

- Criação da medida "Total Funcionários Promover"
```DAX
Total Funcionários Promover = CALCULATE(
    [Total Funcionários],
    DadosRH[StatusPromo]="Considerar Promoção"
    )
```

- Criação da medida "Total Funcionários Não Promover"
```DAX
Total Funcionários Não Promover = CALCULATE(
    [Total Funcionários],
    DadosRH[StatusPromo]="Não Considerar Promoção"
    )
```

### 📊 **Próximos Passos**

- Ajustes nas colunas.
---
## 📅 **10/04/2025**

### ✅ **Tarefas Realizadas**

- Coluna "StatusPromo" adicionada ao [[Projetos/Power BI/RH/Dicionário de Dados]]

- Coluna "Chave" do dicionário de dados removida.
- Coluna "Tipo de Coluna" adicionada ao dicionário.

- A modificação feita anteriormente na coluna "Indice_Envolvimento_Trabalho" foi desfeita, tanto no tipo da coluna quanto nos valores.
- Para tornar a visualização do nível de envolvimento dos funcionários no trabalho, foi criado uma coluna condicional "Envolvimento_Trabalho" para tornar os valores mais compreensíveis:
	- "1" por "Ruim"
	- "2" por "Baixo"
	- "3" por "Médio"
	- "4" por "Alto"
- Com isso o campo no Eixo Y do gráfico de colunas de "Envolvimento dos Funcionários no Trabalho" foi alterado para a nova coluna condicional.
- Essa coluna foi adicionada no [[Projetos/Power BI/RH/Dicionário de Dados]].
- OBS: Essa mudança foi alterado pois aprendi que, da forma anterior, foi necessário mudar inteiramente a coluna "Indice_Envolvimento_Trabalho", partindo do seu tipo de dado, portanto, para evitar essa mudança mais drástica é recomendável criar uma coluna condicional. 

- Alterei a paleta de cores dos gráficos:
	- `#795366` → **Roxo Rosado**
	- `#9E90A6` → **Lilás Acinzentado**

- Ajustei a coluna "Disponivel_Hora_Extra" no dicionário de dados para o que foi modificado anteriormente.

### 📊 **Próximos Passos**

- Explorar os dados para encontrar possíveis informações para adicionar ao dashboard. (Uma possibilidade, porque não tem mais nada para colocar que esteja nas perguntas)
