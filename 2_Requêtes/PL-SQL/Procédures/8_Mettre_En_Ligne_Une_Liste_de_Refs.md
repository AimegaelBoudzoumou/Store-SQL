# Activer une liste de réf non visibles sur le web :
Ecrire une procédure qui reçoit une liste de réfs internes.

Note : Apercevoir la liste avant de lancer la procédure 

Pour chaque réf, mettre à 1 le champ « visibilité web »

Note : Apercevoir la liste après avoir lancé la procédure 

Create or replace procedure procedure_name (liste_de_refs_internes)
Declare
/*traitement du fichier en pièce jointe afin de récupérer les réfs internes dans une liste nommée Liste_de_refs_internes */
Liste_de_refs_internes …
Etat_visibilite_web g_produits.visibilite_web%TYPE ;
Begin
For une_ref IN Liste_de_refs_internes
Loop
 Select visibilité_web 
 Into Etat_visibilite_web
 From g_produits where …

 If Etat_visibilite_web = 0 Then
 Update 
End loop ;


End ;
/

OU

For ref_interne IN (select ref from g_produits where marque=’…’ and gamme = ‘…’)
Loop
…
End loop ;
