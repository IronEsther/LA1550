# Einführung

Die Aufgabe war es, mit `Robocode` einen eigenen Roboter zu programmieren, den wir dann gegen die anderen Roboter der Klasse kämpfen liessen. Der/Die Entwickler/In des besten Roboters hat dann einen kleinen Preis bekommen. Die Regeln sind des Kampfes klar vorgegeben: Man hat Energie, welche das Leben darstellt und gleichzeitig auch beim Schiessen auf andere gebraucht werden konnte, um mehr Schaden zu machen. Jeder Roboter hat einen Radar und eine Kanone. Diese sind genauso wie der Roboter beweglich. Der Roboter wird nicht von einer Person gesteuert, sondern nur vom Code, welcher während dem Kampf abläuft.

In diesem Portfolio-Eintrag werde ich Ihnen zeigen, was mein Roboter alles kann und was meine Strategie für mein Roboter ist.

**Ziele:**

* Dem Leser erklären, was `Robocode` ist.
* Meine Strategie von meinem Roboter dem Leser erklären und es durch verschiede Medien zeigen.

**Was ist `Robocode`?**

`Robocode` ist ein Programmierspiel, bei dem es darum geht, einen Kampfroboter zu programmieren, der in einer Kampfarena gegen andere Roboter antritt. Der Name `Robocode` ist also die Abkürzung für "Robot code". Der Spieler ist der Programmierer des Roboters und hat keinen direkten Einfluss auf das Spielgeschehen. Stattdessen muss der Spieler die KI des Roboters in Java oder .Net schreiben und ihm sagen, wie er sich verhalten und auf Ereignisse in der Kampfarena reagieren soll. Die Kämpfe finden in Echtzeit und auf dem Bildschirm statt.

Es gibt eine [Robocode-Website](https://robocode.sourceforge.io), auf welcher man alles über Robocode erfahren kann. Es gibt ebenfalls Hilfestellungen für C# und Java sowie alle Dateien zum Herunterladen.

# Meine Idee zu meinem Roboter

Am Anfang hatte ich keine 'richtige' Strategien, sondern habe die vorgegebenen Roboter analysiert und ihre Techniken versucht zu verstehen. Einer der Roboter hat mir am meisten gefallen: der Tracker. Der Tracker versucht ein Ziel zu verfolgen und ihn danach zu eliminieren. Ich habe viele Strategien dazu ausgedacht, jedoch hatte ich Probleme bei der Umsetzung, da ich einige Codes nicht wusste und deshalb Codes vom Internet kopiert habe. Dies hat mein Roboter ziemlich kaputt gemacht und ist dann nicht so gut gelaufen. 

Deshalb habe ich wieder einen neuen Roboter und eine neue Strategie erstellt. Diese war meine schlussendliche Strategie:

* Der Roboter sollte zuerst, wenn es viele Gegner hat, im Ecken gehen und dort bleiben.
* Wenn es wenige Gegner hat, dann sollte der Roboter aus dem Ecken gehen und andere Roboter angreifen.
* Wenn der Roboter fast keine Energie hat, sollte er wieder im Ecken gehen und sich regenerieren.

Um die Strategie zu veranschaulichen, füge ich hier ein kleines Video hinzu: 

https://user-images.githubusercontent.com/89132005/151148768-87d62283-3218-4b20-9c7a-aa2c9867a55d.mp4

In diesem Video sieht man, dass der Roboter in den Ecken geht und von dort die Roboter abschiesst. Da die Roboter hier sich nicht bewegt haben, war die Strategie ziemlich einfach, um zu gewinnen. Jedoch war diese Situation im echten Kampf nicht so, da die Roboter da sich bewegten. Dabei hatte ich Probleme und habe mein Roboter so programmiert, dass er dann andere angreift. Hier zeige ich Ihnen einen Auschnitt von diesem Teil:

```java
while (true) {
	if (others < 10){
		ahead(500); // Move ahead 500
		turnRight(200);
		turnGunRight(360); // Spin gun around
		back(200); // Move back 200
		turnGunRight(360); // Spin gun around
		turnLeft(200);
	}
	else if (others > 10) {
		if(robotX > fieldWidth/2) {
			turnTo(90);
			position = 1;
	} else {
		turnTo(-90);
		position = 3;
	}

	// Robot main loop
	int scanStart = -1;
	while(true) {
		ahead(100);		
		if (scanStart == -1) {
			turnGunLeft(360);
		} else {
			turnGunTo(scanStart);
			turnGunLeft(90);
		}
		out.println(position);

		switch (position) {
			case 1:	scanStart = -90;
				break;
			case 2:	scanStart = 0;
				break;
			case 3:	scanStart = 180;
				break;
			case 4:	scanStart = 90;
				break;
		}	
	}
}
```

Hier wird gezeigt, dass wenn es weniger als zehn Gegner hat, dann sollte der Roboter ins Feld fahren. Dies hat zum Glück ziemlich gut funktioniert, jedoch ist der Roboter manchmal einfach stehen geblieben.

# Verifikation und Reflexion

**Verifikation:**

* Ziel 1: Im Abschnitt '**Was ist `Robocode`?**' habe ich dem Leser erklärt, was `Robocode` ist.
* Ziel 2: Im Abschnitt 'Meine Idee zu meinem Roboter' habe ich dem Leser erklärt, was mein Roboter tut.

**Reflexion:**

Am Anfang hatte ich ein bisschen Mühe mit dem Herunterladen der `Robocode`-Applikation. Die Datei wollte sich bei mir nicht öffnen. Jedoch nach dem zweitem Herunterladen ging es und ich konnte mit dem Programmieren anfangen. Am Anfang vom Projekt habe ich ein bisschen ausprobiert, wie das Programm so läuft. Da das Programm kein Debugging hatte, musste ich mit `Compiling` die Fehler suchen und diese auflösen. Dies hat mir ein bisschen Probleme bereitet.

Da Java ähnlich wie C# ist, was wir kürzlich gelernt haben, hatte ich während dem Programmieren nicht viel Mühe gehabt, um den Code zu verstehen und auszuführen. 

Da dieses Projekt nicht wie das letzte Projekt eine Einzelarbeit war, konnte ich diesmal meine Ziele nicht so gut ausführen, wie zum Beispiel *ich sollte nächstes Mal mehr mit meinen Teamkamaraden kommunizieren.* 

Jedoch steht bei mir der Verbesserungsvorschlag für dieses Projekt fest: 

*Ich habe manchmal viel zu lange gewartet bis ich Herrn Colic (unser Informatiklehrer) um Hilfe gebeten habe, und dieser hatte dann meistens viel zu tun und konnte mir nicht direkt helfen, was dazu geführt hatte, dass ich manchmal sehr wenig arbeiten konnte und nicht gerade produktiv war.*
