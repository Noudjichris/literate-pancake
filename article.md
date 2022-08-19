Dans cet article, nous parlerons de la gestion des exceptions en python. Nous parlerons des exceptions en quelques lignes des sujets suivants :

- Assertion
- Exception
- Try finally
- Argument d’une exception
- Lever une Exception
- Et des Exceptions définies par l’utilisateur 

Python fournit deux fonctionnalités très importantes pour gérer toute erreur inattendue dans votre Programme et d’y ajouter des capacités de débogage

- Assertions
- Gestion des exceptions.

Voici une liste des exceptions standards disponibles en Python.

- **Exception** : Classe de base pour toutes les exceptions
- **StopIteration** : Déclenché lorsque la méthode next() d’un itérateur ne pointe pas vers n’importe quel objet.
- **SystemExit** : Déclenché par la fonction sys.exit().
- **StandardError** : Classe de base pour toutes les exceptions intégrées, à l’exception de StopIteration et SystemExit.
- **ArithmeticError** : Classe de base pour toutes les erreurs qui se produisent pour le calcul numérique.
- **OverflowError** : Déclenché lorsqu’un calcul dépasse la limite maximale pour un numérique type.
- **FloatingPointError** : Déclenché lorsqu’un calcul en virgule flottante échoue.
- **ZeroDivisonError** : Augmenté lorsque la division ou modulo par zéro a lieu pour tous types numériques.
- **AssertionError** : Soulevé en cas d’échec de l’instruction Assert.
- **AttributeError** : Soulevé en cas d’échec de la référence ou de l’affectation d’attribut.
- **EOFError** : Déclenché lorsqu’il n’y a pas d’entrée de la part de raw\_input() ou input() et la fin du fichier est atteinte.
- **ImportError** : Déclenché lorsqu’une instruction import échoue.
- **keyboardInterrup** : Déclenché lorsque l’utilisateur interrompt l’exécution du programme, généralement par appuyez sur Ctrl+c.
- **LookUpError** : Classe de base pour toutes les erreurs de recherche.
- **IndexError** : Déclenché lorsqu’un index est introuvable dans une séquence.
- **KeyError**: Raised when the specified key is not found in the dictionary;
- NameError : Déclenché lorsqu’un identificateur est introuvable dans le local ou l’espace global de noms.
- **UnboundLocalError** : Déclenché lorsque vous essayez d’accéder à une variable locale dans une fonction ou mais aucune valeur ne lui a été attribuée.
- **EnvironmentError** : Classe de base pour toutes les exceptions qui se produisent en dehors de Python environnement.


**Assertion**

Une assertion est une vérification du code que vous pouvez activer ou désactiver lorsque vous terminez de tester vos programmes.

- La façon la plus simple de penser à une assertion est de la comparer à une déclaration raise-if. Une expression est testée, et si le résultat apparaît faux, une exception est soulevée.
- Les assertions sont effectuées par l’instruction assert, le mot-clé le plus récent de Python, introduit dans la version 1.5.
- Les programmeurs placent souvent des assertions au début d’une fonction pour vérifier leur validité entrée, et après un appel de fonction pour vérifier la sortie valide.

**La déclaration Assert**

Lorsqu’il rencontre une instruction assert, Python évalue l’expression qui l’accompagne, ce qui, espérons-le, est vrai. Si l’expression est fausse, Python déclenche une exception AssertionError.

La syntaxe de assert est :

**assert Expression[, Arguments]**

Si l’assertion échoue, Python utilise ArgumentExpression comme argument pour le AssertionError. Les exceptions AssertionError peuvent être interceptées et gérées comme n’importe quelle autre exception, à l’aide de l’instruction try-except. S’ils ne sont pas traités, ils mettront fin aux programmes et produire un traçage.

Exemple : 

def KelvinAFahrenheit(Temperature):

assert (Temperature >= 0)," Plus froid que le zéro absolu!"

return ((Temperature-273)\*1.8)+32

print (KelvinAFahrenheit(273))

print (int(KelvinAFahrenheit(505.78)))

print (KelvinAFahrenheit(-5))

Voici une fonction qui convertit une température donnée de degrés Kelvin en degrés Fahrenheit. Étant donné que 0° K est aussi froid que possible, la fonction se sauve si elle voit une température négative

En exécutant ce code on obtient : 

*32.0*

*451*

*Traceback (most recent call last):*

*File "test.py", line 6, in*

*print KelvinAFahrenheit(-5)*

*File "test.py", line 4, in KelvinTAFahrenheit*

*assert (Temperature >= 0)," Plus froid que le zéro absolu!"*

*AssertionError: Plus froid que le zéro absolu!*

**Qu’est-ce qu’une exception :** 

