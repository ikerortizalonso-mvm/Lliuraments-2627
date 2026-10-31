# Pràctica 1: Característiques dels llenguatges de marques

## Descripció

> [!NOTE]
> **Objectiu:** Aprofundir i posar en pràctica els coneixements adquirits sobre l'ús i les característiques principals dels *llenguatges de marques*.

> [!IMPORTANT]
> **Desenvolupament:** En parelles.

> [!TIP]
> **Lliurament:** A través del `Moodle` en format presentació (`odt`, `ppt`, `pptx` o `pdf`).

## Enunciat

L’objectiu d’aquest exercici és aprofundir en els conceptes relacionats amb les característiques inherents als *llenguatges de marques* mitjançant la creació d’un **llenguatge propi**, heu de tenir en compte que, per a poder classificar la vostra creació com a llenguatge de marques, s’han de complir una sèrie de requisits:

> - El llenguatge s’ha de basar en **text pla**.
>
> - Ha de fer ús de **metadades** (no confondre amb metallenguatge).
>
> - N’ha de facilitar el procés automàtic de les dades per part d’un programa informàtic.
>
> - N’ha de facilitar la representació (o la interpretació) de les dades emmagatzemades.

## Un cop hàgiu acabat, prepareu una presentació per a explicar el següent:

1. Una introducció als llenguatges de marques: orígens, per a què es fan servir, etc.

   - Origen: les anotacions als manuscrits abans d'enviar-los a impremta (tipus de lletra, mida…).
   - Fan servir marques (etiquetes) dins d'un text pla.
   - Separen les dades de l'estructura i dels estils.
   - Sorgeixen de la necessitat d'explotar la informació i presentar-la de forma automatitzada; calen estàndards.

   | Any | Llenguatge | Qui / què |
   |---|---|---|
   | 1960 | GML | Charles Goldfarb (IBM). Llenguatge d'ús general |
   | 1970–1980 | TeX | Donald Knuth. Revistes de matemàtiques; complex |
   | 1980 | Scribe | Brian Reid. Separa contingut i estil |
   | 1986 | SGML | Estàndard ISO |
   | 1991 | HTML | Tim Berners-Lee (CERN). Primeres pàgines web |
   | 1998 | XML | W3C. Simplifica SGML; regles estrictes i extensible |

   **Tipus**

   - Presentació i procediment: separen les dades de la seva maquetació; pensats per a l'usuari (Scribe, TeX, HTML).
   - Descriptius o semàntics: separen les dades de la seva definició; pensats per a una màquina; no indiquen com ni en quin ordre es presenten (XML, YAML, JSON).

   **Àrees d'ús:** ERPs, BBDD, sistemes operatius, sistemes de comunicacions, aplicacions ofimàtiques.

---

2. Una introducció al vostre llenguatge de marques, explicació de les regles que heu definit.

   **DPC · Dades amb Punt i Coma.** Parteix de l'exemple de la classe (dades separades per punt i coma). És un fitxer de text pla amb les dades dels Pokémon: nom, element, vida i dany.

   1. Text pla, codificació UTF-8.
   2. La 1a fila són les capçaleres (noms dels camps).
   3. La resta de files són dades (un registre per fila).
   4. Separador de camps: `;`
   5. Separador de registre: `\r\n`
   6. Tipus de dada, al final del camp: `\t` = string, `\f` = float.

---

3. Classificar el vostre llenguatge de programació (procedimental i presentació; descriptiu o semàntic) i justificar aquesta classificació.

   **Descriptiu o semàntic.**

   - No indica com s'han de mostrar les dades ni en quin ordre.
   - Separa les dades de la seva definició: capçaleres i marques de tipus.
   - Pensat perquè un programa el processi de forma automàtica.
   - No és de presentació i procediment: no hi ha cap marca de format.

---

4. Explicar un cas d’ús en el qual es podria fer servir el vostre llenguatge de marques.

   Intercanviar llistes de Pokémon (nom, element, vida i dany) entre dos programes, per exemple un joc de combats que llegeix les dades dels Pokémon. Emissor i receptor només han de conèixer les regles, i el fitxer el llegeix un programa però també el pot entendre una persona.

