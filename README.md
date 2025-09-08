# Linux

La commande `free -ml` est utilisée sur les systèmes Linux pour afficher l'utilisation de la mémoire en mégaoctets (Mo), avec l'option `-l` qui montre également la mémoire basse et haute (low/high memory), bien que cette distinction soit surtout pertinente sur les anciens systèmes 32 bits.

Voici un exemple typique de sortie :

```
              total        used        free      shared  buff/cache   available
Mem:          64262       46258        3452        1024       14552       15874
Low:          64262       46258        3452
High:             0           0           0
Swap:         8192         1024        7168
```

### Explication des colonnes :
- **total** : quantité totale de mémoire.
- **used** : mémoire utilisée.
- **free** : mémoire libre.
- **shared** : mémoire partagée entre les processus.
- **buff/cache** : mémoire utilisée par les buffers et le cache du système.
- **available** : estimation de la mémoire disponible pour les nouveaux processus sans swap.

### Sections supplémentaires :
- **Low/High** : distinction entre mémoire basse et haute (utile sur les anciens systèmes).
- **Swap** : espace d’échange sur disque utilisé lorsque la RAM est pleine.

- Bonne question ! Sur les systèmes modernes (notamment 64 bits), la distinction entre **low** et **high memory** n’a plus vraiment de sens, car toute la mémoire est accessible directement par le noyau.
- L’option `-l` de la commande `free` est donc **obsolète** ou **ignorée** sur la plupart des distributions actuelles.

### Ce qui remplace ou complète `free -ml` aujourd’hui :

#### 1. **`free -m` ou `free -h`**
- `-m` : affiche en mégaoctets.
- `-h` : affiche en format lisible (Mo, Go, etc.).
- Ces options suffisent pour la plupart des besoins.

#### 2. **`vmstat`**
- Donne des infos sur la mémoire, les processus, les E/S, etc.
- Exemple : `vmstat -s`

#### 3. **`top` ou `htop`**
- Affiche l’utilisation de la mémoire en temps réel.
- `htop` est plus lisible et interactif.

#### 4. **`cat /proc/meminfo`**
- Source brute d’information sur la mémoire.
- Très utile pour des scripts ou des analyses détaillées.

#### 5. **`smem`**
- Permet de voir la mémoire utilisée par chaque processus, avec partage.
- Utile pour comprendre qui consomme quoi.

---
# Personnalisation du terminal

Pour personnaliser ton terminal, tu peux modifier le fichier `.bashrc` ou `.zshrc` selon ton shell. Pour inverser les couleurs de la ligne de commande et afficher le chemin dans ton prompt, ajoute une configuration comme celle-ci :

Cmd
Description

```bash
PS1='\[\e[7m\]
\u@\h: \w\$
\[\e[0m\] '
```

Cela affiche l'utilisateur, le nom de l'hôte et le chemin, en inversant les couleurs.
\[\e[7m\]	Pour inverser les couleurs de la ligne de commande
Ou	Ou
\e[32m	change la couleur en vert (code ANSI 32 pour le vert).
	
\u@\h: \w\$	Ainsi, un prompt configuré comme \u@\h:\w\$ afficherait quelque chose comme jeremie@machine:/home/jeremie$
	\u
	Affiche nom d'utilisateur de l'utilisateur connecté.
	\h
	Affiche nom de l'hôte
	\w
	Affiche répertoire de travail actuel 
	(absolu, avec ~ pour représenter le répertoire personnel).
	\$
	affiche # si l'utilisateur est root, ou $ si l'utilisateur est non-root.
	
	
\[\e[0m\] 	réinitialise la couleur pour éviter que tout le texte reste vert.
 Actualise les changements avec `source ~/.bashrc` ou `source ~/.zshrc`.
<img width="1238" height="626" alt="image" src="https://github.com/user-attachments/assets/39935d89-43d6-4876-b967-f9db0e81e3fe" />
