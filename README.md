# Projekt z Technik Pogramowania
Jest to *czwarty etap* realizacji zadania projektowego z Technik programowania
## Szyfrowanie
Jest to symulacja do typowego logowania. Program polega na szyfrowaniu podanego przez użytkownika hasła oraz na sprawdzeniu, czy powtórnie podane hasło jest prawidłowe. Sposób szyfrowania jest bardzo zbliżony do [szyfru Cezara](https://pl.wikipedia.org/wiki/Szyfr_Cezara).
## Spis treści
1. [Wprowadzenie(cel projektu)](#Wprowadzenie)
2. [Technologie](#Technologie)
3. [Uruchomienie](#Uruchomienie)
4. [Przykład użycia](#Przykład-użycia)
5. [Status projektu](#Status-projektu)
## Wprowadzenie
Celem projektu jest zapoznanie z technikami programowania; nabycie umiejętności czytelnego i niezawodnego programowania; poznanie zasad programowania strukturalnego i obiektowego oraz narzędzi wspomagających programowanie

Cel jest osiągany za pomocą programu, który szyfrufie podane przez użytkownika hasło.

## Technologie
Projekt jest wykonany w języku programowania C++, z wykorzystaniem standardowej bibloitek iostream oraz string.

**Podział na moduły**

<img width="1462" alt="moduły" src="https://user-images.githubusercontent.com/106164543/172897243-c9cc3be4-4740-4bb9-a8c2-d828d11f8ec7.png">

## Uruchomienie
Żeby uruchomić projekt wystarczy skopiować podany niżej kod, skompilować i uruchomić go w zintegrowanym środowisku programistycznym np.[Visual Studio](https://visualstudio.microsoft.com/pl/downloads/).
``` cpp
/********************************************************
 * /*Nazwa: Projekt # 1 - Szyfrowanie
|
| Autor: Daria Aleksandrova
| Język: C++

| Termin: 15.04.2022-12.06.2022
|
|
| Opis: Jest to symulacja do typowego logowania. Program polega na szyfrowaniu podanego przez użytkownika hasła oraz 
|  na sprawdzeniu czy powtórnie podane hasło jest prawdziwe. Po raz pierwszy prosimy użytkownika o wprowadzeniu 8 cyfrowego hasła, 
|  po raz drugi występujemy z komunikatem "Powtórz hasło".
|
| Dane wejściowe: 8 cyfrowy ciąg liczb, podany w jednym wierszu z klawiatury.
|
| Dane wyjściowe: Moliwe są kilka wariantów wyświetlanej w jednym wierszu odpowiedzi:
|  "Hasło musi zawierać 8 cyfr", jeżeli użytkownik wprowadził mniej/więcej niż 8 cyfr, litery lub inne znaki;
|  "Weryfikacja udała się", jeżeli wprowadzone dane są prawidłowe;
|  "Weryfikacja nie udała się. Spróbuj ponownie" jeżeli wprowadzone hasła nie zgadzają się;
|  "Błąd weryfikacji. Logowanie nie powiodło się", jeżeli za 3 razem wprowadzone hasła nie zgadzają się.
|
|
| Algorytm: hasło jest pobierane z klawiatury. Poprawność hasła sprawdza się za pomocą 2 funkcji warunkowych "if". 
Szyfrowanie odbywa się przy pomocy zagnieżdzionej pętli "for". Każda cyfra tekstu jawnego (niezaszyfrowanego) zastępowana jest inną, oddaloną od niej o "i" - licznik pętli. 
Analogicznie jest z hasłem do sprawdzenia. Porównanie haseł odbywa się z użyciem pętli "for" oraz 3 funkcji warunkowych "if"
|
| Wymagane funkcje nieuwzględnione: program jest zgodny ze wszystkimi
| wymagania określone w zadaniu programowym i wszystkie
| wymagane funkcje są uwzględnione.
|
| Znane błędy: W tym programie nie ma żadnych znanych błędów.
**********************************************************************/
#include <iostream>
#include <string>

using namespace std;
string haslo_poprawne, haslo_sprawdzane;
int poprawne_szyfrowane[7], sprawdzane_szyfrowane[7];
int
main ()
{
  cout << "Wprowadz haslo do logowania." << endl <<
    " Haslo musi skladac sie z 8 cyfr, nie zamierajac zadnych liter oraz znakow specjalnych, w tym spacje "
    << endl;
powtorz:
  cin >> haslo_poprawne;
  if (haslo_poprawne.length () != 8)
    {
      cout << "Haslo musi zawierac 8 cyfr.Sproboj ponownie!" << endl;
      goto powtorz;
    }
  for (int i = 0; i < 8; i++)
    {
      if (((int) haslo_poprawne[i] < 48) || ((int) haslo_poprawne[i] > 57))
	{
	  cout << "Haslo musi zawierac tylko cyfry.Sproboj ponownie!" <<
	    endl;
	  goto powtorz;
	}
      poprawne_szyfrowane[i] = haslo_poprawne[i] + i;
    }

  cout << "Powtorz haslo" << endl;
  int j = 0;
powtorz1:
  cin >> haslo_sprawdzane;
  if (haslo_sprawdzane.length () != 8)
    {
      cout << "Haslo musi zawierac 8 cyfr.Sproboj ponownie!" << endl;
      goto powtorz1;
    }
  for (int i = 0; i < 8; i++)
    {
      sprawdzane_szyfrowane[i] = haslo_sprawdzane[i] + i;
    }
  for (int i = 0; i < 8; i++)
    {
      if ((sprawdzane_szyfrowane[i] != poprawne_szyfrowane[i]) & (j < 3))
	{
	  j = j + 1;
	  cout << "Weryfikacja nie udala sie. Sproboj ponownie"<<endl;
	  goto powtorz1;
	}
    }
  if (j == 3)
    {
      cout << "Blad weryfikacji. Logowanie nie powiodlo sie";
    }
  if (j == 0)
    {
      cout << "Weryfikacja udala sie";
    }

}
```
## Przykład użycia
![image](https://user-images.githubusercontent.com/106164543/173208000-a80c8bcb-ff2c-4fa5-8e19-61f86cd044ca.png)
![image](https://user-images.githubusercontent.com/106164543/173208045-89f8be93-418e-4495-961c-f0258983d1a7.png)

## Status projektu
W czasie testowania nie udało się znaleść żadnych zastrzeń.
