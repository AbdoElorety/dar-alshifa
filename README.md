# dar-alshifa
دار الشفاء 🏠 - منصة بسيطة وسريعة للبحث عن الأدوية في مصر ومعرفة الاستخدام، السعر، والجرعا
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>منصة تانية ثانوي - الترم الثاني 2026</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Cairo', 'Tahoma', system-ui, sans-serif;
        }
        body {
            background: #f1f8fe;
            padding: 20px;
            color: #1e2f3e;
        }
        .container {
            max-width: 1400px;
            margin: 0 auto;
        }
        /* header */
        .hero {
            text-align: center;
            background: linear-gradient(135deg, #0b2b44, #1b4a6e);
            margin: -20px -20px 30px -20px;
            padding: 35px 20px;
            color: white;
            border-bottom-left-radius: 40px;
            border-bottom-right-radius: 40px;
            box-shadow: 0 12px 25px rgba(0,0,0,0.1);
        }
        .hero h1 {
            font-size: 2.2rem;
            margin-bottom: 8px;
        }
        .hero p {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        .badge-year {
            background: #ffc107;
            color: #0b2b44;
            display: inline-block;
            padding: 4px 15px;
            border-radius: 50px;
            font-weight: bold;
            margin-top: 12px;
        }
        /* filter buttons */
        .filter-buttons {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 12px;
            margin-bottom: 30px;
        }
        .filter-btn {
            background: white;
            border: none;
            padding: 8px 18px;
            border-radius: 50px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            color: #1e4663;
        }
        .filter-btn.active, .filter-btn:hover {
            background: #1e6f5c;
            color: white;
        }
        /* المواد شبكة */
        .subjects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(330px, 1fr));
            gap: 24px;
            margin-bottom: 50px;
        }
        .subject-card {
            background: white;
            border-radius: 30px;
            overflow: hidden;
            box-shadow: 0 12px 24px rgba(0,0,0,0.08);
            transition: transform 0.2s;
            border: 1px solid #e2edf7;
        }
        .subject-card:hover {
            transform: translateY(-5px);
        }
        .card-header {
            background: #d9e9fa;
            padding: 16px 20px;
            border-bottom: 2px solid #b9d4f0;
        }
        .card-header h3 {
            font-size: 1.7rem;
            color: #0a314b;
        }
        .card-header p {
            color: #2c5a74;
            font-size: 0.85rem;
        }
        .card-content {
            padding: 18px;
        }
        .notes-section {
            background: #fefce6;
            border-radius: 20px;
            padding: 12px;
            margin-bottom: 15px;
        }
        .notes-section textarea {
            width: 100%;
            border: 1px solid #e0d6b0;
            border-radius: 16px;
            padding: 10px;
            font-size: 0.9rem;
            background: #fffdf5;
            resize: vertical;
            font-family: inherit;
        }
        .quiz-preview {
            background: #eff5ff;
            padding: 12px;
            border-radius: 20px;
            margin: 10px 0;
        }
        .quiz-question {
            font-weight: bold;
            margin-bottom: 8px;
        }
        .quiz-option {
            display: block;
            margin: 6px 0;
            background: white;
            padding: 6px 12px;
            border-radius: 40px;
            cursor: pointer;
            transition: 0.1s;
            border: 1px solid #cbdde9;
        }
        .quiz-option.selected {
            background: #1e6f5c;
            color: white;
            border-color: #1e6f5c;
        }
        .quiz-feedback {
            font-size: 0.85rem;
            margin-top: 8px;
            color: #2c6e2c;
        }
        button.small-btn {
            background: #1e4663;
            color: white;
            border: none;
            padding: 6px 12px;
            border-radius: 50px;
            cursor: pointer;
            margin-top: 8px;
            font-size: 0.8rem;
        }
        hr {
            margin: 15px 0;
            border: 0;
            height: 1px;
            background: #cce3f5;
        }
        footer {
            text-align: center;
            margin-top: 40px;
            color: #5d7d9c;
            font-size: 0.85rem;
        }
        @media (max-width: 700px) {
            .hero h1 { font-size: 1.5rem; }
            .card-header h3 { font-size: 1.4rem; }
        }
    </style>
</head>
<body>
<div class="hero">
    <h1>📚 منصة المذاكرة الذكية</h1>
    <p>الصف الثاني الثانوي | الترم الثاني 2026</p>
    <div class="badge-year">🌟 جميع المواد - أحدث المناهج 🌟</div>
</div>
<div class="container">
    <div class="filter-buttons" id="filterBtns">
        <button class="filter-btn active" data-filter="all">الكل</button>
        <button class="filter-btn" data-filter="علمي">علمي (رياضة/علوم)</button>
        <button class="filter-btn" data-filter="أدبي">أدبي</button>
    </div>

    <div class="subjects-grid" id="subjectsGrid"></div>
    <footer>
        💡 ملاحظاتك تحفظ تلقائياً في متصفحك | اختبر نفسك بالأسئلة القصيرة لكل مادة
    </footer>
