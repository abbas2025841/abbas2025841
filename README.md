<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مليون - ورشة عملك لتحقيق النجاح والثروة</title>
    <meta name="description" content="موقع مليون: ورشة عملك الشخصية لتحقيق أهدافك اليومية، بناء حضورك الاجتماعي، وتنمية ثروتك من الصفر. مع مهام يومية، نصائح، وآيات قرآنية.">
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts - Noto Naskh Arabic for elegant Arabic script -->
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Noto+Naskh+Arabic:wght@400;700&family=Inter:wght@300;400;500;600;700&display=swap">
    <!-- Font Awesome CDN for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #1a1a1a; /* Dark background */
            color: #e0e0e0; /* Light text for contrast */
        }
        .million-title {
            font-family: 'Noto Naskh Arabic', serif; /* Elegant Arabic font */
            font-weight: 700; /* Bold */
        }
        .gold-text {
            color: #FFD700; /* Gold color */
        }
        .gold-bg {
            background-color: #FFD700;
        }
        .black-bg {
            background-color: #1a1a1a;
        }
        .dark-gray-bg {
            background-color: #2a2a2a;
        }
        .scrollable-content {
            max-height: calc(100vh - 80px); /* Adjust based on header height */
            overflow-y: auto;
            scrollbar-width: thin; /* For Firefox */
            scrollbar-color: #FFD700 #2a2a2a; /* Thumb and Track color */
        }
        /* Custom scrollbar for Webkit browsers */
        .scrollable-content::-webkit-scrollbar {
            width: 8px;
        }
        .scrollable-content::-webkit-scrollbar-track {
            background: #2a2a2a;
            border-radius: 10px;
        }
        .scrollable-content::-webkit-scrollbar-thumb {
            background-color: #FFD700;
            border-radius: 10px;
            border: 2px solid #2a2a2a;
        }
        .active-link {
            background-color: #FFD700;
            color: #1a1a1a;
            font-weight: 600;
        }
        .modal {
            display: none; /* Hidden by default */
            position: fixed; /* Stay in place */
            z-index: 1000; /* Sit on top */
            left: 0;
            top: 0;
            width: 100%; /* Full width */
            height: 100%; /* Full height */
            overflow: auto; /* Enable scroll if needed */
            background-color: rgba(0,0,0,0.7); /* Black w/ opacity */
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background-color: #2a2a2a;
            margin: auto;
            padding: 20px;
            border-radius: 10px;
            width: 80%; /* Could be more responsive */
            max-width: 500px;
            color: #e0e0e0;
            text-align: center;
        }
        .close-button {
            color: #aaa;
            float: left; /* Changed from right for RTL */
            font-size: 28px;
            font-weight: bold;
        }
        .close-button:hover,
        .close-button:focus {
            color: #FFD700;
            text-decoration: none;
            cursor: pointer;
        }
        /* Custom properties for dynamic colors */
        :root {
            --primary-bg: #1a1a1a;
            --secondary-bg: #2a2a2a;
            --text-color: #e0e0e0;
            --gold-color: #FFD700;
            --scrollbar-thumb-color: #FFD700;
            --scrollbar-track-color: #2a2a2a;
        }
        body {
            background-color: var(--primary-bg);
            color: var(--text-color);
        }
        .gold-text { color: var(--gold-color); }
        .gold-bg { background-color: var(--gold-color); }
        .black-bg { background-color: var(--primary-bg); }
        .dark-gray-bg { background-color: var(--secondary-bg); }
        .sidebar-link.active-link {
            background-color: var(--gold-color);
            color: var(--primary-bg); /* Text on gold should be dark */
        }
        .sidebar-link:not(.active-link):hover {
            background-color: rgba(255, 215, 0, 0.2); /* A light gold hover for non-active links */
        }
        .scrollable-content::-webkit-scrollbar-thumb {
            background-color: var(--scrollbar-thumb-color);
            border: 2px solid var(--scrollbar-track-color);
        }
        .scrollable-content::-webkit-scrollbar-track {
            background: var(--scrollbar-track-color);
        }
        /* Style for crown icon to align with text */
        .crown-icon {
            display: inline-block;
            vertical-align: middle;
            margin-right: 10px; /* Space between icon and text */
            font-size: 1em; /* Inherit font size or set specific size */
        }

        /* Adjustments for smaller screens */
        @media (max-width: 768px) {
            .sidebar-link {
                justify-content: center; /* Center text and icon */
                flex-direction: column; /* Stack icon and text vertically */
                text-align: center;
            }
            .sidebar-link svg, .sidebar-link .crown-icon {
                margin-left: 0; /* Remove margin from icon */
                margin-bottom: 5px; /* Add some space below icon */
                margin-right: 0; /* Remove right margin for icons in sidebar links */
            }
            .sidebar-link span {
                display: block; /* Make text break to next line */
            }
            .million-title .crown-icon {
                 font-size: 1.2em; /* Slightly smaller for mobile title */
            }
        }
    </style>
