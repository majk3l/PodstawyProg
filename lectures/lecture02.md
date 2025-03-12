# Podstawy programowania.
### Wykład #2: Struktura programu. Wyrażenia, operatory, instrukcje.
*dr inż. Michał Kępski* 

<!-- footer: | e-mail: mkepski@ur.edu.pl | 
-->

---
<!-- footer: | PwJC | Wykład #2 | dr inż. Michał Kępski | https://github.com/majk3l/C-Introduction/
     page_number: true -->

# Struktura programu

### Przykładowy program:

```cpp
#include <iostream> // dołączenie pliku nagłówkowego

int main() {
    int year;    // deklaracja zmiennej
    year = 2024; // przypisanie wartości do zmiennej
    
    /* To jest komentarz 
    zawierający więcej niż jedną linię */
    
    std::cout << "Hello in " << year << std::endl; // wywołanie funkcji
    
    return 0;
}
```

---

## Program w C++ - imperatywnym języku programowania

Programy są budowane z zestawu podstawowych instrukcji, które komputer potrafi interpretować i wykonywać.

Każdy program składa się z instrukcji głównie realizujących zadania z zakresu:

- Operacji arytmetycznych i logicznych – np. dodawanie, mnożenie, porównania (```+```, ```-```, ```*```, ```==```, ```&&```).
- Proste testy (warunki) – sprawdzanie warunków i sterowanie programem (m. in. ```if```, ```for```, ```switch```).
- Przenoszenia danych – operacje kopiowania i przemieszczania informacji między pamięcią, rejestrami i innymi urządzeniami (w tym wejścia/wyjścia).


---

## Struktura programu
  
```text
|    +-----------+
+----|#include...|   <------dyrektywy preprocesora
|    +-----------+ 
|    +-----------+   
+----|int main() |   <------funkcja główna
|    +-----------+
|              |          +------------+      zawierają tokeny:
|              +----------| instrukcje |  ________________
|                         +------------+                  |       
|                                   |                     V
|    +-----------+    funkcje       |                 +--------------+ 
+----|funkcja a()|  składają się    :deklaracje     <-|słowa kluczowe|
|    +-----------+  z instrukcji    :przypisania    <-|identyfikatory|
|              |  +------------+    :funkcje        <-|   literały   |
|              +--| instrukcje |    :sterujące      <-|  operatory   |
|                 +------------+    :puste          <-|  separatory  | 
|    +-----------+           |          ^           <-+--------------+                
+----|funkcja b()|          ...        /|\                        
|    +-----------+                      |                           
                                rodzaje instrukcji    
```
&nbsp;

---

## ```#include``` 

- dyrektywa preprocesora,
- przetwarzana przed procesem kompilowania kodu,
- ```include``` dołącza zawartość wskazanego pliku w jej miejsce,
- są inne dyrektywy, np. do definiowania stałych (makr), czy dyrektywy warunkowe,
- musi rozpoczynać się znakiem ```#```
- zwykle będziemy używać jej do dołączania bibliotek.

---

## Funkcje

#### Czym jest funkcja?

Funkcja to blok kodu, który wykonuje określone zadanie i może być wielokrotnie wywo-ływany w programie. Pozwala na organizację i ponowne użycie kodu.

Do funkcji możemy przekazać dane (parametry) i wykorzystać wynik zwracany przez funkcję.

#### Każda funkcja składa się z:

- nagłówka – określa nazwę funkcji, typ zwracanej wartości i parametry,
- ciała funkcji – zawiera instrukcje do wykonania,
- instrukcji ```return``` (opcjonalnie) – zwraca wynik funkcji.

---

## Funkcje - analogia matematyczna

Funkcja matematyczna to zależność przypisująca każdemu elementowi zbioru wejściowe-go dokładnie jeden element zbioru wyjściowego.

Funkcja w programowaniu działa podobnie – przyjmuje wartości wejściowe (parametry) i zwraca wynik.

Jednak kontekst funkcji matematycznej jest czysto obliczeniowy, a funkcji w programowa-niu jest szerszy: funkcja może zwracać wiele wartości bądź nic, może wykonywać operacje na pamięci, plikach itp.

Jest to więc nazwany ciąg instrukcji, który realizuje jakieś zadanie.


---

## Funkcje - przykład

