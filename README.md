🎬 Tech & Story Lab
Et kreativt univers for teknologi, fortællinger og eksperimenter.
🚧 Projektet er stadig under udvikling. Flere sider mangler færdig styling og endelige billeder. Nogle funktioner er foreløbige eller kun lavet som demonstrationer.

✨ Om projektet
Tech & Story Lab er et website, der præsenterer labbets muligheder, udstyr, studios, workshops og menneskerne bag. Målet er at gøre det nemt at finde inspiration, udforske faciliteter og opdage arrangementer. Sitet er udviklet i Astro med genanvendelige komponenter, CSS og JavaScript/TypeScript. Indhold om blandt andet workshops, udstyr og team hentes fra Supabase.
🔗 Links

- GitHub-repository
- Live website: Tilføjes, hvis projektet publiceres
- Figma: Tilføjes, hvis relevant
  🧰 Teknologier
- Astro 7 – sider, layouts, komponenter og routing.
- HTML – semantisk struktur i .astro-filerne.
- CSS – global styling og komponenternes egne styles.
- JavaScript/TypeScript – interaktioner, formularer, karruseller og databehandling.
- Supabase REST API – dynamiske data om workshops, udstyr og team.
- Node.js og npm – installation og lokal udvikling.
  📁 Projektstruktur
  tech.story.lab.site-main/
  ├── public/ # Favicon og offentlige filer
  ├── src/
  │ ├── assets/ # Billeder, logoer, SVG og produktbilleder
  │ ├── components/ # Genanvendelige Astro-komponenter
  │ ├── layouts/
  │ │ └── BaseLayout.astro
  │ ├── pages/
  │ │ ├── index.astro
  │ │ ├── events.astro
  │ │ ├── udstyr.astro
  │ │ ├── om.astro
  │ │ ├── studios.astro
  │ │ ├── inspiration.astro
  │ │ ├── ny-i-labbet.astro
  │ │ ├── for-undervisere.astro
  │ │ └── Workshops/
  │ │ └── [id].astro
  │ └── styles/
  │ └── global.css
  ├── astro.config.mjs
  ├── package.json
  └── README.md
  🧩 Hvad gør de vigtigste filer?
  Sider (src/pages/)
- index.astro – forsiden med introduktion, kort, inspiration og indhold fra Supabase.
- events.astro – workshops og events, blandt andet med en kalender.
- Workshops/[id].astro – dynamiske detaljesider for workshops baseret på deres ID.
- udstyr.astro – oversigt over udstyr med data fra Supabase.
- om.astro – præsentation af Tech & Story Lab og teamet.
- studios.astro, inspiration.astro, ny-i-labbet.astro og for-undervisere.astro – sider, der i den uploadede version primært fungerer som sider under opbygning.
  Komponenter (src/components/)
- Header.astro og Footer.astro – navigation og fælles sidefod.
- Hero.astro – hero-sektioner med tekst og billede.
- Card.astro, EventCard.astro, WorkshopCard.astro og TeamCard.astro – forskellige korttyper.
- CardKarrusel.astro – vandret karrusel med knapper og scroll-interaktion.
- Kalender.astro – interaktiv SVG-kalender og tilhørende workshopkort.
- BookingForm.astro – formular til workshoptilmelding.
- Galleri.astro, ImageText.astro, NyILabbet.astro, Section.astro og Watermark.astro – indholds- og designelementer, som kan genbruges.
- Button.astro – fælles knapkomponent.
  Fælles opsætning
- BaseLayout.astro – grundlayout, som siderne bygges ind i.
- global.css – fælles designregler, farver og typografi.
- package.json – afhængigheder og kommandoer til udvikling og build.
  ⚙️ Hvordan fungerer koden?

1. Astro og komponenter
   I stedet for at skrive den samme HTML igen på hver side bruger projektet Astro-komponenter. En side importerer de komponenter, den skal bruge, og sender indhold til dem via props. Det gør det lettere at genbruge designet og rette det ét sted.
2. Data fra Supabase
   Forsiden henter data fra tabellerne Udstyr, Teamet og Workshops. Event- og workshop-siderne henter også workshopdata via Supabases REST API. Dataene kommer som JSON og bruges til at opbygge indhold på siderne.

Et forenklet eksempel på workshopdata, baseret på felterne i koden:
{
"id": "workshop-id",
"name": "Introduktion til foto",
"date": "27. MARTS",
"description": "Beskrivelse af workshoppen",
"image": "https://example.com/billede.webp"
}
id identificerer workshoppen, name er titlen, date er datoen, description er beskrivelsen, og image bruges som billede. 3. Dynamiske workshopsider
src/pages/Workshops/[id].astro bruger Astos getStaticPaths() til at oprette en side for hvert workshop-ID, der hentes fra Supabase under build. Siden henter derefter den relevante workshop og viser navn, dato, beskrivelse, billede og bookingformular.

