#  GUIDE PROJET ÉQUIPE // WORKFLOW GITFLOW & PULL REQUESTS

---

## 1. Objectifs & Règles d'Or de l'Équipe

Ce projet met en pratique le modèle industriel **GitFlow** en équipe, avec revue de code obligatoire via **Pull Requests (PR)** sur GitHub.

###  Règles fondamentales de collaboration :
1. **Zéro commit direct sur `master` et `develop` :** Tout ajout de code passe obligatoirement par une branche dédiée et une Pull Request validée.
2. **Synchronisation :** Toujours faire un `git pull origin develop` (ou `master`) avant de créer sa branche de travail.
3. **Double fusion obligatoire pour Release et Hotfix :** Les branches de fin de cycle (`release/*` et `hotfix/*`) doivent être fusionnées à la fois sur **`master`** ET sur **`develop`**.

---

## 2. Matrice des Rôles & Responsabilités

| Rôle | Membre | Branche de travail | Cible de la PR | Mission principale |
| :--- | :--- | :--- | :--- | :--- |
| **1. Lead / DevOps** | Personne 1 | `master` & `develop` | Dépôt initial | Initialise l'architecture, le style Cyberpunk, la Navbar et configure le dépôt GitHub. |
| **2. Dev Livre 1** | Personne 2 | `feature/livre-1` | `develop` | Fiche du livre *Neuromancien*, système de notation et formulaire d'avis. |
| **3. Dev Livre 2** | Personne 3 | `feature/livre-2` | `develop` | Fiche du livre *1984*, système de notation et formulaire d'avis. |
| **4. Release Manager**| Personne 4 | `release/v1.0.0` | `master` & `develop` | Ajoute le Footer, stabilise la version `1.0.0` et pose le Tag officiel. |
| **5. Hotfix Support** | Personne 5 | `hotfix/v1.0.1` | `master` & `develop` | Corrige le bug critique (avis non affichés) en injectant le JS et monte la version à `1.0.1`. |

---

## 3. Déroulé Pas-à-Pas du Projet

```
master  ───────●─────────────────────────────● (Tag v1.0.0) ──────────● (Tag v1.0.1)
                \                           /                         /
hotfix           \                         /                   ●─────/ (hotfix/v1.0.1)
                  \                       /                   /
release            \             ●───────●───────────────────/
                    \           /         \                 /
develop  ────────────●─────────●           \───────────────●─────────●
                      \       /
feature/livre-1        ●─────●
                        \   /
feature/livre-2          ●─●
```

---

### 🟢 PHASE 1 : Initialisation de la plateforme (Personne 1)

1. J'ouvrez un dossier vide dans **VS Code**.
2. Je crer le fichier **`index.html`** avec le squelette et la charte graphique :

```html
<!DOCTYPE html>
<html lang="fr" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CYBER-BOOKS // Avis & Notations</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600;800;900&family=Share+Tech+Mono&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Share Tech Mono', monospace; }
    h1, h2, h3, .cyber-font { font-family: 'Orbitron', sans-serif; }
    .neon-yellow { text-shadow: 0 0 10px #FCEE09; }
    .neon-cyan { text-shadow: 0 0 10px #00F0FF; }
  </style>
</head>
<body class="bg-[#07070a] text-zinc-200 min-h-screen border-t-4 border-[#FCEE09]">

  <!-- NAVBAR -->
  <nav class="max-w-6xl mx-auto px-6 py-5 flex justify-between items-center border-b border-zinc-800">
    <div class="flex items-center gap-2">
      <span class="w-2.5 h-2.5 bg-[#FCEE09] animate-pulse"></span>
      <span class="cyber-font text-2xl font-black tracking-widest text-[#FCEE09] neon-yellow">CYBER-BOOKS</span>
    </div>
    <span class="text-xs bg-zinc-900 border border-[#00F0FF] text-[#00F0FF] px-3 py-1 font-bold">
      BASE DE DONNÉES // 2 LIVRES
    </span>
  </nav>

  <main class="max-w-6xl mx-auto px-6 py-10 space-y-12">
    <!-- TODO Personne 2: Livre 1 (Neuromancien) -->

    <!-- TODO Personne 3: Livre 2 (1984) -->
  </main>

  <!-- TODO Personne 4: Footer -->
</body>
</html>
```

