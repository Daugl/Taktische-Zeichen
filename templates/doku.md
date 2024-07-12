Nutzung der Templates am Beispiel eines Feuerwehrbootes ZBV:

{% extends "templates/base.j2t" %}
{%- block symbol -%}
	{%- set Sign.Type = "Vehicle" -%}
	{%- set Sign.VehicleType = "Boot" -%}
	{%- set Sign.Organisation = "feuerwehr" -%}
	{{ super() }}
	<text style="font-family: 'Roboto Slab'; font-weight: bold; font-size: 48px; text-anchor: middle;" fill="#FFFFFF" x="128" y="153">ZBV</text>
{%- endblock symbol -%}

Zuerst werden die grundlegenden Variablen
	Sign.Type
	Sign.VehicleType
	Sign.Organisation
 die das Zeichen definieren gesetzt.
Mit dem Aufruf von super() wird das Parent Template (base.j2t) gerendert.
Die für das Zeichen spezifischen Texte und Symbole werden danach hinzugefügt (Textzug "ZBV")


Beschreibung der Variablen in base.j2t:

Sign.Type (string)
	Die Art des Zeichens. Diese Variable muss gesetzt sein.
	Das dazugehörige Template muss als .j2t Datei im Ordner templates vorhanden sein.
	Zulässige Werte sind:
		Action			(Maßnahme)
		Buildung		(Gebäude)
		Converter		(Wandler / Konverter)
		Device			(Endgerät)
		Facility		(Stelle / Einrichtung)
		Hazard			(Gefahr)
		Person			(Person)
		Unit			(Einheit)
		Vehicle			(Fahrzeug)

Sign.Organisation (string)
	Die Organisation die 
		das Gebäudes,
		die Stelle bzw. Einrichtung,
		die Einheit,
		das Fahrzeug
	betreibt bzw. 
		die der Person
	angehörig ist.
	Zulässige Werte sind:
		thw
		feuerwehr
		bundeswehr
		katastrophenschutz
		kommunal
		polizei
		zoll

Sign.UnitSize (string)
	Die Größe der Einheit, oder
	die Größe der Einheit die die Person führt.
	Zulässige Werte sind:
		Trupp
		Gruppe
		Staffel
		Zug
		Bereitschaft
		Verband 1
		Abteilung
		Verband 2
		Großverband
		Verband 3

Sign.VehicleType (string)
	Die Art des Fahrzeuges
	Zulässige Werte sind:
		Anhänger			(Anhänger)	
		Kette				(Kettenfahrzeuge)
		Kraft				(Landgebundene Kraftfahrzeuge)
		Gelände				(Landgebundene, geländegängige oder -fähige Kraftfahrzeuge ohne Kettenantrieb)
		Container			(Abrollcontainer, Wechselladerbrücken und dergleichen)
		Wechsel				(Wechselladerkraftfahrzeuge)
		Wechsel Gelände		(Geländegängige oder -fähige Wechselladerkraftfahrzeuge)
		Schiene				(Schienengebundene Fahrzeuge)
		Boot				(Boote, Schiffe, Pontons, keine Amphibienfahrzeuge)

Sign.SpecialFunction (bool)
	Hat die Person eine besondere Funktion?

Sign.Command (bool)
	Ist die Person eine Führungskraft bzw. 
	ist die Einheit oder Einrichtung eine Führungs- oder Leitungs-Einheit bzw. -Einrichtung oder ein Stab?
	Nicht zu verwechseln mit "Einrichtungen der Führung" [Sign.CommandFacility] (Gelbe Grundfarbe mit schwarze Grundefarbe und Schrift)

Sign.Logistics (bool)
	Ist die Einheit oder Einrichtung eine Logistikeinheit oder -Einrichtung?

Sign.Stationary (bool)
	Ist die Stelle bzw Einrichtung dauerhaft ortsfest untergebracht?

Sign.CommandFacility (bool)
	Ist die Befehlsstelle oder 
	die Einrichtung
	eine Einrichtung der Führung bzw.
	gehört die Person einer Einrichtung der Führung an?
	(Gelbe Grundfarbe mit schwarze Grundefarbe und Schrift)

Sign.Acute (bool)
	Ist die Gefahr Akut?

Sign.Presumed (bool)
	Wird die Gefahr Vermutet?

Sign.Link1 (string)
	Art der IuK-Verbindug auf der linken Seite des Wandlers bzw.
	Art der IuK-Verbindug des Endgeräts.
	Zulässige Werte sind:
		Bild		(Bewegtbildübertragung)
		Daten		(Datenübertragung )
		Sprechen	(Übertragung von Sprache in analoger oder digitaler Form)
		Schreiben	(Fernschreiben)
		Tasten		(Ferntasten, Morsen)
		Festbild	(Festbildübertragung, Fax)
		Relais		(Relaisfunkbetrieb, Repeater- oder Gatewaybetrieb, impliziert [Sign.Wireless1])
		Richt		(Richtfunkbetrieb)

Sign.Wireless1 (bool)
	Ist die IuK-verbindung von [Sign.Link1] drahtlos?
	Darf für den Wert 'Richt' nicht gesetzt werden.

Sign.Link2 (string)
	Art der IuK-Verbindug auf der rechten Seite des Wandlers bzw.
	Art der IuK-Verbindug des Endgeräts wenn [Sign.Link1] nicht gesetzt wurde.
	Zulässige Werte siehe [Sign.Link1]

Sign.Wireless2 (bool)
	Ist die IuK-verbindung von [Sign.Link2] drahtlos?
	Darf für den Wert 'Richt' nicht gesetzt werden.

Sign.StrokeColor (string)
	Überschreibt die Farbe des Schattens bzw. der äußersten Umrandung eines Zeichens die sonst durch [Sign.Organisation] vorgegeben wäre (Beispiel: Schwarz Kreise und Schatten bei einem THW-Fahrzeug).
	Zulässige Werte:
		- Bevorzugt: 6-stellige Hexadezimal RGB_Werte mit führendem #
		- Alle gültigen Werte für den <color> CSS data type
	
Sign.SecondaryColor (string)
	Überschreibt die Farbe der Umrandung und der Schrift eines Zeichens die sonst durch [Sign.Organisation] vorgegeben wäre (Beispiel: Weiße Schrift und Umrandung bei einem THW-Fahrzeug)
	Zulässige Werte:
		- Bevorzugt: 6-stellige Hexadezimal RGB_Werte mit führendem #
		- Alle gültigen Werte für den <color> CSS data type

Sign.PrimaryColor (string)
	Überschreibt die Grundfarbe eines Zeichens die sonst durch [Sign.Organisation] vorgegeben wäre (Beispiel: Blaue Füllung bei einem THW-Fahrzeug)
	Zulässige Werte:
		- Bevorzugt: 6-stellige Hexadezimal RGB_Werte mit führendem #
		- Alle gültigen Werte für den <color> CSS data type