</div>

<script>
    // ---------- بيانات المواد (الترم الثاني 2026) ----------
    const subjectsData = [
        { name: "اللغة العربية", type: "all", icon: "📖", term2topics: "النصوص: (نص قرآني + حديث شريف)، الأدب: العصر الحديث، البلاغة: التشبيه والاستعارة، النحو: المنصوبات والمجرورات" },
        { name: "اللغة الإنجليزية", type: "all", icon: "🇬🇧", term2topics: "Unit 7-12: Reported Speech, Passive, Conditionals, Vocabulary: Environment & Technology, Writing: Opinion Essay" },
        { name: "الرياضيات (بحتة)", type: "علمي", icon: "🧮", term2topics: "حساب المثلثات: المتطابقات، الدوال المثلثية، الهندسة التحليلية: معادلة الدائرة، الإحصاء: مقاييس التشتت" },
        { name: "الفيزياء", type: "علمي", icon: "⚡", term2topics: "الكهربية الساكنة، التيار الكهربي، قانون أوم، المقاومة الكهربية، توصيل المقاومات" },
        { name: "الكيمياء", type: "علمي", icon: "🧪", term2topics: "الأحماض والقواعد، محلول منظم، الأملاح، تفاعلات الأكسدة والاختزال، التحليل الكهربي" },
        { name: "الأحياء", type: "علمي", icon: "🧬", term2topics: "الجهاز العصبي، الهرمونات، المناعة، التكاثر في الكائنات الحية، الهندسة الوراثية" },
        { name: "التاريخ", type: "أدبي", icon: "🏛️", term2topics: "تاريخ مصر الحديث: محمد علي، الخديوي إسماعيل، الثورة العرابية، الحملة الفرنسية" },
        { name: "الجغرافيا", type: "أدبي", icon: "🌍", term2topics: "الموارد الطبيعية، الزراعة، الصناعة، النقل والتجارة، خرائط السكان" },
        { name: "الفلسفة", type: "أدبي", icon: "🧠", term2topics: "مدارس فلسفية: الوجودية، البراجماتية، الفلسفة الإسلامية، مشكلات الفلسفة المعاصرة" }
    ];

    // أسئلة تفاعلية (سؤال واحد لكل مادة كمثال)
    const quizQuestions = {
        "اللغة العربية": { question: "ما هو الشرط الصحيح لجملة 'من يذاكر ينجح'؟", options: ["شرطية جازمة", "شرطية غير جازمة", "جملة عادية"], answer: 0 },
        "اللغة الإنجليزية": { question: "Choose the correct passive: 'Someone wrote this book in 1990.'", options: ["This book is written in 1990.", "This book was written in 1990.", "This book has written in 1990."], answer: 1 },
        "الرياضيات (بحتة)": { question: "إذا كانت sinθ = 1/2 , θ في الربع الثاني، فإن قياس الزاوية θ =", options: ["30°", "150°", "210°"], answer: 1 },
        "الفيزياء": { question: "وحدة قياس المقاومة الكهربية هي؟", options: ["الأوم", "الفولت", "الأمبير"], answer: 0 },
        "الكيمياء": { question: "محلول الأس الهيدروجيني = 3 يكون ...", options: ["قاعدي", "حمضي", "متوسط"], answer: 1 },
        "الأحياء": { question: "الجزء المسؤول عن الاتزان في الأذن الداخلية؟", options: ["القوقعة", "القنوات الهلالية", "طبلة الأذن"], answer: 1 },
        "التاريخ": { question: "من قاد الثورة العرابية في مصر؟", options: ["سعد زغلول", "أحمد عرابي", "مصطفى كامل"], answer: 1 },
        "الجغرافيا": { question: "أحد أنواع الموارد الطبيعية المتجددة:", options: ["النفط", "الفحم", "الطاقة الشمسية"], answer: 2 },
        "الفلسفة": { question: "مؤسس المذهب الوجودي هو:", options: ["أفلاطون", "سارتر", "كانط"], answer: 1 }
    };

    // تحميل الملاحظات المخزنة
    function loadNotes(subjectName) {
        const saved = localStorage.getItem(`notes_${subjectName}`);
        return saved ? saved : `📘 ملخص الترم الثاني 2026 - ${subjectName}\n${getDefaultNotes(subjectName)}`;
    }

    function getDefaultNotes(subjectName) {
        const found = subjectsData.find(s => s.name === subjectName);
        if(found) return found.term2topics;
        return "أضف ملاحظاتك هنا...";
    }

    function saveNotes(subjectName, text) {
        localStorage.setItem(`notes_${subjectName}`, text);
    }

    // بناء واجهة المادة
    function renderSubjects(filterType) {
        const grid = document.getElementById('subjectsGrid');
        const filtered = subjectsData.filter(s => filterType === 'all' ? true : s.type === filterType);
        grid.innerHTML = '';
        filtered.forEach(sub => {
            const savedNotes = loadNotes(sub.name);
            const quiz = quizQuestions[sub.name] || { question: "سؤال نموذجي", options: ["خيار1", "خيار2", "خيار3"], answer: 0 };
            const card = document.createElement('div');
            card.className = 'subject-card';
            card.innerHTML = `
                <div class="card-header">
                    <h3>${sub.icon} ${sub.name}</h3>
                    <p>📅 الترم الثاني 2026</p>
                </div>
                <div class="card-content">
                    <div class="notes-section">
                        <label style="font-weight:bold;">📝 ملاحظاتي ✏️</label>
                        <textarea rows="4" id="notes-${sub.name.replace(/\s/g, '')}" placeholder="اكتب ملخصاتك أو ملاحظاتك هنا...">${escapeHtml(savedNotes)}</textarea>
                        <button class="small-btn" data-subject="${sub.name}" data-save>💾 حفظ الملاحظات</button>
                    </div>
                    <div class="quiz-preview" id="quiz-${sub.name.replace(/\s/g, '')}">
                        <div class="quiz-question">📌 اختبر فهمك: ${quiz.question}</div>
                        <div id="options-${sub.name.replace(/\s/g, '')}"></div>
                        <div id="fb-${sub.name.replace(/\s/g, '')}" class="quiz-feedback"></div>
                        <button class="small-btn" data-quiz-subject="${sub.name}" data-check>تحقق من الإجابة</button>
                    </div>
                </div>
            `;
            grid.appendChild(card);

            // عرض خيارات الاختبار
            const optionsContainer = card.querySelector(`#options-${sub.name.replace(/\s/g, '')}`);
            quiz.options.forEach((opt, idx) => {
                const optDiv = document.createElement('div');
                optDiv.className = 'quiz-option';
                optDiv.innerText = `${idx+1}- ${opt}`;
                optDiv.dataset.optIndex = idx;
                optDiv.addEventListener('click', () => {
                    // إزالة التحديد السابق
                    const allOpts = optionsContainer.querySelectorAll('.quiz-option');
                    allOpts.forEach(o => o.classList.remove('selected'));
                    optDiv.classList.add('selected');
                    // تخزين الإختيار المؤقت
                    optDiv.parentElement.dataset.selected = idx;
                });
                optionsContainer.appendChild(optDiv);
            });

            // ربط حدث حفظ الملاحظات
            const saveBtn = card.querySelector('[data-save]');
            const textarea = card.querySelector(`#notes-${sub.name.replace(/\s/g, '')}`);
            saveBtn.addEventListener('click', () => {
                saveNotes(sub.name, textarea.value);
                alert(`تم حفظ ملاحظات ${sub.name} ✅`);
            });

            // حدث التحقق من الإجابة
            const checkBtn = card.querySelector('[data-check]');
            const fbDiv = card.querySelector(`#fb-${sub.name.replace(/\s/g, '')}`);
            checkBtn.addEventListener('click', () => {
                const selectedDiv = optionsContainer.querySelector('.quiz-option.selected');
                if(!selectedDiv) {
                    fbDiv.innerText = "❌ اختر إجابة أولاً!";
                    fbDiv.style.color = "#b91c1c";
                    return;
                }
                const selectedIdx = parseInt(selectedDiv.dataset.optIndex);
                const correctIdx = quiz.answer;
                if(selectedIdx === correctIdx) {
                    fbDiv.innerHTML = "✅ إجابة صحيحة! أحسنت 🎉";
                    fbDiv.style.color = "#166534";
                } else {
                    fbDiv.innerHTML = `❌ خطأ، الإجابة الصحيحة هي: ${quiz.options[correctIdx]}. راجع الدرس.`;
                    fbDiv.style.color = "#b45309";
                }
            });
        });
    }

    function escapeHtml(str) {
        return str.replace(/[&<>]/g, function(m) {
            if(m === '&') return '&amp;';
            if(m === '<') return '&lt;';
            if(m === '>') return '&gt;';
            return m;
        }).replace(/[\uD800-\uDBFF][\uDC00-\uDFFF]/g, function(c) {
            return c;
        });
    }

    // فلترة
    let currentFilter = 'all';
    function setupFilters() {
        const btns = document.querySelectorAll('.filter-btn');
        btns.forEach(btn => {
            btn.addEventListener('click', () => {
                btns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                currentFilter = btn.dataset.filter;
                renderSubjects(currentFilter);
            });
        });
    }

    renderSubjects('all');
    setupFilters();
</script>
</body>
</html>
