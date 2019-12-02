# Przeciążanie funkcji

W C++ dwie różne funkcje mogą mieć tę samą nazwę, jeśli ich parametry są różne; albo dlatego, że mają inną liczbę parametrów, albo ponieważ dowolny z ich parametrów jest innego typu. Na przykład:

```cpp
// overloading functions
#include <iostream>
using namespace std;

int operate (int a, int b)
{
  return (a*b);
}

double operate (double a, double b)
{
  return (a/b);
}

int main ()
{
  int x=5,y=2;
  double n=5.0,m=2.0;
  cout << operate (x,y) << '\n';
  cout << operate (n,m) << '\n';
  return 0;
}
```

W tym przykładzie są dwie funkcje o nazwie `operate`, ale jedna z nich ma dwa parametry typu `int`, a druga ma je typu `double`. Kompilator wie, który należy wywołać w każdym przypadku, badając typy przekazywane jako argumenty podczas wywoływania funkcji. Jeśli jest wywoływana z dwoma argumentami `int`, wywołuje funkcję, która ma dwa parametry `int`, a jeśli jest wywoływana z dwoma `double`, wywołuje tę z dwoma `double`.

W tym przykładzie obie funkcje zachowują się zupełnie inaczej, wersja `int` zwielokrotnia swoje argumenty, podczas gdy wersja `double` dzieli je. To na ogół nie jest dobry pomysł. Oczekuje się, że dwie funkcje o tej samej nazwie będą miały co najmniej podobne zachowanie, ale ten przykład pokazuje, że jest całkowicie możliwe, że nie będą. Dwie przeciążone funkcje (tj. Dwie funkcje o tej samej nazwie) mają zupełnie różne definicje; są to, dla wszystkich celów, różne funkcje, które mają tylko tę samą nazwę.

Zauważ, że funkcja nie może być przeciążona tylko przez typ zwracany. Co najmniej jeden z jego parametrów musi mieć inny typ.

```cpp
// overloaded functions
#include <iostream>
using namespace std;

int sum (int a, int b)
{
  return a+b;
}

double sum (double a, double b)
{
  return a+b;
}

int main ()
{
  cout << sum (10,20) << '\n';
  cout << sum (1.0,1.5) << '\n';
  return 0;
}
```

Tutaj `sum` jest przeciążona różnymi typami parametrów, ale dokładnie tym samym ciałem funkcji.

Funkcja `sum` może być przeciążona dla wielu typów i może mieć sens, aby wszystkie miały tę samą treść. W takich przypadkach C++ ma możliwość definiowania funkcji o typach ogólnych, znanych jako szablony funkcji. Definiowanie szablonu funkcji odbywa się zgodnie z tą samą składnią, co zwykła funkcja, z tym wyjątkiem, że poprzedza ją słowo kluczowe szablon i szereg parametrów szablonu zawartych w nawiasach kątowych `<>`:

```
szablon <template-parameters> deklaracja funkcji
```

Parametry szablonu to szereg parametrów oddzielonych przecinkami. Parametry te mogą być ogólnymi typami szablonów, podając słowo kluczowe `class` lub `typename`, po którym następuje identyfikator. Tego identyfikatora można następnie użyć w deklaracji funkcji tak, jakby był to typ regularny. Na przykład ogólną funkcję sumy można zdefiniować jako:

```cpp
template <class SomeType>
SomeType sum (SomeType a, SomeType b)
{
  return a+b;
}
```

# Ćwiczenia

1. Stwórz przeciązone funkcje, które przyjmą `int`, `double` lub `float` i wypiszą jakiego typu zmienną podaliśmy.
2. Stwórz funkcje, która w zalezności od parametrów, przywita nas bądz wypisze nasz wiek.
3. Stwórz funkcję, która w przypadku `string` zwróci połączony ciąg, a w przypadku `int` doda dwie liczby.