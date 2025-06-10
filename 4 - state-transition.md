## 🔷 4. State Transition (Transição de Estado)

## 📋 Definição

**State Transition Testing** é uma técnica dinâmica e poderosa de design de testes utilizada para analisar o comportamento de uma aplicação em **diferentes condições de entrada e vários estados**. Esta técnica é particularmente útil em cenários onde o sistema de software possui um número finito de estados e as transições entre esses estados são desencadeadas por eventos ou condições específicas.

### Princípio Fundamental
O método concentra-se nas **transições válidas e inválidas** entre estados, permitindo que os testadores garantam que a aplicação se comporte conforme esperado em todas as circunstâncias, identificando defeitos que podem não ser detetados através de outras técnicas de teste.

## 🏗️ Componentes Fundamentais

### Estados (States)
- **Definição**: Condições ou situações específicas em que o sistema pode existir
- **Características**: Finitos, bem definidos e mutuamente exclusivos
- **Exemplos**: Ligado/Desligado, Autenticado/Não autenticado, Ativo/Inativo

### Eventos (Events)
- **Definição**: Ações, condições ou triggers que causam mudanças de estado
- **Tipos**: Ações do utilizador, timeouts, condições do sistema, dados recebidos
- **Função**: Iniciadores das transições entre estados

### Transições (Transitions)
- **Definição**: Mudanças de um estado para outro como resultado de um evento
- **Características**: Podem ser instantâneas e resultar em ações específicas
- **Sintaxe padrão**: `"evento [condição de guarda] / ação"`

### Condições de Guarda (Guard Conditions)
- **Definição**: Condições adicionais que devem ser verdadeiras para que a transição ocorra
- **Função**: Qualificam quando um evento pode desencadear uma transição
- **Exemplo**: `[saldo > 0]` numa transição de pagamento

### Ações (Actions)
- **Definição**: Operações executadas durante uma transição
- **Tipos**: Atualizações de dados, envio de mensagens, cálculos
- **Timing**: Executadas instantaneamente durante a transição

## 🎯 Importância e Aplicabilidade

### Benefícios Principais
- **Validação de fluxos de trabalho** complexos e sequenciais
- **Verificação de autenticação** e autorização
- **Teste de formulários multi-etapas** e wizards
- **Deteção de falhas** quando o sistema depende de estados anteriores
- **Cobertura de comportamentos** dependentes de histórico

### Cenários Ideais
- **Sistemas de autenticação** com múltiplas tentativas
- **Fluxos de compra** em e-commerce
- **Máquinas de estado** em sistemas embebidos
- **Processamento de transações** financeiras
- **Fluxos de aprovação** em workflows
- **Jogos** com diferentes níveis e estados

## 📊 Modelação de Estados

### 1. State Transition Diagram (Diagrama de Transição de Estados)
Representação visual que mostra:
- **Estados** como círculos ou retângulos
- **Transições** como setas direcionais
- **Eventos e condições** como etiquetas nas setas
- **Estado inicial** marcado especialmente
- **Estados finais** com dupla linha

#### Exemplo Visual:
```
    [Pin Incorreto]
S1 ────────────────► S2 ────────────────► S3 ────────────────► S4 ────────────────► S6
│   Pedir Pin        │   [Pin Incorreto]  │   [Pin Incorreto]  │   [Pin Incorreto]  │
│                    │                    │                    │                    │
│   [Pin Correto]    │   [Pin Correto]    │   [Pin Correto]    │                    │
└────────────────────┼────────────────────┼────────────────────┘                    │
                     │                    │                                         │
                     └────────────────────┼─────────────────────────────────────────┘
                                          │                              Conta
                                          └─────────────► S5             Bloqueada
                                            [Pin Correto]   Acesso
                                                           Concedido
```

### 2. State Table (Tabela de Estados)
Representação matricial onde:
- **Linhas** representam estados atuais
- **Colunas** representam eventos
- **Células** contêm estado de destino e ações
- **Células vazias** representam transições inválidas

