<?php
//1) Connexion à la bdd
//défini les paramètres de connexion
define("DBHOST", "localhost");
define("DBUSER", "root");
define("DBPASSWORD", "root");
define("DBNAME", "tutosql");

//créer la connexion
$dsn = "mysql:host=".DBHOST.";dbname=".DBNAME;

//gestion des erreurs
try{
    $conn = new PDO($dsn, DBUSER, DBPASSWORD);
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    echo "Connexion réussie";
}catch(PDOException $e){
    echo "connexion refusé: " . $e->getMessage();
}

// Ecrire la requête pour charger 30 utilisateurs appartenant à la liste ID 4 ordonnés par nom d’utilisateur //Ex 1
$sql = "SELECT * FROM `UsersList` WHERE `listid` = :listid ORDER BY `UserName` LIMIT 30";

// Ecrire la requête pour charger 30 utilisateurs apYpartenant à la liste MYLIST (nom de la liste) ordonnés par nom d’utilisateur //Ex 2
$sql2 = "SELECT * FROM `UsersList` WHERE `list` =  'MYLIST' ORDER BY `UserName` LIMIT 30";

//On protege les paramètres et on prepare la requete
$query = $conn->prepare($sql); //EXercice 1
$query = $conn->prepare($sql2); //Exercice 2

$query->bindValue(":listid", 4, PDO::PARAM_INT); //Exercice 1

//On execute la requete
$query->execute();

//On recupere les donnees
$users = $query->fetchAll();

