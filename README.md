---
use_math: true
---

Test a display math:
$$
   |\psi_1\rangle = a|0\rangle + b|1\rangle
$$
Is it O.K.?


# OK bois, so hoerrefok werk hierdie crypto shit?

## A.k.a. wat de p**s is Bitcoin

brannewyn hex color: #DE8F01

Skink solank vir jou 'n dubbel en kom sit op oom se skoot laat ons kan praat oor die eerste prys wat opkom.

Bismunte, of bitcoins, gebruik public key encryption bo-op 'n publieke grootboek (ledger) sodat jy gisteraand se rekening kan settle &mdash; maar ontspan pel, ons gaan nou ball chat oor al daai fênsie kak.

Public key encryption maak staat op 'n sogenaamde valdeur funksie ([trapdoor function](https://en.wikipedia.org/wiki/Trapdoor_function)), of die feit dat priemfaktorisering fokken lank neem.

### Begrip 1/3: Eenrigtingfunksies 

$$|\psi\rangle$$

 - 'n Valdeurfunksie is maklik om in een rigting te bereken, maar moeilik in die teenoorgestelde rigting. Net soos om die brannewyn terug te skink wat Hannes vroeër omgepoes het.

Ons kan 'n eenrigting funksie ontwerp (sg. "hash function") wat groter priemgetalle as my piel met mekaar maal en verhef tot 'n eksponent om 'n nuwe syfer te kry waarmee jy nie die oorspronklike priemgetalle kan reverse calculate nie...ten minste nie voor al die KWV 5-jaar in die heelal opgedrink is nie.

Byvoorbeeld, laat `n = p × q` en kies twee priemgetalle `p=3` en `q=5`, dus `n = 3 × 5 = 15`. Jy kan mós vinnig verifieer dat `3 × 5` inderdaad `15` is (goddank vir SG wiskunde). Maar as ek net vir jou `15` gee, wat was die faktore? Wel, dis triviaal om die faktore van 'n klein syfer te bepaal, maar wat van `3233`?

Ja-nee, ook maar goed jy het gehou by die HG. Die priemfaktore `p` en `q` is `61 × 53`. Jy kan dit *crack* maar ons praat van honderdsyfer priemgetalle wat nie op 'n Ford Cortina se bonnet pas nie. En om daai bad boys te crack neem langer as die hitte-sterfte van die heelal - *no word of a lie*.

As ons daai syfer 'n paar keer met homself maal, *dan* praat ons besigheid. So hier is die laaste bietjie Excel:

 1. `p = 61
 - Bereken die "totient" van 

3233


Geluk, jy verstaan die fondament van RSA encryption - skink nog 'n dubbel.

## Genoeg Excel, hoe coin ek dit?

Wel, met hierdie boss tech kan jy die identitiet van 'n party bevestig deur vir hulle 'n geheime boodskap te encrypt met hul public key (wat almal ken) en te vra dat hulle dit decrypt. Net die ware party sal dit kan ontsyfer. Terloops, dit is hoe RedTube oor HTTPS en SSL werk om daai groen slot te wys.

Nou wanneer kom Bitcoin in die game? Dis baie slim: 'n bitcoin wallet is 'n public key en jou wallet password is die private key, maar wallet addresse is meer soos disposable one-use Choice condoms. As jou suster bitcoins na my wallet toe wil stuur vir gisteraand, dan post sy 'n boodsakp na die blockchain ledger wat se, "Betaal 0.3 bitcoins in Petrus se wallet." Sy onderteken dan die transaksie met haar private key en kry 'n nuwe wallet. Die myners se job is om dit te verify en die nuwe wallet amounts te calculate, deur te check dat die private key en public key match.

Later, wanneer ek helfde van daardie 0.3 bitcoins na die Cayman isles wil onttrek, kan ek 'n "spend" transaksie met my geheime private key onderteken en die myners sal verifieer dat die public key aan wie sy die 0.3 coins toegestaan het, wel aan my behoort. Ek kry dan ook 'n nuwe wallet met die nuwe balans in. Op 'n manier word jou reeks van wallets met mekaar gelink met een of ander ketting storie.

Dit is hoe Bitcoin werk. Let wel: Bitcoin gebruik ECDSA in plaas van RSA encryption, maar dit kom ook neer op 'n one-way hashing function.

So 

# Aight, hier is die cheat codes:

 - Om 'n geheime boodskap `m` te kodeer: `c = m^e mod n`, waar `e = 3`
 - Om kriptoteks `c` te dekodeer: `m' = c*d mod n`, waar `piel = (p-1)*(q-1)` en `ed ≡ 1 (mod piel)`
- Laat `n = pq`
- Laat `piel = (p-1)(q-1)`
 - `e < n` sodat `gcd(e, piel) = 1`
 - Laat `d = e^-1 mod piel`
 - `c = m^e mod n`, `1<m<n`
 - `m = c^d mod n`

Basically, jy kies twee poesgroot priemgetalle `p` vir poes en q vir qont en maal hulle met mekaar om die resultaat n te kry, so n=p*q. Jy verhef dan n tot 'n baie groot eksponent e vir ebola (wat ook 'n priemgetal is, dus n^e) om 'n Ben11-size syfer te kry wat julle kan gebruik om 'n message m te encrypt na ciphertext c soos jou ex se kaal foto's. Die formule is: c = m^e mod n.

Al wat jy dan benodig het om jou dick pics te encrypt is jou persoonlike naai en ebola, so ons noem (n, e) jou public key, a.k.a. jou bitcoin wallet address.

Byvoorbeeld:

 - as m=7, e=3 en n=33, dan is
 - c = 7^3 mod 33 = 343 mod 33 = 13 inch = my piel

So nou kan jy 13 op radio Jakaranda of jou Facebook wall post maar niemand weet dit beteken eintlik 7 nie, teensy hulle iets van jou en q weet.

Maar hoe de fok decrypt jy c? Wel, niemand kan dit ontsyfer teensy hulle p en q weet nie - ten minste nie voor Buckleys hulle pool tafels regmaak nie. Jy kort nog twee afleidings piel en d vir koos:

 - Bereken piel = (p-1)*(q-1) = (11-1)*(3-1) = 20
 - Bereken d sodat ed ≡ 1 (mod piel), dus d = e^-1 mod piel = 3^-1 mod 20
 - Vind 'n waarde vir d sodat piel eweredig deel deur (ed-1), bv. toets (d = 1, 2, ...) wat lewer d = 7. 
 
Okay, fokkit daai Excel is dieper as 'n Gringo's dubbel. So, hoe decrypt jy c terug na 'n cleartext message, m' toe? Fok weet, as jy net HG wiskunde deurgekom het, kan jy uitwerk die antwoord is m' = cd mod n. Soos jy dan kan sien, skort 'n man net 'n bietjie ekstra d. Daarom noem ons (n, d) jou private key - moet dit nie op die Hokkiegroep share nie.
 *
 

Addendum A: vir RSA veiligheid, maak seker e, (p-1) en (q-1) het geen gemene faktore, dus gcd(e, p-1) = gcd(e, p-1) = slegs 1 waar gcd beteken "Greatest Common Denominator".

You can use the [editor on GitHub](https://github.com/theronic/bismunt/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/theronic/bismunt/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
