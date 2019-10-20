# Typy i operatory

Przydatność programów „Hello World” pokazanych w poprzednim rozdziale jest raczej wątpliwa. Musieliśmy napisać kilka wierszy kodu, skompilować je, a następnie uruchomić wynikowy program, aby uzyskać wynik prostego zdania zapisanego na ekranie. Na pewno byłoby o wiele szybciej samemu wpisać zdanie wyjściowe.

Jednak programowanie nie ogranicza się tylko do drukowania prostych tekstów na ekranie. Aby pójść nieco dalej i móc pisać programy wykonujące użyteczne zadania, które naprawdę oszczędzają nam pracy, musimy wprowadzić pojęcie zmiennych.

Wyobraźmy sobie, że proszę o zapamiętanie liczby 5, a następnie proszę o zapamiętanie liczby 2 w tym samym czasie. Właśnie zapisałeś dwie różne wartości w pamięci (5 i 2). Teraz, jeśli poproszę cię o dodanie 1 do pierwszego numeru, który powiedziałem, powinieneś zachować liczby 6 (to jest 5 + 1) i 2 w swojej pamięci. Następnie moglibyśmy na przykład odjąć te wartości i uzyskać wynik 4.

Cały proces opisany powyżej jest podobny do tego, co komputer może zrobić z dwiema zmiennymi. Ten sam proces można wyrazić w C++ za pomocą następującego zestawu instrukcji:

```cpp
a = 5;
b = 2;
a = a + 1;
result = a - b;
```

Oczywiście jest to bardzo prosty przykład, ponieważ użyliśmy tylko dwóch małych liczb całkowitych, ale pamiętaj, że twój komputer może przechowywać miliony takich liczb w tym samym czasie i przeprowadzać z nimi skomplikowane operacje matematyczne.

Możemy teraz zdefiniować zmienną jako część pamięci do przechowywania wartości.

Każda zmienna potrzebuje nazwy, która ją identyfikuje i odróżnia ją od innych. Na przykład w poprzednim kodzie nazwy zmiennych były a, b i wynik, ale moglibyśmy nazwać zmienne dowolnymi nazwami, które moglibyśmy wymyślić, pod warunkiem, że są to prawidłowe identyfikatory C++.

## Identyfikatory

Prawidłowy identyfikator to ciąg jednej lub więcej liter, cyfr lub znaków podkreślenia (`_`). Spacje, znaki interpunkcyjne i symbole nie mogą być częścią identyfikatora. Ponadto identyfikatory zawsze zaczynają się od litery. Mogą również zaczynać się od znaku podkreślenia (`_`), ale takie identyfikatory są - w większości przypadków - uważane za zastrzeżone dla słów kluczowych specyficznych dla kompilatora lub identyfikatorów zewnętrznych, a także identyfikatorów zawierających dwa kolejne znaki podkreślenia w dowolnym miejscu. W żadnym wypadku nie mogą zaczynać się cyfrą.

C++ używa wielu słów kluczowych do identyfikacji operacji i opisów danych; dlatego identyfikatory utworzone przez programistę nie mogą pasować do tych słów kluczowych. Standardowymi zastrzeżonymi słowami kluczowymi, których nie można używać do identyfikatorów tworzonych przez programistów, są:

```
alignas, alignof, and, and_eq, asm, auto, bitand, bitor, bool, break, case, catch, char, char16_t, char32_t, class, compl, const, constexpr, const_cast, continue, decltype, default, delete, do, double, dynamic_cast, else, enum, explicit, export, extern, false, float, for, friend, goto, if, inline, int, long, mutable, namespace, new, noexcept, not, not_eq, nullptr, operator, or, or_eq, private, protected, public, register, reinterpret_cast, return, short, signed, sizeof, static, static_assert, static_cast, struct, switch, template, this, thread_local, throw, true, try, typedef, typeid, typename, union, unsigned, using, virtual, void, volatile, wchar_t, while, xor, xor_eq
```

Określone kompilatory mogą także zawierać dodatkowe, zastrzeżone słowa kluczowe.

Bardzo ważne: język C++ jest językiem „rozróżniającym wielkość liter”. Oznacza to, że identyfikator pisany wielkimi literami nie jest równoważny z innym identyfikatorem o tej samej nazwie, ale zapisanym małymi literami. Zatem na przykład zmienna `RESULT` nie jest taka sama jak zmienna `result` lub zmienna `Result`. Są to trzy różne identyfikatory, identyfikujące trzy różne zmienne.

