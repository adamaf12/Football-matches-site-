<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>فوتبول - أحدث الأخبار والمباريات</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <div class="logo">
            <h1>فوتبول</h1>
            <p>مكانك الأول لكل ما يخص كرة القدم!</p>
        </div>
        <nav>
            <ul>
                <li><a href="#home">الرئيسية</a></li>
                <li><a href="#matches">المباريات</a></li>
                <li><a href="#news">الأخبار</a></li>
                <li><a href="#contact">اتصل بنا</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="home">
            <h2>مرحبًا بك في فوتبول</h2>
            <p>تابع أحدث المباريات، الأخبار، والتحليلات الرياضية من مكان واحد.</p>
        </section>

        <section id="matches">
            <h2>المباريات الحالية</h2>
            <ul id="matches-list">
                <!-- سيتم تحديث المباريات هنا ديناميكيًا -->
            </ul>
        </section>

        <section id="news">
            <h2>أحدث الأخبار</h2>
            <div id="news-container">
                <!-- سيتم تحديث الأخبار هنا ديناميكيًا -->
            </div>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 فوتبول. جميع الحقوق محفوظة.</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    direction: rtl;
    background-color: #f8f9fa;
    color: #333;
}

/* الهيدر */
header {
    background-color: #007bff;
    color: white;
    padding: 20px;
    text-align: center;
}

header .logo h1 {
    font-size: 2.5rem;
}

header .logo p {
    margin-top: 10px;
    font-size: 1.2rem;
}

nav ul {
    display: flex;
    justify-content: center;
    list-style: none;
    margin-top: 15px;
}

nav ul li {
    margin: 0 15px;
}

nav ul li a {
    text-decoration: none;
    color: white;
    font-size: 1.1rem;
}

/* الأقسام */
main section {
    padding: 40px 20px;
    text-align: center;
    margin: 20px 0;
}

#matches ul,
#news div {
    max-width: 800px;
    margin: 0 auto;
    text-align: left;
}

/* الفوتر */
footer {
    background-color: #007bff;
    color: white;
    text-align: center;
    padding: 10px 0;
}
const apiUrlMatches = "https://api.football-data.org/v4/matches";
const apiKey = "0ba5c54383ad4be7b0d84d5f166fd1bb"; // هذا هو الرقم الذي أرسلته لي

// عرض المباريات
fetch(apiUrlMatches, {
    headers: { 'X-Auth-Token': apiKey }
})
.then(response => response.json())
.then(data => {
    const matchesList = document.getElementById('matches-list');
    data.matches.forEach(match => {
        const li = document.createElement('li');
        li.textContent = `${match.homeTeam.name} ضد ${match.awayTeam.name} - النتيجة: ${match.score.fullTime.homeTeam} - ${match.score.fullTime.awayTeam}`;
        matchesList.appendChild(li);
    });
})
.catch(error => console.error('خطأ في تحميل المباريات:', error));
const apiUrlNews = "https://newsapi.org/v2/everything?q=football&apiKey=YOUR_NEWS_API_KEY"; // استبدل YOUR_NEWS_API_KEY بمفتاح API للأخبار

fetch(apiUrlNews)
.then(response => response.json())
.then(data => {
    const newsContainer = document.getElementById('news-container');
    data.articles.forEach(article => {
        const div = document.createElement('div');
        div.innerHTML = `
            <h3>${article.title}</h3>
            <p>${article.description}</p>
            <a href="${article.url}" target="_blank">اقرأ المزيد</a>
        `;
        newsContainer.appendChild(div);
    });
})
.catch(error => console.error('خطأ في تحميل الأخبار:', error));
