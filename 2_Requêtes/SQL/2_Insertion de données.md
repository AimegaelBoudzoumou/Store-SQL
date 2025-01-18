# Produits


![Uploading image.png…]()

# Bundles
Le numéro de Bundle est généré par le SGBD :

```sql
select floor(dbms_random.value(1, 300)) from dual;

insert into t values (
    'pc portable',
    floor(dbms_random.value(7000000, 7999999))
);
```

# Gamme

## 1. Suite à l’arrivée de nouveau produits Apple, il faut créer une nouvelle gamme Apple (Mac Mini (M4))