## Podstawowe typy danych

Wartości zmiennych są przechowywane gdzieś w nieokreślonej lokalizacji w pamięci komputera jako zera i jedynki. Nasz program nie musi znać dokładnej lokalizacji, w której przechowywana jest zmienna; może po prostu odnosić się do niego po nazwie. Program musi być świadomy rodzaju danych przechowywanych w zmiennej. Przechowywanie prostej liczby całkowitej nie jest tym samym, co przechowywanie litery lub dużej liczby zmiennoprzecinkowej; mimo że wszystkie są reprezentowane za pomocą zer i jedynek, nie są interpretowane w ten sam sposób, a w wielu przypadkach nie zajmują takiej samej ilości pamięci.

Podstawowe typy danych to podstawowe typy implementowane bezpośrednio przez język, które reprezentują podstawowe jednostki pamięci obsługiwane natywnie przez większość systemów. Można je głównie podzielić na:

- **Typy tekstowe:** mogą reprezentować pojedynczy znak, na przykład „A” lub „$”. Najbardziej podstawowym typem jest `char`, który jest jednobajtowym znakiem. Inne typy są również przewidziane dla szerszych postaci.
- **Numeryczne typy liczb całkowitych:** mogą przechowywać wartość liczb całkowitych, na przykład 7 lub 1024. Występują w różnych rozmiarach i mogą być podpisane lub niepodpisane, w zależności od tego, czy obsługują wartości ujemne, czy nie.
- **Typy zmiennoprzecinkowe:** Mogą reprezentować wartości rzeczywiste, takie jak 3,14 lub 0,01, z różnymi poziomami dokładności, w zależności od tego, który z trzech typów zmiennoprzecinkowych jest używany.
- **Typ boolowski:** typ boolowski, znany w C ++ jako bool, może reprezentować tylko jeden z dwóch stanów, true lub false.

Dokładna lista typów znajduje się pod linkiem:

