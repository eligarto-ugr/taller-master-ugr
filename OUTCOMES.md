# Exercise Outcomes Submission Template

**Student/Group Name**: Elias and Nikolina/DS04  
**Level Completed**: [newbie]  
**Date**: [08-01-2026]

---

## 📋 Exercise Summary

### Exercise: [Newbie]
**Status**: ✅ Completed

**What I did**:
In this first level, we got a solid handle on the Git basics. We walked through the initial setup, the core "add and commit" workflow, and learned how to manage local branches. We also practiced syncing our local work with our remote fork on GitHub, ensuring our progress was properly backed up and tracked.

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
- <img width="1245" height="977" alt="Captura de pantalla 2026-01-08 192552" src="https://github.com/user-attachments/assets/f4ca3a06-fd8e-42be-83e3-b4fc189635c7" />

- <img width="965" height="973" alt="Captura de pantalla 2026-01-08 192616" src="https://github.com/user-attachments/assets/a35ede5a-dfff-412e-8deb-5b40ad9c9c8a" />

- <img width="935" height="956" alt="Captura de pantalla 2026-01-08 192631" src="https://github.com/user-attachments/assets/99b93920-f03d-4bd0-859f-e037232604ea" />

- <img width="1249" height="924" alt="Captura de pantalla 2026-01-08 192925" src="https://github.com/user-attachments/assets/24a2a60f-94f2-4667-bdcf-14441b0366ff" />


---

## 🎯 Key Learnings

**Main concepts I learned**:
1. **The Three-Tree Architecture**: We now understand how Git separates the Working Directory, the Staging Area, and the Local Repository. It makes the workflow much more logical.
2. **Isolated Development**: We learned how to use branches to build new features without risking the stability of our main code.
3. **Remote Synchronization**: We practiced the full cycle of pushing local changes to GitHub and pulling updates to keep our local environment in sync with the remote repository.

**Skills I improved**:
- **CLI Fluency**: We’ve become much more comfortable managing version control through the terminal instead of relying on a GUI.
- **History Tracking**: We learned how to interpret `git log` to trace back changes and see exactly how the project has evolved.
- **Identity Management**: We properly configured our global user settings and verified our connection using SSH keys.

---

## 🚧 Challenges Faced

### Challenge 1: SSH Authentication
**Problema**: When we first tried to clone the repo, we hit a "Permission denied (publickey)" error.

**Solución**: We realized we hadn't linked our SSH keys to GitHub yet. We had to generate a new ED25519 key pair and add the public key to our GitHub account settings to get things moving.

**Comandos/Enfoque**:
```
ssh-keygen -t ed25519 -C "e.eligarto@go.ugr.es"
# Luego copié el contenido de ~/.ssh/id_ed25519.pub en GitHub Settings -> SSH and GPG keys
ssh -T git@github.com # Para verificar la conexión
```

### Challenge 2: Context Awareness (Branching)
**Problema**: We almost made the mistake of committing `my-info.txt` directly to the newbie branch instead of our dedicated feature branch.

**Solución**: We’ve started using `git status` and `git branch` constantly to double-check where we are. We had to use `git checkout` to jump to the right branch before staging our files.


---

## 💭 Personal Reflection

It’s impressive how fast and lightweight Git handles branches. We used to think creating a branch meant duplicating all the files, but learning that they are just "pointers" to commits explains why switching between them is so instant. Getting used to the add step took a bit of time. It felt a bit repetitive at first, but we now see it’s essential for having total control over exactly which changes make it into a commit. The `git log --oneline --graph --all` command is a total game-changer. It gives us a very clear visual map of how branches diverge and where each one stands compared to the others.
In any professional setting, we’ll definitely stick to this "feature-branch" workflow. It’s the only way to ensure the main branch stays clean and functional while we work on experimental updates or new features in the background.

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
  - f437a3f: "Add hello.txt with my name"
  - cc25294: "Add personal information"

**Additional files created** (if any):
- File 1: hello.txt - A simple file to practice the staging workflow.
- File 2: my-info.txt - A file created on a feature branch to practice remote pushes.

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

---

**Submission Date**: [08-01-2026]  
**Ready for Review**: ✅ Yes
