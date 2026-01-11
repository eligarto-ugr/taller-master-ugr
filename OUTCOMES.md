# Exercise Outcomes Submission Template

**Student/Group Name**: [Elias and Nikolina / DS04]  
**Level Completed**: [intermediate]  
**Date**: [11-01-2026]

---

## 📋 Exercise Summary

### Exercise: [Merging, Conflict Resolution and Tagging]
**Status**: ✅ Completed

**What I did**:
He completado el nivel intermedio donde el objetivo principal era gestionar el flujo de trabajo con múltiples ramas y resolver conflictos. Creamos dos ramas independientes (feature/header y feature/footer) que modificaban el mismo archivo (page.html). Durante la integración en la rama intermediate, gestionamos y resolvimos un conflicto de contenido manualmente. Finalmente, aplicamos el uso de etiquetas (tags) anotadas y ligeras para marcar versiones estables del proyecto.

**Commands Used**:
```bash
# Gestión de ramas
git checkout -b feature/header
git checkout -b feature/footer
git merge feature/header
git merge feature/footer

# Resolución de conflictos
git status
git add page.html
git commit -m "Merge footer with resolved conflicts"

# Etiquetas (Tags)
git tag -a v1.0 -m "First stable version"
git tag v1.0-test
git show v1.0
git push origin v1.0
```

**Results/Output**:
```
PS C:\Users\elias\taller-master-ugr> git log --graph --oneline --all
*   c2f3270 (HEAD -> group-DS04-outcomes/intermediate, tag: v1.0-test, tag: v1.0, intermediate) Merge footer con resolución de conflictos de contenido
|\
| * a47915a (feature/footer) Fix page.html encoding to UTF-8 in footer
| * 46d496b Add footer to page
* |   ced1e9c Mantener page.html desde feature/header
|\ \
| * | 0c52ff3 (feature/header) Fix page.html encoding to UTF-8 in header
* | | b737c43 Clean up intermediate before merging
|/ /
* / 8830387 Add header to page
|/
* 994450b (origin/intermediate) refactor: consolidate intermediate exercises into single comprehensive exercise
* a1c17e7 docs: Add submission instructions to intermediate level
* 9f25f7a Update README for intermediate level exercises
| * 8d52f58 (origin/group-DS04-outcomes/newbie, group-DS04-outcomes/newbie) docs: Add newbie level exercise outcomes for Group DS04
| | * cc25294 (origin/feature/my-info, feature/my-info) Add personal information
| |/
| * f437a3f (newbie) Add hello.txt with my name
| * decd60b Add hello.txt with my name
| * 360f4a4 (origin/newbie) refactor: consolidate newbie exercises into single comprehensive exercise
| * 5eedc97 docs: Add submission instructions to newbie level
| * 45e1c31 Update README for newbie level exercises
|/
| * 9602351 (origin/main, origin/HEAD, main) Adding GenAI guidelines
| * 7ad3af4 docs: update main branch files to reflect consolidated exercise structure (1 per level)
| * 4d9131e chore: remove instructor files from repository tracking
| *   adbb307 Merge pull request #9 from miguel-oltra/patch-gitignore-update
| |\
| | * e4709e6 Updated CODEOWNERS file
| | * 2a39a02 chore: add INSTRUCTOR_GUIDE.md to gitignore
| | * 0abdbae chore: add SUMMARY.md to gitignore for instructor files
| |/
| * 88a54ab chore: Add .gitignore to exclude instructor files and sensitive
```

**Screenshots** (if applicable):
- <img width="928" height="957" alt="Captura de pantalla 2026-01-11 112056" src="https://github.com/user-attachments/assets/2e16453f-fc6f-4ec6-b36c-14e7c5e12dbd" />

- <img width="942" height="949" alt="Captura de pantalla 2026-01-11 112125" src="https://github.com/user-attachments/assets/e42098da-2abe-4aaf-9462-f7572654f73a" />

- <img width="935" height="950" alt="Captura de pantalla 2026-01-11 112143" src="https://github.com/user-attachments/assets/2d7b3314-c18d-463e-a810-e6462081f0f0" />

- <img width="931" height="952" alt="Captura de pantalla 2026-01-11 112208" src="https://github.com/user-attachments/assets/6d814f9b-4af7-4158-892e-2e3ffda608e4" />

