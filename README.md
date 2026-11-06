# WordPress onderhoud checklist

Een vaste checklist voor het onderhoud van een WordPress-site: wat je elke week, elke maand, elk kwartaal en elk jaar controleert. Als Markdown (in te vullen op GitHub), als afdrukbare pagina en als logbestand in CSV, zodat je kunt laten zien wat er is gedaan.

Een WordPress-site die niet wordt bijgehouden, wordt vroeg of laat onveilig of traag. De meeste problemen zijn te voorkomen met een uur controle per maand.

## Voor wie

- Eigenaren van een WordPress-site die het onderhoud zelf doen.
- Webbouwers en beheerders die een vaste werkwijze willen voor meerdere sites.

## Wat zit erin

| Bestand | Doel |
|---|---|
| `README.md` | De checklist hieronder |
| `checklist-afdrukbaar.html` | Dezelfde checklist op een A4, om af te drukken of als PDF op te slaan |
| `onderhoudslog.csv` | Sjabloon om elke maand bij te houden wat er is gedaan |

Open `checklist-afdrukbaar.html` in je browser en kies Afdrukken. Daar kun je ook "Opslaan als PDF" kiezen.

## Wekelijks (10 minuten)

- [ ] **Uptime:** is de site bereikbaar? Zet een gratis monitor in (UptimeRobot of vergelijkbaar) met een melding per e-mail.
- [ ] **Formulieren:** stuur een testbericht via je contactformulier en kijk of het aankomt.
- [ ] **Spam en reacties:** haal spam weg en controleer onbekende nieuwe gebruikers.
- [ ] **Beveiligingsmeldingen:** kijk of je beveiligingsplugin of host iets meldt.

## Maandelijks (30 tot 60 minuten)

### Updates

- [ ] **Back-up eerst.** Controleer dat de laatste back-up er is, buiten de server staat en te openen is.
- [ ] **WordPress-core:** werk bij naar de laatste (kleine) release.
- [ ] **Plugins:** werk bij, één voor één bij belangrijke plugins (formulier, webshop, SEO), en kijk na elke update of de site werkt.
- [ ] **Thema:** werk bij. Heb je een child theme, controleer dan of aanpassingen bewaard zijn.
- [ ] **Ongebruikte plugins en thema's:** verwijderen, niet alleen uitschakelen.
- [ ] **Plugins zonder updates:** is een plugin al meer dan een jaar niet bijgewerkt of uit de directory gehaald? Zoek een alternatief.

### PHP en server

