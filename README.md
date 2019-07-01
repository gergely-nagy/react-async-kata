# React async data

## User stories:

- Kérd el az adatokat az API-tól aszinkron módon a következő URL-ből: https://ghibliapi.herokuapp.com/films (filmek listája a Ghibli studioban)
- Jelenítsd meg az adatokat frontenden egy listaként. (cím, leírás, rendező és megjelenési dátum minden filmre)
- Amíg az adat letöltődik, töltő állapot megjelnítése
- Ha az adatot nem sikerült elkérni, hibaüzenet megjelenítése (újratöltés biztosítása)

## Megoldás:

1. [Create React App](https://facebook.github.io/create-react-app/) segítségével projekt létrehozása és `.env` fájl létrehozása.
1. Repóban található `.env` fájl tartalmának átmásolása a lokális fájlba , HOST + PORT beállítása.
1. Új `state`  (`movies: []`) létrehozása filmek tárolásához.
1. Hozzáadni a  `componentDidMount()` metódust az App komponenshez. (https://reactjs.org/docs/react-component.html#componentdidmount)
1. A `componentDidMount()` metódusban aszinkron hívás megvalósítása, ami a fent megadott url-től elkéri az adatokat (Referenciaként tekints ránézhetsz a [következő gistekre](https://gist.github.com/luismartinezs/fefffec1748de0f728a3d6e3aaee841a). (aszinkron hívások eredményével felül kell írnunk a helyi state-ünket)
1. A betöltő widgethez definiáld az `isLoading: true` állapotot (state) az App komponensben, ezután a render metódusban feltételhez kötötten jelenítsd meg a `<Loading />` komponenst a lista komponens helyett ha az `isLoading` értéke `true`.
1. Hiba kezeléséhez definiáld a `loadStatus` állapotot (state) az App komponensben. Az aszinkron hívás `catch` blokkjában írd felül az értéket `error`-al. Feltételhez kötötten jelenítsd meg az `<Error />` komponenst a lista komponens helyett ha az az értéke `error`.
(Ezt a funkciót úgy tudod majd tesztelni ha az url direkt elírod a fetch metódusban. )
