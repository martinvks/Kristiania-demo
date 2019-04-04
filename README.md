# Demo applikasjon for Høyskolen Kristiania

Dette er en demo applikasjon for å vise hvordan man kan bruke dependency injection
for å bygge Android applikasjoner. Dette kan gjøre koden enklere å teste, refaktorere kode
og bytte enkelte lag av applikasjonen.

## Litt bakgrunn om dependency injection

Dependency injection er en programmeringsteknikk der man overlater oppgaven med å opprette
objekter man avhenger av til noen andre. I stedet får man objektet man bruker for eksempel som
argument i konstruktøren.

Eksempel uten dependency injection
```
public class MailService {
    private Mailklient mailklient;

    public MailService() {
        mailklient = new Mailklient("https://api.selskap.no/mail");
    }

    public sendMail(
        String mottaker,
        String tekst
    ) {
        mailklient.sendEpost(mottaker, tekst);
    }
}
```
Eksempel med dependency injection
```
public class MailService {
    private final Mailklient mailklient;

    public MailService(Mailklient mailklient) {
        this.mailklient = mailklient;
    }

    public sendMail(
        String mottaker,
        String tekst
    ) {
        mailklient.sendEpost(mottaker, tekst);
    }
}
```

## Demo applikasjon

Enkel Android applikasjon der brukeren kan taste inn et github brukernavn og få listet ut
repositoriene til brukeren.

### Dependency graf
![Dependency graph](dependency_graph.png?raw=true "Dependency graph")