Flow: Workshopdata hentes → workshop-ID bruges i URL'en → detaljesiden viser data → brugeren kan udfylde formularen. 4. Kalender og karrusel
Kalender.astro viser en SVG-kalender og et workshopkort. JavaScript henter workshopdata og kobler interaktioner til kalenderen. CardKarrusel.astro bruger blandt andet klik- og scroll-events til at navigere mellem kort. 5. Bookingformular – vigtig begrænsning
BookingForm.astro har felter til navn, telefonnummer og e-mail samt HTML-validering. Når formularen indsendes, forhindrer JavaScript den normale indsendelse og viser en bekræftelse. Der bliver endnu ikke sendt eller gemt en reel booking. Bekræftelsen er altså en demonstration af brugeroplevelsen og ikke en garanti for en reserveret plads.
🏷️ Navngivning og kommentarer
Projektet bruger beskrivende komponentnavne som BookingForm, WorkshopCard og CardKarrusel. Astro-komponenterne har typisk PascalCase, mens variabler og funktioner i JavaScript/TypeScript bruger camelCase, eksempelvis workshopsData, initKalender og initBookingForm.

Der er kommentarer i flere filer, som blandt andet forklarer hentning af workshops, initialisering og formularens adfærd. Flere steder bruges TypeScript-interfaces til at beskrive de data, koden forventer.
🎨 Design og billeder
Projektet bruger både lokale PNG-, JPG-, WebP- og SVG-filer. Billeder, logoer og grafiske vandmærker ligger i src/assets/, og designet er fordelt mellem global.css og styles i de enkelte Astro-komponenter.

Status: Det visuelle udtryk er endnu ikke færdigt. Der mangler styling på dele af sitet, og nogle billeder skal udskiftes eller tilføjes. Det er derfor forventeligt, at siderne ikke fremstår helt ens eller færdige endnu.
🌱 Digital bæredygtighed og performance
Vi har bygget siden med genanvendelige komponenter, så den samme struktur og styling ikke skal skrives flere gange. Flere billeder er i WebP-format, som ofte kan reducere filstørrelsen sammenlignet med større billedformater.

Der er stadig mulighed for optimering. I den uploadede version findes også forholdsvis store billed- og SVG-filer, så det vil være relevant at gennemgå billedernes størrelse, komprimering og indlæsning, når det endelige billedmateriale er på plads. Vi har ikke dokumenteret en målt page weight eller Lighthouse-score endnu.
🧪 Test og fejlfinding
Ved videreudvikling er det især relevant at teste:

- Om Supabase-data bliver hentet korrekt, og hvad der sker ved netværksfejl.
- Om links fra kalender og eventkort åbner den rigtige workshop.
- Om formularens validering og bekræftelse fungerer som forventet.
- Om navigation, karruseller og billeder fungerer på mobil og desktop.
- Om billeder har korrekte stier, og om alle sider har færdig styling.
  Det kan undersøges med browserens udviklerværktøjer, konsollen og Network-fanen. Denne liste er forslag til test, ikke en påstand om, at alle test allerede er udført.
  🚧 Det mangler vi / mulige forbedringer
- Færdiggøre styling og responsive tilpasninger på tværs af siderne.
- Indsætte og udskifte de sidste billeder.
- Færdiggøre indholdet på de sider, der stadig er under opbygning.
- Implementere rigtig håndtering og lagring af workshopbookinger, hvis funktionen skal bruges i praksis.
- Forbedre fejl- og loadingtilstande ved API-kald.
- Gennemgå tilgængelighed, herunder tastaturnavigation og billedtekster.
- Optimere store billed- og SVG-filer og måle performance.
- Overveje at samle gentaget Supabase-opsætning i en fælles datafunktion og bruge miljøvariabler til konfiguration.
  🌿 Git og samarbejde
  Projektet ligger på GitHub og kan versionsstyres med Git. Den uploadede ZIP-fil indeholder ikke Git-historikken, så det er ikke muligt at beskrive præcist, hvordan branches, commits og samarbejde er blevet brugt. Dette afsnit kan udbygges med jeres faktiske arbejdsproces og erfaringer.
  👥 Udviklere
  Tilføj navne på gruppemedlemmerne.
  🚀 Sådan startes projektet
  Projektet kræver Node.js 22.23.4 eller nyere ifølge package.json samt npm.

1. Klon repositoryet:
   git clone https://github.com/Kkrattet/tech.story.lab.site.git
2. Åbn mappen og installer afhængigheder:
   cd tech.story.lab.site
   npm install
3. Start udviklingsserveren:
   npm run dev
4. Åbn den lokale adresse, som Astro viser i terminalen (typisk http://localhost:4321).
   Andre kommandoer:
   npm run build # Byg sitet til produktion
   npm run preview # Se det byggede site lokalt
   Der skal være internetforbindelse for at hente indhold fra Supabase. Ved build afhænger genereringen af workshopsider også af, at workshopdata kan hentes.
   README'en beskriver den uploadede projektversion fra november 2026. Den kan opdateres løbende, efterhånden som styling, billeder, indhold og funktioner bliver færdige.
