Дано целое число k, 
определить каким днем недели является k-е число января невисокосного года, 
в котором 1 января приходится на заданный заранее день недели


Проверка високосности года:
Год високосный, если он кратен 4 И НЕ кратен 100
ИЛИ год кратен 400
Вычисление дня недели:
Используется формула для определения дня недели 1 января
Для заданной даты вычисляется смещение от 1 января
Определение дня недели через оператор switch
<img width="2644" height="3448" alt="image" src="https://github.com/user-attachments/assets/53430a08-6f0e-4513-bbd9-a4f4649ddba1" />

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <locale.h>
int main() {
    setlocale(LC_ALL, "Rus");
    int year;
    int k; // день января (например, 31)
    printf("Введите год: ");
    scanf("%d", &year);
    printf("Введите число января: ");
    scanf("%d", &k);
    // Проверка на високосный год
    if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
        printf("Год %d является високосным!\n", year);
        return 1;
    }
    printf("Год %d - невисокосный\n", year);
    // Формула для определения дня недели 1 января
    int day_of_week_jan1 = (year + (year - 1) / 4 - (year - 1) / 100 + (year - 1) / 400) % 7;
    // День недели для k-го января
    int target_day = (day_of_week_jan1 + k - 1) % 7;
    printf("%d января %d года - ", k, year);
    switch (target_day) {
    case 0:
        printf("воскресенье\n");
        break;
    case 1:
        printf("понедельник\n");
        break;
    case 2:
        printf("вторник\n");
        break;
    case 3:
        printf("среда\n");
        break;
    case 4:
        printf("четверг\n");
        break;
    case 5:
        printf("пятница\n");
        break;
    case 6:
        printf("суббота\n");
        break;
    default:
        printf("ошибка вычисления\n");
    }
    return 0;
}



