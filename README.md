# 📊 Modelo Dimensional – LOJA C&M Óptica

Este projeto apresenta um esquema estrela (Star Schema) para análise de vendas da loja C&M Óptica. O modelo foi desenvolvido com foco em Business Intelligence, permitindo consultas eficientes sobre produtos, clientes, vendedores e tempo.

---

## 🧱 Estrutura do Modelo

### 🧮 Tabela Fato: `Fato_Vendas`
Contém os dados transacionais das vendas realizadas.

- `ID_Venda`
- `ID_Produto`
- `ID_Cliente`
- `ID_Vendedor`
- `ID_Tempo`
- `Quantidade`
- `Valor_Unitario`
- `Valor_Total`
- `Desconto`
- `Forma_Pagamento`

### 📦 Dimensão Produto: `Dim_Produto`

- `ID_Produto`
- `Nome_Produto`
- `Categoria`
- `Armação`
- `Material`
- `Cor`
- `Tipo_Lente`
- `Preco_Unitario`

### 👤 Dimensão Cliente: `Dim_Cliente`

- `ID_Cliente`
- `Nome`
- `Sexo`
- `Idade`
- `Cidade`
- `Estado`
- `Segmento`

### 🧑‍💼 Dimensão Vendedor: `Dim_Vendedor`

- `ID_Vendedor`
- `Nome`
- `Cargo`
- `Departamento`
- `Data_Admissao`

### 📅 Dimensão Tempo: `Dim_Tempo`

- `ID_Tempo`
- `Data`
- `Dia`
- `Mes`
- `Ano`
- `Trimestre`
- `Dia_Semana`
- `Feriado`

---

# Onde Realisei a Criação da tabela

</div>
<img align="right" left="80" src="https://imgur.com/oVgAn2B.png" />

https://app.sqldbm.com/MySQL/DatabaseExplorer/p347736/



## 🛠 Scripts SQL

Os scripts de criação das tabelas estão disponíveis na pasta `sql_scripts/`. Eles incluem:

- Criação das tabelas fato e dimensões
- Definição de chaves primárias e estrangeiras
- Tipos de dados otimizados para análise

---

## 📈 Possibilidades de Análise

- Vendas por categoria de produto
- Desempenho de vendedores por período
- Perfil de clientes por região
- Comparativo de vendas entre meses e anos
- Impacto de promoções e descontos

---

## 🚀 Como Usar

1. Clone o repositório:
   ```bash
   git clone https://github.com/guilhermepereiradefreitas-hue/modelo-dimensao-optica.git
2. Importe os scripts SQL no seu banco de dados.
3. Conecte o modelo ao Power BI, Tableau ou outra ferramenta de BI.

---

## 📐 Explicação das Medidas DAX – LOJA C&M Óptica


</div>
<img align="right" left="80" src="https://imgur.com/iXCkvHS.png" />


1. Indica o Total de Faturamento da Óptica.

-`Total_Vendas = SUM(Fato_Vendas[Valor_Total])`

2.Soma a Quantidade de Produtos Vendidos, independente do valor.

-`Total_Quantidade = SUM(Fato_Vendas[Quantidade])`

3.Ticket médio por vendas. 

-`Valor_Medio_Venda = AVERAGE(Fato_Vendas[Valor_Total])`

4.Total e Descontos. 

-`Total_Desconto = SUM(Fato_Vendas[Desconto])`

5.Calcula o Valor medio de Descontos por Vendas.

-`Desconto_Medio = AVERAGE(Fato_Vendas[Desconto])`

6.Identifica a venda por categoria de Produto Que mais Gera receita.

-`Vendas_Por_Categoria = 
CALCULATE(
    SUM(Fato_Vendas[Valor_Total]),
    ALLEXCEPT(Dim_Produto, Dim_Produto[Categoria])
)`

7.Organiza Vendas por Vendedor de forma Individual.

-`Vendas_Por_Vendedor = 
CALCULATE(
    SUM(Fato_Vendas[Valor_Total]),
    ALLEXCEPT(Dim_Vendedor, Dim_Vendedor[Nome])
)`

8.Organiza as vendas por mês e ano.

-`Vendas_Mensais = 
CALCULATE(
    SUM(Fato_Vendas[Valor_Total]),
    ALLEXCEPT(Dim_Tempo, Dim_Tempo[Mes], Dim_Tempo[Ano])
)`

9.Mede o crescimento ou queda mês a mês.

`Crescimento_Mensal = 
VAR VendasAtual = SUM(Fato_Vendas[Valor_Total])
VAR VendasAnterior = 
    CALCULATE(
        SUM(Fato_Vendas[Valor_Total]),
        DATEADD(Dim_Tempo[Data], -1, MONTH)
    )
RETURN
    DIVIDE(VendasAtual - VendasAnterior, VendasAnterior)`


## 📌 Autor

Guilherme – Analista de Dados | Modelagem Dimensional | BI

---
