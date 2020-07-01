# tobbvalt_project
## Röviden a projektről:
Projektünk célja egy olyan rendszer megvalósítása, ami a hétköznapi életben is napi szinten van alkalmazva parkolóházakban. 
Egy kamera (esetünkben egyszerűsítettük a helyzetet, képpel dolgozunk) felismer egy rendszámot, string-et képez belőle, amit
el tudunk tárolni az adatbázisunkban. Az adatbázis tárolja az autó rendszámát, illetve a felvétel időpontját. Továbbiakban már nem
lenne nehéz kiszámolni a parkolás időtartamát sem (ha még egyszer detektáljuk a rendszámot, a két időpontot vonja ki egy másból).

**Esetünkben ez két nagyobb feladatot jelent:**
- Rendszám felismerés (openCV, OCR, Tesseract)
  - Pogácsás Gergely
  - Barcza Bende
- Eltárolása/adatbázisba foglalása (sqlite3)
  - Tóth Imre
  - Gácsi László

**OCR, szövegfelismerés:**
Az autó képéhez - melyen a rendszám lehetőleg vízszintes, világos, a lehető legjobban minőségű - tartozó elérési útvonalat megadva 
a program több lépésben elemzi a kapott képet.
Szürkeárnyalatossá teszi első lépésben a megadott képfájlt. 
A következőkben éleket keres, majd lépésenként "butítja" a képet. 
A kontúrvonalakat zöld színnel feltünteti az eredeti képen, majd a potenciális rendszámot (/rendszámokat) pirossal jelzi. 
Ha bizonyos feltételeknek megfeleltek ezek a piros kerettel ellátott mezők, akkor megkapjuk a kivágott rendszámtáblát. 
Ezt a képet Tesseract-tal lefuttatjuk, felismerjük a rajta található stringeket, melyeket változóként raktározunk el a későbbi adatbázis rendszer érdekben. 
A fenti lépések az Internet, pontosabban egy leleményes python programozó érdeme, mi "csak" utánajártunk, kijavítottuk a hibákat, optimalizáltuk, aktualizáltuk a kódot.

**Adatbázis:**
Az autók rendszerezését adatbázisba foglalással képzeltük el, ehhez a python sqlite3 adatbázis rendszerét vettük
igénybe. Ennek a segítségével alap sql parancsok használatával (SELECT,DELETE,INSERT...stb) tudtuk rendszerezni autóinkat.
Az adatbázisban létrehoztunk egy adattáblát, amelyben helyet kap a Rendszám, és az időpont attribútum. Célszerűnek
tűnt hogy az időpontot is tároljuk (ezt a pythonban letudtuk kérni), így ha esetleg parkolási időt kéne számolni
egy garázsban, már egyszerűen megtehető. Ehhez az egészhez egy windows ablakot is készítettünk.
4 funciót tartalmaz (persze, ezek bővíthetőek igény szerint): Keresés, új rendszám hozzáadása, törlése és az összes
listázása. (Valós életben is előfordulhat hogy manuálisan kell hozzáadni/törölni).
Részletesebb parancsok értelmezésére próbáltuk minél jobban kommentelni a programot.
Megjegyzés: Ha először van lefuttatva az adatbazis, akkor még autó nem lesz benne.
