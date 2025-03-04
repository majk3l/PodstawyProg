# Podstawy programowania 
### Wykład #1: Wprowadzenie.
*dr inż. Michał Kępski* 

<!-- footer: | e-mail: mkepski@ur.edu.pl | 
-->

---

## Czego dotyczy wykład?

### Algorytmy i struktury danych:
Algorytmy i sposoby ich przedstawiania, konwencja notacyjna, struktury algorytmów, własności algorytmów (poprawność, złożoność i efektywność), algorytmy rekurencyjne.

### Komputery:
Schemat funkcjonalny, organizacja pamięci. Pozycyjne systemy liczbowe, konwersje zapisów liczb, stało- i zmiennopozycyjny sposób zapisu liczb.

### Język C++:
Składnia języka. Stałe i zmienne. Instrukcje. Typy danych, literały, operatory i wyrażenia. Operacje wejścia i wyjścia. Funkcje. Typy złożone. Wskaźniki.

---

## Plan wykładu:

- Algorytmy - wprowadzenie;
- System komputerowy z punktu widzenia programisty;
- Podstawowe pojęcia;
- Pierwszy program w C++;
- Struktura programu;
- Kompilacja i uruchomienie;

---

## Literatura

### Algorytmy i struktury danych:

 - Wprowadzenie do algorytmów / Thomas H. Cormen [et al.] ; z ang. przeł. Krzysztof Diks [et al.]. - Wyd. 7 (1 w PWN).  - Warszawa : Wydawnictwo Naukowe PWN, 2012. 

### Komputery:

- Computer Systems: A Programmer's Perspective / Randal E. Bryant, David R. O'Hallaron. - Wyd. 2. - USA : Addison-Wesley Publishing Company, 2010.


### Język C++:

- Język C++ : szkoła programowania / Stephen Prata ; z ang. przeł. Przemysław Szeremiota [et al.]. - Gliwice : Helion, copyright 2022. 

---

## Algorytmy - wprowadzenie

---

## Algorytm

**Algorytm** to pewna ściśle określona procedura obliczeniowa, która dla właściwych danych wejściowych produkuje zadane dane wyjściowe, zwane wynikiem działania algorytmu.

Algorytm jest więc ciągiem kroków obliczeniowych, prowadzących do przekształcenia danych wejściowych w dane wyjściowe.

---

## Algorytm

**Algorytm** możemy również traktować jako sposób rozwiązania konkretnego problemu obliczeniowego.

Postawienie problemu to sprecyzowanie wymagań dotyczących relacji między danymi wejściowymi, a algorytm opisuje właściwą **procedurę obliczeniową**, która zapewnia, że ta relacja zostanie osiągnięta.

---

## Przykłady problemów i algorytmów je rozwiązujące

- wyznaczania największego wspólnego dzielnika - algorytm Euklidesa;
- porządkowanie danych - algorytmy sortowania (np. quicksort);
- wyznaczanie najkrótszej ścieżki (np. routing sieciowy) - algorytm Dijkstry;
- kompresja danych - algorytm Huffmana;
- zapewnienie bezpiecznej komunikacji - szyfrowanie asymetryczne (np. RSA).
 

---

## Algorytm


Algorytm można zrealizować w postaci programu komputerowego albo zrealizować sprzętowo. Jedynym wymaganiem jest precyzja opisu wynikającej z niego procedury obliczeniowej.

Algorytm można zapisać też jako schemat blokowy lub przedstawić w pseudojęzyku pro-gramowania (zwanym też pseudokodem).


---

## NWD 

### Opis w języku polskim:

Oblicz największy wspólny dzielnik dwóch nieujemnych liczb całkowitych *p* i *q* w następujący sposób: jeśli *q* równa się 0, wynikiem jest *p*. W przeciwnym razie należy podzielić *p* przez *q* i wykorzystać resztę *r*. Wynik to największy wspólny dzielnik *q* i *r*.


### Pseudokod:

```
NWD(p, q):
  Jeśli q = 0 wtedy
     Zwróć p
  W przeciwnym razie
    r ← p mod q
    Zwróć NWD(q, r)
```

---

## NWD


### C++

```cpp
int gcd(int p, int q) {
    if (q == 0) return p;
    int r = p % q;
    return gcd(q, r);
}
```

