###### Visa och förklara villoren för "hold and wait" samt "cirkular wait" med en korrekt resursallokeringsgraf.


#### Resursallokeringsgraf

![Resursallokeringsgraf](http://i.imgur.com/QfQJcAOl.jpg)


###### Namnge och förklara de övriga båda villkoren.

### Preventing

#### Prevention

  * numrerade resurser
  * får bara ha en grej
  * preemtion

#### Avoidence

  * Bankers eller annan

#### Detection

  * Algoritm tex bankers
  * Resursallokeringsgraf

## Det finns fyra villkor som måste var uppfyllda för att ett deadlock ska uppstå

### Vilka är dessa villkor ?

#### Mutal Exclusion
  * Detta innebär att ett program som har en delad/gemensam resurs endast tillåter em tråd åt gången att komma åt denna resurs.

#### Hold & Wait
  * En tråd som har en resurs väntar på att få tillgång till någon annan resurs

#### No preemtion for resources
  * En resurs som hålls av en tråd kan endast lämnas tillbaka frivilligt av den tråd som håller i resursen. Inen annan tråd kan stjäla eller på annant sätt tvinga sig till resursen.

#### Circular Wait - Om tråd (1) håller i resurs [a] och väntar på resurs [b] samtidigt som tråd (2) håller i resurs [b] och väntar på resurs [c] pcj väntar på resurs [a] så uppstår circular wait, alltså att trådarna blockerar varandra cirkulärt.

### Vilka av dessa villkor bryter Bankers algorithm ? På vilket sätt ?

#### Bankers bryter cirkular wait, detta genom att räkna ut antalet resurser som används av de trådar som körs. = inga cirkulera grafer.


## Förklara busy-wait ?
#### Busy-Wait uppstår när processorn förhindras fortsätta exekviera något meningsfillt genom till exempel en tom while-loop. Processorn kommer att fastna i loopen tills det att en annan tråf t. ex. tilldelar en variabel så att villkoret i while loopen blir falsk och då kan fortsätta exekveringen.

## Bankers

![Bankers](http://i.imgur.com/mYvqpQ5l.jpg)
