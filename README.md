# Dragon Mechanism - Kinetic Sculpture (Fusion 360)
---
## 📌 Descrierea Proiectului
Acest proiect urmărește realizarea unui mecanism complex sub forma unui dragon articulat care execută o mișcare sinusoidală (în valuri). Acesta este proiectul meu final pentru cursul opțional **Printare și Modelare 3D** (Anul 2 Semestrul 2).

Întregul ansamblu mecanic a fost dezvoltat, asamblat și simulat în aplicația **Autodesk Fusion 360**, fiind ulterior optimizat pentru imprimare 3D. Scopul principal este demonstrarea practică a principiilor de transmitere a mișcării prin angrenaje excentrice și sisteme de pârghii articulate, obținând un produs complet funcțional bazat exclusiv pe îmbinări mecanice (joints, motion link & constraints).

Ca structura a proiectului, pe acest repo se găsesc toate fișierele necesare unei posibile producții. Fișierele cu extensia .f3d (cu istoricul complet al acțiunilor efectuate în Fusion, atât pentru fiecare componentă în parte cât și pentru tot mecanismul asamblat și funcțional.

<div align="center">
  <img width="701" height="577" alt="Dragon Mechanism Overview" src="https://github.com/user-attachments/assets/1955cf1c-ad65-4422-9494-ccbde3dfbaa7" />
</div>

---

## 💡 Sursă de Inspirație
> [!NOTE]
> Acest proiect este o adaptare după modelul de referință:
> **[Dragon Mechanism - Build Kit](https://thangs.com/designer/InvenDev/3d-model/Dragon%20Mechanism%20-%20Build%20Kit-1484460)** creat de **InvenDev**. 
> *Aportul propriu constă în remodelarea ansamblului de la 0 in proporție de 85% (am folosit și mesh-uri pentru conturul neregulat al pieselor de dragon), optimizarea jocurilor și toleranțelor specifice pentru printare, rezolvarea cinematicii prin legături matematice și crearea studiului complet de mișcare sinusoidală în Fusion 360.*

## ⚙️ Modelarea mișcării (Fusion 360)

Transformarea mișcării rotative într-o mișcare liniară-oscilatorie sinusoidală complexă a fost realizată prin implementarea a următoarelor interdependențe:

### 1. Sistemul de Angrenaje și Calculul Raportului de Transmitere
Arborele motor pornește de la o **manivelă principală manuală**. Aceasta este conectată prin **rigid joint** de carcasa **ancorată** la sistemul de coordonate global prin comanda **Pin**.
Mișcarea este transmisă în cascadă printr-o serie de roți dințate drepte - **Spur Gears**: manivela - 8 dinți, în restul sistemului 30 și/sau 11 dinți. 
* **Asamblare mecanică:** Fiecare roată dințată a fost ancorată în carcasă prin îmbinări de rotație pură (**Revolute Joints**), eliminând orice grade de libertate parazite (translații pe axele X, Y, Z).
* **Motion Links (Sincronizare în cascadă):** Pentru a simula interacțiunea fizică dintre dinți, s-au implementat relații de tip *Motion Link* între fiecare pereche de angrenaje succesive, pornind de la axul manivelei și urcând pe întregul lanț al spur gear-urilor, din aproape în aproape.
* **Calculul rotațiilor:** Pentru a asigura sincronizarea perfectă și a evita coliziunile geometrice, *raportul de transmitere* a fost calculat matematic pe baza *numărului de dinți* și sau al *pitch diameter-urilor*. Acolo unde roțile angrenate au fost identice ($N_1 = N_2$), s-a păstrat un raport de $1:1$ (rotație de $360^\circ$ în sensuri opuse, bifând opțiunea *Reverse*). Pentru rapoartele de demultiplicare/multiplicare, unghiul de rotație introdus în constrângere a urmat ecuația:

> [!TIP]
 $$\theta_2 = \theta_1 \cdot \left(\frac{N_1}{N_2}\right)$$
  

### 2. Generarea Mișcării Sinusoidale prin Constrângeri Tangențiale
Eefectul de undă fluidă al corpului dragonului a fost obținut prin decalarea unghiulară geometrică a pinilor de fixare poziționați excentric pe fețele roților dințate.
* Pentru ca segmentele dragonului să execute oscilația verticală fără să se blocheze sau să se desprindă de pini, pârghiile de susținere ale modulelor au fost modelate cu constrângeri de **Tangență (Tangent Constraints / Slider Connectors)** în interiorul **canalelor de culisare** ale pieselor dragonului. 

---

## 🎥 Demonstrație Video și Simulare

> [!IMPORTANT] 
Datorită limitărilor de redare video ale anumitor browsere și dispozitive mobile, dacă playerele native de mai jos nu încarcă videoclipurile, ele pot fi accesate direct prin link-urile alternative.

### 1. Previzualizare mișcare mecanism motor - spur gears pe cadrul de susținere

<video src="https://github.com/user-attachments/assets/8ce9b104-1642-4b2a-8195-49fe472c6384" width="100%" controls playsinline autoplay muted loop>
  Link util pentru mobil: <a href="https://github.com/user-attachments/assets/8ce9b104-1642-4b2a-8195-49fe472c6384">🎦 Rotația angrenajelor</a>
</video>

### 2. Simularea mecanismului complet (Kinetic Wave)

<video src="https://github.com/user-attachments/assets/30e17f99-9f20-43eb-bb68-f1d8aa2a1f71" width="100%" controls playsinline autoplay muted loop>
  Link util pentru mobil: <a href="https://github.com/user-attachments/assets/30e17f99-9f20-43eb-bb68-f1d8aa2a1f71">🎦 Mecanismul complet</a>
</video>

---

## 🛠️ Strategia de printare 
> [!IMPORTANT]
Ansamblul conține peste 20 de piese cu geometrii complet diferite (carcase volumetrice masive, axe cilindrice subțiri și roți dințate cu module mici). Pentru a asigura rezistența mecanică necesară la torsiune și o viteză de execuție optimă, felierea în **PrusaSlicer** a fost configurată personalizat:

### 1. Managementul Grosimii Straturilor (Adaptive Layer Height)
Pentru a evita procesarea manuală ineficientă a fiecărei piese, s-a utilizat algoritmul de înălțime variabilă adaptivă (**Adaptive Layer Height**) aplicată pe piesele bazei de susținere.
* **Profilul de viteză vs. detaliu:** Zonele cu pereți verticali drepți (cum este cutia de bază a carcasei) au fost feliate automat la o înălțime maximă de siguranță pentru a reduce drastic timpul total de printare.
* **Plasa de siguranță structurală (Keep Min):** Opțiunea *Keep Min* a fost păstrată **activă (bifată)**. Acest lucru a garantat că în timpul optimizării geometrice, algoritmul nu a mărit grosimea straturilor în zonele critice. Astfel, dinții fini ai roților și filetele au fost blocate la o rezoluție înaltă (aprox. $0.10\text{ mm}$), asigurând o suprafață netedă și o precizie dimensională extremă la asamblare.
* **Limita critică pentru nozzle:** Pentru un nozzle standard de $0.40\text{ mm}$, valoarea maximă admisă pentru straturile adaptive a fost plafonată strict la **`0.28 mm`** (respectând regula de maximum $80\%$ din diametrul nozzle-ului). Acest lucru a prevenit fenomenul de delaminare (lipirea defectuoasă a straturilor) și a asigurat piese capabile să reziste la solicitări mecanice reale.

### 2. Parametri de Printare 

* **Număr de perimetre (Perimeters):** Crescut la **3 sau 4 perimetre** (în loc de 2 standard) pentru a oferi rigiditate structurală dinților și axelor, asigurându-se că miezul pieselor mecanice nu cedează sub sarcină.
* **Infill:** $15\% - 20\%$ cu model geometric **Grid** (asigură rezistență izotropă).


### 3. Amplasare pe Build Plate

<img width="1919" height="1031" alt="Screenshot 2026-06-02 093159" src="https://github.com/user-attachments/assets/d9bbd4a7-cbba-4fc6-be40-199d1d43faed" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2f469248-d708-4cac-bfe8-d718ef1b9e4b" />

<img width="1919" height="1031" alt="image" src="https://github.com/user-attachments/assets/72bb9156-4d64-4f8c-9cb7-1f6dec192bc5" />

<img width="1916" height="1028" alt="image" src="https://github.com/user-attachments/assets/7ca1fdeb-2dc6-4089-80d5-7749f1369270" />