#### Exemplo de Tabela de Estados:

| Estado Atual | Pin Correto | Pin Incorreto | Timeout | Reset |
|--------------|-------------|---------------|---------|-------|
| **S1 (Início)** | S5 / Conceder Acesso | S2 / Registar Tentativa | - | S1 |
| **S2 (1ª Tentativa)** | S5 / Conceder Acesso | S3 / Registar Tentativa | S1 / Reset | S1 |
| **S3 (2ª Tentativa)** | S5 / Conceder Acesso | S4 / Registar Tentativa | S1 / Reset | S1 |
| **S4 (3ª Tentativa)** | S5 / Conceder Acesso | S6 / Bloquear Conta | S1 / Reset | S1 |
| **S5 (Acesso Concedido)** | - | - | S1 / Logout | S1 |
| **S6 (Conta Bloqueada)** | - | - | - | S1 / Desbloquear |

## ⚙️ Processo de Aplicação

### 1. Análise e Identificação
- **Mapear todos os estados possíveis** do sistema
- **Identificar eventos** que podem ocorrer
- **Analisar especificações** para compreender comportamentos
- **Consultar stakeholders** para validar compreensão

### 2. Modelação do Sistema
- **Criar diagrama de transição** ou tabela de estados
- **Definir estado inicial** e estados finais
- **Mapear todas as transições válidas**
- **Identificar transições inválidas** explicitamente

### 3. Validação do Modelo
- **Revisar com equipas de desenvolvimento** e negócio
- **Verificar completude** de todos os cenários
- **Validar consistência** das regras de transição
- **Confirmar ações** associadas às transições

### 4. Design de Casos de Teste
- **Cobertura de todos os estados**: Cada estado deve ser visitado
- **Cobertura de todas as transições válidas**: Cada transição deve ser testada
- **Teste de transições inválidas**: Verificar tratamento de erros
- **Sequências típicas**: Fluxos de utilizador normais
- **Sequências atípicas**: Cenários de exceção

### 5. Estratégias de Cobertura

#### All States Coverage
- **Objetivo**: Visitar cada estado pelo menos uma vez
- **Critério mínimo** de cobertura
- **Adequado para**: Validação básica de funcionalidade

#### All Transitions Coverage  
- **Objetivo**: Executar cada transição válida pelo menos uma vez
- **Cobertura mais abrangente** que All States
- **Recomendado para**: Maioria dos sistemas críticos

#### All Paths Coverage
- **Objetivo**: Testar todos os caminhos possíveis
- **Pode ser impraticável** em sistemas complexos
- **Adequado para**: Sistemas pequenos e críticos

## ✅ Vantagens

### Cobertura Sistemática
- **Garantia de cobertura** de todas as transições válidas
- **Identificação de estados não alcançáveis** ou órfãos
- **Verificação de completude** do comportamento do sistema

### Deteção de Defeitos
- **Comportamentos inesperados** em sequências específicas
- **Estados inconsistentes** ou corrompidos
- **Transições em falta** ou incorretas
- **Problemas de sincronização** em sistemas concorrentes

### Clareza e Comunicação
- **Visualização clara** dos fluxos do sistema
- **Documentação viva** do comportamento esperado
- **Facilitação da comunicação** entre equipas

## ⚠️ Limitações e Desafios

### Complexidade de Modelação
- **Sistemas com muitos estados** podem ser difíceis de modelar
- **Explosion de estados** em sistemas complexos
- **Necessidade de abstração** adequada

### Requisitos de Qualidade
- **Mapeamento preciso** de estados e eventos é essencial
- **Especificações claras** são prerequisito
- **Manutenção constante** do modelo conforme evolução

### Limitações Práticas
- **Não adequada** para lógica puramente funcional
- **Menos eficaz** para validação de dados
- **Pode ser excessiva** para fluxos simples