```cpp

#include <iostream>

// Deklaracja funkcji
double dodaj(double a, double b) {
    return a + b; // Zwracanie wyniku
}

int main() {
    double wynik = dodaj(5.2, 3.8);
    std::cout << "Wynik: " << wynik << std::endl;
    return 0;
}
```

---

## Wyjście standardowe - czym jest ```std::cout```?

- ```std::cout``` oznacza standardowy strumień wyjścia (ang. *standard output*).

- ```<<``` to operator, który "wysyła" dane do ```std::cout```.

- ```std::endl``` kończy linię, tak jakbyśmy nacisnęli "Enter".

- ```<<``` to operator, który wewnętrznie wywołuje funkcję do obsługi wyjścia.

---

## Biblioteki w językach programowania

Biblioteki to zbiory gotowych funkcji (często klas i modułów), które mogą być używane w programach, aby uniknąć powtarzalnego kodu i ułatwić pracę programistom.

###### Rodzaje bibliotek:

- Standardowe – dostarczane wraz z językiem programowania (np. iostream w C++)
- Zewnętrzne – tworzone przez społeczność/firmy, instalowane dodatkowo (np. boost)
- Własne – tworzone przez programistów na potrzeby konkretnego projektu.

###### Korzyści z używania bibliotek:

- Skracają czas i ułatwiają programowanie.
- Zwiększają czytelność kodu, zmniejszają ryzyko błędów (sprawdzone rozwiązania).
- Pozwalają na łatwe dodawanie nowych funkcji do programu.

---

## Funkcja ```main()```

- funkcja, od której program rozpoczyna działanie, 

- jej istnienie jest wymagane,

- zazwyczaj zawiera wywołania innych funkcji.

---

## Zmienna 

Zmienna to nazwana przestrzeń w pamięci komputera, w której można przechowywać dane. Jej wartość może się zmieniać podczas działania programu.

Program zwykle będzie polegał na kolejnym zmienianiu wartości poszczególnych zmiennych, realizując jakąś procedurę obliczeniową.

Aby użyć zmiennej, trzeba ją zadeklarować, podając jej typ i nazwę.

```cpp
int year;
year = 2024;
```

---


## Identyfikatory (*identifiers*)

```cpp
int year;
year = 2024;
```

```year``` jest identyfikatorem.

Poprawny identyfikator składa się z liter (małych i wielkich), cyfr oraz znaku ``` _ ```.
Nie może rozpoczynać się od cyfry.

C++ rozróżnia wielkość liter, ```year``` i ```Year``` to różne identyfikatory.

---

## Błędne identyfikatory ❌

```cpp
int 2years;    //  Zaczyna się od cyfry
double class;  //  "class" to słowo kluczowe w C++
float height#; //  Niepoprawny znak '#'
```

---

## Słowa kluczowe

Zarezerwowane elementy składni języka, nie można ich użyć do innych celów niż przeznaczone (np. jako nazwy własnych zmiennych). 


---

## Słowa kluczowe
Podstawowe słowa kluczowe (dziedziczone z C):

```auto``` ```break``` ```case``` ```char``` ```const``` ```continue``` ```default``` ```do``` ```double```
 ```else``` ```enum``` ```extern``` ```float``` ```for``` ```goto``` ```if``` ```int``` ```long``` ```register``` ```return``` ```short``` ```signed``` ```sizeof``` ```static``` ```struct``` ```switch``` ```typedef``` ```union``` ```unsigned``` ```void```  ```volatile``` ```while```

Ponadto: ```bool``` ```catch``` ```class``` ```delete``` ```explicit```   ```false``` ```friend``` ```inline``` ```mutable``` ```namespace```   ```new``` ```operator``` ```private``` ```protected``` ```public``` ```reinterpret_cast``` ```static_cast``` ```dynamic_cast``` ```const_cast```   ```template``` ```this``` ```throw``` ```true``` ```try```   ```typeid``` ```typename``` ```using``` ```virtual``` ```wchar_t```  

Pełna lista: https://en.cppreference.com/w/cpp/keyword



---

## Literały

Stałe wartości w kodzie źródłowym, przykładowo ```5``` czy ```'e'```.

Mają określony typ, określany przez kompilator na podstawie ich wartości. Można też wskazać typ przez rzutowanie.

---

## Literały znakowe *escape sequences*

- składają się z dwóch lub więcej znaków,
- mapują się do pojedynczej wartości typu ```char```,
- reprezentują znaki specjalne i niedrukowane elementy tekstu (znaki nowej linii, tabulacje itp.),
- przykłady: ```'\n'```, ```'\t'```, ```'\\'```.



