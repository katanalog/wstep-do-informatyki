# Kompilatory oraz IDE

Niezbędnymi narzędziami do wykonania kursu są komputer i łańcuch narzędzi zdolnych do kompilacji kodu C ++ i zbudowania programów do działania na nim. C++ to język, który ewoluował przez lata, a ten kurs wyjaśniają wiele funkcji dodanych ostatnio do tego języka. Dlatego, aby właściwie postępować zgodnie ze skryptem, potrzebny jest najnowszy kompilator. Powinien obsługiwać (nawet tylko częściowo) funkcje wprowadzone przez standard 2011.

Wielu dostawców kompilatorów obsługuje nowe funkcje w różnym stopniu. Na dole znajdują się kompilatory, o których wiadomo, że obsługują potrzebne funkcje. Niektóre z nich są bezpłatne!

- [Code::Blocks](http://www.codeblocks.org/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Eclipse](https://www.eclipse.org/cdt/)
- [Netbeans](https://netbeans.org/downloads/8.0.1/)
- [Sublime Text](https://www.sublimetext.com/)
- [Dev-C++](https://www.bloodshed.net/devcpp.html)
- [CLion](https://www.jetbrains.com/clion/)

## Co to jest kompilator?

Czerpiąc z definicji podanej przez Wikipedię:

> Kompilator – program służący do automatycznego tłumaczenia kodu napisanego w jednym języku (języku źródłowym) na równoważny kod w innym języku (języku wynikowym). Proces ten nazywany jest kompilacją. W informatyce kompilatorem nazywa się najczęściej program do tłumaczenia kodu źródłowego w języku programowania na język maszynowy. Niektóre z nich tłumaczą najpierw do języka asemblera, a ten na język maszynowy jest tłumaczony przez asembler.<br/><br/>Różnica pomiędzy kompilatorem a asemblerem polega na tym, iż każde polecenie języka programowania może zostać rozbite na wiele podpoleceń języka maszynowego (przy czym nowoczesne asemblery również posiadają składnię umożliwiającą zapis wielu poleceń maszynowych jako jednego polecenia kodu źródłowego oraz opcje optymalizacji kodu). Kompilatory mogą mieć możliwość automatycznej alokacji pamięci dla zmiennych, implementowania struktur kontrolnych lub procedur wejścia-wyjścia. <br/><br/> Stosowanie kompilatorów ułatwia programowanie (programista nie musi znać języka maszynowego) i pozwala na większą przenośność kodu pomiędzy platformami. 

Komputery rozumieją tylko jeden język, który składa się z zestawów instrukcji złożonych z zer i jedynek. Ten język komputerowy jest odpowiednio nazywany językiem maszynowym. Pojedyncza instrukcja dla komputera może wyglądać następująco:

```
00000	10011110
```

Program języka maszynowego określonego komputera, który pozwala użytkownikowi na wprowadzenie dwóch liczb, ich dodanie i wyświetlenie sumy, może zawierać następujące instrukcje kodu maszynowego:

```
00000	10011110
00001	11110100
00010	10011110
00011	11010100
00100	10111111
00101	00000000
```

Jak można sobie wyobrazić, programowanie komputera bezpośrednio w języku maszynowym przy użyciu tylko zer i jedynek jest bardzo żmudne i podatne na błędy. Aby ułatwić programowanie, opracowano języki wysokiego poziomu. Programy wysokiego poziomu ułatwiają również programistom łatwiejsze wzajemne sprawdzanie i rozumienie programów. To część kodu napisana w C ++, która spełnia dokładnie ten sam cel:

```cpp
int a, b, sum;
     
cin >> a;
cin >> b;
             
sum = a + b;
cout << sum << endl;
```

Nawet jeśli tak naprawdę nie rozumiesz powyższego kodu, powinieneś docenić, o ile łatwiej będzie programować w języku C ++ niż w języku maszynowym.

Ponieważ komputer rozumie tylko język maszynowy, a ludzie chcą pisać w językach wysokiego poziomu, języki wysokiego poziomu muszą w pewnym momencie zostać ponownie napisane (przetłumaczone) na język maszynowy. Odbywa się to za pomocą specjalnych programów zwanych kompilatorami, interpreterami lub asemblerami wbudowanymi w różne aplikacje programistyczne.

C++ jest zaprojektowany jako język skompilowany, co oznacza, że ​​jest ogólnie tłumaczony na język maszynowy, który może być zrozumiany bezpośrednio przez system, dzięki czemu wygenerowany program jest bardzo wydajny. Do tego potrzebny jest zestaw narzędzi, zwany łańcuchem narzędzi programistycznych, których rdzeniem jest kompilator i jego linker.

## Aplikacje konsolowe

Programy konsolowe to programy wykorzystujące tekst do komunikowania się z użytkownikiem i środowiskiem, takie jak drukowanie tekstu na ekranie lub odczytywanie danych z klawiatury.

Programy konsolowe są łatwe w obsłudze i generalnie zachowują się identycznie na wszystkich platformach. Są one również łatwe do wdrożenia, a zatem są bardzo przydatne do nauki podstaw języka programowania: Wszystkie przykłady w tych samouczkach dotyczą programów konsolowych.

Sposób kompilacji programów konsoli zależy od konkretnego narzędzia, którego używasz.

Najprostszym sposobem na kompilację programów C ++ dla początkujących jest użycie zintegrowanego środowiska programistycznego (IDE). IDE ogólnie integruje kilka narzędzi programistycznych, w tym edytor tekstu i narzędzia do kompilowania programów bezpośrednio z niego. (zobacz przykłady aplikacji na początku ćwiczenia).

## Witaj świecie!

Najlepszym sposobem nauki języka programowania jest pisanie programów. Zazwyczaj pierwszym programem dla początkujących jest program `Hello World`, który po prostu drukuje „Hello World” na ekranie komputera. Chociaż jest to bardzo proste, zawiera wszystkie podstawowe komponenty, które zawierają programy C++:

```cpp
// Nasz pierwszy program w C++!
#include <iostream>

int main()
{
  std::cout << "Witaj Świecie!";
}
```

### Przeanalizujmy ten program linia po linii:

`// Nasz pierwszy program w C++!`

- Dwa znaki ukośnika wskazują, że reszta wiersza jest komentarzem wstawionym przez programistę, ale nie ma wpływu na zachowanie programu. Programiści używają ich do zamieszczania krótkich wyjaśnień lub spostrzeżeń dotyczących kodu lub programu. W tym przypadku jest to krótki wstępny opis programu.

`#include <iostream>`

- Linie zaczynające się od znaku skrótu (`#`) to dyrektywy odczytywane i interpretowane przez tak zwany preprocesor. Są to specjalne linie interpretowane przed rozpoczęciem kompilacji samego programu. W tym przypadku dyrektywa `#include <iostream>` instruuje preprocesor, aby zawarł sekcję standardowego kodu C++, znaną jako nagłówek iostream, która pozwala na wykonywanie standardowych operacji wejścia i wyjścia, takich jak zapis danych wyjściowych tego programu (Hello World) na ekranie.

`pusta linia`

- Puste linie nie mają wpływu na program. Po prostu poprawiają czytelność kodu.

`int main ()`
- Ten wiersz inicjuje deklarację funkcji. Zasadniczo funkcja jest grupą instrukcji kodowych, którym nadano nazwę: w tym przypadku daje to nazwę „main” następnej grupie instrukcji kodowych. Funkcje zostaną omówione szczegółowo w późniejszym rozdziale, ale zasadniczo ich definicja jest wprowadzana z ciągiem typu (int), nazwy (main) i pary nawiasów (()), opcjonalnie włączając parametry.<br/><br/>Funkcja o nazwie main jest funkcją specjalną we wszystkich programach w C++; jest to funkcja wywoływana podczas uruchamiania programu. Wykonywanie wszystkich programów w C ++ rozpoczyna się od funkcji głównej, niezależnie od tego, gdzie funkcja faktycznie znajduje się w kodzie.

`{ oraz }`
- Otwarty nawias klamrowy (`{`) w wierszu 5 wskazuje początek definicji funkcji głównej, a nawias zamykający (`}`) w wierszu 7 wskazuje jego koniec. Wszystko pomiędzy tymi nawiasami klamrowymi jest ciałem funkcji, która określa, co dzieje się, gdy wywoływana jest funkcja main. Wszystkie funkcje używają nawiasów klamrowych do wskazania początku i końca ich definicji.

`std :: cout << „Witaj Świecie!”;`
- Ta linia jest instrukcją C++. Instrukcja jest wyrażeniem, które może rzeczywiście wywołać pewien efekt. Jest to główna część programu, określające jego faktyczne zachowanie. Instrukcje są wykonywane w tej samej kolejności, w jakiej pojawiają się w ciele funkcji.<br/><br/>Ta instrukcja składa się z trzech części: po pierwsze, std :: cout, która identyfikuje standardowe urządzenie wyjściowe znaków (zwykle jest to ekran komputera). Po drugie, operator wstawiania (`<<`), który wskazuje, że to, co następuje, jest wstawiane do `std::cout`. Wreszcie zdanie w cudzysłowie („Witaj świecie!”) To treść wstawiona do standardowego wyjścia.<br/><br/>Zauważ, że instrukcja kończy się średnikiem (`;`). Ten znak oznacza koniec wyrażenia, podobnie jak kropka kończy zdanie w języku angielskim. Wszystkie instrukcje C++ muszą kończyć się średnikiem. Jednym z najczęstszych błędów składniowych w C++ jest zapomnienie zakończenia instrukcji średnikiem.

Program został podzielony na różne wiersze i odpowiednio wcięty, aby ułatwić zrozumienie czytającym go ludziom. Ale C ++ nie ma ścisłych zasad dotyczących wcięć ani sposobu dzielenia instrukcji w różnych wierszach. Na przykład zamiast:

```cpp
int main ()
{
  std::cout << "Witaj Świecie!";
}
```

Moglibyśmy napisać:

```cpp
int main () { std::cout << "Witaj Świecie!"; }
```

W C++ separacja między instrukcjami jest określona końcowym średnikiem (`;`), przy czym separacja na różne linie nie ma żadnego znaczenia w tym celu. Wiele instrukcji można zapisać w jednym wierszu lub każda instrukcja może znajdować się w osobnym wierszu. Podział kodu na różne wiersze służy jedynie uczynieniu go bardziej czytelnym i schematycznym dla ludzi, którzy mogą go czytać, ale nie ma wpływu na faktyczne zachowanie programu.

## Komentarze

Jak wspomniano powyżej, komentarze nie wpływają na działanie programu; zapewniają one jednak ważne narzędzie do dokumentowania bezpośrednio w kodzie źródłowym, co program robi i jak działa.

C++ obsługuje dwa sposoby komentowania kodu:

```cpp
// Komentarz liniowy
/* Komentarz blokowy */ 
```

Pierwszy z nich, znany jako komentarz do linii, odrzuca wszystko, od miejsca, gdzie para znaków ukośnika (`//`) znajduje się do końca tego samego wiersza. Drugi, znany jako komentarz blokowy, odrzuca wszystko między znakami `/*` a pierwszym pojawieniem się znaków `*/`, z możliwością ukrycia wielu wierszy kodu.

Jeśli komentarze są zawarte w kodzie źródłowym programu bez użycia kombinacji znaków komentarza `//`, `/*` lub `*/`, kompilator przyjmuje je tak, jakby były wyrażeniami C++, najprawdopodobniej powodując niepowodzenie kompilacji z jednym lub kilkoma, komunikaty o błędach.

## Namespace `std`

Jeśli widziałeś wcześniej kod C++, być może widziałeś użycie `cout` zamiast `std::cout`. Oba nazywają ten sam obiekt: pierwszy używa swojej niekwalifikowanej nazwy (`cout`), podczas gdy drugi kwalifikuje go bezpośrednio w przestrzeni nazw `std` (jako `std::cout`).

`cout` jest częścią standardowej biblioteki, a wszystkie elementy w standardowej bibliotece C++ są zadeklarowane w ramach tak zwanej przestrzeni nazw: przestrzeni nazw `std`.

Aby odwoływać się do elementów w przestrzeni nazw `std`, program powinien albo zakwalifikować każde użycie elementów biblioteki (jak zrobiliśmy to, poprzedzając `cout` znakiem `std::`), albo wprowadzić widoczność jego komponentów. Najbardziej typowym sposobem wprowadzenia widoczności tych komponentów jest użycie deklaracji:

```cpp
using namespace std;
```

Powyższa deklaracja umożliwia dostęp do wszystkich elementów w przestrzeni nazw `std` w niekwalifikowany sposób (bez przedrostka `std::`).

Mając to na uwadze, ostatni przykład można przepisać, aby użyć niekwalifikowanych zastosowań `cout` jako:

```cpp
// Nasz pierwszy program w C++!
#include <iostream>
using namespace std;

int main()
{
  cout << "Witaj Świecie!";
}
```

# Zadania

1. Za pomocą wybranej aplikacji (IDE) dostępnej na komputerach w labolatorium stwórz swoją pierwszą aplikację konsolową w C++.
2. W aplikacji umieść odwołanie do przestrzeni nazw `std` oraz pamiętaj by zawrzeć dyrektywę `iostream`.
3. Korzystając z polecenia `cout` wyświetl na konsoli następujące dane:
   - Swoje imię i nazwisko,
   - Numer indeksu,
   - Wiek,
   - Dzisiejszą datę.


Po wykonaniu zadania wejdź na [podaną w linku stronę](http://www.cplusplus.com/info/description/) i uzupełnij swoją wiedzę o języku programowania C++ i jego możliwosciach.