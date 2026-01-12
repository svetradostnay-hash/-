# -
Маленький жёлтый шарик с большими пребольшими глазами случаянно поподает из компьютерной игры в реальный мир. Теперь Лукасику надо срочно вернуться обратно, ведь без него игроки не пройдут игру. 
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Сказка о Лукасике - Интерактивная история</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
            padding: 20px;
            max-width: 800px;
            margin: 0 auto;
            background: linear-gradient(to bottom right, #fff8e1, #e3f2fd);
        }
        
        .container {
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            padding: 30px;
            margin-bottom: 20px;
        }
        
        h1 {
            color: #ff9800;
            text-align: center;
            margin-bottom: 20px;
            font-size: 2.5rem;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.1);
        }
        
        h2 {
            color: #2196f3;
            margin-top: 25px;
            margin-bottom: 15px;
            border-bottom: 2px solid #e3f2fd;
            padding-bottom: 5px;
        }
        
        .scene {
            background-color: #f9f9f9;
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            border-left: 5px solid #ff9800;
        }
        
        .dialogue {
            background-color: #e8f5e9;
            border-radius: 10px;
            padding: 15px;
            margin: 15px 0;
            font-style: italic;
            border-left: 4px solid #4caf50;
        }
        
        .character {
            font-weight: bold;
            color: #d81b60;
        }
        
        .choices {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin: 20px 0;
        }
        
        .choice-btn {
            background-color: #2196f3;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            transition: all 0.3s ease;
            flex: 1;
            min-width: 200px;
            text-align: left;
            box-shadow: 0 3px 5px rgba(0,0,0,0.1);
        }
        
        .choice-btn:hover {
            background-color: #1976d2;
            transform: translateY(-2px);
            box-shadow: 0 5px 8px rgba(0,0,0,0.15);
        }
        
        .choice-btn:active {
            transform: translateY(0);
        }
        
        .choice-btn.luka {
            background-color: #ffeb3b;
            color: #333;
        }
        
        .choice-btn.luka:hover {
            background-color: #fdd835;
        }
        
        .choice-btn.eva {
            background-color: #e91e63;
            color: white;
        }
        
        .choice-btn.eva:hover {
            background-color: #c2185b;
        }
        
        .choice-btn.green {
            background-color: #4caf50;
            color: white;
        }
        
        .choice-btn.green:hover {
            background-color: #388e3c;
        }
        
        .choice-btn.purple {
            background-color: #9c27b0;
            color: white;
        }
        
        .choice-btn.purple:hover {
            background-color: #7b1fa2;
        }
        
        .choice-btn.red {
            background-color: #ff5722;
            color: white;
        }
        
        .choice-btn.red:hover {
            background-color: #e64a19;
        }
        
        .ending {
            background-color: #fff3e0;
            border-radius: 10px;
            padding: 25px;
            margin: 20px 0;
            text-align: center;
            border: 3px dashed #ff9800;
        }
        
        .ending.good {
            background-color: #e8f5e9;
            border-color: #4caf50;
        }
        
        .ending.secret {
            background-color: #f3e5f5;
            border-color: #9c27b0;
        }
        
        .ending.bad {
            background-color: #ffebee;
            border-color: #f44336;
        }
        
        .ending.unexpected {
            background-color: #fff3e0;
            border-color: #ff9800;
        }
        
        .restart-btn {
            background-color: #607d8b;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1.1rem;
            margin: 20px auto;
            display: block;
            transition: all 0.3s ease;
        }
        
        .restart-btn:hover {
            background-color: #455a64;
            transform: scale(1.05);
        }
        
        .luka-char {
            text-align: center;
            margin: 20px 0;
        }
        
        .luka-char div {
            display: inline-block;
            width: 100px;
            height: 100px;
            background-color: #ffeb3b;
            border-radius: 50%;
            position: relative;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .luka-char div::before, 
        .luka-char div::after {
            content: '';
            position: absolute;
            width: 25px;
            height: 35px;
            background-color: #333;
            border-radius: 50%;
            top: 25px;
        }
        
        .luka-char div::before {
            left: 15px;
        }
        
        .luka-char div::after {
            right: 15px;
        }
        
        .progress {
            height: 8px;
            background-color: #e0e0e0;
            border-radius: 4px;
            margin: 20px 0;
            overflow: hidden;
        }
        
        .progress-bar {
            height: 100%;
            background-color: #4caf50;
            width: 0%;
            transition: width 0.5s ease;
        }
        
        .hidden {
            display: none;
        }
        
        footer {
            text-align: center;
            margin-top: 30px;
            color: #757575;
            font-size: 0.9rem;
        }
        
        @media (max-width: 600px) {
            .choice-btn {
                min-width: 100%;
            }
            
            .container {
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Сказка о Лукасике</h1>
        
        <div class="luka-char">
            <div></div>
        </div>
        
        <div class="progress">
            <div class="progress-bar" id="progressBar"></div>
        </div>
        
        <!-- Начальная страница -->
        <div id="page1">
            <div class="scene">
                <h2>Часть 1: Пропавший Лукасик</h2>
                <p>Лукасик живёт со своими братьями в компьютерной игре. Лукасики — это такие шарики с большими пребольшими глазами. Они бывают жёлтыми, синими, красными и зелёными. А также голубыми, оранжевыми и фиолетовыми. Наш Лукасик был жёлтым и очень любопытным.</p>
                <p>Но однажды случилось несчастье. Наш Лукасик попал в реальный мир, и ему надо срочно вернуться, иначе игроки не смогут победить.</p>
                
                <div class="dialogue">
                    <p><span class="character">Лукасик:</span> Как мне вернуться обратно, без меня игра не закончится.</p>
                </div>
                
                <p>Вдруг к нему в голову пришла идея. Он решил поехать на площадь города и найти помощь. Но уже скоро стемнеет, надо поторопиться...</p>
            </div>
            
            <h2>Как Лукасику добраться до площади?</h2>
            <div class="choices">
                <button class="choice-btn luka" data-next="pageA">А. Лукасик сел на автобус и поехал на площадь.</button>
                <button class="choice-btn luka" data-next="pageB">Б. Лукасик спустился в метро и поехал на площадь.</button>
            </div>
        </div>
        
        <!-- Вариант А -->
        <div id="pageA" class="hidden">
            <div class="scene">
                <h2>Автобусное приключение</h2>
                <p>Лукасик доехал до площади, но уже стемнело и никого нигде не было. Вдруг недалеко от себя он увидел светящиеся глаза...</p>
                
                <div class="dialogue">
                    <p><span class="character">Лукасик:</span> Ой, кто это!!!</p>
                </div>
                
                <p>Это оказалась кошка...</p>
            </div>
            
            <h2>Что сделать Лукасику?</h2>
            <div class="choices">
                <button class="choice-btn green" data-next="pageA1">💛 Подойти к кошке (Кошка может привести Лукасика к кому-нибудь, кто ему поможет)</button>
                <button class="choice-btn red" data-next="pageA2">💚 Убежать (Вдруг кошка его съест)</button>
            </div>
        </div>
        
        <!-- Вариант А1 -->
        <div id="pageA1" class="hidden">
            <div class="scene">
                <h2>Новая знакомая</h2>
                <p>Кошка привела Лукасика к шестилетней Еве.</p>
                
                <div class="dialogue">
                    <p><span class="character">Ева:</span> Ой, какой милый жёлтый шарик! Как тебя зовут?</p>
                    <p><span class="character">Лукасик:</span> Меня зовут Лукасик!</p>
                    <p><span class="character">Ева:</span> Ты такой милый. Пойдём ко мне жить!</p>
                    <p><span class="character">Лукасик:</span> Пойдём.</p>
                </div>
                
                <p>Ева взяла Лукасика к себе домой.</p>
            </div>
            
            <button class="choice-btn" data-next="page2">Продолжить историю →</button>
        </div>
        
        <!-- Вариант А2 -->
        <div id="pageA2" class="hidden">
            <div class="scene">
                <h2>Испуганный Лукасик</h2>
                <p>Лукасик испугался кошки и убежал.</p>
                
                <div class="dialogue">
                    <p><span class="character">Лукасик:</span> Может мне вернуться?</p>
                </div>
            </div>
            
            <h2>Что делать Лукасику?</h2>
            <div class="choices">
                <button class="choice-btn" data-next="pageA">Вернуться назад</button>
                <button class="choice-btn red" data-next="badEnding1">Не возвращаться</button>
            </div>
        </div>
        
        <!-- Вариант Б -->
        <div id="pageB" class="hidden">
            <div class="scene">
                <h2>Метро и новогодняя ярмарка</h2>
                <p>Лукасик приехал на площади. Там была большая новогодняя ярмарка: горки, шашлыки, горячий шоколад...</p>
                <p>На этой ярмарке Лукасик и встретил маленькую шестилетнюю девочку.</p>
                
                <div class="dialogue">
                    <p><span class="character">Лукасик:</span> Привет, как тебя зовут?</p>
                    <p><span class="character">Ева:</span> Меня зовут Ева, а ты кто?</p>
                    <p><span class="character">Лукасик:</span> А я Лукасик.</p>
                    <p><span class="character">Ева:</span> Ты такой милый. Пойдём ко мне жить.</p>
                    <p><span class="character">Лукасик:</span> Пойдём.</p>
                </div>
            </div>
            
            <button class="choice-btn" data-next="page2">Продолжить историю →</button>
        </div>
        
        <!-- Страница 2 -->
        <div id="page2" class="hidden">
            <div class="scene">
                <h2>Часть 2: Жизнь у Евы</h2>
                <p>Вот уже несколько дней Лукасик жил у маленькой Евы. Пил молоко и ел шоколад.</p>
                <p>Но как бы ни было хорошо Лукасику у Евы, он очень скучал по своим братьям. И конечно он сильно переживал за игроков, которые не смогут пройти игру.</p>
                <p>Лукасик подумал и решил...</p>
            </div>
            
            <h2>Что решил Лукасик?</h2>
            <div class="choices">
                <button class="choice-btn purple" data-next="page3">💜 Рассказать Еве, откуда он</button>
                <button class="choice-btn red" data-next="unexpectedEnding1">💙 Ничего не говорить</button>
            </div>
        </div>
        
        <!-- Страница 3 -->
        <div id="page3" class="hidden">
            <div class="scene">
                <h2>Часть 3: Признание</h2>
                <p>Лукасик всё рассказал Еве.</p>
                
                <div class="dialogue">
                    <p><span class="character">Ева:</span> Конечно я помогу тебе! Тебе надо идти в компьютерный клуб, там есть VR-очки, может, они тебя телепортируют. Но сегодня уже поздно, пойдём туда завтра.</p>
                </div>
                
                <p>Лукасик решил...</p>
            </div>
            
            <h2>Что сделает Лукасик?</h2>
            <div class="choices">
                <button class="choice-btn red" data-next="badEnding2">♥️ Пойти сейчас одному</button>
                <button class="choice-btn green" data-next="page4">💓 Подождать до завтра</button>
            </div>
        </div>
        
        <!-- Страница 4 -->
        <div id="page4" class="hidden">
            <div class="scene">
                <h2>Часть 4: Возвращение домой</h2>
                <p>Утром Лукасик и Ева пришли в компьютерный клуб. Лукасику было очень жаль расставаться...</p>
            </div>
            
            <h2>Как Лукасик попрощается с Евой?</h2>
            <div class="choices">
                <button class="choice-btn red" data-next="unexpectedEnding2">🍎 ...поэтому он решил остаться с Евой</button>
                <button class="choice-btn green" data-next="goodEnding">🍏 ...поэтому он забрался к Еве на руки, помурлыкал ей на прощание и отправился в свой мир</button>
                <button class="choice-btn purple" data-next="secretEnding">🍐 ...поэтому он рассказал Еве про игру и предложил заходить туда когда она хочет. А потом Лукасик отправился в свой мир</button>
            </div>
        </div>
        
        <!-- Плохие концовки -->
        <div id="badEnding1" class="hidden">
            <div class="ending bad">
                <h2>Плохой конец</h2>
                <p>Лукасик не вернулся назад и набрёл на стаю злых собак. Ему не удалось вернуться домой, и игроки так и не смогли пройти игру.</p>
            </div>
            <button class="restart-btn" onclick="restartStory()">Начать заново</button>
        </div>
        
        <div id="badEnding2" class="hidden">
            <div class="ending bad">
                <h2>Плохой конец</h2>
                <p>Лукасик отправился один ночью в компьютерный клуб и набрёл на стаю злых собак. Ему не удалось вернуться домой, и игроки так и не смогли пройти игру.</p>
            </div>
            <button class="restart-btn" onclick="restartStory()">Начать заново</button>
        </div>
        
        <!-- Неожиданные концовки -->
        <div id="unexpectedEnding1" class="hidden">
            <div class="ending unexpected">
                <h2>Неожиданный конец</h2>
                <p>Лукасик остался жить у Евы, и они стали лучшими друзьями. Но игроки ещё очень долго не могли победить в игре.</p>
            </div>
            <button class="restart-btn" onclick="restartStory()">Начать заново</button>
        </div>
        
        <div id="unexpectedEnding2" class="hidden">
            <div class="ending unexpected">
                <h2>Неожиданный конец</h2>
                <p>Лукасик остался жить у Евы, и они стали лучшими друзьями. Но игроки ещё очень долго не могли победить в игре.</p>
            </div>
            <button class="restart-btn" onclick="restartStory()">Начать заново</button>
        </div>
        
        <!-- Хорошая концовка -->
        <div id="goodEnding" class="hidden">
            <div class="ending good">
                <h2>Хороший конец</h2>
                <p>Лукасик забрался к Еве на руки, помурлыкал ей на прощание и отправился в свой мир.</p>
                <p>Лукасик вернулся домой, и игроки смогли пройти игру. Правда, Еве было очень грустно без Лукасика.</p>
            </div>
            <button class="restart-btn" onclick="restartStory()">Начать заново</button>
        </div>
        
        <!-- Секретная концовка -->
        <div id="secretEnding" class="hidden">
            <div class="ending secret">
                <h2>Секретный конец</h2>
                <p>Лукасик рассказал Еве про игру и предложил заходить туда, когда она захочет. Потом Лукасик отправился в свой мир.</p>
                <p>Лукасик вернулся в свой мир, и игроки наконец-то прошли игру. А на следующий день Ева зашла в компьютерную игру и встретила там Лукасика. Лукасик помог ей пройти игру, и теперь они часто встречаются там.</p>
            </div>
            <button class="restart-btn" onclick="restartStory()">Начать заново</button>
        </div>
    </div>
    
    <footer>
        <p>Интерактивная сказка о Лукасике. Создано для GitHub Pages.</p>
    </footer>
    
    <script>
        // Текущая страница
        let currentPage = 'page1';
        
        // Обновление прогресса
        function updateProgress() {
            const pages = {
                'page1': 0,
                'pageA': 20, 'pageB': 20,
                'pageA1': 40, 'pageA2': 40,
                'page2': 40,
                'page3': 60,
                'page4': 80,
                'badEnding1': 100, 'badEnding2': 100,
                'unexpectedEnding1': 100, 'unexpectedEnding2': 100,
                'goodEnding': 100, 'secretEnding': 100
            };
            
            const progressBar = document.getElementById('progressBar');
            if (progressBar && pages[currentPage] !== undefined) {
                progressBar.style.width = pages[currentPage] + '%';
            }
        }
        
        // Показать страницу
        function showPage(pageId) {
            // Скрыть все страницы
            const pages = document.querySelectorAll('[id^="page"], [id$="Ending"]');
            pages.forEach(page => {
                page.classList.add('hidden');
            });
            
            // Показать нужную страницу
            const pageToShow = document.getElementById(pageId);
            if (pageToShow) {
                pageToShow.classList.remove('hidden');
                currentPage = pageId;
                updateProgress();
                
                // Прокрутка к верху страницы
                window.scrollTo({top: 0, behavior: 'smooth'});
            }
        }
        
        // Начать историю заново
        function restartStory() {
            showPage('page1');
        }
        
        // Инициализация при загрузке страницы
        document.addEventListener('DOMContentLoaded', function() {
            // Назначить обработчики событий для всех кнопок выбора
            const choiceButtons = document.querySelectorAll('.choice-btn');
            choiceButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const nextPage = this.getAttribute('data-next');
                    if (nextPage) {
                        showPage(nextPage);
                    }
                });
            });
            
            // Показать первую страницу
            showPage('page1');
        });
    </script>
</body>
</html>