---

# NWD - wariant z pętlą


Na początku sprawdzamy, czy *q* jest zerem – jeśli tak, wynikiem jest *p*. Jeśli nie, wchodzimy do pętli, gdzie w każdej iteracji obliczana jest reszta z dzielenia *p* przez *q*. Następnie war-tość *q* staje się nową wartością *p*, a obliczona reszta staje się nową wartością *q*. Proces ten powtarzamy, aż *q* osiągnie wartość 0. Wówczas *p* zawiera największy wspólny dzielnik obu liczb.


---

# NWD - wariant z pętlą

```
NWD(p, q):
  Dopóki q ≠ 0 wykonuj:
    r ← p mod q
    p ← q
    q ← r
  Zwróć p
``` 

---

# NWD - wariant z pętlą


```cpp
int gcd(int p, int q) {
    while(q != 0) {
        int r = p % q;
        p = q;
        q = r;
    }
    return p;
}
```



---

## Poprawność i efektywność


- **Egzemplarz problemu** składa się z określonych danych wejściowych spełniających wszystkie warunki podane w opisie problemu.

- Algorytm jest **poprawny**, gdy dla każdego egzemplarza problemu algorytm zatrzy-muje się i daje dobry wynik. 

- Algorytm **niepoprawny** może się nigdy nie zatrzymać albo po zatrzymaniu dać zły wynik. 

---

## Poprawność i efektywność

- Algorytmy przeznaczone do rozwiązywania tego samego problemu często różnią się **efektywnością**.

- Zwykle największy wpływ na efektywność ma zależność od rozmiaru danych wejścio-wych $n$.

- Czas działania będzie też zależny od pewnej stałej niezależnej od wejścia $c$.

---

## Poprawność i efektywność

-   Mamy dwa algorytmy rozwiązujące dany problem obliczeniowy, jeden rozwiązuje go 
w czasie $c_1n^2$, a drugi $c_2nlog{_2n}$.

- Załóżmy że $c_1 < c_2$, a różnica ta jest spora, $c_1 \approx 2$ natomiast $c_2 \approx 50$.

- Dla niewielkich rozmiarów wejścia algorytm 1. będzie szybszy lecz dla dużych danych wejściowych szybszy będzie 2. (przykładowo dla $n = 1000$ wartość $log{_2n}\approx 10$).


---

## Złożoność obliczeniowa


- Dla dostatecznie dużych danych liczymy jedynie rząd wielkości czasu działania - zaj-mujemy się **złożonością asymptotyczną**.

- Do określania złożoności używamy specjalnej **notacji asymptotycznej** o tym więcej w dalszej części kursu. 

---

## Struktury danych

Struktura danych (ang. *data structure*) - specyficzny sposób przechowywania danych 
w komputerze i dostępu do nich. Przykładem jest tablica:

<table>
  <tr>
    <td>10</td>
    <td>30</td>
    <td>50</td>
    <td>70</td>
  </tr>
</table>

- elementy w tablicach są numerowane, 
- numeracja zwykle rozpoczyna się od 0, a nie od 1, 
- przechowują one zwykle dane określonego rodzaju (liczby całkowite, zmiennoprze-cinkowe itd.). 

---

## Abstrakcyjne typy danych

- W analizie algorytmów opisy operacji na danych często określają tylko, co robią operacje, nie wyjaśniając, jak to robią. 

- W projektowaniu oprogramowania oddzielenie tego, co wykonują operacje, od tego, jak to robią, jest nazywane abstrahowaniem. 

- Zbiór operacji określających, co jest robione, lecz nie jak, nazywamy abstrakcyjnym typem danych (ang. *abstract data type*, ADT).

Omawiając algorytmy będziemy często posługiwać się ADT, jednak mówiąc o programo-waniu w  C++ będziemy mówić o jego typach danych (jak ```int``` czy ```struct```).

---

## System komputerowy z punktu widzenia programisty

---

## System komputerowy

To:
- sprzęt,
- oprogramowanie systemowe (system operacyjny, biblioteki),

które współdziałają w celu uruchamiania programów (aplikacji) użytkownika.


---

## Bity i bajty – podstawowe jednostki informacji

