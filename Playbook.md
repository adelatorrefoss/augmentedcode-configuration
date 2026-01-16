## 🎯 Playbook profesional: **Think → Design → Execute → Accelerate**

### Herramientas

* **Claude Code** → pensar y entender sistemas
* **JetBrains Junie** → cambiar código real con seguridad
* **OpenAI Codex** → acelerar escritura de código

---

## FASE 1 — **THINK (entender, no tocar)** → Claude Code

**Objetivo:** construir el modelo mental correcto.

Úsalo cuando:

* Entras en **código legacy**
* No entiendes el *por qué* del diseño
* Detectas deuda técnica difusa
* Necesitas contexto global

Qué pedirle:

* “Explícame este módulo como si fuera nuevo en el equipo.”
* “Qué responsabilidades están mezcladas.”
* “Qué decisiones históricas parecen haber llevado a esto.”
* “Qué smells conceptuales ves.”

**Entregable:**

* Narrativa del sistema
* Hipótesis de intención
* Mapa de responsabilidades

🚫 **Nunca** usar Codex o Junie aquí.

---

## FASE 2 — **DESIGN (decidir qué hacer)** → Claude Code

**Objetivo:** elegir bien antes de tocar nada.

Úsalo para:

* Rediseño de módulos
* Definir límites y contratos
* Evaluar alternativas

Qué pedirle:

* “Propón 2–3 rediseños con pros y contras.”
* “Qué cambiarías ahora y qué pospondrías.”
* “Qué riesgos técnicos hay.”

**Entregable:**

* Decisiones explícitas
* Plan de cambio incremental

🚫 No pedir todavía implementación.

---

## FASE 3 — **EXECUTE (cambiar código real)** → JetBrains Junie

**Objetivo:** aplicar el plan **sin romper el sistema**.

Úsalo cuando:

* Hay cambios estructurales
* Movimientos de clases/paquetes
* Cambios de firmas, tipos, visibilidad
* Actualización de tests

Qué pedirle:

* “Aplica el paso 1 del plan.”
* “Extrae este componente respetando contratos.”
* “Actualiza llamadas afectadas.”

**Ventaja clave:** opera sobre **AST + tipos reales**.

🚫 No usar Claude ni Codex para refactors grandes.

---

## FASE 4 — **ACCELERATE (escribir rápido)** → Codex

**Objetivo:** velocidad y productividad local.

Úsalo cuando:

* El diseño ya está decidido
* El cambio es local y pequeño
* Quieres escribir sin pensar demasiado

Ejemplos:

* Helpers
* Mappers
* DTOs
* Tests repetitivos
* Boilerplate

Qué pedirle:

* “Genera este mapper.”
* “Escribe tests para este caso.”
* “Completa esta función.”

🚫 No usar Codex para:

* Diseño
* Refactors globales
* Cambios conceptuales

---

## FASE 5 — **VALIDATE (feedback loop)**

* Compilar
* Tests
* Revisar diff

Si falla:

* Error conceptual → vuelve a **Claude**
* Error estructural → corrige con **Junie**
* Código repetitivo → acelera con **Codex**

---

## 🧭 Regla de oro (con Codex incluido)

> **Pensar → Claude
> Decidir → Claude
> Cambiar → Junie
> Escribir → Codex**

---

## Tabla de decisión instantánea

| Situación              | Herramienta |
| ---------------------- | ----------- |
| No entiendo el sistema | Claude      |
| Qué diseño elegir      | Claude      |
| Rediseñar módulo       | Claude      |
| Refactor seguro        | Junie       |
| Mover clases           | Junie       |
| Generar código rápido  | Codex       |
| Tests repetitivos      | Codex       |
| Boilerplate            | Codex       |

---

## Errores comunes (muy importantes)

❌ Codex para diseño → código rápido, sistema malo
❌ Claude para refactor grande → buen texto, código frágil
❌ Junie sin plan → refactor correcto, arquitectura peor

---

## Frase final

> **Claude piensa.
> Junie cambia.
> Codex acelera.**

Si quieres, el siguiente paso lógico sería:

* Convertir esto en un **CODEX.md / JUNIE.md / CLAUDE.md** operativo
* O adaptarlo exactamente a **Kotlin + Spring + tests + Terraform**.
