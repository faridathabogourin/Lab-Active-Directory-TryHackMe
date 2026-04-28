# 🖥️ Active Directory Basics — Lab Pratique

> **Plateforme :** TryHackMe  
> **Room :** [Active Directory Basics](https://tryhackme.com/room/winadbasics)  
> **Résultat :** ✅ 100% complété  
> **Durée :** ~30 minutes  
> **Niveau :** Débutant / Intermédiaire  
> **Objectif :** Comprendre et pratiquer l'administration Active Directory sur un environnement Windows Server réel  

---

## 🎯 Pourquoi ce lab ?

Active Directory est utilisé dans **95% des entreprises** sous Windows pour gérer les utilisateurs, les ordinateurs et les droits d'accès. C'est la compétence de base de tout technicien support IT ou administrateur systèmes.

Ce lab m'a permis de pratiquer AD sur un vrai Windows Server, directement dans le navigateur — sans installation locale.

---

## 📋 Ce qui a été couvert

| Tâche | Contenu | Statut |
|-------|---------|--------|
| Task 1 | Introduction à Active Directory | ✅ |
| Task 2 | Windows Domains — structure et rôles | ✅ |
| Task 3 | Utilisateurs et groupes AD | ✅ |
| Task 4 | Unités d'Organisation (OU) et délégation | ✅ |
| Task 5 | Stratégies de groupe (GPO) | ✅ |
| Task 6 | Méthodes d'authentification (Kerberos, NTLM) | ✅ |
| Task 7 | Arbres, forêts et domaines | ✅ |

---

## ⚙️ Compétences pratiquées

### 🗂️ Structure Active Directory
- Navigation dans la console **ADUC** (Active Directory Users and Computers)
- Lecture et compréhension de l'arbre du domaine `thm.local`
- Identification des conteneurs par défaut : Builtin, Computers, Users, Domain Controllers

### 👥 Gestion des utilisateurs et groupes
- Consultation des comptes utilisateurs du domaine
- Lecture des groupes de sécurité (Domain Admins, Domain Users...)
- Compréhension des Unités d'Organisation (OU) : IT, Sales, Marketing, Management, R&D

### 🔐 Délégation et droits
- Délégation de contrôle sur une OU spécifique
- Réinitialisation de mot de passe via **PowerShell** :

```powershell
Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose
Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose
```

### 🛡️ Authentification
- Compréhension du protocole **Kerberos** (tickets TGT/TGS)
- Différence entre authentification locale et authentification de domaine
- Rôle du contrôleur de domaine (DC) dans l'authentification

### 🌐 Architecture avancée
- Différence entre **domaines**, **arbres** et **forêts**
- Rôle des **Enterprise Admins** vs **Domain Admins**
- Réplication entre contrôleurs de domaine

---

## 📸 Aperçu du lab

### Progression 100% complétée
![Progression](screenshots/progression-100.png)

### Console Active Directory — Arbre du domaine thm.local
![Arbre AD](screenshots/ad-tree.png)

### Groupes de sécurité du domaine
![Groupes](screenshots/security-groups.png)

### Domain Admins — Membres du groupe
![Domain Admins](screenshots/domain-admins-members.png)

### Unités d'Organisation (OU) — IT, Sales, Marketing...
![OU Structure](screenshots/ou-structure.png)

### Réinitialisation mot de passe via PowerShell
![PowerShell](screenshots/powershell-reset.png)

---

## 💡 Ce que j'ai appris

### Concepts clés retenus

**1. Pourquoi Active Directory ?**
Sans AD, chaque PC gérerait ses propres utilisateurs localement. AD centralise tout : un seul compte pour accéder à toutes les ressources de l'entreprise.

**2. La logique des OU**
Les Unités d'Organisation permettent de structurer l'annuaire comme un organigramme d'entreprise — et d'appliquer des politiques différentes selon les départements.

**3. La délégation de contrôle**
On peut donner à un utilisateur des droits limités sur une OU spécifique sans lui donner les droits admin complets. Exemple : le responsable RH peut réinitialiser les mots de passe de son département uniquement.

**4. Kerberos vs NTLM**
Kerberos est le protocole moderne et sécurisé utilisé par défaut dans AD. NTLM est l'ancien protocole, encore présent pour la compatibilité mais moins sécurisé.

**5. PowerShell pour l'administration AD**
La ligne de commande est indispensable pour automatiser les tâches d'administration — réinitialisation de MDP, création d'utilisateurs en masse, application de politiques.

---



## 🔗 Ressources complémentaires

- [Documentation Microsoft AD DS](https://learn.microsoft.com/fr-fr/windows-server/identity/ad-ds/)
- [Room TryHackMe — Active Directory Basics](https://tryhackme.com/room/winadbasics)
- [Mon profil TryHackMe](https://tryhackme.com/p/faridathabogourin7)

---

## 🛠️ Technologies & Outils

![Windows Server](https://img.shields.io/badge/Windows_Server-2019-0078D6?style=flat&logo=windows&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active_Directory-AD-0078D6?style=flat&logo=microsoft&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=flat&logo=powershell&logoColor=white)
![TryHackMe](https://img.shields.io/badge/TryHackMe-100%25-212C42?style=flat&logo=tryhackme&logoColor=white)

---

> *Lab complété dans le cadre d'une préparation à une alternance Support IT / Réseaux — 2026*  
> *Plateforme : TryHackMe | Room : Active Directory Basics | Score : 100%*
