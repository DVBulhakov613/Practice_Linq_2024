МІНІСТЕРСТВО ОСВІТИ І НАУКИ УКРАЇНИ

Національний аерокосмічний університет ім. М. Є. Жуковського
«Харківський авіаційний інститут»
факультет програмної інженерії та бізнесу
кафедра інженерії програмного забезпечення

# ПРАКТИЧНА РОБОТА

з дисципліни «Об’єктно орієнтоване програмування»
на тему: «LINQ»

Виконав: студент 2 курсу групи № 	623П	
освітньої програми
121 інженерія програмного забезпечення	
Булгаков Д.В.
Прийняв:	к.т.н. Лучшев П.О.				
Харків – 2024

# ПОСТАНОВКА ЗАВДАННЯ
1.	Скопіювати віддалений репозиторій (зробити Fork) за наданим посиланням у власний акаунт на GitHub:
https://github.com/IlonaShevchenko/Practice_Linq_2024
У вашому акаунті на GitHub має з’явитися репозиторій-копія (fork).
2.	Клонувати отриманий fork-репозиторій на власний комп’ютер.
3.	Перевірити, що склонований проєкт запускається і виводить на екран тестове значення 13049 (це кількість всіх матчів збірних, які були проведені з 2010 року включно).
4.	Ознайомитися зі структурою проєкту
У проєкті наявний код:
-	 опис класу FootballGame, який описує футбольний матч (FootballGame.сs);
-	у файлі Program.cs вже реалізований метод ReadFromFileJson(), який десеріалізаціє json-файл (data/results_2010.json) у колекцію List;
-	також у файлі Program.cs повністю реалізований метод Main()
5.	Необхідно реалізувати методи Query1(), Query2(), …, Query10(), а саме: за допомогою мови LINQ реалізувати запити, формулювання яких оформлені у вигляді коментарів до кожного методу.
Крім запиту мовою LINQ у кожному методі має бути реалізований вивід на екран результатів запиту (приклад оформлення виводу див. у файлі output.txt).
6.	Після реалізації кожного методу QueryN() необхідно робити commit, вказуючи номер N реалізованого запиту.
7.	Оформити Readme.md файл.
 

# ПОРЯДОК ВИКОНАННЯ РОБОТИ
Вказаний репозиторій було скопійовано у новий віддалений та локальний репозиторії (за допомогою функції Fork на GitHub, та клонування репозиторію у Visual Studio). При запуску було перевірено тестове значення, яке дорівнювало 13049.
Було ознайомлено зі структурою проекту, на основі яких були реалізовані методи Query1(), Query2(), …, Query10() за допомогою мови LINQ. Реалізація була основана на формулюванні запиту коментарями в методах. Також, в методах була присутня вимога на вивід результату запиту, які були зроблені по формату вказаному у файлі output.txt репозиторію. Далі наведено як реалізовані запити, починаючи з Query1() та закінчуючи Query10():

// **Запит 1** - Вивести всі матчі, які відбулися в Україні у 2012 році.

