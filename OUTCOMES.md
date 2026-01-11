# Exercise Outcomes Submission Template

**Student/Group Name**: [Elias and Nikolina / DS04]  
**Level Completed**: [intermediate]  
**Date**: [11-01-2026]

---

## 📋 Exercise Summary

### Exercise: [Merging, Conflict Resolution and Tagging]
**Status**: ✅ Completed

**What I did**:
We tackled the intermediate level, focusing on multi-branch workflows and conflict resolution. We set up two separate branches—feature/header and feature/footer—both targeting the same page.html file. This intentionally led to a merge conflict when we brought them back into the intermediate branch, which we had to sort out manually. To wrap things up, we practiced using both annotated and lightweight tags to keep track of our stable project versions.

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
1. **Beyond text conflicts**: We learned that merge conflicts aren't always just about clashing lines of code. Dealing with the "Modify/Delete" conflict showed us that Git also tracks structural changes, which forced us to think more logically about how we integrate different branches.
2. **The encoding headache**: A major takeaway for us was how much file encoding matters. Since we were using PowerShell on Windows, Git initially mistook our text files for binaries because they weren't in UTF-8. It was a bit of a hurdle, but it taught us to always double-check our environment settings to keep the workflow smooth.
3. **Professional Tagging**: We got the hang of using annotated tags to mark project milestones. We now understand that while branches are fluid, tags provide an immutable way to label stable releases, which is essential for any real-world software project.

---

**Skills I improved**:
- **Handling manual merge conflicts and branch cleanup**: We got better at fixing messy conflicts by hand and learned why it's so important to keep our branch history tidy after a merge.
- **Release management via git tag**: We’ve grown comfortable using tags to mark stable releases, ensuring we have clear, permanent milestones in our project.
- **Troubleshooting Git on Windows**: We improved our ability to debug setup quirks, especially when dealing with PowerShell and the encoding issues that tend to pop up in Windows environments.

---

## 🚧 Challenges Faced

### The "Binary Files" Warning & Encoding Mess
**Problem**: While we were trying to merge feature/footer, we hit an unexpected error: `warning: Cannot merge binary files: page.html`. It turned out that because we were working in PowerShell, the file was automatically saved in UTF-16 format. This confused Git into thinking the file was a binary instead of plain text, so it couldn't insert the conflict markers we needed.

**Solution**: We had to abort the merge and manually delete the files from our folder to clear any trace of the wrong encoding. We then recreated them from scratch using VS Code, making sure to specifically save them in UTF-8. This finally let Git see the text and allowed us to finish the merge properly.

**Commands/Approach**:
```bash
git merge --abort
rm page.html
# Recrear archivo en VS Code con codificación UTF-8
git add page.html
git commit -m "Fix encoding to UTF-8"
```

---

### Challenge 2: The "Modify/Delete" Snag
**Problem**: While we were tidying up the repository, we accidentally wiped page.html from the base branch. When we went to merge feature/header, Git hit a bit of a snag. It didn't know whether to stick with the deletion from our base branch or keep the modified version coming from the feature branch. It flagged this with the error: `CONFLICT (modify/delete): page.html deleted in HEAD and modified in feature/header.`.

**Solution**: To get things back on track, we used `git add page.html`. This was our way of telling Git that we definitely wanted to keep the version from the feature branch. Running that command effectively restored the file and let us finish the merge without further issues.

---

## 💭 Personal Reflection

This level was a real eye-opener for us because we ran into actual problems that go way beyond what you see in basic tutorials. Fixing those merge conflicts taught us that Git is all about precision; we learned the hard way that a tiny detail can completely stall a workflow if you aren't careful.
Finally getting a grip on those conflict markers (<<<<<<< HEAD, =======, >>>>>>>) makes us feel a lot more confident about working in a team. Even if everyone is editing the same lines of code, we now know there’s a reliable way to bring it all together without losing work. Plus, we finally see why tagging is so vital for professional organization.

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
  - c2f3270: "Merge footer with resolved conflicts"
  - ced1e9c: "Mantener page.html desde feature/header"
  - b737c43: "Clean up intermediate before merging"

**Additional files created** (if any):
- File 1: page.html - Main file with the header and footer.
- File 2: OUTCOMES.md - Submission file.

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

**Submission Date**: [11-01-2026]  
**Ready for Review**: ✅ Yes
