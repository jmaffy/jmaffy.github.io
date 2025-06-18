<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pomodoro Timer</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Inter Font -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #1a202c; /* Dark background */
            color: #e2e8f0; /* Light text */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
            box-sizing: border-box;
        }
        .container {
            background-color: #2d3748; /* Slightly lighter dark for container */
            border-radius: 1.5rem; /* More rounded corners */
            padding: 2.5rem; /* Increased padding */
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05); /* Subtle shadow */
            max-width: 500px;
            width: 100%;
            text-align: center;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }
        .timer-display {
            font-size: 4.5rem; /* Larger font size for timer */
            font-weight: 700;
            margin-bottom: 1rem;
            color: #63b3ed; /* Blue color for timer */
        }
        .session-info {
            font-size: 1.25rem; /* Slightly larger for session info */
            margin-bottom: 1.5rem;
            color: #cbd5e0;
        }
        .controls button {
            background-color: #4299e1; /* Blue for buttons */
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 0.75rem; /* Rounded button corners */
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.2s ease-in-out, transform 0.1s ease-in-out;
            margin: 0.5rem; /* Space between buttons */
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
        .controls button:hover {
            background-color: #3182ce; /* Darker blue on hover */
            transform: translateY(-2px);
        }
        .controls button:active {
            transform: translateY(0);
            box-shadow: none;
        }
        .controls button:disabled {
            background-color: #607d8b; /* Gray for disabled buttons */
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        .pomodoro-count {
            font-size: 1rem;
            margin-top: 1rem;
            color: #a0aec0;
        }

        /* Responsive adjustments */
        @media (max-width: 600px) {
            .timer-display {
                font-size: 3.5rem;
            }
            .controls button {
                padding: 0.6rem 1.2rem;
                font-size: 0.9rem;
                margin: 0.4rem;
            }
            .container {
                padding: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="text-3xl font-bold mb-4 text-white">Pomodoro Timer</h1>
        <div id="timer" class="timer-display">25:00</div>
        <div id="session-info" class="session-info">Work Session</div>
        <div id="pomodoro-count" class="pomodoro-count">Pomodoros Completed: 0</div>
        <div class="controls flex justify-center flex-wrap">
            <button id="start-btn">Start</button>
            <button id="pause-btn" disabled>Pause</button>
            <button id="reset-btn">Reset</button>
        </div>
    </div>

    <script>
        // Get DOM elements
        const timerDisplay = document.getElementById('timer');
        const sessionInfo = document.getElementById('session-info');
        const pomodoroCountDisplay = document.getElementById('pomodoro-count');
        const startBtn = document.getElementById('start-btn');
        const pauseBtn = document.getElementById('pause-btn');
        const resetBtn = document.getElementById('reset-btn');

        // Timer variables
        let totalSeconds;
        let intervalId;
        let isPaused = true;
        let isWorkSession = true;
        let pomodoroCount = 0;

        // Session durations in seconds
        const WORK_DURATION = 25 * 60; // 25 minutes
        const SHORT_BREAK_DURATION = 5 * 60; // 5 minutes
        const LONG_BREAK_DURATION = 15 * 60; // 15 minutes (can be 15-30 as per document)
        const POMODOROS_FOR_LONG_BREAK = 4;

        /**
         * Initializes the timer to the work session duration.
         */
        function initializeTimer() {
            totalSeconds = WORK_DURATION;
            isWorkSession = true;
            sessionInfo.textContent = 'Work Session';
            updateDisplay();
            pomodoroCountDisplay.textContent = `Pomodoros Completed: ${pomodoroCount}`;
        }

        /**
         * Updates the timer display (MM:SS format).
         */
        function updateDisplay() {
            const minutes = Math.floor(totalSeconds / 60);
            const seconds = totalSeconds % 60;
            timerDisplay.textContent = `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
        }

        /**
         * Plays a sound when a session ends.
         */
        function playAlarm() {
            const audioContext = new (window.AudioContext || window.webkitAudioContext)();
            const oscillator = audioContext.createOscillator();
            const gainNode = audioContext.createGain();

            oscillator.connect(gainNode);
            gainNode.connect(audioContext.destination);

            oscillator.type = 'sine';
            oscillator.frequency.setValueAtTime(440, audioContext.currentTime); // A4 note
            gainNode.gain.setValueAtTime(0, audioContext.currentTime);
            gainNode.gain.linearRampToValueAtTime(0.5, audioContext.currentTime + 0.1);
            gainNode.gain.linearRampToValueAtTime(0, audioContext.currentTime + 0.5);

            oscillator.start();
            oscillator.stop(audioContext.currentTime + 0.5);
        }

        /**
         * Handles the logic for switching between work and break sessions.
         */
        function switchSession() {
            playAlarm(); // Play alarm when session ends

            if (isWorkSession) {
                pomodoroCount++;
                pomodoroCountDisplay.textContent = `Pomodoros Completed: ${pomodoroCount}`;

                if (pomodoroCount % POMODOROS_FOR_LONG_BREAK === 0) {
                    totalSeconds = LONG_BREAK_DURATION;
                    sessionInfo.textContent = 'Long Break!';
                } else {
                    totalSeconds = SHORT_BREAK_DURATION;
                    sessionInfo.textContent = 'Short Break!';
                }
            } else {
                totalSeconds = WORK_DURATION;
                sessionInfo.textContent = 'Work Session';
            }
            isWorkSession = !isWorkSession;
            updateDisplay();
        }

        /**
         * Main timer logic, called every second.
         */
        function timerTick() {
            if (totalSeconds <= 0) {
                clearInterval(intervalId);
                switchSession();
                // Automatically start next session after a short delay
                // to allow alarm to finish and UI to update
                setTimeout(() => {
                    if (!isPaused) { // Only auto-start if not manually paused
                        startTimer();
                    }
                }, 1000);
            } else {
                totalSeconds--;
                updateDisplay();
            }
        }

        /**
         * Starts or resumes the timer.
         */
        function startTimer() {
            if (isPaused) {
                isPaused = false;
                intervalId = setInterval(timerTick, 1000);
                startBtn.disabled = true;
                pauseBtn.disabled = false;
            }
        }

        /**
         * Pauses the timer.
         */
        function pauseTimer() {
            if (!isPaused) {
                isPaused = true;
                clearInterval(intervalId);
                startBtn.disabled = false;
                pauseBtn.disabled = true;
            }
        }

        /**
         * Resets the timer to its initial state.
         */
        function resetTimer() {
            clearInterval(intervalId);
            isPaused = true;
            pomodoroCount = 0;
            initializeTimer();
            startBtn.disabled = false;
            pauseBtn.disabled = true;
        }

        // Event Listeners
        startBtn.addEventListener('click', startTimer);
        pauseBtn.addEventListener('click', pauseTimer);
        resetBtn.addEventListener('click', resetTimer);

        // Initialize the timer when the page loads
        window.onload = initializeTimer;
    </script>
</body>
</html>
