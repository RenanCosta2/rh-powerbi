
# 📊 Projeto Power BI - RH

## 1. Informações Gerais do Projeto

**Nome do Projeto:** Análise de dados de RH
**Responsável:** Renan Costa  
**Data de Início:** 03/04/2025
**Data de Conclusão:** 10/04/2025
**Versão Atual:** 1.0  
**Setor/Departamento:** Recursos Humanos (RH)  

---

## 2. Requisitos do Projeto

- Obter o **total atual de funcionários** ativos na empresa.
- Calcular o **tempo médio de experiência** dos colaboradores, em anos.
- Identificar o **total e o percentual de funcionários por gênero** (masculino e feminino).
- Apresentar a **média salarial mensal** dos colaboradores.
- Exibir o **total de funcionários por função/cargo** na organização.
- Calcular o **percentual de funcionários disponíveis para hora extra**, com base em um campo específico.
- Classificar os colaboradores de acordo com o seu **nível de envolvimento no trabalho**, categorizando-os como Ruim, Baixo, Médio ou Alto.
- Determinar o **total e o percentual de funcionários elegíveis para promoção**, com base na regra de 5 anos ou mais desde a última promoção (mesmo que esse indicador não seja exibido no Dashboard, ele deve ser calculado).

---

## 3. Objetivo do Projeto

**Resumo:** O projeto desenvolvido no Power BI tem como objetivo oferecer uma visão estratégica do setor de Recursos Humanos da empresa, facilitando a análise e o acompanhamento de informações relevantes sobre os colaboradores. O Dashboard permite responder perguntas-chave de negócio, como o total de funcionários, tempo médio de experiência, distribuição por gênero e função, média salarial, disponibilidade para hora extra e níveis de envolvimento no trabalho.

---

## 4. Fontes de Dados

**Origem dos Dados:** Arquivo CSV.

- **Tabela Utilizada: DadosRH**

- **Campos Considerados:**  
  - _Anos_Desde_Ultima_Promocao_
  - _Anos_Experiencia_
  - _Disponivel_Hora_Extra_
  - _Envolvimento_Trabalho_
  - _Funcao_
  - _Genero_
  - _Idade_
  - _Salario_Mensal_

### Dicionário de Dados

| Nome do Campo                          | Tipo de Dado | Descrição                                                                                 | Tipo de Coluna | Exemplo                  | Valores Possíveis                                         |
|---------------------------------------|--------------|-------------------------------------------------------------------------------------------|----------------|---------------------------|-----------------------------------------------------------|
| `Id_Funcionario`                      | Inteiro      | Identificador único do funcionário                                                        | Original       | `10234`                   | `-`                                                       |
| `Idade`                               | Inteiro      | Idade do funcionário                                                                      | Original       | `24`                      | `-`                                                       |
| `Genero`                              | Texto        | Gênero do funcionário                                                                     | Original       | `Masculino`               | `Masculino`, `Feminino`                                  |
| `Estado Civil`                        | Texto        | Estado civil do funcionário                                                               | Original       | `Solteiro`                | `Solteiro`, `Casado`, `Divorciado`                       |
| `Departamento`                        | Texto        | Departamento do funcionário                                                               | Original       | `Data Science`            | `-`                                                       |
| `Funcao`                              | Texto        | Função/Cargo do funcionário                                                               | Original       | `Analista de Dados`       | `-`                                                       |
| `Viagem`                              | Texto        | Frequência em que o funcionário viaja                                                     | Original       | `Apenas Local`            | `Apenas Local`, `Viaja Frequentemente`, `Viaja Raramente`|
| `Valor Diaria`                        | Inteiro      | Valor da diária do funcionário                                                            | Original       | `600`                     | `-`                                                       |
| `Indice_Envolvimento_Trabalho`        | Inteiro      | Indica o nível de envolvimento do funcionário no trabalho                                 | Original       | `3`                       | `1`, `2`, `3`, `4`                                        |
| `Envolvimento_Trabalho`               | Texto        | Indica o nível de envolvimento do funcionário no trabalho                                 | Condicional    | `Baixo`                   | `Ruim`, `Baixo`, `Médio`, `Alto`                         |
| `Nivel_Satisfacao_Trabalho`           | Inteiro      | Valor que indica o nível de satisfação do funcionário com o trabalho                      | Original       | `1`                       | `1`, `2`, `3`, `4`                                        |
| `Salario_Mensal`                      | Inteiro      | Salário Mensal do funcionário                                                             | Original       | `15000`                   | `-`                                                       |
| `Numero_Empresas_Anteriores`          | Inteiro      | Quantidade de empresas que o funcionário já trabalhou                                     | Original       | `8`                       | `-`                                                       |
| `Disponivel_Hora_Extra`               | Texto        | Indica se o funcionário está disponível para hora extra                                   | Original       | `Sim`                     | `Sim`, `Não`                                              |
| `Percentual_Ultimo_Aumento_Salario`   | Inteiro      | Percentual do último aumento de salário do funcionário                                    | Original       | `15`                      | `-`                                                       |
| `Aval_Performance`                    | Inteiro      | Avaliação de performance do funcionário                                                   | Original       | `3`                       | `-`                                                       |
| `Anos_Experiencia`                    | Inteiro      | Indica quantos anos de experiência o funcionário tem                                      | Original       | `10`                      | `-`                                                       |
| `Numero_Treinamentos_Ano_Anterior`    | Inteiro      | Quantidade de treinamentos que o funcionário participou no ano anterior                   | Original       | `3`                       | `-`                                                       |
| `Anos_na_Empresa`                     | Inteiro      | Quantos anos o funcionário está na empresa                                                | Original       | `5`                       | `-`                                                       |
| `Anos_Funcao_Atual`                   | Inteiro      | Quantos anos o funcionário está atuando na sua função atual                               | Original       | `6`                       | `-`                                                       |
| `Anos_Desde_Ultima_Promocao`          | Inteiro      | Quantos anos desde a última promoção do funcionário                                       | Original       | `0`                       | `-`                                                       |
| `Anos_com_Gerente_Atual`              | Inteiro      | Quantos anos o funcionário está sendo gerenciado pelo gerente atual                      | Original       | `8`                       | `-`                                                       |
| `StatusPromo`                         | Texto        | Indica se o funcionário deve ser considerado para promoção com base em critérios específicos (5 anos ou mais desde a última promoção) | Condicional    | `Não Considerar Promoção` | `Considerar Promoção`, `Não Considerar Promoção`         |



