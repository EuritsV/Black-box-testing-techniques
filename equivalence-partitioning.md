## 🔷 1. Equivalence Partitioning (Particionamento por Equivalência)

## Objetivo

Este mini-treinamento tem como objetivo descrever as tecnicas de testes de caixa preta e **demonstrar e aplicar duas técnicas de testes de caixa preta** — *Equivalence Partitioning* e *Boundary Value Analysis* — utilizando como base um **sistema fictício de caixa multibanco (ATM)**.

---

# Dia 1 – Equivalence Partitioning (Particionamento por Equivalência)

## O que é?

**Equivalence Partitioning** é uma técnica de design de testes onde o conjunto de dados de entrada (ou saída) é dividido em partições válidas e inválidas que se comportam da mesma forma. O objetivo é reduzir a quantidade de testes mantendo uma boa cobertura.

Cada partição representa um conjunto de dados que o sistema deve tratar da mesma forma — testar um valor de cada partição é suficiente para representar o comportamento de todos os outros da mesma partição.

**Carateristicas principais em resumo: 
- Reduz casos de testes mantendo uma cobertura completa
- Se um valor numa partição funciona, outros na mesma partição deverão funcionar de forma semelhante
- As partições não devem sobrepor-se nem estar vazias

---
## Existem vários tipos de partiçoes
- Com base no tipo de dados:
      - Continuas: Valores que podem incluir qualquer ponto num intervalo (incluindo decimais)
      - Discretas: valores que só podem conter pontos especificos

- Com base na organização:
     - Ordenadas: Valores que seguem uma sequencia lógica ou hierarquica
     - Não ordenadas: Valores sem sequencia natural
       
- Com base nos limites:
     - Finitas: Conjunto limitado de valores possíveis
     - Infinitas: Valores teoricamente ilimitados
       
- Com base na validade:
     - Válidas: Valores de entrada que o sistema deve aceitar
     - Inválidas: Valores de entrada que o sistema deve rejeitar

---
##Processo de Aplicação
- Identificar Parâmetros de Entrada: Determinar todos os campos e parâmetros de entrada no sistema
- Analisar Especificações: Rever os requisitos para compreender o comportamento esperado
- Definir Partições: Dividir o domínio de entrada de cada parâmetro em partições válidas e inválidas
- Selecionar Valores de Teste: Escolher um valor representativo de cada partição
- Desenhar Casos de Teste: Criar testes utilizando estes valores representativos
- Executar Testes: Executar os testes e documentar os resultados
- Avaliar Cobertura: Calcular quantas partições foram testadas

---

## Aplicação prática: Sistema de Caixa Multibanco

### Cenário fictício: **Levantamento de dinheiro**

O caixa multibanco permite que o utilizador levante valores entre **10 e 1000 unidades monetárias**, em múltiplos de 10.

### Regras de negócio:

- Valor mínimo para levantamento: **10**
- Valor máximo para levantamento: **1000**
- Apenas são aceites valores múltiplos de **10**
- A conta tem de ter saldo suficiente

---

## Definição das Partições

### Partições Válidas:
1. Valores entre 10 e 1000, múltiplos de 10  
   - Exemplo: `10`, `100`, `990`, `1000`

### Partições Inválidas:
2. Valores inferiores a 10  
   - Exemplo: `0`, `5`, `9`
3. Valores superiores a 1000  
   - Exemplo: `1001`, `1500`
4. Valores dentro do intervalo permitido, mas **não múltiplos de 10**  
   - Exemplo: `15`, `123`, `999`

---

## Casos de Teste Baseados nas Partições

| ID | Valor do Levantamento | Partição        | Resultado Esperado             |
|----|------------------------|------------------|-------------------------------|
| 01 | 100                    | Válida           | Levantamento autorizado       |
| 02 | 5                      | Inválida (inferior ao mínimo) | Erro: valor inválido |
| 03 | 1200                   | Inválida (superior ao máximo) | Erro: valor inválido |
| 04 | 55                     | Inválida (não múltiplo de 10) | Erro: valor inválido |

---

## Observações

- Neste cenário, cobrimos **todas as partições possíveis** de entrada para a funcionalidade de levantamento.
- Cada partição foi representada por **um valor típico**, sem precisar testar todos os valores possíveis.

---

## Reflexão

- **Facilidade de aplicação:** O Particionamento por Equivalência revelou-se útil para reduzir o número de testes necessários.
- **Limitação identificada:** A técnica não testa os valores nos limites exatos do intervalo — isso será abordado com a técnica *Boundary Value Analysis*.
- **Próximo passo:** Aplicar **Boundary Value Analysis** amanhã, no mesmo cenário, para verificar os limites inferior e superior do intervalo permitido.

---

*Data de início:* 05/05/2025  
*Autora:* Eurits

# Dia 2 – Análise de Valores Limite (Boundary Value Analysis - BVA)

## 🧠 Objetivo

Este mini-treinamento tem como objetivo explorar a técnica **Boundary Value Analysis (Análise de Valores Limite - AVLim)** utilizada em testes de software para identificar erros nos limites dos domínios de entrada.

---

## 📘 Conceitos-Chave

### O que é a Análise de Valores Limite?

A Análise de Valores Limite (AVLim) é uma técnica de teste baseada no princípio de que **erros ocorrem com mais frequência nos limites dos intervalos válidos de entrada** do que no centro. 

### Benefícios:

✅ Mais eficiência nos testes  
✅ Detecção de falhas críticas em condições de fronteira  
✅ Aumento da robustez e fiabilidade do software

---

## 🎯 Tipos de valores a testar

- 🔹 **Valor limite mínimo**
- 🔹 **Valor limite máximo**
- 🔹 **Valor imediatamente abaixo do mínimo**
- 🔹 **Valor imediatamente acima do mínimo**
- 🔹 **Valor imediatamente abaixo do máximo**
- 🔹 **Valor imediatamente acima do máximo**

---

## 🧪 Exemplo prático

> Um módulo de gravação aceita **números entre 10 e 500 (inclusive)**.

### 🧩 Partições de equivalência:

- ❌ Inválido: x < 10
- ✅ Válido: 10 ≤ x ≤ 500
- ❌ Inválido: x > 500

---

## 🧰 Métodos de Análise

### ✔️ Método de 2 Valores

Foca-se apenas nos valores **fora e nos limites**.

**Casos de Teste**:  
- Inferior: `9` (fora), `10` (limite inferior)  
- Superior: `500` (limite superior), `501` (fora)

```text
Testar: 9, 10, 500, 501

