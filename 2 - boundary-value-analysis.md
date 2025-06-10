## 🔹 2. Boundary Value Analysis (Análise de Valores Limite)


## 📋 Definição

**Boundary Value Analysis (BVA)** é uma técnica de design de testes que se concentra nos **valores nos limites e fronteiras** das partições válidas e inválidas. Esta técnica baseia-se na premissa de que a maioria dos erros de software ocorre nos limites dos domínios de entrada, onde as condições de fronteira são frequentemente mal implementadas.

### Princípio Fundamental
Os defeitos tendem a concentrar-se nas fronteiras dos intervalos de dados, tornando essencial testar não apenas os valores limite, mas também os valores imediatamente adjacentes a essas fronteiras.

## 🎯 Importância e Justificação

### Por que os Limites são Críticos?
- **Erros de implementação**: Programadores frequentemente cometem erros com operadores `<`, `<=`, `>`, `>=`
- **Condições off-by-one**: Erros clássicos de indexação e contagem
- **Validações incorretas**: Implementação inadequada de regras de negócio
- **Overflow/Underflow**: Problemas com limites de tipos de dados

### Estatísticas de Eficácia
- Detecta aproximadamente **80% dos defeitos relacionados a limites**
- Requer apenas **poucos casos de teste** por campo
- **Alta relação custo-benefício** comparado a testes exaustivos

## 🔧 Métodos de Aplicação

### Método 2-BVA (Two-Point Boundary Value Analysis)
Foca exclusivamente nos **valores mínimos e máximos** do intervalo.

**Valores testados:**
- Valor **abaixo do mínimo** (inválido)
- Valor **no mínimo** (válido)
- Valor **no máximo** (válido)  
- Valor **acima do máximo** (inválido)

### Método 3-BVA (Three-Point Boundary Value Analysis)
Expande a cobertura do 2-BVA adicionando valores **adjacentes aos limites**.

**Valores testados:**
- Valor **abaixo do mínimo** (inválido)
- Valor **no mínimo** (válido)
- Valor **imediatamente acima do mínimo** (válido)
- Valor **imediatamente abaixo do máximo** (válido)
- Valor **no máximo** (válido)
- Valor **acima do máximo** (inválido)

### Método Robusto BVA
Inclui **múltiplos valores inválidos** em cada extremo para testar robustez do sistema.

## ✅ Processo de Aplicação

### 1. Identificação de Intervalos
- **Analisar especificações** para encontrar todos os campos com limites
- **Catalogar tipos de dados** (inteiros, decimais, datas, strings)
- **Identificar limites implícitos** (tamanhos de buffer, capacidades)

### 2. Determinação de Valores Limite
- **Limites explícitos**: Definidos nas especificações
- **Limites de sistema**: Máximos de tipos de dados
- **Limites de domínio**: Regras de negócio específicas

### 3. Seleção de Valores de Teste
- **Valores válidos**: Nos limites e adjacentes
- **Valores inválidos**: Fora dos limites
- **Valores especiais**: Zero, null, vazio, máximos de sistema

### 4. Design dos Casos de Teste
- **Estruturar casos** com dados de entrada, procedimentos e resultados esperados
- **Incluir validações** para comportamentos de erro
- **Documentar justificativas** para cada valor escolhido

### 5. Execução e Validação
- **Testar sistematicamente** cada valor
- **Verificar mensagens de erro** apropriadas
- **Validar comportamento** nos limites válidos

## 📊 Tipos de Limites

### Limites Numéricos
- **Inteiros**: 0, 1, -1, MAX_INT, MIN_INT
- **Decimais**: 0.0, 0.1, -0.1, valores de precisão
- **Percentuais**: 0%, 1%, 99%, 100%, 101%

### Limites de String
- **Comprimento**: String vazia, 1 caractere, máximo permitido
- **Caracteres especiais**: Início/fim com espaços, caracteres unicode
- **Formato**: Padrões de email, telefone, códigos