---

## 5. Tratamento de Dados

**Transformações Realizadas no Power Query:**  
- **Alteração de Valores dos Dados**: Os valores da coluna **Disponivel_Hora_Extra** foram ajustados. O **N** foi substituído por **Não** e o **S** foi substituído por **Sim**.

---

## 6. Validação e Verificação dos Dados

**Métodos de Validação:** Verificação Manual.  
**Erros Encontrados e Correções:** Nenhum erro encontrado.

---

## 7. Modelagem de Dados

**Relacionamentos Criados:** Tabela única.

---

## 8. Funções DAX Utilizadas

### Medidas Criadas (DAX):
- **Experiência Média (Anos):**
  ``` DAX
  AVERAGE(DadosRH[Anos_Experiencia])
  ```
- **Salário Médio:** 
  ``` DAX
  AVERAGE(DadosRH[Salario_Mensal])
  ```  
- **Total Funcionários:**  
  ``` DAX
  COUNTROWS(DadosRH)
  ```  
- **Total Funcionários Não Promover:**
  ``` DAX
  CALCULATE(
    [Total Funcionários], 
    DadosRH[StatusPromo]="Não Considerar Promoção"
    )
  ```  
- **Total Funcionários Promover:**
  ``` DAX
  CALCULATE(
    [Total Funcionários], 
    DadosRH[StatusPromo]="Considerar Promoção"
    )
  ```
  
---

## 9. Dashboards e Relatórios

![image](https://github.com/user-attachments/assets/99724e7e-d8cd-4eac-b989-603b2343617b)

### Visão Geral
- **Total de Funcionários:** 1400 colaboradores.
- **Experiência Média:** 11,29 anos, o que indica uma equipe bastante experiente.
- **Salário Médio:** R$ 6.927,51 – um valor razoável para áreas técnicas, principalmente em dados e IA.

### Distribuição por Função
- A função **Cientista de Dados** domina com **638 funcionários (≈46%)**.
- Em seguida, **Analista de Dados** com 246.
- **Engenheiro de IA, Arquiteto de Dados e Engenheiro de Dados** aparecem com proporções menores.
- **Engenheiro Analítico** tem a menor representatividade com 76.

### Distribuição por Gênero
- **Masculino:** 838 (59,86%)
- **Feminino:** 562 (40,14%)

### Envolvimento dos Funcionários
- **Médio:** 826 (≈59%)
- **Baixo:** 356 (≈25%)
- **Alto:** 139 (≈10%)
- **Ruim:** 79 (≈6%)

### Disponibilidade para Hora Extra
- **Disponíveis:** 398 (28,43%)
- **Não Disponíveis:** 1002 (71,57%)

---

## 10. Acesso e Compartilhamento

**Modo de Compartilhamento:** Publicado no Power BI Service  
[🔗 Acessar Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNzE1NTIyMzUtZDQ1OS00MzE4LTk0NTItZjhmNjJkMzlhNWQzIiwidCI6ImJhZTkwYjYxLTg4OTItNDQyMC1hMTEyLTE0NTQ4MzBkYmJiOSJ9)

---

## 11. Considerações Finais

- Há informações no banco de dados que não foram analisadas, são possíveis melhorias que podem ser adicionadas ao dashboard.
- A forma que os visuais estão dispostos no dashboard pode ser melhorada.

## 12. Anexo: LOG de Desenvolvimento

Para acompanhar todo o histórico de desenvolvimento, ajustes e decisões tomadas ao longo do projeto, acesse o LOG de Desenvolvimento disponível no link abaixo:
[🔗 Acessar LOG de Desenvolvimento](./log-desenvolvimento.md)

Última Atualização: 10/04/2025

Autor: Renan Costa
