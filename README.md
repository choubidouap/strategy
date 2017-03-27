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

** Quand utiliser ce design pattern ?**
> Lorsque que nous avons besoin de permuter dynamiquement entre algorithmes, il serait judicieux d'implémenter ce design pattern. 

** Application **
> Quelconque application proposant réalisation d'une tâche de différentes manières.

** Diagramme de séquence **
![diagramme de séquence du poids mouche](https://image.noelshack.com/fichiers/2017/13/1490610078-strategysequencediagram.png)

Exemple: **Les Strings**
> C'est typiquement ce qu'il arrive avec les objets String. Je pense que nous sommes d'accord sur le fait que deux variables contenant la même String (même suite de caractère) pointent sur le même objet String.
```java
public class PoidsMoucheString {
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        
        String s1 = "test";
        String s2 = "foo";

       // Affichage
        System.out.println(s1 + " hashcode : " + s1.hashCode() );
        System.out.println(s2 + " hashcode : " + s2.hashCode() );

       System.out.println("##################");

       // On change ici la valeur de la chaîne
        s2 = "test"; // on assigne "test" à la variable s2
        System.out.println(s1 + " hashcode : " + s1.hashCode() );
        System.out.println(s2 + " hashcode : " + s2.hashCode() );
        // On se rend compte que les 2 variables pointent sur le même objet 
    }   
}
```

**Quand utiliser ce design pattern ?**
- Lorsque nous avons beaucoup d'objets dans notre application.

- Lorsque les coûts en stockage sont élevés.

- Les objets possèdent des mêmes caractéristiques. (ils pourront donc se partager des données)

- L'application n'a pas besoin d'objet unique.

- **‼️ Ne pas utiliser si l'information partagée peut varier à travers le temps ‼️** 

--------

**Diagramme de séquence**
![diagramme de séquence du poids mouche](https://image.noelshack.com/fichiers/2017/13/1490603635-flyweight.png)

--------


**Les projets et le pdf de ce documents sont sur le drive. Bises.**