3. J'xécute dans le terminal de VS Code :
```bash
git init
git add .
git commit -m "init: structure de base revue de livres cyberpunk"
git branch -M master
git remote add origin https://github.com/VOTRE_ORGANISATION/VOTRE_REPO.git
git push -u origin master

# Création de la branche d'intégration
git switch -c develop
git push -u origin develop
```
4. **Action GitHub :** J'invite les 4 membres.

---

### 🟡 PHASE 2 : Développement des fonctionnalités (Personnes 2 & 3)

> **Pour l'équipe :** Clonez le projet sur votre VS Code :  
> `git clone https://github.com/C-S-Sylla/TP-Git-Groupe-1`

#### 👤 Personne 2 : Fiche Livre 1 (*Neuromancien*)
1. Création de la branche :
   ```bash
   git switch develop
   git pull origin develop
   git switch -c feature/livre-1
   ```
2. Dans `index.html`, remplacez `<!-- TODO Personne 2: Livre 1 (Neuromancien) -->` par :
   ```html
   <!-- LIVRE 1 -->
   <section class="bg-zinc-950 p-6 md:p-8 border-l-4 border-[#FCEE09] border-t border-zinc-800">
     <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4 mb-6">
       <div>
         <span class="text-xs text-[#FCEE09] tracking-widest uppercase">// ARCHIVE #01</span>
         <h2 class="text-3xl font-black text-white cyber-font">Neuromancien</h2>
         <p class="text-xs text-[#00F0FF]">Auteur : William Gibson (1984)</p>
       </div>
       <div class="bg-black border border-zinc-800 px-4 py-2 text-right">
         <span class="text-xs text-zinc-500 block">NOTE MOYENNE</span>
         <span class="text-xl font-bold text-[#FCEE09]">★ 4.8 / 5</span>
       </div>
     </div>

     <p class="text-sm text-zinc-400 mb-6 leading-relaxed">
       Le chef-d'œuvre fondateur du mouvement Cyberpunk. Case, un hacker dont le système nerveux a été détruit, est engagé pour une dernière mission d'intrusion dans une IA orbitale.
     </p>

     <!-- Formulaire Livre 1 -->
     <div class="bg-black p-5 border border-zinc-800">
       <h3 class="text-sm font-bold text-white mb-3 uppercase tracking-wider">// Déposer un avis</h3>
       <div class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-3">
         <input id="pseudo-1" type="text" placeholder="Votre Pseudo" class="bg-zinc-900 border border-zinc-700 px-3 py-2 text-xs text-white focus:border-[#FCEE09] outline-none">
         <select id="note-1" class="bg-zinc-900 border border-zinc-700 px-3 py-2 text-xs text-[#FCEE09] focus:border-[#FCEE09] outline-none">
           <option value="★★★★★ (5/5)">Note : ★★★★★ (5/5)</option>
           <option value="★★★★☆ (4/5)">Note : ★★★★☆ (4/5)</option>
           <option value="★★★☆☆ (3/5)">Note : ★★★☆☆ (3/5)</option>
           <option value="★★☆☆☆ (2/5)">Note : ★★☆☆☆ (2/5)</option>
           <option value="★☆☆☆☆ (1/5)">Note : ★☆☆☆☆ (1/5)</option>
         </select>
         <input id="comment-1" type="text" placeholder="Votre critique..." class="md:col-span-2 bg-zinc-900 border border-zinc-700 px-3 py-2 text-xs text-white focus:border-[#FCEE09] outline-none">
       </div>
       <button id="btn-1" class="bg-[#FCEE09] hover:bg-yellow-400 text-black font-extrabold text-xs uppercase px-5 py-2 tracking-wider transition">
         Envoyer la critique
       </button>
     </div>
     <div id="reviews-list-1" class="mt-4 space-y-3"></div>
   </section>
   ```
3. Validation et Pull Request :
   ```bash
   git add index.html
   git commit -m "feat: ajout fiche et formulaire livre 1"
   git push -u origin feature/livre-1
   ```
4. **Sur GitHub :** Ouvrez la PR de `feature/livre-1` vers **`develop`** et faites-la valider par un équipier.

---

#### 👤 Personne 3 : Fiche Livre 2 (*1984*)
1. Création de la branche :
   ```bash
   git switch develop
   git pull origin develop
   git switch -c feature/livre-2
   ```
