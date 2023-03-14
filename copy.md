# Wann werden Werte kopiert und wann nicht?

Grundsätzlich werden beim aufrufen von Funktionen alle werte immer kopiert.

```c++
void set_to_0(int a, int b) //──┐
{                           //  │
  // funktioniert nicht         │
    a = 0;                  //  │
    b = 0;                  //  │
}                           //  │ Sind unterschiedliche Variablen
                            //  │
                            //  │
// ...                          │
                            //  │
int a = 10;//───────────────────┤
int b = 10;//───────────────────┘

set_to_0(a, b);

std::cout << a << ", " << b << std::endl;
// Output: 10, 10
```

Auch wenn sie die selben Namen haben, wurden praktisch neue Variablen erstellt welche nur für diese Funktion leben.

Das selbe gilt für Klassen, Structs und alle anderen Datentypen. In dessen Fällen werden alle Felder des Datentyps kopiert.

Was also, wenn eine funktion Daten bearbeiten soll?


## Pointer um Werte zu referenzieren

Wir können unter anderem Pointer verwenden um dieses Problem zu umgehen.

```c++
void set_to_0(int* a, int* b) //──┐
{                             //  │
                              //  │
    *a = 0;                   //  │
    *b = 0;                   //  │
}                             //  │ Unterschiedliche Variablen,
                              //  │ zeigen auf die unteren
                              //  │
// ...                            │
                              //  │
int a = 10;//<────────────────────┤
int b = 10;//<────────────────────┘

set_to_0(&a, &b);

std::cout << a << ", " << b << std::endl;
// Output: 0, 0
```