- <img width="935" height="692" alt="Captura de pantalla 2026-01-11 112236" src="https://github.com/user-attachments/assets/f2d827ee-b29f-4ae6-810f-035de010137e" />

---

## 🎯 Key Learnings

**Main concepts I learned**:
1. **Resolución de conflictos compleja**: Aprendí que los conflictos no solo son de texto, sino que pueden ser de lógica (como el conflicto Modify/Delete).
2. **Importancia de la codificación**: Descubrí que Git puede confundir archivos de texto con binarios si la codificación no es UTF-8 (problema común en Windows/PowerShell).
3. **Etiquetado de versiones**: El uso de etiquetas anotadas para marcar hitos inmutables en el desarrollo del software.

**Skills I improved**:
- Gestión de conflictos manuales y limpieza de ramas.
- Uso de `git tag` para el control de versiones (Releases).
- Depuración de errores de configuración de Git en entornos Windows.

---

## 🚧 Challenges Faced

### Challenge 1: Advertencia de "Binary Files" y codificación
**Problem**: Al intentar fusionar `feature/footer`, Git lanzaba el error: `warning: Cannot merge binary files: page.html`. Esto se debía a que PowerShell creó el archivo en UTF-16, y Git no podía leer el texto para insertar los marcadores de conflicto.

**Solution**: Tuve que abortar el merge, borrar los archivos físicos y recrearlos usando el editor VS Code asegurando la codificación UTF-8.

**Commands/Approach**:
```bash
git merge --abort
rm page.html
# Recrear archivo en VS Code con codificación UTF-8
git add page.html
git commit -m "Fix encoding to UTF-8"
```

---

### Challenge 2: Conflicto Modify/Delete
**Problem**: Durante la limpieza, borré `page.html` en la rama base. Al intentar fusionar `feature/header`, Git detectó que en una rama el archivo no existía y en la otra sí.
**Mensaje de error**: `CONFLICT (modify/delete): page.html deleted in HEAD and modified in feature/header`.

**Solution**: Utilicé `git add page.html` para confirmar que quería mantener la versión de la rama de la funcionalidad.

---

## 💭 Personal Reflection

Este nivel ha sido especialmente útil porque me enfrenté a problemas reales que van más allá de los tutoriales básicos. La resolución de conflictos me ha enseñado que Git es una herramienta de precisión: un pequeño detalle como la codificación de un archivo puede detener un flujo de trabajo. 

Entender los marcadores de conflicto (`<<<<<<< HEAD`, `=======`, `>>>>>>>`) me da la seguridad de que, incluso si el equipo trabaja en las mismas líneas de código, siempre hay una forma segura de integrar el trabajo de todos. Además, el uso de etiquetas (tags) me parece vital para la organización profesional; ahora entiendo que mientras las ramas son para el "día a día", los tags son para los momentos importantes de entrega. En un proyecto real, esto me permitiría volver a una versión estable en segundos si algo falla en producción.

---

## 📊 Self-Assessment

Rate your confidence level for each topic (1-5, where 5 is very confident):

| Topic | Confidence (1-5) | Notes |
|-------|------------------|-------|
| Basic Git commands | [5] | |
| Branching & merging | [5] | |
| Remote operations | [4] | |
| Conflict resolution | [5] | |
| History rewriting | [1] | |
| Git hooks | [1] | |
| Security practices | [1] | |

---

## 🔗 Evidence/Artifacts

**Links to branches/commits**:
- Link to your outcome branch: `https://github.com/eligarto-ugr/taller-master-ugr/tree/group-DS04-outcomes/intermediate`
- Key commits demonstrating your work:
  - Commit hash: "Merge footer with resolved conflicts"
  - Commit hash: "Tag v1.0 stable release"

**Additional files created** (if any):
- File 1: page.html - El archivo central donde se gestionaron los conflictos de header y footer.
- File 2: OUTCOMES.md - Documentación completa de la entrega.

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

Los ejercicios han sido muy claros para asentar las bases. La obligatoriedad de documentar el proceso en este archivo ayuda mucho a memorizar los comandos recién aprendidos.

---

**Submission Date**: [11-01-2026]  
**Ready for Review**: ✅ Yes
