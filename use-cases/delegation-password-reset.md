# 🎭 Scénario — Délégation de droits & Réinitialisation de mot de passe

> Scénario pratiqué lors du lab TryHackMe "Active Directory Basics"

---

## 📋 Contexte

Dans une entreprise, il n'est pas souhaitable que chaque responsable de département contacte le service IT pour des opérations simples comme réinitialiser un mot de passe. La **délégation de contrôle** permet de donner des droits limités à un utilisateur sur son périmètre uniquement.

---

## 🏢 Situation

| Élément | Détail |
|---------|--------|
| **Domaine** | thm.local |
| **Technicien délégué** | Phillip (département Sales) |
| **Droit accordé** | Réinitialisation des mots de passe — OU Sales uniquement |
| **Utilisateur concerné** | Sophie (Sales) |

---

## ⚙️ Étapes réalisées

### 1. Délégation de contrôle sur l'OU Sales
```
Console ADUC
→ Clic droit sur l'OU "Sales"
→ "Delegate Control"
→ Sélectionner Phillip
→ Droit accordé : Reset user passwords and force password change
```

### 2. Connexion en tant que Phillip
```
Identifiants : THM\phillip / Claire2008
```

### 3. Réinitialisation du mot de passe de Sophie via PowerShell
```powershell
Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose
```

### 4. Forcer le changement à la prochaine connexion
```powershell
Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose
```

### 5. Validation — Connexion avec le compte Sophie
```
Identifiants : THM\sophie / [nouveau mot de passe]
→ Connexion réussie ✅
→ Flag récupéré sur le bureau ✅
```

---

## 💡 Ce que ce scénario apprend

- La **délégation** évite de donner des droits admin complets inutilement
- PowerShell est **indispensable** pour les tâches d'administration AD
- Le principe du **moindre privilège** : chaque utilisateur a uniquement les droits nécessaires

---

> *Scénario issu du lab TryHackMe — Active Directory Basics (100% complété)*
