<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
    <title>Ed-surance - Simple Exam Protection</title>
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
            width: 25%;
            background-color: #000000;
            transition: width 0.25s ease-out;
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

        button:active:not(:disabled) {
            transform: translateY(1px);
        }

        .btn-action {
            background-color: #000000;
            color: #ffffff;
        }

        .btn-action:active {
            background-color: #222222;
        }

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
        }

        @media print {
            .brand-header, .progress-track, #policySurvey, .cert-actions {
                display: none !important;
            }
            .policy-output {
                display: block !important;
                border: none !important;
                box-shadow: none !important;
                padding: 0 !important;
            }
        }
    </style>
</head>
<body>

    <div class="survey-container">
        <header class="brand-header" id="brandHeader">
            <div class="brand-logo">Ed-surance</div>
            <div class="brand-tagline">HKDSE Exam Protection Plan</div>
        </header>

        <div class="progress-track" id="progressTrack">
            <div class="progress-fill" id="progressFill"></div>
        </div>

        <form id="policySurvey">
            <!-- STEP 1 -->
            <div class="survey-card active" id="step1">
                <div class="step-label">Step 1 of 4</div>
                <h2>1. Welcome to Ed-surance</h2>
                <p>We protect students from unexpected exam issues. Check the box below to start.</p>
                
                <label class="touch-option">
                    <input type="checkbox" id="chk1" onchange="autoAdvance(1)">
                    <span class="touch-text">
                        <span class="touch-title">I want to read the rules</span>
                        <span class="touch-subtitle">Tap here to go to the next step.</span>
                    </span>
                </label>
            </div>

            <!-- STEP 2 -->
            <div class="survey-card" id="step2">
                <div class="step-label">Step 2 of 4</div>
                <h2>2. When we cannot pay</h2>
                <p>To keep this plan fair and cheap for everyone, we cannot pay claims if:</p>
                
                <div class="rule-list">
                    <div class="rule-row"><span class="rule-bullet">•</span><span>Your mock exam result is below Level 2.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You miss too many school days or tutor classes.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You score Level 5 or higher in the real exam.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You do not give us clear, official proof.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You break official exam rules (like cheating).</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You skip exams just because you feel unprepared.</span></div>
                    <div class="rule-row"><span class="rule-bullet">•</span><span>You are late but have no official transport delays.</span></div>
                </div>

                <label class="touch-option">
                    <input type="checkbox" id="chk2" onchange="autoAdvance(2)">
                    <span class="touch-text">
                        <span class="touch-title">I understand these rules</span>
                        <span class="touch-subtitle">Tap here to choose your plan.</span>
                    </span>
                </label>
            </div>

            <!-- STEP 3 -->
            <div class="survey-card" id="step3">
                <div class="step-label">Step 3 of 4</div>
                <h2>3. Choose Your Plan</h2>
                <p>Pick the best level of protection for your needs:</p>
                
                <label class="touch-option">
                    <input type="radio" name="planChoice" value="Basic" onclick="autoAdvance(3)">
                    <span class="touch-text">
                        <span class="touch-title">Basic Plan — \$65</span>
                        <span class="touch-subtitle">Covers Exam Fees (Max payout: \$3,000)</span>
                    </span>
                </label>

                <label class="touch-option">
                    <input type="radio" name="planChoice" value="Premium" onclick="autoAdvance(3)">
                    <span class="touch-text">
                        <span class="touch-title">Premium Plan — \$210</span>
                        <span class="touch-subtitle">Covers Exam & Tuition Fees (Max payout: \$10,000)</span>
                    </span>
                </label>
            </div>

            <!-- STEP 4 -->
            <div class="survey-card" id="step4">
                <div class="step-label">Step 4 of 4</div>
                <h2>4. Get Your Document</h2>
                <p>We do not collect any personal data or email addresses. Click below to show your policy.</p>
                
                <label class="touch-option">
                    <input type="checkbox" id="chk4" onchange="autoAdvance(4)">
                    <span class="touch-text">
                        <span class="touch-title">Create my E-Policy Contract</span>
                        <span class="touch-subtitle">Builds the certificate instantly on your screen.</span>
                    </span>
                </label>
            </div>

            <div class="button-bar">
                <button type="button" id="btnBack" onclick="stepChange(-1)" disabled>Go Back</button>
            </div>
        </form>

        <section id="policyDisplay" class="policy-output">
            <header class="cert-header">
                <h1 class="cert-title">Ed-surance Policy</h1>
                <p>HKDSE Protection Agreement</p>
            </header>

            <table class="meta-table">
                <tr>
                    <td>
                        <span class="meta-label">Your Plan</span>
                        <strong id="outPlan">-</strong>
                    </td>
                    <td>
                        <span class="meta-label">Cost</span>
                        <strong id="outFee">-</strong>
                    </td>
                </tr>
                <tr>
                    <td>
                        <span class="meta-label">Max Claim Limit</span>
                        <strong id="outCap">-</strong>
                    </td>
                    <td>
                        <span class="meta-label">Active Since</span>
                        <span id="outDate">-</span>
                    </td>
                </tr>
            </table>

            <div class="cert-clause">
                <h3>1. What we cover</h3>
                <p id="outDesc">-</p>
            </div>

            <div class="cert-clause">
                <h3>2. Policy Rules (No Pay Cases)</h3>
                <ul>
                    <li>Mock results below Level 2.</li>
                    <li>Low attendance in classes or tutoring.</li>
                    <li>Scoring Level 5 or higher in the real exam.</li>
                    <li>Failing to provide official proof documents.</li>
                    <li>Breaking official exam rules.</li>
                    <li>Skipping exams without a valid emergency.</li>
                    <li>Lateness without official transit logs.</li>
                </ul>
            </div>

            <div class="cert-clause">
                <h3>3. Safe & Private</h3>
                <p>This contract is generated on your own phone or computer. No personal details are saved online.</p>
            </div>

            <div class="cert-actions">
                <button type="button" class="btn-action" onclick="window.print()">Print / Save PDF</button>
                <button type="button" onclick="restartSurvey()">Start Over</butto