Bit (*binary digit*) – najmniejsza jednostka informacji, może przyjmować jedną z dwóch wartości: 0 lub 1.

Bajt (*byte*) – 8 bitów, najmniejsza adresowalna jednostka pamięci w większości systemów komputerowych.

<center>

| Bit nr  | 7  | 6  | 5  | 4  | 3  | 2  | 1  | 0  |
|---------|----|----|----|----|----|----|----|----|
| Wartość | 1  | 0  | 1  | 0  | 1  | 0  | 0  | 1  |

</center>

$$
\begin{aligned}
W &= 1 \cdot 2^7 + 0 \cdot 2^6 + 1 \cdot 2^5 + 0 \cdot 2^4 + 1 \cdot 2^3 + 0 \cdot 2^2 + 0 \cdot 2^1 + 1 \cdot 2^0 \\
  &= 1 \cdot 128 + 0 \cdot 64 + 1 \cdot 32 + 0 \cdot 16 + 1 \cdot 8 + 0 \cdot 4 + 0 \cdot 2 + 1 \cdot 1 \\
  &= 128 + 32 + 8 + 1 \\
  &= 169
\end{aligned}
$$

---

- Najbardziej znaczący bit (MSB, *Most Significant Bit*) – pierwszy bit z lewej (bit nr 7), ma największą wagę ($2^7$).
- Najmniej znaczący bit (LSB, *Least Significant Bit*) – ostatni bit z prawej (bit nr 0), ma najmniejszą wagę ($2^0$).


---


## Informacja to bity + kontekst

### To jest kod źródłowy programu:

```cpp
#include <iostream>

int main() {
    std::cout << "hello, world" << std::endl;
    return 0;
}
```
programy napisane w języku C++ przechowujemy z rozszerzeniem ```.cpp```, np. ```hello.cpp``` 

---

## Informacja to bity + kontekst

#### &nbsp;
- #### Plik z kodem źródłowym zawiera sekwencję bajtów.
&nbsp;
- #### Każdy z nich reprezentuje jeden znak w kodzie ASCII.
#### &nbsp;
---

## Informacja to bity + kontekst

```cpp
#include <iostream>

int main() {
    std::cout << "hello, world" << std::endl;
    return 0;
}
```

```text
#   i   n   c  l   u   d   e   <sp>  <   i   o   s   t   r   e   a   m  >
35 105 110 99 108 117 100 101   32   60 105 111 115 116 114 101 97 109 62 

i    n   t  <sp>   m   a   i   n   (   )   <sp>   {
105 110 116  32    109 97 105 110  40 41    32   123  

...

```
---
## Informacja to bity + kontekst

- Wszystkie informacje w systemie komputerowym przechowywane są za pomocą bitów. 

- To co odróżnia poszczególne dane od siebie, to kontekst w jakim na nie patrzymy. 

- Jako programiści musimy odróżniać sprzętowe reprezentacje liczb, gdyż są one różne dla różnych ich typów.

---

## Informacja to bity + kontekst

Bajty mogą reprezentować różne rodzaje danych, np.:

- Liczby całkowite – np. ```00000101``` (8-bitowy zapis) to 5 w systemie dziesiętnym.
- Liczby zmiennoprzecinkowe – np. ```01000000010010010000111111011011``` (IEEE 754) to w przybliżeniu 3.14159
- Znaki tekstu – np. ```'A'``` w ASCII to ```01000001```, ```'Z'``` to ```01011010```.
- Tekst – "Hello" w ASCII to ciąg ```01001000 01100101 01101100 01101100 01101111```.
- Kolory w grafice: RGB (czerwony): (255, 0, 0) → ```11111111 00000000 00000000```

---

## Programy są tłumaczone przez inne programy do różnych form

- Program, w postaci kodu źródłowego napisanego przez programistę jest tłumaczony do niskopoziomowej postaci - języka maszynowego.

- Język maszynowy to zestaw instrukcji dla procesora.

- Program ten następnie łączony jest z wymaganymi bibliotekami i przechowywany na dysku w formie binarnej (plik wykonywalny).

---
## Programy są tłumaczone przez inne programy do różnych form

### Język maszynowy
```text
00: 0005   5
01: 0008   8

10: 8A00   R[A] <- mem[00]
11: 8B01   R[B] <- mem[01]
12: 1CAB   R[C] <- R[A] + R[B]
13: 9C02   mem[02] <- R[C]
14: 0000   halt
```

