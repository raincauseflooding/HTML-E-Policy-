<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ed-surance - Interactive Policy Survey</title>
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

        /* Brand Header */
        .brand-header {
            text-align: center;
            margin-bottom: 2rem;
            border-bottom: 3px double #000000;
            padding-bottom: 1.5rem;
        }

        .brand-logo {
            font-size: 2rem;
            font-weight: 900;
            letter-spacing: -0.03em;
            text-transform: uppercase;
        }

        .brand-tagline {
            font-size: 0.95rem;
            letter-spacing: 0.05em;
            color: #555555;
            text-transform: uppercase;
            margin-top: 0.2rem;
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

        /* Interactive Elements / Plan Tiers */
        .tier-selection {
            display: flex;
            flex-direction: column;
            gap: 1rem;
            margin: 1.5rem 0;
        }

        .option-box {
            display: flex;
            align-items: flex-start;
            padding: 1.2rem;
            border: 2px solid #000000;
            cursor: pointer;
            transition: background 0.2s;
        }

        .option-box:hover {
            background-color: #f5f5f5;
        }

        .option-box input[type="radio"], 
        .option-box input[type="checkbox"] {
            width: 20px;
            height: 20px;
            margin-right: 1rem;
            margin-top: 0.2rem;
            accent-color: #000000;
            cursor: pointer;
        }

        .option-details {
            display: flex;
            flex-direction: column;
        }

        .option-title {
            font-weight: bold;
            font-size: 1.1rem;
        }

        .option-desc {
            font-size: 0.95rem;
            color: #444444;
            margin-top: 0.2rem;
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
            justify-space-between: space-between;
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
        button:focus, input:focus, .option-box:focus-within {
            outline: 3px solid #000000;
            outline-offset: 2px;
        }
    </style>
</head>
<body>

    <div class="survey-container">
        <!-- Brand Identity Section -->
        <header class="brand-header">
            <div class="brand-logo">Ed-surance</div>
            <div class="brand-tagline">HKDSE Exam Protection Plan</div>
        </header>

        <!-- Visual Progress Tracker -->
        <div class="progress-container">
            <div class="progress-bar" id="progressBar"></div>
        </div>

        <form id="policySurvey" onsubmit="handleFormSubmit(event)">
            
            <!-- STEP 1: Purpose -->
            <div class="survey-card active" id="step1">
                <p class="step-indicator">Step 1 of 4</p>
                <h2>1. Welcome to Ed-surance</h2>
                <p>We are here to protect HKDSE students during their exam season. This plan helps support you if unexpected events happen. Please read these short pages carefully to register.</p>
                
                <div class="option-box">
                    <input type="checkbox" id="consent1" onchange="validateStep(1)">
                    <div class="option-details">
                        <label for="consent1" class="option-title">I understand the plan's purpose</label>
                        <span class="option-desc">Please check this box to show you understand.</span>
                    </div>
                </div>
            </div>

            <!-- STEP 2: Candidate Obligations -->
            <div class="survey-card" id="step2">
                <p class="step-indicator">Step 2 of 4</p>
                <h2>2. Rules & Honesty</h2>
                <p>To enjoy our protection, you must follow all official exam rules. If a student cheats or gives false information, their Ed-surance policy will be cancelled immediately.</p>
                
                <div class="option-box">
                    <input type="checkbox" id="consent2" onchange="validateStep(2)">
                    <div class="option-details">
                        <label for="consent2" class="option-title">I agree to be honest</label>
                        <span class="option-desc">Please check this box to agree to the rules.</span>
                    </div>
                </div>
            </div>

            <!-- STEP 3: Plan Selection -->
            <div class="survey-card" id="step3">
                <p class="step-indicator">Step 3 of 4</p>
                <h2>3. Choose Your Plan</h2>
                <p>We offer two simple options to fit your needs. Please select the plan you would like to apply for:</p>
                
                <div class="tier-selection">
                    <!-- Option A -->
                    <label class="option-box">
                        <input type="radio" name="planSelection" value="Basic (\$65)" onclick="validateStep(3)">
                        <div class="option-details">
                            <span class="option-title">Basic Protection — \$65</span>
                            <span class="option-desc">Our essential coverage plan for students on a budget.</span>
                        </div>
                    </label>

                    <!-- Option B -->
                    <label class="option-box">
                        <input type="radio" name="planSelection" value="Premium (\$210)" onclick="validateStep(3)">
                        <div class="option-details">
                            <span class="option-title">Premium Protection — \$210</span>
                            <span class="option-desc">Our complete coverage plan with higher support benefits.</span>
                        </div>
                    </label>
                </div>
            </div>

            <!-- STEP 4: Submit Details -->
            <div class="survey-card" id="step4">
           
