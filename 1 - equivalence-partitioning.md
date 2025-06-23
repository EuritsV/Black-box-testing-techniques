# 🔷 1. Equivalence Partitioning (Particionamento por Equivalência)

## O que é?

É uma técnica que divide o conjunto de dados de entrada (ou, em alguns casos, de saída) em grupos, ou "partições", de forma que todos os valores dentro de uma mesma partição sejam tratados de maneira idêntica pelo sistema.

### Objetivo Principal

Reduzir drasticamente o número de casos de teste necessários, enquanto se mantém uma cobertura funcional robusta e eficaz. Em vez de testar cada valor individualmente, testamos apenas um representante de cada partição, assumindo que os demais se comportarão da mesma forma.

## Por Que o Equivalence Partitioning é Essencial?

Esta técnica resolve o problema da explosão combinatória nos testes. Sem ela, testar todas as entradas possíveis para um sistema seria inviável. Ela permite selecionar um conjunto representativo de dados de teste, garantindo a validação dos comportamentos críticos do sistema com eficiência.

## Princípio Fundamental

Imagine uma caixa cheia de frutas: se uma maçã Granny Smith está madura e doce, as outras da mesma safra provavelmente também estarão.  
Aplicado ao software: se um valor dentro de uma partição é processado corretamente, os outros também serão. Assim, testamos apenas um valor **representativo** por partição.

---

## 🎯 Características Principais

- **Eficiência**: Reduz o número de testes mantendo cobertura adequada.
- **Exclusividade**: As partições são mutuamente exclusivas.
- **Uniformidade**: Cada partição representa um comportamento consistente.
- **Representatividade**: Um valor representa toda a partição.

---

## 📊 Tipos de Partições Cruciais

### Por Validade

- **Válidas**: Dados que o sistema deve aceitar.
- **Inválidas**: Dados que o sistema deve rejeitar.

### Outras Classificações

- **Contínuas**: Intervalos com valores decimais (ex: idade entre 18-65).
- **Discretas**: Valores específicos ou inteiros (ex: quantidade de itens).
- **Ordenadas**: Sequência lógica (ex: notas de 0 a 20).
- **Não Ordenadas**: Lista sem ordem (ex: tipo de conta).
- **Finitas**: Número limitado de valores (ex: cores disponíveis).
- **Infinitas**: Teoricamente ilimitadas (ex: números inteiros).

---

## ⚙️ Processo de Aplicação

1. **Identificação dos Parâmetros**  
   Liste os campos de entrada, configuração e saída relevantes.

2. **Análise de Especificações**  
   Revise requisitos e regras de negócio. Identifique validações e restrições.

3. **Definição de Partições**  
   Crie partições válidas e inválidas com base nas regras. Evite lacunas e sobreposições.

4. **Seleção de Valores Representativos**  
   Escolha valores típicos (válidos) e violadores claros (inválidos).

5. **Design dos Casos de Teste**  
   Crie casos com entradas, passos e resultados esperados.

6. **Execução e Documentação**  
   Execute testes sistematicamente e registre resultados e defeitos.

7. **Avaliação de Cobertura**  
   Verifique se todas as partições foram testadas. Calcule a cobertura e identifique lacunas.

---

## 📈 Quando Utilizar

### Cenários Ideais

- Formulários com múltiplas validações
- APIs com muitos parâmetros
- Sistemas com regras de negócio claras
- Interfaces com múltiplas opções de configuração

### Contextos Apropriados

- Especificações claras e bem documentadas
- Recursos de teste limitados
- Busca por alta cobertura funcional com poucos casos

---

## ✅ Vantagens

- **Simplicidade**: Fácil de entender e aplicar.
- **Eficiência**: Reduz o número de testes.
- **Foco funcional**: Testa o comportamento real do sistema.
- **Automação**: Base sólida para testes automatizados.
- **Cobertura**: Garante validação de comportamentos principais.
- **Manutenibilidade**: Facilita atualizações com mudanças nos requisitos.

---

## ⚠️ Limitações e Considerações

- **Valores de Fronteira**: Não cobre limites — use Boundary Value Analysis.
- **Dependência de Especificações**: Requer documentação clara.
- **Interações Complexas**: Pode não cobrir combinações entre partições.
- **Casos Edge**: Pode deixar escapar cenários atípicos.

