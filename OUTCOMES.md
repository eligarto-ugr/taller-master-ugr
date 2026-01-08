# Exercise Outcomes Submission Template

**Student/Group Name**: Elias/DS04  
**Level Completed**: [newbie]  
**Date**: [08-01-2026]

---

## 📋 Exercise Summary

### Exercise: [Newbie]
**Status**: ✅ Completed

**What I did**:
[En este nivel he aprendido los fundamentos de Git: configuración inicial, el flujo de trabajo básico (add/commit), la gestión de ramas locales y la sincronización con repositorios remotos en GitHub.]

**Commands Used**:
```bash
git config --global user.name "[Elias]"
git config --global user.email "[e.eligarto@go.ugr.es]"
git clone git@github.com: eligarto-ugr/taller-master-ugr.git
git status
git add hello.txt
git commit -m "Add hello.txt with my name"
git log
```

**Results/Output**:
```
$ git status
On branch newbie
Your branch is ahead of 'origin/newbie' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

```
elias@PC_de_Elias MINGW64 ~/taller-master-ugr (newbie)
$ git commit -m "Add hello.txt with my name"
[newbie f437a3f] Add hello.txt with my name
 1 file changed, 1 insertion(+), 1 deletion(-)

elias@PC_de_Elias MINGW64 ~/taller-master-ugr (newbie)
$ git log
commit f437a3f1f30c06faedaf8f922c9c1ab40c6af38f (HEAD -> newbie)
Author: Elias <e.eligarto@go.ugr.es>
Date:   Thu Jan 8 19:23:19 2026 +0100

    Add hello.txt with my name

commit decd60b944976dc07908d477e8791e83d4353518
Author: Elias <e.eligarto@go.ugr.es>
Date:   Thu Jan 8 19:21:45 2026 +0100

    Add hello.txt with my name

commit 360f4a4bc62dce8a00a239d4f5b32b94336fb072 (origin/newbie)
Author: Miguel Angel Oltra <miguel.oltra@se.com>
Date:   Mon Dec 22 09:41:22 2025 +0100

    refactor: consolidate newbie exercises into single comprehensive exercise

commit 5eedc97b386a1ed53906add09886cae3f46924ae
Author: Miguel Angel Oltra <SESA219665@se.com>
Date:   Sat Nov 29 12:08:59 2025 +0100

    docs: Add submission instructions to newbie level

commit 45e1c318443a778075a76f732824589fd922a845
Author: Miguel Angel Oltra <SESA219665@se.com>
Date:   Sat Nov 29 11:53:59 2025 +0100

    Update README for newbie level exercises
:...skipping...
commit f437a3f1f30c06faedaf8f922c9c1ab40c6af38f (HEAD -> newbie)
Author: Elias <e.eligarto@go.ugr.es>
Date:   Thu Jan 8 19:23:19 2026 +0100

    Add hello.txt with my name

commit decd60b944976dc07908d477e8791e83d4353518
Author: Elias <e.eligarto@go.ugr.es>
Date:   Thu Jan 8 19:21:45 2026 +0100

    Add hello.txt with my name

commit 360f4a4bc62dce8a00a239d4f5b32b94336fb072 (origin/newbie)
Author: Miguel Angel Oltra <miguel.oltra@se.com>
Date:   Mon Dec 22 09:41:22 2025 +0100

    refactor: consolidate newbie exercises into single comprehensive exercise

commit 5eedc97b386a1ed53906add09886cae3f46924ae
Author: Miguel Angel Oltra <SESA219665@se.com>
Date:   Sat Nov 29 12:08:59 2025 +0100

    docs: Add submission instructions to newbie level

commit 45e1c318443a778075a76f732824589fd922a845
Author: Miguel Angel Oltra <SESA219665@se.com>
Date:   Sat Nov 29 11:53:59 2025 +0100

    Update README for newbie level exercises

commit dc582031fed7a252a3c583fe16f497dbc9dcedd1
Author: Miguel Angel Oltra <SESA219665@se.com>
Date:   Sat Oct 25 12:14:28 2025 +0200

    Revert "Update README.md"

    This reverts commit e2db1ca85b4c8eca7b31d883744bd3a6f5e444b3.

