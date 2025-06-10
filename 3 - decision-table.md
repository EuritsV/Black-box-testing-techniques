## 🔸 3. Decision Table (Tabela de Decisão)

## 📋 Definição

**Decision Table** é uma técnica de design de testes que utiliza representação tabular para mapear **múltiplas condições de entrada e suas respetivas ações**, baseada em regras de negócio complexas. Esta técnica é especialmente eficaz para sistemas com lógica condicional intrincada, onde múltiplas variáveis influenciam o comportamento do sistema.

### Princípio Fundamental
As tabelas de decisão fornecem uma representação visual sistemática que categoriza condições de entrada e ações resultantes em seções distintas, permitindo uma visualização lógica e transparente do processo de tomada de decisão.

## 🏗️ Estrutura da Decision Table

### Componentes Principais

#### Condition Stubs (Condições Base)
- **Definição**: Lista as várias condições ou critérios que podem influenciar os resultados das decisões
- **Função**: Atuam como as **entradas** para a tabela
- **Localização**: Lado esquerdo da tabela, na vertical

#### Action Stubs (Ações Base)  
- **Definição**: Delineiam os resultados potenciais ou passos tomados em resposta às condições
- **Função**: Representam as **saídas** do processo de tomada de decisão
- **Localização**: Lado esquerdo da tabela, abaixo das condições

#### Condition Entries (Entradas de Condição)
- **Definição**: Especificam os estados ou valores específicos das condições sendo avaliadas
- **Valores**: Tipicamente **True/False**, **Yes/No**, ou valores específicos
- **Localização**: Colunas sob os condition stubs

#### Action Entries (Entradas de Ação)
- **Definição**: Definem claramente as ações empreendidas como reação às condições estabelecidas
- **Valores**: **X** (executar), **-** (não executar), ou descrições específicas
- **Localização**: Colunas sob os action stubs

