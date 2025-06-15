# 🔷 1. Equivalence Partitioning (Particionamento por Equivalência)

## Introdução

No universo dos testes de software, um dos maiores desafios é garantir uma cobertura abrangente sem cair na armadilha de testar exaustivamente todas as combinações possíveis – uma tarefa, na maioria das vezes, inviável. É aqui que entra o **Equivalence Partitioning** (Particionamento por Equivalência), uma técnica de design de testes poderosa e inteligente.

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

## 📚 Exemplo Prático: Módulo de Pagamento Online com Cartão de Crédito

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

- **Válido**: Valor ≥ valor da compra (ex: compra = R$100, limite = R$150)
- **Inválido**: Valor < valor da compra (ex: limite = R$50)

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

---

## ✅ Conclusão

O Equivalence Partitioning é uma técnica essencial para qualquer QA que busca eficiência, clareza e eficácia na criação de casos de teste. Seu uso adequado melhora significativamente a qualidade do produto final.