---

5. Mostrar un exemple de com es fa servir el vostre llenguatge i explicar-lo.

   ```text
   nom;element;vida;dany
   Pikachu\t;Elèctric\t;35\f;55\f
   Charmander\t;Foc\t;39\f;52\f
   Squirtle\t;Aigua\t;44\f;48\f
   ```

   | nom (string) | element (string) | vida (float) | dany (float) |
   |---|---|---|---|
   | Pikachu | Elèctric | 35 | 55 |
   | Charmander | Foc | 39 | 52 |
   | Squirtle | Aigua | 44 | 48 |

   **Explicació**

   1. La 1a fila són les capçaleres: nom, element, vida i dany (les metadades).
   2. Cada fila següent és un registre, separat pel `\r\n`.
   3. El `;` separa els camps de cada registre.
   4. `\t` indica text (string) i `\f` un decimal (float): «Pikachu» és text i 35 és un nombre.

---

6. Explicar un cas d’ús en el qual el vostre llenguatge de marques no seria el més adient.

   - **Un document amb format:** DPC no té cap marca de presentació; no es poden indicar títols, negretes ni imatges. Millor: HTML o TeX.
   - **Dades amb estructura niada:** només té files i columnes; no pot representar, per exemple, un Pokémon amb diversos atacs, cadascun amb el seu element i dany. Millor: XML.

---

7. Justificar per què el vostre llenguatge es pot classificar com "de marques".

   - **Basat en text pla:** fitxer de text, codificat en UTF-8.
   - **Fa servir metadades:** capçaleres i marques de tipus (`\t`, `\f`) descriuen les dades.
   - **Facilita el procés automàtic:** un programa separa per `;` i `\r\n` i sap el tipus de cada camp.
   - **Facilita la interpretació:** les regles pactades expliquen com llegir i representar les dades.

---

## Rúbrica d’avaluació

> [!CAUTION]
> **Atenció:** l’incompliment de les instruccions de lliurament impliquen la NO correcció de la pràctica i una nota de 0 punts. Cal seguir totes les instruccions estrictament al peu de la lletra.

|  | 0 punts | 0,5 punts | 1 punt |
|---|---|---|---|
| **Introducció als llenguatges de marques.** | No s’ha realitzat o conté errors molt greus. | Explicació superficial o amb errors lleus. | Explicació clara, detallada i correcta. |
| **Explicació del llenguatge i regles d’ús** | No s’ha realitzat o conté errors molt greus. | Explicació superficial o amb errors lleus. | Explicació clara, detallada i correcta. |
| **Cas d’ús (si s’adapta)** | No s’ha realitzat o conté errors molt greus. | Explicació superficial o amb errors lleus. | Explicació clara, detallada i correcta. |
| **Cas d’ús (no s’adapta)** | No s’ha realitzat o conté errors molt greus. | Explicació superficial o amb errors lleus. | Explicació clara, detallada i correcta. |
| **Exemple** | No s’ha realitzat o conté errors molt greus. | Explicació superficial o amb errors lleus. | Explicació clara, detallada i correcta. |
| **Classificació** | No s’ha realitzat o conté errors molt greus. | Explicació superficial o amb errors lleus. | Explicació clara, detallada i correcta. |
| **Justificació llenguatge de marques.** | No s’ha realitzat o conté errors molt greus. | Explicació superficial o amb errors lleus. | Explicació clara, detallada i correcta. |
| **Estil de les transparències** | No s’ha realitzat o conté erros greus. | Pobre, poc treballat o es nota que s’ha fet a correcuita. | Correcte, agradable a la vista i homogeni. |
| **Temps** | Menys de 3 minuts o més de 7 minuts. | Menys de 4 minuts o més de 6 minuts. | Exactament o aproximadament 5 minuts (2:30 per alumne). |
| **Presència sobre l’escenari** | No ha presentat | Li costa expressar-se en públic i mostra dificultats per fer-se entendre. | S’expressa amb naturalitat i claredat. Se’l veu còmode quan parla en públic. |
