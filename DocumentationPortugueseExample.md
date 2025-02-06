# Documentação Técnica: Projeto de Controle de Gastos Pessoais

## 1. Introdução
Este documento descreve a estrutura e o funcionamento de uma planilha de controle de gastos pessoais desenvolvida em Excel. A planilha é composta por três abas principais: BD, Lançamentos e Controle de Gastos. Cada uma dessas abas tem uma função específica no gerenciamento de despesas e receitas pessoais.

## 2. Estrutura do Arquivo

### 2.1. Aba "BD"
A aba BD serve como uma base de dados que contém informações sobre as categorias de despesas e receitas, além de detalhes como classificação, tipo, mês, trimestre, semestre e tipo de pagamento.

![image](https://github.com/user-attachments/assets/2bd6dbc5-0a9f-4132-924b-be41df260b0d)

### 2.2. Aba "Lançamentos"
A aba Lançamentos é utilizada para registrar as transações financeiras. Cada transação é associada a uma conta da aba BD e contém informações como data, descrição, valor e tipo de pagamento.


Aqui está a transformação das informações em formato de tabela:

| **Campo**           | **Descrição**                                                            |
|---------------------|--------------------------------------------------------------------------|
| **Tipo de Pagamento**| Método de pagamento utilizado.                                           |
| **Dia**             | Dia da transação.                                                        |
| **Mês**             | Mês da transação.                                                        |
| **Ano**             | Ano da transação.                                                        |
| **Trimestre**       | Trimestre da transação.                                                  |
| **Semestre**        | Semestre da transação.                                                   |
| **Data**            | Data completa da transação.                                              |
| **Conta**           | Conta associada à transação (referência à aba BD).                       |
| **Descrição**       | Descrição detalhada da transação.                                         |
| **Classificação**   | Classificação da transação (referência à aba BD).                        |
| **Tipo**            | Tipo de transação (DESPESA ou RECEITA).                                  |
| **Valor**           | Valor da transação.                                                      |
| **Tipo de pagamento**| Método de pagamento utilizado.                                          |

Se precisar de mais algum ajuste ou adição, fique à vontade para pedir!

### 2.3. Aba "Controle de Gastos"
A aba Controle de Gastos consolida as informações das transações registradas na aba Lançamentos e apresenta um resumo mensal das despesas e receitas por categoria.

Aqui está o formato em tabela que você solicitou:

| **CATEGORIA**    | **CONTA**        | **JANEIRO** | **FEVEREIRO** | **MARÇO** | **ABRIL** | **MAIO** | **JUNHO** | **JULHO** | **AGOSTO** | **SETEMBRO** | **OUTUBRO** | **NOVEMBRO** | **DEZEMBRO** | **TOTAL** |
|------------------|------------------|-------------|---------------|-----------|-----------|----------|-----------|-----------|------------|--------------|-------------|--------------|--------------|-----------|
| Renda            | Conta 1          | X           | Y             | Z         | W         | X        | Y         | Z         | W          | X            | Y           | Z            | W            | TOTAL1    |
| Alimentação      | Conta 2          | X           | Y             | Z         | W         | X        | Y         | Z         | W          | X            | Y           | Z            | W            | TOTAL2    |
| Transporte       | Conta 3          | X           | Y             | Z         | W         | X        | Y         | Z         | W          | X            | Y           | Z            | W            | TOTAL3    |
| **TOTAL**        |                  | **X**       | **Y**         | **Z**     | **W**     | **X**    | **Y**     | **Z**     | **W**      | **X**        | **Y**       | **Z**        | **W**        | **TOTAL** |

Substitua os valores "X", "Y", "Z", "W" pelas transações reais para cada mês e categoria. Cada linha representa uma categoria de transação e a soma das transações ao longo do ano na coluna "TOTAL".


## 3. Funcionalidades e Fórmulas

### 3.1. Aba "BD"

TIPO DE PAGAMENTO: A coluna TIPO DE PAGAMENTO é preenchida manualmente ou através de referências a outras células.

### 3.2. Aba "Lançamentos"
Aqui está a tabela transformada, incluindo a coluna que descreve o cálculo realizado por cada fórmula:

Claro! Aqui está a tabela reformulada, com a descrição do cálculo incluída em uma linha abaixo de cada item:

| **Campo**         | **Fórmula**                                                                                   | 
|-------------------|-----------------------------------------------------------------------------------------------| 
| Tipo de Pagamento | =IF('BD '!K4=0,"",('BD '!K4))                                                                  | 
|                   | **Descrição:** Verifica se o valor na célula 'BD '!K4 é 0. Se for 0, deixa a célula em branco; caso contrário, preenche com o valor de 'BD '!K4. |
| Dia               | =IF(ISBLANK(H4),"",DAY(H4))                                                                   | 
|                   | **Descrição:** Verifica se a célula H4 está em branco. Se estiver, deixa em branco; se não, retorna o dia da data em H4.                    |
| Mês               | =IF(ISBLANK(H4),"",CHOOSE(MONTH(H4),"Janeiro","Fevereiro","Março","Abril","Maio","Junho","Julho","Agosto","Setembro","Outubro","Novembro","Dezembro")) | 
|                   | **Descrição:** Verifica se a célula H4 está em branco. Se não, retorna o nome do mês correspondente à data na célula H4.                     |
| Ano               | =IF(ISBLANK(H4),"",(YEAR(H4)))                                                                 | 
|                   | **Descrição:** Verifica se a célula H4 está em branco. Se não, retorna o ano da data presente em H4.                                          |
| Trimestre         | =IFERROR(VLOOKUP(C4,'BD '!$G:$H,2,0),"")                                                      | 
|                   | **Descrição:** Faz uma busca na coluna G da aba BD e retorna o valor correspondente na coluna H. Se houver erro, retorna em branco.           |
| Semestre          | =IFERROR(VLOOKUP(C4,'BD '!$G:$I,3,0),"")                                                      | 
|                   | **Descrição:** Realiza uma busca na coluna G da aba BD e retorna o valor correspondente na coluna I, indicando o semestre. Se houver erro, retorna em branco. |
| Classificação     | =IFERROR(VLOOKUP(I4,'BD '!$C:$D,2,0),"")                                                      | 
|                   | **Descrição:** Faz uma busca na coluna C da aba BD e retorna o valor correspondente na coluna D, indicando a classificação da transação. Se houver erro, retorna em branco. |
| Tipo              | =IFERROR(VLOOKUP(K4,'BD '!$D:$E,2,0),"")                                                      | 
|                   | **Descrição:** Realiza uma busca na coluna D da aba BD e retorna o valor correspondente na coluna E, indicando o tipo da transação. Se houver erro, retorna em branco. |

Agora, a descrição do cálculo está organizada em uma linha separada para cada item.
Essa tabela descreve claramente as fórmulas utilizadas para cada campo, juntamente com uma breve explicação de cada cálculo.

### 3.3. Aba "Controle de Gastos"

Aqui está a tabela conforme solicitado, incluindo a descrição do cálculo em uma linha abaixo de cada item:

| **Campo**         | **Fórmula**                                                                                   | 
|-------------------|-----------------------------------------------------------------------------------------------| 
| Soma dos Valores Mensais | =IF(SUMIFS(Lançamentos!$M:$M,Lançamentos!$I:$I,'Controle de gastos '!$C5,Lançamentos!$C:$C,'Controle de gastos '!D$4)=0,"",(SUMIFS(Lançamentos!$M:$M,Lançamentos!$I:$I,'Controle de gastos '!$C5,Lançamentos!$C:$C,'Controle de gastos '!D$4))) | 
|                   | **Descrição:** A fórmula usa `SUMIFS` para somar os valores da coluna M na aba "Lançamentos", com base nas condições das colunas I e C. Ela verifica se a soma é igual a zero e, caso seja, deixa em branco. Caso contrário, retorna o valor somado. |
| Total Anual       | =SUM(D5:O5)                                                                                 | 
|                   | **Descrição:** A fórmula soma os valores da linha de D5 a O5, calculando o total anual de cada conta, considerando as transações de janeiro a dezembro. |

Cada fórmula tem a descrição detalhada do cálculo que realiza, com a explicação dividida em uma linha abaixo de cada item.

## 4. Fluxo de Dados
Base de Dados (BD): A aba BD contém as informações básicas sobre as contas, classificações e tipos de transações.

Registro de Transações (Lançamentos): As transações são registradas na aba Lançamentos, onde cada transação é associada a uma conta da aba BD.

Consolidação (Controle de Gastos): A aba Controle de Gastos consolida as transações registradas na aba Lançamentos e apresenta um resumo mensal e anual das despesas e receitas.

## 5. Considerações Finais
Esta planilha foi projetada para facilitar o controle de gastos pessoais, permitindo que o usuário registre suas transações e visualize um resumo financeiro mensal e anual. As fórmulas e referências entre as abas garantem que os dados sejam consistentes e atualizados automaticamente conforme novas transações são registradas.

## 6. Melhorias Futuras
* Automatização de Categorias: Implementar uma lista suspensa para seleção de categorias e contas, reduzindo erros de digitação.

* Gráficos e Relatórios: Adicionar gráficos e relatórios para uma visualização mais clara das despesas e receitas.

* Integração com Bancos: Possibilidade de integração com extratos bancários para importação automática de transações.

## 7. Conclusão
A planilha de controle de gastos pessoais é uma ferramenta eficaz para o gerenciamento financeiro pessoal, oferecendo uma visão detalhada e organizada das despesas e receitas ao longo do tempo. Com a estrutura atual, o usuário pode facilmente registrar e monitorar suas finanças, tomando decisões mais informadas sobre seus gastos.