### Técnicas Complementares

- **Boundary Value Analysis**
- **Pairwise Testing**
- **Error Guessing**

---

## 🔧 Boas Práticas

### Durante o Design

- Revise partições com stakeholders e devs.
- Documente os critérios usados.
- Valide a completude das partições.
- Use cenários reais do mundo real.

### Durante a Execução

- Mantenha rastreabilidade entre partições e testes.
- Registre defeitos com vínculo à partição.
- Atualize testes conforme mudanças nos requisitos.

---

## 🔗 Integração com Outras Técnicas

- **Boundary Value Analysis**: Testa os limites das partições.
- **Decision Table Testing**: Útil para múltiplas condições.
- **State Transition Testing**: Para sistemas baseados em estados.
- **Use Case Testing**: Para validar fluxos completos do utilizador.

---

## 📝 Resumo

O **Equivalence Partitioning** é essencial para otimizar testes, reduzir esforço e garantir cobertura funcional significativa. Combinado com outras técnicas, ele ajuda a construir testes robustos e inteligentes.

---

## 📚 Exemplo Prático 1 : Módulo de Pagamento Online com Cartão de Crédito

### Cenário

O utilizador selecionou "Cartão de Crédito" como método de pagamento. A tela de inserção de dados está visível.

### 1. Número do Cartão de Crédito

- **Válido**: 16 dígitos (ex: `1234567890123456`)
- **Inválidos**:
  - Menos de 16 dígitos (`123456789012345`)
  - Mais de 16 dígitos (`12345678901234567`)
  - Caracteres não numéricos (`1234ABCD90123456`)
  - Falha no algoritmo Luhn (se aplicável)

### 2. Data de Validade

- **Válida**: Data futura, formato `MM/AA` (ex: `12/27`)
- **Inválidos**:
  - Data no passado (`06/23`)
  - Mês inválido (`13/26`)
  - Ano no formato errado (`08/2026`)
  - Formato incorreto (`07-25`)

### 3. Código CCV / CVC / CVV

- **Válido**: 3 ou 4 dígitos (ex: `123`)
- **Inválidos**:
  - Menos dígitos (`12`)
  - Mais dígitos (`12345`)
  - Letras ou símbolos (`ABC`)

### 4. Nome do Titular

- **Válido**: Nome com letras, espaços, acentos (ex: `Maria Lúcia D'Ávila`)
- **Inválidos**:
  - Nome vazio
  - Apenas números ou símbolos (`12345`)
  - Nome muito longo

### 5. Valor Disponível no Cartão

