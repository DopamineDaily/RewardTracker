<script>
    let dailyStats = {
        quick: 0,
        low: 0,
        big: 0,
        total: 0,
        mood: null,
        date: new Date().toDateString()
    };

    let weeklyData = [];
    let activityLog = [];

    // DOM references
    const customInput = document.getElementById('customReward');
    const customCategorySelect = document.createElement('select');
    customCategorySelect.id = "customCategory";
    ['quick', 'low', 'big'].forEach(val => {
        const opt = document.createElement('option');
        opt.value = val;
        opt.textContent = ({
            quick: 'Quick Wins',
            low: 'Low Energy',
            big: 'Big Boosts'
        })[val];
        customCategorySelect.appendChild(opt);
    });
    document.querySelector('.add-custom').insertBefore(customCategorySelect, customInput);

    function toggleReward(checkbox, category) {
        const isChecked = checkbox.classList.contains('checked');
        const countElement = checkbox.parentElement.querySelector('.reward-count');
        const rewardText = checkbox.parentElement.querySelector('.reward-text').textContent;

        if (isChecked) {
            checkbox.classList.remove('checked');
            const currentCount = parseInt(countElement.textContent);
            countElement.textContent = Math.max(0, currentCount - 1);
            dailyStats[category] = Math.max(0, dailyStats[category] - 1);
            dailyStats.total = Math.max(0, dailyStats.total - 1);
            activityLog = activityLog.filter(log => log.reward !== rewardText || log.timestamp !== getLastTimestamp(rewardText));
        } else {
            checkbox.classList.add('checked');
            const currentCount = parseInt(countElement.textContent);
            countElement.textContent = currentCount + 1;
            dailyStats[category]++;
            dailyStats.total++;

            const now = new Date();
            activityLog.unshift({
                reward: rewardText,
                category: category,
                timestamp: now.toLocaleTimeString(),
                mood: dailyStats.mood
            });
        }

        updateStats();
        updateActivityLog();
        saveData();

        setTimeout(() => checkbox.classList.remove('checked'), 1000);
    }

    function getLastTimestamp(rewardText) {
        const log = activityLog.find(l => l.reward === rewardText);
        return log ? log.timestamp : null;
    }

    function selectMood(button, mood) {
        document.querySelectorAll('.mood-button').forEach(btn => btn.classList.remove('selected'));
        button.classList.add('selected');
        dailyStats.mood = mood;
        updateStats();
        saveData();
    }

    function addCustomReward() {
        const text = customInput.value.trim();
        const category = customCategorySelect.value;
        if (!text) return;

        const categorySection = document.querySelector(`.category h2:contains(${customCategorySelect.options[customCategorySelect.selectedIndex].text})`)?.parentElement;
        const fallbackSection = {
            quick: document.querySelectorAll('.category')[0],
            low: document.querySelectorAll('.category')[1],
            big: document.querySelectorAll('.category')[2]
        }[category];

        const targetSection = categorySection || fallbackSection;
        const newReward = document.createElement('div');
        newReward.className = 'reward-item';
        newReward.innerHTML = `
            <div class="reward-checkbox" onclick="toggleReward(this, '${category}')"></div>
            <div class="reward-text">${text}</div>
            <div class="reward-count">0</div>
        `;
        targetSection.appendChild(newReward);
        customInput.value = '';
        saveData();
    }

    function updateStats() {
        document.getElementById('totalToday').textContent = dailyStats.total;

        const weekTotal = weeklyData.reduce((sum, day) => sum + day.total, 0) + dailyStats.total;
        const weekAverage = Math.round(weekTotal / Math.max(1, weeklyData.length + 1));
        document.getElementById('weeklyAverage').textContent = weekAverage;

        const categories = {
            'Quick Wins': dailyStats.quick,
            'Low Energy': dailyStats.low,
            'Big Boosts': dailyStats.big
        };
        const favorite = Object.keys(categories).reduce((a, b) => categories[a] > categories[b] ? a : b);
        document.getElementById('favoriteCategory').textContent = categories[favorite] > 0 ? favorite : '-';

        document.getElementById('currentStreak').textContent = dailyStats.total > 0 ? '1' : '0';
    }

    function updateActivityLog() {
        const logElement = document.getElementById('activityLog');
        logElement.innerHTML = '';

        activityLog.slice(0, 10).forEach(entry => {
            const logItem = document.createElement('div');
            logItem.className = 'log-entry';

            const categoryEmoji = {
                'quick': '⚡',
                'low': '🌙',
                'big': '🔥'
            };

            logItem.innerHTML = `
                <div class="log-time">${entry.timestamp}</div>
                <div class="log-content">${categoryEmoji[entry.category]} ${entry.reward}</div>
            `;
            logElement.appendChild(logItem);
        });
    }

    function resetDaily() {
        if (confirm('Are you sure you want to reset today\'s progress?')) {
            weeklyData.push({ ...dailyStats }); // Log yesterday
            dailyStats = {
                quick: 0,
                low: 0,
                big: 0,
                total: 0,
                mood: null,
                date: new Date().toDateString()
            };
            document.querySelectorAll('.reward-checkbox').forEach(cb => cb.classList.remove('checked'));
            document.querySelectorAll('.reward-count').forEach(count => count.textContent = '0');
            document.querySelectorAll('.mood-button').forEach(btn => btn.classList.remove('selected'));

            activityLog = [];
            updateStats();
            updateActivityLog();
            saveData();
        }
    }

    function saveData() {
        localStorage.setItem('dopamineData', JSON.stringify({
            dailyStats,
            weeklyData,
            activityLog
        }));
        localStorage.setItem('dopamineDate', dailyStats.date);
    }

    function loadData() {
        const saved = JSON.parse(localStorage.getItem('dopamineData'));
        const savedDate = localStorage.getItem('dopamineDate');

        if (saved) {
            if (savedDate !== new Date().toDateString()) {
                // Push previous day to weeklyData
                weeklyData = saved.weeklyData || [];
                weeklyData.push(saved.dailyStats);
                dailyStats = {
                    quick: 0,
                    low: 0,
                    big: 0,
                    total: 0,
                    mood: null,
                    date: new Date().toDateString()
                };
                activityLog = [];
            } else {
                dailyStats = saved.dailyStats;
                weeklyData = saved.weeklyData || [];
                activityLog = saved.activityLog || [];
            }
        }
    }

    // Init
    loadData();
    updateStats();
    updateActivityLog();
</script>
