# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu.
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu.

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.

<a id="ac3"></a>
### AC3: System płatności

Wybrany system płatności. 




## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):

* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC2](#uc2): Wysłanie produktu z aukcji
  [UC3](#uc3): Przekazanie produktu [Kupującemu]

[Kupujący](#ac2)

* [UC4](#uc4):Zalicytowanie produktu
  [UC5](#uc5):Wygranie aukcji
  [UC6](#uc6):Przegranie aukcji
  [UC7](#uc7):Przekazanie należności sprzedającemu

[System płatności](#ac3)

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc4"></a>
### UC4: Zalicytowanie produktu

**Aktorzy:** [Kupujacy](#ac2)

**Scenariusz główny:**

1. [Kupujący](#ac2) loguje się do systemu, w którym będzie mógł licytować produkt poprzez podanie swojego imienia i nazwiska. 
2. [Kupujący](#ac2) wybiera przycisk zalicytowania produktu.
3. System prosi o podanie kwoty.
4. [Kupujący](#ac2) podaje kwotę za którą licytuje. 
5. System zatwierdza poprawność danych [br1].
6. System informuje o pomyślnym zalicytowaniu produktu.

**Scenariusze alternatywne:** 

5.A. Podano za niską kwotę do licytowania.
* 5.A.1. System informuje o błędnie podanych danych.
* 5.A.2. Przejdź do kroku 3.

---

<a id="uc5"></a>
### UC5: Wygranie aukcji

**Aktorzy:** 

**Scenariusz główny:**
1. System blokuje możliwość dalszego licytowania produktu.
2. System weryfikuje, który [Kupujący] podał najwyższą kwotę licytacji [br2]. 
3. System przesyła powiadomienie na maila wygrywającego [Kupujacy] o wygraniu licytacji wraz z informacją o ID wygranej licytacji. 


**Scenariusze alternatywne:** 

2.A. Brak zalicytowania produktu przez żadnego [Kupujący].  
* 2.A.1. System informuje [Sprzedający] o braku licytującego wygrywającego aukcje.

---

<a id="uc7"></a>
### UC7: Przekazanie należności sprzedającemu

**Aktorzy:** [Kupujacy](#ac2), [Sprzedający](#ac1), [System płatności](#ac3)

**Scenariusz główny:**

1. [Kupujący](#ac2) loguje się do systemu, w którym będzie mógł opłacić wylicytowany produkt. 
2. [Kupujący](#ac2) wybiera przycisk opłacenia produktu, którego licytację wygrał. 
2. System prosi o podanie ID wygranej aukcji oraz imię i nazwisko kupującego.
3. System weryfikuje poprawność danych.
4. System przekierowuje [Kupujący] do [System płatności].
5. [Kupujący] loguje się w [System płatności]
5. [System płatności] weryfikuje poprawność danych.
6. [Kupujący] zatwierdza płatność produktu.
7. [System płatności] weryfikuje dane i zatwierdza płatność.
8. [System płatności] wysyła pomyśle opłacenie zamówienia.  

**Scenariusze alternatywne:** 

6.A. Podano błędne dane logowania do [System płatności]
* 6.A.1. System informuje o błędnie podanych danych.
* 6.A.2. Przejdź do kroku 5.

7.A. [System płatności] werfikuje, iż brakuje środków na koncie [Kupujący].
* 7.A.1. System informuje o braku środków na koncie.
* 7.A.2. Przejdź do kroku 5.

---



<a id="uc2"></a>
### UC2: Wysłanie produktu z aukcji

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Scenariusz główny:**
1. ...

**Scenariusze alternatywne:** 

1.A. ...
* 4.A.1. ...

---

## Obiewkty biznesowe (inaczej obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | ... |
| ------------------------------------------------- | ------ | ------- | --- |
| UC1: Wystawienia produktu na aukcję               |    C   |    C    | ... |
| ???                                               |  ...   |  ...    | ... |


