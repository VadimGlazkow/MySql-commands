# **Шаблон `C`**
```c++
#include <stdio.h> // позволяет использовать `printf` и `scanf`

int main() {
    return 0;
}
```

# **Шаблон `C++`**
```C++
#include <iostream> // позволяет использовать `cout` и `cin`

using namespace std; // позволяет не писать вначале `std::`

int main() {
    return 0;
}
```

# **Подключить кириллицу `C`**
```c++
#define _CRT_SECURE_NO_WARNINGS
...
#include <locale.h>

int main() {
    setlocale(LC_ALL, "Rus");
    ...
    return 0;
}
```

# **Подключить кириллицу `C++`**
```c++
...
#include <clocale>

using namespace std;

int main() {
    setlocale(LC_ALL, "Rus");
    ...
    return 0;
}
```


# Типы данных
### **`C/C++`**:
* `int` - `%d`, `%i`;
* `float` - `%f`;
* `double` - `%lf`, `%le`;
* `char` - `%c`;
* `void`;
### **C++**
* `bool`;

# **Ввод/вывод `С`**
* `printf`, `scanf`:
    ```c++
    printf("Частное %d и %d равна %d\n", b, a, b % a);
    scanf("%d %d %d", &a, &b, &c);
    ```
# **Ввод/вывод `С++`**

* `cout`, `cin`:
    ```c++
    cout << "Text" << x;
    cin >> x >> y;
    ```

# **Тернарный оператор `C`/`C++`**
* `max = ((a > b) ? a : b)`;

# **Логические операторы `C`/`C++`**
* `&&` - `И`;
* `||` - `ИЛИ`;
* `!` - `НЕ`;

# `switch` - `C`/`C++`;
```С++
switch (a) {
case 5:
	printf("Будний день\n");
	break;
case 6:
	printf("Суббота\n");
	break;
case 7:
	printf("Воскресенье\n");
	break;
default:
	printf("ОШИБКА!");
}
```

# `do while` - `C`/`C++`
```c++
...
int n = 0;
do {
	printf("%d", n);
	n += 1;
} while (n != 1);
...
```

# **Подключить мат. библиотеку**
* `#include <math.h>` - для `C`;
* `#include <cmath>` - для `C++`;

# **Массивы `C`/`C++`**
* `int arr[100]` - создать массив;
* `int arr[] = { 2, 3, 5, 7 }` - создать массив длины 4 из элементов `[2, 3, 5, 7]`;
* `int arr1[10] = { 2, 3, 4 }` - создать массив длины 10, где первые три элемента `2, 3, 4`;

# **Двумерные массивы `C`/`C++`**
* `int matrix[N][N]` - создать матрицу `N` на `N`;

# **Вывести рандомное число**
```c++
...
#include <cstdlib>
#include <ctime>
...
int main() {
    srand(time(NULL));
    cout << rand();
    return 0;
}
```

# **Форматирование текста**
```c++
...
#include <iomanip>

using namespace std;

int main() {
	int x = 4;
	cout << setw(2) << x; // на число выделяет 2 символа, лишние справа забивает пробелами
}
```







