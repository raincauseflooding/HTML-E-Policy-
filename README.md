<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ed-surance - Interactive Policy & Certificate Generator</title>
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
            max-width: 750px;
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
            font-size: 2.2rem;
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
            width: 25%; /* Dynamically updated by JS (Steps 1 to 4) */
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
            display: block; /* Show only current active step */
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

        /* Policy Exclusion List style */
        .exclusion-list {
            margin: 1.5rem 0;
            border: 1px solid #000000;
            background-color: #fafafa;
            padding: 1rem;
        }

        .exclusion-item {
            margin-bottom: 0.8rem;
