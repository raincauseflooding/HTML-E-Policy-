<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">

    <title>Ed-surance - Private Candidate Protection</title>

    <style>

        \\\\\\\* {

            box-sizing: border-box;

            margin: 0;

            padding: 0;

            -webkit-tap-highlight-color: transparent;

        }

/\\\\\\\* Disable and hide all hover links, anchor icons, and auto-generated header links \\\\\\\*/

h1 a, h2 a, h3 a, h4 a, 

.anchor, .header-link, .markdown-anchor, 

[id] > a, [class\\\\\\\*="anchor"] {

    display: none !important;

    visibility: hidden !important;

    opacity: 0 !important;

    pointer-events: none !important;

    text-decoration: none !important;

}

  

/\\\\\\\* Ensure headings do not show pointers or look clickable \\\\\\\*/

h1, h2, h3, h4 {

    cursor: default !important;

    user-select: text !important;

}

  

        body {

            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;

            line-height: 1.5;

            color: #000000;

            background-color: #ffffff;

            padding: 1.5rem 1rem;

        }

  

        .survey-container {

            width: 100%;

            max-width: 550px;

            margin: 0 auto;

        }

  

        .brand-header {

            text-align: center;

            margin-bottom: 1.5rem;

            border-bottom: 2px solid #000000;

            padding-bottom: 0.8rem;

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

            width: 20%;

            background-color: #000000;

            transition: width 0.2s ease;

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

  

        .formal-warning-box {

            border: 2px solid #000000;

            background-color: #fafafa;

            padding: 1rem;

            margin-bottom: 1.2rem;

            font-size: 0.9rem;

        }

  

        .formal-warning-title {

            font-weight: 800;

            text-transform: uppercase;

            margin-bottom: 0.3rem;

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

            margin-bottom: 0.5rem;

        }

  

        /\\\\\\\* Large, Bulletproof Button Cards \\\\\\\*/

        .card-btn {

            display: block;

            width: 100%;

            min-height: 54px;

            padding: 1rem;

            border: 2px solid #000000;

            margin-top: 0.8rem;

            background-color: #ffffff;

            cursor: pointer;

            text-align: left;

            font-family: inherit;

        }

  

        .card-btn:active {

            background-color: #eeeeee;

        }

  

        .card-btn-title {

            display: block;

            font-size: 0.95rem;

            font-weight: 700;

            color: #000000;

            margin-bottom: 0.15rem;

        }

  

        .card-btn-subtitle {

            display: block;

            font-size: 0.8rem;

            color: #555555;

        }

  

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

  

        select {

            width: 100%;

            min-height: 44px;

            padding: 0.6rem;

            border: 2px solid #000000;

            font-size: 0.95rem;

            background-color: #ffffff;

        }

  

        .subject-scroll-area {

            max-height: 220px;

            overflow-y: auto;

            border: 2px solid #000000;

            padding: 0.6rem;

            background-color: #fafafa;

        }

  

        .subject-category {

            font-size: 0.8rem;

            font-weight: 800;

            text-transform: uppercase;

            color: #555555;

            margin: 0.6rem 0 0.3rem 0;

            border-bottom: 1px solid #cccccc;

            padding-bottom: 0.1rem;

        }

  

        .subject-grid {

            display: grid;

            grid-template-columns: 1fr 1fr;

            gap: 0.5rem;

        }

  

        /\\\\\\\* Bulletproof Checkbox Container \\\\\\\*/

        .sub-box {

            display: flex;

            align-items: center;

            padding: 0.5rem;

            border: 1px solid #000000;

            background-color: #ffffff;

            font-size: 0.85rem;

            font-weight: 600;

            cursor: pointer;

        }

  

        .sub-box input {

            margin-right: 0.5rem;

            width: 18px;

            height: 18px;

            accent-color: #000000;

        }

  

        .generator-container {

            border: 2px dashed #000000;

            padding: 1rem;

            text-align: center;

            background-color: #fafafa;

            margin-top: 1.2rem;

        }

  

        .candidate-num-display {

            font-size: 1.5rem;

            font-weight: 900;

            letter-spacing: 0.1em;

            margin: 0.8rem 0;

            font-family: monospace;

        }

  

        .btn-action {

            width: 100%;

            min-height: 48px;

            font-size: 0.95rem;

            font-weight: 700;

            border: 2px solid #000000;

            background-color: #000000;

            color: #ffffff;

            cursor: pointer;

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

  

        @media (max-width: 540px) {

            .meta-table td {

                display: block;

                width: 100%;

            }

            .meta-table tr {

                display: flex;

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

  

        <form id="policySurvey" onsubmit="return false;">

            <!-- STEP 1 -->

            <div class="survey-card active" id="step1">

                <div class="step-label">Step 1 of 5</div>

                

                <div class="formal-warning-box">

                    <div class="formal-warning-title"> Important Notice for Parents & Students:</div>

                    If you are worried about high costs, lost study momentum, or missing the examination due to sudden emergencies, you can buy our protection plan to secure your peace of mind.

                </div>

  

                <h2>1. Why Ed-surance Exists</h2>

                <p>Global exams like IELTS or IGCSE offer refunds if you miss an exam. In contrast, the HKDSE only offers "assessed grades" to day-school students.</p>

                

                <div class="comparison-box">

                    <div class="comparison-title"> The Private Candidate Problem:</div>

                    If you are a private, mainland, or international student, <strong>you cannot get an assessed grade</strong> if you miss the DSE. You get an automatic "Absent" (0 score) and lose your exam fee plus a whole year of study.

                </div>

  

                <div class="highlight-alert">

                     Ed-surance is the only plan that bridges this gap, providing financial safety for private candidates facing the 13% baseline absence rate.

                </div>

  

                <button type="button" class="card-btn" onclick="goToStep(2)">

                    <span class="card-btn-title">I understand my unique risks</span>

                    <span class="card-btn-subtitle">Tap here to view the eligibility rules.</span>

                </button>

            </div>

  

            <!-- STEP 2 -->

            <div class="survey-card" id="step2">

                <div class="step-label">Step 2 of 5</div>

                <h2>2. When We Cannot Pay</h2>

                <p>To keep plans fair and cheap for all honest students, claims are not payable if:</p>

                

                <div class="rule-list">

                    <div class="rule-row"><strong>•</strong> Your mock exam result is below Level 2.</div>

                    <div class="rule-row"><strong>•</strong> You have low attendance in school days or tutoring classes.</div>

                    <div class="rule-row"><strong>•</strong> You score Level 5 or higher in the real exam.</div>

                    <div class="rule-row"><strong>•</strong> You fail to provide valid official proof documents.</div>

                    <div class="rule-row"><strong>•</strong> You break official exam rules (e.g., cheating).</div>

                    <div class="rule-row"><strong>•</strong> You miss an exam without an emergency (feeling unprepared does not count).</div>

                    <div class="rule-row"><strong>•</strong> You are late without an official transit delay slip.</div>

                </div>

  

                <button type="button" class="card-btn" onclick="goToStep(3)">

                    <span class="card-btn-title">I accept these exclusion terms</span>

                    <span class="card-btn-subtitle">Tap here to choose your plan.</span>

                </button>

            </div>

  

            <!-- STEP 3 -->

            <div class="survey-card" id="step3">

                <div class="step-label">Step 3 of 5</div>

                <h2>3. Choose Your Plan</h2>

                <p>Select your protection level:</p>

                

                <button type="button" class="card-btn" onclick="selectPlan('Basic')">

                    <span class="card-btn-title">Tier 1: Basic Plan — $65</span>

                    <span class="card-btn-subtitle">Covers Basic HKDSE Exam Fees (Max payout: $3,000)</span>

                </button>

  

                <button type="button" class="card-btn" onclick="selectPlan('Premium')">

                    <span class="card-btn-title">Tier 2: Premium Partner Plan — $210</span>

                    <span class="card-btn-subtitle">Covers Basic HKDSE Fee + 37.5% Tutorial Fees (Max payout: $18,000)</span>

                </button>

            </div>

  

            <!-- STEP 4 -->

            <div class="survey-card" id="step4">

                <div class="step-label">Step 4 of 5</div>

                <h2>4. Your HKDSE Details</h2>

                <p>Select your exam year, check all covered subjects, then write your candidate number.</p>

                

                <div class="input-group">

                    <label for="examYear">Select Exam Year</label>

                    <select id="examYear">

                        <option value="2027">2027</option>

                        <option value="2028">2028</option>

                    </select>

                </div>

  

                <div class="input-group">

                    <label>Select Covered Subjects (Scroll to choose all that apply)</label>

                    <div class="subject-scroll-area">

                        <div class="subject-category">Core Subjects</div>

                        <div class="subject-grid">

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Chinese Language"> Chinese Language</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="English Language"> English Language</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Mathematics (Compulsory)"> Mathematics</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Citizenship & Social Development"> CS Dev.</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Mathematics Extended (M1)"> Math M1</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Mathematics Extended (M2)"> Math M2</label>

                        </div>

  

                        <div class="subject-category">Sciences</div>

                        <div class="subject-grid">

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Biology"> Biology</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Chemistry"> Chemistry</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Physics"> Physics</label>

                        </div>

  

                        <div class="subject-category">Humanities</div>

                        <div class="subject-grid">

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Chinese History"> Chinese History</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="History"> History</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Economics"> Economics</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Geography"> Geography</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Tourism & Hospitality Studies"> Tourism</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Ethics & Religious Studies"> Ethics</label>

                        </div>

  

                        <div class="subject-category">Business & Tech</div>

                        <div class="subject-grid">

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="BAFS"> BAFS</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="ICT"> ICT</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Design & Applied Technology"> Design</label>

                            <label class="sub-box"><input type="checkbox" name="subjectChoice" value="Technology & Living"> Living</label>

                        </div>

                    </div>

                </div>

  

                <div class="generator-container">

                    <label style="font-weight: bold; font-size: 0.9rem;">DSE Candidate Number</label>

                    <div class="candidate-num-display" id="candidateNumBox">---------</div>

                    <button type="button" class="btn-action" onclick="generateDseNumber()">Write my number</button>

                </div>

            </div>

  

            <!-- STEP 5 -->

            <div class="survey-card" id="step5">

                <div class="step-label">Step 5 of 5</div>

                <h2>5. Generate Document</h2>

                <p>We do not collect any personal data or email addresses. Tap below to build your agreement immediately.</p>

                

                <button type="button" class="card-btn" onclick="goToStep(6)">

                    <span class="card-btn-title">Create my E-Policy Contract</span>

                    <span class="card-btn-subtitle">Builds the certificate instantly on your screen.</span>

                </button>

            </div>

        </form>

  

        <!-- THE GENERATED LOCAL E-POLICY -->

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

                        <span class="meta-label">Candidate Number</span>

                        <strong id="outCandNum" style="font-family: monospace; letter-spacing: 0.05em;">-</strong>

                    </td>

                </tr>

                <tr>

                    <td>

                        <span class="meta-label">DSE Exam Year</span>

                        <strong id="outYear">-</strong>

                    </td>

                    <td>

                        <span class="meta-label">Covered Subjects</span>

                        <strong id="outSubjects">-</strong>

                    </td>

                </tr>

                <tr>

                    <td colspan="2" style="text-align: center;">

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

  

            <div class="cert-actions">

                <button type="button" class="btn-action" onclick="restartSurvey()">Start Over</button>

            </div>

        </section>

    </div>

  

    <script>

        let step = 1;

        const total = 5;

        let generatedCandNum = "";

        let selectedPlanTier = "Basic";

  

        function refreshProgress() {

            document.getElementById('progressFill').style.width = ((step / total) \\\\\\\* 100) + '%';

        }

  

        function goToStep(target) {

            if (target === 6) {

                renderPolicy();

                return;

            }

            document.getElementById('step' + step).classList.remove('active');

            step = target;

            document.getElementById('step' + step).classList.add('active');

            refreshProgress();

        }

  

        function selectPlan(tier) {

            selectedPlanTier = tier;

            goToStep(4);

        }

  

        function generateDseNumber() {

            const year = document.getElementById('examYear').value;

            const subjects = document.querySelectorAll('input[name="subjectChoice"]:checked');

  

            if (subjects.length === 0) {

                alert("Please select at least one covered subject.");

                return;

            }

  

            const prefix = year.substring(2);

            let serializedDigits = "";

            for (let i = 0; i < 7; i++) {

                serializedDigits += Math.floor(Math.random() \\\\\\\* 10);

            }

  

            generatedCandNum = prefix + serializedDigits;

            document.getElementById('candidateNumBox').textContent = generatedCandNum;

  

            // Instantly advances to Step 5 the moment the number is generated

            goToStep(5);

        }

  

        function renderPolicy() {

            const selectedYear = document.getElementById('examYear').value;

            const selectedSubjects = Array.from(document.querySelectorAll('input[name="subjectChoice"]:checked')).map(el => el.value).join(', ');

  

            const outPlan = document.getElementById('outPlan');

            const outFee = document.getElementById('outFee');

            const outCap = document.getElementById('outCap');

            const outDesc = document.getElementById('outDesc');

            

            const outCandNum = document.getElementById('outCandNum');

            const outYear = document.getElementById('outYear');

            const outSubjects = document.getElementById('outSubjects');

  

            outCandNum.textContent = generatedCandNum;

            outYear.textContent = selectedYear;

            outSubjects.textContent = selectedSubjects;

  

            if (selectedPlanTier === 'Basic') {

                outPlan.textContent = 'Tier 1: Basic Protection';

                outFee.textContent = '$65 HKD';

                outCap.textContent = '$3,000 HKD Max';

                outDesc.textContent = 'Covers basic HKDSE registration examination fees up to $3,000 HKD paid directly to the examination authority.';

            } else {

                outPlan.textContent = 'Tier 2: Premium Partner Plan';

                outFee.textContent = '$300 HKD';

                outCap.textContent = '$18,000 HKD Max';

                outDesc.textContent = 'Covers official basic HKDSE examination fees plus 37.5% of verified tutorial/retake fees (up to a combined maximum payout of $18,000 HKD) coordinated via partner tutoring centres.';

            }

  

            document.getElementById('outDate').textContent = new Date().toLocaleString();

  

            document.getElementById('brandHeader').style.display = 'none';

            document.getElementById('progressTrack').style.display = 'none';

            document.getElementById('policySurvey').style.display = 'none';

            document.getElementById('policyDisplay').classList.add('active');

        }

  

        function restartSurvey() {

            document.getElementById('policySurvey').reset();

            generatedCandNum = "";

            document.getElementById('candidateNumBox').textContent = "---------";

            document.getElementById('policyDisplay').classList.remove('active');

            document.getElementById('brandHeader').style.display = 'block';

            document.getElementById('progressTrack').style.display = 'block';

            document.getElementById('policySurvey').style.display = 'block';

  

            document.getElementById('step' + step).classList.remove('active');

            step = 1;

            document.getElementById('step1').classList.add('active');

            refreshProgress();

        }

    </script>

</body>

</html>