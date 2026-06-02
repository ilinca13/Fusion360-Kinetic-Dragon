# Dragon Mechanism - Kinetic Sculpture (Fusion 360 Project)

## 📌 Descrierea Proiectului
Acest proiect urmărește realizarea unui mecanism complex sub forma unui dragon articulat care execută o mișcare sinusoidală (în valuri). Proiectul a fost dezvoltat ca parte finală a materiei opționale **Printare și Modelare 3D**, Anul 2 Semestrul 2, utilizând software-ul **Autodesk Fusion 360**.

Scopul principal este demonstrarea principiilor de transmitere a mișcării prin angrenaje și sisteme de tip „pin-slide linkage”, rezultând într-o sculptură cinetică complet funcțională.

<div align="center">
  <img width="701" height="577" alt="Screenshot 2026-05-05 153109" src="https://github.com/user-attachments/assets/1955cf1c-ad65-4422-9494-ccbde3dfbaa7" />
</div>


## ⚙️ Detalii Tehnice și Mecanism
Mecanismul se bazează pe transformarea mișcării de rotație într-o mișcare oscilatorie complexă:
- **Offset Gears (Angrenaje Excentrice):** O serie de roți dințate interconectate care, prin poziționarea decalată a axelor de rotație, creează efectul de val.
- **Pin-Slide Linkage:** Sistemul de pârghii care susține segmentele dragonului și permite translația fluidă a acestora.
- **Snap-fit Design:** Toate componentele sunt proiectate pentru a fi asamblate fără elemente de fixare externe (șuruburi sau lipici), utilizând toleranțe precise de modelare.

## 🚀 Funcționalități în Fusion 360
În cadrul acestui proiect au fost utilizate următoarele funcții avansate:
- **As-Built Joints & Joint Origins:** Pentru definirea corectă a mișcării între componente.
- **Motion Study:** Simularea mișcării sinusoidale pentru a verifica coliziunile înainte de printare.
- **Contact Sets:** Utilizate pentru a valida interacțiunea reală dintre dinții angrenajelor.
- **Parametric Design:** Ajustarea toleranțelor pentru componentele snap-fit.

## 📂 Modul de funcționare 



<video src="https://github.com/user-attachments/assets/8ce9b104-1642-4b2a-8195-49fe472c6384" width="100%" controls playsinline autoplay muted loop>
  Browserul tău nu suportă redarea video.
</video>

<video src="https://github.com/user-attachments/assets/30e17f99-9f20-43eb-bb68-f1d8aa2a1f71" width="100%" controls playsinline autoplay muted loop>
  Browserul tău nu suportă redarea video.
</video>


- `/Models`: Fișierele `.f3d` (Fusion 360) și `.step`.
- `/STL`: Fișierele pregătite pentru slicing și printare 3D.
- `/Simulations`: Capturi de ecran sau video cu studiul mișcării.
- `/Documentation`: Schema de asamblare și detaliile mecanismului.

## 💡 Sursă de Inspirație
> [!NOTE]
> Acest proiect este o recreare/adaptare după modelul original:
**[Dragon Mechanism - Build Kit](https://thangs.com/designer/InvenDev/3d-model/Dragon%20Mechanism%20-%20Build%20Kit-1484460)** creat de **InvenDev**. 
*Proiectul curent include adaptări proprii pentru optimizarea printării și simularea mișcării în mediul Fusion 360.*
> 

## 🛠️ Setări recomandate pentru printare
- **Material:** PLA
- **Înălțime strat:** 0.2mm
- **Infill:** 15-20% (Grid)
- **Suporturi:** Nu sunt necesare (proiectat pentru printare directă).
