<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>موقع المباريات</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <div class="container">
            <h1>موقع المباريات - تابع المباريات لحظة بلحظة</h1>
        </div>
    </header>

    <main>
        <div class="container">
            <section class="matches">
                <h2>المباريات الحالية</h2>
                <ul id="matches-list">
                    <!-- المباريات ستظهر هنا -->
                </ul>
            </section>

            <section class="update">
                <h2>تحديث المباريات</h2>
                <form id="update-form">
                    <input type="text" id="match-info" placeholder="أدخل تفاصيل المباراة" required>
                    <input type="tel" id="phone" placeholder="رقم هاتفك" required>
                    <button type="submit">تحديث المباراة</button>
                </form>
                <div id="response-message"></div>
            </section>
        </div>
    </main>

    <footer>
        <div class="container">
            <p>&copy; 2024 موقع المباريات. كل الحقوق محفوظة.</p>
        </div>
    </footer>

    <script src="script.js"></script>
</body>
</html>
/* الأساسيات */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    direction: rtl;
    background-color: #f4f4f4;
}

/* الهيدر */
header {
    background-color: #333;
    color: white;
    padding: 20px 0;
}

header .container {
    text-align: center;
}

header h1 {
    font-size: 2rem;
}

/* التصميم الرئيسي */
main {
    padding: 40px 0;
}

.container {
    width: 80%;
    margin: 0 auto;
}

.matches {
    margin-bottom: 40px;
}

.matches ul {
    list-style-type: none;
    padding: 0;
}

.matches li {
    background-color: #fff;
    margin: 10px 0;
    padding: 10px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

/* نموذج التحديث */
.update {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.update form {
    display: flex;
    flex-direction: column;
}

.update input[type="text"],
.update input[type="tel"],
.update button {
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.update button {
    background-color: #28a745;
    color: white;
    cursor: pointer;
}

.update button:hover {
    background-color: #218838;
}

/* الفوتر */
footer {
    background-color: #333;
    color: white;
    padding: 20px 0;
    text-align: center;
}
// المثال المعدل لاستخدام رقمك في الكود عند تحديث المباريات:
document.getElementById('update-form').addEventListener('submit', function(e) {
    e.preventDefault();
    
    const matchInfo = document.getElementById('match-info').value;
    const phone = "0ba5c54383ad4be7b0d84d5f166fd1bb"; // هذا هو الرقم الذي قمت بإرساله
    
    // إضافة بيانات المباراة الجديدة إلى القائمة
    matches.push({ team1: matchInfo.split(" ضد ")[0], team2: matchInfo.split(" ضد ")[1], score: "لم يتم" });

    // تحديث العرض
    displayMatches();

    // عرض رسالة تأكيد مع الرقم
    const responseMessage = document.getElementById('response-message');
    responseMessage.textContent = `تم تحديث المباراة بنجاح! سيتم تحديث النتيجة قريبًا. سيتم التواصل معك عبر الرقم: ${phone}`;

    // مسح البيانات في النموذج
    document.getElementById('match-info').value = '';
    document.getElementById('phone').value = '';
});
