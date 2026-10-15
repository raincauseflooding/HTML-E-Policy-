<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
    <title>Ed-surance - Private Candidate Exam Protection</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            line-height: 1.5;
            color: #000000;
            background-color: #ffffff;
            -webkit-font-smoothing: antialiased;
        }

        .survey-container {
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        .brand-header {
            text-align: center;
            margin-bottom: 1.5rem;
            border-bottom: 2px solid #000000;
            padding-bottom: 1rem;
        }

        .brand-logo {
            font-size: 1.8rem;
            font-weight: 900;
            text-transform: uppercase;
        }

        .brand-tagline {
            font-size: 0.85rem;
            color: #444444;
            text-transform: uppercase;
            font-weight: bold;
        }

        .progress-track {
            width: 100%;
            height: 6px;
            background-color: #eaeaea;
            margin-bottom: 1.5rem;
            border-radius: 3px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            width: 20%; /* Updated dynamically by JS for 5 steps */
            background-color: #000000;
            transition: width 0.2s ease-out;
        }

        .survey-card {
            display: none;
            border: 2px solid #000000;
            padding: 1.5rem;
            background-color: #ffffff;
            margin-bottom: 1.5rem;
            box-shadow: 4px 4px 0px #000000;
        }

        .survey-card.active {
            display: block;
        }

        .step-label {
            font-size: 0.8rem;
            text-transform: uppercase;
            font-weight: 700;
            color: #555555;
            margin-bottom: 0.3rem;
        }

        h2 {
            font-size: 1.35rem;
            font-weight: 800;
            margin-bottom: 1rem;
            border-bottom: 1px solid #000000;
            padding-bottom: 0.4rem;
        }

        p {
            font-size: 0.95rem;
            margin-bottom: 1rem;
        }

        /* Formal Notice Alert Box */
        .formal-warning-box {
            border: 2px solid #000000;
            background-color: #fafafa;
            padding: 1rem;
            margin-bottom: 1.2rem;
            font-size: 0.9rem;
            line-height: 1.4;
        }

        .formal-warning-title {
            font-weight: 800;
            text-transform: uppercase;
            margin-bottom: 0.3rem;
            font-size: 0.85rem;
            letter-spacing: 0.03em;
        }

        .comparison-box {
            border: 1px solid #000000;
            background-color: #f9f9f9;
            padding: 0.8rem;
            margin-bottom: 1rem;
            font-size: 0.85rem;
        }

        .comparison-title {
            font-weight: bold;
            text-transform: uppercase;
            margin-bottom: 0.4rem;
            font-size: 0.9rem;
        }

        .highlight-alert {
            background-color: #000000;
            color: #ffffff;
            padding: 0.8rem;
            font-size: 0.85rem;
            margin-bottom: 1rem;
            border-left: 5px solid #555555;
        }

        .rule-list {
            border: 1px solid #000000;
            background-color: #fcfcfc;
            padding: 0.8rem;
            margin: 1rem 0;
            font-size: 0.85rem;
        }

        .rule-row {
            margin-bottom: 0.6rem;
            display: flex;
            gap: 0.5rem;
        }

        .rule-row:last-child {
            margin-bottom: 0;
        }

        .rule-bullet {
            font-weight: bold;
        }

        /* Interactive Elements styling */
        .touch-option {
            display: flex;
            align-items: center;
            min-height: 52px;
            padding: 0.8rem;
            border: 2px solid #000000;
            margin-top: 0.8rem;
            cursor: pointer;
            touch-action: manipulation;
        }

        .touch-option:active {
            background-color: #eeeeee;
        }

        .touch-option input {
            width: 22px;
            height: 22px;
            margin-right: 0.8rem;
            accent-color: #000000;
            flex-shrink: 0;
            cursor: pointer;
        }

        .touch-text {
            display: flex;
            flex-direction: column;
            gap: 0.15rem;
        }

        .touch-title {
            font-size: 0.95rem;
            font-weight: 700;
        }

        .touch-subtitle {
            font-size: 0.8rem;
            color: #444444;
        }

        /* Form Fields Styling */
        .input-group {
            margin-top: 1rem;
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .input-group label {
            font-weight: bold;
            font-size: 0.9rem;
        }

        select, input[type="text"] {
            width: 100%;
            min-height: 44px;
            padding: 0.6rem;
            border: 2px solid #000000;
            font-size: 0.95rem;
            background-color: #ffffff;
            font-family: inherit;
        }

        /* Checkbox Grid for Subjects */
        .subject-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.8rem;
            margin-top: 0.8rem;
        }

        .subject-label {
            display: flex;
            align-items: center;
            padding: 0.6rem;
            border: 2px solid #000000;
            cursor: pointer;
            font-size: 0.9rem;
            font-weight: bold;
        }

        .subject-label input {
            margin-right: 0.6rem;
            width: 18px;
            height: 18px;
            accent-color: #000000;
        }

        /* Generator Box */
        .generator-container {
            border: 2px dashed #000000;
            padding: 1rem;
            text-align: center;
            background-color: #fafafa;
            margin-top: 1rem;
        }

        .candidate-num-display {
            font-size: 1.5rem;
            font-weight: 900;
            letter-spacing: 0.1em;
            margin: 0.8rem 0;
            font-family: monospace;
        }

        /* Controls */
        .button-bar {
            display: flex;
            gap: 0.8rem;
        }

        button {
            flex: 1;
            min-height: 48px;
            font-size: 0.95rem;
            font-weight: 700;
            border: 2px solid #000000;
            background-color: #ffffff;
            color: #000000;
            cursor: pointer;
            touch-action: manipulation;
        }

        .btn-action {
            background-color: #000000;
            color: #ffffff;
        }

        .btn-action:active {
            background-color: #222222;
        }

        button:disabled {
            border-color: #cccccc;
            color: #cccccc;
            cursor: not-allowed;
        }

        /* Output Certificate */
        .policy-output {
            display: none;
            border: 2px solid #000000;
            padding: 1.5rem;
            background-color: #ffffff;
            box-shadow: 4px 4px 0px #000000;
        }

        .policy-output.active {
            display: block;
        }

        .cert-header {
            text-align: center;
            border-bottom: 2px solid #000000;
            padding-bottom: 1rem;
            margin-bottom: 1.2rem;
        }

        .cert-title {
            font-size: 1.4rem;
            font-weight: 900;
            text-transform: uppercase;
        }

        .meta-table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 1.2rem;
            font-size: 0.85rem;
        }

        .meta-table td {
            border: 1px solid #000000;
            padding: 0.6rem;
            width: 50%;
        }

        .meta-label {
            font-size: 0.7rem;
            text-transform: uppercase;
            color: #555555;
            display: block;
            margin-bottom: 0.2rem;
        }

        .cert-clause {
            margin-bottom: 1.2rem;
            font-size: 0.85rem;
        }

        .cert-clause h3 {
            font-size: 0.95rem;
            border-bottom: 1px solid #000000;
            padding-bottom: 0.2rem;
            margin-bottom: 0.5rem;
            text-transform: uppercase;
        }

        .cert-clause ul {
            padding-left: 1.2rem;
            margin-top: 0.3rem;
        }

        .cert-clause li {
            margin-bottom: 0.3rem;
        }

        .cert-actions {
            display: flex;
            gap: 0.8rem;
            margin-top: 1.5rem;
        }

        @media (max-width: 540px) {
            .meta-table td {
                display: block;
                width: 100%;
            }
            .meta-table tr {
                display: flex;
                flex-direction: column;
            }
            .cert-actions {
                flex-direction: column;
            }
            .subject-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>

    <div class="survey-container">
        <!-- Logo Header -->
        <header class="brand-header" id="brandHeader">
            <div class="brand-logo">Ed-surance</div>
            <div class="brand-tagline">HKDSE Private Candidate Exam Protection</div>
        </header>

        <!-- Progress Tracker -->
        <div class="progress-track" id="progressTrack">
            <div class="progress-fill" id="progressFill"></div>
        </div>

        <form id="policySurvey">
            <!-- STEP 1: Context Setup -->
            <div class="survey-card active" id="step1">
                <div class="step-label">Step 1 of 5</div>
                
                <!-- Formal Notice Alert Box -->
                <div class="formal-warning-box">
                    <div class="formal-warning-title">📢 Important Notice for Parents & Students:</div>
                    If you are worried about the high costs, loss of study momentum, or missing the examination due to sudden emergencies, you can buy our protection plan to secure your peace of mind.
                </div>

                <h2>1. Why Ed-surance Exists</h2>
                <p>Global exams like IELTS or IGCSE offer refunds if you miss an exam. In contrast, the HKDSE only offers "assessed grades" to day-school students.</p>
                
                <div class="comparison-box">
                    <div class="comparison-title">❌ The Private Candidate Problem:</div>
                    If you are a private, mainland, or international student, <strong>you cannot get an assessed grade</strong> if you miss the DSE. You get an automatic "Absent" (0 score) and lose your exam fee plus a whole year of study.
                </div>

                <div class="highlight-alert">
                    🛡️ Ed-surance is the only plan that bridges this gap, providing financial safety for private candidates facing the 13% baseline absence rate.
                </div>

                <label class="touch-option">
                    <input type="checkbox" id="chk1" onchange="instantAdvance(1)">
                    <span class="touch-text">
                        <span class="touch-title">I understand my unique risks</span>
                        <span class="touch-subtitle">Tap here to view the eligibility rules.</span>
                    </span>
                </label>
            </div>

            <!-- STEP 2: Exclusion Clauses -->
            <div class="survey-card" id="step2">
                <div class="step-label">Step 2 of 5</div>
                <h2>2. When We Cannot Pay</h2>
                <p>To keep plans fair and cheap for all honest students, claims are not payable if:</p>
                
                <div class="rule-list">
                    <div class="rule-row"><span class="rule-bullet">•</span><span>Your mock exam result is below Level 2.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You have low attendance in school days or tutoring classes.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You score Level 5 or higher in the real exam.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You fail to provide valid official proof documents.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You break official exam rules (e.g., cheating).</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You miss an exam without an emergency (feeling unprepared does not count).</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You are late without an official transit delay slip.</span></div>
                </div>

                <label class="touch-option">
                    <input type="checkbox" id="chk2" onchange="instantAdvance(2)">
                    <span class="touch-text">
                        <span class="touch-title">I accept these exclusion terms</span>
                        <span class="touch-subtitle">Tap here to choose yo
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
    <title>Ed-surance - Private Candidate Exam Protection</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            line-height: 1.5;
            color: #000000;
            background-color: #ffffff;
            -webkit-font-smoothing: antialiased;
        }

        .survey-container {
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        .brand-header {
            text-align: center;
            margin-bottom: 1.5rem;
            border-bottom: 2px solid #000000;
            padding-bottom: 1rem;
        }

        .brand-logo {
            font-size: 1.8rem;
            font-weight: 900;
            text-transform: uppercase;
        }

        .brand-tagline {
            font-size: 0.85rem;
            color: #444444;
            text-transform: uppercase;
            font-weight: bold;
        }

        .progress-track {
            width: 100%;
            height: 6px;
            background-color: #eaeaea;
            margin-bottom: 1.5rem;
            border-radius: 3px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            width: 20%; /* Updated dynamically by JS for 5 steps */
            background-color: #000000;
            transition: width 0.2s ease-out;
        }

        .survey-card {
            display: none;
            border: 2px solid #000000;
            padding: 1.5rem;
            background-color: #ffffff;
            margin-bottom: 1.5rem;
            box-shadow: 4px 4px 0px #000000;
        }

        .survey-card.active {
            display: block;
        }

        .step-label {
            font-size: 0.8rem;
            text-transform: uppercase;
            font-weight: 700;
            color: #555555;
            margin-bottom: 0.3rem;
        }

        h2 {
            font-size: 1.35rem;
            font-weight: 800;
            margin-bottom: 1rem;
            border-bottom: 1px solid #000000;
            padding-bottom: 0.4rem;
        }

        p {
            font-size: 0.95rem;
            margin-bottom: 1rem;
        }

        /* Formal Notice Alert Box */
        .formal-warning-box {
            border: 2px solid #000000;
            background-color: #fafafa;
            padding: 1rem;
            margin-bottom: 1.2rem;
            font-size: 0.9rem;
            line-height: 1.4;
        }

        .formal-warning-title {
            font-weight: 800;
            text-transform: uppercase;
            margin-bottom: 0.3rem;
            font-size: 0.85rem;
            letter-spacing: 0.03em;
        }

        .comparison-box {
            border: 1px solid #000000;
            background-color: #f9f9f9;
            padding: 0.8rem;
            margin-bottom: 1rem;
            font-size: 0.85rem;
        }

        .comparison-title {
            font-weight: bold;
            text-transform: uppercase;
            margin-bottom: 0.4rem;
            font-size: 0.9rem;
        }

        .highlight-alert {
            background-color: #000000;
            color: #ffffff;
            padding: 0.8rem;
            font-size: 0.85rem;
            margin-bottom: 1rem;
            border-left: 5px solid #555555;
        }

        .rule-list {
            border: 1px solid #000000;
            background-color: #fcfcfc;
            padding: 0.8rem;
            margin: 1rem 0;
            font-size: 0.85rem;
        }

        .rule-row {
            margin-bottom: 0.6rem;
            display: flex;
            gap: 0.5rem;
        }

        .rule-row:last-child {
            margin-bottom: 0;
        }

        .rule-bullet {
            font-weight: bold;
        }

        /* Interactive Elements styling */
        .touch-option {
            display: flex;
            align-items: center;
            min-height: 52px;
            padding: 0.8rem;
            border: 2px solid #000000;
            margin-top: 0.8rem;
            cursor: pointer;
            touch-action: manipulation;
        }

        .touch-option:active {
            background-color: #eeeeee;
        }

        .touch-option input {
            width: 22px;
            height: 22px;
            margin-right: 0.8rem;
            accent-color: #000000;
            flex-shrink: 0;
            cursor: pointer;
        }

        .touch-text {
            display: flex;
            flex-direction: column;
            gap: 0.15rem;
        }

        .touch-title {
            font-size: 0.95rem;
            font-weight: 700;
        }

        .touch-subtitle {
            font-size: 0.8rem;
            color: #444444;
        }

        /* Form Fields Styling */
        .input-group {
            margin-top: 1rem;
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .input-group label {
            font-weight: bold;
            font-size: 0.9rem;
        }

        select, input[type="text"] {
            width: 100%;
            min-height: 44px;
            padding: 0.6rem;
            border: 2px solid #000000;
            font-size: 0.95rem;
            background-color: #ffffff;
            font-family: inherit;
        }

        /* Checkbox Grid for Subjects */
        .subject-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.8rem;
            margin-top: 0.8rem;
        }

        .subject-label {
            display: flex;
            align-items: center;
            padding: 0.6rem;
            border: 2px solid #000000;
            cursor: pointer;
            font-size: 0.9rem;
            font-weight: bold;
        }

        .subject-label input {
            margin-right: 0.6rem;
            width: 18px;
            height: 18px;
            accent-color: #000000;
        }

        /* Generator Box */
        .generator-container {
            border: 2px dashed #000000;
            padding: 1rem;
            text-align: center;
            background-color: #fafafa;
            margin-top: 1rem;
        }

        .candidate-num-display {
            font-size: 1.5rem;
            font-weight: 900;
            letter-spacing: 0.1em;
            margin: 0.8rem 0;
            font-family: monospace;
        }

        /* Controls */
        .button-bar {
            display: flex;
            gap: 0.8rem;
        }

        button {
            flex: 1;
            min-height: 48px;
            font-size: 0.95rem;
            font-weight: 700;
            border: 2px solid #000000;
            background-color: #ffffff;
            color: #000000;
            cursor: pointer;
            touch-action: manipulation;
        }

        .btn-action {
            background-color: #000000;
            color: #ffffff;
        }

        .btn-action:active {
            background-color: #222222;
        }

        button:disabled {
            border-color: #cccccc;
            color: #cccccc;
            cursor: not-allowed;
        }

        /* Output Certificate */
        .policy-output {
            display: none;
            border: 2px solid #000000;
            padding: 1.5rem;
            background-color: #ffffff;
            box-shadow: 4px 4px 0px #000000;
        }

        .policy-output.active {
            display: block;
        }

        .cert-header {
            text-align: center;
            border-bottom: 2px solid #000000;
            padding-bottom: 1rem;
            margin-bottom: 1.2rem;
        }

        .cert-title {
            font-size: 1.4rem;
            font-weight: 900;
            text-transform: uppercase;
        }

        .meta-table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 1.2rem;
            font-size: 0.85rem;
        }

        .meta-table td {
            border: 1px solid #000000;
            padding: 0.6rem;
            width: 50%;
        }

        .meta-label {
            font-size: 0.7rem;
            text-transform: uppercase;
            color: #555555;
            display: block;
            margin-bottom: 0.2rem;
        }

        .cert-clause {
            margin-bottom: 1.2rem;
            font-size: 0.85rem;
        }

        .cert-clause h3 {
            font-size: 0.95rem;
            border-bottom: 1px solid #000000;
            padding-bottom: 0.2rem;
            margin-bottom: 0.5rem;
            text-transform: uppercase;
        }

        .cert-clause ul {
            padding-left: 1.2rem;
            margin-top: 0.3rem;
        }

        .cert-clause li {
            margin-bottom: 0.3rem;
        }

        .cert-actions {
            display: flex;
            gap: 0.8rem;
            margin-top: 1.5rem;
        }

        @media (max-width: 540px) {
            .meta-table td {
                display: block;
                width: 100%;
            }
            .meta-table tr {
                display: flex;
                flex-direction: column;
            }
            .cert-actions {
                flex-direction: column;
            }
            .subject-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>

    <div class="survey-container">
        <!-- Logo Header -->
        <header class="brand-header" id="brandHeader">
            <div class="brand-logo">Ed-surance</div>
            <div class="brand-tagline">HKDSE Private Candidate Exam Protection</div>
        </header>

        <!-- Progress Tracker -->
        <div class="progress-track" id="progressTrack">
            <div class="progress-fill" id="progressFill"></div>
        </div>

        <form id="policySurvey">
            <!-- STEP 1: Context Setup -->
            <div class="survey-card active" id="step1">
                <div class="step-label">Step 1 of 5</div>
                
                <!-- Formal Notice Alert Box -->
                <div class="formal-warning-box">
                    <div class="formal-warning-title">📢 Important Notice for Parents & Students:</div>
                    If you are worried about the high costs, loss of study momentum, or missing the examination due to sudden emergencies, you can buy our protection plan to secure your peace of mind.
                </div>

                <h2>1. Why Ed-surance Exists</h2>
                <p>Global exams like IELTS or IGCSE offer refunds if you miss an exam. In contrast, the HKDSE only offers "assessed grades" to day-school students.</p>
                
                <div class="comparison-box">
                    <div class="comparison-title">❌ The Private Candidate Problem:</div>
                    If you are a private, mainland, or international student, <strong>you cannot get an assessed grade</strong> if you miss the DSE. You get an automatic "Absent" (0 score) and lose your exam fee plus a whole year of study.
                </div>

                <div class="highlight-alert">
                    🛡️ Ed-surance is the only plan that bridges this gap, providing financial safety for private candidates facing the 13% baseline absence rate.
                </div>

                <label class="touch-option">
                    <input type="checkbox" id="chk1" onchange="instantAdvance(1)">
                    <span class="touch-text">
                        <span class="touch-title">I understand my unique risks</span>
                        <span class="touch-subtitle">Tap here to view the eligibility rules.</span>
                    </span>
                </label>
            </div>

            <!-- STEP 2: Exclusion Clauses -->
            <div class="survey-card" id="step2">
                <div class="step-label">Step 2 of 5</div>
                <h2>2. When We Cannot Pay</h2>
                <p>To keep plans fair and cheap for all honest students, claims are not payable if:</p>
                
                <div class="rule-list">
                    <div class="rule-row"><span class="rule-bullet">•</span><span>Your mock exam result is below Level 2.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You have low attendance in school days or tutoring classes.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You score Level 5 or higher in the real exam.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You fail to provide valid official proof documents.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You break official exam rules (e.g., cheating).</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You miss an exam without an emergency (feeling unprepared does not count).</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You are late without an official transit delay slip.</span></div>
                </div>

                <label class="touch-option">
                    <input type="checkbox" id="chk2" onchange="instantAdvance(2)">
                    <span class="touch-text">
                        <span class="touch-title">I accept these exclusion terms</span>
                        <span class="touch-subtitle">Tap here to choose yo
