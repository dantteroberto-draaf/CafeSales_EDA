# CafeSales Analysis: From Dirty Data to Insights
## 📌 Sobre o projeto
Este projeto consiste em uma Análise Exploratória de Dados(EDA) completa sobre transações de uma cafeteria fictícia. O foco principal não foi apenas gerar visualizações, mas sim **simular um cenário real de Engenharia de Dados**, onde o dataset original continha diversos erros de integridade, valores ausentes e inconsistências que precisaram ser tratados com regras de negócio lógicas antes da análise.

## 🎯 Objetivos do Negócio
O objetivo é responder perguntas estratégicas para o funcionamento da cafeteria e suas tendências:
* **Faturamento:** Qual a relação entre o ticket médio e o método de pagamento?
* **Logística:** Há um padrão de consumo (loja vs. takeaway) que impacte o estoque?
* **Produto:** Quais itens têm maior saída e qual a elasticidade de preço observada?

## 🛠️ O Desafio dos Dados - Data Cleaning Strategy
O Dataset original(dirty_cafe_sales.csv) apresentava cerca de 10.000 linhas com diversos problemas de qualidade: tipagem incorreta; strings 'ERROR', 'UNKNOWN e valores nulos.

Estratégia de tratamento adotada: ao invés de simplesmente descartar linhas problemáticas e acabar perdendo uma signifcativa parcela dos dados, adotei uma abordagem que utiliza a lógica para tornar o Dataset o mais consistente possível, com o mínimo de valores
'UNKNOWN' ou nulos. Para isso, foram seguidos os seguintes passos:
1. **Correção de tipagem:** As colunas numéricas foram convertidas para o tipo correto e os valores inconsistentes('UNKNOWN' e 'ERROR') foram transformados em NaN;

2. **Engenharia reversa de preços:** Mapeamento dos preços unitários baseados nos preços já conhecidos de cada item. Por exemplo: todo Cookie custa 1.0
   
3. **Reconstrução matemática das colunas:** Utilização da relação Total = Quantidade * Preço para preencher valores ausentes.

4. **Tratamento de Categorias:** Itens com ambiguidade de preço (Ex: itens de $3.00 que poderiam ser Bolo ou Suco) foram tratados conservadoramente como "Unknown" para não enviesar a análise de produtos. No caso dos produtos que antes eram desconhecidos, mas tinham um preço único(Ex: Unknown que custa 1.0 = Cookie), estes tiveram seus nomes devidamente corrigidos para melhor cobertura dos dados para os insights

## 📂 Estrutura do Repositório
```bash
├── data
│   ├── raw                 # Dataset original (dirty_cafe_sales.csv)
│   └── processed           # Dataset limpo após o pipeline (clean_cafe_sales.csv)
│
├── notebooks
│   ├── base_cafe_EDA.ipynb   # Limpeza, tratamento de NaNs e conversão de tipos
│   └── EDA_analysis.ipynb    # Análise exploratória e geração de insights
│
├── README.md               # Documentação do projeto
└── requirements.txt        # Bibliotecas necessárias
```
## 📊 Principais Insights e Conclusões
### 🍪☕ Combos
<img width="1002" height="595" alt="image" src="https://github.com/user-attachments/assets/9ece2fc0-9136-4c89-b9bd-554ecf31cf6d" />
Oportunidade de Negócio: Identificamos que Café e Cookie são majoritariamente consumidos para viagem (Takeaway), enquanto Salada e Suco são consumidos na loja.

* Ação Recomendada: Criar o "Combo Express" (Café + Cookie) para clientes apressados e o "Combo Almoço" (Salada + Suco) para aumentar o ticket médio de quem fica na loja.

### 💲 Pagamento
<img width="836" height="543" alt="image" src="https://github.com/user-attachments/assets/cb943481-d96d-4190-9f29-734a0be28402" />

Comportamento de Pagamento: Não houve correlação entre o valor da compra e o método de pagamento.

* Conclusão: Campanhas de incentivo para uso de cartão ou dinheiro não teriam impacto significativo no ticket médio.

## 💻 Como executar o projeto
1. Clone o repositório
```bash
git clone https://github.com/dantteroberto-draaf/CafeSales_EDA.git
```
2. Instale as dependências
```bash
pip install -r requirements.txt
```
3. Execute o jupyter notebook na pasta 'notebooks'

## 📬 Contato
Dantte Roberto - www.linkedin.com/in/dantte-roberto

