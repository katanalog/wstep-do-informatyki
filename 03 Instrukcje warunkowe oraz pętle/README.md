# Instrukcje warunkowe oraz pętle

Instrukcja C++ jest każdą z indywidualnych instrukcji programu, takich jak deklaracje zmiennych i wyrażenia widoczne w poprzednich sekcjach. Zawsze kończą się średnikiem (;) i są wykonywane w tej samej kolejności, w jakiej występują w programie.

Ale programy nie są ograniczone do liniowej sekwencji instrukcji. Podczas tego procesu program może powtarzać segmenty kodu lub podejmować decyzje i rozwidlać. W tym celu C++ udostępnia instrukcje kontroli przepływu, które służą do określenia, co nasz program musi zrobić, kiedy i w jakich okolicznościach.

Wiele instrukcji kontroli przepływu wyjaśnionych w tej sekcji wymaga ogólnej instrukcji jako części składni. Ta instrukcja może być prostą instrukcją C++, taką jak pojedyncza instrukcja, zakończoną średnikiem (;) - lub instrukcją złożoną. Instrukcja złożona to grupa instrukcji (każda zakończona własnym średnikiem), ale wszystkie zgrupowane razem w bloku, zamknięte w nawiasy klamrowe:

```cpp
{ wyrażenie1; wyrażenie2; wyrażenie3; } 
```

Cały blok jest uważany za pojedynczą instrukcję (składającą się z wielu podstacji). Ilekroć instrukcja ogólna jest częścią składni instrukcji kontroli przepływu, może to być instrukcja prosta lub instrukcja złożona.

## IF - ELSE

Słowo kluczowe if służy do wykonania instrukcji lub bloku, tylko wtedy, gdy warunek jest spełniony. Jego składnia to:

```cpp
if (wyrażenie) zróbCoś;
```

Tutaj warunek jest ocenianym wyrażeniem. Jeśli ten warunek jest spełniony, instrukcja jest wykonywana. Jeśli jest to fałsz, instrukcja nie jest wykonywana (jest po prostu ignorowana), a program kontynuuje działanie zaraz po całej instrukcji wyboru. Na przykład poniższy fragment kodu wypisuje komunikat (x wynosi 100), tylko jeśli wartość przechowywana w zmiennej x rzeczywiście wynosi 100:

```cpp
if (x == 100)
  cout << "x wynosi 100";
```

Jeśli x nie jest dokładnie 100, to polecenie jest ignorowane i nic nie jest drukowane.

Jeśli chcesz dołączyć więcej niż jedną instrukcję do wykonania, gdy warunek jest spełniony, instrukcje te powinny być ujęte w nawiasy klamrowe (`{}`), tworząc blok:

```cpp
if (x == 100)
{
   cout << "x to ";
   cout << x;
}
```

Jak zwykle wcięcia i podziały wierszy w kodzie mają tylko efekt wizualny, więc powyższy kod jest równoważny z:

```cpp
if (x == 100) { cout << "x to "; cout << x; }
```

Instrukcje wyboru z if mogą również określać, co dzieje się, gdy warunek nie jest spełniony, poprzez użycie słowa kluczowego else w celu wprowadzenia instrukcji alternatywnej. Jego składnia to:

```cpp
if (wyrażenie) zróbCoś else zróbCośInnego
```

gdzie `zróbCoś` jest wykonywane, jeśli warunek jest spełniony, a jeśli tak nie jest, `zróbCośInnego` jest wykonywane. Na przykład:

```cpp
if (x == 100)
  cout << "x jest 100";
else
  cout << "x nie jest 100";
```

Kilka struktur if + else można połączyć w celu sprawdzenia zakresu wartości. Na przykład:

```cpp
if (x > 0)
  cout << "x jest większe od zera";
else if (x < 0)
  cout << "x jest mniejsze od zera";
else
  cout << "x jest równe zero";
```

Wypisuje, czy x jest dodatnie, ujemne lub równe zero, łącząc dwie struktury if-else. Ponownie byłoby również możliwe wykonanie więcej niż jednej instrukcji na przypadek, grupując je w bloki zamknięte w nawiasach klamrowych: `{}`.

## Instrukcje iteracyjne (pętle) - While

Pętle powtarzają instrukcję określoną liczbę razy lub gdy warunek jest spełniony. Są one wprowadzane za pomocą słów kluczowych while, do i for.

### Pętla While

Najprostszym rodzajem pętli jest pętla while. Jej składnia to:

```cpp
while (wyrażenie) zróbCoś
```