</head>
<body class="bg-black-bg text-e0e0e0 min-h-screen flex flex-col">

    <!-- Firebase SDKs -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";
        import { getFirestore, doc, getDoc, setDoc, onSnapshot, collection, query, addDoc, updateDoc } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";

        // Global Firebase instances
        let app;
        let db;
        let auth;
        let userId = 'guest_user'; // Default for unauthenticated

        // Function to show custom alert modal
        window.showAlert = function(message) {
            const modal = document.getElementById('customAlertModal');
            const messageElement = document.getElementById('alertMessage');
            messageElement.textContent = message;
            modal.style.display = 'flex'; // Show modal
        };

        window.onload = async function() {
            try {
                // IMPORTANT: Use __app_id and __firebase_config provided by the environment
                const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
                const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};

                if (Object.keys(firebaseConfig).length === 0) {
                    console.error("Firebase config not found. Please ensure __firebase_config is set.");
                    // Fallback for development if not in Canvas environment
                    showAlert("خطأ: إعدادات Firebase غير موجودة. الرجاء التحقق من البيئة.");
                    return;
                }

                app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);

                // Authenticate user with custom token or anonymously
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                    await signInWithCustomToken(auth, __initial_auth_token);
                } else {
                    await signInAnonymously(auth);
                }

                onAuthStateChanged(auth, async (user) => {
                    if (user) {
                        userId = user.uid;
                        console.log("Firebase Authenticated! User ID:", userId);
                        document.getElementById('userIdDisplay').textContent = `ID: ${userId}`;
                        // Now that we have a user ID, we can initialize app data and listeners
                        initApp(userId, db);
                    } else {
                        console.log("No user signed in. Using anonymous user.");
                        userId = crypto.randomUUID(); // Fallback for truly anonymous (no token)
                        document.getElementById('userIdDisplay').textContent = `ID: ${userId} (مجهول)`;
                        initApp(userId, db);
                    }
                });

            } catch (error) {
                console.error("Error initializing Firebase or authentication:", error);
                showAlert(`حدث خطأ أثناء تهيئة التطبيق: ${error.message}`);
            }
        };

        // Main app initialization after auth
        async function initApp(currentUserId, firestoreDb) {
            // Check if user is logged in (password screen)
            const isAuthenticated = localStorage.getItem('authenticated') === 'true';
            if (!isAuthenticated) {
                document.getElementById('login-screen').classList.remove('hidden');
                document.getElementById('main-app').classList.add('hidden');
            } else {
                document.getElementById('login-screen').classList.add('hidden');
                document.getElementById('main-app').classList.remove('hidden');
                await loadAndDisplayUserData(currentUserId, firestoreDb);
            }

            // Setup event listeners for navigation and other actions
            setupEventListeners(currentUserId, firestoreDb);
            // Initial render of daily content
            updateDailyContent();
        }

        // --- Firebase Data Management ---
        const getUserDocRef = (userId) => doc(db, `artifacts/${__app_id}/users/${userId}/data/user_profile`);

        async function loadAndDisplayUserData(userId, firestoreDb) {
            const userDocRef = getUserDocRef(userId);
            onSnapshot(userDocRef, (docSnap) => {
                const userData = docSnap.exists() ? docSnap.data() : {
                    tasks: [],
                    settings: {},
                    dailyContent: {
                        quotes: [
                            "النجاح ليس مفتاح السعادة. السعادة هي مفتاح النجاح. إذا أحببت ما تفعله، فستنجح.",
                            "الطريق إلى النجاح دائمًا تحت الإنشاء.",
                            "ابدأ من حيث أنت. استخدم ما لديك. افعل ما تستطيع.",
                            "إذا لم تكن مستعدًا للمخاطرة، فعليك أن ترضى بالحياة العادية.",
                            "الفرص لا تحدث، أنت تخلقها.",
                            "السر في التقدم هو البدء.",
                            "المستقبل ملك لأولئك الذين يؤمنون بجمال أحلامهم.",
                            "الشخص الوحيد الذي قدر لك أن تصبح هو الشخص الذي تقرر أن تكونه."
                        ],
                        tips: [
                            "ركز على مهمة واحدة في كل مرة لتجنب التشتت وزيادة الإنتاجية.",
                            "خصص وقتًا يوميًا للتعلم واكتساب مهارات جديدة في مجالك.",
                            "حافظ على روتين نوم صحي لدعم طاقتك وتركيزك.",
                            "تناول وجبة فطور متوازنة لتبدأ يومك بنشاط.",
                            "ممارسة التأمل لبضع دقائق يوميًا يمكن أن يحسن تركيزك ويقلل التوتر."
                        ],
                        businessIdeas: [
                            "كيف تبدأ مشروعًا صغيرًا بتمويل ذاتي: ركز على الخدمات الرقمية التي لا تتطلب رأس مال كبير.",
                            "أهمية بناء علامتك التجارية الشخصية: اجعل اسمك هو المنتج الأول الذي تبيعه.",
                            "استراتيجيات التسويق بالمحتوى: أنشئ محتوى قيمًا يجذب جمهورك المستهدف عضويًا.",
                            "فن التفاوض: تعلم كيف تحصل على أفضل الصفقات في عالم الأعمال.",
                            "بناء شبكة علاقات قوية: احضر الفعاليات، وتواصل مع المؤثرين في مجالك."
                        ],
                        quranVerses: [
                            { text: "﴿فَإِنَّ مَعَ الْعُسْرِ يُسْرًا﴾", surah: "الشرح: 5" },
                            { text: "﴿وَسَارِعُوا إِلَى مَغْفِرَةٍ مِّن رَّبِّكُمْ وَجَنَّةٍ عَرْضُهَا السَّمَاوَاتُ وَالْأَرْضُ أُعِدَّتْ لِلْمُتَّقِينَ﴾", surah: "آل عمران: 133" },
                            { text: "﴿وَلَا تَيْأَسُوا مِن رَّوْحِ اللَّهِ﴾", surah: "يوسف: 87" },
                            { text: "﴿وَعَسَى أَن تَكْرَهُوا شَيْئًا وَهُوَ خَيْرٌ لَّكُمْ﴾", surah: "البقرة: 216" },
                            { text: "﴿إِنَّ اللَّهَ لَا يُغَيِّرُ مَا بِقَوْمٍ حَتَّىٰ يُغَيِّرُوا مَا بِأَنفُسِهِمْ﴾", surah: "الرعد: 11" }
                        ],
                        videoLinks: [
                            { title: "أسرار النمو على تيك توك في 2024", url: "https://www.youtube.com/watch?v=example1" },
                            { title: "كيف تصنع فيديو فيروسي بـ 3 خطوات بسيطة", url: "https://www.youtube.com/watch?v=example2" },
                            { title: "أفكار محتوى مبتكرة لزيادة التفاعل", url: "https://www.youtube.com/watch?v=example3" }
                        ],
                        editingTutorials: [
                            { title: "تعلم المونتاج الاحترافي بـ DaVinci Resolve (مجاني)", url: "https://www.youtube.com/watch?v=davinci_example" },
                            { title: "أفضل تطبيقات المونتاج المجانية للهاتف", url: "https://www.youtube.com/watch?v=mobile_editing" },
                            { title: "خدع مونتاج لجذب الانتباه (للمبتدئين)", url: "https://www.youtube.com/watch?v=editing_tricks" }
                        ]
                    },
                    tasks: [
                        { name: "قراءة", target: "30 دقيقة", completed: false, type: "daily" },
                        { name: "كتابة", target: "500 كلمة", completed: false, type: "daily" },
                        { name: "تمارين رياضية منزلية", target: "30 دقيقة", completed: false, type: "daily" },
                        { name: "التحقق من أحدث الترندات على تيك توك", target: "15 دقيقة", completed: false, type: "social" },
                        { name: "التفاعل مع 3 حسابات مؤثرة في مجالي", target: "", completed: false, type: "social" }
                    ]
                };

                // Store current user data globally for easy access
                window.currentUserData = userData;
                window.currentUserDocRef = userDocRef; // Store reference for updates

                displayTasks(userData.tasks);
                displayLinks(userData.dailyContent.videoLinks, 'viralVideoLinks');
                displayLinks(userData.dailyContent.editingTutorials, 'editingTutorialsLinks');
                updateDailyContent(); // Refresh daily content based on loaded data
                populateSettings(userData); // Populate settings form
                applyBackgroundSettings(userData); // Apply initial custom colors
            }, (error) => {
                console.error("Error loading user data:", error);
                showAlert(`خطأ في تحميل البيانات: ${error.message}`);
            });
        }

        async function updateUserData(userId, data) {
            try {
                const userDocRef = getUserDocRef(userId);
                await setDoc(userDocRef, data, { merge: true }); // Merge to update existing fields without overwriting
                console.log("User data updated successfully!");
            } catch (error) {
                console.error("Error updating user data:", error);
                showAlert(`خطأ في تحديث البيانات: ${error.message}`);
            }
        }

        // --- Core Application Logic ---

        // Handle navigation
        function showSection(sectionId) {
            document.querySelectorAll('.content-section').forEach(section => {
                section.classList.add('hidden');
            });
            document.getElementById(sectionId).classList.remove('hidden');

            // Update active link styling
            document.querySelectorAll('.sidebar-link').forEach(link => {
                link.classList.remove('active-link');
                link.style.backgroundColor = 'var(--secondary-bg)'; /* Reset to dark gray */
                link.style.color = 'var(--text-color)'; /* Reset to light text */
            });
            const activeLink = document.querySelector(`.sidebar-link[data-section="${sectionId}"]`);
            if (activeLink) {
                activeLink.classList.add('active-link');
                activeLink.style.backgroundColor = 'var(--gold-color)';
                activeLink.style.color = 'var(--primary-bg)';
            }
        }

        // Generate daily content
        function updateDailyContent() {
            const today = new Date();
            const dayOfYear = Math.floor((today - new Date(today.getFullYear(), 0, 0)) / 1000 / 60 / 60 / 24);

            const userData = window.currentUserData;
            if (!userData) return; // Ensure data is loaded

            const quotes = userData.dailyContent.quotes;
            const tips = userData.dailyContent.tips;
            const businessIdeas = userData.dailyContent.businessIdeas;
            const quranVerses = userData.dailyContent.quranVerses;

            // Update Motivational Quote
            if (quotes && quotes.length > 0) {
                const quoteIndex = dayOfYear % quotes.length;
                document.getElementById('motivationalQuote').textContent = quotes[quoteIndex];
            } else {
                document.getElementById('motivationalQuote').textContent = "لا توجد مقولات تحفيزية. أضفها من الإعدادات!";
            }

            // Update Daily Tip
            if (tips && tips.length > 0) {
                const tipIndex = dayOfYear % tips.length;
                document.getElementById('dailyTip').textContent = tips[tipIndex];
            } else {
                document.getElementById('dailyTip').textContent = "لا توجد نصائح يومية. أضفها من الإعدادات!";
            }

            // Update Business Idea
            if (businessIdeas && businessIdeas.length > 0) {
                const ideaIndex = dayOfYear % businessIdeas.length;
                document.getElementById('businessIdea').textContent = businessIdeas[ideaIndex];
            } else {
                document.getElementById('businessIdea').textContent = "لا توجد أفكار أعمال. أضفها من الإعدادات!";
            }

            // Update Quran Verse
            if (quranVerses && quranVerses.length > 0) {
                const quranIndex = dayOfYear % quranVerses.length;
                document.getElementById('quranVerse').innerHTML = `${quranVerses[quranIndex].text} <br> <span class="text-sm gold-text">(${quranVerses[quranIndex].surah})</span>`;
            } else {
                document.getElementById('quranVerse').textContent = "لا يوجد ورد يومي. أضف آيات من الإعدادات!";
            }
        }

        // Display Tasks
        function displayTasks(tasks) {
            const tasksContainer = document.getElementById('dailyTasksContainer');
            if (!tasksContainer) return; // Guard clause
            tasksContainer.innerHTML = ''; // Clear previous tasks

            const socialTasksContainer = document.getElementById('socialTasksContainer');
            if (!socialTasksContainer) return; // Guard clause
            socialTasksContainer.innerHTML = '';

            tasks.forEach((task, index) => {
                const taskElement = `
                    <div class="flex items-center justify-between p-3 dark-gray-bg rounded-lg mb-2 shadow-md">
                        <div class="flex items-center">
                            <input type="checkbox" id="task-${index}" data-index="${index}" ${task.completed ? 'checked' : ''} class="task-checkbox h-5 w-5 text-gold-text form-checkbox rounded border-gray-500 focus:ring-gold-text bg-gray-700">
                            <label for="task-${index}" class="mr-3 text-lg ${task.completed ? 'line-through text-gray-500' : 'gold-text'}">${task.name} ${task.target ? `(${task.target})` : ''}</label>
                        </div>
                        <button class="delete-task-btn text-red-500 hover:text-red-700 focus:outline-none" data-index="${index}">
                            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
                                <path fill-rule="evenodd" d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm6 0a1 1 0 012 0v6a1 1 0 11-2 0V8z" clip-rule="evenodd"></path>
                            </svg>
                        </button>
                    </div>
                `;
                if (task.type === "daily") {
                    tasksContainer.insertAdjacentHTML('beforeend', taskElement);
                } else if (task.type === "social") {
                    socialTasksContainer.insertAdjacentHTML('beforeend', taskElement);
                }
            });

            // Add event listeners for checkboxes and delete buttons
            document.querySelectorAll('.task-checkbox').forEach(checkbox => {
                checkbox.onchange = async (e) => {
                    const index = parseInt(e.target.dataset.index);
                    if (window.currentUserData && window.currentUserData.tasks) {
                        window.currentUserData.tasks[index].completed = e.target.checked;
                        await updateUserData(userId, { tasks: window.currentUserData.tasks });
                        displayTasks(window.currentUserData.tasks); // Re-render to apply line-through
                    }
                };
            });
            document.querySelectorAll('.delete-task-btn').forEach(button => {
                button.onclick = async (e) => {
                    const index = parseInt(e.currentTarget.dataset.index);
                    if (window.currentUserData && window.currentUserData.tasks) {
                        window.currentUserData.tasks.splice(index, 1);
                        await updateUserData(userId, { tasks: window.currentUserData.tasks });
                        displayTasks(window.currentUserData.tasks); // Re-render
                    }
                };
            });
        }

        // Display Links
        function displayLinks(links, containerId) {
            const container = document.getElementById(containerId);
            if (!container) return; // Guard clause
            container.innerHTML = '';
            links.forEach(link => {
                container.insertAdjacentHTML('beforeend', `
                    <a href="${link.url}" target="_blank" class="block p-3 dark-gray-bg rounded-lg mb-2 hover:gold-bg hover:text-black-bg transition-colors duration-200 shadow-md">
                        <p class="text-lg">${link.title}</p>
                    </a>
                `);
            });
        }

        // Populate Settings Form
        function populateSettings(userData) {
            const settingsForm = document.getElementById('settingsForm');
            if (!settingsForm || !userData || !userData.dailyContent || !userData.tasks) return;

            // Daily Content Settings
            document.getElementById('quotesInput').value = userData.dailyContent.quotes.join('\n');
            document.getElementById('tipsInput').value = userData.dailyContent.tips.join('\n');
            document.getElementById('businessIdeasInput').value = userData.dailyContent.businessIdeas.join('\n');
            document.getElementById('quranVersesInput').value = JSON.stringify(userData.dailyContent.quranVerses, null, 2); // Pretty print JSON

            // Background color input - use a simple text input for hex code
            document.getElementById('backgroundColorInput').value = userData.settings.backgroundColor || '#1a1a1a';
            document.getElementById('textColorInput').value = userData.settings.textColor || '#e0e0e0';
            document.getElementById('goldColorInput').value = userData.settings.goldColor || '#FFD700';

            // Populate current tasks for editing
            const currentTasksList = document.getElementById('currentTasksList');
            currentTasksList.innerHTML = '';
            userData.tasks.forEach((task, index) => {
                currentTasksList.insertAdjacentHTML('beforeend', `
                    <li class="flex items-center justify-between p-2 bg-gray-800 rounded-md mb-1">
                        <span class="text-sm">${task.name} (${task.type}) - ${task.target}</span>
                        <button class="delete-settings-task-btn text-red-400 hover:text-red-600 text-sm" data-index="${index}">حذف</button>
                    </li>
                `);
            });
            document.querySelectorAll('.delete-settings-task-btn').forEach(button => {
                button.onclick = async (e) => {
                    const index = parseInt(e.currentTarget.dataset.index);
                    if (window.currentUserData && window.currentUserData.tasks) {
                        window.currentUserData.tasks.splice(index, 1);
                        await updateUserData(userId, { tasks: window.currentUserData.tasks });
                        populateSettings(window.currentUserData); // Re-populate settings list
                        displayTasks(window.currentUserData.tasks); // Re-render dashboard tasks
                    }
                };
            });

            // Populate current links for editing
            const currentViralVideosList = document.getElementById('currentViralVideosList');
            currentViralVideosList.innerHTML = '';
            userData.dailyContent.videoLinks.forEach((link, index) => {
                currentViralVideosList.insertAdjacentHTML('beforeend', `
                    <li class="flex items-center justify-between p-2 bg-gray-800 rounded-md mb-1">
                        <span class="text-sm">${link.title}</span>
                        <button class="delete-viral-link-btn text-red-400 hover:text-red-600 text-sm" data-index="${index}">حذف</button>
                    </li>
                `);
            });
            document.querySelectorAll('.delete-viral-link-btn').forEach(button => {
                button.onclick = async (e) => {
                    const index = parseInt(e.currentTarget.dataset.index);
                    if (window.currentUserData && window.currentUserData.dailyContent) {
                        window.currentUserData.dailyContent.videoLinks.splice(index, 1);
                        await updateUserData(userId, { dailyContent: window.currentUserData.dailyContent });
                        populateSettings(window.currentUserData);
                        displayLinks(window.currentUserData.dailyContent.videoLinks, 'viralVideoLinks');
                    }
                };
            });

            const currentEditingTutorialsList = document.getElementById('currentEditingTutorialsList');
            currentEditingTutorialsList.innerHTML = '';
            userData.dailyContent.editingTutorials.forEach((link, index) => {
                currentEditingTutorialsList.insertAdjacentHTML('beforeend', `
                    <li class="flex items-center justify-between p-2 bg-gray-800 rounded-md mb-1">
                        <span class="text-sm">${link.title}</span>
                        <button class="delete-editing-link-btn text-red-400 hover:text-red-600 text-sm" data-index="${index}">حذف</button>
                    </li>
                `);
            });
            document.querySelectorAll('.delete-editing-link-btn').forEach(button => {
                button.onclick = async (e) => {
                    const index = parseInt(e.currentTarget.dataset.index);
                    if (window.currentUserData && window.currentUserData.dailyContent) {
                        window.currentUserData.dailyContent.editingTutorials.splice(index, 1);
                        await updateUserData(userId, { dailyContent: window.currentUserData.dailyContent });
                        populateSettings(window.currentUserData);
                        displayLinks(window.currentUserData.dailyContent.editingTutorials, 'editingTutorialsLinks');
                    }
                };
            });
        }

        // Apply background settings (dynamic CSS variables)
        function applyBackgroundSettings(userData) {
            const root = document.documentElement;
            const settings = userData.settings || {};

            const primaryBg = settings.backgroundColor || '#1a1a1a';
            const textColor = settings.textColor || '#e0e0e0';
            const goldColor = settings.goldColor || '#FFD700';

            root.style.setProperty('--primary-bg', primaryBg);
            root.style.setProperty('--secondary-bg', darkenColor(primaryBg, 10)); /* Slightly darker for cards/sidebar */
            root.style.setProperty('--text-color', textColor);
            root.style.setProperty('--gold-color', goldColor);
            root.style.setProperty('--scrollbar-thumb-color', goldColor);
            root.style.setProperty('--scrollbar-track-color', darkenColor(primaryBg, 10));

            // Re-apply active link style after color change
            const activeLink = document.querySelector('.sidebar-link.active-link');
            if (activeLink) {
                activeLink.style.backgroundColor = goldColor;
                activeLink.style.color = darkenColor(goldColor, 80); // Darker text on gold for contrast
            }
        }

        function darkenColor(hex, percent) {
            let f=parseInt(hex.slice(1),16),t=percent<0?0:255,p=percent<0?percent*-1:percent,R=f>>16,G=(f>>8)&0x00FF,B=f&0x0000FF;
            return "#"+(0x1000000+(Math.round((t-R)*p)+R)*0x10000+(Math.round((t-G)*p)+G)*0x100+(Math.round((t-B)*p)+B)).toString(16).slice(1);
        }


        // --- Event Listeners ---
        function setupEventListeners(currentUserId, firestoreDb) {
            // Login form submission
            document.getElementById('loginForm').addEventListener('submit', function(e) {
                e.preventDefault();
                const password = document.getElementById('passwordInput').value;
                const correctPassword = '737825698a'; // Hardcoded password

                if (password === correctPassword) {
                    localStorage.setItem('authenticated', 'true');
                    document.getElementById('login-screen').classList.add('hidden');
                    document.getElementById('main-app').classList.remove('hidden');
                    loadAndDisplayUserData(currentUserId, firestoreDb);
                } else {
                    showAlert('كلمة المرور غير صحيحة.');
                }
            });

            // Sidebar navigation
            document.querySelectorAll('.sidebar-link').forEach(link => {
                link.addEventListener('click', function() {
                    showSection(this.dataset.section);
                });
            });

            // Add New Task
            document.getElementById('addTaskBtn').addEventListener('click', async () => {
                const newTaskName = document.getElementById('newTaskName').value.trim();
                const newTaskTarget = document.getElementById('newTaskTarget').value.trim();
                const newTaskType = document.getElementById('newTaskType').value;

                if (newTaskName) {
                    const newTask = {
                        name: newTaskName,
                        target: newTaskTarget,
                        completed: false,
                        type: newTaskType // "daily" or "social"
                    };
                    if (window.currentUserData && window.currentUserData.tasks) {
                        window.currentUserData.tasks.push(newTask);
                        await updateUserData(currentUserId, { tasks: window.currentUserData.tasks });
                        document.getElementById('newTaskName').value = '';
                        document.getElementById('newTaskTarget').value = '';
                    }
                } else {
                    showAlert('الرجاء إدخال اسم للمهمة.');
                }
            });

            // Add New Viral Video Link
            document.getElementById('addViralVideoLinkBtn').addEventListener('click', async () => {
                const title = document.getElementById('newViralVideoTitle').value.trim();
                const url = document.getElementById('newViralVideoUrl').value.trim();
                if (title && url) {
                    if (window.currentUserData && window.currentUserData.dailyContent) {
                        window.currentUserData.dailyContent.videoLinks.push({ title, url });
                        await updateUserData(currentUserId, { dailyContent: window.currentUserData.dailyContent });
                        document.getElementById('newViralVideoTitle').value = '';
                        document.getElementById('newViralVideoUrl').value = '';
                    }
                } else {
                    showAlert('الرجاء إدخال عنوان ورابط للفيديو.');
                }
            });

            // Add New Editing Tutorial Link
            document.getElementById('addEditingTutorialLinkBtn').addEventListener('click', async () => {
                const title = document.getElementById('newEditingTutorialTitle').value.trim();
                const url = document.getElementById('newEditingTutorialUrl').value.trim();
                if (title && url) {
                    if (window.currentUserData && window.currentUserData.dailyContent) {
                        window.currentUserData.dailyContent.editingTutorials.push({ title, url });
                        await updateUserData(currentUserId, { dailyContent: window.currentUserData.dailyContent });
                        document.getElementById('newEditingTutorialTitle').value = '';
                        document.getElementById('newEditingTutorialUrl').value = '';
                    }
                } else {
                    showAlert('الرجاء إدخال عنوان ورابط لدرس المونتاج.');
                }
            });

            // Save Settings
            document.getElementById('saveSettingsBtn').addEventListener('click', async () => {
                if (!window.currentUserData) {
                    showAlert('خطأ: بيانات المستخدم غير متاحة. الرجاء إعادة تحميل الصفحة.');
                    return;
                }

                // Ensure dailyContent object exists
                if (!window.currentUserData.dailyContent) {
                    window.currentUserData.dailyContent = {};
                }

                // Update Daily Content arrays
                window.currentUserData.dailyContent.quotes = document.getElementById('quotesInput').value.split('\n').map(s => s.trim()).filter(s => s);
                window.currentUserData.dailyContent.tips = document.getElementById('tipsInput').value.split('\n').map(s => s.trim()).filter(s => s);
                window.currentUserData.dailyContent.businessIdeas = document.getElementById('businessIdeasInput').value.split('\n').map(s => s.trim()).filter(s => s);

                try {
                    const quranVersesInput = document.getElementById('quranVersesInput').value;
                    window.currentUserData.dailyContent.quranVerses = JSON.parse(quranVersesInput);
                    // Validate JSON for quranVerses to prevent errors
                    if (!Array.isArray(window.currentUserData.dailyContent.quranVerses) || !window.currentUserData.dailyContent.quranVerses.every(item => typeof item === 'object' && item.text && item.surah)) {
                        throw new Error("تنسيق آيات القرآن غير صحيح. يجب أن يكون JSON array of objects with 'text' and 'surah'.");
                    }
                } catch (e) {
                    showAlert(`خطأ في تنسيق آيات القرآن: ${e.message}. الرجاء التأكد من أنها بصيغة JSON صحيحة.`);
                    // Optionally, keep the previous valid data or clear it
                    window.currentUserData.dailyContent.quranVerses = [];
                    return; // Stop saving if there's a JSON parse error
                }

                // Update Background settings
                window.currentUserData.settings.backgroundColor = document.getElementById('backgroundColorInput').value;
                window.currentUserData.settings.textColor = document.getElementById('textColorInput').value;
                window.currentUserData.settings.goldColor = document.getElementById('goldColorInput').value;

                await updateUserData(currentUserId, window.currentUserData);
                applyBackgroundSettings(window.currentUserData); // Apply immediately
                updateDailyContent(); // Refresh daily content based on new settings
                showAlert('تم حفظ الإعدادات بنجاح!');
            });

            // Chat with AI
            const chatInput = document.getElementById('chatInput');
            const chatSendBtn = document.getElementById('chatSendBtn');
            const chatMessages = document.getElementById('chatMessages');
            const chatLoading = document.getElementById('chatLoading');

            async function sendMessageToAI() {
                const prompt = chatInput.value.trim();
                if (!prompt) return;

                // Clear input
                chatInput.value = '';

                // Add user message to chat
                chatMessages.innerHTML += `<div class="bg-gray-700 text-gold-text p-2 rounded-lg mb-2 self-end max-w-[80%]">${prompt}</div>`;
                chatMessages.scrollTop = chatMessages.scrollHeight; // Scroll to bottom

                chatLoading.classList.remove('hidden'); // Show loading indicator

                try {
                    let chatHistory = [];
                    // You might want to build a more robust chat history for context
                    chatHistory.push({ role: "user", parts: [{ text: prompt }] });

                    const payload = { contents: chatHistory };
                    // Replace with the actual API key from your Canvas environment if available, otherwise it's filled automatically
                    const apiKey = ""; 
                    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    const result = await response.json();
                    chatLoading.classList.add('hidden'); // Hide loading indicator

                    if (result.candidates && result.candidates.length > 0 &&
                        result.candidates[0].content && result.candidates[0].content.parts &&
                        result.candidates[0].content.parts.length > 0) {
                        const text = result.candidates[0].content.parts[0].text;
                        chatMessages.innerHTML += `<div class="bg-blue-900 text-e0e0e0 p-2 rounded-lg mb-2 self-start max-w-[80%]">${text}</div>`;
                    } else {
                        chatMessages.innerHTML += `<div class="bg-red-800 text-white p-2 rounded-lg mb-2 self-start max-w-[80%]">خطأ: لم يتم استلام استجابة صالحة من الذكاء الاصطناعي.</div>`;
                    }
                } catch (error) {
                    console.error("Error communicating with AI:", error);
                    chatLoading.classList.add('hidden'); // Hide loading indicator
                    chatMessages.innerHTML += `<div class="bg-red-800 text-white p-2 rounded-lg mb-2 self-start max-w-[80%]">خطأ في الاتصال بالذكاء الاصطناعي: ${error.message}</div>`;
                }
                chatMessages.scrollTop = chatMessages.scrollHeight; // Scroll to bottom
            }

            chatSendBtn.addEventListener('click', sendMessageToAI);
            chatInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    sendMessageToAI();
                }
            });
        }
    </script>

    <div id="customAlertModal" class="modal">
        <div class="modal-content">
            <span class="close-button" onclick="document.getElementById('customAlertModal').style.display='none'">×</span>
            <p id="alertMessage" class="mt-4 text-xl"></p>
            <button onclick="document.getElementById('customAlertModal').style.display='none'" class="mt-5 px-6 py-2 gold-bg text-black-bg font-semibold rounded-md hover:opacity-90 transition-opacity">موافق</button>
        </div>
    </div>

    <div id="login-screen" class="min-h-screen flex items-center justify-center bg-black-bg hidden">
        <div class="bg-dark-gray-bg p-8 rounded-lg shadow-xl text-center max-w-sm w-full border border-gold-text">
            <h1 class="text-5xl font-extrabold gold-text million-title mb-6 flex items-center justify-center">
                مليون
            </h1>
            <p class="text-2xl text-e0e0e0 mb-8">المستقبل</p>
            <form id="loginForm">
                <input type="password" id="passwordInput" placeholder="كلمة المرور" class="w-full p-3 mb-4 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50" required>
                <button type="submit" class="w-full p-3 gold-bg text-black-bg font-bold rounded-md hover:opacity-90 transition-opacity text-xl">دخول</button>
            </form>
        </div>
    </div>

    <div id="main-app" class="flex flex-1 hidden">
        <aside class="w-64 bg-dark-gray-bg p-6 flex flex-col rounded-l-lg shadow-lg">
            <div class="flex items-center justify-center mb-10">
                <h2 class="text-3xl font-extrabold gold-text million-title flex items-center justify-center">
                    مليون
                </h2>
            </div>
            <nav class="flex-1">
                <ul>
                    <li class="mb-3">
                        <a href="#" data-section="dashboard-section" class="sidebar-link active-link flex items-center p-3 rounded-lg transition-colors duration-200">
                            <svg class="w-6 h-6 ml-3" fill="currentColor" viewBox="0 0 20 20"><path d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z"></path></svg>
                            <span>لوحة القيادة</span>
                        </a>
                    </li>
                    <li class="mb-3">
                        <a href="#" data-section="daily-tasks-section" class="sidebar-link flex items-center p-3 rounded-lg hover:bg-gray-700 transition-colors duration-200">
                            <svg class="w-6 h-6 ml-3" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 9a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM9 13a1 1 0 011-1h6a1 1 0 110 2h-6a1 1 0 01-1-1z" clip-rule="evenodd"></path></svg>
                            <span>مهامي اليومية</span>
                        </a>
                    </li>
                    <li class="mb-3">
                        <a href="#" data-section="social-media-section" class="sidebar-link flex items-center p-3 rounded-lg hover:bg-gray-700 transition-colors duration-200">
                        <svg class="w-6 h-6 ml-3" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M18 10c0 3.866-3.582 7-8 7a8.841 8.841 0 01-4.17-.953l-4.58 1.355a1 1 0 01-1.218-1.218l1.355-4.58A7 7 0 012 10c0-3.866 3.582-7 8-7s8 3.134 8 7zM9 9a1 1 0 000 2h2a1 1 0 100-2H9z" clip-rule="evenodd"></path></svg>
                            <span>الحضور الاجتماعي</span>
                        </a>
                    </li>
                     <li class="mb-3">
                        <a href="#" data-section="business-wealth-section" class="sidebar-link flex items-center p-3 rounded-lg hover:bg-gray-700 transition-colors duration-200">
                            <svg class="w-6 h-6 ml-3" fill="currentColor" viewBox="0 0 20 20"><path d="M5.5 10a.5.5 0 11-1 0 .5.5 0 011 0zM12 10a.5.5 0 11-1 0 .5.5 0 011 0zM15 10a.5.5 0 11-1 0 .5.5 0 011 0z"></path><path fill-rule="evenodd" d="M12.914 1.054a1 1 0 00-.914-.515H7.728a1 1 0 00-.914.515L.896 9.873a1 1 0 00-.024.939l2.766 6.839a1.001 1.001 0 00.952.649h10.912a1.001 1.001 0 00.952-.649l2.766-6.839a1 1 0 00-.024-.939l-5.918-8.819zM9 16a1 1 0 100-2 1 1 0 000 2zm1-7a1 1 0 00-2 0v2a1 1 0 102 0V9z" clip-rule="evenodd"></path></svg>
                            <span>تطوير الأعمال والثروة</span>
                        </a>
                    </li>
                    <li class="mb-3">
                        <a href="#" data-section="content-library-section" class="sidebar-link flex items-center p-3 rounded-lg hover:bg-gray-700 transition-colors duration-200">
                            <svg class="w-6 h-6 ml-3" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M4 4a2 2 0 012-2h4.586A2 2 0 0112 2.414L14.586 5A2 2 0 0115 5.414V16a2 2 0 01-2 2H6a2 2 0 01-2-2V4zm2 2V4h3.586L12 7.414V16h-6V6zm4 8a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd"></path></svg>
                            <span>مكتبة المحتوى</span>
                        </a>
                    </li>
                    <li class="mb-3">
                        <a href="#" data-section="quran-section" class="sidebar-link flex items-center p-3 rounded-lg hover:bg-gray-700 transition-colors duration-200">
                            <svg class="w-6 h-6 ml-3" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M4 4a2 2 0 012-2h8a2 2 0 012 2v12a2 2 0 01-2 2H6a2 2 0 01-2-2V4zm2 2v10h8V6H6zm2 2h4a1 1 0 100-2H8a1 1 0 000 2zm0 4h4a1 1 0 100-2H8a1 1 0 000 2z" clip-rule="evenodd"></path></svg>
                            <span>القرآن الكريم</span>
                        </a>
                    </li>
                    <li class="mb-3">
                        <a href="#" data-section="ai-chat-section" class="sidebar-link flex items-center p-3 rounded-lg hover:bg-gray-700 transition-colors duration-200">
                            <svg class="w-6 h-6 ml-3" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M18 10c0 3.866-3.582 7-8 7a8.841 8.841 0 01-4.17-.953l-4.58 1.355a1 1 0 01-1.218-1.218l1.355-4.58A7 7 0 012 10c0-3.866 3.582-7 8-7s8 3.134 8 7zM9 9a1 1 0 000 2h2a1 1 0 100-2H9z" clip-rule="evenodd"></path></svg>
                            <span>محادثة الذكاء الاصطناعي</span>
                        </a>
                    </li>
                    <li class="mb-3">
                        <a href="#" data-section="settings-section" class="sidebar-link flex items-center p-3 rounded-lg hover:bg-gray-700 transition-colors duration-200">
                            <svg class="w-6 h-6 ml-3" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M11.49 3.17c-.38-1.16-1.57-1.16-1.95 0L8.036 6.35c-.38 1.16-.38 2.45 0 3.61l.783 2.383c.38 1.16 1.57 1.16 1.95 0l.783-2.383c.38-1.16.38-2.45 0-3.61L11.49 3.17zM14 12a1 1 0 100 2 1 1 0 000-2zm-8-3a1 1 0 100 2 1 1 0 000-2z" clip-rule="evenodd"></path></svg>
                            <span>الإعدادات</span>
                        </a>
                    </li>
                </ul>
            </nav>
            <div class="mt-auto text-sm text-gray-500">
                <p id="userIdDisplay" class="text-xs text-center"></p>
            </div>
        </aside>

        <main class="flex-1 p-8 scrollable-content">

            <section id="dashboard-section" class="content-section">
                <div class="bg-dark-gray-bg p-6 rounded-lg mb-8 shadow-xl">
                    <h2 class="text-3xl font-bold gold-text mb-4">لوحة القيادة</h2>
                    <p id="motivationalQuote" class="text-xl italic text-e0e0e0 mb-4"></p>
                    <p id="dailyTip" class="text-md mb-4"></p>
                    <p id="businessIdea" class="text-md mb-4"></p>
                    <p id="quranVerse" class="text-xl text-e0e0e0 mb-4 text-center"></p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-dark-gray-bg p-6 rounded-lg shadow-xl">
                        <h3 class="text-2xl font-semibold gold-text mb-4">مهامي اليومية</h3>
                        <div id="dailyTasksContainer">
                            <p class="text-gray-400">لا توجد مهام يومية حاليًا. أضفها من قسم المهام اليومية!</p>
                        </div>
                    </div>
                    <div class="bg-dark-gray-bg p-6 rounded-lg shadow-xl">
                        <h3 class="text-2xl font-semibold gold-text mb-4">أحدث الفيديوهات الفيروسية</h3>
                        <div id="viralVideoLinks">
                            <p class="text-gray-400">لا توجد روابط فيديو حاليًا. أضفها من الإعدادات!</p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="daily-tasks-section" class="content-section hidden">
                <div class="bg-dark-gray-bg p-6 rounded-lg mb-8 shadow-xl">
                    <h2 class="text-3xl font-bold gold-text mb-4">مهامي اليومية</h2>
                    <div id="dailyTasksContainer">
                        </div>

                    <h3 class="text-2xl font-semibold gold-text mt-8 mb-4">إضافة مهمة جديدة</h3>
                    <div class="flex flex-col md:flex-row gap-4">
                        <input type="text" id="newTaskName" placeholder="اسم المهمة (مثال: قراءة)" class="flex-1 p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50">
                        <input type="text" id="newTaskTarget" placeholder="الهدف (مثال: 30 دقيقة، 500 كلمة)" class="flex-1 p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50">
                        <select id="newTaskType" class="p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50">
                            <option value="daily">يومي</option>
                            <option value="social">اجتماعي</option>
                        </select>
                        <button id="addTaskBtn" class="p-3 gold-bg text-black-bg font-bold rounded-md hover:opacity-90 transition-opacity whitespace-nowrap">إضافة مهمة</button>
                    </div>
                </div>
            </section>

            <section id="social-media-section" class="content-section hidden">
                <div class="bg-dark-gray-bg p-6 rounded-lg mb-8 shadow-xl">
                    <h2 class="text-3xl font-bold gold-text mb-4">خطة بناء حضوري على المواقع الاجتماعية</h2>
                    <p class="text-e0e0e0 mb-4">هنا ستجد المهام اليومية المتعلقة بحضورك على السوشيال ميديا وقوالب المحتوى المقترحة.</p>
                    <h3 class="text-2xl font-semibold gold-text mb-4">مهام السوشيال ميديا</h3>
                    <div id="socialTasksContainer">
                        <p class="text-gray-400">لا توجد مهام سوشيال ميديا حاليًا. أضفها من قسم المهام اليومية (نوع اجتماعي)!</p>
                    </div>
                    <h3 class="text-2xl font-semibold gold-text mt-8 mb-4">أفكار ومحتوى فيروسي</h3>
                    <div class="bg-gray-700 p-4 rounded-md">
                        <p class="text-e0e0e0">على سبيل المثال: "ابتكر 5 قصص قصيرة تفاعلية على انستغرام هذا الأسبوع، ركز على 'خلف الكواليس' من مشروعك".</p>
                        <p class="text-e0e0e0 mt-2">يمكنك إضافة المزيد من الأفكار من قسم الإعدادات.</p>
                    </div>
                </div>
            </section>

            <section id="business-wealth-section" class="content-section hidden">
                <div class="bg-dark-gray-bg p-6 rounded-lg mb-8 shadow-xl">
                    <h2 class="text-3xl font-bold gold-text mb-4">تطوير الأعمال وبناء الثروة</h2>
                    <p class="text-e0e0e0 mb-4">كل يوم، ستجد هنا فكرة جديدة لمساعدتك في بناء وتنمية عملك وثروتك من الصفر.</p>
                    <div class="bg-gray-700 p-4 rounded-md">
                        <p id="businessIdea" class="text-xl italic text-e0e0e0"></p>
                    </div>
                </div>
            </section>

            <section id="content-library-section" class="content-section hidden">
                <div class="bg-dark-gray-bg p-6 rounded-lg mb-8 shadow-xl">
                    <h2 class="text-3xl font-bold gold-text mb-4">مكتبة المحتوى</h2>

                    <h3 class="text-2xl font-semibold gold-text mb-4">فيديوهات فيروسية ملهمة (في مجالك)</h3>
                    <div id="viralVideoLinks">
                        </div>
                    <div class="mt-6 p-4 bg-gray-700 rounded-md">
                        <h4 class="text-xl gold-text mb-2">إضافة رابط فيديو فيروسي جديد</h4>
                        <input type="text" id="newViralVideoTitle" placeholder="عنوان الفيديو" class="w-full p-3 mb-2 rounded-md bg-gray-800 text-e0e0e0 border border-gray-600 focus:border-gold-text">
                        <input type="url" id="newViralVideoUrl" placeholder="رابط الفيديو (URL)" class="w-full p-3 mb-2 rounded-md bg-gray-800 text-e0e0e0 border border-gray-600 focus:border-gold-text">
                        <button id="addViralVideoLinkBtn" class="p-3 gold-bg text-black-bg font-bold rounded-md hover:opacity-90 transition-opacity w-full">إضافة رابط فيديو</button>
                    </div>
                </div>

                <div class="bg-dark-gray-bg p-6 rounded-lg shadow-xl mt-8">
                    <h3 class="text-2xl font-semibold gold-text mb-4">مصادر لتعلم مونتاج الفيديوهات (مجانية)</h3>
                    <div id="editingTutorialsLinks">
                        </div>
                    <div class="mt-6 p-4 bg-gray-700 rounded-md">
                        <h4 class="text-xl gold-text mb-2">إضافة رابط درس مونتاج جديد</h4>
                        <input type="text" id="newEditingTutorialTitle" placeholder="عنوان الدرس" class="w-full p-3 mb-2 rounded-md bg-gray-800 text-e0e0e0 border border-gray-600 focus:border-gold-text">
                        <input type="url" id="newEditingTutorialUrl" placeholder="رابط الدرس (URL)" class="w-full p-3 mb-2 rounded-md bg-gray-800 text-e0e0e0 border border-gray-600 focus:border-gold-text">
                        <button id="addEditingTutorialLinkBtn" class="p-3 gold-bg text-black-bg font-bold rounded-md hover:opacity-90 transition-opacity w-full">إضافة رابط درس</button>
                    </div>
                </div>
            </section>

            <section id="quran-section" class="content-section hidden">
                <div class="bg-dark-gray-bg p-6 rounded-lg mb-8 shadow-xl text-center">
                    <h2 class="text-3xl font-bold gold-text mb-4">وردك اليومي من القرآن الكريم</h2>
                    <div class="bg-gray-700 p-6 rounded-md shadow-inner">
                        <p id="quranVerse" class="text-2xl italic text-e0e0e0 leading-relaxed"></p>
                    </div>
                    <p class="text-gray-400 mt-4">يمكنك تخصيص آيات الورد اليومي من قسم الإعدادات.</p>
                </div>
            </section>

            <section id="ai-chat-section" class="content-section hidden flex flex-col h-[calc(100vh-80px)]">
                <div class="bg-dark-gray-bg p-6 rounded-lg shadow-xl flex-1 flex flex-col">
                    <h2 class="text-3xl font-bold gold-text mb-4">محادثة الذكاء الاصطناعي (Gemini)</h2>
                    <div id="chatMessages" class="flex-1 overflow-y-auto p-4 bg-gray-800 rounded-lg mb-4 flex flex-col scrollable-content" style="max-height: calc(100vh - 250px);">
                        <div class="text-gray-400 text-center py-4">أهلاً بك في مساعدك الشخصي! اسألني عن أي شيء.</div>
                    </div>
                    <div id="chatLoading" class="hidden text-center text-gold-text mb-2">الذكاء الاصطناعي يفكر...</div>
                    <div class="flex">
                        <input type="text" id="chatInput" placeholder="اكتب سؤالك هنا..." class="flex-1 p-3 rounded-r-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50">
                        <button id="chatSendBtn" class="p-3 gold-bg text-black-bg font-bold rounded-l-md hover:opacity-90 transition-opacity">إرسال</button>
                    </div>
                </div>
            </section>

            <section id="settings-section" class="content-section hidden">
                <div class="bg-dark-gray-bg p-6 rounded-lg shadow-xl">
                    <h2 class="text-3xl font-bold gold-text mb-4">الإعدادات</h2>
                    <form id="settingsForm">
                        <div class="mb-6">
                            <h3 class="text-2xl font-semibold gold-text mb-3">إدارة كلمة المرور (للديمو فقط)</h3>
                            <input type="password" id="newPassword" placeholder="كلمة المرور الجديدة" class="w-full p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50 mb-2">
                            <input type="password" id="confirmPassword" placeholder="تأكيد كلمة المرور الجديدة" class="w-full p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50">
                            <p class="text-sm text-gray-500 mt-2">ملاحظة: هذه وظيفة تجريبية فقط. لا تستخدم كلمات مرور حقيقية هنا.</p>
                        </div>

                        <div class="mb-6">
                            <h3 class="text-2xl font-semibold gold-text mb-3">تخصيص المظهر</h3>
                            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                                <div>
                                    <label for="backgroundColorInput" class="block text-sm font-medium text-gray-400">لون الخلفية الرئيسي (HEX)</label>
                                    <input type="color" id="backgroundColorInput" class="w-full h-10 p-1 rounded-md bg-gray-700 border border-gray-600 cursor-pointer">
                                </div>
                                <div>
                                    <label for="textColorInput" class="block text-sm font-medium text-gray-400">لون النص الرئيسي (HEX)</label>
                                    <input type="color" id="textColorInput" class="w-full h-10 p-1 rounded-md bg-gray-700 border border-gray-600 cursor-pointer">
                                </div>
                                <div>
                                    <label for="goldColorInput" class="block text-sm font-medium text-gray-400">اللون الذهبي (HEX)</label>
                                    <input type="color" id="goldColorInput" class="w-full h-10 p-1 rounded-md bg-gray-700 border border-gray-600 cursor-pointer">
                                </div>
                            </div>
                            <p class="text-sm text-gray-500 mt-2">تغيير الألوان الرئيسية للموقع.</p>
                        </div>


                        <div class="mb-6">
                            <h3 class="text-2xl font-semibold gold-text mb-3">تخصيص المحتوى اليومي</h3>
                            <label for="quotesInput" class="block text-sm font-medium text-gray-400 mb-2">مقولات تحفيزية (مقولة لكل سطر)</label>
                            <textarea id="quotesInput" rows="5" class="w-full p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50 mb-4"></textarea>

                            <label for="tipsInput" class="block text-sm font-medium text-gray-400 mb-2">نصائح يومية (نصيحة لكل سطر)</label>
                            <textarea id="tipsInput" rows="5" class="w-full p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50 mb-4"></textarea>

                            <label for="businessIdeasInput" class="block text-sm font-medium text-gray-400 mb-2">أفكار بناء الأعمال (فكرة لكل سطر)</label>
                            <textarea id="businessIdeasInput" rows="5" class="w-full p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50 mb-4"></textarea>

                            <label for="quranVersesInput" class="block text-sm font-medium text-gray-400 mb-2">آيات قرآنية (بصيغة JSON - نص وآية)</label>
                            <textarea id="quranVersesInput" rows="7" class="w-full p-3 rounded-md bg-gray-700 text-e0e0e0 border border-gray-600 focus:border-gold-text focus:ring focus:ring-gold-text focus:ring-opacity-50 font-mono text-sm"></textarea>
                            <p class="text-sm text-gray-500 mt-2">مثال: `[{"text": "﴿فَإِنَّ مَعَ الْعُسْرِ يُسْرًا﴾", "surah": "الشرح: 5"}]`</p>
                        </div>

                        <div class="mb-6">
                            <h3 class="text-2xl font-semibold gold-text mb-3">إدارة المهام الحالية</h3>
                            <ul id="currentTasksList" class="space-y-2">
                                </ul>
                        </div>

                        <div class="mb-6">
                            <h3 class="text-2xl font-semibold gold-text mb-3">إدارة روابط الفيديوهات الفيروسية</h3>
                            <ul id="currentViralVideosList" class="space-y-2">
                                </ul>
                        </div>

                        <div class="mb-6">
                            <h3 class="text-2xl font-semibold gold-text mb-3">إدارة روابط دروس المونتاج</h3>
                            <ul id="currentEditingTutorialsList" class="space-y-2">
                                </ul>
                        </div>

                        <button type="button" id="saveSettingsBtn" class="w-full p-3 gold-bg text-black-bg font-bold rounded-md hover:opacity-90 transition-opacity text-xl">حفظ الإعدادات</button>
                    </form>
                </div>
            </section>

        </main>
    </div>

</body>
</html>