---

## Separatory (*separators*) i białe znaki (*white spaces*)


Oddzielają tokeny. Separatory (jednocześnie będące tokenami) to:

```( ) [ ] { } ; , . :``` **White spaces** są separatorem, ale nie tokenem.


```cpp
#include <iostream>

int main() {
    std::cout << "hello, world\n";
    return 0;
}
```
```cpp
#include <iostream>
int main(){std::cout << "hello, world\n";return 0;}
```
Z punktu widzenia kompilatora powyższe programy są równoważne.

---

## Wyrażenia

Wyrażenia składają się z **operatorów i operandów.** Pojedynczy operand także jest wyrażeniem.

Wyrażenia mają **wartości**.

---
## Wyrażenia

<!--
<style scoped>
th { background-color: #ffffffff; border-color: #ffffffff }    
td { background-color: #ffffffff; border-color: #ffffffff }
</style>
-->


| Wyrażenie | Wartość | 
|:-:|:-:|
|```-4 + 6``` | 2 |
|```c = 3 + 8``` | 11|
| ```5 > 3``` | 1 |
|```6 + (c = 3 + 8)``` | 17 |

---



## Instrukcje

Podstawowe elementy budowy programu. Instrukcje zakończone są średnikiem.
```eyes = 2```
jest wyrażeniem, ale
```eyes = 2;```
jest instrukcją.

---
## Instrukcje

- ```;```  (instrukcja pusta)

- **proste** - nie zawierają innych instrukcji jako składowych, np. instrukcja przypisania.
- **złożone** - zawierają jedną lub więcej instrukcji (które też mogą być złożone) i są otoczone znakami ```{}```.

---

# Operatory

Wartości wyrażeń wyznaczane są w oparciu o:
- semantykę,
- priorytet,
- łączność

operatorów, oraz wartości operandów.

---
## Typy operatorów

- *Arithmetic* (arytmetyczne, w tym bitowe),
- *Assignment* (przypisania),
- *Member access* (dostępu),
- *Logical* (logiczne),
- *Comparison* (porównania).

---

<!--
<style scoped>  
td { background-color: #ffffffff;  }
</style>
-->


## Arytmetyczne
  
| Operator | Nazwa| Przykład | Rezultat|
|:-:|:-:|:-:|:-:|
| ```+```  | plus (unarny)  | ```+a``` | promocja typu do ```int```  |
| ```-```  | minus (unarny) | ```-a``` | zmiana znaku na przeciwny |
| ```+```  | dodawanie | ```a + b```   | suma wartości operandów |
| ```-```  | odejmowanie | ```a - b``` | różnica wartości operandów |
| ```*```  | mnożenie | ```a * b```    | iloczyn wartości operandów |
| ```/```  | dzielenie | ```a / b```   | iloraz wartości operandów |
| ```%```  | modulo | ```a % b```   | resza z dzielenia ```a``` przez ```b``` |

---

<!--
<style scoped>  
td { background-color: #ffffffff;  }
</style>
-->


## Arytmetyczne: bitowe

| Operator | Nazwa| Przykład | Rezultat|
|:-:|:-:|:-:|:-:|
| ```~```  | negacja bitowa      | ```~a```    | negacja (dopełnienie) bitowe  |
| ```&```  | iloczyn bitowy      | ```a & b``` | iloczyn bitowy ```a``` i ```b```  |
| ```\|``` | suma bitowa         | ```a \| b```| suma bitowa ```a``` i ```b``` |
| ```^```  | xor                 | ```a ^ b``` | bitowa alternatywa rozłączna ```a``` i ```b``` |
| ```<<``` | przesunięcie bitowe | ```a << b```| ```a``` przesunięte o ```b``` bitów w lewo |
| ```>>``` | przesunięcie bitowe | ```a >> b```| ```a``` przesunięte o ```b``` bitów w prawo |

---

## Przypisania

<!--
<style scoped>
table { font-size: 26px; }
td { background-color: #ffffffff;  }
p {font-size: 22px; }
</style>
-->


| Operator | Nazwa | Przykład | Rezultat |
|:-:|:-:|:-:|:-:|
| ```=```   | *basic assignment*       | ```a = b```    | ```a``` otrzymuje wartość ```b``` |
| ```+=```  | *addition assignment*    | ```a += b```   | ```a``` otrzymuje wartość ```a + b``` |
| ```-=```  | *subtraction assignment* | ```a -= b```   | ```a``` otrzymuje wartość ```a - b``` |
| ```*=```  | *multiplication assignment* | ```a *= b```   | ```a``` otrzymuje wartość ```a * b``` |
| ```/=```  | *division assignment* | ```a /= b```   | ```a``` otrzymuje wartość ```a / b``` |
| ```%=```  | *modulo assignment* | ```a %= b```   | ```a``` otrzymuje wartość  ```a % b``` |
| ```&=```  | *bitwise AND assignment* | ```a &= b```   | ```a``` otrzymuje wartość ```a & b``` |

Dla pozostałych operacji bitowych istnieją operatory przypisania: ```|=``` ```^=``` ```<<=``` ```>>=```, działają one anlogicznie do ```&=```.

---

## Logiczne

<!--
<style scoped>
td { background-color: #ffffffff;  }
</style>
-->

| Operator | Nazwa | Przykład | Rezultat |
|:-:|:-:|:-:|:-:|
| ```!```   | negacja logiczna | ```!a```       | logiczna negacja ```a```|
| ```&&```  | iloczyn logiczny | ```a && b```   | logiczny iloczyn ```a``` i ```b``` |
| ```\|\|```| suma logiczna    | ```a \|\| b``` | logiczna suma  ```a``` i ```b```   |

###### *Any **nonzero** expression is considered **true** in C, while an expression that evaluates to **zero** is considered **false**.*

---
## Logiczne: NOT

*The logical NOT expression has the form*

```!expression```		

*where:*

***expression***	-	*an expression of any scalar type.*

*The logical NOT operator has type* **```int```**. *Its value is* ``0`` *if expression evaluates to a value that compares unequal to zero.*

*Its value is* ```1``` *if expression evaluates to a value that compares equal to zero.*

---

## Logiczne: AND

*The logical AND expression has the form*

```lhs && rhs```		

*where*

***lhs, rhs*** - an expression of any scalar type

*The logical AND operator has type* **```int```** *and the value* ```1``` *if both lhs and rhs compare unequal to zero. It has the value* ```0``` *otherwise (if either lhs or rhs or both compare equal to zero).*

*There is a sequence point after the evaluation of lhs. If the result of lhs compares equal to zero, then rhs is not evaluated at all (so-called short-circuit evaluation).*

---

<!--
<style scoped>
td { background-color: #ffffffff;  }
</style>
-->

## Comparison (porównania)

  
| Operator | Przykład | Rezultat|
|:-:|:-:|:-:|
|```==```| ```a == b```|1 jeśli wartości ```a``` i ```b``` są równe, inaczej 0|
|```!=```| ```a != b```|1 jeśli wartości ```a``` i ```b``` są różne, inaczej 0|
|```<``` |```a < b```|1 jeśli wartość ```a``` mniejsza od  ```b```, inaczej 0|
|```>```|```a > b```|1 jeśli wartość ```a``` większa od  ```b```, inaczej 0|
|```<=```| ```a <= b```|1 jeśli wartość ```a``` mniejsza lub równa od  ```b```, inaczej 0|
|```>=```|```a >= b```|1 jeśli wartość ```a``` większa lub równa od  ```b```, inaczej 0|

---

## Operatory inkrementacji ```++``` i dekrementacji ```--```

Operatory te (odpowiednio) dodają bądź odejmują od operandu wartość 1. Można je stosować przed lub po operandzie, co daje różne wyniki:

```cpp
#include <iostream>
int main() {
    int x = 5;
    std::cout << x++ << "\n";  // Wypisuje x, a następnie go inkrementuje
                               // x ma teraz wartość 6
    std::cout << ++x << "\n";  // Inkrementuje x, a następnie go wypisuje
}
```

co skutkuje wypisaniem na konsolę:

```
5
7
```

---

## Operatory

Każdy z operatorów ma przypisany:

- **priorytet** - w jakiej kolejności wykonywane będą różne operacje zawarte w tym samym wyrażeniu,
- **łączność** - kolejność wykonywania operacji o tym samym priorytecie.

---

## Operatory: priorytet i łączność

https://en.cppreference.com/w/cpp/language/operator_precedence

---

# Bibliografia

1. Stephen Prata. 2011. C++ Primer Plus; Addison-Wesley Professional.
2. https://en.cppreference.com/