- [Lista typów C++](https://www.tutorialspoint.com/cplusplus/cpp_data_types.htm)

W każdej z powyższych grup różnica między typami polega tylko na ich wielkości (tj. Ile zajmują w pamięci): pierwszy typ w każdej grupie jest najmniejszy, a ostatni jest największy, przy czym każdy typ jest co najmniej taki sam duży jak ten poprzedzający go w tej samej grupie. Poza tym typy w grupie mają te same właściwości.

Zauważ w powyższym panelu, że poza char (który ma rozmiar dokładnie jednego bajtu), żaden z podstawowych typów nie ma określonego standardowego rozmiaru (ale najwyżej rozmiaru minimalnego). Dlatego typ nie jest wymagany (aw wielu przypadkach nie jest) dokładnie ten minimalny rozmiar. Nie oznacza to, że typy te mają nieokreślony rozmiar, ale nie ma standardowego rozmiaru we wszystkich kompilatorach i maszynach; każda implementacja kompilatora może określać rozmiary tych typów, które najlepiej pasują do architektury, w której program będzie uruchamiany. Ta dość ogólna specyfikacja wielkości dla typów daje język C ++ dużą elastyczność, którą można dostosować do optymalnej pracy na wszystkich rodzajach platform, zarówno obecnych, jak i przyszłych.

W przypadku typów całkowitych posiadanie bardziej reprezentatywnych wartości oznacza, że ​​zakres wartości, które mogą reprezentować, jest większy; na przykład 16-bitowa liczba całkowita bez znaku byłaby w stanie reprezentować 65536 różnych wartości w zakresie od 0 do 65535, podczas gdy jej podpisany odpowiednik byłby w stanie reprezentować, w większości przypadków, wartości od -32768 do 32767. Należy zauważyć, że zakres wartości dodatnie są w przybliżeniu zmniejszone o połowę w typach ze znakiem w porównaniu z typami bez znaku, ze względu na fakt, że jeden z 16 bitów jest używany dla znaku; jest to stosunkowo niewielka różnica w zakresie i rzadko uzasadnia użycie niepodpisanych typów na podstawie wyłącznie zakresu dodatnich wartości, które mogą reprezentować.

Dla typów zmiennoprzecinkowych rozmiar wpływa na ich precyzję, ponieważ zawiera mniej lub więcej bitów dla ich znaczącej i wykładniczej wartości.

Jeśli rozmiar lub precyzja typu nie jest problemem, to zwykle char, int i double są zwykle wybierane do reprezentowania odpowiednio znaków, liczb całkowitych i liczb zmiennoprzecinkowych. Inne typy w odpowiednich grupach są używane tylko w bardzo szczególnych przypadkach.

Właściwości podstawowych typów w konkretnej implementacji systemu i kompilatora można uzyskać za pomocą klas numeric_limits (patrz standardowy nagłówek <limits>). Jeśli z jakiegoś powodu potrzebne są typy o określonych rozmiarach, biblioteka definiuje pewne aliasy typu o stałym rozmiarze w nagłówku <cstdint>.

Typy opisane powyżej (znaki, liczby całkowite, zmiennoprzecinkowe i logiczne) są wspólnie znane jako typy arytmetyczne. Istnieją jednak dwa dodatkowe podstawowe typy: pustka, która wskazuje na brak typu; oraz typ nullptr, który jest specjalnym typem wskaźnika. Oba typy zostaną omówione w następnym rozdziale na temat wskaźników.

C ++ obsługuje szeroką gamę typów w oparciu o podstawowe typy omówione powyżej; te inne typy są znane jako złożone typy danych i są jedną z głównych zalet języka C ++. Zobaczymy je również bardziej szczegółowo w przyszłych rozdziałach.

## Deklaracja zmiennych

C ++ jest silnie typowanym językiem i wymaga, aby każda zmienna była zadeklarowana ze swoim typem przed pierwszym użyciem. Informuje to kompilator, jaki rozmiar rezerwować w pamięci dla zmiennej i jak interpretować jej wartość. Składnia do deklarowania nowej zmiennej w C ++ jest prosta: po prostu piszemy typ, po którym następuje nazwa zmiennej (tj. Jej identyfikator). Na przykład:

```cpp
int a;
float mynumber;
```

Są to dwie prawidłowe deklaracje zmiennych. Pierwszy deklaruje zmienną typu int o identyfikatorze a. Drugi deklaruje zmienną typu float z identyfikatorem mynumber. Po zadeklarowaniu zmienne a i mynumber mogą być używane w pozostałej części ich zakresu w programie.
Jeśli deklaruje więcej niż jedną zmienną tego samego typu, wszystkie mogą być zadeklarowane w jednej instrukcji, oddzielając ich identyfikatory przecinkami. Na przykład:

```cpp
int a, b, c;
```

Ponizej deklarujemy trzy zmienne (a, b i c), wszystkie typu int, i ma dokładnie takie samo znaczenie jak:

```cpp
int a;
int b;
int c;
```

Aby zobaczyć, jak wyglądają deklaracje zmiennych w działaniu w programie, spójrzmy na cały kod C ++ w przykładzie dotyczącym twojej pamięci mentalnej zaproponowanym na początku tego rozdziału:

```cpp
#include <iostream>
using namespace std;

int main ()
{
  // declaring variables:
  int a, b;
  int result;

  // process:
  a = 5;
  b = 2;
  a = a + 1;
  result = a - b;

  // print out the result:
  cout << result;

  // terminate the program:
  return 0;
}
```

## Inicjalizacja zmiennych

Kiedy zmienne w powyższym przykładzie są zadeklarowane, mają nieokreśloną wartość, dopóki nie zostaną im przypisane wartości po raz pierwszy. Ale możliwe jest, że zmienna ma określoną wartość od momentu jej zadeklarowania. Nazywa się to inicjalizacją zmiennej.

W C ++ istnieją trzy sposoby inicjowania zmiennych. Wszystkie są równoważne i przypominają ewolucję języka na przestrzeni lat:

- Pierwszy, znany jako inicjalizacja podobna do c (ponieważ jest dziedziczona z języka C), polega na dołączeniu znaku równości, po którym następuje wartość, dla której inicjowana jest zmienna:
   ```cpp
   identyfikator typu = wartość_początkowa;
   ```
   Na przykład, aby zadeklarować zmienną typu int o nazwie x i zainicjować ją do wartości zero od tego samego momentu, w którym zostanie zadeklarowana, możemy napisać:
   ```cpp
   int x = 0;
   ```
- Druga metoda, znana jako inicjalizacja konstruktora (wprowadzona przez język C ++), obejmuje wartość początkową między nawiasami:
   ```cpp
   int x (0);
   ```
- Trzecia metoda, znana jako jednolita inicjalizacja, podobna do powyższej, ale za pomocą nawiasów klamrowych ({}) zamiast nawiasów (została wprowadzona w wyniku zmiany standardu C++ w 2011 r.):
   ```cpp
   int x {0}; 
   ```

**Przykład inicjalizacji zmiennych:**

```cpp
#include <iostream>
using namespace std;

int main ()
{
  int a=5;               // initial value: 5
  int b(3);              // initial value: 3
  int c{2};              // initial value: 2
  int result;            // initial value undetermined

  a = a + b;
  result = a - c;
  cout << result;

  return 0;
}
```

## Wartości tekstowe

Typy podstawowe reprezentują najbardziej podstawowe typy obsługiwane przez maszyny, na których może działać kod. Ale jedną z głównych zalet języka C++ jest jego bogaty zestaw typów złożonych, z których podstawowymi typami są jedynie elementy składowe.

Przykładem typu złożonego jest klasa `string`. Zmienne tego typu mogą przechowywać sekwencje znaków, takie jak słowa lub zdania. Bardzo przydatna funkcja!

Pierwszą różnicą w stosunku do podstawowych typów danych jest to, że w celu zadeklarowania i użycia obiektów (zmiennych) tego typu, program musi zawierać nagłówek, w którym typ jest zdefiniowany w standardowej bibliotece (nagłówek <ciąg>):

```cpp
#include <iostream>
#include <string>
using namespace std;

int main ()
{
  string mystring;
  mystring = "This is a string";
  cout << mystring;
  return 0;
}
```

Jak widać w poprzednim przykładzie, łańcuchy mogą być inicjowane dowolnym poprawnym literałem łańcuchowym, podobnie jak zmienne typu numerycznego mogą być inicjalizowane dowolnym poprawnym literałem liczbowym. Podobnie jak w przypadku typów podstawowych, wszystkie formaty inicjalizacji są poprawne z ciągami:

```cpp
string mystring = "This is a string";
string mystring ("This is a string");
string mystring {"This is a string"};
```

Ciągi mogą również wykonywać wszystkie inne podstawowe operacje, które mogą wykonywać podstawowe typy danych, takie jak zadeklarowanie bez wartości początkowej i zmiana jej wartości podczas wykonywania:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main ()
{
  string mystring;
  mystring = "This is the initial string content";
  cout << mystring << endl;
  mystring = "This is a different string content";
  cout << mystring << endl;
  return 0;
}
```

## Wartości stałe

Literals są najbardziej oczywistym rodzajem stałych. Służą do wyrażania określonych wartości w kodzie źródłowym programu. Użyliśmy już niektórych z poprzednich rozdziałów, aby podać określone wartości zmiennym lub wyrazić komunikaty, które chcieliśmy, aby nasze programy wydrukowały, na przykład, gdy napisaliśmy:

```cpp
a = 5;
```

Czasami wygodnie jest nadać nazwę stałej wartości:

```cpp
const double pi = 3.1415926;
const char tab = '\t';
```

Następnie możemy użyć tych nazw zamiast literałów, do których zostały zdefiniowane:

```cpp
using namespace std;

const double pi = 3.14159;
const char newline = '\n';

int main ()
{
  double r=5.0;               // radius
  double circle;

  circle = 2 * pi * r;
  cout << circle;
  cout << newline;
}
```

## Definicje preprocesora (#define)

Innym mechanizmem nazywania wartości stałych jest użycie definicji preprocesora. Mają następującą formę:

```cpp
#define identifier replacement
```

Po tej dyrektywie każde wystąpienie identyfikatora w kodzie jest interpretowane jako zamiana, gdzie zamiana jest dowolną sekwencją znaków (do końca wiersza). Ta zamiana jest wykonywana przez preprocesor i ma miejsce przed kompilacją programu, powodując w ten sposób rodzaj ślepej zamiany: ważność typów lub składni nie jest w żaden sposób sprawdzana.

```cpp
#include <iostream>
using namespace std;

#define PI 3.14159
#define NEWLINE '\n'

int main ()
{
  double r=5.0;               // radius
  double circle;

  circle = 2 * PI * r;
  cout << circle;
  cout << NEWLINE;

}
```

## Operatory

Po wprowadzeniu do zmiennych i stałych możemy zacząć z nimi operować za pomocą operatorów. Poniżej znajduje się pełna lista operatorów. W tym momencie prawdopodobnie nie trzeba znać ich wszystkich, ale wszystkie są tutaj wymienione, aby służyć również jako odniesienie.

Operator przypisania przypisuje wartość do zmiennej.

```cpp
x = 5;
```

Ta instrukcja przypisuje wartość całkowitą 5 do zmiennej x. Operacja przypisania odbywa się zawsze od prawej do lewej, a nigdy na odwrót:

```cpp
x = y;
```

Ta instrukcja przypisuje zmiennej x wartość zawartą w zmiennej y. Wartość x w momencie wykonania tej instrukcji jest tracona i zastępowana przez wartość y.

Weź również pod uwagę, że przypisujemy wartość y do x w momencie operacji przypisania. Dlatego jeśli y zmieni się w późniejszym momencie, nie wpłynie to na nową wartość przyjętą przez x.

Na przykład, spójrzmy na następujący kod - ewolucję treści przechowywanej w zmiennych zawarłem jako komentarze:

```cpp
#include <iostream>
using namespace std;

int main ()
{
  int a, b;         // a:?,  b:?
  a = 10;           // a:10, b:?
  b = 4;            // a:10, b:4
  a = b;            // a:4,  b:4
  b = 7;            // a:4,  b:7

  cout << "a:";
  cout << a;
  cout << " b:";
  cout << b;
}
```

Pięć operacji arytmetycznych obsługiwanych przez C ++ to:
- `+`, `-`, `*`, `/`, `%`

Niektóre wyrażenia można jeszcze bardziej skrócić: operator zwiększania (++) i operator zmniejszania (--) zwiększają lub zmniejszają o jedną wartość przechowywaną w zmiennej. Są one odpowiednio równoważne += 1 i -= 1. A zatem:

```cpp
++x;
x+=1;
x=x+1;
```

### Operatory porównania

Dwa wyrażenia można porównać za pomocą operatorów relacyjnych i równości. Na przykład, aby wiedzieć, czy dwie wartości są równe lub czy jedna jest większa od drugiej.

Wynikiem takiej operacji jest albo prawda, albo fałsz (tj. Wartość logiczna).

Operatory relacyjne w C ++ to:

- `==`, `!=`, `<`, `>`, `<=`, `=>`.

```cpp
(7 == 5)     // evaluates to false
(5 > 4)      // evaluates to true
(3 != 2)     // evaluates to true
(6 >= 6)     // evaluates to true
(5 < 5)      // evaluates to false 
```

Bądź ostrożny! Operator przypisania (operator = z jednym znakiem równości) nie jest tym samym co operator porównania równości (operator ==, z dwoma znakami równości); pierwszy (=) przypisuje wartość po prawej stronie zmiennej po lewej, a drugi (==) porównuje, czy wartości po obu stronach operatora są równe. Dlatego w ostatnim wyrażeniu ((b = 2) == a) najpierw przypisaliśmy wartość 2 do b, a następnie porównaliśmy ją z a (która również przechowuje wartość 2), uzyskując wartość true.

### Operatory logiczne

Operator `!` jest operatorem C ++ dla operacji logicznej NOT. Ma tylko jeden operand po swojej prawej stronie i odwraca go, wytwarzając fałsz, jeśli jego operand jest prawdziwy, i prawdziwy, jeśli jego operand jest fałszywy. Zasadniczo zwraca odwrotną wartość logiczną podczas oceny swojego argumentu. Na przykład:

```cpp
!(5 == 5)   // evaluates to false because the expression at its right (5 == 5) is true
!(6 <= 4)   // evaluates to true because (6 <= 4) would be false
!true       // evaluates to false
!false      // evaluates to true 
```

Operatory logiczne `&&` i `||` są używane podczas oceny dwóch wyrażeń w celu uzyskania pojedynczego wyniku relacyjnego. Operator `&&` odpowiada logicznej operacji logicznej AND, która daje wartość true, jeśli oba operandy są prawdziwe, a fałsz w przeciwnym razie. Poniższy panel pokazuje wynik oceny przez operatora `&&` wyrażenia `a&&b`. Operator `||` odpowiada logicznej operacji logicznej OR, która daje wartość true, jeśli jeden z jego operandów jest prawdziwy, a zatem jest fałszywy tylko wtedy, gdy oba operandy są fałszywe.

```cpp
( (5 == 5) && (3 > 6) )  // evaluates to false ( true && false )
( (5 == 5) || (3 > 6) )  // evaluates to true ( true || false ) 
```

Używając operatorów logicznych, C++ ocenia tylko to, co jest konieczne od lewej do prawej, aby uzyskać połączony wynik relacyjny, ignorując resztę. Dlatego w ostatnim przykładzie `((5 == 5) || (3> 6))` C++ ocenia najpierw, czy `5 == 5 `jest prawdą, a jeśli tak, nigdy nie sprawdza, czy `3> 6` jest prawdą, czy nie.

# Ćwiczenia