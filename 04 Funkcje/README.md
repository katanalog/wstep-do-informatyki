# Funkcje

Funkcje pozwalają na uporządkowanie programów w segmenty kodu w celu wykonania poszczególnych zadań.

W C++ funkcja to grupa instrukcji, której nadano nazwę i którą można wywołać z dowolnego miejsca programu. Najczęstszą składnią definiującą funkcję jest:

```cpp
typ nazwa( parameter1, parameter2, ...)
{ 
    // Logika funkcji
}
```

Gdzie:
- typ to typ wartości zwracanej przez funkcję.
- nazwa to identyfikator, za pomocą którego można wywoływać funkcję.
- parametry (tyle, ile potrzeba): każdy parametr składa się z typu, po którym następuje identyfikator, przy czym każdy parametr jest oddzielony od następnego przecinkiem. Każdy parametr wygląda bardzo podobnie do deklaracji zmiennej regularnej (na przykład: `int x`) i faktycznie działa w obrębie funkcji jako zmienna lokalna dla funkcji. Celem parametrów jest umożliwienie przekazywania argumentów do funkcji z miejsca, z którego jest wywoływana.
- instrukcje są ciałem funkcji. Jest to blok instrukcji otoczony nawiasami klamrowymi `{}`, które określają, co faktycznie robi funkcja.

Przykładowo:

```cpp
#include <iostream>
using namespace std;

int addition (int a, int b)
{
  int r;
  r=a+b;
  return r;
}

int main ()
{
  int z;
  z = addition (5,3);
  cout << "The result is " << z;
}
```

Ten program jest podzielony na dwie funkcje: `addition` i `main`. Pamiętaj, że bez względu na kolejność, w jakiej są zdefiniowane, program C ++ zawsze zaczyna się od wywołania `main`. W rzeczywistości `main` jest jedyną funkcją wywoływaną automatycznie, a kod w dowolnej innej funkcji jest wykonywany tylko wtedy, gdy jej funkcja jest wywoływana z `main` (bezpośrednio lub pośrednio).

Aby zwrócić wartość w funkcji **trzeba** wykorzystać słowo kluczowe `return`.

## Funkcja bez zwracania typu

Czasami nie potrzebujemy by nasza funkcja coś zwracała (np. funkcja do wypisywania danych). W tym przypadku musimy zastosować typ `void` (brak typu).

Przykładowo:

```cpp
void printmessage (void)
{
  cout << "I'm a function!";
}
```

## Domyślne wartości funkcji

Czasami, gdy funkcja będzie wykonywana często z tymi samymi parametrami, zaleca się stworzenie tzw. domyślnych parametrów. Robi się to w następujący sposób:

```cpp
int divide (int a, int b=2)
{
  int r;
  r=a/b;
  return (r);
}
```

W tym przypadku parametr `b` domyślnie przyjmie wartość 2, więc funkcja moze być wywołana następująco:

```cpp
divide(10)  // Nie podajemy parametru b, funkcja zwróci 5
```

# Ćwiczenia

By zaznajomić się z funkcjami, przekształć kod z poprzednich zajęć (*03 Instrukcje warunkowe oraz pętle*) na funkcje. Zamiast pobierać dane za pomocą `cin`, stwórz funkcję w której pobierane wartości będą pobierane za pomocą parametrów jak w przykładach powyzej. Wszystkie funkcje umieść w jednym pliku. A na końcu je wywołaj.