# mohibas_oblig1 - Obligatorisk innlevering

# Introduksjon

I denne obligen skal du lage en applikasjon i Android Studio. Her vil du bli kjent
med forskjellige verktøy, og noen nyttige komponenter som ofte brukes i
Android-utvikling. Kotlin skal benyttes som programmeringsspråk, og Jetpack
Compose til design. Det er ingen krav til hvordan appen skal se ut, utover det som er
spesifisert i oppgaveteksten. Denne obligen skal løses individuelt, og for å få den
godkjent må alle deloppgaver være gjort og appen skal kunne kjøres i en emulator
med API-level 30 uten å krasje. Under retting vil en Google Pixel 5 emulator med
API level 30 benyttes. Hvis du tester på egen Android-enhet, spesifiser
Android-versjon i kommentarfeltet på Devilry.
Oppgaven
Oppgaven er tredelt: du skal lage en app med tre ulike funksjonaliteter.
Hver funksjonalitet skal være i hver sin Screen. Navigasjon imellom disse skal skje
med navigasjonsbiblioteket til Compose.
1. Lage en palindrom-sjekker.
2. Lage en konverterer.
3. Bruke objektorientering til å lage en liten quiz.

## Levering

Trykk på “Build” → “Clean Project”, deretter skal mappen som inneholder Android
Studio-prosjektet skal komprimeres til en zip/tar-fil, og leveres i Devilry innen
fristen fredag 10. februar 23:59.


## Nyttige ressurser

● https://developer.android.com/jetpack/compose/tutorial

● https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary

● https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#ExposedDropdownMenuBox(kotlin.Boolean,kotlin.Function1,androidx.compose.ui.Modifier,kotlin.Function1)

● Navigasjon mellom skjermer:

https://developer.android.com/jetpack/compose/navigation

● https://m3.material.io/components/snackbar/overview

## Komme i gang

Opprett et nytt Android Studio-prosjekt, sett prosjektnavn til:
[ditt uio-brukernavn]_oblig1.

Videre velger du “Empty Compose Activity (Material 3)” og “Kotlin” som
programmeringsspråk.

Velg API 23 som target SDK/Minimum API Level.

## Versjoner og gradle

Siden versjonene som automatisk settes på de forskjellige pakkene av android studio
når prosjektet opprettes kan avvike med de som er i dokumentasjonen kan det oppstå
problemer med å benytte seg av eksempler fra dokumentasjonen. Det kan derfor
hende man må gjøre noe i byggsystemet gradle sine konfigurasjonsfiler for å få
eksemplene til å funke. Sørg for at du har nyeste versjon av android studio installert
(electric eel). Dersom du får problemer burde endringene under fikse det

I build.gradle modul-filen kan man trenge å endre compose sin kompilator
(kotlinCompilerExtensionVersion) fra versjon 1.2.0 til 1.4.0. Per dags dato er den
nyeste versjonen av material3 1.1.0-alpha05 så oppdater også denne.
I prosjektet sin build.gradle endre “compose_version” til 1.3.3 Endre også
avhengigheten org.jetbrains.kotlin.android til 1.8.0 i denne fila.

# Del 0 - Forberede filer og sette opp navigasjon

Start med å lage tre sub-pakker i ui-mappen for hver av deloppgavene. Opprett
deretter 3 filer i hver av disse mappene slik at filstiene blir som følger:

- ui/palindrom/PalindromeScreen.kt
- ui/unitconverter/UnitConverterScreen.kt
- ui/quiz/QuizScreen.kt

Eksempelet viser altså tre mapper (palindrom, unitconverter og quiz) som hver har en
Kotlin-fil i seg. I hver av disse filene skal du ha en composable med samme navn som
fila og en tekst som sier hvilken skjerm man er på.

F.eks. så skal du ha en composable-funksjon med navn PalindromeScreen som
inneholder en “Text” der det står “PalindromeScreen” i PalindromeScreen.kt.

##Sette opp navigasjon
For å navigere mellom skjermene skal du benytte deg av compose sitt
navigasjonsbibliotek. Du trenger ikke å gjøre dette for å begynne og lage skjermene,
du kan lage skjermene for alle deloppgavene allerede nå hvis du ønsker.

Det skal settes opp 3 navigasjons-ruter:

- “palindrome” skal kobles opp til PalindromeScreen()-funksjonen
- “unitconverter” skal kobles opp til UnitConverterScreen()-funksjonen
- “quiz” skal kobles opp til QuizScreen()-funksjonen der “palindrome” skal være satt som startDestination.

## Del 1 - Palindrom
I denne deloppgaven skal du lage den første skjermen: en palindrom-sjekker som
skal hete PalindromeScreen. Denne skjermen skal kort forklart: ta input fra bruker,
sjekke om input er et palindrom eller ikke og vise resultatet til brukeren.
Et palindrom er et stykke tekst som er identisk sett både forfra og bakfra. I denne
oppgaven skal dere se bort fra om bokstavene er store eller små, slik at strengen
“Hannah” er et palindrom. 

Eksempler:
Palindrom Ikke palindrom
“bob” “ivar”
“Hannah” “Alpakka”
“123454321” “1234”

### PalindromeScreen skal inneholde følgende composables og funksjonalitet

