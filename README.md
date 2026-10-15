<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HKDSE Exam Protection Plan - Interactive Policy Survey</title>
    <style>
        /* Reset & High-Contrast Base Styling */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            line-height: 1.6;
            color: #000000;
            background-color: #ffffff;
            -webkit-font-smoothing: antialiased;
        }

        /* Centered Layout Container */
        .survey-container {
            max-width: 700px;
            margin: 0 auto;
            padding: 3rem 1.5rem;
        }

        /* Progress Bar */
        .progress-container {
            width: 100%;
            height: 8px;
            background-color: #e0e0e0;
            margin-bottom: 2.5rem;
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-bar {
            height: 100%;
            width: 25%; /* Dynamically updated by JS */
            background-color: #000000;
            transition: width 0.3s ease;
        }

        /* Survey Cards */
        .survey-card {
            display: none; /* Hidden by default */
            border: 2px solid #000000;
            padding: 2.5rem;
            background-color: #ffffff;
            margin-bottom: 2rem;
            box-shadow: 4px 4px 0px #000000;
        }

        .survey-card.active {
            display: block; /* Show only current step */
        }

        .step-indicator {
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            color: #666666;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }

        h2 {
            font-size: 1.6rem;
            font-weight: 800;
            margin-bottom: 1.5rem;
            border-bottom: 2px solid #000000;
            padding-bottom: 0.5rem;
        }

        p {
            font-size: 1.05rem;
            margin-bottom: 1.5rem;
        }

        /* Interactive Elements */
        .consent-option {
            display: flex;
            align-items: center;
            margin: 1.5rem 0;
            padding: 1rem;
            border: 1px solid #000000;
            cursor: pointer;
            transition: background 0.2s;
        }

        .consent-option:hover {
            background-color: #f5f5f5;
        }

        .consent-option input {
            width: 20px;
            height: 20px;
            margin-right: 1rem;
            accent-color: #000000;
            cursor: pointer;
        }

        .consent-label {
            font-weight: bold;
            font-size: 1rem;
            cursor: pointer;
        }

        /* Form Inputs (Final Step) */
        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .form-group input {
            width: 100%;
            padding: 0.8rem;
            border: 2px solid #000000;
            font-size: 1rem;
            background-color: #ffffff;
            color: #000000;
        }

        /* Navigation Buttons */
        .button-group {
            display: flex;
            justify-content: space-between;
            gap: 1rem;
        }

        button {
            padding: 0.8rem 1.8rem;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            border: 2px solid #000000;
            background-color: #ffffff;
            color: #000000;
            transition: all 0.2s ease;
        }

        button:hover:not(:disabled) {
            background-color: #000000;
            color: #ffffff;
        }

        button:disabled {
            border-color: #cccccc;
            color: #cccccc;
            cursor: not-allowed;
        }

        .btn-next {
            background-color: #000000;
            color: #ffffff;
        }

        .btn-next:hover:not(:disabled) {
            background-color: #333333;
        }

        /* Accessibility Focus State */
        button:focus, input:focus, .consent-option:focus-within {
            outline: 3px solid #000000;
            outline-offset: 2px;
        }
    </style>
</head>
<body>

    <div class="survey-container">
        <!-- Visual Progress Tracker -->
        <div class="progress-container">
            <div class="progress-bar" id="progressBar"></div>
        </div>

        <form id="policySurvey" onsubmit="handleFormSubmit(event)">
            
            <!-- STEP 1: Purpose -->
            <div class="survey-card active" id="step1">
                <p class="step-indicator">Step 1 of 4</p>
                <h2>1. Purpose & Scope</h2>
                <p>The HKDSE Exam Protection Plan offers safety nets and formal eligibility clauses for registered candidates. By entering this walkthrough, you begin the process of reviewing security guidelines and protection parameters.</p>
                <div class="consent-option">
                    <input type="checkbox" id="consent1" onchange="validateStep(1)">
                    <label for="consent1" class="consent-label">I understand the purpose of this protection plan.</label>
                </div>
            </div>

            <!-- STEP 2: Candidate Responsibilities -->
            <div class="survey-card" id="step2">
                <p class="step-indicator">Step 2 of 4</p>
                <h2>2. Candidate Obligations</h2>
                <p>All candidates must strictly adhere to the academic integrity protocols outlined by official examinations. Misrepresentation of identity or fraudulent claims immediately voids your eligibility for any protection benefits.</p>
                <div class="consent-option">
                    <input type="checkbox" id="consent2" onchange="validateStep(2)">
                    <label for="consent2" class="consent-label">I agree to maintain academic integrity and honesty.</label>
                </div>
            </div>

            <!-- STEP 3: Protection Limits -->
            <div class="survey-card" id="step3">
                <p class="step-indicator">Step 3 of 4</p>
                <h2>3. Coverage Limits</h2>
                <p>This plan acts as an administrative buffer and support network. It does not replace officially mandated HKEAA rules, nor does it guarantee academic grading changes. Claims must be submitted within 48 hours of your scheduled exam.</p>
                <div class="consent-option">
                    <input type="checkbox" id="consent3" onchange="validateStep(3)">
                    <label for="consent3" class="consent-label">I acknowledge the coverage limitations and timelines.</label>
                </div>
            </div>

            <!-- STEP 4: Submit Details -->
            <div class="survey-card" id="step4">
                <p class="step-indicator">Step 4 of 4</p>
                <h2>4. Finalize Registration</h2>
                <p>Please provide your basic contact details to tie your explicit policy consent to your registration profile.</p>
                
                <div class="form-group">
                    <label for="fullName">Full Name (as in HKID/Passport)</label>
                    <input type="text" id="fullName" required oninput="validateStep(4)">
                </div>

                <div class="form-group">
                    <label for="studentEmail">Email Address</label>
                    <input type="email" id="studentEmail" required oninput="validateStep(4)">
                </div>
            </div>

            <!-- Global Survey Controls -->
            <div class="button-group">
                <button type="button" id="prevBtn" onclick="navigate(-1)" disabled>Previous</button>
                <button type="button" id="nextBtn" class="btn-next" onclick="navigate(1)" disabled>Next</button>
                <button type="submit" id="submitBtn" class="btn-next" style="display: none;" disabled>Submit Agreement</button>
            </div>
        </form>
    </div>

    <script>
        let currentStep = 1;
        const totalSteps = 4;

        function updateProgress() {
            const percentage = (currentStep / totalSteps) * 100;
            document.getElementById('progressBar').style.width = `${percentage}%`;
        }

        function validateStep(step) {
            let isValid = false;
            
            if (step >= 1 && step <= 3) {
                // For steps 1-3, check if the corresponding checkbox is checked
                const checkbox = document.getElementById(`consent${step}`);
                isValid = checkbox && checkbox.checked;
            } else if (step === 4) {
                // For step 4, check if text inputs are filled out
                const name = document.getElementById('fullName').value.trim();
                const email = document.getElementById('studentEmail').value.trim();
                isValid = name.length > 0 && email.length > 0 && document.getElementById('studentEmail').validity.valid;
            }

            // Enable/disable navigation buttons based on validation
            if (step === totalSteps) {
                document.getElementById('submitBtn').disabled = !isValid;
            } else {
                document.getElementById('nextBtn').disabled = !isValid;
            }
        }

        function navigate(direction) {
            // Hide current card
            document.getElementById(`step${currentStep}`).classList.remove('active');
            
            // Adjust current step index
            currentStep += direction;
            
            // Show new card
            document.getElementById(`step${currentStep}`).classList.add('active');

            // Handle button visibility
            document.getElementById('prevBtn').disabled = currentStep === 1;

            if (currentStep === totalSteps) {
                document.getElementById('nextBtn').style.display = 'none';
                document.getElementById('submitBtn').style.display = 'block';
            } else {
                document.getElementById('nextBtn').style.display = 'block';
                document.getElementById('submitBtn').style.display = 'none';
            }

            // Re-validate the newly active step
            validateStep(currentStep);
            updateProgress();
        }

        function handleFormSubmit(event) {
            event.preventDefault();
            
            const name = document.getElementById('fullName').value;
            const email = document.getElementById('studentEmail').value;
            
            alert(`Thank you, ${name}! Your explicit consent has been logged. Email confirmation will be sent to ${email}.`);
            
            // Note: In production, you can redirect to your Google Form or send this 
            // data to a backend handler (like Netlify Forms, Formspree, or Google Sheets API).
        }
    </script>
</body>
</html>
