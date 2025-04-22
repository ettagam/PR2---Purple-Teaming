# Installation et configuration de CALDERA

Ce document décrit les étapes suivies pour installer et lancer la plateforme CALDERA dans le cadre de notre projet de simulation d’attaque.

---

## 1. Clonage du dépôt officiel

Nous avons cloné le répertoire GitHub officiel de CALDERA avec ses sous-modules :
```bash
git clone https://github.com/mitre/caldera.git --recursive
cd caldera
```

## 2. Activation de l'environnement Python

L’environnement virtuel Python est ensuite activé :
```bash
source .venv/bin/activate
```

> Si l’environnement `.venv` n’est pas encore présent, vous pouvez le créer avec :
> ```bash
> python3 -m venv .venv
> source .venv/bin/activate
> ```

## 3. Installation des dépendances

CALDERA utilise plusieurs bibliothèques Python listées dans `requirements.txt`. L'installation se fait via :
```bash
pip3 install -r requirements.txt
```

## 4. Lancement du serveur CALDERA

Une fois toutes les dépendances installées, le serveur peut être démarré :
```bash
python3 server.py --insecure --build
```

- L’option `--insecure` permet un lancement rapide sans certificat SSL (utile pour les tests locaux).
- L’option `--build` permet de générer les plugins et modules automatiquement lors du lancement.

## 5. Accès à l’interface web

Une fois le serveur lancé, l’interface web de CALDERA est accessible via :
```
http://localhost:8888
```

Les identifiants par défaut sont :
- **Username** : red
- **Password** : admin

---

