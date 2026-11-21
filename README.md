# Spotify Soundboard

Ett soundboard med 30 knappar per flik och 10 flikar (300 låtar totalt) som laddas från en Spotify-spellista. Varje knapp är en låt, och du kan sätta en startpunkt (cue) per låt. Appen är en enda sida som körs i webbläsaren, och ljudet spelas av Spotify-appen.

**Öppna appen:** https://sefreon1.github.io/Spotify-Soundboard/

Du behöver inte installera något eller ladda ner någon fil. Öppna länken i Chrome på plattan, telefonen eller datorn och följ stegen nedan.

## Krav

- **Spotify Premium** (krävs för att styra uppspelning).
- **Internet** på enheten. Varje knapptryck är ett litet kommando till Spotify, så dela mobilnät om hallen saknar wifi.
- **Spotify-appen** installerad och inloggad på samma konto på den enhet som ska spela.
- En spellista som **du själv äger** (Spotify lämnar bara ut innehållet för egna spellistor).

## Så fungerar det med dina uppgifter

Varje användare skapar **sin egen Spotify-app** (del 1 nedan) och får ett eget **Client ID**. Det beror på att Spotify begränsar en app i utvecklarläge till högst 5 användare. Du lägger in ditt Client ID i soundboardet, och det sparas bara i din egen webbläsare. Sidan på GitHub är bara en fil och sparar ingenting om dig. Ditt Client ID är inte hemligt, men dela det ändå inte med andra.

---

## Del 1: Skapa en Spotify-app och hämta Client ID

Du behöver ett **Client ID** från Spotify. Det är ett långt id som identifierar din app. Du behöver **inget Client Secret**.

> **Tips för mobil:** Spotifys sida visar inte knappen "Create app" i mobilvyn. Tryck på ⋮ i Chrome och välj **Datorversion** (Desktop site), eller gå direkt till `https://developer.spotify.com/dashboard/create`.

1. Gå till **https://developer.spotify.com/dashboard** och logga in med ditt Spotify-konto (Premium).
2. Tryck **Create app**.
3. Fyll i formuläret:
   - **App name:** `Soundboard` (valfritt namn)
   - **App description:** `Soundboard för spellista` (valfri text)
   - **Website:** lämna tomt
   - **Redirect URIs:** skriv in exakt
     `https://sefreon1.github.io/Spotify-Soundboard/`
     och tryck **Add** så att den hamnar i listan under fältet.
     Adressen måste stämma tecken för tecken, inklusive `https://` och snedstrecket sist.
   - **Which API/SDKs are you planning to use?** Kryssa i **Web API**.
   - Kryssa i att du godkänner Spotifys *Developer Terms of Service*.
4. Tryck **Save**.
5. Du hamnar på appens sida. Tryck **Settings** (uppe till höger).
6. Under **Basic Information** hittar du **Client ID**. Det är en lång rad med bokstäver och siffror. Tryck för att markera och **kopiera** den.
7. Gå till fliken **User Management** och lägg till ditt eget Spotify-konto (namn och den e-postadress du använder på Spotify) om det inte redan finns.

---

## Del 2: Fyll i Client ID i appen och logga in

1. Öppna **https://sefreon1.github.io/Spotify-Soundboard/** i Chrome. Inställningsrutan öppnas automatiskt första gången. Annars trycker du på **⚙**.
2. Under **1. Spotify-inloggning**:
   - Klistra in **Client ID** som du kopierade i fältet "Client ID".
   - Kontrollera att **Redirect URI** som visas i rutan är exakt samma som den du la in i Spotify-appen.
   - Tryck **Logga in med Spotify**.
3. Spotify frågar om du vill ge appen åtkomst. Tryck **Godkänn** (Agree). Du skickas tillbaka till soundboardet och ser **● Inloggad**.
4. Under **2. Spellista**: tryck **Hämta mina**, välj spellistan i listan (eller klistra in länken till den) och tryck **Ladda in i soundboardet**.
5. Öppna **Spotify-appen** på samma enhet, spela en låt i ett par sekunder och låt appen ligga kvar i bakgrunden.
6. Under **3. Spelare**: tryck **Uppdatera** och välj din enhet i listan.
7. Tryck **Stäng** och tryck på en låt.

Client ID och inloggning sparas på enheten. Du behöver bara göra det här en gång per enhet.

---

## Så använder du soundboardet

**Färger**

| Färg | Betydelse |
|---|---|
| Grön | Låten är redo |
| Blå | Låten spelas |
| Ljusröd | Låten har spelats |
| Vit ram + NÄSTA | Nästa låt som spelas när du trycker ▶ SPELA |

**Knappar**

- **▶ SPELA** spelar låten med ramen. **■ STOPP** stoppar. **↘ FADE** tonar ut (se begränsningar nedan).
- Tryck på en **grön** eller **röd** låt för att spela den. Tryck på en **blå** låt för att stoppa den.
- **↺ Alla gröna** gör alla låtar i den flik du står på gröna igen. När du byter flik blir alla låtar i den fliken gröna.
- **⏱ Sätt cue här** sparar nuvarande position i låten som startpunkt.

**Flaggor och filter**

Varje låt kan flaggas som **Uppvärm**, **Paus**, **Mål** eller **Utvis**. Flaggan syns som en liten färgad etikett på knappen. Raden högst upp filtrerar spellistan:

- **Alla** visar hela spellistan, **Uppvärm / Paus / Mål / Utvis** visar bara låtar med den flaggan och **Oflaggade** visar låtar som saknar flagga. Siffran är antal låtar.
- Spellistan kan alltså vara blandad. Du behöver inte sortera den i Spotify, eftersom filtret samlar låtarna åt dig.
- Visar ett filter fler än 30 låtar delas de upp på flikarna 1, 2, 3 och så vidare (30 per flik).
- När du byter filter blir alla låtar gröna igen.

**Redigera-läge (✎ Redigera)**

Tryck ✎ Redigera. Då visas en rad med val under knapparna: **Tryck på låt:**

- **Ställ in cue:** tryck på en låt och skriv startpunkt, till exempel `0:42.5`. Finjustera med −1 s, −0,5, +0,5 och +1 s.
- **Uppvärm / Paus / Mål / Utvis:** välj en flagga och tryck sedan på de låtar som ska ha den. Varje tryck flaggar direkt, så du kan flagga många låtar snabbt. Byt flagga när du vill.
- **Ta bort flagga:** tryck på låtar som ska bli oflaggade.
- Tryck på en **flik** för att ge den ett namn, till exempel `Efter mål`. Flik-namnen sparas separat för varje filter.
- Tryck ✎ Redigera igen för att gå tillbaka till spelläget. Först då uppdateras listan efter det filter som är valt.

**Flera spellistor och sparade inställningar**

Cue-punkter, flaggor och flik-namn sparas **separat för varje spellista** på enheten. Laddar du in en annan spellista och sedan tillbaka den första finns allt kvar. Under ⚙ → *2. Spellista* finns **Sparade spellistor**, där du kan byta mellan listor du laddat in tidigare utan att hämta dem från Spotify igen. Vill du uppdatera en lista med nya låtar använder du **Ladda in från Spotify**. Dina flaggor och cue-punkter följer med låtarna.

**Säkerhetskopia:** under ⚙ → *4. Säkerhetskopia* kan du **Exportera** cue-punkter, flaggor och flik-namn för den spellista som är laddad och **Importera** dem igen, till exempel på en ny enhet.

---

## Begränsningar

- **Kräver internet.** Spotifys API fungerar inte offline, även om låtarna är nedladdade i Spotify-appen.
- **Fade** fungerar bara om uppspelningsenheten tillåter volymstyrning från Spotify, vilket brukar gå på dator. På Android-mobiler och surfplattor gör Spotify det oftast inte, och då stoppas låten direkt med ett meddelande. Efter en fade sätts volymen tillbaka först när Spotify har pausat.
- **Fördröjning:** räkna med ungefär 0,3–1 sekund från tryck till ljud. Testa med riktigt mobilnät innan du använder det på plats.
- **Ingen mixning:** Spotify kan bara spela en låt åt gången.
- Spellistor du inte äger kan inte läsas in.
- Max 5 användare per Spotify-app (utvecklarläge) och ägarkontot måste ha Premium.

---

## Felsökning

| Meddelande eller problem | Lösning |
|---|---|
| `INVALID_CLIENT: Invalid redirect URI` vid inloggning | Redirect URI i din Spotify-app stämmer inte exakt med den som visas i ⚙. Kontrollera `https://`, användarnamn, repo-namn och snedstrecket sist, och tryck **Save** igen. |
| *Ingen aktiv enhet* | Öppna Spotify-appen på enheten, spela en låt en sekund, och tryck **Uppdatera** under *3. Spelare* i ⚙ och välj enheten. |
| Enheten syns inte i listan | Kontrollera att Spotify-appen är inloggad på samma konto, inte i offline-läge, och starta om den. |
| *Spotify nekade (403)* | Kontot saknas under **User Management** i din Spotify-app, eller så har ägarkontot inte Premium. |
| *Premium krävs* | Uppspelningsstyrning kräver Spotify Premium. |
| *För många anrop* (429) | Vänta en stund och försök igen. |
| *Bad gateway* (502) | Tillfälligt fel hos Spotify. Appen försöker automatiskt en gång till. Tryck annars igen efter en stund. |
| Enheten (datorn) hittas inte | Öppna Spotify-programmet, spela en låt en sekund, tryck **Uppdatera** under *3. Spelare* i ⚙ och välj enheten igen. Enhetens id byts när Spotify startas om. |
| Inga låtar laddas | Spellistan måste ägas av dig. Prova att välja den i listan under **Hämta mina**. |
| Ändringar syns inte efter uppdatering | Webbläsaren cachar. Vänta 1–2 minuter och öppna adressen med `?v=2` sist. |
| Logga in igen | ⚙ → **Logga ut** och sedan **Logga in med Spotify**. |

---

## Valfritt: egen kopia av appen

Du behöver bara det här om du vill köra en egen version, till exempel för att ändra koden.

1. Gör en kopia (Fork) av repot på GitHub, eller skapa ett nytt repo och ladda upp `index.html`.
2. Gå till **Settings → Pages**, välj **Deploy from branch**, branch **main**, mapp **/ (root)** och tryck **Save**.
3. Efter 1–2 minuter ligger appen på `https://DITT-ANVÄNDARNAMN.github.io/REPO-NAMN/`.
4. Använd den adressen (med snedstreck på slutet) som **Redirect URI** i din Spotify-app i del 1 i stället för adressen ovan.

Appen går inte att köra genom att öppna `index.html` direkt från mappen på datorn, eftersom Spotify kräver en `https://`-adress för inloggningen.