Pętla while po prostu powtarza instrukcję, podczas gdy wyrażenie jest prawdziwe. Jeśli po wykonaniu instrukcji wyrażenie nie jest już prawdziwe, pętla kończy się, a program kontynuuje działanie zaraz po pętli. Na przykład, spójrzmy na odliczanie za pomocą pętli while:

```cpp
#include <iostream>
using namespace std;

int main ()
{
  int n = 10;

  while (n>0) {
    cout << n << ", ";
    --n;
  }

  cout << "Odlot!\n";
}
```

Pierwsza instrukcja w kodzie main `n` wynosi 10. Jest to pierwsza liczba w odliczaniu. Następnie rozpoczyna się pętla while: jeśli ta wartość spełnia warunek n> 0 (że n jest większy od zera), wówczas wykonywany jest blok następujący po warunku i powtarzany tak długo, jak długo warunek (n> 0) pozostaje prawdziwe.

W przypadku pętli while należy wziąć pod uwagę to, że pętla powinna się w pewnym momencie zakończyć, a zatem instrukcja w jakiś sposób zmieni wartości sprawdzone w warunku, aby w pewnym momencie zmusić ją do fałszowania. W przeciwnym razie pętla będzie kontynuować pętlę na zawsze. W tym przypadku pętla zawiera `--n`, co zmniejsza wartość zmiennej, która jest oceniana w warunku (n) o jeden - ostatecznie spowoduje to, że warunek (n> 0) będzie fałszywy po określonej liczbie iteracji pętli . Mówiąc dokładniej, po 10 iteracjach n staje się 0, co powoduje, że warunek przestaje być prawdziwy, i kończy pętlę while.

### Pętla Do - While

Bardzo podobna pętla to pętla do-while, której składnia to:

```cpp
do zróbCoś while (wyrażenie)
```

Zachowuje się jak pętla while, z tym wyjątkiem, że warunek jest oceniany po wykonaniu instrukcji zamiast wcześniej, gwarantując co najmniej jedno wykonanie instrukcji, nawet jeśli warunek nigdy nie jest spełniony. Na przykład następujący program przykładowy wyświetla dowolny tekst wprowadzany przez użytkownika, dopóki użytkownik nie wpisze "cześć":

```cpp
#include <iostream>
#include <string>
using namespace std;

int main ()
{
  string str;
  do {
    cout << "Wpisz tekst: ";
    getline (cin, str);
    cout << "Wpisałeś: " << str << '\n';
  } while (str != "cześć");
}
```

Pętla do-while jest zwykle lepsza niż pętla while, gdy instrukcja musi zostać wykonana co najmniej raz, na przykład gdy warunek sprawdzany do końca pętli jest określany w samej instrukcji pętli. W poprzednim przykładzie dane wprowadzone przez użytkownika w bloku określają, czy pętla się kończy. I tak, nawet jeśli użytkownik chce zakończyć pętlę tak szybko, jak to możliwe, żegnając się, blok w pętli musi zostać wykonany przynajmniej raz, aby poprosić o wprowadzenie danych, a warunek można w rzeczywistości określić dopiero po tym jak jest wykonywany.

### Pętla For

Pętla for ma za zadanie iterować wiele razy. Jego składnia to:

```cpp
for (inicjalizacja; warunek; zwiększenie) zróbCoś;
```

Podobnie jak pętla while, ta pętla powtarza instrukcję, gdy warunek jest spełniony. Ale dodatkowo, pętla for zapewnia określone lokalizacje, które zawierają inicjalizację i wyrażenie zwiększające, wykonywane przed pierwszą pętlą i odpowiednio po każdej iteracji. Dlatego szczególnie użyteczne jest użycie przeciwnych zmiennych jako warunku.

Oto przykład odliczania za pomocą pętli for:

```cpp
#include <iostream>
using namespace std;

int main ()
{
  for (int n=10; n>0; n--) {
    cout << n << ", ";
  }
  cout << "Odlot!\n";
}
```

Zwróć uwagę na kilka rzeczy:

- W inicjalizacji mówimy że zmienna `n` zacznie z wartością 10,
- Funkcja wykonuje się do czasu gdy warunek `n > 10` przestanie być spełniony,
- Z każdym krokiem `n` jest zmniejszane o `1`.

Trzy pola w pętli for są opcjonalne. Można je pozostawić puste, ale we wszystkich przypadkach wymagane są między nimi znaki średnika. Na przykład, dla `(; n <10;)` jest pętlą bez inicjalizacji lub zwiększenia (równoważną pętli while); a dla `(; n <10; ++n)` jest pętlą ze wzrostem, ale bez inicjalizacji (być może dlatego, że zmienna została już zainicjowana przed pętlą). Pętla bez warunku jest równoważna pętli z prawdą jako warunkiem (tj. Pętlą nieskończoną).

