## 🔹 1. Boundary Value Analysis (Análise de Valores Limite)

### 📘 Definição
Técnica que testa os **valores nos limites** das partições válidas e inválidas, onde os erros ocorrem com mais frequência.

### 🎯 Importância
- Detecta erros nas **fronteiras** dos intervalos de entrada.
- Aumenta a eficácia com poucos testes.

### ✅ Vantagens
- Poucos testes com grande eficácia.
- Ideal para campos numéricos com intervalos definidos.

### ⚠️ Desvantagens
- Exige especificação clara dos limites.
- Não cobre lógica interna ou fluxo de estados.

### 🛠️ Como aplicar
1. Identificar os intervalos válidos de entrada.
2. Determinar os valores mínimos e máximos.
3. Criar testes com:
   - Valor abaixo do mínimo
   - Valor no mínimo
   - Valor logo acima do mínimo
   - Valor logo abaixo do máximo
   - Valor no máximo
   - Valor acima do máximo

### 💡 Exemplo real
Campo “Idade” com intervalo válido: 18 a 65.

| Valor | Objectivo                      |
|-------|--------------------------------|
| 17    | Abaixo do limite inferior (inválido) |
| 18    | Limite inferior (válido)      |
| 19    | Valor logo acima do mínimo    |
| 64    | Valor logo abaixo do máximo   |
| 65    | Limite superior (válido)      |
| 66    | Acima do limite superior (inválido) |
