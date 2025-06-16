# 🔹 2. Análise de Valores Limite (Boundary Value Analysis - BVA)

## 📋 Definição
A **Boundary Value Analysis (BVA)** é uma técnica de design de testes que foca nos valores extremos (limites) das partições válidas e inválidas de um domínio de entrada. A premissa é que a maioria dos erros de software ocorre exatamente nessas fronteiras, onde as condições são frequentemente mal interpretadas ou implementadas.

### Princípio Fundamental
Defeitos tendem a se concentrar nas fronteiras dos intervalos de dados. Por isso, é crucial testar não apenas os valores limite, mas também aqueles imediatamente adjacentes a essas fronteiras.

## 🎯 Importância e Justificativa

### Por que os Limites são Críticos?
- **Erros de implementação**: Programadores frequentemente erram ao usar operadores como `<`, `<=`, `>`, `>=`.
- **Condições "off-by-one"**: Falhas clássicas de indexação e contagem (e.g., usar `n` em vez de `n-1` ou vice-versa).
- **Validações incorretas**: Implementação inadequada de regras de negócio.
- **Overflow/Underflow**: Problemas com os limites de tipos de dados numéricos.

### Estatísticas de Eficácia
- Detecta aproximadamente **80% dos defeitos** relacionados a limites.
- Requer **poucos casos de teste por campo**.
- Apresenta uma **alta relação custo-benefício** comparada a testes exaustivos.

## 🔧 Métodos de Aplicação

### 2-BVA (Two-Point Boundary Value Analysis)
Foca nos valores mínimo e máximo do intervalo, além dos imediatamente adjacentes (um abaixo do mínimo e um acima do máximo).

**Exemplo** para um intervalo `[min, max]`: `min−1`, `min`, `max`, `max+1`.

### 3-BVA (Three-Point Boundary Value Analysis)
Expande o 2-BVA, adicionando valores imediatamente adjacentes aos limites internos do intervalo.

**Exemplo** para um intervalo `[min, max]`: `min−1`, `min`, `min+1`, `max−1`, `max`, `max+1`.

### BVA Robusto (Robust BVA)
Inclui múltiplos valores inválidos em cada extremo para testar a **robustez e resiliência** do sistema a entradas inesperadas.

## ✅ Processo de Aplicação

### 1. Identificação de Intervalos
- Analisar especificações para encontrar todos os campos com limites definidos.
- Catalogar tipos de dados (inteiros, decimais, datas, strings, etc.).
- Identificar limites implícitos (e.g., tamanho de buffer, capacidade de armazenamento).

### 2. Determinação de Valores Limite
- **Limites explícitos**: Definidos diretamente nas especificações.
- **Limites de sistema**: Máximos/mínimos de tipos de dados (e.g., `MAX_INT`).
- **Limites de domínio**: Regras de negócio específicas.

### 3. Seleção de Valores de Teste
- **Valores válidos**: Nos limites e adjacentes (e.g., `min`, `min+1`, `max−1`, `max`).
- **Valores inválidos**: Fora dos limites (e.g., `min−1`, `max+1`).
- **Valores especiais**: Zero, nulo, vazio, extremos do sistema.

### 4. Design dos Casos de Teste
- Estruturar casos de teste com dados de entrada, procedimentos e resultados esperados.
- Incluir validações para comportamentos de erro (e.g., mensagens de erro esperadas).
- Documentar as justificativas para cada valor escolhido.

### 5. Execução e Validação
- Testar sistematicamente cada valor limite.
- Verificar mensagens de erro apropriadas para entradas inválidas.
- Validar comportamento do sistema para entradas nos limites válidos.

## 📊 Tipos de Limites Comuns

- **Numéricos**: `0`, `1`, `-1`, `MAX_INT`, `MIN_INT`, `0.0`, `0.1`, `-0.1`, `0%`, `100%`, `101%`.
- **Strings**: Vazia, 1 caractere, comprimento máximo permitido, caracteres especiais (espaços, Unicode), padrões (e-mail, telefone).
- **Temporais**: Datas (`01/01/1900`, `31/12/2099`, anos bissextos), horários (`00:00:00`, `23:59:59`), mudanças de fuso.
- **Sistema**: Memória (buffers pequenos/grandes), rede (timeouts, largura de banda), arquivos (tamanhos extremos).

## ✅ Vantagens

- **Eficácia**: Alta detecção de defeitos com número reduzido de testes.
- **Eficiência**: Redução significativa no número de testes, fácil automação e manutenção, alto ROI.
- **Aplicabilidade**: Ideal para campos numéricos com intervalos bem definidos.

## ⚠️ Limitações e Considerações

- **Dependência**: Requer especificações claras e bem definidas.
- **Não aborda**: Lógica interna complexa ou fluxos de estado complexos.
- **Perda de Defeitos**: Pode não identificar defeitos que surgem da combinação de múltiplos parâmetros.
- **Contextos menos apropriados**: Sistemas com lógica qualitativa, múltiplos componentes ou regras não baseadas em limites.

## 💡 Exemplo Prático Detalhado: Campo "Idade" para Sistema de Seguros

**Intervalo válido:** 18 a 65 anos

| Valor | Classificação                 | Objetivo do Teste                            | Resultado Esperado                        |
|-------|-------------------------------|----------------------------------------------|-------------------------------------------|
| 17    | Inválido (abaixo do mínimo)   | Testar rejeição abaixo do limite inferior    | Erro: "Idade mínima é 18 anos"            |
| 18    | Válido (limite inferior)      | Validar aceitação no limite mínimo           | Aceito - processa normalmente             |
| 19    | Válido (acima do mínimo)      | Confirmar aceitação próximo ao limite        | Aceito - processa normalmente             |
| 64    | Válido (abaixo do máximo)     | Confirmar aceitação próximo ao limite        | Aceito - processa normalmente             |
| 65    | Válido (limite superior)      | Validar aceitação no limite máximo           | Aceito - processa normalmente             |
| 66    | Inválido (acima do máximo)    | Testar rejeição acima do limite superior     | Erro: "Idade máxima é 65 anos"            |

**Casos de Teste Adicionais (para robustez):**
- `0`: Testar valor zero.
- `-1`: Testar valor negativo.
- `999`: Testar valor extremamente alto.
- `Null`/`Vazio`: Testar valores ausentes ou nulos.

## 🔗 Integração com Outras Técnicas

- **Equivalence Partitioning (EP)**: Define as partições e a BVA testa seus limites — combinação eficiente.
- **Decision Tables**: Representa limites como condições em regras complexas.
- **Testes Automatizados**: Permite parametrização de limites, execução repetível e integração com CI/CD.

## 🛠️ Ferramentas e Implementação

### Estratégias de Automação
- **Data-driven testing**: Usar dados pré-definidos de valores limite.
- **Geração automática**: Ferramentas que criam testes a partir de limites.
- **Validação automática**: Verificação programática de mensagens de erro e comportamentos.

### Documentação e Rastreabilidade
- **Matriz de cobertura**: Acompanhamento de limites testados.
- **Mapeamento**: Rastreio de requisitos, limites e casos de teste.
- **Relatórios**: Geração de documentação detalhada.

## 📈 Métricas e Avaliação

- **Indicadores de Cobertura**: Percentual de limites identificados/testados, número de defeitos por limite, tempo de execução.
- **Critérios de Sucesso**: Todos os limites testados, comportamentos de erro validados, performance aceitável nos valores limite.