Une exception est un événement qui se produit pendant l’exécution d’un programme qui perturbe l’exécution normale des instructions du programme. En général, lorsqu’un code Python rencontre une situation à laquelle il ne peut pas faire face, il soulève une exception. Une exception est un objet Python cela représente une erreur.

Lorsqu’un code Python déclenche une exception, il doit gérer l’exception immédiatement sinon, il se termine et se ferme.

Si vous avez un code qui peut déclencher une exception, vous pouvez le protéger des erreurs en plaçant le code dans un bloc try:. Après l’essai : bloquer, inclure une instruction except: , suivie d’un bloc de code qui gère le problème avec autant d’élégance dans la mesure du possible.

La syntaxe est : 

Try :

`	`Code à exécuter…

except Exception:

`	`S’il y’a une exception, exécuter le code

Voici quelques points importants sur la syntaxe mentionnée ci-dessus

- Une seule instruction try peut avoir plusieurs instructions except. Ceci est utile lorsque le bloc try contient des instructions qui peuvent lever différents types d’exceptions.
- Vous pouvez également fournir une clause d’exception générique, qui gère toute exception.

**The try-finally Clause**

Vous pouvez utiliser un bloc finally: avec un bloc de try:,  Le bloc  finally: est un endroit à mettre tout code qui doit s’exécuter, que le bloc try ait soulevé une exception ou non. La syntaxe de la déclaration try-finally est la suivante :

try:

Code à executer;

finally:

Ce code va toujours s’exécuter.

**Exemple :** 

try:

fh = open("testfile", "w")

fh.write("Ceci est un code mon fichier pour essayer l’exception!!")

finally:

print ("Erreur : Ne peut pas lire ce fichier")

fh.close()

Si vous n’êtes pas autorisé à ouvrir le fichier en mode écriture, cela produira le résultat suivant : « Erreur : Ne peut pas lire ce fichier »

**Argument d’une exception**

Une exception peut avoir un argument, qui est une valeur qui donne des informations supplémentaires sur le problème. Le contenu de l’argument varie selon l’exception. Vous obtenez un argument de l’exception en fournissant une variable dans la clause except comme suit :

try:

Code à executer

except ExceptionType as Argument:

Vous pouvez executer la Valeur comme argument ici...

Si vous écriviez le code pour gérer une seule exception, vous pouvez faire en sorte qu’une variable suive le nom de l’exception dans l’instruction except. Si vous piégez plusieurs exceptions, vous pouvez avoir une variable qui suit le tuple de l’exception.

Cette variable reçoit la valeur de l’exception contenant principalement la cause de l'exception. La variable peut recevoir une ou plusieurs valeurs sous la forme d’un tuple. Ce tuple contient généralement la chaîne d’erreur, le numéro d’erreur et un emplacement d’erreur.

def convertir(var):

try:

return int(var)

except ValueError as Argument:

print("Cet argument ne contient pas un chiffre \n", Argument)

**Lever une Exception :**

Vous pouvez lever des exceptions de plusieurs manières à l’aide de l’instruction raise. La syntaxe générale pour la déclaration d’augmentation est la suivante :

raise [Exception [, args [, traceback]]]

Ici, Exception est de type d’exception (par exemple, NameError) et l’argument est un l’argument d’exception. L’argument est facultatif ; s’il n’est pas fourni, l’argument n’existe pas.

Le dernier argument, le traçage, est également facultatif (et rarement utilisé dans la pratique), et s’il est présent, il sera l’objet de traçage utilisé pour l’exception.

Exemple : Une exception peut-être une chaîne, une classe ou un objet. La plupart des exceptions que Python lève sont des classes, avec un argument qui est une instance de la classe. L’exemple suivant illustre l’utilisation de l’élévation d’une exception :

def NomFonction( n ):

if n <1:

raise Exception(n)

\# Le code ci-dessous ne va être executé 

\# si l’exception est lévé

return n

try:

l= NomFonction (-10)

print ("n=",l)

except Exception as e:

print ("Erreur en n argument",e.args[0])

Cela produira le de résultat suivant :

Erreur en n argument -10

**Exceptions définies par l’utilisateur**

Python vous permet également de créer vos propres exceptions en dérivant des classes de la norme des exceptions intégrées.

Voici un exemple lié à RuntimeError. Ici, une classe est créée qui est sous-classée à partir de RuntimeError. Ceci est utile lorsque vous devez afficher des informations plus spécifiques lorsqu’une exception est détectée.

Dans le bloc try, l’exception définie par l’utilisateur est déclenchée et interceptée dans le bloc except. La variable e est utilisée pour créer une instance de la classe Networkerror.

class Networkerror(RuntimeError):

def \_\_init\_\_(self, arg):

self.args = arg

Ainsi, une fois que vous avez défini la classe ci-dessus, vous pouvez lever l’exception comme suit :

try:

raise Networkerror("mauvais nom de l’hôte ")

except Networkerror,e:

print e.args
