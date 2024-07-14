# Projeto de Análise de Cancelamento de Cartão de Crédito

## Descrição

Este projeto foi desenvolvido como parte de um desafio da plataforma [Hashtag Treinamentos](https://www.hashtagtreinamentos.com/projetos-iniciantes-python). O objetivo principal era analisar o comportamento dos clientes de uma empresa de cartão de crédito e identificar possíveis razões para o cancelamento de seus cartões, visando elaborar estratégias de retenção.

## Objetivo

- **Analisar o comportamento dos clientes**: Compreender os padrões e tendências nos dados de clientes que cancelaram seus cartões.
- **Identificar razões para o cancelamento**: Investigar fatores que podem estar contribuindo para a decisão dos clientes de cancelar seus cartões.
- **Propor estratégias de retenção**: Sugerir ações que a empresa pode adotar para melhorar a retenção de clientes.

## Metodologia

1. **Coleta de Dados**: Utilização de uma base de dados fornecida pela empresa de cartão de crédito, que contém informações detalhadas sobre os clientes e suas interações com a empresa.
2. **Tratamento de Dados**:
    - Identificação de valores ausentes: Durante o tratamento da base, identifiquei que uma linha da coluna "Idade" estava vazia.
    - Remoção de linhas com valores ausentes: Foi recomendada a remoção da linha com o valor ausente, uma vez que seria apenas uma informação faltante.
    ```python
    tabela = tabela.dropna()
    display(tabela.info())
    display(tabela.describe().round(1))
    ```

3. **Análise Exploratória de Dados (EDA)**:
    - Avaliação da divisão entre clientes e cancelados: Para entender a proporção de cancelamentos, utilizei o método `value_counts()` para comparar o número de clientes e cancelados.
    ```python
    qtde_categoria = tabela["Categoria"].value_counts()
    display(qtde_categoria)
    qtde_categoria_perc = tabela["Categoria"].value_counts(normalize=True)
    display(qtde_categoria_perc)
    ```

    - Resultados:
    ```plaintext
    Cliente      8499
    Cancelado    1627
    Name: Categoria, dtype: int64

    Cliente      0.839325
    Cancelado    0.160675
    Name: Categoria, dtype: float64
    ```
    Apenas 16% da base eram cancelados, enquanto 84% eram clientes ativos.

4. **Visualização de Dados**:
    - Utilização da biblioteca Plotly para criar gráficos comparativos e analisar a relação entre os clientes que optaram por cancelar.
    ```python
    import plotly.express as px

    for coluna in tabela:
        grafico = px.histogram(tabela, x=coluna, color="Categoria")
        grafico.show()
    ```

## Resultados da Análise

1. **Clientes com menos produtos contratados tendem a cancelar mais**:
    - Estratégia: Ofertar mais produtos para aumentar o interesse no cartão.
2. **Clientes que utilizam menos o cartão durante 12 meses têm a maior chance de cancelamento**:
    - Estratégia: Incentivar o uso do cartão com promoções e benefícios.
3. **Clientes que entram em contato com o banco mais de 2 vezes têm a maior chance de cancelamento**:
    - Estratégia: Realizar uma análise qualitativa das solicitações dos clientes para melhorar a qualidade do atendimento.

## Conclusão

Através deste projeto, foi possível identificar diversas razões que levam ao cancelamento dos cartões de crédito e propor ações para a retenção de clientes. As análises realizadas podem ser utilizadas pela empresa para melhorar suas estratégias de retenção e reduzir o churn de clientes.

## Ferramentas Utilizadas

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Plotly
