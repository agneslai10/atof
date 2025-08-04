<!DOCTYPE html>
<html lang="ms">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perbandingan Seni Persembahan: Teater Bangsawan & Opera Cina</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals with Soft Accents -->
    <!-- Application Structure Plan: A single-page, top-to-bottom narrative flow designed for students. It starts with a general introduction, moves to an interactive comparison (tabs for similarities/differences), then allows a deeper dive into each art form, visualizes data with a chart, and ends with a reinforcement quiz. This guided discovery path is more engaging for young learners than a static report, encouraging exploration step-by-step. -->
    <!-- Visualization & Content Choices: Report Info: Comparing two art forms. -> Goal: Inform, Compare, Engage. -> Viz/Presentation Method: Interactive tabs (HTML/JS) for direct comparison, cards for focused info, a Bar Chart (Chart.js) to visually compare instrument types, and an interactive quiz (HTML/JS) for reinforcement. -> Interaction: Users click tabs to switch views, hover on chart bars for tooltips, and click quiz answers for immediate feedback. -> Justification: These methods break down complex information into digestible, interactive chunks, making it fun and memorable for students. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FDFBF7;
            color: #4A4A4A;
        }
        .tab-active {
            background-color: #8B5CF6;
            color: #FFFFFF;
            font-weight: 600;
        }
        .tab-inactive {
            background-color: #E5E7EB;
            color: #374151;
        }
        .card-hover {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .quiz-option {
            transition: background-color 0.3s ease;
        }
        .quiz-correct {
            background-color: #D1FAE5 !important;
            border-color: #10B981 !important;
        }
        .quiz-incorrect {
            background-color: #FEE2E2 !important;
            border-color: #EF4444 !important;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
    </style>
</head>
<body class="antialiased">

    <div class="container mx-auto p-4 md:p-8 max-w-5xl">

        <header class="text-center mb-12">
            <h1 class="text-4xl md:text-5xl font-bold text-violet-600 mb-2">Dunia Seni Persembahan</h1>
            <p class="text-lg md:text-xl text-gray-600">Jom Kenali Keunikan Teater Bangsawan & Opera Cina!</p>
        </header>

        <main>
            <section id="pengenalan" class="mb-16">
                 <div class="text-center mb-8">
                    <h2 class="text-3xl font-bold mb-2">Apa itu Seni Persembahan?</h2>
                    <p class="text-gray-600 max-w-3xl mx-auto">Seni persembahan adalah warisan budaya kita yang sangat istimewa. Ia menggabungkan lakonan, muzik, tarian, dan kostum untuk menceritakan kisah-kisah hebat. Di sini, kita akan meneroka dua jenis seni persembahan yang popular di Malaysia: Teater Bangsawan dan Opera Cina.</p>
                </div>
                <div class="grid md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-xl shadow-lg card-hover">
                        <img src="https://placehold.co/600x400/3B82F6/FFFFFF?text=Teater+Bangsawan" alt="Gambaran Teater Bangsawan" class="w-full h-48 object-cover rounded-lg mb-4">
                        <h3 class="text-2xl font-bold text-blue-600 mb-2">Teater Bangsawan</h3>
                        <p class="text-gray-700">Seni persembahan Melayu yang menceritakan kisah-kisah kehidupan istana, pahlawan dan golongan bangsawan. Ia penuh dengan drama, komedi dan muzik tradisional Melayu.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg card-hover">
                        <img src="https://placehold.co/600x400/EF4444/FFFFFF?text=Opera+Cina" alt="Gambaran Opera Cina" class="w-full h-48 object-cover rounded-lg mb-4">
                        <h3 class="text-2xl font-bold text-red-600 mb-2">Opera Cina</h3>
                        <p class="text-gray-700">Berasal dari negara China, seni persembahan ini terkenal dengan solekan tebal, kostum berwarna-warni dan nyanyian bernada tinggi yang unik, mengisahkan lagenda dan sejarah Cina.</p>
                    </div>
                </div>
            </section>

            <section id="perbandingan" class="mb-16">
                <div class="text-center mb-8">
                    <h2 class="text-3xl font-bold mb-2">Sama Tapi Tak Serupa</h2>
                    <p class="text-gray-600 max-w-3xl mx-auto">Walaupun nampak berbeza, kedua-dua seni persembahan ini ada beberapa persamaan! Mari kita lihat apa yang sama dan apa yang berbeza antara keduanya dengan menekan butang di bawah.</p>
                </div>

                <div class="flex justify-center mb-6 space-x-4">
                    <button id="tab-persamaan" class="px-6 py-2 rounded-full text-sm font-medium tab-active">Persamaan</button>
                    <button id="tab-perbezaan" class="px-6 py-2 rounded-full text-sm font-medium tab-inactive">Perbezaan</button>
                </div>

                <div id="content-persamaan" class="bg-white p-6 rounded-xl shadow-md">
                    <h3 class="text-xl font-bold text-center mb-4">Apa yang Sama? 🤔</h3>
                    <ul class="space-y-3 text-gray-700 list-inside list-disc">
                        <li>Kedua-duanya dipersembahkan di atas **pentas**.</li>
                        <li>Diiringi dengan **muzik** untuk menghidupkan suasana.</li>
                        <li>Para pelakon memakai **solekan** dan **kostum** yang khas.</li>
                    </ul>
                </div>

                <div id="content-perbezaan" class="hidden bg-white p-6 rounded-xl shadow-md">
                     <div class="overflow-x-auto">
                        <table class="w-full text-left">
                            <thead>
                                <tr class="bg-gray-100">
                                    <th class="p-3 font-bold">Ciri-ciri</th>
                                    <th class="p-3 font-bold text-blue-600">Teater Bangsawan</th>
                                    <th class="p-3 font-bold text-red-600">Opera Cina</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="border-b">
                                    <td class="p-3 font-semibold">Asal Usul Kisah</td>
                                    <td class="p-3">Kisah bangsawan Melayu</td>
                                    <td class="p-3">Kisah bangsawan Cina</td>
                                </tr>
                                <tr class="border-b">
                                    <td class="p-3 font-semibold">Alat Muzik</td>
                                    <td class="p-3">Gong, gendang, biola, akordion</td>
                                    <td class="p-3">Pipa, guqin, erh-hu, ruan</td>
                                </tr>
                                <tr class="border-b">
                                    <td class="p-3 font-semibold">Solekan</td>
                                    <td class="p-3">Solekan biasa dan natural</td>
                                    <td class="p-3">Solekan tebal dan berwarna-warni</td>
                                </tr>
                                <tr>
                                    <td class="p-3 font-semibold">Pakaian</td>
                                    <td class="p-3">Pakaian tradisional Melayu</td>
                                    <td class="p-3">Pakaian tradisional Cina yang mewah</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <section id="visualisasi" class="mb-16">
                <div class="text-center mb-8">
                    <h2 class="text-3xl font-bold mb-2">Visualisasi Alat Muzik</h2>
                    <p class="text-gray-600 max-w-3xl mx-auto">Setiap persembahan menggunakan alat muzik yang berbeza untuk mencipta melodi yang unik. Carta di bawah menunjukkan jumlah jenis alat muzik yang disenaraikan untuk setiap persembahan. Gerakkan tetikus anda ke atas bar untuk melihat nama alat muzik!</p>
                </div>
                <div class="bg-white p-4 sm:p-6 rounded-xl shadow-lg">
                    <div class="chart-container">
                        <canvas id="instrumentChart"></canvas>
                    </div>
                </div>
            </section>

            <section id="kuiz" class="text-center bg-violet-100 p-8 rounded-2xl">
                <h2 class="text-3xl font-bold mb-2">Jom Uji Minda! 🧠</h2>
                <p class="text-gray-700 mb-6">Anda rasa anda sudah faham? Cuba jawab soalan di bawah.</p>
                
                <div id="quiz-container" class="bg-white p-6 rounded-xl shadow-md max-w-2xl mx-auto">
                    <p id="quiz-question" class="text-lg font-semibold mb-4"></p>
                    <div id="quiz-options" class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    </div>
                    <p id="quiz-feedback" class="mt-4 font-bold h-6"></p>
                    <button id="next-question" class="mt-4 bg-violet-600 text-white px-6 py-2 rounded-full hover:bg-violet-700 transition hidden">Soalan Seterusnya</button>
                </div>
            </section>

        </main>

        <footer class="text-center mt-12 text-gray-500 text-sm">
            <p>Dibangunkan untuk tujuan pendidikan.</p>
        </footer>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const tabPersamaan = document.getElementById('tab-persamaan');
            const tabPerbezaan = document.getElementById('tab-perbezaan');
            const contentPersamaan = document.getElementById('content-persamaan');
            const contentPerbezaan = document.getElementById('content-perbezaan');

            function switchTab(activeTab, inactiveTab, activeContent, inactiveContent) {
                activeTab.classList.remove('tab-inactive');
                activeTab.classList.add('tab-active');
                inactiveTab.classList.remove('tab-active');
                inactiveTab.classList.add('tab-inactive');
                activeContent.classList.remove('hidden');
                inactiveContent.classList.add('hidden');
            }

            tabPersamaan.addEventListener('click', () => {
                switchTab(tabPersamaan, tabPerbezaan, contentPersamaan, contentPerbezaan);
            });

            tabPerbezaan.addEventListener('click', () => {
                switchTab(tabPerbezaan, tabPersamaan, contentPerbezaan, contentPersamaan);
            });

            const data = {
                teaterBangsawan: {
                    name: 'Teater Bangsawan',
                    instruments: ['Gong', 'Gendang', 'Biola', 'Akordion'],
                },
                operaCina: {
                    name: 'Opera Cina',
                    instruments: ['Pipa', 'Guqin', 'Erh-hu', 'Ruan'],
                }
            };

            const ctx = document.getElementById('instrumentChart').getContext('2d');
            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: [data.teaterBangsawan.name, data.operaCina.name],
                    datasets: [{
                        label: 'Jumlah Jenis Alat Muzik',
                        data: [data.teaterBangsawan.instruments.length, data.operaCina.instruments.length],
                        backgroundColor: [
                            'rgba(59, 130, 246, 0.6)',
                            'rgba(239, 68, 68, 0.6)'
                        ],
                        borderColor: [
                            'rgba(59, 130, 246, 1)',
                            'rgba(239, 68, 68, 1)'
                        ],
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    indexAxis: 'y',
                    scales: {
                        x: {
                            beginAtZero: true,
                            ticks: {
                                stepSize: 1
                            }
                        }
                    },
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    const label = context.dataset.label || '';
                                    if (label) {
                                        return `${label}: ${context.raw}`;
                                    }
                                    return context.raw;
                                },
                                afterLabel: function(context) {
                                    if (context.label === data.teaterBangsawan.name) {
                                        return 'Contoh: ' + data.teaterBangsawan.instruments.join(', ');
                                    }
                                    if (context.label === data.operaCina.name) {
                                        return 'Contoh: ' + data.operaCina.instruments.join(', ');
                                    }
                                    return '';
                                }
                            }
                        }
                    }
                }
            });

            const quizData = [
                {
                    question: "Seni persembahan manakah yang terkenal dengan solekan yang tebal?",
                    options: ["Teater Bangsawan", "Opera Cina"],
                    answer: "Opera Cina"
                },
                {
                    question: "Alat muzik 'biola' biasanya digunakan dalam persembahan...",
                    options: ["Teater Bangsawan", "Opera Cina"],
                    answer: "Teater Bangsawan"
                },
                {
                    question: "Apakah persamaan antara kedua-dua seni persembahan ini?",
                    options: ["Menggunakan alat muzik yang sama", "Dipersembahkan di atas pentas"],
                    answer: "Dipersembahkan di atas pentas"
                }
            ];

            let currentQuestionIndex = 0;
            const questionEl = document.getElementById('quiz-question');
            const optionsEl = document.getElementById('quiz-options');
            const feedbackEl = document.getElementById('quiz-feedback');
            const nextButton = document.getElementById('next-question');

            function loadQuestion() {
                const currentQuestion = quizData[currentQuestionIndex];
                questionEl.textContent = currentQuestion.question;
                optionsEl.innerHTML = '';
                feedbackEl.textContent = '';
                nextButton.classList.add('hidden');

                currentQuestion.options.forEach(optionText => {
                    const button = document.createElement('button');
                    button.textContent = optionText;
                    button.classList.add('p-3', 'border-2', 'rounded-lg', 'quiz-option', 'hover:bg-gray-100');
                    button.onclick = () => checkAnswer(optionText);
                    optionsEl.appendChild(button);
                });
            }

            function checkAnswer(selectedOption) {
                const currentQuestion = quizData[currentQuestionIndex];
                const optionButtons = optionsEl.querySelectorAll('button');
                
                optionButtons.forEach(button => {
                    button.disabled = true;
                    if (button.textContent === currentQuestion.answer) {
                        button.classList.add('quiz-correct');
                    }
                });

                if (selectedOption === currentQuestion.answer) {
                    feedbackEl.textContent = "Betul! 👍";
                    feedbackEl.style.color = '#10B981';
                } else {
                    feedbackEl.textContent = "Jawapan kurang tepat. Cuba lagi! 🤔";
                    feedbackEl.style.color = '#EF4444';
                    optionButtons.forEach(button => {
                        if (button.textContent === selectedOption) {
                            button.classList.add('quiz-incorrect');
                        }
                    });
                }
                
                if (currentQuestionIndex < quizData.length - 1) {
                    nextButton.classList.remove('hidden');
                } else {
                    nextButton.textContent = "Selesai!";
                    nextButton.classList.remove('hidden');
                    nextButton.disabled = true;
                }
            }
            
            nextButton.addEventListener('click', () => {
                currentQuestionIndex++;
                loadQuestion();
            });

            loadQuestion();
        });
    </script>
</body>
</html>
