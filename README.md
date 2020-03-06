# Club Ethical Hacking - CLUSIR-Rhone-Alpes

## 2020-03-11 (Niveau Bonus)

### Installation

1. installer `docker` et `docker-compose`:
    - https://docs.docker.com/install
    - https://docs.docker.com/compose/install/
2. cloner ce dépôt:
    - `git clone https://github.com/Club-Ethical-Hacking-CLUSIR-Rhone-Alpes/2020-03-11.git`
3. rendez-vous dans le répertoire du projet, puis dans `challenge/`
4. création des challenges:
    - `chmod u+x start_level`
    - `docker-compose build -q`
5. démarrage des challenges:
    - `docker-compose up -d`
6. démarrage d'un niveau:
    - `./start_level` 
    - utilisez level11 comme mot de passe

> `docker-compose down` OU `ctrl+c` pour arrêter le challenge

---

### Objectifs

Vous devez réussir à passer “root” sur la machine.

Dans le fichier *“/root/flag”* se trouve un code qui permet de valider le
challenge.