### Limites Temporais
- **Datas**: 01/01/1900, 31/12/2099, anos bissextos
- **Horários**: 00:00:00, 23:59:59, mudanças de fuso
- **Períodos**: Durações mínimas/máximas

### Limites de Sistema
- **Memória**: Buffers pequenos/grandes
- **Rede**: Timeouts, largura de banda
- **Arquivos**: Tamanhos mínimos/máximos

## ✅ Vantagens

### Eficácia
- **Alta detecção de defeitos** com poucos testes
- **Foco nas áreas mais propensas** a erros
- **Cobertura sistemática** de todas as fronteiras

### Eficiência
- **Redução significativa** no número de testes
- **Fácil automação** e manutenção
- **ROI elevado** comparado a outras técnicas

### Aplicabilidade
- **Ideal para campos numéricos** com intervalos bem definidos
- **Compatível com automação** de testes
- **Integração natural** com Equivalence Partitioning

## ⚠️ Limitações e Considerações

### Principais Limitações
- **Dependência de especificações claras** dos limites
- **Não cobre lógica interna** complexa do sistema
- **Inadequada para fluxos** de estados complexos
- **Pode perder defeitos** em combinações de parâmetros

### Contextos Menos Apropriados
- Sistemas com **lógica predominantemente qualitativa**
- **Fluxos de trabalho** complexos
- **Interações** entre múltiplos componentes
- **Regras de negócio** não baseadas em limites

## 💡 Exemplo Prático Detalhado

### Cenário: Campo "Idade" para Sistema de Seguros
**Intervalo válido**: 18 a 65 anos

| Valor | Classificação | Objetivo do Teste | Resultado Esperado |
|-------|---------------|-------------------|-------------------|
| 17    | Inválido (abaixo) | Testar rejeição abaixo do mínimo | Erro: "Idade mínima é 18 anos" |
| 18    | Válido (limite inferior) | Validar aceitação no mínimo | Aceito - processa normalmente |
| 19    | Válido (acima do mínimo) | Confirmar valores próximos ao limite | Aceito - processa normalmente |
| 64    | Válido (abaixo do máximo) | Confirmar valores próximos ao limite | Aceito - processa normalmente |
| 65    | Válido (limite superior) | Validar aceitação no máximo | Aceito - processa normalmente |
| 66    | Inválido (acima) | Testar rejeição acima do máximo | Erro: "Idade máxima é 65 anos" |

### Casos de Teste Adicionais
- **0**: Teste de valor zero
- **-1**: Teste de valor negativo
- **999**: Teste de valor extremamente alto
- **Null/Vazio**: Teste de valores ausentes

## 🔗 Integração com Outras Técnicas

### Complementaridade com Equivalence Partitioning
- **EP**: Define as partições
- **BVA**: Testa os limites das partições
- **Combinação**: Cobertura completa e eficiente

### Uso com Decision Tables
- **Limites como condições** nas tabelas de decisão
- **Combinações de limites** para regras complexas
- **Validação de múltiplos parâmetros** simultaneamente

### Aplicação em Testes Automatizados
- **Parametrização fácil** de valores limite
- **Execução repetível** e consistente
- **Integração em pipelines** de CI/CD

## 🛠️ Ferramentas e Implementação

### Estratégias de Automação
- **Data-driven testing** com valores limite pré-definidos
- **Geração automática** de casos de teste
- **Validação automática** de mensagens de erro

### Documentação e Rastreabilidade
- **Matriz de cobertura** de limites testados
- **Mapeamento requisitos-limites-testes**
- **Relatórios de execução** detalhados

## 📈 Métricas e Avaliação

### Indicadores de Cobertura
- **Percentual de limites testados**
- **Número de defeitos encontrados por limite**
- **Tempo de execução por caso de teste**

### Critérios de Sucesso
- **Todos os limites identificados** foram testados
- **Comportamentos de erro** validados adequadamente
- **Performance aceitável** nos valores limite
