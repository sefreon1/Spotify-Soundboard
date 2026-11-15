# Spotify Soundboard

Ett soundboard med 30 knappar per flik och 10 flikar (300 låtar totalt) som laddas från en Spotify-spellista. Varje knapp är en låt, och du kan sätta en startpunkt (cue) per låt. Appen är en enda fil (`index.html`) som körs i webbläsaren, och ljudet spelas av Spotify-appen.

## Krav

- **Spotify Premium** (krävs för att styra uppspelning).
- **Internet** på enheten. Varje knapptryck är ett litet kommando till Spotify, så dela mobilnät om hallen saknar wifi.
- **Spotify-appen** installerad och inloggad på samma konto på den enhet som ska spela.
- En spellista som **du själv äger** (Spotify lämnar bara ut innehållet för egna spellistor).

---

## Del 1: Lägg appen på GitHub Pages

1. Skapa ett repo på GitHub, till exempel `Spotify-Soundboard`.
2. Ladda upp `index.html` (och den här filen) till repot: **Add file → Upload files → Commit changes**.
3. Gå till **Settings → Pages**. Under *Build and deployment* väljer du **Deploy from a branch**, branch **main** och mapp **/ (root)**, och trycker **Save**.
4. Efter 1–2 minuter ligger appen på:

   ```
   https://DITT-ANVÄNDARNAMN.github.io/Spotify-Soundboard/
   ```

   Exempel: `https://sefreon1.github.io/Spotify-Soundboard/`

   Det här är din **Redirect URI**. Du behöver den exakt som den står, med snedstreck på slutet, i nästa del.

---

## Del 2: Skapa en Spotify-app och hämta Client ID

Du behöver ett **Client ID** från Spotify. Det är ett långt id som identifierar din app. Du behöver **inget Client Secret**.

> **Tips för mobil:** Spotifys sida visar inte knappen "Create app" i mobilvyn. Tryck på ⋮ i Chrome och välj **Datorversion** (Desktop site), eller gå direkt till `https://developer.spotify.com/dashboard/create`.

1. Gå till **https://developer.spotify.com/dashboard** och logga in med ditt Spotify-konto (Premium).
2. Tryck **Create app**.
3. Fyll i formuläret:
   - **App name:** `Soundboard` (valfritt namn)
   - **App description:** `Soundboard för spellista` (valfri text)
   - **Website:** lämna tomt (eller skriv din GitHub Pages-adress)
   - **Redirect URIs:** klistra in din adress från del 1, till exempel
     `https://sefreon1.github.io/Spotify-Soundboard/`
     och tryck **Add** så att den hamnar i listan under fältet.
     Adressen måste stämma tecken för tecken, inklusive `https://` och snedstrecket sist.
   - **Which API/SDKs are you planning to use?** Kryssa i **Web API**.
   - Kryssa i att du godkänner Spotifys *Developer Terms of Service*.
4. Tryck **Save**.
5. Du hamnar på appens sida. Tryck **Settings** (uppe till höger).
6. Under **Basic Information** hittar du **Client ID**. Det är en lång rad med bokstäver och siffror. Tryck för att markera och **kopiera** den.
7. Gå till fliken **User Management** och lägg till ditt eget Spotify-konto (namn och den e-postadress du använder på Spotify) om det inte redan finns. Spotify tillåter högst **5 användare** för en app i utvecklarläge, vilket räcker för eget bruk.

---

## Del 3: Fyll i Client ID i appen och logga in

1. Öppna din adress (`https://DITT-ANVÄNDARNAMN.github.io/Spotify-Soundboard/`) i Chrome på plattan eller telefonen. Inställningsrutan öppnas automatiskt första gången. Annars trycker du på **⚙**.
2. Under **1. Spotify-inloggning**:
   - Klistra in **Client ID** som du kopierade i fältet "Client ID".
   - Kontrollera att **Redirect URI** som visas i rutan är exakt samma som den du la in i Spotify-appen. Är den inte det, ändra i Spotify-appen så att den stämmer.
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

**Redigera-läge (✎ Redigera)**

- Tryck på en **låt** för att ställa in startpunkt (cue) för just den låten, till exempel `0:42.5`. Finjustera med −1 s, −0,5, +0,5 och +1 s.
- Tryck på en **flik** för att ge den ett namn, till exempel `Uppvärmning`.
- Tryck ✎ Redigera igen för att gå tillbaka till spelläget.

**Säkerhetskopia:** under ⚙ → *4. Cue-punkter* kan du **Exportera** cue-punkter och flik-namn som text och **Importera** dem igen, till exempel på en ny enhet.

---

## Begränsningar

- **Kräver internet.** Spotifys API fungerar inte offline, även om låtarna är nedladdade i Spotify-appen.
- **Fade** fungerar bara om uppspelningsenheten tillåter volymstyrning från Spotify. På Android-mobiler och surfplattor gör Spotify det oftast inte, och då stoppas låten direkt med ett meddelande.
- **Fördröjning:** räkna med ungefär 0,3–1 sekund från tryck till ljud. Testa med riktigt mobilnät innan du använder det på plats.
- **Ingen mixning:** Spotify kan bara spela en låt åt gången.
- Spellistor du inte äger kan inte läsas in.
- Max 5 användare per Spotify-app (utvecklarläge) och ägarkontot måste ha Premium.

---

## Felsökning

| Meddelande eller problem | Lösning |
|---|---|
| `INVALID_CLIENT: Invalid redirect URI` vid inloggning | Redirect URI i Spotify-appen stämmer inte exakt med den som visas i ⚙. Kontrollera `https://`, användarnamn, repo-namn och snedstrecket sist, och tryck **Save** igen. |
| *Ingen aktiv enhet* | Öppna Spotify-appen på enheten, spela en låt en sekund, och tryck **Uppdatera** under *3. Spelare* i ⚙ och välj enheten. |
| Enheten syns inte i listan | Kontrollera att Spotify-appen är inloggad på samma konto, inte i offline-läge, och starta om den. |
| *Spotify nekade (403)* | Kontot saknas under **User Management** i Spotify-appen, eller så har ägarkontot inte Premium. |
| *Premium krävs* | Uppspelningsstyrning kräver Spotify Premium. |
| *För många anrop* (429) | Vänta en stund och försök igen. |
| Inga låtar laddas | Spellistan måste ägas av dig. Prova att välja den i listan under **Hämta mina**. |
| Ändringar syns inte efter uppdatering | GitHub Pages cachar. Vänta 1–2 minuter och öppna adressen med `?v=2` sist. |
| Logga in igen | ⚙ → **Logga ut** och sedan **Logga in med Spotify**. |
