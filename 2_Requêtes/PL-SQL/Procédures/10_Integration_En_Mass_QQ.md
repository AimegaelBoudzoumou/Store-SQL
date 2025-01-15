Intégration en masse :

For ref in (select ref_interne from g_produits where fabricant = ‘Apple’ and (gamme =’iPhone 16’ or gamme =’iPhone 16 Plus’ or gamme = ‘iPhone Pro’ or gamme = ‘iPhone Pro Max’)

Loop
…
End loop ;

For ref in (select ref_interne from g_produits where marque = ‘Apple’ and (gamme in (‘iPhone 16’, ’iPhone 16 Plus’, ‘iPhone Pro’, ‘iPhone Pro Max’)
