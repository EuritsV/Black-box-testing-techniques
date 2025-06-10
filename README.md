# 🧪 Mini Treino: Técnicas de Teste Caixa Preta

Este mini treino foi criado con intuito de compreender e aplicar quatro técnicas essenciais de design de testes **caixa preta**:

- Equivalence Partitioning (Particionamento por Equivalência)
- Boundary Value Analysis (Análise de Valores Limite)
- Decision Table (Tabela de Decisão)
- State Transition (Transição de Estado)

---

## 🎯 Objectivo

- Entender o que é cada técnica
- Saber quando e por que utilizá-las
- Aplicar na prática em sistemas reais
- Estruturar casos de teste eficazes

---

## 📚 Conteúdo do Treino

### 1. Equivalence Partitioning (Particionamento por Equivalência)
- **Definição**: Técnica que divide os dados de entrada em grupos (partições) onde se espera que todos os valores tenham o mesmo comportamento.
- **Importância**: Reduz a quantidade de testes mantendo boa cobertura.
- **Aplicação prática**: Validação de campo “quantidade de itens no carrinho” com faixas distintas.
- [Ver detalhes](#equivalence-partitioning.md)

### 2. Boundary Value Analysis (Análise de Valores Limite)
- **Definição**: Técnica que testa os valores nas fronteiras das entradas válidas e inválidas.
- **Importância**: Ajuda a detetar erros em limites de campos numéricos.
- **Aplicação prática**: Teste de intervalo de idade num formulário (ex: 18 a 65).
- [Ver detalhes](#boundary-value-analysis.md)

### 3. Decision Table (Tabela de Decisão)
- **Definição**: Técnica que organiza e testa múltiplas combinações de regras e condições.
- **Importância**: Ideal para regras de negócio complexas.
- **Aplicação prática**: Política de cancelamento de reservas com base em horas e subscrição.
- [Ver detalhes](#decision-table.md)

### 4. State Transition (Transição de Estado)
- **Definição**: Técnica que modela e testa o comportamento de sistemas com base em estados e eventos.
- **Importância**: Fundamental para validar fluxos (ex: autenticação, multi-passos).
- **Aplicação prática**: Sistema de login por PIN com limite de tentativas.
- [Ver detalhes](#state-transition.md)

---

## 📌 Quando usar cada técnica?

| Técnica                        | Usar quando...                                      |
|-------------------------------|-----------------------------------------------------|
| **Equivalence Partitioning**  | Os dados de entrada podem ser agrupados por comportamentos equivalentes |
| **Boundary Value Analysis**   | Há limites numéricos ou intervalos a validar        |
| **Decision Table**            | Existem regras com múltiplas condições e acções     |
| **State Transition**          | O sistema muda de comportamento conforme o estado atual |

---

## 🧩 Requisitos

Este treino pode ser usado com:
- Casos de teste manuais
- Ferramentas de automação (Ex: Cypress, Robot Framework, Playwright)
- Frameworks BDD (Cucumber, Behave, SpecFlow)

---

## 📂 Estrutura recomendada do repositório

### Arquivos principais (conteúdo das técnicas)

- [`README.md`](README.md): Página inicial com visão geral do repositório
- [`equivalence-partitioning.md`](equivalence-partitioning.md): Particionamento por equivalência
- [`boundary-value-analysis.md`](boundary-value-analysis.md): Análise de valores limite
- [`decision-table.md`](decision-table.md): Tabelas de decisão
- [`state-transition.md`](state-transition.md): Testes por transição de estado

### 📂 Pasta `exemplos/` (aplicações práticas)

- [`carrinho_ep.md`](exemplos/carrinho_ep.md): Validação de quantidade em carrinho (EP)
- [`formulario_idade_bva.md`](exemplos/formulario_idade_bva.md): Validação de idade (BVA)
- [`reservas_decision_table.md

---

## ✅ Contribuição

Sinta-se à vontade para adaptar, reutilizar ou melhorar este conteúdo em contextos de formação, documentação interna, workshops ou apresentações.

---

## 📬 Contacto

Dúvidas, sugestões ou ideias para expandir este material? Cria um issue ou entra em contacto com o autor do repositório.

---


