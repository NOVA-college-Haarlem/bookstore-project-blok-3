# Project Bookstore

## Opdrachten

### Opdracht 1 - Database ontwerp

- Maak op basis van onderstaande userstories en het SQL-bestand een database ontwerp. 

### Opdracht 2 - Repository

- Maak gebruik van de repository: https://github.com/NOVA-college-Haarlem/bookstore-project-blok-3
- Fork de repository
- Clone de repository

### Opdracht 3 - Website

- Maak een website voor een boekenwinkel.

### Opdracht 4 - Controleren

- Controleer je website door gebruik te maken van de rubric.

## Overzichtspagina

**Als een** bezoeker  
**Wil ik** een overzicht zien van alle beschikbare boeken  
**Zodat ik** snel kan bladeren door verschillende boeken

**Als een** bezoeker  
**Wil ik** basisinformatie zien van elk boek (titel, auteur, thumbnail afbeelding)  
**Zodat ik** een eerste indruk krijg zonder naar de detailpagina te hoeven gaan

**Als een** bezoeker  
**Wil ik** op een boek kunnen klikken  
**Zodat ik** naar de detailpagina kan gaan voor meer informatie

## Filtering (beperkt tot 2)

**Als een** bezoeker  
**Wil ik** kunnen filteren op genre (fictie, non-fictie, thriller, fantasy, etc.)  
**Zodat ik** alleen boeken zie die passen bij mijn leesvoorkeur

**Als een** bezoeker  
**Wil ik** kunnen filteren op auteur  
**Zodat ik** boeken kan vinden van schrijvers die ik waardeer

## Overige Functionaliteiten

**Als een** bezoeker  
**Wil ik** kunnen sorteren op prijs (van laag naar hoog of hoog naar laag)  
**Zodat ik** boeken kan vinden binnen mijn budget

**Als een** bezoeker  
**Wil ik** zien hoeveel resultaten er beschikbaar zijn binnen mijn gekozen filters  
**Zodat ik** weet hoeveel opties ik heb

```sql
-- Database schema voor Bookstore Catalog met één tabel

-- Boeken tabel
CREATE TABLE boeken (
    id INT PRIMARY KEY AUTO_INCREMENT,
    titel VARCHAR(200) NOT NULL,
    auteur VARCHAR(100) NOT NULL,
    genre VARCHAR(50) NOT NULL,
    beschrijving TEXT,
    isbn VARCHAR(20),
    paginas INT,
    uitgeverij VARCHAR(100),
    publicatiejaar INT,
    prijs DECIMAL(10, 2),
    thumbnail_url VARCHAR(255)
);

-- Voorbeelddata invoegen
INSERT INTO boeken (titel, auteur, genre, beschrijving, isbn, paginas, uitgeverij, publicatiejaar, prijs, thumbnail_url) VALUES 
('Harry Potter en de Steen der Wijzen', 'J.K. Rowling', 'Fantasy', 'Het eerste boek in de Harry Potter-serie over een jonge tovenaar die ontdekt dat hij bijzonder is.', '9789061697671', 223, 'De Harmonie', 1998, 19.99, 'harrypotter1.jpg'),
('De Da Vinci Code', 'Dan Brown', 'Thriller', 'Een thriller over symbolen, geheime genootschappen en een moord in het Louvre.', '9789024556502', 489, 'Luitingh-Sijthoff', 2004, 15.99, 'davinci.jpg'),
('Het Diner', 'Herman Koch', 'Literaire fictie', 'Een roman over twee echtparen die in een restaurant bijeenkomen om te praten over hun kinderen.', '9789041415448', 301, 'Ambo|Anthos', 2009, 12.50, 'diner.jpg'),
('Sapiens: Een kleine geschiedenis van de mensheid', 'Yuval Noah Harari', 'Non-fictie', 'Een boek over de evolutie van de mensheid en hoe we de wereld hebben gevormd.', '9789045036199', 455, 'Thomas Rap', 2015, 22.99, 'sapiens.jpg'),
('De Aanslag', 'Harry Mulisch', 'Literaire fictie', 'Een roman over de gevolgen van een aanslag in de Tweede Wereldoorlog in Nederland.', '9789023495321', 272, 'De Bezige Bij', 1982, 14.99, 'aanslag.jpg'),
('1984', 'George Orwell', 'Science Fiction', 'Een dystopische roman over een totalitaire staat waarin alles wordt gecontroleerd.', '9789029538473', 328, 'Arbeiderspers', 1983, 11.99, '1984.jpg'),
('De Hobbit', 'J.R.R. Tolkien', 'Fantasy', 'Het verhaal van Bilbo Baggins die op een avontuur gaat om een schat te vinden bewaakt door de draak Smaug.', '9789022557402', 350, 'Boekerij', 2012, 18.99, 'hobbit.jpg'),
('Het Achterhuis', 'Anne Frank', 'Non-fictie', 'Het dagboek dat Anne Frank schreef terwijl ze ondergedoken zat tijdens de Tweede Wereldoorlog.', '9789044646924', 350, 'Prometheus', 2008, 14.95, 'achterhuis.jpg'),
('De Ontdekking van de Hemel', 'Harry Mulisch', 'Literaire fictie', 'Een omvangrijke roman over vriendschap, liefde en metafysica.', '9789023464044', 927, 'De Bezige Bij', 1992, 19.99, 'hemel.jpg'),
('Girl on the Train', 'Paula Hawkins', 'Thriller', 'Een psychologische thriller over een vrouw die vanuit de trein een moord gezien denkt te hebben.', '9789400506022', 325, 'A.W. Bruna', 2015, 10.99, 'train.jpg'),
('De Vliegeraar', 'Khaled Hosseini', 'Literaire fictie', 'Een verhaal over vriendschap, verraad en verlossing in Afghanistan.', '9789023454939', 367, 'De Bezige Bij', 2007, 13.99, 'vliegeraar.jpg'),
('Het leven van een Loser', 'Jeff Kinney', 'Jeugd', 'De grappige dagboeknotities van Bram Botermans die worstelt met het leven op de middelbare school.', '9789026136184', 224, 'De Fontein', 2009, 14.99, 'loser.jpg'),
('De Alchemist', 'Paulo Coelho', 'Literaire fictie', 'Een verhaal over een jonge schaapherder die op zoek gaat naar een schat en zichzelf tegenkomt.', '9789029587136', 239, 'De Arbeiderspers', 1994, 12.50, 'alchemist.jpg'),
('De Hongerspelen', 'Suzanne Collins', 'Young Adult', 'In een dystopische toekomst moet een meisje deelnemen aan een strijd op leven en dood die live wordt uitgezonden.', '9789000356553', 398, 'Van Holkema & Warendorf', 2010, 16.99, 'hongerspelen.jpg'),
('Het Rosie Project', 'Graeme Simsion', 'Romantiek', 'Een professor met autistische trekken begint een wetenschappelijk project om een vrouw te vinden.', '9789022567784', 304, 'Boekerij', 2013, 10.99, 'rosie.jpg');
```

