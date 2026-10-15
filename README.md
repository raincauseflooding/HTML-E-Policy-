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
            width: 25%;
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
    </style>
</head>
<body>

    <div class="survey-container">
        <header class="brand-header" id="brandHeader">
            <div class="brand-logo">Ed-surance</div>
            <div class="brand-tagline">Private Candidate Exam Protection</div>
        </header>

        <div class="progress-track" id="progressTrack">
            <div class="progress-fill" id="progressFill"></div>
        </div>

        <form id="policySurvey">
            <!-- STEP 1 -->
            <div class="survey-card active" id="step1">
                <div class="step-label">Step 1 of 4</div>
                <h2>1. Why Private Candidates Need Protection</h2>
                <p>Private, mainland, and non-local candidates <strong>cannot get assessed grades</strong> from the HKEAA. If you miss an exam, you forfeit your registration fees, your university placement, and a full year of tuition to retake.</p>
                
                <div class="highlight-alert">
                    ⚠️ Private candidates face an average 13% absence rate. Ed-surance is designed to secure you against this financial loss.
                </div>

                <label class="touch-option">
                    <input type="checkbox" id="chk1" onchange="instantAdvance(1)">
                    <span class="touch-text">
                        <span class="touch-title">I understand my unique risks</span>
                        <span class="touch-subtitle">Tap here to view the eligibility rules.</span>
                    </span>
                </label>
            </div>

            <!-- STEP 2 -->
            <div class="survey-card" id="step2">
                <div class="step-label">Step 2 of 4</div>
                <h2>2. When We Cannot Pay</h2>
                <p>To keep plans fair and affordable for all honest students, claims are not payable if:</p>
                
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
                        <span class="touch-subtitle">Tap here to choose your plan.</span>
                    </span>
                </label>
            </div>

            <!-- STEP 3 -->
            <div class="survey-card" id="step3">
                <div class="step-label">Step 3 of 4</div>
                <h2>3. Choose Your Plan</h2>
                <p>Select your protection level:</p>
                
                <label class="touch-option">
                    <input type="radio" name="planChoice" value="Basic" onclick="instantAdvance(3)">
                    <span class="touch-text">
                        <span class="touch-title">Basic Plan — $65</span>
                        <span class="touch-subtitle">Covers Exam Fees only (Max claim payout: $3,000)</span>
                    </span>
                </label>

                <label class="touch-option">
                    <input type="radio" name="planChoice" value="Premium" onclick="instantAdvance(3)">
                    <span class="touch-text">
                        <span class="touch-title">Premium Partner Plan — $300</span>
                        <span class="touch-subtitle">Covers Exam & Retaker Tuition Vouchers (Max claim payout: $10,000)</span>
                    </span>
                </label>
            </div>

            <!-- STEP 4 -->
            <div class="survey-card" id="step4">
                <div class="step-label">Step 4 of 4</div>
                <h2>4. Generate Document</h2>
                <p>No personal identity or email records are collected. Tap below to build your agreement immediately.</p>
                
                <label class="touch-option">
                    <input type="checkbox" id="chk4" onchange="instantAdvance(4)">
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
                <p>Private Candidate Protection Agreement</p>
            </header>

            <table class="meta-table">
                <tr>
                    <td>
                        <span class="meta-label">Selected Tier</span>
                        <strong id="outPlan">-</strong>
                    </td>
                    <td>
                        <span class="meta-label">Premium Charged</span>
                        <strong id="outFee">-</strong>
                    </td>
                </tr>
                <tr>
                    <td>
                        <span class="meta-label">Max Claim Ceiling</span>
                        <strong id="outCap">-</strong>
                    </td>
                    <td>
                        <span class="meta-label">Active Since</span>
                        <span id="outDate">-</span>
                    </td>
                </tr>
            </table>

            <div class="cert-clause">
                <h3>1. Covered Benefit Details</h3>
                <p id="outDesc">-</p>
            </div>

            <div class="cert-clause">
                <h3>2. Binding Exclusion Rules</h3>
                <ul>
                    <li>Mock results below Level 2 forfeit claims.</li>
                    <li>Low attendance records cancel plan eligibility.</li>
                    <li>Achieving Level 5 or higher places performance outside claim bounds.</li>
                    <li>Missing official proof or hospital documentation voids claims.</li>
                    <li>Direct violation of HKEAA exam rules invalidates coverage.</li>
                    <li>Voluntary absence without verifiable medical records is excluded.</li>
                    <li>Lateness without official transit delay logs is ineligible.</li>
                </ul>
            </div>

            <div class="cert-clause">
                <h3>3. Privacy & Device Issuance</h3>
                <p>This policy contract was generated strictly in your client runtime. No personal records, names, or emails have been uploaded or retained on external servers.</p>
            </div>

            <div class="cert-actions">
                <button type="button" class="btn-action" onclick="restartSurvey()">Start Over</button>
            </div>
        </section>
    </div>

    <script>
        let step = 1;
        const total = 4;

        function refreshProgress() {
            document.getElementById('progressFill').style.width = ((step / total) * 100) + '%';
        }

        function instantAdvance(currentStep) {
            if (currentStep === total) {
                renderPolicy();
            } else {
                stepChange(1);
            }
        }

        function stepChange(delta) {
            document.getElementById('step' + step).classList.remove('active');
            step += delta;
            document.getElementById('step' + step).classList.add('active');

            document.getElementById('btnBack').disabled = (step === 1);
            refreshProgress();
        }

        function renderPolicy() {
            let selected = 'Basic';
            const radios = document.getElementsByName('planChoice');
            for (let r of radios) {
                if (r.checked) { selected = r.value; break; }
            }

            const outPlan = document.getElementById('outPlan');
            const outFee = document.getElementById('outFee');
            const outCap = document.getElementById('outCap');
            const outDesc = document.getElementById('outDesc');

            if (selected === 'Basic') {
                outPlan.textContent = 'Basic Protection';
                outFee.textContent = '$65 HKD';
                outCap.textContent = '$3,000 HKD Max';
                outDesc.textContent = 'Reimburses official HKDSE registration examination fees paid directly to the examination authority.';
            } else {
                outPlan.textContent = 'Premium Partner Plan';
                outFee.textContent = '$300 HKD';
                outCap.textContent = '$10,000 HKD Max';
                outDesc.textContent = 'Reimburses up to $3,000 HKD for exam fees and issues up to $7,000 HKD in retake tuition vouchers through partner tutoring centres.';
            }

            document.getElementById('outDate').textContent = new Date().toLocaleString();

            document.getElementById('brandHeader').style.display = 'none';
            document.getElementById('progressTrack').style.display = 'none';
            document.getElementById('policySurvey').style.display = 'none';
            document.getElementById('policyDisplay').classList.add('active');
        }

        function restartSurvey() {
            document.getElementById('policySurvey').reset();
            document.getElementById('policyDisplay').classList.remove('active');
            document.getElementById('brandHeader').style.display = 'block';
            document.getElementById('progressTrack').style.display = 'block';
            document.getElementById('policySurvey').style.display = 'block';

            document.getElementById('step' + step).classList.remove('active');
            step = 1;
            document.getElementById('step1').classList.add('active');

            document.getElementById('btnBack').disabled = true;
            refreshProgress();
        }
    </script>
</body>
</html>