## 💡 Exemplo Prático Detalhado

### Cenário: Sistema de Gestão de PIN Bancário

#### Estados Identificados
- **S1**: Início (estado inicial)
- **S2**: 1ª Tentativa (primeira tentativa incorreta)
- **S3**: 2ª Tentativa (segunda tentativa incorreta)  
- **S4**: 3ª Tentativa (terceira tentativa incorreta)
- **S5**: Acesso Concedido (PIN válido inserido)
- **S6**: Conta Bloqueada (três tentativas incorretas)

#### Eventos do Sistema
- **Pedir PIN**: Solicitar inserção do PIN
- **PIN Correto**: PIN válido inserido
- **PIN Incorreto**: PIN inválido inserido
- **Timeout**: Tempo limite excedido
- **Reset Administrativo**: Intervenção administrativa

#### Casos de Teste Derivados

| Caso | Sequência de Estados | Eventos | Resultado Esperado |
|------|---------------------|---------|-------------------|
| **TC01** | S1 → S5 | PIN Correto na 1ª tentativa | Acesso imediato concedido |
| **TC02** | S1 → S2 → S5 | PIN Incorreto → PIN Correto | Acesso concedido após 1 erro |
| **TC03** | S1 → S2 → S3 → S5 | 2x PIN Incorreto → PIN Correto | Acesso concedido após 2 erros |
| **TC04** | S1 → S2 → S3 → S4 → S6 | 3x PIN Incorreto → PIN Incorreto | Conta bloqueada |
| **TC05** | S1 → S2 → S3 → S4 → S5 | 3x PIN Incorreto → PIN Correto | Acesso na última tentativa |
| **TC06** | S5 → S1 | Timeout após acesso | Logout automático |
| **TC07** | S6 → S1 | Reset administrativo | Conta desbloqueada |

#### Testes de Transições Inválidas

| Caso | Tentativa de Transição | Resultado Esperado |
|------|----------------------|-------------------|
| **TC08** | S5 → S2 (PIN incorreto após acesso) | Transição rejeitada/Logout |
| **TC09** | S6 → S5 (acesso direto de conta bloqueada) | Transição negada |
| **TC10** | Estados inexistentes | Tratamento de erro adequado |

## 🔧 Estratégias Avançadas

### Redução de Complexidade
- **Abstração de estados**: Agrupar estados similares
- **Hierarquia de estados**: Estados compostos e sub-estados
- **Particionamento do modelo**: Dividir em módulos menores

### Otimização de Testes
- **Geração automática** de casos de teste
- **Priorização baseada em risco** dos caminhos
- **Cobertura incremental** começando pelos fluxos críticos

## 🔗 Integração com Outras Técnicas

### Técnicas Complementares
- **Equivalence Partitioning**: Para valores nas condições de guarda
- **Boundary Value Analysis**: Para limites em transições numéricas
- **Decision Tables**: Para lógica complexa nas condições

### Combinação Estratégica
- **Use Case Testing**: Para validar cenários completos de utilizador
- **Risk-Based Testing**: Para priorizar estados e transições críticos
- **Model-Based Testing**: Para geração automática de testes

## 📊 Métricas e Avaliação

### Indicadores de Cobertura
- **Percentual de estados visitados**
- **Percentual de transições executadas**
- **Número de caminhos únicos testados**

### Métricas de Qualidade
- **Densidade de defeitos por estado**
- **Tempo médio de execução por transição**
- **Complexidade ciclomática do modelo**

## 🚀 Ferramentas e Automação

### Ferramentas de Modelação
- **Ferramentas UML** para diagramas de estado
- **Ferramentas de workflow** para processos de negócio
- **Simuladores de máquinas de estado**

### Automação de Testes
- **Execução automática** de sequências de estados
- **Validação automática** de transições
- **Monitorização em tempo real** de estados do sistema
