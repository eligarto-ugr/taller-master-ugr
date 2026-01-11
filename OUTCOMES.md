# Exercise Outcomes Submission Template

**Student/Group Name**: [Elias and Nikolina / DS04]  
**Level Completed**: [master-of-the-universe]  
**Date**: [11-01-2026]

---

## 📋 Exercise Summary

### Exercise: Branch Protection and Security Best Practices
**Status**: ✅ Completed

**What I did**:
En este nivel experto, he transformado el repositorio en un entorno de desarrollo seguro de grado empresarial. He configurado Branch Protection Rules en la rama main para forzar revisiones de código y firmas obligatorias. He implementado un sistema de firmas criptográficas GPG para verificar la autenticidad de cada commit, garantizando que nadie pueda suplantar mi identidad. Además, he realizado una auditoría de seguridad del historial para detectar posibles fugas de secretos y he reforzado la política de exclusión de archivos mediante un .gitignore profesional. Finalmente, he habilitado las funciones de seguridad avanzada de GitHub (Dependabot y Secret Scanning).

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
1. **Verificación de la Cadena de Suministro**: El papel de GPG para asegurar que el código fuente no ha sido alterado por terceros.
2. **Gobernanza mediante Branch Protection**: Cómo las reglas automáticas sustituyen la "buena voluntad" por políticas técnicas infranqueables.
3. **Inmutabilidad del Historial de Secretos**: La comprensión de que un secreto subido una vez es un secreto comprometido para siempre, independientemente de si se borra en commits posteriores.

**Skills I improved**:
- Configuración de infraestructura criptográfica local.
- Auditoría de seguridad de repositorios Git.
- Implementación de políticas de Code Owners para revisiones automáticas.

---

## 🚧 Challenges Faced

### Challenge 1: Configuración de GPG Agent
**Problem**: Git no solicitaba la contraseña de la llave GPG en la terminal, fallando el commit directamente con el error "error: gpg failed to sign the data".

**Solution**: Tuve que configurar la variable de entorno GPG_TTY y reiniciar el agente GPG para que la interfaz de entrada de contraseña (pinentry) apareciera correctamente en PowerShell.

**Commands/Approach**:
```bash
[Environment]::SetEnvironmentVariable("GPG_TTY", (tty), "User")
git config --global gpg.program "C:\Program Files (x86)\GnuPG\bin\gpg.exe"
```

---

### Challenge 2: Pushes bloqueados por protección
**Problem**: Incluso tras habilitar GPG, el push a main fallaba porque no cumplía con la regla de "Require a pull request before merging".

**Solution**: Esto demostró que las reglas funcionan incluso para administradores. Tuve que cambiar el flujo de trabajo a uno basado estrictamente en ramas de funcionalidad y PRs.

---

## 💭 Personal Reflection

La culminación de este entrenamiento en el nivel "Master of the Universe" me ha permitido comprender que Git no es solo una herramienta de almacenamiento de código, sino el núcleo de la seguridad en la cadena de suministro de software (Supply Chain Security). En un entorno profesional, la confianza es un activo que no puede dejarse al azar. El uso de firmas GPG es la única forma técnica de garantizar la no repudiación; sin ellas, cualquier atacante con acceso a la red interna podría configurar un user.email falso y subir código malicioso que parecería provenir de un desarrollador senior o un administrador. La marca "Verified" en GitHub no es un adorno estético, es una prueba criptográfica de integridad.
Por otro lado, la implementación de las Branch Protection Rules cambia radicalmente la cultura de un equipo. Al exigir revisiones obligatorias y estados de comprobación (checks) verdes, el repositorio se protege contra el error humano y la urgencia mal entendida. La integración de los Code Owners asegura que el conocimiento esté distribuido y que los expertos en seguridad o arquitectura tengan siempre la última palabra sobre los cambios en áreas críticas del sistema. Esto crea un equilibrio saludable entre la agilidad de desarrollo y la estabilidad del sistema.
Finalmente, la gestión de datos sensibles es quizás el punto más crítico de esta formación. He aprendido que la seguridad en Git es retrospectiva: una vez que un token de acceso o una contraseña llega al historial, la única respuesta profesional es la rotación inmediata de la credencial y la limpieza del historial mediante herramientas como git-filter-repo. Estas prácticas, sumadas al uso de firmas y protecciones, alinean el flujo de trabajo con los principios de DevSecOps, donde la seguridad no es una fase final, sino una propiedad intrínseca del proceso de construcción de software. Como "Master of the Universe", mi responsabilidad ahora es diseñar flujos de trabajo donde sea fácil hacer las cosas bien y técnicamente difícil cometer errores de seguridad.

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
  - db958f8: Commit firmado y verificado con GPG.

**Additional files created** (if any):
- security-artifacts/public-key.asc: Mi llave pública GPG para verificación externa.
- security-artifacts/protection-rules.txt: Resumen de las reglas aplicadas en GitHub.

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