# Beoordelingscriteria Bookstore Catalog Project

## Overzichtspagina

| Criterium                         | Onvoldoende                                 | Voldoende                                       | Goed                                                                      |
| --------------------------------- | ------------------------------------------- | ----------------------------------------------- | ------------------------------------------------------------------------- |
| **Basisweergave van boeken**      | Boeken worden niet of nauwelijks getoond    | Boeken worden correct weergegeven               | Boeken worden aantrekkelijk weergegeven met duidelijke visuele hiërarchie |
| **Filter op genre**               | Filter werkt niet of met ernstige fouten    | Filter werkt, maar heeft kleine gebreken        | Filter werkt perfect en is gebruiksvriendelijk                            |
| **Filter op auteur**              | Filter werkt niet of met ernstige fouten    | Filter werkt, maar heeft kleine gebreken        | Filter werkt perfect en is gebruiksvriendelijk                            |
| **Sortering op prijs**            | Sortering werkt niet of met ernstige fouten | Sortering werkt, maar heeft kleine gebreken     | Sortering werkt perfect en is gebruiksvriendelijk                         |
| **Doorklikken naar detailpagina** | Links werken niet of met ernstige fouten    | Links werken, maar zijn niet optimaal geplaatst | Links werken perfect en zijn intuïtief                                    |

## Detailpagina

| Criterium                           | Onvoldoende                               | Voldoende                          | Goed                                                   |
| ----------------------------------- | ----------------------------------------- | ---------------------------------- | ------------------------------------------------------ |
| **Weergave van boek details**       | Details worden niet of nauwelijks getoond | Details worden correct weergegeven | Details worden uitgebreid en aantrekkelijk weergegeven |
| **Teruglink naar overzichtspagina** | Link werkt niet of is niet aanwezig       | Link is aanwezig en werkt          | Link is duidelijk zichtbaar en gebruiksvriendelijk     |

## Algemene aspecten

| Criterium              | Onvoldoende                                | Voldoende                                      | Goed                                           |
| ---------------------- | ------------------------------------------ | ---------------------------------------------- | ---------------------------------------------- |
| **Database connectie** | Query's werken niet of met ernstige fouten | Query's werken, maar zijn niet geoptimaliseerd | Query's werken goed en zijn geoptimaliseerd    |
| **Code kwaliteit**     | Rommelige code met veel fouten             | Redelijk nette code met enkele fouten          | Nette, goed gestructureerde code zonder fouten |

## Beoordeling

De beoordeling wordt gebaseerd op de volgende niveaus:
- **Onvoldoende**: Het project voldoet niet aan de basisvereisten
- **Voldoende**: Het project voldoet aan de basisvereisten
- **Goed**: Het project voldoet aan alle vereisten en toont extra aandacht voor gebruikerservaring en code kwaliteit
