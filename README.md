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
- [Ver detalhes](#-1-equivalence-partitioning-particionamento-por-equivalência)

### 2. Boundary Value Analysis (Análise de Valores Limite)
- **Definição**: Técnica que testa os valores nas fronteiras das entradas válidas e inválidas.
- **Importância**: Ajuda a detetar erros em limites de campos numéricos.
- **Aplicação prática**: Teste de intervalo de idade num formulário (ex: 18 a 65).
- [Ver detalhes](#-2-boundary-value-analysis-análise-de-valores-limite)

### 3. Decision Table (Tabela de Decisão)
- **Definição**: Técnica que organiza e testa múltiplas combinações de regras e condições.
- **Importância**: Ideal para regras de negócio complexas.
- **Aplicação prática**: Política de cancelamento de reservas com base em horas e subscrição.
- [Ver detalhes](#-3-decision-table-tabela-de-decisão)

### 4. State Transition (Transição de Estado)
- **Definição**: Técnica que modela e testa o comportamento de sistemas com base em estados e eventos.
- **Importância**: Fundamental para validar fluxos (ex: autenticação, multi-passos).
- **Aplicação prática**: Sistema de login por PIN com limite de tentativas.
- [Ver detalhes](#-4-state-transition-transição-de-estado)

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
.
├── README.md
├── equivalence-partitioning.md
├── boundary-value-analysis.md
├── decision-table.md
├── state-transition.md
└── exemplos/
├── carrinho_ep.md
├── formulario_idade_bva.md
├── reservas_decision_table.md
└── login_pin_state_transition.md


---

## ✅ Contribuição

Sinta-se à vontade para adaptar, reutilizar ou melhorar este conteúdo em contextos de formação, documentação interna, workshops ou apresentações.

---

## 📬 Contacto

Dúvidas, sugestões ou ideias para expandir este material? Cria um issue ou entra em contacto com o autor do repositório.

---


