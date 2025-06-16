# 🔸 3. Decision Table (Tabela de Decisão)

## 📋 Definição

**Decision Table** é uma técnica de design de testes que utiliza representação tabular para mapear múltiplas condições de entrada e suas respetivas ações, baseada em regras de negócio complexas. É eficaz para sistemas com lógica condicional intrincada.

---

## 🎯 Princípio Fundamental

As tabelas de decisão fornecem uma representação visual sistemática que categoriza condições de entrada e ações resultantes em seções distintas, permitindo uma visualização lógica e transparente do processo de decisão.

---

## 🏗️ Estrutura da Decision Table

### 🔹 Componentes Principais

- **Condition Stubs (Condições Base)**  
  - *Definição:* Lista as várias condições ou critérios que influenciam decisões  
  - *Função:* Entradas da tabela  
  - *Localização:* Lado esquerdo superior da tabela (vertical)

- **Action Stubs (Ações Base)**  
  - *Definição:* Resultados possíveis ou passos tomados  
  - *Função:* Saídas do processo de decisão  
  - *Localização:* Abaixo das condições (vertical)

- **Condition Entries (Entradas de Condição)**  
  - *Definição:* Estados/valores específicos das condições  
  - *Valores:* True/False, Yes/No, valores específicos  
  - *Localização:* Colunas abaixo dos condition stubs

- **Action Entries (Entradas de Ação)**  
  - *Definição:* Ações executadas como reação às condições  
  - *Valores:* `X` (executar), `-` (não executar)  
  - *Localização:* Colunas abaixo dos action stubs

---

### 🔹 Formato Visual da Tabela

```text
┌─────────────────────┬─────┬─────┬─────┬─────┐
│ Condition Stubs     │ R1  │ R2  │ R3  │ R4  │
├─────────────────────┼─────┼─────┼─────┼─────┤
│ Condição 1          │  T  │  T  │  F  │  F  │
│ Condição 2          │  T  │  F  │  T  │  F  │
├─────────────────────┼─────┼─────┼─────┼─────┤
│ Action Stubs        │     │     │     │     │
├─────────────────────┼─────┼─────┼─────┼─────┤
│ Ação 1              │  X  │  -  │  X  │  -  │
│ Ação 2              │  -  │  X  │  -  │  X  │
└─────────────────────┴─────┴─────┴─────┴─────┘
```

> 💡 **Regra Padrão (Default Rule):** cobre combinações não explicitamente definidas.

---

## 🎯 Importância e Aplicabilidade

### ✅ Benefícios

- Cobertura sistemática de regras
- Visualização clara de decisões complexas
- Detecção de ambiguidade e inconsistências
- Facilita a comunicação técnica-negócio

### ✅ Cenários Ideais

- Validações com múltiplas regras
- Processamento condicional de transações
- Sistemas de aprovação
- Configurações com várias opções
- Workflows com lógica condicional

---

## ⚙️ Processo de Aplicação

1. **Identificação de Condições**
   - Analisar especificações, mapear variáveis, identificar estados
2. **Mapeamento de Ações**
   - Listar ações possíveis e seus efeitos
3. **Construção da Tabela**
   - Criar matriz com combinações possíveis, otimizar e validar
4. **Definição de Resultados**
   - Especificar ações esperadas, resolver conflitos
5. **Extração de Casos de Teste**
   - Converter regras em testes com entradas e saídas esperadas

---

## ✅ Vantagens

### 📌 Sistemática e Cobertura

- Cobertura completa de combinações relevantes
- Prevenção de lacunas

### 📌 Clareza e Comunicação

- Intuitiva para entender lógica de negócio
- Facilita documentação e revisão

### 📌 Manutenibilidade

- Fácil atualização
- Rastreabilidade clara
- Rapidez em avaliar impacto de mudanças

---

## ⚠️ Limitações e Desafios

- **Complexidade crescente:** explosão combinatória
- **Requisitos de qualidade:** necessidade de especificações claras
- **Limitações de aplicação:** não ideal para lógica simples, performance ou usabilidade

---

## 🛠️ Estratégias de Otimização

- **Técnicas de Redução**
  - *Collapsed Decision Tables*
  - *Extended Entry Tables*
  - *Mixed Entry Tables*

- **Simplificação Prática**
  - *Don't Care Conditions (-)*
  - *Eliminação de combinações impossíveis*
  - *Consolidação de regras*

---

## 💡 Exemplo Prático: Sistema de Aprovação de Empréstimos

### 🔹 Condições

- Idade >= 18 anos  
- Rendimento >= €1000/mês  
- Histórico de crédito bom  
- Valor do empréstimo <= 10x rendimento

### 🔹 Ações

- Aprovar empréstimo  
- Rejeitar por idade  
- Rejeitar por rendimento  
- Rejeitar por histórico  
- Solicitar garantias adicionais

### 🔹 Tabela de Decisão

```text
Condições                R1  R2  R3  R4  R5  R6  R7  R8
Idade >= 18              T   T   T   T   F   F   F   F
Rendimento >= €1000      T   T   F   F   T   T   F   F
Histórico Bom            T   F   T   F   T   F   T   F
Valor <= 10x Rendimento  T   F   T   F   T   F   T   F

Ações
Aprovar                  X   -   -   -   -   -   -   -
Rejeitar por Idade       -   -   -   -   X   X   X   X
Rejeitar por Rendimento  -   -   X   X   -   -   X   X
Rejeitar por Histórico   -   X   -   X   -   X   -   X
Solicitar Garantias      -   X   -   -   -   -   -   -
```

---

### 🔹 Casos de Teste Derivados

| Caso  | Idade | Rendimento | Histórico | Valor    | Resultado Esperado                  |
|-------|-------|------------|-----------|----------|--------------------------------------|
| TC01  | 25    | €1500      | Bom       | €10000   | Aprovação automática                 |
| TC02  | 30    | €1200      | Mau       | €15000   | Solicitar garantias adicionais       |
| TC03  | 22    | €800       | Bom       | €5000    | Rejeição por rendimento insuficiente |
| TC04  | 16    | €2000      | Bom       | €8000    | Rejeição por idade                   |

---

## 🔗 Integração com Outras Técnicas

### 🔹 Complementaridade

- *Equivalence Partitioning*
- *Boundary Value Analysis*
- *State Transition Testing*

### 🔹 Combinação Estratégica

- *Pairwise Testing*
- *Cause-Effect Graphing*
- *Risk-Based Testing*

---

## 📊 Métricas e Avaliação

- **Indicadores**
  - % de regras cobertas
  - Nº de condições por regra
  - Complexidade ciclomática

- **Critérios de Completude**
  - Cobertura de todas combinações lógicas
  - Mapeamento de todas ações possíveis
  - Resolução de inconsistências

---

## 🚀 Ferramentas e Automação

- Geradores automáticos de tabelas
- Validação automatizada
- Geração de casos de teste
- Integração com CI/CD
- Documentação viva e rastreável

> 💬 *As Decision Tables ajudam a dominar a complexidade de regras de negócio e são uma ferramenta poderosa para QA e análise de requisitos.*

