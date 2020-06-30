# tobbvalt_project
Röviden a projektről:
Projektünk célja egy olyan rendszer megvalósítása, ami a hétköznapi életben is szinte naponta van használva a parkolók esetén. 
Egy kamera (esetünkben egyszerűsítettük a helyzetet, képpel dolgozunk) felismeri egy rendszámot, string-et képez belőle, amit
eltudunk tárolni az adatázisunkban. Az adatbázis tárolja az autó rendszámát, illetve felvétel időpontját. Továbbiakban már nem
lenne nehéz kiszámolni a parkolás időtartamát sem. (ha mégegyszer detektáljuk a rendszámot, a két időpontot vonja ki egy másból).

Esetünkben ez két nagyobb feladatot jelent:
-Rendszám felismerés(opencv,ocr,tesseract)
-Eltárolása/adatbázisba foglalása(sqlite3)

OCR, szövegfelismerés:


Adatbázis:
Az autók rendszerezését adatbázisba foglalással képzeltük el, ehhez a python sqlite3 adatbázis rendszerét vettük
igénybe. Ennek a segítségével alap sql parancsok használatával (SELECT,DELETE,INSERT...stb) tudtuk rendszerezni autóinkat.
Az adatbázisban létrehoztunk egy adattáblát, amelyben helyet kap a Rendszám, és az időpont attribútum. Célszerűnek
tűnt hogy az időpontot is tároljuk (ezt a pythonban letudtuk kérni), így ha esetleg parkolási időt kéne számolni
egy garázsban, már egyszerűen megtehető. Ehhez az egészhez egy windows ablakot is készítettünk.
4 funciót tartalmaz (persze, ezek bővíthetőek igény szerint): Keresés, új rendszám hozzáadása, törlése és az összes
listázása. (Valós életben is előfordulhat hogy manuálisan kell hozzáadni/törölni).
Részletesebb parancsok értelmezésére próbáltuk minél jobban kommentelni a programot.
