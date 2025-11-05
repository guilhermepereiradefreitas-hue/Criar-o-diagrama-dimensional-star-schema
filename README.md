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

##📌 Autor
Guilherme – Analista de Dados | Modelagem Dimensional | BI

