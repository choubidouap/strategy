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
--------
**Exemples 1**

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

```java
public class Classement {
     private TriStrategy methodeTri;
     int[] tableauClassement = new int[20];   
    
    public Classement(){}

    public void definirMethodeTri(TriStrategy  typeTriChoisi){
        this.methodeTri = typeTriChoisi;
    }
      
    public void trier(int[] tableau){
        methodeTri.trier(tableau);
    }

    void peuplerClassement(int maximum) {
        // peuple de chiffres aléatoires le tableau
        for ( int a = 0 ; a < this.tableauClassement.length ; a ++){
            this.tableauClassement[a] = (int)(Math.random()*maximum);
        }     
    }
    
}
```
L'interface ⤵️
```java
public interface TriStrategy {
    public int[] trier(int[] tableau);  
}
```

```java
import java.util.Arrays;
public class TriDecroissantConcreteStrategy implements TriStrategy{

    @Override
    public int[] trier(int[] tableau) {
        System.out.println("Tri décroissant");
        Arrays.sort(tableau);
        for(int i = 0; i < tableau.length / 2; i++)
        {
            int temp = tableau[i];
            tableau[i] = tableau[tableau.length - i - 1];
            tableau[tableau.length - i - 1] = temp;
        }     
        return tableau;
    }
}
```

```java
import java.util.Arrays;
public class TriCroissantConcreteStrategy implements TriStrategy {  
    @Override
    public int[] trier(int[] tableau) {
        System.out.println("Tri Croissant");
        Arrays.sort(tableau);
        return tableau;
    }
}
```


**Exemples 2**
> Dans ce programme, une personne peut se déplacer de plusieurs façon différentes.

```java
public class StrategyAeroport {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {

          // Création du contexte
          Personne personne1 = new Personne("AvecUnA", "kAren");
              
          // ici on défini la stratégie (le moyen de déplacement) à utiliser
          int a = 0 ;
          if (a == 1){
                personne1.choisirModeDeplacement(new EnVoitureConcreteStrategy());
          } else {
                personne1.choisirModeDeplacement(new EnAvionConcreteStrategy());
          }
          
          // L'appel sera toujours le même pourtant le code effectué derrière sera différent
          // (l'action sera toujours la même, mais la façon de la faire peut varier)
          personne1.seDeplacer();
   
          // création d'une nouvelle personne
          Personne personne2 = new Personne("Kostic", "Julien");
          personne2.choisirModeDeplacement(new EnVoitureConcreteStrategy());
          personne2.seDeplacer();
          
          // change le mode déplacement
          personne2.choisirModeDeplacement(new EnAvionConcreteStrategy());
          personne2.seDeplacer();
    } // end main
}

```

**On constate que nous appelons toujours la même méthode dans le main, cependant c'est un autre algorithme qui est utilisé.**

**Les projets et le pdf de ce documents sont sur le drive. Bises.**
