🍃 Strategy - Stratégie 🍃
--------
```java
La page est longue car à la fin il y a des exemples de codes.
```
**Intentions du pattern**
> Permettre la sélection d'un algortihme en fonction du besoin.

**Comment ?**
- Définition d'une famille d'algorithmes
- Encapsulation de ces algorithmes en tant qu'objets
- Rendre ces algorithmes interchangeables

- **Données intrinsèques**: dépendent de l'objet en question

- **Données extrinsèques**: ne dépendent pas de l'objet en question

**Quand utiliser ce design pattern ?**
> Lorsque que nous avons besoin de permuter dynamiquement entre algorithmes, il serait judicieux d'implémenter ce design pattern. 

**Application**
> Quelconque application proposant réalisation d'une tâche de différentes manières.

--------
**Diagramme de séquence**
![diagramme de séquence du poids mouche](https://image.noelshack.com/fichiers/2017/13/1490610078-strategysequencediagram.png)
-------
**Exemples**

Classement

> Ici il y aura plusieurs façon de trier un classement.

```java
import java.util.Arrays;
public class StrategyClassement {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
            // nouveau contexte (ici classement)
            Classement monClassement = new Classement();
            
            // peupler le classement en mentionnant le chiffre maximum
            monClassement.peuplerClassement(20);
            
            // définition de quel stratégie (ici méthode de tri) utiliser
            int i = 0;
            if( i < 1 ){
                monClassement.definirMethodeTri(new TriCroissantConcreteStrategy());
            } else {
                monClassement.definirMethodeTri(new TriDecroissantConcreteStrategy());
            }
            
            // Visualisation du tableau avant le tri
            System.out.println(Arrays.toString(monClassement.tableauClassement));
            // Tri du tableau en utilisant la stratégie définie plus haut
            monClassement.trier(monClassement.tableauClassement);
            // Visualisation du tableau après le tri
            System.out.println(Arrays.toString(monClassement.tableauClassement));
    } // end main
}
```

**Les projets et le pdf de ce documents sont sur le drive. Bises.**
