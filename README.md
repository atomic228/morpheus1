# morpheus1
553503

Михалев Антон Андреевич

Игровая программа "Tic tac toe".

В игры вам предстоит играть крестиками либо ноликами.Каждый из них за один ход может поставить один символ на незанятую грань одной из клеток.

//В будущем информация будет дополнена

#include <iostream> 
#include <conio.h> 
#include <random> 
#include <time.h> 

using namespace std; 
char name1[30]; 
char name2[30]; 
char table[3][3]; 
bool step; 

void instruction() 
{ 
cout « "\t\t Крестики-нолики \n\n"; 
cout « " Правила:\n"; 
cout « " Играю два игрока на поле 3х3\n"; 
cout « " Побеждает тот кто составит выйграшную комбинацию\n"; 
cout « " Вид поля\n"; 
int l = 0; 

for (int i = 0; i < 3; i++) 
{ 
for (int j = 0; j < 3; j++) 
{ 
cout « "| " « l + 1 « ' '; 
table[i][j] = char(49 + l); 
l++; 
} 
cout « '|'; 
cout « endl; 
} 
cout « " \n Для ходя нажмите цифру яцейки поля \n"; 
cout « " Для начала игры нажмите клавишу: "; 
_getch(); 
} 
bool input() 
{ 
for (int i = 0; i < 3; i++) 
{ 
for (int j = 0; j < 3; j++) 
{ 
cout « "| " « table[i][j] « ' '; 
} 
cout « '|'; 
cout « endl; 
} 
cout « endl; 
if (step) 
cout « " Ходит " « name1 « " : "; 
else 
cout « " Ходит " « name2 « " : "; 
int n; 
cin » n; 
if (n < 1 || n > 9) 
return false; 
int i, j; 

if (n % 3 == 0) 
{ 
i = n / 3 - 1; 
j = 2; 
} 
else 
{ 
j = n % 3 - 1; 
i = n / 3; 
} 
if (table[i][j] == 'O' || table[i][j] == 'X') 
return false; 
if (step) 
{ 
table[i][j] = 'X'; 
step = false; 
} 
else 
{ 
table[i][j] = 'O'; 
step = true; 
} 
return true; 

} 
bool win() 
{ 
for (int i = 0; i < 3; i++) 
if ((table[i][0] == table[i][1]) && (table[i][0] == table[i][2])) 
return false; 

else 
if ((table[0][i] == table[1][i]) && (table[0][i] == table[2][i])) 
return false; 
else 
if ((table[0][0] == table[1][1]) && (table[0][0] == table[2][2]) && (table[0][2] == table[1][1]) && (table[0][2] == table[2][0])) 
return true; 
return false; 
} 

int main() 
{ 
SetConsoleCP(1251); 
SetConsoleOutputCP(1251); 
instruction(); 
system("cls"); 

cout « " Введите имя 1 игрока: "; 
cin.getline(name1, 30); 
cout « " Введите имя 2 игрока: "; 
cin.getline(name2, 30); 

srand(time(NULL)); 
if (rand() & 1) 
step = true; 
else step = false; 

int draw = 0; 

while (!win()) 
{ 
if (draw == 9) break; 
system("cls"); 
if (!input()) 
{ 
cout « " Вы ввели неверные данные! Повторите!"; 
_getch(); 
} 
draw++ 
} 
system("cls"); 

if ((draw == 9) && win) cout « "Ничья\n" 
else 
if (step) 
cout « " Победил! " « name2 « endl; 
else 
cout « " Победил! " « name1 « endl; 
_getch(); 
}