2. Dans `index.html`, remplacez `<!-- TODO Personne 3: Livre 2 (1984) -->` par :
   ```html
   <!-- LIVRE 2 -->
   <section class="bg-zinc-950 p-6 md:p-8 border-l-4 border-[#00F0FF] border-t border-zinc-800">
     <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4 mb-6">
       <div>
         <span class="text-xs text-[#00F0FF] tracking-widest uppercase">// ARCHIVE #02</span>
         <h2 class="text-3xl font-black text-white cyber-font">1984</h2>
         <p class="text-xs text-[#FF003C]">Auteur : George Orwell (1949)</p>
       </div>
       <div class="bg-black border border-zinc-800 px-4 py-2 text-right">
         <span class="text-xs text-zinc-500 block">NOTE MOYENNE</span>
         <span class="text-xl font-bold text-[#00F0FF]">★ 4.9 / 5</span>
       </div>
     </div>

     <p class="text-sm text-zinc-400 mb-6 leading-relaxed">
       La dystopie de référence sur la surveillance permanente de Big Brother. Winston Smith tente de préserver son humanité et ses souvenirs au cœur de l'Océania.
     </p>

     <!-- Formulaire Livre 2 -->
     <div class="bg-black p-5 border border-zinc-800">
       <h3 class="text-sm font-bold text-white mb-3 uppercase tracking-wider text-[#00F0FF]">// Déposer un avis</h3>
       <div class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-3">
         <input id="pseudo-2" type="text" placeholder="Votre Pseudo" class="bg-zinc-900 border border-zinc-700 px-3 py-2 text-xs text-white focus:border-[#00F0FF] outline-none">
         <select id="note-2" class="bg-zinc-900 border border-zinc-700 px-3 py-2 text-xs text-[#00F0FF] focus:border-[#00F0FF] outline-none">
           <option value="★★★★★ (5/5)">Note : ★★★★★ (5/5)</option>
           <option value="★★★★☆ (4/5)">Note : ★★★★☆ (4/5)</option>
           <option value="★★★☆☆ (3/5)">Note : ★★★☆☆ (3/5)</option>
           <option value="★★☆☆☆ (2/5)">Note : ★★☆☆☆ (2/5)</option>
           <option value="★☆☆☆☆ (1/5)">Note : ★☆☆☆☆ (1/5)</option>
         </select>
         <input id="comment-2" type="text" placeholder="Votre critique..." class="md:col-span-2 bg-zinc-900 border border-zinc-700 px-3 py-2 text-xs text-white focus:border-[#00F0FF] outline-none">
       </div>
       <button id="btn-2" class="bg-[#00F0FF] hover:bg-cyan-400 text-black font-extrabold text-xs uppercase px-5 py-2 tracking-wider transition">
         Envoyer la critique
       </button>
     </div>
     <div id="reviews-list-2" class="mt-4 space-y-3"></div>
   </section>
   ```
3. Validation et Pull Request :
   ```bash
   git add index.html
   git commit -m "feat: ajout fiche et formulaire livre 2"
   git push -u origin feature/livre-2
   ```
4. **Sur GitHub :** Ouvrez la PR de `feature/livre-2` vers **`develop`** et validez la fusion.

---

### 🔵 PHASE 3 : Préparation de la Release v1.0.0 (Personne 4)

Les deux fonctionnalités sont réunies sur `develop`. Personne 4 finalise la version de production.

1. Création de la branche de release :
   ```bash
   git switch develop
   git pull origin develop
   git switch -c release/v1.0.0
   ```
2. Dans `index.html`, remplacez `<!-- TODO Personne 4: Footer -->` par :
   ```html
   <footer class="mt-20 border-t border-zinc-900 bg-black py-8 px-6 text-center text-xs text-zinc-500 tracking-wider">
     <div class="max-w-6xl mx-auto flex flex-col md:flex-row justify-between items-center gap-4">
       <span class="text-[#FCEE09] font-bold">CYBER-BOOKS // VERSION 1.0.0</span>
       <span>PLATEFORME DE CRITIQUES LITTÉRAIRES</span>
       <span class="text-zinc-600">DÉVELOPPÉ EN ÉQUIPE AVEC GITFLOW</span>
     </div>
   </footer>
   ```
