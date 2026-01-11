# Exercise Outcomes Submission Template

**Student/Group Name**: [Elias and Nikolina / DS04]  
**Level Completed**: [master-of-the-universe]  
**Date**: [11-01-2026]

---

## 📋 Exercise Summary

### Exercise: Branch Protection and Security Best Practices
**Status**: ✅ Completed

**What I did**:
For this final expert level, we turned our repository into a secure, enterprise-grade development environment. We locked down the main branch by setting up Branch Protection Rules that enforce code reviews and mandatory commit signing. We also implemented a GPG cryptographic signing system to verify the authenticity of every commit, making it impossible for anyone to impersonate us. On top of that, we ran a security audit on our entire history to check for leaked secrets and tightened our .gitignore policy. To wrap things up, we enabled GitHub’s advanced security features like Dependabot and Secret Scanning to keep the repo safe moving forward.

**Commands Used**:
```bash
# Generación y configuración de GPG
gpg --full-generate-key
gpg --list-secret-keys --keyid-format=long
gpg --armor --export [ID_KEY]
git config --global user.signingkey [ID_KEY]
git config --global commit.gpgsign true

# Verificación y auditoría
git log --show-signature -1
git log -p | grep -i "password\|api_key\|secret"
git rev-list --objects --all | git cat-file --batch-check

# Flujo de trabajo firmado
git commit -S -m "docs: Add security outcomes"
```

**Results/Output**:
```
elias@PC_de_Elias MINGW64 ~/taller-master-ugr (feature/verified-work)
$ git log --show-signature -1
commit db958f881b86e866e81b067422cfa4fb1f4db234 (HEAD -> feature/verified-work, origin/feature/verified-work)
gpg: Signature made do., 11 de ene. de 2026 13:11:02
gpg:                using RSA key C719984927DD9CF335010572A4E40DA03E7907B4
gpg: Good signature from "eligarto-ugr (master) <e.eligarto@go.ugr.es>" [ultimate]
Author: Elias <e.eligarto@go.ugr.es>
Date:   Sun Jan 11 13:11:02 2026 +0100

    feat: add verified commit with GPG
```

**Screenshots** (if applicable):
- <img width="1902" height="954" alt="Captura de pantalla 2026-01-11 130218" src="https://github.com/user-attachments/assets/09e9f192-16da-41d0-9eba-8905a5d1c0dd" />

- <img width="927" height="927" alt="Captura de pantalla 2026-01-11 131307" src="https://github.com/user-attachments/assets/4fc0303e-3906-4c9e-aabe-56ed17b8c52a" />

- <img width="945" height="952" alt="Captura de pantalla 2026-01-11 131435" src="https://github.com/user-attachments/assets/7b451eb4-e72b-4aff-beeb-fbc60bc74e7e" />

- <img width="841" height="959" alt="Captura de pantalla 2026-01-11 131502" src="https://github.com/user-attachments/assets/50daef9f-b189-4723-82fe-ec56b4918c09" />

- <img width="925" height="943" alt="Captura de pantalla 2026-01-11 131551" src="https://github.com/user-attachments/assets/ced35ecb-ff3d-4f11-8755-9d41fb20937b" />

- <img width="928" height="912" alt="Captura de pantalla 2026-01-11 131611" src="https://github.com/user-attachments/assets/04ff677b-b101-40bb-ac86-ebce4dd973d0" />

- <img width="921" height="947" alt="Captura de pantalla 2026-01-11 131629" src="https://github.com/user-attachments/assets/f568cfe5-7d78-40e5-b745-6a502f6738ac" />

- <img width="929" height="888" alt="Captura de pantalla 2026-01-11 131646" src="https://github.com/user-attachments/assets/0aaaf5cf-1d45-44cc-960c-029226b1a9f6" />

---

## 🎯 Key Learnings

**Main concepts I learned**:
1. **Supply Chain Security**: We learned how GPG acts as a digital seal, ensuring that the source code hasn't been tampered with by unauthorized third parties.
2. **Governance via Branch Protection**: We saw how automated rules replace "good intentions" with technical safeguards that simply cannot be bypassed.
3. **The Permanence of Leaked Secrets**: We now understand that once a secret is pushed, it is compromised forever, regardless of whether it’s deleted in later commits.

**Skills I improved**:
- Setting up local cryptographic infrastructure for Git.
- Conducting thorough security audits on repository histories.
- Implementing Code Owners policies to automate specialized reviews.

---

## 🚧 Challenges Faced

### Challenge 1: GPG Agent Configuration Quirks
**Problem**: At first, Git wasn't prompting us for the GPG passphrase in the terminal. The commits just kept failing with the generic "error: gpg failed to sign the data" message.

**Solution**: We had to troubleshoot the environment variables and set `GPG_TTY`. After restarting the GPG agent, the pinentry interface finally popped up correctly in our PowerShell terminal, allowing us to sign our work.

**Commands/Approach**:
```bash
[Environment]::SetEnvironmentVariable("GPG_TTY", (tty), "User")
git config --global gpg.program "C:\Program Files (x86)\GnuPG\bin\gpg.exe"
```

---

### Challenge 2: Blocked by our own Protections
**Problem**: Even after we got GPG working, our attempts to push to main were blocked because we hadn't met the "Require a pull request before merging" rule.

**Solution**: This was actually a great "success" because it proved the rules were working even for us as admins. We had to shift our mindset and strictly follow the feature-branch and PR workflow for every single change.

---

## 💭 Personal Reflection

We’ve realized that Git isn’t just about saving code; it’s the heart of Supply Chain Security. Using GPG signatures is the only technical way to guarantee non-repudiation. Without them, any attacker with internal access could spoof a user.email and push malicious code that looks like it came from a dev. The "Verified" badge on GitHub isn't just for show; it’s cryptographic proof of integrity. Implementing Branch Protection Rules also fundamentally changes the team culture. By requiring mandatory reviews and "green" status checks, the repository is shielded from human error and "emergency" shortcuts that usually lead to technical debt or security holes. Integrating Code Owners ensures that knowledge is distributed and that security or architecture experts always have the final say on changes to critical parts of the system. This creates a healthy balance between development speed and system stability.
Finally, managing sensitive data was perhaps the most eye-opening part of this training. We learned that security in Git is retrospective: once a token or password hits the history, the only professional response is immediate credential rotation and a deep history cleanup using tools like git-filter-repo. These practices, combined with signing and protections, align our workflow with DevSecOps principles, where security is an intrinsic part of the build process rather than a final checkbox.

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
| Git hooks | [5] | |
| Security practices | [5] | |

---

## 🔗 Evidence/Artifacts

**Links to branches/commits**:
- Link to your outcome branch: `https://github.com/miguel-oltra/taller-master-ugr/tree/group-DS04-outcomes/master-of-the-universe`
- Key commits demonstrating your work:
  - db958f8: Verified commit signed with our GPG key.

**Additional files created** (if any):
- security-artifacts/public-key.asc: Our GPG public key for external verification.
- security-artifacts/protection-rules.txt: Summary of the rules we applied on GitHub.

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