commit e2db1ca85b4c8eca7b31d883744bd3a6f5e444b3 (tag: v0.0.1)
Author: Miguel A. Oltra <39242642+miguel-oltra@users.noreply.github.com>
```

**Screenshots** (if applicable):
- ![alt text](<Captura de pantalla 2026-01-08 192552.png>)
- ![alt text](<Captura de pantalla 2026-01-08 192616.png>)
- ![alt text](<Captura de pantalla 2026-01-08 192631.png>)
- ![alt text](<Captura de pantalla 2026-01-08 192925.png>)

---

## 🎯 Key Learnings

**Main concepts I learned**:
1. **La arquitectura de tres áreas**: Entender la diferencia entre el Directorio de Trabajo (Working Directory), el Área de Preparación (Staging Area) y el Repositorio Local.
2. **Desarrollo aislado**: Cómo utilizar ramas para trabajar en nuevas funcionalidades (`feature/my-info`) sin afectar el código estable de la rama principal.
3. **Sincronización remota**: El flujo de trabajo para subir cambios locales a un servidor remoto (GitHub) y descargar actualizaciones para mantener el entorno local al día.

**Skills I improved**:
- **Uso de la Terminal (CLI)**: Mayor fluidez al gestionar el control de versiones mediante comandos en lugar de una interfaz gráfica.
- **Rastreo del historial**: Interpretación de `git log` para seguir el rastro de los cambios y entender la evolución del proyecto.
- **Gestión de identidad en Git**: Configuración correcta de los ajustes globales de usuario y autenticación mediante llaves SSH.

---

## 🚧 Challenges Faced

### Challenge 1: Autenticación SSH
**Problema**: Al intentar clonar el repositorio por primera vez, recibí un error de "Permission denied (publickey)".

**Solución**: Me di cuenta de que no había añadido mi llave pública SSH a la configuración de mi cuenta de GitHub o no la había generado aún en este equipo.

**Comandos/Enfoque**:
```
ssh-keygen -t ed25519 -C "e.eligarto@go.ugr.es"
# Luego copié el contenido de ~/.ssh/id_ed25519.pub en GitHub Settings -> SSH and GPG keys
ssh -T git@github.com # Para verificar la conexión
```

### Challenge 2: Gestión del contexto (Ramas)
**Problema**: Casi realizo el commit del archivo my-info.txt directamente en la rama newbie en lugar de la rama feature/my-info.

**Solución**: Aprendí a usar git status y git branch frecuentemente para verificar mi ubicación actual antes de ejecutar git add. Tuve que usar git checkout para moverme a la rama correcta antes de preparar el archivo.


---

## 💭 Personal Reflection

**What surprised me**:
Me sorprendió lo rápido y ligero que es el sistema de ramas en Git. Pensaba que crear una rama duplicaría todos los archivos, pero ahora entiendo que son solo punteros a commits, lo que hace que cambiar de una a otra sea instantáneo.

**What I found most difficult**:
Acostumbrarme al paso intermedio del Staging Area (el comando add). A veces parece redundante, pero entiendo que es fundamental para tener un control total sobre qué cambios específicos queremos incluir en un commit y cuáles no.

**What I found most useful**:
El comando git log --oneline --graph --all. Proporciona un mapa visual muy claro de cómo divergen las ramas y dónde se encuentra cada una respecto a las demás.

**How I would apply this in real projects**:
En cualquier proyecto profesional, utilizaría este flujo para asegurar que la rama principal siempre sea funcional. Cada nueva tarea, por pequeña que sea, tendría su propia rama, y usaría mensajes de commit descriptivos para documentar el "por qué" de cada cambio, no solo el "qué".

---

## 📊 Self-Assessment

Rate your confidence level for each topic (1-5, where 5 is very confident):

| Topic | Confidence (1-5) | Notes |
|-------|------------------|-------|
| Basic Git commands | [5] | |
| Branching & merging | [4] | |
| Remote operations | [4] | |
| Conflict resolution | [2] | |
| History rewriting | [1] | |
| Git hooks | [1] | |
| Security practices | [1] | |

---

## 🔗 Evidence/Artifacts

**Links to branches/commits**:
- Link to your outcome branch: `https://github.com/eligarto-ugr/taller-master-ugr/tree/group-DS04-outcomes/newbie`
- Key commits demonstrating your work:
  - Commit hash: "Add hello.txt with my name"
  - Commit hash: "Add personal information"

**Additional files created** (if any):
- File 1: hello.txt - Archivo básico para practicar el flujo de preparación.
- File 2: my-info.txt - Archivo creado en una rama específica para practicar push remoto.

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

**Submission Date**: [08-01-2026]  
**Ready for Review**: ✅ Yes
