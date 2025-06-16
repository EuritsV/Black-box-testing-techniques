# 🧪 Mini manual: Técnicas de Teste Caixa Preta

## Introdução

No universo dos testes de software, um dos maiores desafios é garantir uma cobertura abrangente sem cair na armadilha de testar exaustivamente todas as combinações possíveis – uma tarefa, na maioria das vezes, inviável. É aqui que entra as tecnicas de teste  **Equivalence Partitioning** (Particionamento por Equivalência), **Boundary Value Analysis** (Análise de Valores Limite), **Decision Table** (Tabela de Decisão), **State Transition** (Transição de Estado)  técnicas de design de testes poderosas e inteligentes.

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
- [Ver detalhes](https://github.com/EuritsV/Black-box-testing-techniques/blob/main/1%20-%20equivalence-partitioning.md#-1-equivalence-partitioning-particionamento-por-equival%C3%AAncia)

### 2. Boundary Value Analysis (Análise de Valores Limite)
- **Definição**: Técnica que testa os valores nas fronteiras das entradas válidas e inválidas.
- **Importância**: Ajuda a detetar erros em limites de campos numéricos.
- **Aplicação prática**: Teste de intervalo de idade num formulário (ex: 18 a 65).
- [Ver detalhes](https://github.com/EuritsV/Black-box-testing-techniques/blob/main/2%20-%20boundary-value-analysis.md#-2-boundary-value-analysis-an%C3%A1lise-de-valores-limite)

### 3. Decision Table (Tabela de Decisão)
- **Definição**: Técnica que organiza e testa múltiplas combinações de regras e condições.
- **Importância**: Ideal para regras de negócio complexas.
- **Aplicação prática**: Política de cancelamento de reservas com base em horas e subscrição.
- [Ver detalhes](https://github.com/EuritsV/Black-box-testing-techniques/blob/main/3%20-%20decision-table.md#-3-decision-table-tabela-de-decis%C3%A3o)

### 4. State Transition (Transição de Estado)
- **Definição**: Técnica que modela e testa o comportamento de sistemas com base em estados e eventos.
- **Importância**: Fundamental para validar fluxos (ex: autenticação, multi-passos).
- **Aplicação prática**: Sistema de login por PIN com limite de tentativas.
- [Ver detalhes](https://github.com/EuritsV/Black-box-testing-techniques/blob/main/4%20-%20state-transition.md#-4-state-transition-transi%C3%A7%C3%A3o-de-estado)

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
- [`equivalence-partitioning.md`](https://github.com/EuritsV/Black-box-testing-techniques/blob/main/1%20-%20equivalence-partitioning.md#-1-equivalence-partitioning-particionamento-por-equival%C3%AAncia): Particionamento por equivalência
- [`boundary-value-analysis.md`](https://github.com/EuritsV/Black-box-testing-techniques/blob/main/2%20-%20boundary-value-analysis.md#-2-boundary-value-analysis-an%C3%A1lise-de-valores-limite): Análise de valores limite
- [`decision-table.md`](https://github.com/EuritsV/Black-box-testing-techniques/blob/main/3%20-%20decision-table.md#-3-decision-table-tabela-de-decis%C3%A3o): Tabelas de decisão
- [`state-transition.md`](https://github.com/EuritsV/Black-box-testing-techniques/blob/main/4%20-%20state-transition.md#-4-state-transition-transi%C3%A7%C3%A3o-de-estado): Testes por transição de estado

### 📂 Pasta `exemplos/` (aplicações práticas) -> Em progresso, não finalizado

- [`carrinho_ep.md`](carrinho_ep.md): Validação de quantidade em carrinho (EP)
- [`formulario_idade_bva.md`](formulario_idade_bva.md): Validação de idade (BVA)
- [`reservas_decision_table.md

---

## ✅ Contribuição

Sinta-se à vontade para adaptar, reutilizar ou melhorar este conteúdo em contextos de formação, documentação interna, workshops ou apresentações.

---

## 📬 Contacto

Dúvidas, sugestões ou ideias para expandir este material? Cria um issue ou entra em contacto com o autor do repositório.

---


