## 🔷 3. State Transition (Transição de Estado)

### 📘 Definição
Técnica que testa o comportamento do sistema com base em **diferentes estados e eventos**, simulando **fluxos e sequências**.

### 🎯 Importância
- Ideal para validar **fluxos de trabalho, autenticação, formulários em etapas**.
- Detecta falhas quando o sistema depende de estados anteriores.

### ✅ Vantagens
- Garante cobertura de todas as transições válidas.
- Detecta comportamentos inesperados em sequências.

### ⚠️ Desvantagens
- Pode ser complexa de modelar.
- Necessita um mapeamento preciso dos estados e eventos.

### 🛠️ Como aplicar
1. Identificar os estados possíveis do sistema.
2. Listar os eventos que causam mudanças de estado.
3. Desenhar um **diagrama de transição** ou uma **tabela de estados**.
4. Criar casos de teste que validem sequências válidas e inválidas.

### 💡 Exemplo real
Sistema com tentativa de login via PIN:

**Estados:**
- S1: Início
- S2: 1ª tentativa
- S3: 2ª tentativa
- S4: 3ª tentativa
- S5: Acesso concedido
- S6: Conta bloqueada

**Transições de exemplo:**
- S1 → S2 → S3 → S4 → S6 (3 tentativas erradas → bloqueio)
- S1 → S2 → S5 (acesso correcto na 1ª tentativa)

---

## 📌 Quando utilizar cada técnica?

| Técnica                  | Usar quando...                                      |
|--------------------------|-----------------------------------------------------|
| Boundary Value Analysis  | Há limites numéricos ou intervalos a serem testados |
| Decision Table           | Há múltiplas regras de negócio e combinações lógicas|
| State Transition         | O sistema depende de **estados anteriores** ou tem **fluxos sequenciais** |
