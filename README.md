# Chemischer Reaktor

**Autoren:**  
Jakob Brettschneider, Valentin Steinwender, Thomas Klimisch

---

## Inhaltsverzeichnis

1. [Versionshistorie](#1-versionshistorie)  
2. [Anwendungsbeispiel](#2-anwendungsbeispiel)  
3. [Konkretes Beispiel zur Funktionsüberprüfung](#3-konkretes-beispiel-zur-funktionsüberprüfung)  
4. [Mathematischer Hintergrund](#4-mathematischer-hintergrund)  

---

## 1. Versionshistorie
###  Version 1.1 (01.05.2025)
**Änderungen**
- Erstelllen der Eingabeparameter und rxn Funktion
- implementieren der ode45 Funktion
- Plotten der Konzentrationswerte

### Version 1.2 (10.05.2025)
**Änderungen**
- Abänderung der User Interface
  
### Version 1.3 (10.06.2025)  
**Änderungen:**  
- Auswahl der Integrationsdauer hinzugefügt  
- README-Datei aktualisiert und ergänzt  
- Repository neu strukturiert  

### Version 1.4.1 (21.06.2025)  
**Änderungen:**  
- Codekorrekturen  
- Neue Struktur der README-Datei  
- Änderungen im Format der Ergebnisdateien  

---

## 2. Anwendungsbeispiel

Das Anwendungsbeispiel behandelt die Reaktionskinetik einer einfachen chemischen Reaktion, die in zwei aufeinanderfolgenden Schritten abläuft. Es wird angenommen, dass keine Rückreaktionen stattfinden:

A + B → C  
B + C → D

Die Reaktionsgeschwindigkeiten hängen von den Konzentrationen der Edukte ab und werden wie folgt beschrieben:

r₁ = k₁ · [A] · [B]  
r₂ = k₂ · [B] · [C]

Diese Gleichungen werden zur Simulation des Reaktionsverlaufs verwendet. Die zeitabhängige Konzentrationsentwicklung wird im Zuge des Programmes errechnet und als Grafik ausgegeben. Zusätzlich errechnet das Programm noch 
die reaktionstechnischen Kennwerte Umsatz, Selektivität, und die Maximal und Minimal Konzentrationen aller beteiliger Stoffe. Zusätzlich wird untersucht welchen Einfluss es auf die reaktionstechnischen Kennwerte hat, wenn 
die Menge an Stoff A erhöht wird. Die Ergebnisse dieser Berechnungen werden in einer Ergebnisdatei abgespeichert.

---

## 3. Konkretes Beispiel zur Funktionsüberprüfung

Das Modell ist bereits auf eine spezifische Reaktion zugeschnitten. Anwender:innen können jedoch die Startkonzentrationen durch Anpassung des Arrays `c0` verändern, zum Beispiel:

c0 = [2, 3, 0, 0];

Nachdem die Konzentrationen und die spezifische Anwendung selber bereits in das Programm implementriert ist, ist dem Progamm jetzt kein seperates Beispiel beigelegt, um die Eigenverwendung weiter zu veranschaulichen. Dennoch
kann über folgenden Befehl in der Konsole die Richtigkeit der Übergabeparameter geprüft werden. Dabei wird einfach nur geprüft, ob die Konzentration für t=0 der Anfangskonzentration c0_{0} entspricht.

**isequal(c(1, :), c0)**

Wenn die Rückgabe in der Konsole gleich (logical) 1 ist, dann ist der Test positiv und die Funktion übernimmt die Übergabeparameter korrekt. 

---

## 4. Mathematischer Hintergrund

Die Simulation basiert auf einem System gewöhnlicher Differentialgleichungen (ODEs), das die zeitliche Änderung der Konzentrationen beschreibt. Für die obigen Reaktionen ergeben sich die folgenden Gleichungen:

- d[A]/dt = –r₁  
- d[B]/dt = –r₁ – r₂  
- d[C]/dt = +r₁ – r₂  
- d[D]/dt = +r₂  

Die Reaktionsgeschwindigkeiten `r₁` und `r₂` werden durch die Massenwirkungsgesetze definiert:

- r₁ = k₁ · [A] · [B]  
- r₂ = k₂ · [B] · [C]  

Die numerische Lösung dieser Gleichungen erfolgt z. B. mit MATLABs `ode45`-Solver. Dabei wird der Konzentrationsverlauf der Stoffe über die Zeit berechnet.

---

