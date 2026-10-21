# RestaurantInventory

RestaurantInventory je konzolna aplikacija napisana u C# koja služi za upravljanje inventarom restorana. Aplikacija omogućava praćenje robe, filtriranje stavki, provjeru minimalnih zaliha i generiranje jednostavnih izvještaja o stanju inventara.

## Opis projekta

Projekat je razvijen kao jednostavan sistem za evidenciju artikala u restoranu, sa fokusom na:
- dodavanje novih stavki u inventar,
- pregled svih stavki,
- sortiranje po cijeni ili količini,
- pretragu i filtriranje po različitim kriterijima,
- provjeru kritičnih zaliha,
- ažuriranje količina,
- uklanjanje stavki,
- generisanje izvještaja o stanju i vrijednosti inventara.

Aplikacija je dizajnirana kao CLI (Command Line Interface) aplikacija, što znači da se koristi direktno kroz terminal (konzolu).

## Tehnologije

- C#
- .NET 8
- MSTest
- Visual Studio / .NET SDK

## Struktura projekta

Repozitorij sadrži dvije glavne cjeline:

- RestaurantInventory
  - glavni projekat aplikacije,
  - sadrži modele, servise i logiku konzolnog interfejsa.
- RestaurantInventoryTest
  - projekat sa unit testovima,
  - pokriva funkcionalnost poslovnih servisa i validaciju pravila poslovne logike.

### Glavne datoteke

- Program.cs
  - glavna aplikacija,
  - sadrži meni, unos korisničkih podataka i pozive poslovnih funkcija.
- Models/
  - definicije domenskih objekata poput stavke inventara, kategorije, filtera, izvještaja, narudžbe i drugih entiteta.
- Services/
  - poslovna logika aplikacije:
    - InventarService
    - FilterService
    - StavkaInventaraService
    - IzvjestajService

## Funkcionalnosti

### 1. Dodavanje stavke
Korisnik može unijeti:
- naziv artikla,
- opis,
- kategoriju,
- količinu,
- minimalnu količinu,
- cijenu,
- dobavljača,
- datum nabavke.

### 2. Prikaz inventara
Aplikacija omogućava pregled svih stavki u inventaru uz izbor sortiranja:
- po cijeni,
- po količini,
- rastuće ili padajuće.

### 3. Pretraga i filtriranje
Korisnik može filtrirati inventar prema:
- nazivu,
- dobavljaču,
- minimalnoj i maksimalnoj cijeni.

### 4. Provjera minimalnih zaliha
Aplikacija provjerava koje stavke imaju količinu ispod zadane minimalne vrijednosti i označava ih kao kritične.

### 5. Ažuriranje količine
Vrednost količine stavke može se promijeniti nakon što se pronađe po nazivu.

### 6. Uklanjanje stavke
Stavka se može ukloniti po nazivu.

### 7. Generisanje izvještaja
Korisnik može kreirati izvještaj sa:
- nazivom,
- periodom,
- kategorijom,
- pregledom stavki i ukupnom vrijednošću inventara.

## Modeli domena

Najvažniji modeli u projektu su:

- StavkaInventara
  - predstavlja jednu stavku u inventaru,
  - sadrži naziv, količinu, cijenu, dobavljača, datum nabavke, minimalnu količinu, opis i kategoriju.
- Inventar
  - predstavlja kolekciju svih stavki.
- Filter
  - služi za pretragu i filtriranje.
- Izvjestaj
  - služi za kreiranje izvještaja o stanju inventara.
- Kategorija
  - enum za različite tipove artikala (hrana, piće, posuđe, sredstva za čišćenje, namještaj, ostalo).
- Narudzba
  - predstavlja narudžbu koja se generiše za artikle čija je količina ispod minimalnog nivoa.

## Poslovna logika

Servisi sadrže glavnu poslovnu logiku:
- InventarService
  - dodavanje, pretraga, uklanjanje, ažuriranje i validacija stavki,
  - provjera minimalnih zaliha,
  - generisanje liste narudžbi.
- FilterService
  - primjenjuje logiku filtera na listu stavki.
- StavkaInventaraService
  - pruža pomoćne metode vezane za pojedinačnu stavku, uključujući provjeru kritičnosti i ažuriranje količine.
- IzvjestajService
  - generiše statistiku i formatira izvještaj.

## Testiranje

Projekat sadrži detaljan skup testova u okviru RestaurantInventoryTest. Testovi pokrivaju:
- validaciju filtera,
- provjeru pravilnog ponašanja InventarService,
- testove TDD (Test-Driven Development),
- white-box testove,
- testove za kritične slučajeve i granice logike.

Testovi su napisani koristeći MSTest framework.

## Pokretanje projekta

Prvo obavite restore paketa:
```bash
dotnet restore
```

Zatim build:
```bash
dotnet build
```

Pokretanje aplikacije:
```bash
dotnet run --project RestaurantInventory
```

## Zaključak

RestaurantInventory je jednostavan, ali funkcionalan sistem za upravljanje inventarom restorana. Projekat demonstrira dobre osnove objektno-orijentisanog programiranja, rada sa kolekcijama, filterima, servisnim slojem i testiranjem poslovne logike. To ga čini odličnim primjerom aplikacije za praćenje robe i upravljanje zalihama u malom restoranskom okruženju.

## Napomena

Ovaj repositorij je strukturiran kao primjer akademskog ili laboratorijskog projekta, sa akcentom na poslovnu logiku, validaciju podataka i testiranje ponašanja aplikacije.
