# Linux commandes
# free -ml
La commande `free -ml` est utilisée pour afficher l’état de la mémoire sur un système Linux, avec les options suivantes :

- `-m` : affiche les valeurs en **mégaoctets**.
- `-l` : affiche également la **mémoire basse (low)** et la **mémoire haute (high)**, ce qui est utile sur certains systèmes 32 bits, mais souvent sans effet sur les systèmes modernes 64 bits.

### Exemple de sortie :
```bash
              total        used        free      shared  buff/cache   available
Mem:           64299       46200        1200        1024       16900       15800
Low:           64299       46200        1200
High:              0           0           0
Swap:          8192         500        7692
```

### Utilité :
Cette commande est utile pour surveiller la consommation mémoire, notamment pour détecter :
- une saturation de la RAM,
- une utilisation excessive du swap,
- ou pour comprendre comment le système gère le cache.

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

## Ce qui remplace ou complète `free -ml` aujourd’hui :

### 1. **`free -m` ou `free -h`**
- `-m` : affiche en mégaoctets.
- `-h` : affiche en format lisible (Mo, Go, etc.).
- Ces options suffisent pour la plupart des besoins.

### 2. **`vmstat`**
- Donne des infos sur la mémoire, les processus, les E/S, etc.
- Exemple : `vmstat -s`

### 3. **`top` ou `htop`**
- Affiche l’utilisation de la mémoire en temps réel.
- `htop` est plus lisible et interactif.

### 4. **`cat /proc/meminfo`**
- Source brute d’information sur la mémoire.
- Très utile pour des scripts ou des analyses détaillées.

### 5. **`smem`**
- Permet de voir la mémoire utilisée par chaque processus, avec partage.
- Utile pour comprendre qui consomme quoi.
---





# du -h -d 1
La commande `du -h -d 1` est utilisée sous Linux pour afficher l'utilisation de l'espace disque des sous-répertoires d'un répertoire donné, avec les options suivantes :

- `du` : "disk usage", affiche la taille des fichiers et dossiers.
- `-h` : "human-readable", affiche les tailles dans un format lisible (Ko, Mo, Go).
- `-d 1` : profondeur de récursion limitée à 1 niveau, donc seuls les dossiers directement contenus dans le répertoire courant sont listés.

### Exemple :
```bash
du -h -d 1
```

### Résultat typique :
```
1.2G    ./var
500M    ./home
20K     ./tmp
1.7G    .
```

Cela signifie :
- Le dossier `var` utilise 1.2 Go.
- Le dossier `home` utilise 500 Mo.
- Le dossier `tmp` utilise 20 Ko.
- Le total pour le répertoire courant est de 1.7 Go.
---




# df -h
La commande `df -h` est utilisée pour afficher l’espace disque disponible et utilisé sur les systèmes de fichiers montés, avec des tailles lisibles par l’humain.

### Détails des options :
- `df` : "disk free", affiche l’espace disque.
- `-h` : "human-readable", affiche les tailles en Ko, Mo, Go, etc.

### Exemple de sortie :
```bash
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   30G   18G  63% /
tmpfs            32G     0   32G   0% /dev/shm
/dev/sdb1       100G   70G   30G  70% /data
```

### Explication des colonnes :
- **Filesystem** : nom du système de fichiers ou du périphérique.
- **Size** : taille totale.
- **Used** : espace utilisé.
- **Avail** : espace disponible.
- **Use%** : pourcentage d’utilisation.
- **Mounted on** : point de montage dans l’arborescence.
---


