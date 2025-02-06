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

2.3. Aba "Controle de Gastos"
A aba Controle de Gastos consolida as informações das transações registradas na aba Lançamentos e apresenta um resumo mensal das despesas e receitas por categoria.

Colunas:

CATEGORIA: Categoria da transação (ex: Renda, Alimentação, Transporte, etc.).

CONTA: Conta associada à transação.

JANEIRO a DEZEMBRO: Colunas que representam os meses do ano, onde são somados os valores das transações correspondentes a cada mês.

TOTAL: Soma total das transações ao longo do ano para cada conta.

3. Funcionalidades e Fórmulas
3.1. Aba "BD"
TIPO DE PAGAMENTO: A coluna TIPO DE PAGAMENTO é preenchida manualmente ou através de referências a outras células.

3.2. Aba "Lançamentos"
Tipo de Pagamento: A fórmula =IF('BD '!K4=0,"",('BD '!K4)) é utilizada para preencher o tipo de pagamento com base na aba BD.

Dia, Mês, Ano, Trimestre, Semestre: As fórmulas =IF(ISBLANK(H4),"",DAY(H4)), =IF(ISBLANK(H4),"",CHOOSE(MONTH(H4),"Janeiro","Fevereiro","Março","Abril","Maio","Junho","Julho","Agosto","Setembro","Outubro","Novembro","Dezembro")), =IF(ISBLANK(H4),"",(YEAR(H4))), =IFERROR(VLOOKUP(C4,'BD '!$G:$H,2,0),""), e =IFERROR(VLOOKUP(C4,'BD '!$G:$I,3,0),"") são utilizadas para extrair o dia, mês, ano, trimestre e semestre da data da transação.

Classificação e Tipo: As fórmulas =IFERROR(VLOOKUP(I4,'BD '!$C:$D,2,0),"") e =IFERROR(VLOOKUP(K4,'BD '!$D:$E,2,0),"") são utilizadas para preencher a classificação e o tipo da transação com base na aba BD.

3.3. Aba "Controle de Gastos"
Soma dos Valores Mensais: A fórmula =IF(SUMIFS(Lançamentos!$M:$M,Lançamentos!$I:$I,'Controle de gastos '!$C5,Lançamentos!$C:$C,'Controle de gastos '!D$4)=0,"",(SUMIFS(Lançamentos!$M:$M,Lançamentos!$I:$I,'Controle de gastos '!$C5,Lançamentos!$C:$C,'Controle de gastos '!D$4))) é utilizada para somar os valores das transações correspondentes a cada mês e conta.

Total Anual: A fórmula =SUM(D5:O5) é utilizada para calcular o total anual de cada conta.

4. Fluxo de Dados
Base de Dados (BD): A aba BD contém as informações básicas sobre as contas, classificações e tipos de transações.

Registro de Transações (Lançamentos): As transações são registradas na aba Lançamentos, onde cada transação é associada a uma conta da aba BD.

Consolidação (Controle de Gastos): A aba Controle de Gastos consolida as transações registradas na aba Lançamentos e apresenta um resumo mensal e anual das despesas e receitas.

5. Considerações Finais
Esta planilha foi projetada para facilitar o controle de gastos pessoais, permitindo que o usuário registre suas transações e visualize um resumo financeiro mensal e anual. As fórmulas e referências entre as abas garantem que os dados sejam consistentes e atualizados automaticamente conforme novas transações são registradas.

6. Melhorias Futuras
Automatização de Categorias: Implementar uma lista suspensa para seleção de categorias e contas, reduzindo erros de digitação.

Gráficos e Relatórios: Adicionar gráficos e relatórios para uma visualização mais clara das despesas e receitas.

Integração com Bancos: Possibilidade de integração com extratos bancários para importação automática de transações.

7. Conclusão
A planilha de controle de gastos pessoais é uma ferramenta eficaz para o gerenciamento financeiro pessoal, oferecendo uma visão detalhada e organizada das despesas e receitas ao longo do tempo. Com a estrutura atual, o usuário pode facilmente registrar e monitorar suas finanças, tomando decisões mais informadas sobre seus gastos.

