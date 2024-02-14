# Objectif du projet RsFaas
<img width="719" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/b57a413d-15e9-4c49-ad5e-0a2751eca433">

# Framework Faas choisi : OpenFaas
Pour notre projet, nous avons choisi le framework OpenFaas pour sa facilité d'installation et d'utilisation.
L'ajout d'une fonction sur OpenFaas se fait en quelques étapes simples :
* faas-cli new pydict --lang python3-flask-debian
* faas-cli build -f pydict.yml
* faas-cli push -f pydict.yml
* faas-cli deploy -f pydict.yml -g http://127.0.0.1:8080
Cette série d'instructions créent une architecture particulière, comme on peut le voir dans l'exemple suivant pour un projet python :
<img width="576" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/2dec67b5-2e1d-41ab-b1a0-6bf7c3a935f9">
* Le fichier **requirements.txt** contient les librairies necessaires pour l'exécution de la fonction
* Le fichier **handler.py** contient la fonction en elle-même
  <img width="960" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/9e6300c2-a130-44c4-a762-796c4c8f8089">
 * L'évènemennt ici se refère à une requête HTTP simple 
<img width="960" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/12aba1a1-96ed-42ee-953e-522f1e670f15">

# Conception de la solution
Notre solution est un script écrit en python qui s'execute de façon continue sur le serveur et intercepte les requêtes HTTP qui contiennent la clé de déchiffrement. Une fois la requête interceptée, le script déchiffre à l'aide de la clé le précédent fichier **handler.py** puis re-execute les précédentes commandes. 
Ensuite la requête est acheminée donc la fonction est executée puis le script chiffre le fichier **handler.py**
![script](https://github.com/fils07/RsFaasDescription/assets/59063893/b0d18c65-d4b9-4413-8ec4-7388e875eff8)

# Implementation de la solution
<img width="960" alt="image" src="https://github.com/fils07/RsFaasDescription/assets/59063893/a30d35f9-7cbd-4013-861f-38c3257a33e8">
Une fois que la requête est interceptée, la clé secrète est extraite et la fonction déchiffré avant d'être executée et le résultat renvoyé à l'utilisateur

# Démonstration  de la solution
https://drive.google.com/file/d/1RUE_rt7Io7wE9P7DyFARHQn2QY4bCHRA/view?usp=sharing