**TextField** skal ta input fra bruker.Skal ha en label som redegjør for hva brukeren skal skrive inn.

**Button**(1) skal kjøre en funksjon som sjekker om gitt input er et palindrom eller ikke.

**Text** som viser resultat:

● Skal vise til brukeren om input er et palindrom eller ikke.

**Button**(2) sender brukeren til neste skjerm:

● Knappen skal plasseres helt nederst på
skjermen.

● Knappen skal være like bred som
skjermen.

### Viktig:
● Alle elementer i skjermen skal være midtstilt.

● Legg til funksjonalitet som gjør at TextField tømmes for innhold når brukeren
trykker på Button(1).

● Legg til funksjonalitet som gjør at skjermtastaturet lukker seg når brukeren
trykker på Button(1). Benytt dere av LocalFocusManager.current og
localFocusManager.clearFocus()

### Filnavn:
ui/palindrome/PalindromeScreen.kt


## Del 2 - Konverterer

I denne deloppgaven skal du lage skjermen ConverterScreen. Denne skjermen skal
konvertere volum i form av væske fra det imperiske system til liter (L). Det skal være
mulig å konvertere fra følgende imperiske enheter: fluid ounce (fl oz), cup (cp), gallon
(gal) og hogshead.

### Konverteringstabell

*1,0 fluid ounce = 0,02957 L

*1,0 cup = 0,23659 L

*1,0 gallon = 3,78541 L

*1,0 hogshead = 238,481 L

De fire ulike imperiske enhetene skal vises i en ExposedDropdownMenu slik at
brukeren enkelt kan velge hvilken enhet det ønskes å konvertere fra. For å gjøre dette
skal du lage en string-array i strings.xml-filen og legge inn de imperiske enhetene.

### Viktig:
● Tastaturet skal være et talltastatur (numpad).

● Appen skal ikke krasje ved ugyldig (f.eks. tekst eller tom input), og da heller
vise en feilmelding til bruker i form av en Snackbar.

● Outputen skal kun ha to desimaler.

● Legg til funksjonalitet som gjør at skjermtastaturet lukker seg når brukeren
trykker på Button(1).

### Utforming
Det skal være en TextField-funksjon som tar input fra brukeren. Under TextField
skal det være en ExposedDropdownMenu. Under denne skal det plasseres en
Button(1), og når denne blir trykket på, skal inputen konverteres. Resultatet av
konverteringen skal vises i en Text-funksjon. Nederst på skjermen skal det være en
Button(2) som sender brukeren til siste deloppgave (QuizScreen).

### ConverterScreen skal inneholde følgende composables og funksjonalitet
● TextField skal ta input fra bruker.
Skal inneholde et hint som redegjør
for hva brukeren skal skrive inn.

● ExposedDropdownMenu som gjør
det mulig å velge mellom de fire
enhetene nevnt tidligere.

● Button(1) kjører en funksjon som
konverterer inputen basert på hva som
står i Spinner. Tom input skal gi
feilmelding i form av en Snackbar.

● Text skal vise det konverterte
resultatet.


● Button(2) skal sende brukeren til
neste aktivitet. Button(2) skal
plasseres helt nederst på skjermen, og
skal være like bred som skjermen.

### Filnavn:
ui/unitconverter/UnitConverterScreen.kt

## Del 3 - Quiz
I denne deloppgaven skal du utvide QuizScreen som ble opprettet i del 2, og lage en
liten quiz som skal stille minst tre fleip/fakta spørsmål. Du skal benytte deg av
objektorientering, og representere hvert enkelt spørsmål i quizen som et
spørsmål-objekt. Opprett en data class kalt QuizUiState som skal
representere tilstanden til Quiz-skjermen. Denne kan f.eks. bestå av en
List<Question> og hvor mange riktige spørsmål som er besvart, legg til ekstra
data i denne hvis nødvendig. Opprett en data class kalt Question.
Spørsmål-objektene skal inneholde en string: spørsmålet, og boolean: sann/usann.
Spørsmålene må du lage selv, og det skal være minimum tre spørsmål.

### Tips:
  
● Basert på en indeks i QuizUiState (counter) kan Text(1) vise gjeldende
spørsmål.

● Hold orden på indeksene, slik at du ikke prøver å aksessere tomme verdier i
listen.

● La QuizUiState holde styr på hvilket spørsmål som er nåværende.
Viktig:

● Text (2) skal når alle spørsmålene er gjennomgått vise “Poeng: [poeng / antall
mulige poeng]”

● Button(3) skal være en “reset”-knapp som gjør at brukeren kan ta quizen på
nytt.

● True/False-knappene skal bli gjennomsiktige når quizen er gjennomført.

### Filnavn:
ui/quiz/Quiz.kt, ui/quiz/QuizUiState.kt, data/Questions.kt


### QuizScreen skal inneholde følgende composables og funksjonalitet
● Text(1) viser spørsmålene til brukeren.

● Button(1) skal representere “Fakta”. Denne knappen skal være grønn.

● Button(2) skal representere “Fleip”. Denne knappen skal være rød.

● Text(2) skal vise antall poeng. Oppdateres for hvert svar. Riktig svar gir 1 poeng, feil gir 0 poeng.

● Button(3) skal starte quizen på nytt og plasseres helt nederst på skjermen.

