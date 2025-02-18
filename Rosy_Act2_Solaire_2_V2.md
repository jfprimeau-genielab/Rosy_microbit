# Rosy, Activité 2.2 : Gestion de l'énergie

## Étape 1 @showdialog

Dans cette activité, nous allons découvrir comment **diriger** l'électricité vers différents systèmes en fonction de l'énergie disponible.

Selon l'énergie générée par le panneau solaire, nous pourrons faire **allumer** différentes lumières qui seront alimentées directement par le panneau solaire.

<img alt="Résultat attendu de l'activité : le micro:bit affiche le niveau de tension électrique généré par le panneau solaire." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gifactivite2a_v3.gif" width="300px">


## Étape 3

Il ne reste qu'à **programmer** le micro:bit.

Nous voulons faire **allumer** les DELs en fonction de la **lumière reçue** par le panneau solaire :

- Très peu de lumière : **aucune** lumière allumée
- Peu de lumière : lumière **rouge** allumée
- Beaucoup de lumière : lumière **verte** allumée

Nous allons repartir du code précédent.
Vous pouvez le revoir **en cliquant** sur **l'ampoule** dans le cercle bleu.

***Assurez-vous*** que le capteur infrarouge ne soit pas inséré.

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
    led.plotBarGraph(
    volts,
    3.3
    )
    )
```


## Étape 4

**Ajouter** au code existant un bloc ``||logic:si <vrai>...sinon||`` de la section ``||logic:Logique||``.

> ***Astuce 1*** *: N'hésitez pas à déplacer les blocs sur la surface de programmation pour mieux voir votre code.*

> ***Astuce 2*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 9." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gif1Act2b.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
    led.plotBarGraph(
    volts,
    3.3
    )
    if (true) {

    } else {

    }
})
```

## Étape 5

Nous voulons que le programme agisse différemment **selon la tension électrique** détectée.

1. **Remplacer** ``||logic:<vrai>||`` par un bloc ``||logic: > || `` (plus grand que) . 
2. Dans sa case de gauche, **ajouter** la variable ``||variables:volts||``.
3. Dans la case de droite, **écrire** le nombre "2.1".

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 10." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gif2Act2b.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {

    } else {

    }
})
```

## Étape 6

Pour la plage **plus grande que 2.1 volts**, nous allons faire allumer la DEL verte et nous assurer que la DEL rouge est éteinte.

1. Dans le crochet directement sous ``||logic:si||``, **Ajouter** 2 fois ``||pins:écrire sur la broche||``qui se trouve dans la section ``||pins:Broches||`` du menu "**Avancé**".
2. Dans le premier, **choisir** la broche ``||pins:P8||``, et **inscrire** le nombre **1**.
3. Dans le second, **choisir** la broche ``||pins:P2||``, et **inscrire** le nombre **0**.


<img alt="Animation de l'assemblage des blocs de programmation de l'étape 11." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gif3Act2b.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(DigitalPin.P8, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
    } else {

    }
})
```

## Étape 7

Nous voulons maintenant **déterminer** ce qui va se passer si le courant est plus petit ou égal à 2.1v, mais plus grand que 1.2v.

> ***Astuce*** *: Faire clic droit sur un bloc et sélectionner **Dupliquer** permet de gagner beaucoup de temps !*

1. **Cliquer** sur le symbole ``||logic:+||`` en bas du bloc ``||logic:si < >...sinon||`` pour ajouter un ``||logic:sinon...si||``.
2. **Lui ajouter** un bloc ``||logic:<> et <>||``.
3. Dans sa case de gauche, **ajouter** un bloc de ``||logic:Logique||`` avec la variable ``||variables:volts||`` à gauche, le symbole ``||logic:≤||`` (plus petit ou égal), dans la case de droite, **écrire** le nombre "**2.1**".
4. Dans sa case de droite, **ajouter** un bloc de ``||logic:Logique||`` avec la variable ``||variables:volts||`` à gauche, le symbole ``||logic:>||`` (plus grand que), dans la case de droite, **écrire** le nombre "**1.2**".

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 12." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gif4Act2bV2.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(DigitalPin.P8, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
    } else if (volts <= 2.1 && volts > 1.2) {

    } else {

    }
})
```

## Étape 8

Si la tension électrique détectée est entre 2.1v et 1.2v, seule la DEL rouge s'allumera.

1. Dans le crochet directement sous ``||logic:si||``, **ajouter** 2 fois ``||pins:écrire sur la broche||``.
2. Dans le premier, **choisir** la broche ``||pins:P8||``, et **inscrire** le nombre **0**.
3. Dans le second, **choisir** la broche ``||pins:P2||``, et **inscrire** le nombre **1**.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 13." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gif5Act2b.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(DigitalPin.P8, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
    } else if (volts <= 2.1 && volts > 1.2) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        pins.digitalWritePin(DigitalPin.P8, 0)
    } else {

    }
})
```

## Étape 9

Finalement, dans le crochet ``||logic:sinon||``, mettre 2 fois ``||pins:écrire sur la broche||``.

1. Dans le premier, **choisir** la broche ``||pins:P8||``, et **inscrire** le nombre **0**.
2. Dans le second, **choisir** la broche ``||pins:P2||``, et **inscrire** le nombre **0**.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 14." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gif6Act2b.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(DigitalPin.P8, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
    } else if (volts <= 2.1 && volts > 1.2) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        pins.digitalWritePin(DigitalPin.P8, 0)
    } else {
        pins.digitalWritePin(DigitalPin.P8, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
    }
})
```

## Étape 10
Il faut maintenant activer la broche 1 ou les DELs ne s'allumeront pas.  

1. Dans le bloc ``||basic:au démarrage|| `` y glisser ``||pins:écrire sur la broche||``.
2. **Choisir** la broche ``||pins:P1||``, et **inscrire** le nombre **1**.


<img alt="Animation de l'assemblage des blocs de programmation de l'étape 9." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RosyAct2_2E9_2.gif" width="80%">

```blocks
let solaire = 0
let volts = 0

pins.digitalWritePin(DigitalPin.P1, 1)

basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(DigitalPin.P8, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
    } else if (volts <= 2.1 && volts > 1.2) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        pins.digitalWritePin(DigitalPin.P8, 0)
    } else {
        pins.digitalWritePin(DigitalPin.P8, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
    }
})

```

## Étape 11

Il ne reste qu'à **téléverser** le code sur le micro:bit, et vous êtes prêt·e.

Si vous avez besoin de vous rafraîchir la mémoire au sujet du téléversement du code, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 12

Voilà ! Nous avons maintenant un système qui **réagit en fonction du courant disponible** fourni par le panneau solaire !

Pour aller plus loin, vous pouvez cliquer sur le bouton **Terminer** à droite de ce texte pour avoir accès à tous les blocs. Voici quelques idées :

- Changer les valeurs dans la section ``||logic:si < >...sinon||`` pour que le circuit réagisse mieux aux conditions dans lesquelles vous vous trouvez.
- Faire activer différentes animations à l'écran du micro:bit selon la tension électrique détectée.
- Utiliser les capteurs du micro:bit comme le thermomètre ou la boussole en combinaison avec la tension électrique générée par le panneau solaire.
