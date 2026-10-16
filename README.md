# Prepoznavanje hrvatskoga teksta

Repozitorij sadrži modul hrvatskoga jezika za prepoznavanje (identifikaciju) teksta `libexttextcat`om.

## Metodologija rada

- preuzimanje cijele hrvatske Wikipedije
- čišćenje wiki oznaka (predlošci, oznake naslova...)
- čišćenje preostalih XML tagova pomoću alata `sed` i pravilnih izraza
- nasumično uzimanje 300 000 odlomaka
- pokretanje `createfp` na takvom korpusu

U Wikipediji ima i puno stranih imena, toponima i općenito stranih riječi, pa je pitanje koliko je 300 000 odlomaka reprezentativno. Postoje dvije stvari vezano za ovo:

- ako imamo isključivo tekst sastavljen od hrvatskih riječi, možda tekst kopiran iz hrvatske Wikipedije koji ima dovoljno stranih riječi neće biti prepoznat kao hrvatski
- miješani tekst (hrvatska Wikipedija) ipak strana imena, toponime i riječi veže unutar hrvatskoga teksta, tako da je pretpostavka da je hrvatski tekst na vrhu (veća statistička vjerojatnost), a strane riječi su više došle kao šum, ali postoje u modelu pa zbog njih `libexttextcat` neće odbaciti tekst

## Zašto ne cijela hrvatska Wikipedija

Ograničenje sklopovlja koje posjedujemo onemogućava da s `createfp` provedemo cijelu Wikipediju na hrvatskome jer bi proces stvaranja jezičnoga modela na > 235 000 članaka i preko 53 milijuna riječi trajao predugo. Uostalom nema ni potrebe, dovoljno je nekoliko megabajta teksta da `createfp` izvuče što mu treba.

---

Krunoslav Šebetić (listopad 2026.)
kruno.se@gmx.com
LGPLv3+
