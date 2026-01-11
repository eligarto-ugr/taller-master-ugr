# Exercise Outcomes Submission Template

**Student/Group Name**: [Elias and Nikolina / DS04]  
**Level Completed**: [master]  
**Date**: [11-01-2026]

---

## 📋 Exercise Summary

### Exercise: [Rewriting History (Rebase and Amend Commits)]
**Status**: ✅ Completed

**What we did**:
En este nivel avanzado, hemos dominado técnicas para mantener un historial de commits limpio y profesional. Primero, utilizamos git commit --amend para corregir y ampliar el último commit sin generar entradas innecesarias en el log. Segundo, realizamos un Rebase Interactivo para limpiar el historial de una funcionalidad, utilizando la operación fixup para integrar correcciones de errores en los commits originales de la "Feature". Finalmente, aplicamos un Rebase de rama para integrar los cambios de la rama master en mi rama de funcionalidad, logrando un historial lineal y evitando los "merge commits" que ensucian el gráfico del repositorio.

**Commands Used**:
```bash
# Parte 1: Amend
git commit --amend -m "Add complete configuration file"

# Parte 2: Rebase Interactivo
git rebase -i HEAD~3 # Usando 'fixup' y 'reword'

# Parte 3: Rebase de rama
git checkout feature/awesome-feature
git rebase master

# Visualización
git log --graph --oneline --all -n 10
```

**Results/Output**:
```
PS C:\Users\elias\taller-master-ugr> git log --graph --oneline --all -n 10
* 9b83fc1 (HEAD -> feature/awesome-feature) Add awesome feature
* 11968b5 (master) Update on master branch
* 0dd9dfb Add feature B
* bfc80b5 Add feature A
* a41fe26 Add complete configuration file
* b5d8eb6 (origin/master) refactor: consolidate master exercises into single comprehensive exercise on history rewriting
* 960a0a6 docs: Add submission instructions to master level
* f0055a0 Update README for master level exercises
```

**Screenshots** (if applicable):
- [Screenshot 1: Description]
- [Screenshot 2: Description]

---

## 🎯 Key Learnings

**Main concepts I learned**:
1. **Inmutabilidad del historial**: Entendí que cualquier operación de reescritura (amend o rebase) no modifica los commits existentes, sino que crea otros nuevos con diferentes SHAs.
2. **Historial Lineal vs. Cronológico**: La diferencia entre usar merge (que conserva el orden temporal y crea nudos) y rebase (que prioriza la limpieza lógica del proyecto).
3. **Regla de Oro de Git**: Nunca reescribir la historia en ramas públicas o compartidas, ya que rompe el flujo de trabajo de los demás colaboradores.

**Skills I improved**:
- **Higiene de Commits**: Capacidad para "limpiar" commits de trabajo en curso antes de una revisión de código.
- **Uso avanzado del editor interactivo**: Gestión de scripts de rebase (pick, fixup, reword).
- **Seguridad en el Push**: Entendimiento del uso de --force-with-lease frente al peligroso --force.

---

## 🚧 Challenges Faced

### Challenge 1: Cambio de SHAs tras el Rebase
**Problem**: Al realizar el rebase de la rama de funcionalidad sobre master, me sorprendió ver que los identificadores (SHAs) de mis commits de "Feature" habían cambiado totalmente, aunque el contenido fuera el mismo.

**Solution**: Comprendí que al "rebasar", Git está aplicando mis cambios sobre una base nueva, lo que técnicamente genera nuevos objetos en la base de datos de Git. Esto me enseñó por qué es peligroso hacerlo en ramas compartidas.


### Challenge 2: Reordenación en el Rebase Interactivo
**Problem**: Durante el ejercicio de fixup, tuve que mover la línea del commit de "typo" justo debajo del commit que quería arreglar en el editor de texto.

**Solution**: Aprendí que el orden de las líneas en el editor interactivo determina el orden final del historial y sobre qué commit se aplica cada fixup.

---

## 💭 Personal Reflection

**What surprised me**:
Lo que más me sorprendió es la capacidad de "mentir" positivamente sobre el historial. Poder condensar 10 commits de pruebas y errores en un solo commit perfecto y bien explicado es fundamental para que el resto del equipo pueda entender el código meses después.

**What I found most difficult**:
Lo más difícil fue asimilar el concepto de que el historial de Git no es algo sagrado o intocable, sino que es una herramienta de comunicación. Al principio da miedo usar rebase -i, pero una vez entiendes que puedes volver atrás con el reflog si algo sale mal, se vuelve una herramienta indispensable.

**What I found most useful**:
Sin duda, el git commit --amend. Es muy común olvidar una línea de código o un comentario justo después de hacer el commit, y esta herramienta evita llenar el historial de mensajes como "oops", "ahora sí" o "arreglando olvido".

**How I would apply this in real projects**:
En un entorno profesional, utilizaría rebase para mantener mi rama de trabajo actualizada con la rama principal (main) diariamente. Antes de enviar un Pull Request, usaría el rebase interactivo para agrupar mis cambios en unidades lógicas y limpias, asegurando que el revisor de código vea una progresión clara y no mi proceso de ensayo y error.

---

## 📊 Self-Assessment

Rate your confidence level for each topic (1-5, where 5 is very confident):

| Topic | Confidence (1-5) | Notes |
|-------|------------------|-------|
| Basic Git commands | [5] | |
| Branching & merging | [5] | |
| Remote operations | [5] | |
| Conflict resolution | [5] | |
| History rewriting | [5] | |
| Git hooks | [2] | |
| Security practices | [2] | |

---

## 🔗 Evidence/Artifacts

**Links to branches/commits**:
- Link to your outcome branch: `https://github.com/eligarto-ugr/taller-master-ugr/tree/group-DS04-outcomes/master`
- Key commits demonstrating your work:
  - 9b83fc1: Commit final tras el rebase sobre master.
  - a41fe26: Commit unificado mediante amend.

**Additional files created** (if any):
- config.txt: Archivo usado para practicar amend.
- featureA.txt y featureB.txt: Archivos usados para practicar rebase -i.

---

## ✅ Completion Checklist

Before submitting, ensure you have:
- [✅] Completed the exercise for your chosen level (including all parts)
- [✅] Documented all commands used with their outputs
- [✅] Described challenges and how you resolved them
- [✅] Provided a thoughtful reflection on your learning
- [✅] Self-assessed your confidence in each topic
- [✅] Pushed your outcome branch to the remote repository
- [✅] Created a Pull Request (if required by your instructor)

---

## 📝 Additional Comments

[Any additional thoughts, questions, or feedback about the exercises]

---

**Submission Date**: [11-01-2026]  
**Ready for Review**: ✅ Yes
