# Pointer

Ein Pointer ist ein Wert welcher auf einen anderen Wert zeigt.
Eine Variable vom Datentyp ***Pointer auf `X`*** beinhaltet eine Adresse an dessen Ort ein Wert mit dem Datentyp `X` liegen soll.

> Dass dort wirklich ein Wert vom Datentyp `X` liegt ist nicht immer garantiert, dafür ist der Programmierer selbst verantwortlich.

Die Syntax um eine solche Variable zu erstellen ist wie folgt.

```c++
X* test;
```

`test` zeigt auf garbage, deswegen sollten wir sie initialisieren.


## Das keyword `nullptr` (seit C++11)

Der de facto standard Weg einen Pointer auf nichts zeigen zu lassen, ist ihn auf `nullptr` zu setzen.

```c++
X* test = nullptr;
```

Das ist praktisch das selbe wie dem Pointer die Adresse 0 zuzuweisen.

> `nullptr` hat den Vorteil, dass es für den Programmierer, aber auch für den Compiler verständlicher ist, was gemeint ist.

Da ein Pointer im Endeffekt nur eine Zahl ist, können wir ihn wie einen bool behandeln.

```c++
X* test = nullptr;

if (test)
	// Pointer beinhaltet eine Adresse

if (!test)
	// Pointer ist ein nullptr
```

> 0 == false, !0 == true


## Einem Pointer eine Adresse zuweisen

Um einem Pointer eine Adresse zuweisen zu können, brauchen wir in erster Linie eine Adresse. Diese können wir durch den `&` Operator erlangen.

```c++
int x = 12; // <─────────────┐ pointer_auf_x zeigt auf die Adresse von x
int* pointer_auf_x = &x; // ─┘
```

Man kann `&x` wie ***Adresse von `x`*** lesen.

## Auf den Wert zugreifen

Um auf den Wert zuzugreifen, der bei jener Adresse liegt, die wir in `pointer_auf_x` gespeichert haben, können wir “dereferenzieren” mit den `*` Operator.

```c++
int x = 12; // <─────────────┐ pointer_auf_x zeigt auf Adresse von x
int* pointer_auf_x = &x; // ─┘

std::cout << *pointer_auf_x << std::endl;
// Output: 12
```

`*pointer_auf_x` ist wie ***Wert bei `pointer_auf_x`*** zu lesen.

Genau mit der selben Syntax können wir auch schreiben.

```c++
int x = 12; // <─────────────┐ pointer_auf_x zeigt auf die Adresse 
int* pointer_auf_x = &x; // ─┘

*pointer_auf_x = 14; // Wert bei `pointer_auf_x` gleich 14

std::cout << *pointer_auf_x << std::endl;
// Output: 14
```
