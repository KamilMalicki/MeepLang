# 🐣 Meep – interpreter języka Meep  
**autor: KamilMalicki**

---

## 📦 Co to jest?

Meep to prosty i zwinny interpreter języka Meep — inspirowany ptakiem **Scolopax** (American Woodcock), który w naturze wydaje charakterystyczne dźwięki „peep” i „meep”.  
Meep pozwala tworzyć i uruchamiać programy zapisane w specjalnym, minimalistycznym języku tekstowym — języku Meep.

Meep to **język ezoteryczny**, czyli język programowania stworzony bardziej dla eksperymentów, zabawy i nauki niż do praktycznych zastosowań.  
Meep jest językiem niskopoziomowym, asembleropodobnym esolangiem — operuje bezpośrednio na pamięci i prostych instrukcjach sterujących, z własnym systemem zmiennych i pętli.

---

## ▶️ Jak używać?

Nie wymaga instalacji ani kompilacji.

### Linux / macOS:
```bash
./meep twoj_program.meep
````

### Windows:

```cmd
meep.exe twoj_program.meep
```

---

## 🐦 Instrukcje – czyli co ptak mówi i co robi:

### `meep[adres] <- 'tekst'`

Zapisuje tekst do pamięci od podanego adresu.

### `meep[src] -> meep[dst]`

Kopiuje pojedynczą wartość z adresu `src` do adresu `dst`.
Specjalne adresy:

* `0xFFFF0001` — stdout (ptak „meep” wypuszcza znak na ekran),
* `0xFFFF0002` — stdin (ptak „meep” wczytuje znak z klawiatury).

### `0xFFFF0000` — adres specjalny `ADDR_COMPARE`

Tutaj ptak „meep” przechowuje wartość do porównania przy wykonywaniu pętli `loop`.
Instrukcja `loop wartość` sprawdza, czy pamięć pod tym adresem jest równa `wartość`. Jeśli nie, powraca do zapisanego miejsca (pętla), jeśli tak — kontynuuje.

---

### `peep push`

Zapisuje aktualny punkt w programie (numer linii) na stos, jak ptak zostawiający ślad.

### `peep pop`

Usuwa ostatni zapisany ślad ze stosu.

### `loop wartość`

Sprawdza wartość pod `0xFFFF0000`.
Jeśli różna od podanej, wraca do ostatniego śladu ze stosu (pętla).
Jeśli równa — usuwa ślad i leci dalej.

### `peep egg nazwa <- wartość`

Tworzy lub zmienia zmienną (jajko) o nazwie `nazwa`.

### `peep egg nazwa -> meep[adres]`

Zapisuje wartość zmiennej do pamięci pod wskazany adres.

---

## 📁 Przykład — „Hello, world!” śpiew ptaka Meep

```meep
meep[0x1000] <- 'Hello, world!\n'
meep[0x1000] -> meep[0xFFFF0001]
```

Uruchomienie:

```bash
./meep hello.meep
```

Efekt:

```
Hello, world!
```

---

## 🦤 Ptak Scolopax (American Woodcock)

Ten program i język został zainspirowany ptakiem **Scolopax**, który wydaje dźwięki „peep” i „meep”, tak samo jak instrukcje w języku Meep.
To symbol prostoty i naturalnej komunikacji, którą przeniosłem na programowanie.

![Ptak Scolopax (American Woodcock)](https://animalia.bio/wp-content/uploads/american-woodcock.jpg)

---

## 👤 Autor

**KamilMalicki**
Prosty, szybki interpreter języka Meep, który pozwala poczuć się jak ptak mówiący „peep” i „meep”.

```

Jeśli chcesz, możesz wkleić ten tekst do pliku `README.md` i będzie gotowy.  
Daj znać, jeśli chcesz go przerobić.
```
