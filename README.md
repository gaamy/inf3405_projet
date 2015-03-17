# inf3405_projet
Projet d'interaction server client pour une application électoral


TP4 : Projet
Système de vote
1. Informations générales
Session
Hiver 2015
Public cible
Étudiants de 1er cycle
Pondération
10%
Lieu de réalisation
L-4708
Taille des équipes
2 étudiants
Date de début du projet
10 mars 2015
Date de remise du projet
1 Avril 2015 (23h55 au plus tard)
Directives particulières
 Tout rapport sera pénalisé de 5 points s’il est soumis par une équipe dont la taille est différente de deux (02 étudiants), sans l’approbation préalable du chargé de laboratoire.
 Soumission par moodle uniquement (http://moodle.polymtl.ca).
 Soumission d’une archive compressée contenant le rapport et le code source de l’application.
 Toute soumission de rapport en retard est pénalisée à raison de 3 points par jour de retard.  Programmation C++ avec Visual Studio 2013.
Auteurs
Aurel RANDOLPH & Éric FAFOLAHAN
Chargé de laboratoire
Éric FAFOLAHAN(eric.fafolahan@polymtl.ca)
2. Connaissances requises
 Sockets
 Threads
 Programmation C++
 Bibliothèque Winsock
3. Objectifs du laboratoire
L’objectif de ce laboratoire est de familiariser l'étudiant:
 aux échanges Client / Serveur en utilisant les sockets en mode connecté;
 au développement « d’applications réseau » en utilisant les threads.
École Polytechnique de Montréal
Département Génie Informatique et Génie Logiciel
INF3405 – Réseaux Informatiques
2
4. Description
L'application à développer comprend un serveur et un client, utilisés dans le cadre d'un processus électoral. Le processus électoral simulé dans ce projet met en contexte un électeur (client), un serveur de vote (serveur), une liste de candidats, une durée de scrutin. Chaque électeur se connecte au serveur, prend connaissance du bulletin de vote à travers une liste de candidats que lui transmet le serveur, exprime son vote puis se déconnecte. La liste des candidats vous est fournie. L'expression du vote consiste à choisir un candidat dans la liste et à transmettre ce choix au serveur. Le serveur comptabilise au fur et à mesure, le nombre d’électeurs, le nombre de votes valides et invalides ainsi que le score de chaque candidat. A la fin du scrutin (expiration de la durée de vote), le serveur proclame les résultats en affichant les statistiques du vote : le nombre total d’électeurs, le nombre de votes valides, ainsi que le score obtenu par chaque candidat.
Au démarrage du scrutin, le décompte de la durée du vote est lancé dès la réception du premier électeur. A l’expiration du délai, le scrutin est clos et aucune nouvelle connexion n’est acceptée par le serveur. Cependant, tout processus de vote commencé avant l’expiration du délai est poursuivi jusqu’à son terme. Le serveur écoute un seul port (dans la plage 5000 à 5050 inclusivement) et prend en charge plusieurs électeurs à la fois.
Le programme client et le programme serveur ne sont pas exécutés sur la même machine et plusieurs clients peuvent tenter d’accéder au même serveur de vote. Cependant, chaque client connaît d’avance l'adresse IP du serveur ainsi que le numéro de port écouté. Durant le scrutin, le serveur garde un journal des électeurs qui ont voté : adresse IP, port utilisé, horodatage (correspond à date - en heure minute et seconde - de réception du vote de l'électeur), statut du vote (valide ou invalide).
5. Requis fonctionnels
La liste des candidats est un fichier texte au format (.txt). Le serveur doit au lancement, lire le fichier contenant la liste des candidats. Les fonctionnalités attendues sont indiquées comme suit : La Figure 1 montre la séquence d'exécution des principales actions.
 Serveur (serveur.cpp)
 Ouverture du vote : A cette étape, le serveur se met en mode écoute sur le port sélectionné et prêt à lancer le décompte du scrutin dès la réception du premier électeur.
3
 A chaque requête de connexion au port écouté, transmettre la liste des candidats au client (électeur).
 Recevoir et comptabiliser le vote d'un électeur.  Tenir un journal des électeurs. Il s'agit d'un fichier nommé journal au format .txt édité par le serveur.
 Fermeture du vote. (A l’expiration du temps alloué au vote, plus aucune connexion n'est acceptée.)
 Afficher les statistiques du scrutin.
 Electeur (electeur.cpp)
 Saisir au clavier de l'adresse IP du serveur et le port sur lequel le vote sera fait.
 Vérifier la validité de l’adresse IP saisie et le numéro de port.
 Se connecter au serveur.
 Réceptionner la liste des candidats.
 Choisir un candidat.
 Transmettre son vote au serveur.
 Se déconnecter.
Figure 1 : Séquence d'exécution des principales actions
4
6. Livrable
6.1. Soumission
Le livrable est une archive (ZIP ou RAR) dont le nom est formé des numéros matricules des membres de l'équipe, séparé par un trait de soulignement ( _ ). Votre archive contiendra les fichiers suivants:
 les fichiers .cpp;
 les fichiers .h le cas échéant;
 le rapport au format PDF ou Word
L'archive ne doit pas contenir de programme exécutable, de fichier de projet ou solution de Visual Studio, de répertoire Debug ou Release, etc. Les fichiers .cpp et .h suffiront pour l'évaluation du travail. Le nom respect de cette consigne pourrait entrainer une pénalité de 3 points.
6.2. Rapport
Le rapport doit comporter les éléments suivants :
 Page présentation qui doit contenir Le nom ou le logo de l’école, le libellé et l'identifiant du cours, la session, le numéro et l’identification du projet, la date de remise, les matricules et noms des membres de l’équipe, la mention « Soumis à : nom et prénoms du chargé de laboratoire ». Vous pouvez compléter la page présentation qui vous est fournie.
 Introduction avec vos propres mots pour mettre en évidence le contexte et les objectifs du TP.
 Présentation de vos travaux. Une explication de votre solution mettant en lumière la prise en compte des principaux requis du système.
 Difficultés rencontrées lors de l’élaboration du TP et les éventuelles solutions apportées.
 Critiques et Améliorations : Il serait intéressant d’inclure vos suggestions pour améliorer le laboratoire.
 Conclusion : Expliquez en quoi ce laboratoire vous a été utile, ce que vous avez appris, si vos attentes ont été comblées, etc.
7. Évaluation
Evaluation de l’exécutable
6
Evaluation de l’implémentation : passage d’arguments, gestion adéquate des variables et de toute ressource (création, utilisation, libération), gestion des erreurs, , logique de développement, documentation du code, etc.
8
Rapport
6
Total de points
20
