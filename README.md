<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
    <title>Ed-surance - Interactive Policy & Certificate</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            line-height: 1.5;
            color: #000000;
            background-color: #ffffff;
            -webkit-font-smoothing: antialiased;
        }

        .survey-container {
            width: 100%;
            max-width: 720px;
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
            letter-spacing: -0.02em;
            text-transform: uppercase;
        }

        .brand-tagline {
            font-size: 0.85rem;
            color: #444444;
            text-transform: uppercase;
            letter-spacing: 0.05em;
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

        .exclusion-box {
            border: 1px solid #000000;
            background-color: #fcfcfc;
            padding: 0.8rem;
            margin: 1rem 0;
            font-size: 0.85rem;
        }

        .exclusion-row {
            margin-bottom: 0.6rem;
            display: flex;
            gap: 0.5rem;
        }

        .exclusion-row:last-child {
            margin-bottom: 0;
        }

        .exclusion-bullet {
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
            transition: background-color 0.15s ease;
        }

        button:active:not(:disabled) {
            transform: translateY(1px);
        }

        button:disabled {
            border-color: #cccccc;
            color: #cccccc;
            cursor: not-allowed;
        }

        .btn-action {
            background-color: #000000;
            color: #ffffff;
        }

        .btn-action:active:not(:disabled) {
            background-color: #222222;
        }

        button:focus-visible, 
        input:focus-visible, 
        .touch-option:focus-within {
            outline: 3px solid #000000;
            outline-offset: 2px;
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
            vertical-align: top;
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
            body {
                background: #ffffff;
            }
            .survey-container {
                max-width: 100%;
                padding: 0;
            }
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
            <div class="survey-card active" id="step1">
                <div class="step-label">Step 1 of 4</div>
                <h2>1. Scope & Intent</h2>
                <p>Ed-surance provides exam risk protection for HKDSE candidates. Tap the checkbox below to begin review.</p>
                
                <label class="touch-option">
                    <input type="checkbox" id="chk1" onchange="runValidation(1)">
                    <span class="touch-text">
                        <span class="touch-title">I understand the plan objective</span>
                        <span class="touch-subtitle">Confirms understanding of structural exam protection.</span>
                    </span>
                </label>
            </div>

            <div class="survey-card" id="step2">
                <div class="step-label">Step 2 of 4</div>
                <h2>2. Eligibility & Exclusions</h2>
                <p>To prevent moral hazard, the following cases are ineligible for compensation:</p>
                
                <div class="exclusion-box">
                    <div class="exclusion-row"><span class="exclusion-bullet">•</span><span>Mock exam scores below Level 2 (limited post-secondary foundation).</span></div>
                    <div class="exclusion-row"><span class="exclusion-bullet">•</span><span>Low attendance in classes/tutors (insufficient preparation).</span></div>
                    <div class="exclusion-row"><span class="exclusion-bullet">•</span><span>Real DSE result Level 5 or higher (top performance secured).</span></div>
                    <div class="exclusion-row"><span class="exclusion-bullet">•</span><span>Missing or invalid official verification documents.</span></div>
                    <div class="exclusion-row"><span class="exclusion-bullet">•</span><span>Exam rule violations or cheating misconduct.</span></div>
                    <div class="exclusion-row"><span class="exclusion-bullet">•</span><span>Voluntary absence without an emergency rationale.</span></div>
                    <div class="exclusion-row"><span class="exclusion-bullet">•</span><span>Delays lacking official third-party transit/incident logs.</span></div>
                </div>

                <label class="touch-option">
                    <input type="checkbox" id="chk2" onchange="runValidation(2)">
                    <span class="touch-text">
                        <span class="touch-title">I accept these exclusion terms</span>
                        <span class="touch-subtitle">Acknowledged to protect policy reserve integrity.</span>
                    </span>
                </label>
            </div>

            <div class="survey-card" id="step3">
                <div class="step-label">Step 3 of 4</div>
                <h2>3. Plan Selection</h2>
                <p>Select your tier to establish price and claim caps:</p>
                
                <label class="touch-option">
                    <input type="radio" name="planChoice" value="Basic" onclick="runValidation(3)">
                    <span class="touch-text">
                        <span class="touch-title">Basic Plan — $65</span>
                        <span class="touch-subtitle">Exam fee coverage • Max claim $3,000</span>
                    </span>
                </label>

                <label class="touch-option">
                    <input type="radio" name="planChoice" value="Premium" onclick="runValidation(3)">
                    <span class="touch-text">
                        <span class="touch-title">Premium Plan — $210</span>
                        <span class="touch-subtitle">Exam & tuition coverage • Max claim $10,000</span>
                    </span>
                </label>
            </div>

            <div class="survey-card" id="step4">
                <div class="step-label">Step 4 of 4</div>
                <h2>4. Generate Contract</h2>
                <p>No personal identity or email records are collected. Proceed to create your local printable certificate.</p>
                
                <label class="touch-option">
                    <input type="checkbox" id="chk4" onchange="runValidation(4)">
                    <span class="touch-text">
                        <span class="touch-title">Authorize policy generation</span>
                        <span class="touch-subtitle">Build customized document on client device.</span>
                    </span>
                </label>
            </div>

            <div class="button-bar">
                <button type="button" id="btnBack" onclick="stepChange(-1)" disabled>Back</button>
                <button type="button" id="btnNext" class="btn-action" onclick="stepChange(1)" disabled>Next</button>
                <button type="button" id="btnBuild" class="btn-action" style="display: none;" onclick="renderPolicy()" disabled>Create E-Policy</button>
            </div>
        </form>

        <section id="policyDisplay" class="policy-output">
            <header class="cert-header">
                <h1 class="cert-title">Ed-surance E-Policy</h1>
                <p>HKDSE Protection Plan Contract</p>
            </header>

            <table class="meta-table">
                <tr>
                    <td>
                        <span class="meta-label">Selected Tier</span>
                        <strong id="outPlan">-</strong>
                    </td>
                    <td>
                        <span class="meta-label">Total Premium</span>
                        <strong id="outFee">-</strong>
                    </td>
                </tr>
                <tr>
                    <td>
                        <span class="meta-label">Coverage Ceiling</span>
                        <strong id="outCap">-</strong>
                    </td>
                    <td>
                        <span class="meta-label">Generation Time</span>
                        <span id="outDate">-</span>
                    </td>
                </tr>
            </table>

            <div class="cert-clause">
                <h3>1. Benefit Scope</h3>
                <p id="outDesc">-</p>
            </div>

            <div class="cert-clause">
                <h3>2. Binding Exclusions</h3>
                <ul>
                    <li>Mock results below Level 2 void qualification.</li>
                    <li>Unsubstantiated attendance lapses forfeit payouts.</li>
                    <li>Real exam results at or exceeding Level 5 fall outside claim scope.</li>
                    <li>Absence of official third-party logs disqualifies delays.</li>
                    <li>Academic malpractice or voluntary absence voids all benefits.</li>
                </ul>
            </div>

            <div class="cert-clause">
                <h3>3. Privacy & Device Issuance</h3>
                <p>Generated locally inside client runtime. No personal identification data or telemetry transferred.</p>
            </div>

            <div class="cert-actions">
                <button type="button" class="btn-action" onclick="window.print()">Print / Save PDF</button>
                <button type="button" onclick="restartSurvey()">Start Over</button>
            </div>
        </section>
    </div>

    <script>
        let step = 1;
        const total = 4;

        function refreshProgress() {
            document.getElementById('progressFill').style.width = ((step / total) * 100) + '%';
        }

        function runValidation(targetStep) {
            let pass = false;
            if (targetStep === 1 || targetStep === 2 || targetStep === 4) {
                const box = document.getElementById('chk' + targetStep);
                pass = box && box.checked;
            } else if (targetStep === 3) {
                const radios = document.getElementsByName('planChoice');
                for (let r of radios) {
                    if (r.checked) { pass = true; break; }
                }
            }

            if (step === total) {
                document.getElementById('btnBuild').disabled = !pass;
            } else {
                document.getElementById('btnNext').disabled = !pass;
            }
        }

        function stepChange(delta) {
            document.getElementById('step' + step).classList.remove('active');
            step += delta;
            document.getElementById('step' + step).classList.add('active');

            document.getElementById('btnBack').disabled = (step === 1);

            if (step === total) {
                document.getElementById('btnNext').style.display = 'none';
                document.getElementById('btnBuild').style.display = 'block';
            } else {
                document.getElementById('btnNext').style.display = 'block';
                document.getElementById('btnBuild').style.display = 'none';
            }

            runValidation(step);
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
                outDesc.textContent = 'Limited strictly to compensation for official HKDSE registration examination fees.';
            } else {
                outPlan.textContent = 'Premium Protection';
                outFee.textContent = '$210 HKD';
                outCap.textContent = '$10,000 HKD Max';
                outDesc.textContent = 'Extends compensation to both official registration fees and preparatory tuition costs.';
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
            document.getElementById('btnNext').style.display = 'block';
            document.getElementById('btnBuild').style.display = 'none';

            refreshProgress();
            runValidation(1);
        }
    </script>
</body>
</html>
