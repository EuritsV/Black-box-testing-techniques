## 🔸 2. Decision Table (Tabela de Decisão)

### 📘 Definição
Técnica utilizada para testar **múltiplas condições e combinações possíveis**, com base em regras de negócio.

### 🎯 Importância
- Garante cobertura sistemática de regras de decisão.
- Ajuda a visualizar e estruturar decisões complexas.

### ✅ Vantagens
- Testes sistemáticos e completos.
- Boa clareza em sistemas com regras lógicas.

### ⚠️ Desvantagens
- Pode tornar-se complexa com muitas condições.
- Requer selecção e organização cuidadosa das combinações.

### 🛠️ Como aplicar
1. Identificar as condições de entrada.
2. Listar as acções possíveis.
3. Criar uma tabela com todas as combinações relevantes.
4. Definir o resultado esperado para cada combinação.
5. Criar casos de teste com base nas linhas da tabela.

### 💡 Exemplo real
Sistema de reservas – Cancelamento de reserva:

| Tem Subscrição | Mais de 24h para reserva? | Penalização? | Acção esperada                 |
|----------------|---------------------------|---------------|--------------------------------|
| Sim            | Sim                       | Não           | Cancelamento sem penalização   |
| Sim            | Não                       | Sim           | Cancelamento com penalização   |
| Não            | Sim                       | Sim           | Cancelamento com penalização   |
| Não            | Não                       | Sim           | Cancelamento com penalização   |
