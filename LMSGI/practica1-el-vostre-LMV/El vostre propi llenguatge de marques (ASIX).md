
# El nostre propi llenguatge de marques

## DPC · Dades Pokémon Compactes

Llenguatges de marques i sistemes de gestió empresarial (M04) · Pràctica 1 · ASIX

`t:Pikachu|t:Elèctric|n:35|n:55`

**Iker Ortiz, David Ballesteros i Mohamed Chafiq**

---

# Què és un llenguatge de marques

*Introducció als llenguatges de marques*

- **Origen:** les anotacions als manuscrits abans d'enviar-los a impremta (tipus de lletra, mida…)
- Fa servir **marques** (etiquetes) dins d'un **text pla**
- Separa les dades de l'estructura i dels estils
- Sorgeix de la necessitat d'explotar la informació i presentar-la de forma automatitzada
- Cal una forma de posar-se d'acord en com fer-ho: els **estàndards**

### Un petit repàs

- Basats en text pla
- Simplifiquen la gestió i l'automatització de la informació
- Fan servir marques per separar les dades de l'estructura

---

# Els orígens

*Línia del temps dels llenguatges de marques*

| Any | Llenguatge | Qui / què |
|---|---|---|
| 1960 | **GML** | Charles Goldfarb (IBM). Llenguatge d'ús general; precursor de SGML |
| 1970–80 | **TeX** | Donald Knuth. Maquetació de revistes de caire matemàtic |
| 1980 | **Scribe** | Brian Reid. Separa el contingut de l'estil |
| 1986 | **SGML** | Esdevé estàndard ISO |
| 1991 | **HTML** | Tim Berners-Lee (CERN). Primeres pàgines web |
| 1998 | **XML** | W3C. Simplifica SGML; regles estrictes; extensible |

---

# Tipus i àrees d'ús

*Dos tipus de llenguatges de marques i on s'utilitzen*

### Presentació i procediment

- Separen les dades de com s'ha de mostrar la informació
- Les marques indiquen com es mostra el contingut (negreta, títol, mida)
- Pensats perquè l'usuari en sigui el destinatari
- **Exemples:** Scribe, TeX, HTML

### Descriptius o semàntics

- Separen les dades de la seva definició
- Les marques indiquen què és cada dada (nom, vida…)
- Pensats perquè una màquina en sigui la destinatària; no indiquen com ni en quin ordre es presenten
- **Exemples:** XML, YAML, JSON

**Àrees d'ús:** ERPs · BBDD · Sistemes operatius · Sistemes de comunicacions · Aplicacions ofimàtiques

---

# Presentem el nostre llenguatge: DPC

*Dades Pokémon Compactes*

- Llenguatge propi per guardar les dades dels Pokémon: nom, element, vida i dany
- És un fitxer de text pla, amb les dades en files i camps
- Emissor i receptor necessiten un «diccionari» per entendre's: són les regles que hem definit
- Les regles diuen què és cada part del fitxer

### Cada Pokémon té 4 camps

| Camp | Tipus |
|---|---|
| `nom` | text |
| `element` | text |
| `vida` | número |
| `dany` | número |

---

# Les regles de DPC

*El «diccionari» que han de conèixer emissor i receptor*

1. **Text pla:** codificació UTF-8.
2. **Comentaris:** les línies que comencen per `//` s'ignoren.
3. **Capçaleres:** la 1a fila que no és comentari conté els noms dels camps.
4. **Dades:** la resta de files; un registre per fila.
5. **Separador de camps:** `|`
6. **Separador de registre:** salt de línia (`\n`).
7. **Tipus de dada**, al davant del camp: `t:` = text, `n:` = número.

---

# Classificació

*Quin tipus de llenguatge de marques és DPC?*

## DPC és un llenguatge descriptiu o semàntic

**Per què?**

- ✓ No indica com s'han de mostrar les dades ni en quin ordre
- ✓ Separa les dades de la seva definició: capçaleres i marques de tipus
- ✓ Pensat perquè un programa el processi de forma automàtica

✗ **No és de presentació i procediment:** no hi ha cap marca de format.

---

# Cas d'ús: on sí encaixa

*Intercanviar llistes de Pokémon entre dos programes*

**Programa emissor** (genera les dades) → **Fitxer DPC** (`pokemons.dpc`) → **Programa receptor** (p. ex. un joc de combats)

- Intercanviar llistes de Pokémon (nom, element, vida i dany) entre dos programes
- Per exemple, un joc de combats que llegeix les dades dels Pokémon
- Emissor i receptor només han de conèixer les regles
- El llegeix un programa i també el pot entendre una persona

---

# Exemple

*Fitxer `pokemons.dpc` i com s'interpreta*

### Fitxer DPC

```text
// Pokédex en DPC
nom|element|vida|dany
t:Pikachu|t:Elèctric|n:35|n:55
t:Charmander|t:Foc|n:39|n:52
t:Squirtle|t:Aigua|n:44|n:48
```

### Dades interpretades

| nom (text) | element (text) | vida (número) | dany (número) |
|---|---|---|---|
| Pikachu | Elèctric | 35 | 55 |
| Charmander | Foc | 39 | 52 |
| Squirtle | Aigua | 44 | 48 |

---

# Explicació de l'exemple

*Com llegeix un programa el fitxer, pas a pas*

1. La línia que comença per `//` és un comentari i s'ignora.
2. La 1a fila que no és comentari són les capçaleres: nom, element, vida i dany (les metadades).
3. Cada fila següent és un registre, separat pel salt de línia.
4. El `|` separa els camps de cada registre.
5. `t:` indica text i `n:` un número: `t:Pikachu` és text i `n:35` és un número.

---

# Cas d'ús: on no és el més adient

*Situacions en què DPC es queda curt*

### ✗ Un document amb format

DPC no té cap marca de presentació: no es poden indicar títols, negretes ni imatges.

**Millor:** HTML o TeX

### ✗ Dades amb estructura niada

Només té files i columnes: no pot representar, per exemple, un Pokémon amb diversos atacs, cadascun amb el seu element i dany.

**Millor:** XML

---

# Per què és un llenguatge de marques

*DPC compleix els quatre requisits de l'enunciat*

| Requisit | Com el compleix DPC |
|---|---|
| ✓ **Basat en text pla** | Fitxer de text, codificat en UTF-8 |
| ✓ **Fa servir metadades** | Capçaleres i marques de tipus (`t:`, `n:`) descriuen les dades |
| ✓ **Facilita el procés automàtic** | Un programa separa per `\|` i pel salt de línia i sap el tipus de cada camp |
| ✓ **Facilita la interpretació** | Les regles pactades expliquen com llegir i representar les dades |

---

# Gràcies per la vostra atenció!

## DPC · Dades Pokémon Compactes

**Iker Ortiz, David Ballesteros i Mohamed Chafiq**

# Link de la presentació!
## https://canva.link/12u9a1x9g0vn6dz

