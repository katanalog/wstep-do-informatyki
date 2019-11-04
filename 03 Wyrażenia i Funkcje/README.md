# Wyrażenia i Funkcje

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