### Formato Visual da Tabela
```
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

## 🎯 Importância e Aplicabilidade

### Benefícios Principais
- **Cobertura sistemática** de todas as regras de decisão
- **Visualização clara** de decisões complexas
- **Eliminação de ambiguidades** na lógica de negócio
- **Detecção de lacunas** e inconsistências nas especificações
- **Facilitação da comunicação** entre stakeholders técnicos e de negócio

### Cenários Ideais de Aplicação
- **Sistemas de validação** com múltiplas regras
- **Processamento de transações** com várias condições
- **Sistemas de aprovação** com critérios complexos
- **Configurações de sistema** com múltiplas opções
- **Fluxos de trabalho** condicionais

## ⚙️ Processo de Aplicação

### 1. Identificação de Condições
- **Analisar especificações** para identificar todas as condições relevantes
- **Mapear variáveis de entrada** que influenciam decisões
- **Catalogar estados do sistema** que afetam comportamento
- **Identificar condições implícitas** não documentadas

### 2. Mapeamento de Ações
- **Listar todas as ações possíveis** que o sistema pode executar
- **Categorizar tipos de resposta** (aprovação, rejeição, processamento especial)
- **Identificar ações combinadas** que podem ocorrer simultaneamente
- **Documentar efeitos colaterais** de cada ação

### 3. Construção da Tabela
- **Criar matriz completa** com todas as combinações possíveis
- **Eliminar combinações impossíveis** ou irrelevantes
- **Otimizar a tabela** removendo redundâncias
- **Validar completude** da cobertura

### 4. Definição de Resultados
- **Especificar ações esperadas** para cada combinação
- **Validar consistência** das regras de negócio
- **Resolver conflitos** e ambiguidades
- **Documentar exceções** e casos especiais

### 5. Extração de Casos de Teste
- **Converter cada regra** numa caso de teste
- **Definir dados de entrada** específicos
- **Especificar resultados esperados** detalhados
- **Incluir validações** de efeitos colaterais

## ✅ Vantagens

### Sistemática e Cobertura
- **Testes abrangentes e sistemáticos** de todas as combinações relevantes
- **Cobertura garantida** de cenários complexos
- **Prevenção de lacunas** na cobertura de testes

### Clareza e Comunicação
- **Visualização intuitiva** da lógica de negócio
- **Documentação clara** das regras de decisão
- **Facilitação do diálogo** entre equipas técnicas e de negócio

### Manutenibilidade
- **Fácil atualização** quando regras mudam
- **Rastreabilidade clara** entre regras e testes
- **Identificação rápida** de impactos de mudanças

## ⚠️ Limitações e Desafios

### Complexidade Crescente
- **Explosão combinatória** com muitas condições
- **Dificuldade de gestão** em tabelas muito grandes
- **Necessidade de otimização** cuidadosa

### Requisitos de Qualidade
- **Dependência de especificações** claras e completas
- **Necessidade de validação** constante das regras
- **Requer análise cuidadosa** para evitar redundâncias

### Limitações de Aplicação
- **Menos eficaz** para fluxos sequenciais simples
- **Inadequada** para testes de performance ou usabilidade
- **Pode ser excessiva** para lógica simples

## 🛠️ Estratégias de Otimização

### Técnicas de Redução
- **Collapsed Decision Tables**: Combinar colunas com ações idênticas
- **Extended Entry Tables**: Usar valores específicos em vez de True/False
- **Mixed Entry Tables**: Combinar diferentes tipos de entrada

### Simplificação Prática
- **Don't Care Conditions**: Usar "-" para condições irrelevantes
- **Impossible Combinations**: Eliminar cenários logicamente impossíveis
- **Rule Consolidation**: Combinar regras similares

## 💡 Exemplo Prático Detalhado

### Cenário: Sistema de Aprovação de Empréstimos

#### Condições Base
- **Idade >= 18 anos**
- **Rendimento >= €1000/mês**
- **Histórico de crédito bom**
- **Valor empréstimo <= 10x rendimento**

#### Ações Base
- **Aprovar empréstimo**
- **Rejeitar por idade**
- **Rejeitar por rendimento**
- **Rejeitar por histórico**
- **Solicitar garantias adicionais**

#### Tabela de Decisão Completa

| Condições | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
|-----------|----|----|----|----|----|----|----|----|
| Idade >= 18 | T | T | T | T | F | F | F | F |
| Rendimento >= €1000 | T | T | F | F | T | T | F | F |
| Histórico Bom | T | F | T | F | T | F | T | F |
| Valor <= 10x Rendimento | T | F | T | F | T | F | T | F |
| **Ações** | | | | | | | | |
| Aprovar | X | - | - | - | - | - | - | - |
| Rejeitar por Idade | - | - | - | - | X | X | X | X |
| Rejeitar por Rendimento | - | - | X | X | - | - | X | X |
| Rejeitar por Histórico | - | X | - | X | - | X | - | X |
| Solicitar Garantias | - | X | - | - | - | - | - | - |

### Casos de Teste Derivados

| Caso | Idade | Rendimento | Histórico | Valor | Resultado Esperado |
|------|-------|------------|-----------|-------|-------------------|
| TC01 | 25 | €1500 | Bom | €10000 | Aprovação automática |
| TC02 | 30 | €1200 | Mau | €15000 | Solicitar garantias adicionais |
| TC03 | 22 | €800 | Bom | €5000 | Rejeição por rendimento insuficiente |
| TC04 | 16 | €2000 | Bom | €8000 | Rejeição por idade |

## 🔗 Integração com Outras Técnicas

### Complementaridade
- **Equivalence Partitioning**: Para definir valores das condições
- **Boundary Value Analysis**: Para testar limites das condições
- **State Transition Testing**: Para fluxos com estados dependentes

### Combinação Estratégica
- **Pairwise Testing**: Para reduzir combinações em tabelas grandes
- **Cause-Effect Graphing**: Para visualizar dependências complexas
- **Risk-Based Testing**: Para priorizar regras críticas

## 📊 Métricas e Avaliação

### Indicadores de Qualidade
- **Percentual de regras cobertas**
- **Número de condições por regra**
- **Complexidade ciclomática da tabela**

### Critérios de Completude
- **Todas as combinações lógicas** representadas
- **Todas as ações possíveis** mapeadas
- **Inconsistências e conflitos** resolvidos

## 🚀 Ferramentas e Automação

### Suporte Tecnológico
- **Geradores automáticos** de tabelas de decisão
- **Validação de consistência** automatizada
- **Conversão automática** para casos de teste

### Integração em Processos
- **Documentação viva** sincronizada com código
- **CI/CD integration** para validação contínua
- **Rastreabilidade** requisitos-regras-testes

---

*Decision Tables representam uma ferramenta poderosa para dominar a complexidade de sistemas com múltiplas regras de negócio, garantindo cobertura sistemática e comunicação clara entre todas as partes interessadas no projeto.*