- [ ] **PHP-versie:** controleer welke versie draait (Hulpmiddelen, Site Health, Info, Server). Gebruik een versie die beveiligingsupdates krijgt. PHP 8.2 krijgt die tot en met 31 december 2026, PHP 8.3 tot en met 31 december 2027 en PHP 8.4 tot en met 31 december 2028 (bron: php.net). Met [php-eol-check](https://github.com/Joepify/php-eol-check) zie je het vanaf de command line.
- [ ] **Site Health:** open Hulpmiddelen, Site Health en los de punten "Kritiek" en "Aanbevolen" op.
- [ ] **Schijfruimte en geheugen:** ruim op als je host meldt dat het bijna vol is.

### Beveiliging

- [ ] **Beheerders:** staan er alleen mensen die er horen? Verwijder oude accounts.
- [ ] **Wachtwoorden en tweestapsverificatie** voor alle beheerders.
- [ ] **Beveiligingsscan:** draai een scan, bijvoorbeeld met de gratis [WordPress check](https://www.joepify.nl/wordpress-check?utm_source=github&utm_medium=readme&utm_campaign=wordpress-onderhoud-checklist) van buitenaf, en kijk naar bekende lekken in plugins.
- [ ] **Inlogpogingen:** zijn er veel mislukte pogingen? Beperk ze met een plugin of op serverniveau.
- [ ] **Bestandswijzigingen:** `wp core verify-checksums` en `wp plugin verify-checksums --all` (WP-CLI) laten afwijkende bestanden zien.

### Snelheid en vindbaarheid

- [ ] **Snelheid:** meet de belangrijkste pagina's op mobiel met PageSpeed Insights. Noteer de score in het log.
- [ ] **Afbeeldingen:** zijn nieuwe afbeeldingen verkleind (breedte niet groter dan nodig, WebP waar mogelijk)?
- [ ] **Search Console:** kijk bij Pagina's naar nieuwe fouten (404, serverfout, niet geïndexeerd).
- [ ] **Kapotte links:** controleer interne links op 404's.

### Back-ups

- [ ] **Terugzettest:** zet één keer per kwartaal een back-up terug op een testomgeving. Een back-up die je nooit hebt getest, is een hoop.
- [ ] **Bewaartermijn:** bewaar minimaal 14 dagen aan dagelijkse back-ups en een maandelijkse kopie.

## Per kwartaal

- [ ] SSL-certificaat: wanneer verloopt het, en verlengt het automatisch?
- [ ] E-mail van je domein: controleer SPF, DKIM en DMARC met [mail-auth-check](https://github.com/Joepify/mail-auth-check).
- [ ] Security headers (HSTS en andere) en de cookiebanner.
- [ ] Toegang: wie heeft nog een login voor hosting, domein en WordPress?
- [ ] Formulieren en webshop: doe een volledige testbestelling of testaanvraag.

## Per jaar

- [ ] Domein en hosting: vervaldatum, wie is eigenaar, wie ontvangt de facturen?
- [ ] Zijn de teksten nog juist (prijzen, contactgegevens, openingstijden, KvK-nummer)?
- [ ] Past het huidige hostingpakket nog bij het bezoek? Meet laadtijd en serverrespons.
- [ ] Overweeg of het thema of een plugin vervangen moet worden door iets onderhoudbaars.
- [ ] Privacyverklaring, cookiebeleid en wettelijke pagina's nalopen.

## Handige WP-CLI-commando's

```bash
wp core version
wp core check-update
wp plugin list --update=available
wp theme list --update=available
wp plugin update --all        # maak eerst een back-up
wp core verify-checksums
wp user list --role=administrator
wp cron event list
wp db size --tables
```

## Wanneer is het te veel werk?

Als je merkt dat updates blijven liggen, dat je de back-up nooit test of dat je niet weet wie het beheer heeft, is het tijd om dit over te dragen aan iemand met een vaste werkwijze. Lees wat een WordPress-specialist doet op [WordPress specialist Rotterdam](https://www.joepify.nl/wordpress-specialist-rotterdam?utm_source=github&utm_medium=readme&utm_campaign=wordpress-onderhoud-checklist).

## Laat het mij doen

Ik voer dit onderhoud uit, zodat jij er niet aan hoeft te denken. Vaste prijs: €35, €69 of €129 per maand (excl. btw). [Meer over mijn werk met WordPress](https://www.joepify.nl/wordpress-specialist-rotterdam?utm_source=github&utm_medium=readme&utm_campaign=wordpress-onderhoud-checklist) of [stuur een WhatsApp-bericht](https://wa.me/31687195043?text=Hoi%20Ayoub%2C%20ik%20kom%20via%20GitHub%20%28wordpress-onderhoud-checklist%29%20en%20wil%20hulp%20met%20wordpress%20onderhoud.).

## Over Joepify

[Joepify](https://www.joepify.nl?utm_source=github&utm_medium=readme&utm_campaign=wordpress-onderhoud-checklist) is een webbureau aan de Metaalhof 27 in Rotterdam. Ayoub Assaidi bouwt en onderhoudt WordPress-sites zelf. Met de gratis [WordPress check](https://www.joepify.nl/wordpress-check?utm_source=github&utm_medium=readme&utm_campaign=wordpress-onderhoud-checklist) zie je in een minuut hoe je site ervoor staat.

## English

A recurring maintenance checklist for WordPress sites (weekly, monthly, quarterly, yearly) covering updates, backups, PHP version, uptime, security and speed. Includes a printable A4 HTML page and a CSV log template. PHP security support dates: 8.2 until 31 Dec 2026, 8.3 until 31 Dec 2027, 8.4 until 31 Dec 2028 (php.net).

## Licentie

CC BY 4.0, zie [LICENSE](LICENSE).
