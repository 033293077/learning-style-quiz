# learning-style-quiz<!DOCTYPE html>
<!DOCTYPE html>
<html lang="he">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>בחן את סגנון הלמידה שלך</title>
    <style>
        .question {
            display: none;
        }
        .active {
            display: block;
        }
    </style>
</head>
<body>
    <h1>בחן את סגנון הלמידה שלך</h1>

    <form id="learning-style-quiz">
        <div class="question active" id="question1">
            <h2>כיצד אתה מעדיף לקבל מידע חדש?</h2>
            <input type="radio" id="visual" name="learning-style" value="visual">
            <label for="visual">באמצעות דימויים, גרפים, ומפות</label><br>
            <input type="radio" id="auditory" name="learning-style" value="auditory">
            <label for="auditory">דרך הרצאות או הקלטות שמע</label><br>
            <input type="radio" id="kinesthetic" name="learning-style" value="kinesthetic">
            <label for="kinesthetic">אני מעדיף להתנסות ולהיות בתנועה תוך כדי למידה</label><br>
            <input type="radio" id="textual" name="learning-style" value="textual">
            <label for="textual">דרך קריאת טקסטים וסיכום</label><br><br>
            <button type="button" onclick="nextQuestion(1)">הבא</button>
        </div>

        <div class="question" id="question2">
            <h2>מהי הדרך האידיאלית שלך ללמידה?</h2>
            <input type="radio" id="independent" name="learning-approach" value="independent">
            <label for="independent">אני מעדיף לעבוד לבד בקצב שלי</label><br>
            <input type="radio" id="social" name="learning-approach" value="social">
            <label for="social">אני נהנה מלמידה קבוצתית ושיתוף פעולה עם אחרים</label><br>
            <input type="radio" id="goal-oriented" name="learning-approach" value="goal-oriented">
            <label for="goal-oriented">אני צריך מטרה ברורה ומשימות מוגדרות מראש</label><br>
            <input type="radio" id="curious" name="learning-approach" value="curious">
            <label for="curious">אני נהנה לחקור וללמוד נושאים שונים בגמישות רבה</label><br><br>
            <button type="button" onclick="nextQuestion(2)">הבא</button>
        </div>

        <div class="question" id="question3">
            <h2>מהי מידת המעורבות שלך בתהליך הלמידה?</h2>
            <input type="radio" id="active" name="learning-engagement" value="active">
            <label for="active">אני משתתף בצורה פעילה ותורם לדיון</label><br>
            <input type="radio" id="passive" name="learning-engagement" value="passive">
            <label for="passive">אני מעדיף להקשיב ולצפות מבלי להשתתף יותר מדי</label><br>
            <input type="radio" id="high-interest" name="learning-engagement" value="high-interest">
            <label for="high-interest">אני מאוד מעוניין בנושא וממשיך לחקור מעבר לשיעור</label><br>
            <input type="radio" id="low-interest" name="learning-engagement" value="low-interest">
            <label for="low-interest">אני זקוק לעידוד חיצוני להישאר מעורב בחומר הנלמד</label><br><br>
            <button type="button" onclick="nextQuestion(3)">הבא</button>
        </div>

        <div class="question" id="question4">
            <h2>כיצד אתה מתמודד עם כלים וטכנולוגיות דיגיטליות בלמידה?</h2>
            <input type="radio" id="advanced" name="digital-skills" value="advanced">
            <label for="advanced">אני מסתגל בקלות לטכנולוגיות חדשות</label><br>
            <input type="radio" id="traditional" name="digital-skills" value="traditional">
            <label for="traditional">אני מעדיף להיצמד לשיטות למידה מסורתיות</label><br>
            <input type="radio" id="mixed" name="digital-skills" value="mixed">
            <label for="mixed">אני משתמש בשיטות מסורתיות וגם בטכנולוגיות, בהתאם לצורך</label><br><br>
            <button type="button" onclick="nextQuestion(4)">הבא</button>
        </div>

        <div class="question" id="question5">
            <h2>איזה סוג של תוכן מעניין אותך יותר?</h2>
            <input type="radio" id="analytical" name="content-preference" value="analytical">
            <label for="analytical">אני אוהב ללמוד דרך ניתוח נתונים וסטטיסטיקות</label><br>
            <input type="radio" id="creative" name="content-preference" value="creative">
            <label for="creative">אני מעדיף למידה יצירתית וחוויות חדשניות</label><br><br>
            <button type="submit">גלה את סגנון הלמידה שלך</button>
        </div>
    </form>

    <div id="result"></div>

    <script>
        function nextQuestion(currentQuestion) {
            // Hide current question
            document.getElementById('question' + currentQuestion).classList.remove('active');
            // Show next question
            document.getElementById('question' + (currentQuestion + 1)).classList.add('active');
        }

        document.getElementById("learning-style-quiz").addEventListener("submit", function(event){
            event.preventDefault();
            let result = "הנה התיאור של סגנון הלמידה שלך:\n\n";
            const learningStyle = document.querySelector('input[name="learning-style"]:checked').value;
            const learningApproach = document.querySelector('input[name="learning-approach"]:checked').value;
            const engagement = document.querySelector('input[name="learning-engagement"]:checked').value;
            const digitalSkills = document.querySelector('input[name="digital-skills"]:checked').value;
            const contentPreference = document.querySelector('input[name="content-preference"]:checked').value;

            // סגנון למידה
            if (learningStyle === "visual") {
                result += "אתה לומד בצורה הטובה ביותר דרך דימויים חזותיים כמו גרפים, מפות, ואינפוגרפיקות. ";
            } else if (learningStyle === "auditory") {
                result += "אתה לומד טוב ביותר דרך שמיעה, כמו בהרצאות מוקלטות או פודקאסטים. ";
            } else if (learningStyle === "kinesthetic") {
                result += "אתה נוטה ללמוד דרך התנסות ותנועה. ניסויים ופעילויות פיזיות עוזרות לך להבין את החומר בצורה הטובה ביותר. ";
            } else if (learningStyle === "textual") {
                result += "אתה מעדיף לקרוא ולכתוב כדי ללמוד. קריאת טקסטים וכתיבת סיכומים הם הכלים הטובים ביותר עבורך. ";
            }

            // גישה ללמידה
            if (learningApproach === "independent") {
                result += "אתה מעדיף ללמוד לבד בקצב שלך, ולעיתים אתה מוצא שלמידה בקבוצה אינה מתאימה לך כמו למידה עצמאית. ";
            } else if (learningApproach === "social") {
                result += "אתה נהנה מלמידה בשיתוף פעולה עם אחרים, ומאמין שדיונים ושיתוף פעולה הם חלק בלתי נפרד מהתהליך הלימודי שלך. ";
            } else if (learningApproach === "goal-oriented") {
                result += "אתה לומד בצורה הטובה ביותר כאשר יש לך מטרות ברורות ומשימות מוגדרות שאתה יכול לעבוד עליהן באופן שיטתי. ";
            } else if (learningApproach === "curious") {
                result += "אתה לומד מתוך סקרנות פנימית, ורוצה לחקור נושאים מגוונים ולשאול שאלות כדי להבין לעומק. ";
            }

            // רמת מעורבות
            if (engagement === "active") {
                result += "אתה מעורב מאוד בלמידה שלך, תמיד תורם לדיונים ומביא את הדעות שלך לתוך השיח. ";
            } else if (engagement === "passive") {
                result += "אתה נוטה להקשיב יותר ולצפות, ומעדיף לא להשתתף באופן פעיל בשיעורים. ";
            } else if



            document.getElementById("result").innerText = result;
        });
    </script>
</body>
</html>