Ponieważ każde z pól jest wykonywane w określonym czasie w cyklu życia pętli, użyteczne może być wykonanie więcej niż jednego wyrażenia jako dowolnej inicjalizacji, warunku lub instrukcji. Niestety nie są to instrukcje, ale proste wyrażenia, dlatego nie można ich zastąpić blokiem. Jako wyrażenia mogą jednak korzystać z operatora przecinka (`,`): Ten operator jest separatorem wyrażeń i może oddzielać wiele wyrażeń tam, gdzie ogólnie oczekuje się tylko jednego. Na przykład przy jego użyciu pętla for mogłaby obsługiwać dwie zmienne licznika, inicjując i zwiększając oba:

```cpp
for ( n=0, i=100 ; n!=i ; ++n, --i )
{
   // Dalsze działania funkcji
}
```

### Pętla for oparta na zakresie

Pętla for ma inną składnię, która jest używana wyłącznie z zakresami:

```cpp
for ( deklaracja : zakres ) zróbCoś;
```

Ten rodzaj pętli for iteruje wszystkie elementy w zakresie, w których deklaracja deklaruje jakąś zmienną zdolną do przyjęcia wartości elementu z tego zakresu. Zakresy to sekwencje elementów, w tym tablice, kontenery i każdy inny typ obsługujący funkcje rozpoczynania i kończenia; Większość tych typów nie została jeszcze wprowadzona w tym kursie, ale znamy już co najmniej jeden rodzaj zakresu: ciągi znaków, które są sekwencjami znaków.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main ()
{
  string str {"Cześć!"};
  for (char c : str)
  {
    cout << "[" << c << "]";
  }
  cout << '\n';
}
```

Zwróć uwagę, że to, co poprzedza dwukropek (:) w pętli for, to deklaracja zmiennej char (elementy łańcucha są typu char). Następnie używamy tej zmiennej c w bloku instrukcji do reprezentowania wartości każdego z elementów w zakresie.

## Instrukcje break oraz continue

Instrukcje skoków umożliwiają zmianę przepływu programu poprzez wykonywanie skoków do określonych lokalizacji.

### Break

`break` pozostawia pętlę, nawet jeśli warunek jej końca nie jest spełniony. Można go użyć do zakończenia nieskończonej pętli lub do wymuszenia jej zakończenia przed jej naturalnym końcem. Na przykład zatrzymajmy odliczanie przed jego naturalnym końcem:

```cpp
#include <iostream>
using namespace std;

int main ()
{
  for (int n=10; n>0; n--)
  {
    cout << n << ", ";
    if (n==3)
    {
      cout << "Odliczanie zakończone";
      break;
    }
  }
}
```

### Continue

Instrukcja `continue` powoduje, że program pomija resztę pętli w bieżącej iteracji, tak jakby osiągnięto koniec bloku instrukcji, powodując, że przeskakuje ona na początek następnej iteracji. Na przykład pomińmy numer 5 w naszym odliczaniu:

```cpp
#include <iostream>
using namespace std;

int main ()
{
  for (int n=10; n>0; n--) {
    if (n==5) continue;
    cout << n << ", ";
  }
  cout << "Odlot!\n";
}
```

## Instrukcja Switch

Składnia instrukcji `switch` jest nieco osobliwa. Jej celem jest sprawdzenie wartości wśród wielu możliwych stałych wyrażeń. Jest to coś podobnego do łączenia instrukcji if-else, ale ogranicza się do wyrażeń stałych.

```cpp
switch (wyrażenie)
{
  case stała1:
     zróbCoś;
     break;
  case stała2:
     zróbCośInnego;
     break;
  .
  .
  .
  default:
     zróbCośCałkiemInnego;
}
```

Działa w następujący sposób: przełącznik ocenia wyrażenie i sprawdza, czy jest ono równoważne stałej1; jeśli tak, wykonuje `zróbCoś`, dopóki nie znajdzie instrukcji break. Gdy znajdzie tę instrukcję break, program przeskakuje na koniec całej instrukcji switch (nawias zamykający).

Jeśli wyrażenie nie było równe stałej1, jest ono następnie sprawdzane względem stałej2. Jeśli jest równy, wykonuje `zróbCośInnego` aż do znalezienia przerwy, kiedy przeskoczy na koniec przełącznika.

Wreszcie, jeśli wartość wyrażenia nie pasuje do żadnej z wcześniej określonych stałych (może być ich dowolna liczba), program wykonuje instrukcje zawarte po domyślnej etykiecie, jeśli istnieje (ponieważ jest opcjonalna).