Dodawanie w abstrakcyjnym języku maszynowym TOY (Princeton University).

---

## Programy są tłumaczone przez inne programy do różnych form
### Asembler

Język asemblerowy to taki, którego instrukcje odpowiadają rozkazom procesora w kodzie maszynowym, ale ich liczbowa reprezentacja została zastąpiona przez mnemoniki. 

Jest bardziej czytelny dla człowieka niż język maszynowy.

---

## Programy są tłumaczone przez inne programy do różnych form
### Asembler

```asm
.LC0:
        .string "Hello, world!"
main:
        pushq   %rbp
        movq    %rsp, %rbp
        movl    $.LC0, %edi
        call    puts
        movl    $0, %eax
        popq    %rbp
        ret
  ```
---

## Programy są tłumaczone przez inne programy do różnych form


```sh  
hello.cpp      hello.i       hello.s        hello.o        hello 
    _________      ________      _________      ________
   |         |    |        |    |         |    |        |
   |   pre-  |    |compiler|    |assembler|    | linker |
-->|processor|--->| (ccl)  |--->|  (as)   |--->|  (ld)  |->
   |  (cpp)  |    |________|    |_________|    |________|
   |_________|    
```

```hello.cpp``` - program źródłowy (tekst)  
```hello.i``` - zmodyfikowany program źródłowy (tekst)  
```hello.s``` - program w asemblerze (tekst)  
```hello.o``` - relokowalny plik obiektowy (binarny)  
```hello```  &nbsp;&nbsp;&nbsp; - plik wykonywalny (binarny) 

---

# Podstawowe pojęcia: typ

Typ danych jest to zestaw atrybutów (cech) opisujących dane. Zazwyczaj dotyczy:

- rozmiaru,
- wewnętrznej struktury,
- zakresu wartości,
- zbioru dozwolonych operacji.

Przykładowy typ danych w C to **typ całkowity** ```int```.

---

# Podstawowe pojęcia: typ ```int```

Przykładowy typ danych ```int``` na typowym 32-bitowym procesorze ma:

- **rozmiar**: 4 bajty,
- **zakresu wartości**: od -2147483648 do 2147483647,
- **zbiór dozwolonych operacji**:
  - unarnych: ```+```, ```-```, ```~```, ```&```, ```++```, ```--```,
  - binarnych: ```=```, ```+```, ```-```, ```*```, ```/```, ```%```, ```<```, ```>```, ```==```, ```!=```, ```&```, ```|```, ```&&```, ```||```.

---

# Podstawowe pojęcia

- **instrukcja** - najmniejszy element programu, zawiera akcję do wykonania (np. przypisanie wartości do zmiennej, wywołanie funkcji). 

- **program** - zestaw instrukcji wykonujący określone zadanie.

- **proces** - program komputerowy uruchomiony w systemie operacyjnym.

- **język programowania** - formalnie zdefiniowany zbiór reguł dotyczący semantyki i syntaktyki (składni) określający jak pisać programy.

---

## Języki programowania - podział

### Ze względu na:
- paradygmat,
- sposób wykonywania,
- kontrolę typów,
- poziom.

###

---

## Języki programowania - podział

### Ze względu na paradygmat:

 - **imperatywne**
  *program jako sekwencja instrukcji zmieniających stan systemu*;
  
  - **deklaratywne**
  *program opisuje jakie warunki ma spełniać końcowe rozwiązanie*;
  
---
## Języki programowania - podział

### Ze względu na paradygmat:

 - **proceduralne**
 *program podzielony na procedury, wykonujące określone operacje*;

 - **obiektowe**:
*program jako zbiór obiektów (łączących dane i zachowanie)*;

---

## Języki programowania - podział
### Ze względu na sposób wykonywania:

 - **kompilowane**
   *kod źródłowy programu zamieniany na kod wykonywalny przed uruchomieniem programu*;
 - **interpretowane**
   *programy wykonywane bezpośrednio przez interpreter bez konieczności zamiany na kod maszynowy*;
 
---

## Języki programowania - podział
### Ze względu na typowanie

- **statyczne**
  *typ zmiennych w programie jest znany w momencie kompilacji*;

