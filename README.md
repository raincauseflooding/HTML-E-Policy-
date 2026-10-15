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
            <div class="brand-tagline">HKDSE Exam Protection Plan</div>
        </header>

        <div class="progress-track" id="progressTrack">
            <div class="progress-fill" id="progressFill"></div>
        </div>

        <form id="policySurvey">
            <!-- STEP 1 -->
            <div class="survey-card active" id="step1">
                <div class="step-label">Step 1 of 4</div>
                <h2>1. We
