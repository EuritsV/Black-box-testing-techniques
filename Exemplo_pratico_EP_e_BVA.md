# 📚 Exemplo Prático: Módulo de Pagamento Online com Cartão de Crédito

Vamos aplicar o **Equivalence Partitioning (EP)** e o **Boundary Value Analysis (BVA)** a um cenário muito comum: o módulo de pagamento por cartão de crédito em uma compra online.

## Cenário

Um utilizador finalizou suas compras, passou pelo checkout e selecionou "Cartão de Crédito" como método de pagamento. Agora, ele precisa inserir os dados do cartão para concluir a transação.

## Pré-condição

O utilizador já escolheu os produtos, adicionou-os ao carrinho, iniciou o processo de checkout e selecionou a opção de pagamento com cartão de crédito. A tela de inserção dos dados do cartão está visível e pronta para receber as informações.

## Processo de Particionamento e Análise de Valores Limítrofes

### 1. Número do Cartão de Crédito (Ex: 16 dígitos)

- **EP Válido**: 1234567890123456
- **EP Inválidos**:
  - 123456789012345 (15 dígitos)
  - 12345678901234567 (17 dígitos)
  - 1234ABCD90123456
- **BVA**:
  - 15 dígitos: abaixo do mínimo
  - 16 dígitos: no limite
  - 17 dígitos: acima do máximo

### 2. Data de Validade do Cartão (MM/AA)

- **EP Válido**: 12/27
- **EP Inválidos**:
  - 06/23 (passado)
  - 13/26 (mês inválido)
  - 08/2026 (formato incorreto)
  - 07-25 (formato errado)
- **BVA**:
  - Mínimo: 01/26
  - Máximo: 12/25
  - 00/25 (abaixo do mínimo)
  - 13/25 (acima do máximo)
  - 06/25 (mês atual válido)
  - 05/25 (mês anterior, inválido)

### 3. Código CCV / CVC / CVV (3 ou 4 dígitos)

- **EP Válido**: 123
- **EP Inválidos**:
  - 12 (2 dígitos)
  - 12345 (5 dígitos)
  - ABC (caracteres)
- **BVA**:
  - 2 dígitos: abaixo do mínimo
  - 3 dígitos: no limite
  - 4 dígitos: acima do máximo

### 4. Nome do Titular

- **EP Válido**: João Silva, Maria Lúcia D'Ávila
- **EP Inválidos**:
  - Nome vazio
  - 12345 (apenas números)
- **BVA** (limite = 50):
  - 0, 1, 50, 51 caracteres

### 5. Valor Disponível no Cartão

- **EP Válido**: €150 (compra = €100)
- **EP Inválido**: €50
- **BVA**:
  - €99.99 (falha)
  - €100.00 (sucesso)
  - €100.01 (sucesso)

## Casos de Teste

- **CT1**: EP válido, saldo €150 → Aprovado
- **CT2**: Mês 13 → "Mês inválido"
- **CT3**: Saldo €50 → "Saldo insuficiente"
- **CT4**: Saldo €99.99 → "Transação negada"
- **CT5**: Saldo €100.00 → Aprovado
- **CT6**: Saldo €100.01 → Aprovado

---

# 📚 Exemplo Prático: Módulo de Levantamento de Dinheiro em Caixa Multibanco

## Cenário

O utilizador quer levantar dinheiro num caixa com regras de valores mínimo/máximo e limite diário.

## Pré-condição

Cartão inserido, PIN digitado, opção "Levantamento" selecionada.

## Regras de Negócio

- Mínimo: €10
- Máximo: €200
- Diário: €400 (máx. 2x €200)

## Particionamento e BVA

### 1. Valor por Operação

- **EP Válido**: €50, €120
- **EP Inválidos**:
  - €5, €0 (abaixo)
  - €250 (acima)
  - €13 (valor inválido)
- **BVA**:
  - €9 (abaixo do mínimo)
  - €10 (mínimo)
  - €200 (máximo)
  - €201 (acima do máximo)

### 2. Acumulação Diária

- **EP Válido**: 2x €200 = €400
- **EP Inválidos**:
  - Tentativa após €400
  - Mais de 2 operações de €200
- **BVA**:
  - 1º: €200
  - 2º: €200 → total €400
  - 3º: €10 → rejeitado
  - 1º: €199, 2º: €200 → total €399, 3º: €2 → rejeitado
  - 1º tentativa: €401 → rejeitado

## Casos de Teste

- **CT1**: €50 → Aprovado
- **CT2**: €10 (mínimo) → Aprovado
- **CT3**: €200 (máximo) → Aprovado
- **CT4**: €9 → "Valor mínimo é €10"
- **CT5**: €201 → "Valor máximo é €200"
- **CT6**: Após €200, novo €200 → Aprovado
- **CT7**: Após 2x €200, novo €10 → "Limite diário atingido"

## Benefícios da Combinação EP + BVA

Cobertura de cenários típicos e de limites críticos, com foco em identificar erros lógicos comuns, como off-by-one e validações de regras de negócio.