- **dynamiczne**
  *typ jest określany w momencie wykonywania programu*;
  

---
## Języki programowania - podział
### Ze względu na poziom

- **wysokopoziomowe**
  *abstrakcja od szczegółów sprzętowych, ułatwiająca programowanie;*

- **niskopoziomowe**
 *dostęp do szczegółowych operacji sprzętowych i zarządzania pamięcią;*

---

## C++

### Imperatywny, proceduralny, obiektowy, generyczny, kompilowany, statycznie typowany;

*Omawiamy specyfikację C++11.*


---

## Pisanie programów

1. Zdefiniuj cele dla programu.
2. Zaprojektuj program.
3. Napisz kod źródłowy.
4. Skompiluj.
5. Uruchom.
6. Testuj i debuguj.
7. Utrzymuj i zmieniaj według potrzeb kod źródłowy.

---

## Przykładowy program - struktura



```cpp
#include <iostream>

int main(){
    int year = 2025;
    std::cout << "Witaj w roku " << year << "!" << std::endl;
    return 0;
}
```

---

## Przykładowy program - struktura

```cpp

#include <iostream>
#include <ctime>

int main(){
    // Pobierz aktualny czas systemowy
    std::time_t now = std::time(nullptr);
    std::tm *localTime = std::localtime(&now);
    
    // Oblicz bieżący rok (tm_year liczy lata od 1900)
    int year = 1900 + localTime->tm_year;
    
    std::cout << "Witaj w roku " << year << "!" << std::endl;
    return 0;
}
```

---

## Struktura programu
  
```text                           
     +-----------+
+----|#include...|   <------ dyrektywy preprocesora
|    +-----------+ 
|
|    +-----------+   
+----|int main() |   <------ funkcja główna, zwykle wywołuje inne funkcje zdefiniowane
|    +-----------+           w programie i funkcje biblioteczne
|              | 
|              |         +------------+      
|              +---------| instrukcje |  funkcje składają się z instrukcji 
|                        +------------+                         
|    +-----------+              |                   
+----|funkcja a()|             ...      
|    +-----------+               
|              |         +------------+          
|              +---------| instrukcje |  funkcje zwykle zwracają wartość, która        
|                        +------------+  może użyta w miejscu ich wywołania           
|    +-----------+              |                                 
+----|funkcja b()|             ...                               
|    +-----------+                                                                           
```
&nbsp;

---

## Kompilowanie i uruchomienie

### Kompilator gcc (Linux)


```bash
$ g++ hello.cpp -o hello
$ ./hello
Hello world!
```

- wywołanie kompilatora gcc w ten sposób tworzy plik wykonywalny o nazwie ```hello```
- flaga ```-o``` umożliwia nadanie nazwy plikowi wynikowemu
- ```./``` przed nazwą programu (w lokalnym folderze) służy do uruchomienia go

---

## Inne flagi kompilatora

- ```-Wall``` – włącza ważne ostrzeżenia, ułatwia znalezienie błędów.
- ```-Werror``` – traktuje ostrzeżenia jako błędy.
- ```-g``` – dodaje informacje potrzebne do debugowania (np. w GDB).
- ```-O``` (lub ```-O2```, ```-O3```) – optymalizacja kodu.

---

## Kompilacja, uruchomienie, debugowanie - przykład

---

# Bibliografia

1. Stephen Prata. 2013. C Primer Plus (6th ed.) Addison-Wesley Professional.
2. https://en.cppreference.com/
3. Wprowadzenie do algorytmów / Thomas H. Cormen [et al.] ; z ang. przeł. Krzysztof Diks [et al.]. - Wyd. 7 (1 w PWN).  - Warszawa : Wydawnictwo Naukowe PWN, 2012. 
4. Computer Systems: A Programmer's Perspective / Randal E. Bryant, David R. O'Hallaron. - Wyd. 2. - USA : Addison-Wesley Publishing Company, 2010.
5. Algorytmy bez tajemnic / Thomas H. Cormen l ; [tł. Zdzisław Płoski]. - Gliwice : Helion, cop. 2013. 

---

<!-- backgroundColor: '#eaeaea' -->
<!-- _footer: &nbsp; -->

# Dziękuję za uwagę!
