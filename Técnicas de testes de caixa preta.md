# Mini-Treinamento: Técnicas de Testes de Caixa Preta

## Objetivo

Este mini-treinamento tem como objetivo **demonstrar e aplicar duas técnicas de testes de caixa preta** — *Equivalence Partitioning* e *Boundary Value Analysis* — utilizando como base um **sistema fictício de caixa multibanco (ATM)**.

---

# Dia 1 – Equivalence Partitioning (Particionamento por Equivalência)

## O que é?

**Equivalence Partitioning** é uma técnica de design de testes onde o conjunto de dados de entrada (ou saída) é dividido em partições válidas e inválidas que se comportam da mesma forma. O objetivo é reduzir a quantidade de testes mantendo uma boa cobertura.

Cada partição representa um conjunto de dados que o sistema deve tratar da mesma forma — testar um valor de cada partição é suficiente para representar o comportamento de todos os outros da mesma partição.

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