3. Pousser la branche de release :
   ```bash
   git add index.html
   git commit -m "chore(release): ajout footer et preparation version 1.0.0"
   git push -u origin release/v1.0.0
   ```
4. **Sur GitHub, double fusion obligatoire :**
   * **PR 1 :** de `release/v1.0.0` vers **`master`** *(Merge)*.
   * **PR 2 :** de `release/v1.0.0` vers **`develop`** *(Merge)*.
5. **Poser le Tag de version officielle sur `master` :**
   ```bash
   git switch master
   git pull origin master
   git tag -a v1.0.0 -m "Release officielle v1.0.0"
   git push origin v1.0.0
   ```

---

### 🔴 PHASE 4 : Hotfix critique en Production (Personne 5)

> **Constat du bug en production :**  
> En testant la version `1.0.0` sur `master`, un dysfonctionnement majeur est détecté : **le clic sur les boutons d'envoi n'affiche aucun avis à l'écran**.  
> Le correctif consiste à injecter le script d'affichage dynamique des commentaires et à monter le numéro de version à **`1.0.1`**.

1. Créer la branche directement depuis **`master`** :
   ```bash
   git switch master
   git pull origin master
   git switch -c hotfix/v1.0.1
   ```
2. **Ajouter le script JavaScript de publication :**  
   Ouvrez `index.html` et collez ce script juste avant la fermeture de `</body>` :
   ```html
     <!-- SCRIPT HOTFIX : AFFICHAGE DYNAMIQUE DES COMMENTAIRES -->
     <script>
       function addReview(btnId, pseudoId, noteId, commentId, listId, colorBorder, colorText) {
         document.getElementById(btnId).addEventListener('click', function() {
           const pseudo = document.getElementById(pseudoId).value.trim();
           const note = document.getElementById(noteId).value;
           const comment = document.getElementById(commentId).value.trim();

           if (!pseudo || !comment) {
             alert("SYSTÈME : Remplissez le pseudo et le commentaire avant d'envoyer.");
             return;
           }

           const reviewCard = document.createElement('div');
           reviewCard.className = `bg-zinc-900 border-l-2 ${colorBorder} p-3 text-xs flex flex-col gap-1 transition-all`;
           reviewCard.innerHTML = `
             <div class="flex justify-between items-center text-zinc-400">
               <span class="font-bold text-white uppercase">[ID: ${pseudo}]</span>
               <span class="${colorText} font-bold">${note}</span>
             </div>
             <p class="text-zinc-300 italic">"${comment}"</p>
           `;

           document.getElementById(listId).prepend(reviewCard);

           document.getElementById(pseudoId).value = '';
           document.getElementById(commentId).value = '';
         });
       }

       addReview('btn-1', 'pseudo-1', 'note-1', 'comment-1', 'reviews-list-1', 'border-[#FCEE09]', 'text-[#FCEE09]');
       addReview('btn-2', 'pseudo-2', 'note-2', 'comment-2', 'reviews-list-2', 'border-[#00F0FF]', 'text-[#00F0FF]');
     </script>
   </body>
   ```

3. **Mettre à jour le numéro de version dans le Footer :**  
   Modifiez la ligne de version :
   ```html
   <!-- AVANT : VERSION 1.0.0 -->
   <!-- REMPLACER PAR : -->
   <span class="text-[#FCEE09] font-bold">CYBER-BOOKS // VERSION 1.0.1</span>
   ```

4. Valider et pousser le hotfix :
   ```bash
   git add index.html
   git commit -m "fix(prod): affichage dynamique des avis et mise a jour version 1.0.1"
   git push -u origin hotfix/v1.0.1
   ```

5. **Sur GitHub, double fusion obligatoire :**
   * **PR 1 :** de `hotfix/v1.0.1` vers **`master`** *(Merge)*.
   * **PR 2 :** de `hotfix/v1.0.1` vers **`develop`** *(Merge - garantit que le bug ne réapparaît pas plus tard)*.

6. **Poser le Tag de patch sur `master` :**
   ```bash
   git switch master
   git pull origin master
   git tag -a v1.0.1 -m "Patch v1.0.1: Système d'avis opérationnel"
   git push origin v1.0.1
   ```

---