static void Query1(List<FootballGame> games)
{
    var selectedGames = 
        games.Where(t => t.Date >= new DateTime(2012, 1, 1) && t.Date < new DateTime(2013, 1, 1) && t.Country == "Ukraine"); // Корегуємо запит !!!


    // Перевірка
    Console.WriteLine("\n======================== QUERY 1 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames) 
        Console.WriteLine($"{game.Date.ToString("dd.MM.yyyy")} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

// **Запит 2** - Вивести Friendly матчі збірної Італії, які вона провела з 2020 року. 

static void Query2(List<FootballGame> 
{

    var selectedGames = games.Where(t => t.Date >= new DateTime(2020, 1, 1) && (t.Home_team == "Italy" || t.Away_team == "Italy") && t.Tournament == "Friendly"); // Корегуємо запит !!!


    // Перевірка
    Console.WriteLine("\n======================== QUERY 2 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames)
        Console.WriteLine($"{game.Date.ToString("dd.MM.yyyy")} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

// **Запит 3** - Вивести всі домашні матчі збірної Франції за 2021 рік, де вона зіграла у нічию.

static void Query3(List<FootballGame> games)
{


    var selectedGames = games.Where(t => t.Country == "France" && (t.Home_team == "France" || t.Away_team == "France") && t.Date >= new DateTime(2021, 1, 1) && t.Date < new DateTime(2022, 1, 1) && (t.Home_score == t.Away_score));   // Корегуємо запит !!!

    // Перевірка
    Console.WriteLine("\n======================== QUERY 3 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames)
        Console.WriteLine($"{game.Date.ToString("dd.MM.yyyy")} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");


}

// **Запит 4** - Вивести всі матчі збірної Германії з 2018 року по 2020 рік (включно), в яких вона на виїзді програла.

static void Query4(List<FootballGame> games)
{

    var selectedGames = games.Where(t => t.Away_team == "Germany" && t.Date >= new DateTime(2018, 1, 1) && t.Date < new DateTime(2021, 1, 1) && t.Home_score > t.Away_score);   // Корегуємо запит !!!


    // Перевірка
    Console.WriteLine("\n======================== QUERY 4 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames)
        Console.WriteLine($"{game.Date.ToString("dd.MM.yyyy")} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");


}

// **Запит 5** - Вивести всі кваліфікаційні матчі (UEFA Euro qualification), які відбулися у Києві чи у Харкові, а також за умови перемоги української збірної.

static void Query5(List<FootballGame> games)
{

    var selectedGames = games.Where(t => (t.City == "Kharkiv" || t.City == "Kyiv") && t.Tournament == "UEFA Euro qualification" && t.Home_score > t.Away_score);  // Корегуємо запит !!!


    // Перевірка
    Console.WriteLine("\n======================== QUERY 5 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames)
        Console.WriteLine($"{game.Date.ToString("dd.MM.yyyy")} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

// **Запит 6** - Вивести всі матчі останнього чемпіоната світу з футболу (FIFA World Cup), починаючи з чвертьфіналів (тобто останні 8 матчів). Матчі мають відображатися від фіналу до чвертьфіналів (тобто у зворотній послідовності).
    
static void Query6(List<FootballGame> games)
{

    var selectedGames = games.Where(t => t.Tournament == "FIFA World Cup").OrderBy(t => t.Date).TakeLast(8).OrderByDescending(t => t.Date);   // Корегуємо запит !!!


    // Перевірка
    Console.WriteLine("\n======================== QUERY 6 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames)
        Console.WriteLine($"{game.Date.ToString("dd.MM.yyyy")} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");

}

// **Запит 7** - Вивести перший матч у 2023 році, в якому збірна України виграла.

static void Query7(List<FootballGame> games)
{

    FootballGame g = games.First(t => (t.Date >= new DateTime(2023, 1, 1) && t.Date < new DateTime(2024, 1, 1)) 
    && (((t.Home_score > t.Away_score) && t.Home_team == "Ukraine") || (t.Away_score > t.Home_score) && t.Away_team == "Ukraine"));   // Корегуємо запит !!!


    // Перевірка
    Console.WriteLine("\n======================== QUERY 7 ========================");

    // див. приклад як має бути виведено:
    Console.WriteLine($"{g.Date.ToString("dd.MM.yyyy")} {g.Home_team} - {g.Away_team}, Score: {g.Home_score} - {g.Away_score}, Country: {g.Country}");

}

// **Запит 8** - Перетворити всі матчі Євро-2012 (UEFA Euro), які відбулися в Україні, на матчі з наступними властивостями:
MatchYear - рік матчу, Team1 - назва приймаючої команди, Team2 - назва гостьової команди, Goals - сума всіх голів за матч

static void Query8(List<FootballGame> games)
{

    var selectedGames = games
        .Where(t => (t.Date >= new DateTime(2012, 1, 1) && t.Date < new DateTime(2013, 1, 1)) && t.Country == "Ukraine" && t.Tournament == "UEFA Euro")
        .Select(t => new
        {
            MatchYear = t.Date.Year,
            Team1 = t.Home_team,
            Team2 = t.Away_team,
            Goals = t.Home_score + t.Away_score
        });   // Корегуємо запит !!!

    // Перевірка
    Console.WriteLine("\n======================== QUERY 8 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames)
        Console.WriteLine($"{game.MatchYear} {game.Team1} - {game.Team2}, Goals: {game.Goals}");

}


// **Запит 9** - Перетворити всі матчі UEFA Nations League у 2023 році на матчі з наступними властивостями:
MatchYear - рік матчу, Game - назви обох команд через дефіс (першою - Home_team), Result - результат для першої команди (Win, Loss, Draw)

static void Query9(List<FootballGame> games)
{

    var selectedGames = games
        .Where(t => (t.Date >= new DateTime(2023, 1, 1) && t.Date < new DateTime(2024, 1, 1)) && t.Tournament == "UEFA Nations League")
        .Select(t => new
        {
            MatchYear = t.Date.Year,
            Game = $"{t.Home_team}-{t.Away_team}",
            Result = t.Home_score > t.Away_score ? "Win" :
                     t.Home_score < t.Away_score ? "Loss" :
                     "Draw"
        });   // Корегуємо запит !!!

    // Перевірка
    Console.WriteLine("\n======================== QUERY 9 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames)
        Console.WriteLine($"{game.MatchYear} {game.Game}, Result for team1: {game.Result}");

}

// **Запит 10** - Вивести з 5-го по 10-тий (включно) матчі Gold Cup, які відбулися у липні 2023 р.

static void Query10(List<FootballGame> games)
{

    var selectedGames = games
        .Where(t => (t.Date >= new DateTime(2023, 7, 1) && t.Date < new DateTime(2023, 8, 1)) && t.Tournament == "Gold Cup")
        .Skip(4).Take(6);    // Корегуємо запит !!!

    // Перевірка
    Console.WriteLine("\n======================== QUERY 10 ========================");

    // див. приклад як має бути виведено:
    foreach (var game in selectedGames)
        Console.WriteLine($"{game.Date.ToString("dd.MM.yyyy")} {game.Home_team} - {game.Away_team}, Score: {game.Home_score} - {game.Away_score}, Country: {game.Country}");
}

Код програми можна побачити в репозиторії.
 
# ВИСНОВКИ
Під час виконання практичної роботи було реалізовано 10 запитів за допомогою мови LINQ. Для цього було скопійовано віддалений репозиторій за допомогою функції Fork на GitHub, перевірено запуск склонованого проекту, ознайомлено з мовою LINQ та запитом, який мав бути реалізований. Результати запитів було виведено на екран та перевірено, після чого знайдені помилки було виправлено. 
