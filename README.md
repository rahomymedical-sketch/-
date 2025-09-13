<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>حساب درجات السنة الدراسية</title>
    <style>
        :root {
            --primary-color: #4CAF50;
            --secondary-color: #2196F3;
            --accent-color: #FF9800;
            --light-color: #f9f9f9;
            --dark-color: #333;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: var(--dark-color);
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            background-color: var(--primary-color);
            color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        .subjects-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .subject-card {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }
        
        .subject-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
        }
        
        .subject-title {
            font-size: 1.5rem;
            color: var(--primary-color);
            margin-bottom: 15px;
            text-align: center;
            border-bottom: 2px solid var(--primary-color);
            padding-bottom: 10px;
        }
        
        .input-group {
            margin-bottom: 15px;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        
        input[type="number"] {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }
        
        button {
            background-color: var(--secondary-color);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            width: 100%;
            transition: background-color 0.3s ease;
        }
        
        button:hover {
            background-color: #0b7dda;
        }
        
        .result {
            margin-top: 15px;
            padding: 15px;
            background-color: var(--light-color);
            border-radius: 4px;
            text-align: center;
            font-weight: bold;
            font-size: 1.2rem;
            display: none;
        }
        
        .total-result {
            background-color: var(--dark-color);
            color: white;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            margin-top: 30px;
            display: none;
        }
        
        .total-result h2 {
            margin-bottom: 15px;
        }
        
        @media (max-width: 768px) {
            .subjects-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>حساب درجات السنة الدراسية</h1>
            <p>أدخل درجاتك لحساب النتيجة النهائية لكل مادة</p>
        </header>
        
        <div class="subjects-container">
            <!-- التشريح -->
            <div class="subject-card">
                <h3 class="subject-title">التشريح</h3>
                <div class="input-group">
                    <label for="anatomy_practical_mid">العملي المد (10)</label>
                    <input type="number" id="anatomy_practical_mid" min="0" max="10" step="0.5">
                </div>
                <div class="input-group">
                    <label for="anatomy_theoretical_mid">النظري المد (20)</label>
                    <input type="number" id="anatomy_theoretical_mid" min="0" max="20" step="0.5">
                </div>
                <div class="input-group">
                    <label for="anatomy_practical_final">العملي الفاينل (20)</label>
                    <input type="number" id="anatomy_practical_final" min="0" max="20" step="0.5">
                </div>
                <div class="input-group">
                    <label for="anatomy_theoretical_final">النظري الفاينل (50)</label>
                    <input type="number" id="anatomy_theoretical_final" min="0" max="50" step="0.5">
                </div>
                <button onclick="calculateAnatomy()">حساب الدرجة</button>
                <div class="result" id="anatomy_result"></div>
            </div>
            
            <!-- الفسلجة -->
            <div class="subject-card">
                <h3 class="subject-title">الفسلجة</h3>
                <div class="input-group">
                    <label for="physiology_practical_mid">العملي المد (10)</label>
                    <input type="number" id="physiology_practical_mid" min="0" max="10" step="0.5">
                </div>
                <div class="input-group">
                    <label for="physiology_theoretical_mid">النظري المد (25)</label>
                    <input type="number" id="physiology_theoretical_mid" min="0" max="25" step="0.5">
                </div>
                <div class="input-group">
                    <label for="physiology_practical_final">العملي الفاينل (10)</label>
                    <input type="number" id="physiology_practical_final" min="0" max="10" step="0.5">
                </div>
                <div class="input-group">
                    <label for="physiology_theoretical_final">النظري الفاينل (50)</label>
                    <input type="number" id="physiology_theoretical_final" min="0" max="50" step="0.5">
                </div>
                <div class="input-group">
                    <label for="physiology_seminar">السمنر (2)</label>
                    <input type="number" id="physiology_seminar" min="0" max="2" step="0.5">
                </div>
                <div class="input-group">
                    <label for="physiology_quizzes">الكوزات (3)</label>
                    <input type="number" id="physiology_quizzes" min="0" max="3" step="0.5">
                </div>
                <button onclick="calculatePhysiology()">حساب الدرجة</button>
                <div class="result" id="physiology_result"></div>
            </div>
            
            <!-- الكيمياء -->
            <div class="subject-card">
                <h3 class="subject-title">الكيمياء</h3>
                <div class="input-group">
                    <label for="chemistry_practical_mid">العملي المد (13)</label>
                    <input type="number" id="chemistry_practical_mid" min="0" max="13" step="0.5">
                </div>
                <div class="input-group">
                    <label for="chemistry_theoretical_mid">النظري المد (20)</label>
                    <input type="number" id="chemistry_theoretical_mid" min="0" max="20" step="0.5">
                </div>
                <div class="input-group">
                    <label for="chemistry_practical_final">العملي الفاينل (13)</label>
                    <input type="number" id="chemistry_practical_final" min="0" max="13" step="0.5">
                </div>
                <div class="input-group">
                    <label for="chemistry_theoretical_final">النظري الفاينل (50)</label>
                    <input type="number" id="chemistry_theoretical_final" min="0" max="50" step="0.5">
                </div>
                <div class="input-group">
                    <label for="chemistry_seminar">السمنر/البوستر (4)</label>
                    <input type="number" id="chemistry_seminar" min="0" max="4" step="0.5">
                </div>
                <button onclick="calculateChemistry()">حساب الدرجة</button>
                <div class="result" id="chemistry_result"></div>
            </div>
            
            <!-- الأنسجة -->
            <div class="subject-card">
                <h3 class="subject-title">الأنسجة</h3>
                <div class="input-group">
                    <label for="histology_practical_mid">العملي المد (10)</label>
                    <input type="number" id="histology_practical_mid" min="0" max="10" step="0.5">
                </div>
                <div class="input-group">
                    <label for="histology_theoretical_mid">النظري المد (20)</label>
                    <input type="number" id="histology_theoretical_mid" min="0" max="20" step="0.5">
                </div>
                <div class="input-group">
                    <label for="histology_practical_final">العملي الفاينل (13)</label>
                    <input type="number" id="histology_practical_final" min="0" max="13" step="0.5">
                </div>
                <div class="input-group">
                    <label for="histology_theoretical_final">النظري الفاينل (55)</label>
                    <input type="number" id="histology_theoretical_final" min="0" max="55" step="0.5">
                </div>
                <div class="input-group">
                    <label for="histology_lookbook">لوك بوك (2)</label>
                    <input type="number" id="histology_lookbook" min="0" max="2" step="0.5">
                </div>
                <button onclick="calculateHistology()">حساب الدرجة</button>
                <div class="result" id="histology_result"></div>
            </div>
            
            <!-- الأجنة -->
            <div class="subject-card">
                <h3 class="subject-title">الأجنة</h3>
                <div class="input-group">
                    <label for="embryology_mid">امتحان المد (30)</label>
                    <input type="number" id="embryology_mid" min="0" max="30" step="0.5">
                </div>
                <div class="input-group">
                    <label for="embryology_final">امتحان الفاينل (70)</label>
                    <input type="number" id="embryology_final" min="0" max="70" step="0.5">
                </div>
                <button onclick="calculateEmbryology()">حساب الدرجة</button>
                <div class="result" id="embryology_result"></div>
            </div>
            
            <!-- أخلاقيات الطب -->
            <div class="subject-card">
                <h3 class="subject-title">أخلاقيات الطب</h3>
                <div class="input-group">
                    <label for="ethics_mid">امتحان المد (30)</label>
                    <input type="number" id="ethics_mid" min="0" max="30" step="0.5">
                </div>
                <div class="input-group">
                    <label for="ethics_final">امتحان الفاينل (70)</label>
                    <input type="number" id="ethics_final" min="0" max="70" step="0.5">
                </div>
                <button onclick="calculateEthics()">حساب الدرجة</button>
                <div class="result" id="ethics_result"></div>
            </div>
            
            <!-- جرائم حزب البعث -->
            <div class="subject-card">
                <h3 class="subject-title">جرائم حزب البعث</h3>
                <div class="input-group">
                    <label for="baath_mid">امتحان المد (40)</label>
                    <input type="number" id="baath_mid" min="0" max="40" step="0.5">
                </div>
                <div class="input-group">
                    <label for="baath_final">امتحان الفاينل (60)</label>
                    <input type="number" id="baath_final" min="0" max="60" step="0.5">
                </div>
                <button onclick="calculateBaath()">حساب الدرجة</button>
                <div class="result" id="baath_result"></div>
            </div>
        </div>
        
        <button onclick="calculateAll()" style="background-color: var(--accent-color); margin-bottom: 20px; font-size: 1.2rem; padding: 15px;">حساب جميع الدرجات</button>
        
        <div class="total-result" id="total_result">
            <h2>النتيجة النهائية لجميع المواد</h2>
            <div id="all_results"></div>
        </div>
    </div>

    <script>
        // دالة حساب التشريح
        function calculateAnatomy() {
            const practicalMid = parseFloat(document.getElementById('anatomy_practical_mid').value) || 0;
            const theoreticalMid = parseFloat(document.getElementById('anatomy_theoretical_mid').value) || 0;
            const practicalFinal = parseFloat(document.getElementById('anatomy_practical_final').value) || 0;
            const theoreticalFinal = parseFloat(document.getElementById('anatomy_theoretical_final').value) || 0;
            
            const total = practicalMid + theoreticalMid + practicalFinal + theoreticalFinal;
            
            const resultElement = document.getElementById('anatomy_result');
            resultElement.style.display = 'block';
            resultElement.innerHTML = `الدرجة النهائية: ${total}/100`;
            resultElement.style.color = total >= 50 ? 'green' : 'red';
            
            return total;
        }
        
        // دالة حساب الفسلجة
        function calculatePhysiology() {
            const practicalMid = parseFloat(document.getElementById('physiology_practical_mid').value) || 0;
            const theoreticalMid = parseFloat(document.getElementById('physiology_theoretical_mid').value) || 0;
            const practicalFinal = parseFloat(document.getElementById('physiology_practical_final').value) || 0;
            const theoreticalFinal = parseFloat(document.getElementById('physiology_theoretical_final').value) || 0;
            const seminar = parseFloat(document.getElementById('physiology_seminar').value) || 0;
            const quizzes = parseFloat(document.getElementById('physiology_quizzes').value) || 0;
            
            const total = practicalMid + theoreticalMid + practicalFinal + theoreticalFinal + seminar + quizzes;
            
            const resultElement = document.getElementById('physiology_result');
            resultElement.style.display = 'block';
            resultElement.innerHTML = `الدرجة النهائية: ${total}/100`;
            resultElement.style.color = total >= 50 ? 'green' : 'red';
            
            return total;
        }
        
        // دالة حساب الكيمياء
        function calculateChemistry() {
            const practicalMid = parseFloat(document.getElementById('chemistry_practical_mid').value) || 0;
            const theoreticalMid = parseFloat(document.getElementById('chemistry_theoretical_mid').value) || 0;
            const practicalFinal = parseFloat(document.getElementById('chemistry_practical_final').value) || 0;
            const theoreticalFinal = parseFloat(document.getElementById('chemistry_theoretical_final').value) || 0;
            const seminar = parseFloat(document.getElementById('chemistry_seminar').value) || 0;
            
            const total = practicalMid + theoreticalMid + practicalFinal + theoreticalFinal + seminar;
            
            const resultElement = document.getElementById('chemistry_result');
            resultElement.style.display = 'block';
            resultElement.innerHTML = `الدرجة النهائية: ${total}/100`;
            resultElement.style.color = total >= 50 ? 'green' : 'red';
            
            return total;
        }
        
        // دالة حساب الأنسجة
        function calculateHistology() {
            const practicalMid = parseFloat(document.getElementById('histology_practical_mid').value) || 0;
            const theoreticalMid = parseFloat(document.getElementById('histology_theoretical_mid').value) || 0;
            const practicalFinal = parseFloat(document.getElementById('histology_practical_final').value) || 0;
            const theoreticalFinal = parseFloat(document.getElementById('histology_theoretical_final').value) || 0;
            const lookbook = parseFloat(document.getElementById('histology_lookbook').value) || 0;
            
            const total = practicalMid + theoreticalMid + practicalFinal + theoreticalFinal + lookbook;
            
            const resultElement = document.getElementById('histology_result');
            resultElement.style.display = 'block';
            resultElement.innerHTML = `الدرجة النهائية: ${total}/100`;
            resultElement.style.color = total >= 50 ? 'green' : 'red';
            
            return total;
        }
        
        // دالة حساب الأجنة
        function calculateEmbryology() {
            const mid = parseFloat(document.getElementById('embryology_mid').value) || 0;
            const final = parseFloat(document.getElementById('embryology_final').value) || 0;
            
            const total = mid + final;
            
            const resultElement = document.getElementById('embryology_result');
            resultElement.style.display = 'block';
            resultElement.innerHTML = `الدرجة النهائية: ${total}/100`;
            resultElement.style.color = total >= 50 ? 'green' : 'red';
            
            return total;
        }
        
        // دالة حساب أخلاقيات الطب
        function calculateEthics() {
            const mid = parseFloat(document.getElementById('ethics_mid').value) || 0;
            const final = parseFloat(document.getElementById('ethics_final').value) || 0;
            
            const total = mid + final;
            
            const resultElement = document.getElementById('ethics_result');
            resultElement.style.display = 'block';
            resultElement.innerHTML = `الدرجة النهائية: ${total}/100`;
            resultElement.style.color = total >= 50 ? 'green' : 'red';
            
            return total;
        }
        
        // دالة حساب جرائم حزب البعث
        function calculateBaath() {
            const mid = parseFloat(document.getElementById('baath_mid').value) || 0;
            const final = parseFloat(document.getElementById('baath_final').value) || 0;
            
            const total = mid + final;
            
            const resultElement = document.getElementById('baath_result');
            resultElement.style.display = 'block';
            resultElement.innerHTML = `الدرجة النهائية: ${total}/100`;
            resultElement.style.color = total >= 50 ? 'green' : 'red';
            
            return total;
        }
        
        // دالة حساب جميع المواد
        function calculateAll() {
            const anatomy = calculateAnatomy();
            const physiology = calculatePhysiology();
            const chemistry = calculateChemistry();
            const histology = calculateHistology();
            const embryology = calculateEmbryology();
            const ethics = calculateEthics();
            const baath = calculateBaath();
            
            const totalAverage = (anatomy + physiology + chemistry + histology + embryology + ethics + baath) / 7;
            
            const allResultsElement = document.getElementById('all_results');
            allResultsElement.innerHTML = `
                <p>التشريح: ${anatomy}/100</p>
                <p>الفسلجة: ${physiology}/100</p>
                <p>الكيمياء: ${chemistry}/100</p>
                <p>الأنسجة: ${histology}/100</p>
                <p>الأجنة: ${embryology}/100</p>
                <p>أخلاقيات الطب: ${ethics}/100</p>
                <p>جرائم حزب البعث: $
