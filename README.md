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

    <form id="learning-style-quiz" onsubmit="showResult(event)">
        <div class="question active" id="question1">
            <h2>כיצד אתה מעדיף לקבל מידע חדש? (ניתן לבחור יותר מתשובה אחת)</h2>
            <input type="checkbox" id="visual" name="learning-style" value="visual">
            <label for="visual">באמצעות דימויים, גרפים, ומפות</label><br>
            <input type="checkbox" id="auditory" name="learning-style" value="auditory">
            <label for="auditory">דרך הרצאות או הקלטות שמע</label><br>
            <input type="checkbox" id="kinesthetic" name="learning-style" value="kinesthetic">
            <label for="kinesthetic">אני מעדיף להתנסות ולהיות בתנועה תוך כדי למידה</label><br>
            <input type="checkbox" id="textual" name="learning-style" value="textual">
            <label for="textual">דרך קריאת טקסטים וסיכום</label><br><br>
            <button type="button" onclick="nextQuestion(1)">הבא</button>
        </div>

        <div class="question" id="question2">
            <h2>מהי הדרך האידיאלית שלך ללמידה? (ניתן לבחור יותר מתשובה אחת)</h2>
            <input type="checkbox" id="independent" name="learning-approach" value="independent">
            <label for="independent">אני מעדיף לעבוד לבד בקצב שלי</label><br>
            <input type="checkbox" id="social" name="learning-approach" value="social">
            <label for="social">אני נהנה מלמידה קבוצתית ושיתוף פעולה עם אחרים</label><br>
            <input type="checkbox" id="goal-oriented" name="learning-approach" value="goal-oriented">
            <label for="goal-oriented">אני צריך מטרה ברורה ומשימות מוגדרות מראש</label><br>
            <input type="checkbox" id="curious" name="learning-approach" value="curious">
            <label for="curious">אני נהנה לחקור וללמוד נושאים שונים בגמישות רבה</label><br><br>
            <button type="button" onclick="nextQuestion(2)">הבא</button>
        </div>

        <div class="question" id="question3">
            <h2>מהי מידת המעורבות שלך בתהליך הלמידה? (ניתן לבחור יותר מתשובה אחת)</h2>
            <input type="checkbox" id="active" name="learning-engagement" value="active">
            <label for="active">אני משתתף בצורה פעילה ותורם לדיון</label><br>
            <input type="checkbox" id="passive" name="learning-engagement" value="passive">
            <label for="passive">אני מעדיף להקשיב ולצפות מבלי להשתתף יותר מדי</label><br>
            <input type="checkbox" id="high-interest" name="learning-engagement" value="high-interest">
            <label for="high-interest">אני מאוד מעוניין בנושא וממשיך לחקור מעבר לשיעור</label><br>
            <input type="checkbox" id="low-interest" name="learning-engagement" value="low-interest">
            <label for="low-interest">אני זקוק לעידוד חיצוני להישאר מעורב בחומר הנלמד</label><br><br>
            <button type="button" onclick="nextQuestion(3)">הבא</button>
        </div>

        <div class="question" id="question4">
            <h2>כיצד אתה מתמודד עם כלים וטכנולוגיות דיגיטליות בלמידה? (ניתן לבחור יותר מתשובה אחת)</h2>
            <input type="checkbox" id="advanced" name="digital-skills" value="advanced">
            <label for="advanced">אני מסתגל בקלות לטכנולוגיות חדשות</label><br>
            <input type="checkbox" id="traditional" name="digital-skills" value="traditional">
            <label for="traditional">אני מעדיף להיצמד לשיטות למידה מסורתיות</label><br>
            <input type="checkbox" id="mixed" name="digital-skills" value="mixed">
            <label for="mixed">אני משתמש בשיטות מסורתיות וגם בטכנולוגיות, בהתאם לצורך</label><br><br>
            <button type="button" onclick="nextQuestion(4)">הבא</button>
        </div>

        <div class="question" id="question5">
            <h2>איזה סוג של תוכן מעניין אותך יותר? (ניתן לבחור יותר מתשובה אחת)</h2>
            <input type="checkbox" id="analytical" name="content-preference" value="analytical">
            <label for="analytical">אני אוהב ללמוד דרך ניתוח נתונים וסטטיסטיקות</label><br>
            <input type="checkbox" id="creative" name="content-preference" value="creative">
            <label for="creative">אני מעדיף למידה יצירתית וחוויות חדשניות</label><br><br>
            <button type="submit">גלה את סגנון הלמידה שלך</button>
        </div>
    </form>

    <script>
        function nextQuestion(currentQuestion) {
            document.getElementById('question' + currentQuestion).classList.remove('active');
            document.getElementById('question' + (currentQuestion + 1)).classList.add('active');
        }

        function showResult(event) {
            event.preventDefault();
            let result = "הנה התיאור הסיפורי שלך:\n\n";

            // איסוף תשובות מתוך הבחירה המרובה
            const learningStyles = document.querySelectorAll('input[name="learning-style"]:checked');
            const learningApproaches = document.querySelectorAll('input[name="learning-approach"]:checked');
            const engagements = document.querySelectorAll('input[name="learning-engagement"]:checked');
            const digitalSkills = document.querySelectorAll('input[name="digital-skills"]:checked');
            const contentPreferences = document.querySelectorAll('input[name="content-preference"]:checked');

            // בניית התוצאה הסיפורית
            if (learningStyles.length > 0) {
                result += "נראה שאתה לומד בצורה: ";
                learningStyles.forEach(style => {
                    if (style.value === "visual") {
                        result += "חזותית, ";
                    } else if (style.value === "auditory") {
                        result += "שמיעתית, ";
                    } else if (style.value === "kinesthetic") {
                        result += "קינסטטית, ";
                    } else if (style.value === "textual") {
                        result += "טקסטואלית, ";
                    }
                });
                result += "\n";
            }

            if (learningApproaches.length > 0) {
                result += "בנוגע לגישה שלך ללמידה, אתה ";
                learningApproaches.forEach(approach => {
                    if (approach.value === "independent") {
                        result += "לומד עצמאי, ";
                    } else if (approach.value === "social") {
                        result += "לומד חברתי, ";
                    } else if (approach.value === "goal-oriented") {
                        result += "מונחה מטרה, ";
                    } else if (approach.value === "curious") {
                        result += "סקרן, ";
                    }
                });
                result += "\n";
            }

            if (engagements.length > 0) {
                result += "אתה מעורב בצורה ";
                engagements.forEach(engagement => {
                    if (engagement.value === "active") {
                        result += "פעילה, ";
                    } else if (engagement.value === "passive") {
                        result += "פאסיבית, ";
                    } else if (engagement.value === "high-interest") {
                        result += "בעלת עניין גבוה, ";
                    } else if (engagement.value === "low-interest") {
                        result += "בעלת עניין נמוך, ";
                    }
                });
                result += "\n";
            }

            if (digitalSkills.length > 0) {
                result += "היכולות הדיגיטליות שלך הן: ";
                digitalSkills.forEach(skill => {
                    if (skill.value === "advanced") {
                        result += "מתקדמות, ";
                    } else if (skill.value === "traditional") {
                       


