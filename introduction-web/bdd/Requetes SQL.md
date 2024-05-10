# Requetes SQL

[SQL.SH](https://sql.sh)

Les requêtes SQL sont des commandes utilisées pour interagir avec des bases de données relationnelles. Voici un résumé succinct des types de requêtes les plus courantes :

1. **SELECT :** Utilisé pour extraire des données d'une table ou d'une vue.

   ```sql
   SELECT colonnes FROM table WHERE condition;
   ```

2. **INSERT :** Insère de nouvelles lignes de données dans une table.

   ```sql
   INSERT INTO table (colonne1, colonne2) VALUES (valeur1, valeur2);
   ```

3. **UPDATE :** Modifie des données existantes dans une table.

   ```sql
   UPDATE table SET colonne = nouvelle_valeur WHERE condition;
   ```

4. **DELETE :** Supprime des lignes de données d'une table.

   ```sql
   DELETE FROM table WHERE condition;
   ```

5. **JOIN :** Combine des données de deux tables basé sur une condition de jointure.

   ```sql
   SELECT t1.colonne, t2.colonne FROM table1 t1 JOIN table2 t2 ON t1.clé = t2.clé;
   ```

6. **GROUP BY :** Regroupe les résultats basé sur une ou plusieurs colonnes.

   ```sql
   SELECT colonne, COUNT(*) FROM table GROUP BY colonne;
   ```

7. **ORDER BY :** Trie les résultats par ordre croissant ou décroissant.

   ```sql
   SELECT colonnes FROM table ORDER BY colonne ASC/DESC;
   ```

8. **DISTINCT :** Sélectionne des valeurs uniques dans une colonne.

   ```sql
   SELECT DISTINCT colonne FROM table;
   ```

9. **WHERE :** Filtre les résultats basé sur une condition.

   ```sql
   SELECT colonnes FROM table WHERE condition;
   ```

10. **LIMIT :** Restreint le nombre de lignes retournées dans le résultat.
    ```sql
    SELECT colonnes FROM table LIMIT nombre;
    ```

Ces commandes de base permettent de manipuler les données dans une base de données relationnelle en utilisant le langage SQL (Structured Query Language).

- **OPERATEUR DE COMPARAISON :**

| Opérateur   | Description                |
| ----------- | -------------------------- |
| =           | Égalité                    |
| <>          | Différent de               |
| !=          | Différent de (alternative) |
| <           | Inférieur à                |
| <=          | Inférieur ou égal à        |
| >           | Supérieur à                |
| >=          | Supérieur ou égal à        |
| BETWEEN     | Entre deux valeurs         |
| LIKE        | Correspondance partielle   |
| IN          | Appartenance à un ensemble |
| IS NULL     | Est nul                    |
| IS NOT NULL | N'est pas nul              |
