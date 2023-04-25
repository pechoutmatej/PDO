# Webová aplikace pro vizualizaci jízd na motocyklu
---
### Kdo to je
Jedná se o profesora Technické univerzity v Liberci.
### Kde pracuje
Pracuje převážně na budově H liberecké Technické univerzity.
### Co potřebuje
Poptává webovou aplikaci zobrazující data získaná během jízdy na motocyklu.
1. Vytvoření kostry webové stránky  
Celý projekt začínáme tím, že navrhneme základní vzhled celé stránky. V našem případě bude vzhled velice jednoduchý a stručný. Hlavním elementem stránky bude tabulka s vykreslenými daty. Tento element umístíme doprostřed, tak aby vše uživatel okamžitě viděl. Nad tabulku umístíme informace o jízdě ze které jsou data získána, tedy datum a motocykl ze kterého je jízda zaznamenána. Projekt navrhujeme v Expresu, tudíž vše stylizujeme pomocí html a css.
2. Backend
    1. Připojení k databázi  
    Data jsou uložena v databázi MongoDB, ke které se budeme připojovat pomocí knihovny Mongoose. Získáme connection string z klienta MongoDB. Pomocí něj se následně připojíme pomocí příkazu **mongoose.connect("***conection string**"*)**
    2. Získání dat  
    Pro získání dat je nejdříve potřeba vytvořit si schéma dané tabulky, které chceme z databáze získat. Jelikož data z databáze pouze čteme, nemusíme definovat povinnost daných parametrů, tedy zdali by bylo možné vytvořit danou tabulku bez některých atributů.
    ![img1](schema.jpg)
    3. Práce s daty
        1. Vytřízení relevantních dat    
        Získaná data vytřídíme na dvě skupiny, podle toho kam je budeme vykreslovat. První skupina bude vykreslována do již zmíněných informací o jízdě mimo hlavní tabulku a druhá skupina budou již data která budou přímo zobrazena v hlavní tabulce se všemi informacemi.
        2. Datové operace    
        Jedinou datovou operací ktero budeme muset provést je výpočet průměrné rychlosti jízdy. Pro výpočet použijeme vzoreček ve kterém vzdálenost dělíme časem. Musíme si dát pozor na jednotky, čas je v databázi uložen v sekundách, vzdálenost v metrech.
        3. Zpřehlednění dat pro jejich vykreslení  
        Získaná data musíme převést do podoby která více vyhovuje jejich srozumitelnosti ze strany uživatele. Čas je v tabulce uložen pomocí sekund, je tedy potřeba čas převést do formátu **hodiny:minuty:sekundy**. Vzdálenost je potřeba převést na kilometry. Všechna získaná data zaokrouhlujeme na dvě desetinná místa.
3. Frontend
    1. Stylizace webové stránky  
    Tvoříme stránku pro interní použití. Nemusíme tudíž myslet na poutavý design, vynechat prostor pro reklamu či pro upozornění o využívání cookies. Zaměříme se tedy na barevné odlišení jednotlivých segmentů a jejich vizuální úpravu. Horní, informační, panel obsahující data o zobrazované jízdě zobrazíme tmavší barvou, tabulku s daty samotnými vybarvíme světlejším odstínem barvy horního panelu.
    2. Získání a vykreslení dat z backendu  
    Data z backendu propíšeme do frontendu naší aplikace pomocí Node.js frameworku Express.js. Zjednodušeně píšeme HTML dokument, ve kterém místa, kde chceme data zobrazit označíme pomocí znaků procenta.
4. Hostování webové aplikace
    1. Hledání vhodného hostingu  
    Při hledání vhodného hostingu musíme uvažovat nad několika faktory. Jednoduchosti nasazení, cena pronájmu hostingu a například také podpora, kterou budeme moci využít při problémech s chodem či nasazení naší aplikace. V případě placeného hostingu se musíme zaměřit na jednotlivé úrovně předplatného a na jeho jednotlivé výhody. To z důvodu abychom neplatili zbytečně příliš a nebo naopak neměli potíže s malým výkonem serveru.
    2. Zprovoznění aplikace online  
    Velká část dnešních hostingů, zvláště těch které více podporují různé testovací projekty umožňují přímé nahrání kódu přes github. To nám velice zjednodušuje nasazení naší aplikace online, jelikož se její nasazení provede při úspěšném nahrání nové verze na github. V některých případech si hosting nemusí rozumět s použitými styly či knihovnami, je tedy potřeba vše důsledně otestovat, popřípadě zvolit knihovnu či styl jiný.
