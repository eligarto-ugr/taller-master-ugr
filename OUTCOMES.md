# Exercise Outcomes Submission Template

**Student/Group Name**: [Elias and Nikolina / DS04]  
**Level Completed**: [master]  
**Date**: [11-01-2026]

---

## 📋 Exercise Summary

### Exercise: [Rewriting History (Rebase and Amend Commits)]
**Status**: ✅ Completed

**What we did**:
We moved up to the Master level to learn how to keep a project history looking professional. We started by using git `commit --amend` to tweak our last commit instead of just piling up "oops" commits every time we forgot a line of code. Then, we dove into Interactive Rebase to tidy up our work; using `fixup` was great for merging small typo fixes into the main feature commits so they disappeared from the log. To finish it off, we rebased our feature branch onto master. This gave us that nice linear history without the messy "merge commits" you usually see in the graph.

**Commands Used**:
```bash
# Part 1: Amend
git commit --amend -m "Add complete configuration file"

# Part 2: Interactive Rebase
git rebase -i HEAD~3 # Usando 'fixup' y 'reword'

# Parte 3: Branch Rebase
git checkout feature/awesome-feature
git rebase master

# Visualization
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
- <img width="931" height="955" alt="Captura de pantalla 2026-01-11 122030" src="https://github.com/user-attachments/assets/6be420e3-6717-40ed-a8b1-fee7c7ca9497" />

- <img width="942" height="952" alt="Captura de pantalla 2026-01-11 122127" src="https://github.com/user-attachments/assets/37fd1318-b1a6-4832-8960-453c6ede2d80" />

- <img width="929" height="440" alt="Captura de pantalla 2026-01-11 122148" src="https://github.com/user-attachments/assets/58d15800-cef9-4094-92ee-e62bbfe413c2" />

---

## 🎯 Key Learnings

**Main concepts I learned**:
1. **Commits are (technically) permanent**: We learned that rewriting history doesn't actually edit an old commit; instead, Git creates a brand new one with a different SHA. It was interesting to see how the IDs changed even if the content stayed the same.
2. **Clean vs. Messy graphs**: We now see the difference between a chronological history (merges) and a logical one (rebases). Keeping a linear history makes the whole project much easier to follow for anyone else.
3. **The "Golden Rule"**: We realized why you should never rewrite history on shared branches. Doing so breaks everyone else's local repo, so we'll be keeping these tools for our private feature branches only.

**Skills I improved**:
- **Commit hygiene**: We've gotten much better at cleaning up "work in progress" commits before they ever reach a code review.
- **Mastering the interactive editor**: We’re now comfortable using the rebase script to pick, fixup, and reword our history.
- **Safer Pushing**: We understand why `--force-with-lease` is the professional way to go when you need to update a rebased branch, as it protects us from accidentally overwriting a teammate's work.

---

## 🚧 Challenges Faced

### Challenge 1: The disappearing SHAs
**Problem**: After rebasing our feature branch onto master, we were surprised to see that every single commit ID had changed. We had to wrap our heads around the fact that Git was basically "replaying" our work on a new foundation, creating entirely new objects.

**Solution**: This taught us exactly why rebasing is strictly for local/private work. If we had done this on a public branch, our teammates would have had a nightmare trying to sync their work.


### Challenge 2: Reordering in Interactive Rebase
**Problem**: Getting the `fixup` command to work correctly was a bit tricky at first. We had to manually move the "typo fix" line in the editor so it sat right under the commit we wanted to patch.

**Solution**: We learned that the order of the lines in the rebase script is exactly how Git will rebuild the history. Once we figured out how to move the lines around, the squashing process worked perfectly.

---

## 💭 Personal Reflection

Honestly, it's pretty cool that you can "clean up" your past mistakes to make the history look perfect. Being able to take a dozen messy trial-and-error commits and squash them into one well-explained feature commit is a huge plus for anyone reading our code later. It took a bit of a mindset shift to realize that the Git history isn't "sacred." At first, `rebase -i` felt like we were playing with fire, but knowing that we can always use `git reflog` to undo a mistake made us feel much more adventurous.
In a real job, we'd use rebase daily to keep our feature branches in sync with the main branch. Before opening a Pull Request, we’d definitely use interactive rebase to polish our work so the reviewer sees a clear, logical progression of features instead of our behind-the-scenes struggles.

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
  - 9b83fc1: Final commit after rebasing onto master.
  - a41fe26: Unified commit created via `amend`.

**Additional files created** (if any):
- config.txt: Used for the amend exercise.
- featureA.txt y featureB.txt: Files used during the interactive rebase.

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