- **Válido**: Valor ≥ valor da compra (ex: compra = €100, limite = €150)
- **Inválido**: Valor < valor da compra (ex: limite = €50

---

## 🧪 Casos de Teste (Exemplos)

### CT1: Pagamento Válido

- **Entrada**: Dados válidos em todos os campos
- **Resultado Esperado**: Transação aprovada

### CT2: Número do Cartão Inválido

- **Entrada**: Cartão com 15 dígitos
- **Resultado Esperado**: Erro: "Número do cartão inválido"

### CT3: Data de Validade Inválida

- **Entrada**: Data no passado
- **Resultado Esperado**: Erro: "Data de validade expirada"

### CT4: Saldo Insuficiente

- **Entrada**: Dados válidos, saldo insuficiente
- **Resultado Esperado**: Erro: "Transação negada"

# 📚 Exemplo Prático 2 : Módulo de Levantamento de Dinheiro em Caixa Multibanco

Vamos aplicar o **Equivalence Partitioning** a um cenário de levantamento de dinheiro em um caixa multibanco.

---

## 🖼️ Cenário

Um utilizador deseja levantar dinheiro num caixa multibanco, que possui regras específicas sobre os valores mínimo, máximo e o número de operações diárias.

### ✅ Pré-condição

- O utilizador inseriu o cartão no caixa multibanco.
- Digitou o código PIN.
- Selecionou a opção de **"Levantamento"**.
- Agora, precisa inserir o montante que deseja levantar.

---

## 📋 Regras de Negócio Relevantes

- **Levantamento Mínimo**: €10 por operação  
- **Levantamento Máximo por Operação**: €200  
- **Levantamento Máximo Diário**: €400  
- **Limitação adicional**: O valor de €400 diários pode ser atingido com um máximo de **duas operações de €200**.  
  (Ou seja, não se pode levantar €400 de uma só vez, e se levantar €200 uma vez, só pode levantar mais €200 outra vez no mesmo dia)

---

## ⚙️ Processo de Particionamento por Equivalência

### 1. Valor Solicitado para Levantamento

#### ✅ Partição Válida

Valores entre **€10 e €200**, inclusivamente, que respeitam os múltiplos de notas disponíveis.

**Exemplos para teste**:  
- €10  
- €50  
- €120  
- €200  

#### ❌ Partições Inválidas

- Valor inferior a €10  
  - Ex: €5, €0  
- Valor superior a €400 (por operação)  
  - Ex: €1000
- Valor que não é múltiplo das notas disponíveis (ex: se só houver notas de €10 e €20)  
  - Ex: €13, €25

---

### 2. Acumulação Diária de Levantamentos

#### ✅ Partição Válida

- **Primeira operação do dia**: qualquer valor entre €10 e €200  
- **Segunda operação do dia**: valor que, somado ao levantamento anterior, **não exceda €400** e **seja ≤ €200**  
  - Ex: Se já levantou €200, novo levantamento de €200 é válido (atinge os €400 permitidos)

#### ❌ Partições Inválidas

- Tentativa de levantamento **após atingir o limite diário de €400**  
  - Ex: Após levantar €200 + €200, qualquer nova tentativa
- Tentativa de terceira operação **independentemente do valor**, caso a regra limite a 2 operações máximas  
  - Ex: Levantar €100 + €200, depois tentar mais €100 (total €400, mas terceira operação)

> ⚠️ A interpretação da regra pode variar:
> - Se for **"máximo de 2 levantamentos de €200"**, aplica-se a limitação por operação.
> - Se for **"até €400 no total"**, desde que por operações de até €200, aceita-se outras combinações.

---

## 🧪 Casos de Teste (Exemplos)

### CT1: Levantamento Válido (Primeira Operação)

- **Entrada**: Valor solicitado = €50  
- **Resultado Esperado**: Transação aprovada, dinheiro dispensado, limite diário atualizado (€350 restantes)

---

### CT2: Levantamento Válido (Máximo por Operação)

- **Entrada**: Valor solicitado = €200  
- **Resultado Esperado**: Transação aprovada, dinheiro dispensado, limite diário atualizado (€200 restantes)

---

### CT3: Levantamento Inválido (Abaixo do Mínimo)

- **Entrada**: Valor solicitado = €5  
- **Resultado Esperado**: Mensagem de erro: "Valor mínimo de levantamento é €10", transação não aprovada

---

### CT4: Levantamento Inválido (Acima do Máximo por Operação)

- **Entrada**: Valor solicitado = €250  
- **Resultado Esperado**: Mensagem de erro: "Valor máximo por operação é €200", transação não aprovada

---

### CT5: Levantamento Inválido (Excedendo Limite Diário – Segunda Operação)

- **Pré-condição**: Utilizador já levantou €200 no dia  
- **Entrada**: Novo valor solicitado = €250  
- **Resultado Esperado**: Mensagem de erro: "Excedeu o limite diário de levantamento", transação não aprovada

---

### CT6: Levantamento Inválido (Tentativa de Terceira Operação)

- **Pré-condição**: Utilizador já levantou €200 + €200 (duas operações)  
- **Entrada**: Novo valor solicitado = €10  
- **Resultado Esperado**: Mensagem de erro: "Limite diário de levantamento atingido", transação não aprovada

---

## ✅ Conclusão

Este exemplo mostra como o **Equivalence Partitioning** pode ser aplicado não apenas a valores de entrada, mas também a **regras de negócio dependentes do estado do sistema** (como o limite diário de levantamentos).  

Ao identificar partições válidas e inválidas com base nas regras, conseguimos garantir que o sistema:

- **Aceite apenas operações permitidas**
- **Rejeite solicitações que violam limites**
- **Ofereça segurança e consistência ao utilizador final**

---

## ✅ 

O Equivalence Partitioning é uma técnica essencial para qualquer QA que busca eficiência, clareza e eficácia na criação de casos de teste. Seu uso adequado melhora significativamente a qualidade do produto final.
