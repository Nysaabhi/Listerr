<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Nysa Lister</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/flatpickr/dist/flatpickr.min.css">
    <style>
:root { 
    --primary-color: #FFD700; 
    --secondary-color: #FDB931; 
    --background-dark: #1a1a1f; 
    --text-light: #ffffff; 
    --text-dark: #000000; 
    --accent-gradient: linear-gradient(135deg, var(--primary-color), var(--secondary-color)); 
    --error-color: #ff4444; 
    --success-color: #00C851; 
    --info-color: #33b5e5;
    --warning-color: #ffbb33;
    --border-radius: 8px;
    --box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    --transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}

* { 
    box-sizing: border-box; 
    margin: 0; 
    padding: 0; 
}

body { 
    font-family: 'Poppins', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif; 
    background-color: var(--background-dark); 
    color: var(--text-light); 
    line-height: 1.6; 
    overflow-x: hidden; 
    -webkit-font-smoothing: antialiased;
}

.header { 
    padding: 8px 16px; 
    background: rgba(26, 26, 31, 0.95); 
    position: fixed; 
    width: 100%; 
    top: 0; 
    left: 0; 
    z-index: 1000; 
    border-bottom: 2px solid var(--primary-color); 
    backdrop-filter: blur(10px); 
    height: 60px; 
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo { 
    font-size: 1.8em; 
    font-weight: 900; 
    background: var(--accent-gradient); 
    -webkit-background-clip: text; 
    color: transparent; 
    letter-spacing: 1.2px; 
    display: flex;
    align-items: center;
    gap: 8px;
}

.logo-icon {
    font-size: 1.2em;
}

.menu-button { 
    padding: 10px 20px; 
    background: var(--accent-gradient); 
    border: none; 
    border-radius: 50px; 
    color: var(--text-dark); 
    font-weight: 600; 
    cursor: pointer; 
    transition: var(--transition); 
    font-size: 0.95em; 
    display: flex;
    align-items: center;
    gap: 8px;
}

.menu-button:hover {
    transform: translateY(-2px);
    box-shadow: var(--box-shadow);
}

.main-container {
    margin-top: 80px;
    padding: 20px;
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
}

.page-title {
    text-align: center; 
    margin-top: 0; 
    margin-bottom: 40px; 
    color: var(--primary-color);
    font-weight: 700;
    font-size: 2rem;
    position: relative;
    padding-bottom: 15px;
}

.page-title::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100px;
    height: 3px;
    background: var(--accent-gradient);
    border-radius: 3px;
}

.listing-types {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 25px;
    margin-bottom: 40px;
}

.listing-card {
    background: rgba(255, 255, 255, 0.05);
    border-radius: var(--border-radius);
    padding: 25px;
    transition: var(--transition);
    cursor: pointer;
    border: 1px solid rgba(255, 215, 0, 0.1);
    text-align: center;
    display: flex;
    flex-direction: column;
    height: 100%;
}

.listing-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--box-shadow);
    border-color: var(--primary-color);
    background: rgba(255, 255, 255, 0.08);
}

.listing-icon {
    font-size: 40px;
    color: var(--primary-color);
    margin-bottom: 15px;
}

.listing-title {
    font-size: 1.3em;
    margin-bottom: 10px;
    font-weight: 600;
    color: var(--primary-color);
}

.listing-description {
    font-size: 0.9em;
    opacity: 0.8;
    margin-bottom: 20px;
    flex-grow: 1;
}

.listing-button {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 12px 20px;
    border-radius: var(--border-radius);
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    width: 100%;
    font-size: 1em;
    margin-top: auto;
}

.listing-button:hover {
    opacity: 0.9;
    transform: translateY(-2px);
}

.form-container {
    background: rgba(26, 26, 31, 0.95);
    border-radius: var(--border-radius);
    padding: 30px;
    margin-top: 30px;
    border: 1px solid rgba(255, 215, 0, 0.2);
    display: none;
    box-shadow: var(--box-shadow);
}

.active-form {
    display: block;
    animation: fadeIn 0.5s ease;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

.form-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 25px;
    padding-bottom: 15px;
    border-bottom: 1px solid rgba(255, 215, 0, 0.2);
}

.form-title {
    font-size: 1.5em;
    font-weight: 700;
    color: var(--primary-color);
    display: flex;
    align-items: center;
    gap: 10px;
}

.close-form {
    background: none;
    border: none;
    color: var(--primary-color);
    font-size: 1.5em;
    cursor: pointer;
    padding: 5px;
    transition: var(--transition);
}

.close-form:hover {
    transform: rotate(90deg);
}

.form-group {
    margin-bottom: 20px;
}

.form-label {
    display: block;
    margin-bottom: 8px;
    font-weight: 500;
    color: var(--primary-color);
}

.form-label.required::after {
    content: ' *';
    color: var(--error-color);
}

.form-control {
    width: 100%;
    padding: 12px 15px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 215, 0, 0.2);
    border-radius: var(--border-radius);
    color: var(--text-light);
    font-size: 14px;
    font-family: 'Poppins', sans-serif;
    transition: var(--transition);
}

.form-control:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.2);
}

.form-select {
    width: 100%;
    padding: 12px 15px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 215, 0, 0.2);
    border-radius: var(--border-radius);
    color: var(--text-light);
    font-size: 14px;
    appearance: none;
    background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23FFD700'%3e%3cpath d='M7 10l5 5 5-5z'/%3e%3c/svg%3e");
    background-repeat: no-repeat;
    background-position: right 10px center;
    background-size: 20px;
}

.form-textarea {
    min-height: 120px;
    resize: vertical;
}

.form-radio-group, .form-checkbox-group {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
    margin-top: 10px;
}

.form-radio, .form-checkbox {
    display: flex;
    align-items: center;
    cursor: pointer;
}

.form-radio input, .form-checkbox input {
    margin-right: 8px;
    cursor: pointer;
}

.form-radio-label, .form-checkbox-label {
    cursor: pointer;
}

.form-submit {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 14px 25px;
    border-radius: var(--border-radius);
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    width: 100%;
    margin-top: 30px;
    font-size: 1.1em;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.form-submit:hover {
    opacity: 0.9;
    transform: translateY(-2px);
    box-shadow: var(--box-shadow);
}

.form-section {
    margin-bottom: 30px;
    padding-bottom: 20px;
    border-bottom: 1px solid rgba(255, 215, 0, 0.1);
}

.form-section-title {
    color: var(--primary-color);
    font-size: 1.2em;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    font-weight: 600;
}

.form-section-title i {
    font-size: 1.1em;
}

.form-steps {
    display: flex;
    justify-content: space-between;
    margin-bottom: 30px;
    position: relative;
}

.form-step {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    z-index: 2;
    flex: 1;
}

.form-step-number {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: rgba(255, 215, 0, 0.2);
    color: var(--primary-color);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 600;
    margin-bottom: 8px;
    border: 2px solid var(--primary-color);
    transition: var(--transition);
}

.form-step.active .form-step-number {
    background: var(--accent-gradient);
    color: var(--text-dark);
    transform: scale(1.1);
}

.form-step-label {
    font-size: 0.85em;
    text-align: center;
    color: rgba(255, 255, 255, 0.7);
}

.form-step.active .form-step-label {
    color: var(--primary-color);
    font-weight: 500;
}

.form-steps::before {
    content: '';
    position: absolute;
    top: 20px;
    left: 0;
    right: 0;
    height: 2px;
    background: rgba(255, 215, 0, 0.2);
    z-index: 1;
}

.form-steps-progress {
    position: absolute;
    top: 20px;
    left: 0;
    height: 2px;
    background: var(--accent-gradient);
    z-index: 1;
    transition: width 0.3s ease;
}

.file-upload {
    position: relative;
    margin-bottom: 15px;
}

.file-upload-input {
    position: absolute;
    left: 0;
    top: 0;
    opacity: 0;
    width: 100%;
    height: 100%;
    cursor: pointer;
}

.file-upload-label {
    display: block;
    padding: 30px;
    border: 2px dashed rgba(255, 215, 0, 0.3);
    border-radius: var(--border-radius);
    text-align: center;
    cursor: pointer;
    transition: var(--transition);
}

.file-upload-label:hover {
    border-color: var(--primary-color);
    background: rgba(255, 215, 0, 0.05);
}

.file-upload-label i {
    font-size: 28px;
    color: var(--primary-color);
    margin-bottom: 10px;
    display: block;
}

.file-upload-text {
    font-size: 0.9em;
    margin-bottom: 5px;
}

.file-upload-hint {
    font-size: 0.8em;
    opacity: 0.7;
}

.file-preview {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 15px;
}

.file-preview-item {
    position: relative;
    width: 100px;
    height: 100px;
    border-radius: var(--border-radius);
    overflow: hidden;
    border: 1px solid rgba(255, 255, 255, 0.1);
}

.file-preview-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.file-preview-item-remove {
    position: absolute;
    top: 5px;
    right: 5px;
    background: rgba(0, 0, 0, 0.7);
    width: 24px;
    height: 24px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: var(--transition);
}

.file-preview-item-remove:hover {
    background: var(--error-color);
}

.file-preview-item-remove i {
    font-size: 12px;
}

.subscription-plans {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 15px;
    margin-bottom: 20px;
}

.subscription-plan {
    background: rgba(255, 255, 255, 0.05);
    border-radius: var(--border-radius);
    padding: 20px;
    text-align: center;
    cursor: pointer;
    transition: var(--transition);
    border: 1px solid transparent;
    display: flex;
    flex-direction: column;
}

.subscription-plan:hover {
    transform: translateY(-5px);
    box-shadow: var(--box-shadow);
}

.subscription-plan.active {
    border-color: var(--primary-color);
    background: rgba(255, 215, 0, 0.1);
    transform: scale(1.03);
}

.subscription-plan-name {
    font-weight: 600;
    margin-bottom: 10px;
    color: var(--primary-color);
}

.subscription-plan-price {
    font-size: 1.5em;
    font-weight: 700;
    color: var(--primary-color);
    margin: 10px 0;
}

.subscription-plan-duration {
    font-size: 0.85em;
    opacity: 0.8;
    margin-bottom: 15px;
}

.subscription-plan-features {
    font-size: 0.85em;
    text-align: left;
    margin-top: auto;
    padding-left: 15px;
}

.subscription-plan-features li {
    margin-bottom: 5px;
    position: relative;
    list-style-type: none;
}

.subscription-plan-features li::before {
    content: '✓';
    color: var(--primary-color);
    margin-right: 8px;
}

.features-checklist {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 15px;
}

.feature-checkbox {
    display: flex;
    align-items: center;
    margin-bottom: 8px;
    background: rgba(255, 255, 255, 0.05);
    padding: 10px 15px;
    border-radius: var(--border-radius);
    transition: var(--transition);
}

.feature-checkbox:hover {
    background: rgba(255, 215, 0, 0.1);
}

.feature-checkbox input {
    margin-right: 10px;
    cursor: pointer;
}

.feature-checkbox-label {
    cursor: pointer;
}

.form-row {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
}

.form-date-time {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
}

@media (max-width: 768px) {
    .form-date-time {
        grid-template-columns: 1fr;
    }
}

.form-actions {
    display: flex;
    justify-content: space-between;
    margin-top: 30px;
}

.btn {
    padding: 12px 25px;
    border-radius: var(--border-radius);
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    border: none;
    font-size: 1em;
}

.btn-primary {
    background: var(--accent-gradient);
    color: var(--text-dark);
}

.btn-secondary {
    background: rgba(255, 255, 255, 0.1);
    color: var(--text-light);
    border: 1px solid rgba(255, 215, 0, 0.3);
}

.btn:hover {
    opacity: 0.9;
    transform: translateY(-2px);
    box-shadow: var(--box-shadow);
}

.confirmation-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 2000;
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
    backdrop-filter: blur(5px);
}

.confirmation-modal.active {
    opacity: 1;
    visibility: visible;
}

.confirmation-content {
    background-color: var(--background-dark);
    border-radius: var(--border-radius);
    padding: 40px;
    text-align: center;
    max-width: 500px;
    width: 90%;
    border: 1px solid var(--primary-color);
    box-shadow: var(--box-shadow);
    animation: modalFadeIn 0.4s ease;
}

@keyframes modalFadeIn {
    from { opacity: 0; transform: scale(0.9); }
    to { opacity: 1; transform: scale(1); }
}

.confirmation-icon {
    font-size: 60px;
    color: var(--success-color);
    margin-bottom: 20px;
}

.confirmation-title {
    font-size: 1.8em;
    margin-bottom: 15px;
    color: var(--primary-color);
    font-weight: 700;
}

.confirmation-message {
    margin-bottom: 25px;
    line-height: 1.7;
}

.confirmation-button {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 14px 30px;
    border-radius: var(--border-radius);
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    font-size: 1.1em;
    margin-top: 20px;
    width: 100%;
    max-width: 200px;
}

.confirmation-button:hover {
    opacity: 0.9;
    transform: translateY(-2px);
    box-shadow: var(--box-shadow);
}

.form-navigation {
    display: flex;
    justify-content: space-between;
    margin-top: 30px;
}

.form-progress {
    height: 6px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 3px;
    margin-bottom: 30px;
    overflow: hidden;
}

.form-progress-bar {
    height: 100%;
    background: var(--accent-gradient);
    border-radius: 3px;
    transition: width 0.3s ease;
}

.form-tab {
    display: none;
}

.form-tab.active {
    display: block;
    animation: fadeIn 0.5s ease;
}

.form-footer {
    margin-top: 40px;
    padding-top: 20px;
    border-top: 1px solid rgba(255, 215, 0, 0.1);
    text-align: center;
    font-size: 0.9em;
    opacity: 0.8;
}

/* Responsive adjustments */
@media (max-width: 1024px) {
    .subscription-plans {
        grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    }
    
    .features-checklist {
        grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    }
}

@media (max-width: 768px) {
    .listing-types {
        grid-template-columns: 1fr;
    }
    
    .form-container {
        padding: 20px;
    }
    
    .features-checklist {
        grid-template-columns: 1fr;
    }
    
    .form-row {
        grid-template-columns: 1fr;
    }
    
    .form-steps {
        flex-wrap: wrap;
        gap: 15px;
    }
    
    .form-step {
        flex: 0 0 calc(50% - 15px);
    }
    
    .form-steps::before, .form-steps-progress {
        display: none;
    }
}

@media (max-width: 480px) {
    .header {
        padding: 8px 10px;
    }
    
    .logo {
        font-size: 1.5em;
    }
    
    .menu-button {
        padding: 8px 15px;
        font-size: 0.85em;
    }
    
    .page-title {
        font-size: 1.5em;
        margin-bottom: 30px;
    }
    
    .form-title {
        font-size: 1.3em;
    }
    
    .subscription-plans {
        grid-template-columns: 1fr;
    }
    
    .form-step {
        flex: 0 0 100%;
    }
    
    .form-actions {
        flex-direction: column;
        gap: 15px;
    }
    
    .btn {
        width: 100%;
    }
}

/* Hide unwanted elements */
body > h1:first-of-type:not(.heading) { 
    display: none !important; 
}

.markdown-body h1:first-child { 
    display: none !important; 
}

.position-relative h1:first-child { 
    display: none !important; 
}

/* Form validation styles */
.form-control.error {
    border-color: var(--error-color);
}

.form-feedback {
    font-size: 0.85em;
    margin-top: 5px;
    padding-left: 5px;
}

.form-feedback.error {
    color: var(--error-color);
}

.form-feedback.success {
    color: var(--success-color);
}

/* Tooltip styles */
.tooltip {
    position: relative;
    display: inline-block;
    margin-left: 5px;
    cursor: pointer;
}

.tooltip-icon {
    color: var(--primary-color);
    font-size: 0.9em;
}

.tooltip-text {
    visibility: hidden;
    width: 200px;
    background-color: rgba(0, 0, 0, 0.8);
    color: #fff;
    text-align: center;
    border-radius: var(--border-radius);
    padding: 8px;
    position: absolute;
    z-index: 1;
    bottom: 125%;
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;
    transition: opacity 0.3s;
    font-size: 0.8em;
    font-weight: normal;
}

.tooltip:hover .tooltip-text {
    visibility: visible;
    opacity: 1;
}

/* Rating input */
.rating-input {
    display: flex;
    align-items: center;
    gap: 10px;
}

.rating-stars {
    display: flex;
    gap: 5px;
}

.rating-star {
    font-size: 24px;
    color: rgba(255, 215, 0, 0.3);
    cursor: pointer;
    transition: var(--transition);
}

.rating-star.active, .rating-star:hover {
    color: var(--primary-color);
    transform: scale(1.1);
}

/* Time slot selector */
.time-slots {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 10px;
    margin-top: 10px;
}

.time-slot {
    padding: 8px 10px;
    background: rgba(255, 255, 255, 0.05);
    border-radius: var(--border-radius);
    text-align: center;
    cursor: pointer;
    transition: var(--transition);
    border: 1px solid rgba(255, 215, 0, 0.1);
}

.time-slot:hover {
    background: rgba(255, 215, 0, 0.1);
}

.time-slot.selected {
    background: var(--accent-gradient);
    color: var(--text-dark);
    font-weight: 600;
    border-color: transparent;
}

/* Range slider */
.range-slider {
    width: 100%;
    margin-top: 15px;
}

.range-slider input[type="range"] {
    width: 100%;
    height: 6px;
    -webkit-appearance: none;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 3px;
    outline: none;
}

.range-slider input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 18px;
    height: 18px;
    background: var(--primary-color);
    border-radius: 50%;
    cursor: pointer;
}

.range-values {
    display: flex;
    justify-content: space-between;
    margin-top: 5px;
    font-size: 0.85em;
}

/* Calendar/date picker */
.flatpickr-input {
    background: rgba(255, 255, 255, 0.05) !important;
    border: 1px solid rgba(255, 215, 0, 0.2) !important;
    color: var(--text-light) !important;
    padding: 12px 15px !important;
    border-radius: var(--border-radius) !important;
    width: 100% !important;
    font-family: 'Poppins', sans-serif !important;
}

.flatpickr-input:focus {
    border-color: var(--primary-color) !important;
    box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.2) !important;
}

/* Multi-select dropdown */
.select2-container--default .select2-selection--multiple {
    background: rgba(255, 255, 255, 0.05) !important;
    border: 1px solid rgba(255, 215, 0, 0.2) !important;
    border-radius: var(--border-radius) !important;
    min-height: 45px !important;
}

.select2-container--default .select2-selection--multiple .select2-selection__choice {
    background: rgba(255, 215, 0, 0.2) !important;
    border: 1px solid rgba(255, 215, 0, 0.3) !important;
    color: var(--text-light) !important;
    border-radius: 3px !important;
}

.select2-container--default .select2-selection--multiple .select2-selection__choice__remove {
    color: var(--primary-color) !important;
    margin-right: 5px !important;
}

.select2-container--default .select2-results__option--highlighted[aria-selected] {
    background-color: var(--primary-color) !important;
    color: var(--text-dark) !important;
}

/* Toggle switch */
.toggle-switch {
    position: relative;
    display: inline-block;
    width: 50px;
    height: 24px;
    margin-left: 10px;
}

.toggle-switch input {
    opacity: 0;
    width: 0;
    height: 0;
}

.toggle-slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(255, 255, 255, 0.1);
    transition: .4s;
    border-radius: 24px;
}

.toggle-slider:before {
    position: absolute;
    content: "";
    height: 16px;
    width: 16px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    transition: .4s;
    border-radius: 50%;
}

input:checked + .toggle-slider {
    background-color: var(--primary-color);
}

input:checked + .toggle-slider:before {
    transform: translateX(26px);
}

.toggle-label {
    display: flex;
    align-items: center;
    cursor: pointer;
}

/* Responsive table */
.responsive-table {
    width: 100%;
    border-collapse: collapse;
    margin: 20px 0;
}

.responsive-table th, .responsive-table td {
    padding: 12px 15px;
    text-align: left;
    border-bottom: 1px solid rgba(255, 215, 0, 0.1);
}

.responsive-table th {
    background: rgba(255, 215, 0, 0.1);
    color: var(--primary-color);
    font-weight: 600;
}

@media (max-width: 768px) {
    .responsive-table {
        display: block;
        overflow-x: auto;
    }
}

/* Accordion styles */
.accordion {
    margin-bottom: 20px;
    border-radius: var(--border-radius);
    overflow: hidden;
}

.accordion-header {
    background: rgba(255, 215, 0, 0.1);
    padding: 15px 20px;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-weight: 600;
    color: var(--primary-color);
    transition: var(--transition);
}

.accordion-header:hover {
    background: rgba(255, 215, 0, 0.2);
}

.accordion-content {
    background: rgba(255, 255, 255, 0.05);
    padding: 0;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.3s ease;
}

.accordion-content-inner {
    padding: 20px;
}

.accordion.active .accordion-content {
    max-height: 1000px;
}

.accordion-icon {
    transition: transform 0.3s ease;
}

.accordion.active .accordion-icon {
    transform: rotate(180deg);
}

/* Chip/tag styles */
.chip-container {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 10px;
}

.chip {
    background: rgba(255, 215, 0, 0.1);
    padding: 5px 12px;
    border-radius: 20px;
    font-size: 0.85em;
    display: flex;
    align-items: center;
    gap: 5px;
}

.chip-remove {
    cursor: pointer;
    font-size: 0.9em;
    color: var(--error-color);
}

/* Search input with icon */
.search-input-container {
    position: relative;
}

.search-input {
    padding-left: 40px !important;
}

.search-icon {
    position: absolute;
    left: 15px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--primary-color);
}

/* Loading spinner */
.loading-spinner {
    display: inline-block;
    width: 20px;
    height: 20px;
    border: 3px solid rgba(255, 215, 0, 0.3);
    border-radius: 50%;
    border-top-color: var(--primary-color);
    animation: spin 1s ease-in-out infinite;
    margin-right: 10px;
}

@keyframes spin {
    to { transform: rotate(360deg); }
}

/* Responsive iframe */
.responsive-iframe {
    position: relative;
    padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
    height: 0;
    overflow: hidden;
    border-radius: var(--border-radius);
    margin: 20px 0;
}

.responsive-iframe iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: none;
}

/* Badge styles */
.badge {
    display: inline-block;
    padding: 3px 8px;
    border-radius: 12px;
    font-size: 0.75em;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.badge-primary {
    background: var(--primary-color);
    color: var(--text-dark);
}

.badge-secondary {
    background: rgba(255, 255, 255, 0.1);
    color: var(--text-light);
}

/* Alert messages */
.alert {
    padding: 15px;
    border-radius: var(--border-radius);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 15px;
}

.alert-icon {
    font-size: 1.5em;
}

.alert-success {
    background: rgba(0, 200, 81, 0.1);
    border: 1px solid rgba(0, 200, 81, 0.3);
    color: var(--success-color);
}

.alert-error {
    background: rgba(255, 68, 68, 0.1);
    border: 1px solid rgba(255, 68, 68, 0.3);
    color: var(--error-color);
}

.alert-warning {
    background: rgba(255, 187, 51, 0.1);
    border: 1px solid rgba(255, 187, 51, 0.3);
    color: var(--warning-color);
}

.alert-info {
    background: rgba(51, 181, 229, 0.1);
    border: 1px solid rgba(51, 181, 229, 0.3);
    color: var(--info-color);
}

/* Responsive grid */
.grid {
    display: grid;
    gap: 20px;
}

.grid-2 {
    grid-template-columns: repeat(2, 1fr);
}

.grid-3 {
    grid-template-columns: repeat(3, 1fr);
}

.grid-4 {
    grid-template-columns: repeat(4, 1fr);
}

@media (max-width: 1024px) {
    .grid-4 {
        grid-template-columns: repeat(3, 1fr);
    }
}

@media (max-width: 768px) {
    .grid-3, .grid-4 {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 480px) {
    .grid-2, .grid-3, .grid-4 {
        grid-template-columns: 1fr;
    }
}

/* Custom scrollbar */
::-webkit-scrollbar {
    width: 8px;
    height: 8px;
}

::-webkit-scrollbar-track {
    background: rgba(255, 255, 255, 0.05);
}

::-webkit-scrollbar-thumb {
    background: rgba(255, 215, 0, 0.5);
    border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
    background: var(--primary-color);
}

/* Animation classes */
.fade-in {
    animation: fadeIn 0.5s ease;
}

.slide-up {
    animation: slideUp 0.5s ease;
}

@keyframes slideUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

.pulse {
    animation: pulse 2s infinite;
}

@keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.05); }
    100% { transform: scale(1); }
}

/* Utility classes */
.text-center {
    text-align: center;
}

.text-primary {
    color: var(--primary-color);
}

.mt-0 { margin-top: 0; }
.mt-10 { margin-top: 10px; }
.mt-20 { margin-top: 20px; }
.mt-30 { margin-top: 30px; }
.mt-40 { margin-top: 40px; }

.mb-0 { margin-bottom: 0; }
.mb-10 { margin-bottom: 10px; }
.mb-20 { margin-bottom: 20px; }
.mb-30 { margin-bottom: 30px; }
.mb-40 { margin-bottom: 40px; }

.hidden {
    display: none !important;
}

/* Print styles */
@media print {
    .no-print {
        display: none !important;
    }
    
    body {
        background: white !important;
        color: black !important;
    }
    
    .form-container {
        border: none !important;
        box-shadow: none !important;
        padding: 0 !important;
    }
}
    </style>
</head>
<body>
    <header class="header">
        <div class="logo">
            <i class="fas fa-list-alt logo-icon"></i>
            Nysa Lister
        </div>
        <button class="menu-button" id="menuButton">
            <i class="fas fa-bars"></i> Menu
        </button>
    </header>

    <div class="main-container">
        <h2 class="page-title">Create a New Listing</h2>
        
        <div class="listing-types">
            <div class="listing-card" onclick="showForm('serviceProviderForm')">
                <div class="listing-icon"><i class="fas fa-tools"></i></div>
                <h3 class="listing-title">Service Provider</h3>
                <p class="listing-description">List electricians, plumbers, cleaners, and other service professionals with detailed service offerings and availability</p>
                <button class="listing-button">List Service</button>
            </div>
            
            <div class="listing-card" onclick="showForm('storeForm')">
                <div class="listing-icon"><i class="fas fa-store"></i></div>
                <h3 class="listing-title">Store</h3>
                <p class="listing-description">List retail stores, supermarkets, and other businesses with product offerings and store details</p>
                <button class="listing-button">List Store</button>
            </div>
            
            <div class="listing-card" onclick="showForm('publicPlaceForm')">
                <div class="listing-icon"><i class="fas fa-landmark"></i></div>
                <h3 class="listing-title">Public Place</h3>
                <p class="listing-description">List parks, malls, hospitals, and other public locations with visitor information and facilities</p>
                <button class="listing-button">List Place</button>
            </div>
            
            <div class="listing-card" onclick="showForm('realEstateForm')">
                <div class="listing-icon"><i class="fas fa-home"></i></div>
                <h3 class="listing-title">Real Estate</h3>
                <p class="listing-description">List properties for sale or rent with detailed specifications and contact information</p>
                <button class="listing-button">List Property</button>
            </div>
            
            <div class="listing-card" onclick="showForm('jobForm')">
                <div class="listing-icon"><i class="fas fa-briefcase"></i></div>
                <h3 class="listing-title">Job</h3>
                <p class="listing-description">List job opportunities and vacancies with requirements and application details</p>
                <button class="listing-button">List Job</button>
            </div>
        </div>

        <!-- Service Provider Form -->
        <div id="serviceProviderForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-tools"></i> Service Provider Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Basic Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Service Details</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Location</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Documents</div>
                </div>
                <div class="form-step" data-step="5">
                    <div class="form-step-number">5</div>
                    <div class="form-step-label">Subscription</div>
                </div>
                <div class="form-steps-progress" style="width: 20%;"></div>
            </div>
            
            <form id="serviceProviderFormData">
                <div class="form-tab active" data-tab="1">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-info-circle"></i> Basic Information</div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="serviceName" class="form-label required">Business/Service Name</label>
                                <input type="text" class="form-control" id="serviceName" required>
                            </div>
                            <div class="form-group">
                                <label for="serviceType" class="form-label required">Type of Service</label>
                                <select class="form-select" id="serviceType" required>
                                    <option value="">Select service type</option>
                                    <option value="electrician">Electrician</option>
                                    <option value="plumber">Plumber</option>
                                    <option value="carpenter">Carpenter</option>
                                    <option value="painter">Painter</option>
                                    <option value="pest-control">Pest Control</option>
                                    <option value="cleaning">House Cleaning</option>
                                    <option value="ac-repair">AC Repair</option>
                                    <option value="appliance-repair">Appliance Repair</option>
                                    <option value="plumbing">Plumbing Services</option>
                                    <option value="carpentry">Carpentry</option>
                                    <option value="masonry">Masonry</option>
                                    <option value="roofing">Roofing</option>
                                    <option value="welding">Welding</option>
                                    <option value="tiling">Tiling</option>
                                    <option value="fabrication">Fabrication</option>
                                    <option value="gardening">Gardening</option>
                                    <option value="cleaning-commercial">Commercial Cleaning</option>
                                    <option value="moving">Moving Services</option>
                                    <option value="laundry">Laundry Services</option>
                                    <option value="catering">Catering</option>
                                    <option value="event-planning">Event Planning</option>
                                    <option value="photography">Photography</option>
                                    <option value="videography">Videography</option>
                                    <option value="makeup">Makeup Artist</option>
                                    <option value="hair-stylist">Hair Stylist</option>
                                    <option value="tailoring">Tailoring</option>
                                    <option value="driving">Driving Instructor</option>
                                    <option value="tutoring">Tutoring</option>
                                    <option value="fitness">Fitness Trainer</option>
                                    <option value="yoga">Yoga Instructor</option>
                                    <option value="massage">Massage Therapist</option>
                                    <option value="beauty">Beauty Services</option>
                                    <option value="pet-care">Pet Care</option>
                                    <option value="computer-repair">Computer Repair</option>
                                    <option value="mobile-repair">Mobile Repair</option>
                                    <option value="network">Network Services</option>
                                    <option value="security">Security Services</option>
                                    <option value="cctv">CCTV Installation</option>
                                    <option value="interior-design">Interior Design</option>
                                    <option value="architecture">Architecture</option>
                                    <option value="legal">Legal Services</option>
                                    <option value="accounting">Accounting</option>
                                    <option value="tax">Tax Services</option>
                                    <option value="consulting">Business Consulting</option>
                                    <option value="other">Other Service</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="serviceOwner" class="form-label required">Owner Name</label>
                                <input type="text" class="form-control" id="serviceOwner" required>
                            </div>
                            <div class="form-group">
                                <label for="serviceGender" class="form-label">Gender</label>
                                <select class="form-select" id="serviceGender">
                                    <option value="">Select gender</option>
                                    <option value="male">Male</option>
                                    <option value="female">Female</option>
                                    <option value="other">Other</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="servicePhone" class="form-label required">Phone Number</label>
                                <input type="tel" class="form-control" id="servicePhone" required>
                            </div>
                            <div class="form-group">
                                <label for="serviceWhatsApp" class="form-label required">WhatsApp Number</label>
                                <input type="tel" class="form-control" id="serviceWhatsApp" required>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="serviceEmail" class="form-label">Email</label>
                            <input type="email" class="form-control" id="serviceEmail">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1)">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="2">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-clipboard-list"></i> Service Details</div>
                        <div class="form-group">
                            <label for="serviceDescription" class="form-label required">Description of Services Offered</label>
                            <textarea class="form-control form-textarea" id="serviceDescription" required></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label for="serviceAbout" class="form-label">About Service Provider</label>
                            <textarea class="form-control form-textarea" id="serviceAbout" placeholder="Tell us about your experience and qualifications"></textarea>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="serviceExperience" class="form-label">Years of Experience</label>
                                <input type="number" class="form-control" id="serviceExperience" min="0" max="50">
                            </div>
                            <div class="form-group">
                                <label for="servicePricing" class="form-label">Pricing Range</label>
                                <input type="text" class="form-control" id="servicePricing" placeholder="e.g. ₹500 - ₹2000">
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label required">Working Hours & Days</label>
                            <div class="form-date-time">
                                <div class="form-group">
                                    <label for="serviceStartTime" class="form-label">Start Time</label>
                                    <input type="time" class="form-control" id="serviceStartTime">
                                </div>
                                <div class="form-group">
                                    <label for="serviceEndTime" class="form-label">End Time</label>
                                    <input type="time" class="form-control" id="serviceEndTime">
                                </div>
                            </div>
                            <div class="form-group mt-20">
                                <label class="form-label">Working Days</label>
                                <div class="form-checkbox-group">
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="serviceMonday" name="workingDays" value="monday" checked>
                                        <label for="serviceMonday" class="form-checkbox-label">Monday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="serviceTuesday" name="workingDays" value="tuesday" checked>
                                        <label for="serviceTuesday" class="form-checkbox-label">Tuesday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="serviceWednesday" name="workingDays" value="wednesday" checked>
                                        <label for="serviceWednesday" class="form-checkbox-label">Wednesday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="serviceThursday" name="workingDays" value="thursday" checked>
                                        <label for="serviceThursday" class="form-checkbox-label">Thursday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="serviceFriday" name="workingDays" value="friday" checked>
                                        <label for="serviceFriday" class="form-checkbox-label">Friday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="serviceSaturday" name="workingDays" value="saturday">
                                        <label for="serviceSaturday" class="form-checkbox-label">Saturday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="serviceSunday" name="workingDays" value="sunday">
                                        <label for="serviceSunday" class="form-checkbox-label">Sunday</label>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Available Service Modes</label>
                            <div class="form-checkbox-group">
                                <div class="form-checkbox">
                                    <input type="checkbox" id="serviceModeHome" name="serviceModes" value="home" checked>
                                    <label for="serviceModeHome" class="form-checkbox-label">Home Service</label>
                                </div>
                                <div class="form-checkbox">
                                    <input type="checkbox" id="serviceModeOnline" name="serviceModes" value="online">
                                    <label for="serviceModeOnline" class="form-checkbox-label">Online</label>
                                </div>
                                <div class="form-checkbox">
                                    <input type="checkbox" id="serviceModeShop" name="serviceModes" value="shop">
                                    <label for="serviceModeShop" class="form-checkbox-label">In-Shop Only</label>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Languages Spoken</label>
                            <div class="form-checkbox-group">
                                <div class="form-checkbox">
                                    <input type="checkbox" id="serviceLangHindi" name="languages" value="hindi" checked>
                                    <label for="serviceLangHindi" class="form-checkbox-label">Hindi</label>
                                </div>
                                <div class="form-checkbox">
                                    <input type="checkbox" id="serviceLangEnglish" name="languages" value="english">
                                    <label for="serviceLangEnglish" class="form-checkbox-label">English</label>
                                </div>
                                <div class="form-checkbox">
                                    <input type="checkbox" id="serviceLangOther" name="languages" value="other">
                                    <label for="serviceLangOther" class="form-checkbox-label">Other</label>
                                </div>
                            </div>
                            <div class="form-group mt-10" id="serviceLangOtherContainer" style="display: none;">
                                <input type="text" class="form-control" id="serviceLangOtherText" placeholder="Please specify other languages">
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2)">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2)">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="3">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-map-marker-alt"></i> Location Details</div>
                        <div class="form-group">
                            <label for="serviceArea" class="form-label required">Area / Locality of Service</label>
                            <input type="text" class="form-control" id="serviceArea" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="serviceAddress" class="form-label required">Full Business Address</label>
                            <textarea class="form-control form-textarea" id="serviceAddress" required></textarea>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="serviceCity" class="form-label required">City</label>
                                <select class="form-select" id="serviceCity" required>
                                    <option value="">Select city</option>
                                    <option value="delhi">Delhi</option>
                                    <option value="mumbai">Mumbai</option>
                                    <option value="bangalore">Bangalore</option>
                                    <option value="hyderabad">Hyderabad</option>
                                    <option value="chennai">Chennai</option>
                                    <option value="kolkata">Kolkata</option>
                                    <option value="pune">Pune</option>
                                    <option value="ahmedabad">Ahmedabad</option>
                                    <option value="jaipur">Jaipur</option>
                                    <option value="lucknow">Lucknow</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="servicePincode" class="form-label required">Pincode</label>
                                <input type="text" class="form-control" id="servicePincode" required>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="serviceMapsLink" class="form-label">Google Maps Link</label>
                            <input type="url" class="form-control" id="serviceMapsLink" placeholder="https://maps.google.com/...">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3)">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3)">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="4">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-file-upload"></i> Upload Documents</div>
                        
                        <div class="form-group">
                            <label class="form-label required">ID Proof of Owner</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="serviceIdProof" accept=".jpg,.jpeg,.png,.pdf" required>
                                <label for="serviceIdProof" class="file-upload-label">
                                    <i class="fas fa-id-card"></i>
                                    <div class="file-upload-text">Upload ID Proof (PAN/Aadhaar)</div>
                                    <div class="file-upload-hint">Max file size: 5MB (JPG, PNG, PDF)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="serviceIdProofPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Business Proof</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="serviceBusinessProof" accept=".jpg,.jpeg,.png,.pdf">
                                <label for="serviceBusinessProof" class="file-upload-label">
                                    <i class="fas fa-file-contract"></i>
                                    <div class="file-upload-text">Upload Business Proof (GST Certificate/Shop License)</div>
                                    <div class="file-upload-hint">Max file size: 5MB (JPG, PNG, PDF)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="serviceBusinessProofPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Service Photos</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="servicePhotos" accept=".jpg,.jpeg,.png" multiple>
                                <label for="servicePhotos" class="file-upload-label">
                                    <i class="fas fa-images"></i>
                                    <div class="file-upload-text">Upload Service Photos (Max 5)</div>
                                    <div class="file-upload-hint">Max file size: 5MB each (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="servicePhotosPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Business Logo</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="serviceLogo" accept=".jpg,.jpeg,.png">
                                <label for="serviceLogo" class="file-upload-label">
                                    <i class="fas fa-image"></i>
                                    <div class="file-upload-text">Upload Business Logo</div>
                                    <div class="file-upload-hint">Max file size: 2MB (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="serviceLogoPreview"></div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4)">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(4)">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="5">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-credit-card"></i> Subscription Plan</div>
                        
                        <div class="subscription-plans">
                            <div class="subscription-plan" onclick="selectPlan(this, 'basic')">
                                <div class="subscription-plan-name">Basic</div>
                                <div class="subscription-plan-price">₹300</div>
                                <div class="subscription-plan-duration">1 Month Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Basic listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 3 photos</li>
                                    <li>Standard support</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan active" onclick="selectPlan(this, 'standard')">
                                <div class="subscription-plan-name">Standard</div>
                                <div class="subscription-plan-price">₹800</div>
                                <div class="subscription-plan-duration">3 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Higher listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 5 photos</li>
                                    <li>Priority support</li>
                                    <li>Basic analytics</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'premium')">
                                <div class="subscription-plan-name">Premium</div>
                                <div class="subscription-plan-price">₹1200</div>
                                <div class="subscription-plan-duration">6 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Top listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 10 photos</li>
                                    <li>24/7 support</li>
                                    <li>Advanced analytics</li>
                                    <li>Featured badge</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'enterprise')">
                                <div class="subscription-plan-name">Enterprise</div>
                                <div class="subscription-plan-price">₹2000</div>
                                <div class="subscription-plan-duration">12 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Highest listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Unlimited photos</li>
                                    <li>24/7 VIP support</li>
                                    <li>Full analytics</li>
                                    <li>Featured badge</li>
                                    <li>Social media promotion</li>
                                </ul>
                            </div>
                        </div>
                        
                        <input type="hidden" id="servicePlan" value="standard">
                        
                        <div class="form-group">
                            <div class="form-checkbox">
                                <input type="checkbox" id="serviceVerification" name="verification">
                                <label for="serviceVerification" class="form-checkbox-label">Verified Listing (Additional ₹200)</label>
                                <span class="tooltip">
                                    <i class="fas fa-info-circle tooltip-icon"></i>
                                    <span class="tooltip-text">Verified listings include a verification badge after our team confirms your details</span>
                                </span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-share-alt"></i> Social Media Links</div>
                        
                        <div class="form-group">
                            <label for="serviceInstagram" class="form-label">Instagram Link</label>
                            <input type="url" class="form-control" id="serviceInstagram" placeholder="https://instagram.com/yourprofile">
                        </div>
                        
                        <div class="form-group">
                            <label for="serviceFacebook" class="form-label">Facebook Link</label>
                            <input type="url" class="form-control" id="serviceFacebook" placeholder="https://facebook.com/yourpage">
                        </div>
                        
                        <div class="form-group">
                            <label for="serviceOffers" class="form-label">Any Offers/Deals</label>
                            <textarea class="form-control form-textarea" id="serviceOffers" placeholder="List any current offers or deals for customers"></textarea>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(5)">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        </div>

        <!-- Store Form -->
        <div id="storeForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-store"></i> Store Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Basic Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Store Details</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Location</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Uploads</div>
                </div>
                <div class="form-step" data-step="5">
                    <div class="form-step-number">5</div>
                    <div class="form-step-label">Subscription</div>
                </div>
                <div class="form-steps-progress" style="width: 20%;"></div>
            </div>
            
            <form id="storeFormData">
                <div class="form-tab active" data-tab="1">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-info-circle"></i> Basic Store Information</div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="storeName" class="form-label required">Store Name</label>
                                <input type="text" class="form-control" id="storeName" required>
                            </div>
                            <div class="form-group">
                                <label for="storeCategory" class="form-label required">Category</label>
                                <select class="form-select" id="storeCategory" required>
                                    <option value="">Select store category</option>
                                    <option value="grocery">Grocery Store</option>
                                    <option value="electronics">Electronics</option>
                                    <option value="clothing">Clothing</option>
                                    <option value="pharmacy">Pharmacy</option>
                                    <option value="furniture">Furniture</option>
                                    <option value="jewelry">Jewelry</option>
                                    <option value="footwear">Footwear</option>
                                    <option value="books">Books & Stationery</option>
                                    <option value="sports">Sports Goods</option>
                                    <option value="toys">Toys & Games</option>
                                    <option value="beauty">Beauty Products</option>
                                    <option value="hardware">Hardware</option>
                                    <option value="automobile">Automobile Parts</option>
                                    <option value="pet">Pet Supplies</option>
                                    <option value="gift">Gift Shop</option>
                                    <option value="liquor">Liquor Store</option>
                                    <option value="organic">Organic Products</option>
                                    <option value="handicrafts">Handicrafts</option>
                                    <option value="flowers">Flower Shop</option>
                                    <option value="bakery">Bakery</option>
                                    <option value="butcher">Butcher Shop</option>
                                    <option value="fish">Fish Market</option>
                                    <option value="vegetables">Vegetable Market</option>
                                    <option value="fruits">Fruit Market</option>
                                    <option value="dairy">Dairy Products</option>
                                    <option value="sweets">Sweet Shop</option>
                                    <option value="tea">Tea & Coffee</option>
                                    <option value="spices">Spices</option>
                                    <option value="mobile">Mobile Store</option>
                                    <option value="computer">Computer Store</option>
                                    <option value="bicycle">Bicycle Shop</option>
                                    <option value="fabric">Fabric Store</option>
                                    <option value="other">Other</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="storeOwner" class="form-label required">Owner Name</label>
                                <input type="text" class="form-control" id="storeOwner" required>
                            </div>
                            <div class="form-group">
                                <label for="storePhone" class="form-label required">Phone Number / WhatsApp</label>
                                <input type="tel" class="form-control" id="storePhone" required>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="storeTimings" class="form-label required">Store Timings</label>
                            <div class="form-date-time">
                                <div class="form-group">
                                    <label for="storeOpenTime" class="form-label">Opening Time</label>
                                    <input type="time" class="form-control" id="storeOpenTime">
                                </div>
                                <div class="form-group">
                                    <label for="storeCloseTime" class="form-label">Closing Time</label>
                                    <input type="time" class="form-control" id="storeCloseTime">
                                </div>
                            </div>
                            <div class="form-group mt-20">
                                <label class="form-label">Working Days</label>
                                <div class="form-checkbox-group">
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="storeMonday" name="storeWorkingDays" value="monday" checked>
                                        <label for="storeMonday" class="form-checkbox-label">Monday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="storeTuesday" name="storeWorkingDays" value="tuesday" checked>
                                        <label for="storeTuesday" class="form-checkbox-label">Tuesday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="storeWednesday" name="storeWorkingDays" value="wednesday" checked>
                                        <label for="storeWednesday" class="form-checkbox-label">Wednesday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="storeThursday" name="storeWorkingDays" value="thursday" checked>
                                        <label for="storeThursday" class="form-checkbox-label">Thursday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="storeFriday" name="storeWorkingDays" value="friday" checked>
                                        <label for="storeFriday" class="form-checkbox-label">Friday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="storeSaturday" name="storeWorkingDays" value="saturday">
                                        <label for="storeSaturday" class="form-checkbox-label">Saturday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="storeSunday" name="storeWorkingDays" value="sunday">
                                        <label for="storeSunday" class="form-checkbox-label">Sunday</label>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'store')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="2">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-clipboard-list"></i> Store Information</div>
                        <div class="form-group">
                            <label for="storeDescription" class="form-label required">Store Description</label>
                            <textarea class="form-control form-textarea" id="storeDescription" required></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label for="storeShortDescription" class="form-label">Short Description (Max 150 characters)</label>
                            <textarea class="form-control form-textarea" id="storeShortDescription" maxlength="150"></textarea>
                            <div class="form-feedback" id="storeShortDescriptionCounter">0/150</div>
                        </div>
                        
                        <div class="form-group">
                            <label for="storeProducts" class="form-label">List of Products/Brands Sold</label>
                            <textarea class="form-control form-textarea" id="storeProducts" placeholder="List your main products or brands separated by commas"></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label for="storeOffers" class="form-label">Offers/Discounts</label>
                            <textarea class="form-control form-textarea" id="storeOffers" placeholder="List any current offers or discounts"></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Payment Options Available</label>
                            <div class="form-checkbox-group">
                                <div class="form-checkbox">
                                    <input type="checkbox" id="storePaymentCash" name="paymentOptions" value="cash" checked>
                                    <label for="storePaymentCash" class="form-checkbox-label">Cash</label>
                                </div>
                                <div class="form-checkbox">
                                    <input type="checkbox" id="storePaymentCard" name="paymentOptions" value="card">
                                    <label for="storePaymentCard" class="form-checkbox-label">Card</label>
                                </div>
                                <div class="form-checkbox">
                                    <input type="checkbox" id="storePaymentUPI" name="paymentOptions" value="upi">
                                    <label for="storePaymentUPI" class="form-checkbox-label">UPI</label>
                                </div>
                                <div class="form-checkbox">
                                    <input type="checkbox" id="storePaymentEMI" name="paymentOptions" value="emi">
                                    <label for="storePaymentEMI" class="form-checkbox-label">EMI</label>
                                </div>
                                <div class="form-checkbox">
                                    <input type="checkbox" id="storePaymentOther" name="paymentOptions" value="other">
                                    <label for="storePaymentOther" class="form-checkbox-label">Other</label>
                                </div>
                            </div>
                            <div class="form-group mt-10" id="storePaymentOtherContainer" style="display: none;">
                                <input type="text" class="form-control" id="storePaymentOtherText" placeholder="Please specify other payment options">
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Home Delivery Available</label>
                            <div class="form-radio-group">
                                <div class="form-radio">
                                    <input type="radio" id="storeDeliveryYes" name="delivery" value="yes">
                                    <label for="storeDeliveryYes" class="form-radio-label">Yes</label>
                                </div>
                                <div class="form-radio">
                                    <input type="radio" id="storeDeliveryNo" name="delivery" value="no" checked>
                                    <label for="storeDeliveryNo" class="form-radio-label">No</label>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-group" id="storeDeliveryDetails" style="display: none;">
                            <label for="storeDeliveryInfo" class="form-label">Delivery Information</label>
                            <textarea class="form-control form-textarea" id="storeDeliveryInfo" placeholder="Provide details about delivery areas, charges, and minimum order"></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label for="storeReturnPolicy" class="form-label">Return/Exchange Policy Info</label>
                            <textarea class="form-control form-textarea" id="storeReturnPolicy" placeholder="Describe your return/exchange policy"></textarea>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'store')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'store')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="3">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-map-marked-alt"></i> Store Location</div>
                        <div class="form-group">
                            <label for="storeAddress" class="form-label required">Full Address</label>
                            <textarea class="form-control form-textarea" id="storeAddress" required></textarea>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="storePincode" class="form-label required">Pincode</label>
                                <input type="text" class="form-control" id="storePincode" required>
                            </div>
                            <div class="form-group">
                                <label for="storeCity" class="form-label required">City</label>
                                <select class="form-select" id="storeCity" required>
                                    <option value="">Select city</option>
                                    <option value="delhi">Delhi</option>
                                    <option value="mumbai">Mumbai</option>
                                    <option value="bangalore">Bangalore</option>
                                    <option value="hyderabad">Hyderabad</option>
                                    <option value="chennai">Chennai</option>
                                    <option value="kolkata">Kolkata</option>
                                    <option value="pune">Pune</option>
                                    <option value="ahmedabad">Ahmedabad</option>
                                    <option value="jaipur">Jaipur</option>
                                    <option value="lucknow">Lucknow</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="storeLandmark" class="form-label">Landmark</label>
                            <input type="text" class="form-control" id="storeLandmark" placeholder="Nearby well-known place">
                        </div>
                        
                        <div class="form-group">
                            <label for="storeMapsLink" class="form-label">Google Maps Link</label>
                            <input type="url" class="form-control" id="storeMapsLink" placeholder="https://maps.google.com/...">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'store')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'store')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="4">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-images"></i> Upload Section</div>
                        
                        <div class="form-group">
                            <label class="form-label required">Store Front Image</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="storeFrontImage" accept=".jpg,.jpeg,.png" required>
                                <label for="storeFrontImage" class="file-upload-label">
                                    <i class="fas fa-store"></i>
                                    <div class="file-upload-text">Upload Store Front Image</div>
                                    <div class="file-upload-hint">Max file size: 5MB (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="storeFrontImagePreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Inside Store Images (Max 5)</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="storeInsideImages" accept=".jpg,.jpeg,.png" multiple>
                                <label for="storeInsideImages" class="file-upload-label">
                                    <i class="fas fa-image"></i>
                                    <div class="file-upload-text">Upload Inside Store Images</div>
                                    <div class="file-upload-hint">Max file size: 5MB each (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="storeInsideImagesPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Product/Display Images (Max 5)</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="storeProductImages" accept=".jpg,.jpeg,.png" multiple>
                                <label for="storeProductImages" class="file-upload-label">
                                    <i class="fas fa-box-open"></i>
                                    <div class="file-upload-text">Upload Product/Display Images</div>
                                    <div class="file-upload-hint">Max file size: 5MB each (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="storeProductImagesPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Store Logo</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="storeLogo" accept=".jpg,.jpeg,.png">
                                <label for="storeLogo" class="file-upload-label">
                                    <i class="fas fa-camera"></i>
                                    <div class="file-upload-text">Upload Store Logo</div>
                                    <div class="file-upload-hint">Max file size: 2MB (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="storeLogoPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">GST Certificate</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="storeGstCertificate" accept=".jpg,.jpeg,.png,.pdf">
                                <label for="storeGstCertificate" class="file-upload-label">
                                    <i class="fas fa-file-invoice"></i>
                                    <div class="file-upload-text">Upload GST Certificate</div>
                                    <div class="file-upload-hint">Max file size: 5MB (JPG, PNG, PDF)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="storeGstCertificatePreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Shop License</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="storeLicense" accept=".jpg,.jpeg,.png,.pdf">
                                <label for="storeLicense" class="file-upload-label">
                                    <i class="fas fa-file-signature"></i>
                                    <div class="file-upload-text">Upload Shop License</div>
                                    <div class="file-upload-hint">Max file size: 5MB (JPG, PNG, PDF)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="storeLicensePreview"></div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'store')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(4, 'store')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="5">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-credit-card"></i> Subscription Plan</div>
                        
                        <div class="subscription-plans">
                            <div class="subscription-plan" onclick="selectPlan(this, 'basic', 'store')">
                                <div class="subscription-plan-name">Basic</div>
                                <div class="subscription-plan-price">₹300</div>
                                <div class="subscription-plan-duration">1 Month Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Basic listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 3 photos</li>
                                    <li>Standard support</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan active" onclick="selectPlan(this, 'standard', 'store')">
                                <div class="subscription-plan-name">Standard</div>
                                <div class="subscription-plan-price">₹800</div>
                                <div class="subscription-plan-duration">3 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Higher listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 5 photos</li>
                                    <li>Priority support</li>
                                    <li>Basic analytics</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'premium', 'store')">
                                <div class="subscription-plan-name">Premium</div>
                                <div class="subscription-plan-price">₹1200</div>
                                <div class="subscription-plan-duration">6 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Top listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 10 photos</li>
                                    <li>24/7 support</li>
                                    <li>Advanced analytics</li>
                                    <li>Featured badge</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'enterprise', 'store')">
                                <div class="subscription-plan-name">Enterprise</div>
                                <div class="subscription-plan-price">₹2000</div>
                                <div class="subscription-plan-duration">12 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Highest listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Unlimited photos</li>
                                    <li>24/7 VIP support</li>
                                    <li>Full analytics</li>
                                    <li>Featured badge</li>
                                    <li>Social media promotion</li>
                                </ul>
                            </div>
                        </div>
                        
                        <input type="hidden" id="storePlan" value="standard">
                        
                        <div class="form-group">
                            <div class="form-checkbox">
                                <input type="checkbox" id="storeVerification" name="verification">
                                <label for="storeVerification" class="form-checkbox-label">Verified Listing (Additional ₹200)</label>
                                <span class="tooltip">
                                    <i class="fas fa-info-circle tooltip-icon"></i>
                                    <span class="tooltip-text">Verified listings include a verification badge after our team confirms your details</span>
                                </span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-share-alt"></i> Social Media Links</div>
                        
                        <div class="form-group">
                            <label for="storeInstagram" class="form-label">Instagram Link</label>
                            <input type="url" class="form-control" id="storeInstagram" placeholder="https://instagram.com/yourstore">
                        </div>
                        
                        <div class="form-group">
                            <label for="storeFacebook" class="form-label">Facebook Link</label>
                            <input type="url" class="form-control" id="storeFacebook" placeholder="https://facebook.com/yourstore">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(5, 'store')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        </div>

        <!-- Public Place Form -->
        <div id="publicPlaceForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-landmark"></i> Public Place Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Basic Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Place Details</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Location</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Uploads</div>
                </div>
                <div class="form-step" data-step="5">
                    <div class="form-step-number">5</div>
                    <div class="form-step-label">Subscription</div>
                </div>
                <div class="form-steps-progress" style="width: 20%;"></div>
            </div>
            
            <form id="publicPlaceFormData">
                <div class="form-tab active" data-tab="1">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-info-circle"></i> Basic Information</div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="placeName" class="form-label required">Name of Public Place</label>
                                <input type="text" class="form-control" id="placeName" required>
                            </div>
                            <div class="form-group">
                                <label for="placeCategory" class="form-label required">Category</label>
                                <select class="form-select" id="placeCategory" required>
                                    <option value="">Select place category</option>
                                    <option value="park">Park</option>
                                    <option value="hospital">Hospital</option>
                                    <option value="mall">Shopping Mall</option>
                                    <option value="school">School</option>
                                    <option value="college">College</option>
                                    <option value="library">Library</option>
                                    <option value="museum">Museum</option>
                                    <option value="temple">Temple</option>
                                    <option value="mosque">Mosque</option>
                                    <option value="church">Church</option>
                                    <option value="gurudwara">Gurudwara</option>
                                    <option value="community-center">Community Center</option>
                                    <option value="stadium">Stadium</option>
                                    <option value="gym">Gym</option>
                                    <option value="swimming-pool">Swimming Pool</option>
                                    <option value="playground">Playground</option>
                                    <option value="theater">Theater</option>
                                    <option value="cinema">Cinema</option>
                                    <option value="restaurant">Restaurant</option>
                                    <option value="cafe">Cafe</option>
                                    <option value="hotel">Hotel</option>
                                    <option value="resort">Resort</option>
                                    <option value="bus-stand">Bus Stand</option>
                                    <option value="railway-station">Railway Station</option>
                                    <option value="airport">Airport</option>
                                    <option value="metro-station">Metro Station</option>
                                    <option value="police-station">Police Station</option>
                                    <option value="fire-station">Fire Station</option>
                                    <option value="post-office">Post Office</option>
                                    <option value="bank">Bank</option>
                                    <option value="atm">ATM</option>
                                    <option value="market">Market</option>
                                    <option value="pharmacy">Pharmacy</option>
                                    <option value="clinic">Clinic</option>
                                    <option value="diagnostic-center">Diagnostic Center</option>
                                    <option value="petrol-pump">Petrol Pump</option>
                                    <option value="car-wash">Car Wash</option>
                                    <option value="other">Other</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="placeContactPerson" class="form-label required">Contact Person Name</label>
                                <input type="text" class="form-control" id="placeContactPerson" required>
                            </div>
                            <div class="form-group">
                                <label for="placePhone" class="form-label required">Contact Number / WhatsApp</label>
                                <input type="tel" class="form-control" id="placePhone" required>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="placeWebsite" class="form-label">Website</label>
                                <input type="url" class="form-control" id="placeWebsite" placeholder="https://example.com">
                            </div>
                            <div class="form-group">
                                <label for="placeEmail" class="form-label">Email</label>
                                <input type="email" class="form-control" id="placeEmail">
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'place')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="2">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-clipboard-list"></i> Place Details</div>
                        <div class="form-group">
                            <label for="placeDescription" class="form-label required">Overview Description</label>
                            <textarea class="form-control form-textarea" id="placeDescription" required></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label required">Open Hours & Days</label>
                            <div class="form-date-time">
                                <div class="form-group">
                                    <label for="placeOpenTime" class="form-label">Opening Time</label>
                                    <input type="time" class="form-control" id="placeOpenTime">
                                </div>
                                <div class="form-group">
                                    <label for="placeCloseTime" class="form-label">Closing Time</label>
                                    <input type="time" class="form-control" id="placeCloseTime">
                                </div>
                            </div>
                            <div class="form-group mt-20">
                                <label class="form-label">Open Days</label>
                                <div class="form-checkbox-group">
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="placeMonday" name="placeOpenDays" value="monday" checked>
                                        <label for="placeMonday" class="form-checkbox-label">Monday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="placeTuesday" name="placeOpenDays" value="tuesday" checked>
                                        <label for="placeTuesday" class="form-checkbox-label">Tuesday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="placeWednesday" name="placeOpenDays" value="wednesday" checked>
                                        <label for="placeWednesday" class="form-checkbox-label">Wednesday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="placeThursday" name="placeOpenDays" value="thursday" checked>
                                        <label for="placeThursday" class="form-checkbox-label">Thursday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="placeFriday" name="placeOpenDays" value="friday" checked>
                                        <label for="placeFriday" class="form-checkbox-label">Friday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="placeSaturday" name="placeOpenDays" value="saturday">
                                        <label for="placeSaturday" class="form-checkbox-label">Saturday</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="placeSunday" name="placeOpenDays" value="sunday">
                                        <label for="placeSunday" class="form-checkbox-label">Sunday</label>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="placeEntryFee" class="form-label">Entry Fee</label>
                            <input type="text" class="form-control" id="placeEntryFee" placeholder="e.g. Free, ₹50, ₹100-200">
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Facilities Available</label>
                            <div class="features-checklist">
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityParking" name="facilities" value="parking">
                                    <label for="placeFacilityParking" class="feature-checkbox-label">Parking</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityWashrooms" name="facilities" value="washrooms">
                                    <label for="placeFacilityWashrooms" class="feature-checkbox-label">Washrooms</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityWifi" name="facilities" value="wifi">
                                    <label for="placeFacilityWifi" class="feature-checkbox-label">WiFi</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityWheelchair" name="facilities" value="wheelchair">
                                    <label for="placeFacilityWheelchair" class="feature-checkbox-label">Wheelchair Access</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityCafeteria" name="facilities" value="cafeteria">
                                    <label for="placeFacilityCafeteria" class="feature-checkbox-label">Cafeteria</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityFirstAid" name="facilities" value="first-aid">
                                    <label for="placeFacilityFirstAid" class="feature-checkbox-label">First Aid</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityDrinkingWater" name="facilities" value="drinking-water">
                                    <label for="placeFacilityDrinkingWater" class="feature-checkbox-label">Drinking Water</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilitySecurity" name="facilities" value="security">
                                    <label for="placeFacilitySecurity" class="feature-checkbox-label">Security</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityAtm" name="facilities" value="atm">
                                    <label for="placeFacilityAtm" class="feature-checkbox-label">ATM</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="placeFacilityOther" name="facilities" value="other">
                                    <label for="placeFacilityOther" class="feature-checkbox-label">Other</label>
                                </div>
                            </div>
                            <div class="form-group mt-10" id="placeFacilityOtherContainer" style="display: none;">
                                <input type="text" class="form-control" id="placeFacilityOtherText" placeholder="Please specify other facilities">
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="placeAreaSize" class="form-label">Area Size</label>
                                <input type="text" class="form-control" id="placeAreaSize" placeholder="e.g. 5 acres, 10,000 sq ft">
                            </div>
                            <div class="form-group">
                                <label for="placeParkingCharges" class="form-label">Parking Charges</label>
                                <input type="text" class="form-control" id="placeParkingCharges" placeholder="e.g. Free, ₹20/hour, ₹50 flat">
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="placeVisitorGuidelines" class="form-label">Visitor Guidelines</label>
                            <textarea class="form-control form-textarea" id="placeVisitorGuidelines" placeholder="List any specific guidelines for visitors"></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Pet Friendly</label>
                            <div class="form-radio-group">
                                <div class="form-radio">
                                    <input type="radio" id="placePetFriendlyYes" name="petFriendly" value="yes">
                                    <label for="placePetFriendlyYes" class="form-radio-label">Yes</label>
                                </div>
                                <div class="form-radio">
                                    <input type="radio" id="placePetFriendlyNo" name="petFriendly" value="no" checked>
                                    <label for="placePetFriendlyNo" class="form-radio-label">No</label>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'place')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'place')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="3">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-map-marker-alt"></i> Location</div>
                        <div class="form-group">
                            <label for="placeAddress" class="form-label required">Complete Address</label>
                            <textarea class="form-control form-textarea" id="placeAddress" required></textarea>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="placeCity" class="form-label required">City</label>
                                <select class="form-select" id="placeCity" required>
                                    <option value="">Select city</option>
                                    <option value="delhi">Delhi</option>
                                    <option value="mumbai">Mumbai</option>
                                    <option value="bangalore">Bangalore</option>
                                    <option value="hyderabad">Hyderabad</option>
                                    <option value="chennai">Chennai</option>
                                    <option value="kolkata">Kolkata</option>
                                    <option value="pune">Pune</option>
                                    <option value="ahmedabad">Ahmedabad</option>
                                    <option value="jaipur">Jaipur</option>
                                    <option value="lucknow">Lucknow</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="placePincode" class="form-label required">Pincode</label>
                                <input type="text" class="form-control" id="placePincode" required>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="placeMapsLink" class="form-label">Google Maps Link</label>
                            <input type="url" class="form-control" id="placeMapsLink" placeholder="https://maps.google.com/...">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'place')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'place')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="4">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-images"></i> Images Carousel</div>
                        
                        <div class="form-group">
                            <label class="form-label required">Images (5-8 recommended)</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="placeImages" accept=".jpg,.jpeg,.png" multiple required>
                                <label for="placeImages" class="file-upload-label">
                                    <i class="fas fa-images"></i>
                                    <div class="file-upload-text">Upload Place Images</div>
                                    <div class="file-upload-hint">Max file size: 5MB each (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="placeImagesPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Logo/Entry Signboard</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="placeLogo" accept=".jpg,.jpeg,.png">
                                <label for="placeLogo" class="file-upload-label">
                                    <i class="fas fa-camera"></i>
                                    <div class="file-upload-text">Upload Logo/Signboard</div>
                                    <div class="file-upload-hint">Max file size: 2MB (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="placeLogoPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Brochure/Pamphlet (PDF)</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="placeBrochure" accept=".pdf">
                                <label for="placeBrochure" class="file-upload-label">
                                    <i class="fas fa-file-pdf"></i>
                                    <div class="file-upload-text">Upload Brochure (PDF)</div>
                                    <div class="file-upload-hint">Max file size: 5MB (PDF only)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="placeBrochurePreview"></div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'place')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(4, 'place')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="5">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-credit-card"></i> Subscription Plan</div>
                        
                        <div class="subscription-plans">
                            <div class="subscription-plan" onclick="selectPlan(this, 'basic', 'place')">
                                <div class="subscription-plan-name">Basic</div>
                                <div class="subscription-plan-price">₹300</div>
                                <div class="subscription-plan-duration">1 Month Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Basic listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 5 photos</li>
                                    <li>Standard support</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan active" onclick="selectPlan(this, 'standard', 'place')">
                                <div class="subscription-plan-name">Standard</div>
                                <div class="subscription-plan-price">₹800</div>
                                <div class="subscription-plan-duration">3 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Higher listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 8 photos</li>
                                    <li>Priority support</li>
                                    <li>Basic analytics</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'premium', 'place')">
                                <div class="subscription-plan-name">Premium</div>
                                <div class="subscription-plan-price">₹1200</div>
                                <div class="subscription-plan-duration">6 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Top listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 15 photos</li>
                                    <li>24/7 support</li>
                                    <li>Advanced analytics</li>
                                    <li>Featured badge</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'enterprise', 'place')">
                                <div class="subscription-plan-name">Enterprise</div>
                                <div class="subscription-plan-price">₹2000</div>
                                <div class="subscription-plan-duration">12 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Highest listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Unlimited photos</li>
                                    <li>24/7 VIP support</li>
                                    <li>Full analytics</li>
                                    <li>Featured badge</li>
                                    <li>Social media promotion</li>
                                </ul>
                            </div>
                        </div>
                        
                        <input type="hidden" id="placePlan" value="standard">
                        
                        <div class="form-group">
                            <div class="form-checkbox">
                                <input type="checkbox" id="placeVerification" name="verification">
                                <label for="placeVerification" class="form-checkbox-label">Verified Listing (Additional ₹200)</label>
                                <span class="tooltip">
                                    <i class="fas fa-info-circle tooltip-icon"></i>
                                    <span class="tooltip-text">Verified listings include a verification badge after our team confirms your details</span>
                                </span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-share-alt"></i> Social Media Links</div>
                        
                        <div class="form-group">
                            <label for="placeInstagram" class="form-label">Instagram Link</label>
                            <input type="url" class="form-control" id="placeInstagram" placeholder="https://instagram.com/yourplace">
                        </div>
                        
                        <div class="form-group">
                            <label for="placeFacebook" class="form-label">Facebook Link</label>
                            <input type="url" class="form-control" id="placeFacebook" placeholder="https://facebook.com/yourplace">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(5, 'place')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        </div>

        <!-- Real Estate Form -->
        <div id="realEstateForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-home"></i> Real Estate Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Property Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Owner/Agent</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Property Details</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Location</div>
                </div>
                <div class="form-step" data-step="5">
                    <div class="form-step-number">5</div>
                    <div class="form-step-label">Uploads</div>
                </div>
                <div class="form-step" data-step="6">
                    <div class="form-step-number">6</div>
                    <div class="form-step-label">Subscription</div>
                </div>
                <div class="form-steps-progress" style="width: 16.66%;"></div>
            </div>
            
            <form id="realEstateFormData">
                <div class="form-tab active" data-tab="1">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-home"></i> Property Type</div>
                        <div class="form-group">
                            <label for="propertyType" class="form-label required">Property Type</label>
                            <select class="form-select" id="propertyType" required>
                                <option value="">Select property type</option>
                                <option value="residential">Residential</option>
                                <option value="commercial">Commercial</option>
                                <option value="land">Land</option>
                                <option value="rental">Rental</option>
                            </select>
                        </div>
                        
                        <div id="propertyResidentialContainer" style="display: none;">
                            <div class="form-group">
                                <label for="propertyResidentialType" class="form-label required">Residential Type</label>
                                <select class="form-select" id="propertyResidentialType">
                                    <option value="">Select residential type</option>
                                    <option value="apartment">Apartment</option>
                                    <option value="villa">Villa</option>
                                    <option value="house">Independent House</option>
                                    <option value="plot">Plot</option>
                                    <option value="farm-house">Farm House</option>
                                    <option value="penthouse">Penthouse</option>
                                    <option value="studio">Studio Apartment</option>
                                    <option value="builder-floor">Builder Floor</option>
                                </select>
                            </div>
                        </div>
                        
                        <div id="propertyCommercialContainer" style="display: none;">
                            <div class="form-group">
                                <label for="propertyCommercialType" class="form-label required">Commercial Type</label>
                                <select class="form-select" id="propertyCommercialType">
                                    <option value="">Select commercial type</option>
                                    <option value="office">Office Space</option>
                                    <option value="shop">Shop/Retail</option>
                                    <option value="warehouse">Warehouse</option>
                                    <option value="industrial">Industrial</option>
                                    <option value="hotel">Hotel</option>
                                    <option value="restaurant">Restaurant</option>
                                    <option value="hospital">Hospital/Clinic</option>
                                    <option value="school">School/College</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="propertyName" class="form-label">Property Name/Label</label>
                            <input type="text" class="form-control" id="propertyName" placeholder="e.g. Sunshine Apartments, Green Valley Villa">
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label required">New/Resale</label>
                            <div class="form-radio-group">
                                <div class="form-radio">
                                    <input type="radio" id="propertyNew" name="propertyAge" value="new" checked>
                                    <label for="propertyNew" class="form-radio-label">New</label>
                                </div>
                                <div class="form-radio">
                                    <input type="radio" id="propertyResale" name="propertyAge" value="resale">
                                    <label for="propertyResale" class="form-radio-label">Resale</label>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'realEstate')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="2">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-user-tie"></i> Contact Information</div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="propertyContact" class="form-label required">Contact Name</label>
                                <input type="text" class="form-control" id="propertyContact" required>
                            </div>
                            <div class="form-group">
                                <label for="propertyPhone" class="form-label required">Phone Number</label>
                                <input type="tel" class="form-control" id="propertyPhone" required>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="propertyEmail" class="form-label">Email</label>
                                <input type="email" class="form-control" id="propertyEmail">
                            </div>
                            <div class="form-group">
                                <label for="propertyCompany" class="form-label">Company Name</label>
                                <input type="text" class="form-control" id="propertyCompany">
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="propertyWhatsApp" class="form-label">WhatsApp Number</label>
                            <input type="tel" class="form-control" id="propertyWhatsApp">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'realEstate')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'realEstate')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="3">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-info-circle"></i> Property Details</div>
                        <div class="form-group">
                            <label for="propertyDescription" class="form-label required">Description</label>
                            <textarea class="form-control form-textarea" id="propertyDescription" required></textarea>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="propertyArea" class="form-label required">Carpet Area/Built-up Area (sq ft)</label>
                                <input type="number" class="form-control" id="propertyArea" required>
                            </div>
                            <div class="form-group">
                                <label for="propertyPrice" class="form-label required">Price</label>
                                <input type="text" class="form-control" id="propertyPrice" required>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="propertyFurnishing" class="form-label">Furnishing Details</label>
                                <select class="form-select" id="propertyFurnishing">
                                    <option value="">Select furnishing</option>
                                    <option value="furnished">Furnished</option>
                                    <option value="semi-furnished">Semi-Furnished</option>
                                    <option value="unfurnished">Unfurnished</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="propertyAge" class="form-label">Age of Property</label>
                                <select class="form-select" id="propertyAge">
                                    <option value="">Select age</option>
                                    <option value="new">New Construction</option>
                                    <option value="0-5">0-5 years</option>
                                    <option value="5-10">5-10 years</option>
                                    <option value="10-20">10-20 years</option>
                                    <option value="20+">20+ years</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="propertyBedrooms" class="form-label">Bedrooms</label>
                                <select class="form-select" id="propertyBedrooms">
                                    <option value="">Select bedrooms</option>
                                    <option value="1">1</option>
                                    <option value="2">2</option>
                                    <option value="3">3</option>
                                    <option value="4">4</option>
                                    <option value="5+">5+</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="propertyBathrooms" class="form-label">Bathrooms</label>
                                <select class="form-select" id="propertyBathrooms">
                                    <option value="">Select bathrooms</option>
                                    <option value="1">1</option>
                                    <option value="2">2</option>
                                    <option value="3">3</option>
                                    <option value="4+">4+</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="propertyAvailability" class="form-label">Availability Status</label>
                            <select class="form-select" id="propertyAvailability">
                                <option value="available">Available Now</option>
                                <option value="soon">Available Soon</option>
                                <option value="sold">Sold/Booked</option>
                            </select>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Amenities</label>
                            <div class="features-checklist">
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityParking" name="amenities" value="parking">
                                    <label for="propertyAmenityParking" class="feature-checkbox-label">Parking</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityLift" name="amenities" value="lift">
                                    <label for="propertyAmenityLift" class="feature-checkbox-label">Lift</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityPower" name="amenities" value="power">
                                    <label for="propertyAmenityPower" class="feature-checkbox-label">Power Backup</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenitySecurity" name="amenities" value="security">
                                    <label for="propertyAmenitySecurity" class="feature-checkbox-label">Security</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityGarden" name="amenities" value="garden">
                                    <label for="propertyAmenityGarden" class="feature-checkbox-label">Garden</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityGym" name="amenities" value="gym">
                                    <label for="propertyAmenityGym" class="feature-checkbox-label">Gym</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityPool" name="amenities" value="pool">
                                    <label for="propertyAmenityPool" class="feature-checkbox-label">Swimming Pool</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityClub" name="amenities" value="club">
                                    <label for="propertyAmenityClub" class="feature-checkbox-label">Club House</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityWater" name="amenities" value="water">
                                    <label for="propertyAmenityWater" class="feature-checkbox-label">24/7 Water</label>
                                </div>
                                <div class="feature-checkbox">
                                    <input type="checkbox" id="propertyAmenityOther" name="amenities" value="other">
                                    <label for="propertyAmenityOther" class="feature-checkbox-label">Other</label>
                                </div>
                            </div>
                            <div class="form-group mt-10" id="propertyAmenityOtherContainer" style="display: none;">
                                <input type="text" class="form-control" id="propertyAmenityOtherText" placeholder="Please specify other amenities">
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'realEstate')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'realEstate')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="4">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-map-marker-alt"></i> Location</div>
                        <div class="form-group">
                            <label for="propertyAddress" class="form-label required">Full Address</label>
                            <textarea class="form-control form-textarea" id="propertyAddress" required></textarea>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="propertyCity" class="form-label required">City</label>
                                <select class="form-select" id="propertyCity" required>
                                    <option value="">Select city</option>
                                    <option value="delhi">Delhi</option>
                                    <option value="mumbai">Mumbai</option>
                                    <option value="bangalore">Bangalore</option>
                                    <option value="hyderabad">Hyderabad</option>
                                    <option value="chennai">Chennai</option>
                                    <option value="kolkata">Kolkata</option>
                                    <option value="pune">Pune</option>
                                    <option value="ahmedabad">Ahmedabad</option>
                                    <option value="jaipur">Jaipur</option>
                                    <option value="lucknow">Lucknow</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="propertyPincode" class="form-label required">Pincode</label>
                                <input type="text" class="form-control" id="propertyPincode" required>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="propertyLandmark" class="form-label">Landmark</label>
                            <input type="text" class="form-control" id="propertyLandmark" placeholder="Nearby well-known place">
                        </div>
                        
                        <div class="form-group">
                            <label for="propertyMapsLink" class="form-label">Google Maps Link</label>
                            <input type="url" class="form-control" id="propertyMapsLink" placeholder="https://maps.google.com/...">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'realEstate')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(4, 'realEstate')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="5">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-images"></i> Property Images</div>
                        
                        <div class="form-group">
                            <label class="form-label required">Property Images (Up to 10)</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="propertyImages" accept=".jpg,.jpeg,.png" multiple required>
                                <label for="propertyImages" class="file-upload-label">
                                    <i class="fas fa-home"></i>
                                    <div class="file-upload-text">Upload Property Images</div>
                                    <div class="file-upload-hint">Max file size: 5MB each (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="propertyImagesPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Property Documents</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="propertyDocuments" accept=".jpg,.jpeg,.png,.pdf" multiple>
                                <label for="propertyDocuments" class="file-upload-label">
                                    <i class="fas fa-file-alt"></i>
                                    <div class="file-upload-text">Upload Property Documents</div>
                                    <div class="file-upload-hint">Max file size: 5MB each (JPG, PNG, PDF)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="propertyDocumentsPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label required">Owner ID Proof</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="propertyIdProof" accept=".jpg,.jpeg,.png,.pdf" required>
                                <label for="propertyIdProof" class="file-upload-label">
                                    <i class="fas fa-id-card"></i>
                                    <div class="file-upload-text">Upload Owner ID Proof</div>
                                    <div class="file-upload-hint">Max file size: 5MB (JPG, PNG, PDF)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="propertyIdProofPreview"></div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(5, 'realEstate')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(5, 'realEstate')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="6">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-credit-card"></i> Subscription Plan</div>
                        
                        <div class="subscription-plans">
                            <div class="subscription-plan" onclick="selectPlan(this, 'basic', 'realEstate')">
                                <div class="subscription-plan-name">Basic</div>
                                <div class="subscription-plan-price">₹300</div>
                                <div class="subscription-plan-duration">1 Month Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Basic listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 5 photos</li>
                                    <li>Standard support</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan active" onclick="selectPlan(this, 'standard', 'realEstate')">
                                <div class="subscription-plan-name">Standard</div>
                                <div class="subscription-plan-price">₹800</div>
                                <div class="subscription-plan-duration">3 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Higher listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 10 photos</li>
                                    <li>Priority support</li>
                                    <li>Basic analytics</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'premium', 'realEstate')">
                                <div class="subscription-plan-name">Premium</div>
                                <div class="subscription-plan-price">₹1200</div>
                                <div class="subscription-plan-duration">6 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Top listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Up to 15 photos</li>
                                    <li>24/7 support</li>
                                    <li>Advanced analytics</li>
                                    <li>Featured badge</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'enterprise', 'realEstate')">
                                <div class="subscription-plan-name">Enterprise</div>
                                <div class="subscription-plan-price">₹2000</div>
                                <div class="subscription-plan-duration">12 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Highest listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Unlimited photos</li>
                                    <li>24/7 VIP support</li>
                                    <li>Full analytics</li>
                                    <li>Featured badge</li>
                                    <li>Social media promotion</li>
                                </ul>
                            </div>
                        </div>
                        
                        <input type="hidden" id="realEstatePlan" value="standard">
                        
                        <div class="form-group">
                            <div class="form-checkbox">
                                <input type="checkbox" id="realEstateVerification" name="verification">
                                <label for="realEstateVerification" class="form-checkbox-label">Verified Listing (Additional ₹200)</label>
                                <span class="tooltip">
                                    <i class="fas fa-info-circle tooltip-icon"></i>
                                    <span class="tooltip-text">Verified listings include a verification badge after our team confirms your details</span>
                                </span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-share-alt"></i> Social Media Links</div>
                        
                        <div class="form-group">
                            <label for="realEstateInstagram" class="form-label">Instagram Link</label>
                            <input type="url" class="form-control" id="realEstateInstagram" placeholder="https://instagram.com/yourprofile">
                        </div>
                        
                        <div class="form-group">
                            <label for="realEstateFacebook" class="form-label">Facebook Link</label>
                            <input type="url" class="form-control" id="realEstateFacebook" placeholder="https://facebook.com/yourpage">
                        </div>
                        
                        <div class="form-group">
                            <label for="realEstateOffers" class="form-label">Any Offers/Deals</label>
                            <textarea class="form-control form-textarea" id="realEstateOffers" placeholder="List any current offers or deals for buyers"></textarea>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(6, 'realEstate')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        </div>

        <!-- Job Form -->
        <div id="jobForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-briefcase"></i> Job Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Company Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Job Details</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Job Description</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Uploads</div>
                </div>
                <div class="form-step" data-step="5">
                    <div class="form-step-number">5</div>
                    <div class="form-step-label">Subscription</div>
                </div>
                <div class="form-steps-progress" style="width: 20%;"></div>
            </div>
            
            <form id="jobFormData">
                <div class="form-tab active" data-tab="1">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-building"></i> Company Details</div>
                        <div class="form-group">
                            <label for="jobCompany" class="form-label required">Company Name</label>
                            <input type="text" class="form-control" id="jobCompany" required>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="jobContact" class="form-label required">Contact Person</label>
                                <input type="text" class="form-control" id="jobContact" required>
                            </div>
                            <div class="form-group">
                                <label for="jobPhone" class="form-label required">Phone Number</label>
                                <input type="tel" class="form-control" id="jobPhone" required>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="jobEmail" class="form-label">Email</label>
                                <input type="email" class="form-control" id="jobEmail">
                            </div>
                            <div class="form-group">
                                <label for="jobWhatsApp" class="form-label">WhatsApp Number</label>
                                <input type="tel" class="form-control" id="jobWhatsApp">
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="jobCompanyAddress" class="form-label required">Company Address</label>
                            <textarea class="form-control form-textarea" id="jobCompanyAddress" required></textarea>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="jobCompanyCity" class="form-label required">City</label>
                                <select class="form-select" id="jobCompanyCity" required>
                                    <option value="">Select city</option>
                                    <option value="delhi">Delhi</option>
                                    <option value="mumbai">Mumbai</option>
                                    <option value="bangalore">Bangalore</option>
                                    <option value="hyderabad">Hyderabad</option>
                                    <option value="chennai">Chennai</option>
                                    <option value="kolkata">Kolkata</option>
                                    <option value="pune">Pune</option>
                                    <option value="ahmedabad">Ahmedabad</option>
                                    <option value="jaipur">Jaipur</option>
                                    <option value="lucknow">Lucknow</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="jobCompanyPincode" class="form-label required">Pincode</label>
                                <input type="text" class="form-control" id="jobCompanyPincode" required>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="jobWebsite" class="form-label">Company Website</label>
                            <input type="url" class="form-control" id="jobWebsite" placeholder="https://example.com">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'job')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="2">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-clipboard-list"></i> Job Details</div>
                        <div class="form-group">
                            <label for="jobTitle" class="form-label required">Job Title</label>
                            <input type="text" class="form-control" id="jobTitle" required>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="jobType" class="form-label required">Job Type</label>
                                <select class="form-select" id="jobType" required>
                                    <option value="">Select job type</option>
                                    <option value="full-time">Full-time</option>
                                    <option value="part-time">Part-time</option>
                                    <option value="contract">Contract</option>
                                    <option value="freelance">Freelance</option>
                                    <option value="internship">Internship</option>
                                    <option value="temporary">Temporary</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="jobCategory" class="form-label required">Job Category</label>
                                <select class="form-select" id="jobCategory" required>
                                    <option value="">Select job category</option>
                                    <option value="it">IT/Software</option>
                                    <option value="sales">Sales</option>
                                    <option value="marketing">Marketing</option>
                                    <option value="finance">Finance</option>
                                    <option value="hr">Human Resources</option>
                                    <option value="operations">Operations</option>
                                    <option value="customer-service">Customer Service</option>
                                    <option value="driver">Driver</option>
                                    <option value="delivery">Delivery</option>
                                    <option value="house-help">House Help</option>
                                    <option value="security">Security</option>
                                    <option value="teacher">Teacher</option>
                                    <option value="healthcare">Healthcare</option>
                                    <option value="hospitality">Hospitality</option>
                                    <option value="construction">Construction</option>
                                    <option value="manufacturing">Manufacturing</option>
                                    <option value="other">Other</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="jobSalary" class="form-label">Salary Range</label>
                                <input type="text" class="form-control" id="jobSalary" placeholder="e.g. ₹15,000 - ₹25,000 per month">
                            </div>
                            <div class="form-group">
                                <label for="jobExperience" class="form-label">Experience Required</label>
                                <input type="text" class="form-control" id="jobExperience" placeholder="e.g. 1-3 years">
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="jobEducation" class="form-label">Education Qualification</label>
                                <input type="text" class="form-control" id="jobEducation" placeholder="e.g. Any Graduate, B.Tech, MBA">
                            </div>
                            <div class="form-group">
                                <label for="jobVacancies" class="form-label">Number of Vacancies</label>
                                <input type="number" class="form-control" id="jobVacancies" min="1">
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="jobJoining" class="form-label">Joining Timeline</label>
                                <select class="form-select" id="jobJoining">
                                    <option value="immediate">Immediate</option>
                                    <option value="15-days">15 Days</option>
                                    <option value="30-days">30 Days</option>
                                    <option value="negotiable">Negotiable</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Work Location Type</label>
                                <div class="form-checkbox-group">
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="jobLocationOffice" name="workLocation" value="office" checked>
                                        <label for="jobLocationOffice" class="form-checkbox-label">Office</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="jobLocationRemote" name="workLocation" value="remote">
                                        <label for="jobLocationRemote" class="form-checkbox-label">Remote</label>
                                    </div>
                                    <div class="form-checkbox">
                                        <input type="checkbox" id="jobLocationHybrid" name="workLocation" value="hybrid">
                                        <label for="jobLocationHybrid" class="form-checkbox-label">Hybrid</label>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="jobSkills" class="form-label">Skills Required</label>
                            <textarea class="form-control form-textarea" id="jobSkills" placeholder="List required skills separated by commas"></textarea>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'job')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'job')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="3">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-file-alt"></i> Job Description</div>
                        <div class="form-group">
                            <label for="jobSummary" class="form-label required">Job Summary</label>
                            <textarea class="form-control form-textarea" id="jobSummary" required></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label for="jobResponsibilities" class="form-label required">Roles & Responsibilities</label>
                            <textarea class="form-control form-textarea" id="jobResponsibilities" required></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label for="jobBenefits" class="form-label">Benefits & Perks</label>
                            <textarea class="form-control form-textarea" id="jobBenefits" placeholder="List any benefits or perks offered"></textarea>
                        </div>
                        
                        <div class="form-group">
                            <label for="jobApplicationProcess" class="form-label">Application Process</label>
                            <textarea class="form-control form-textarea" id="jobApplicationProcess" placeholder="Describe how candidates should apply"></textarea>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'job')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'job')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="4">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-file-upload"></i> Upload Section</div>
                        
                        <div class="form-group">
                            <label class="form-label">Company Logo</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="jobCompanyLogo" accept=".jpg,.jpeg,.png">
                                <label for="jobCompanyLogo" class="file-upload-label">
                                    <i class="fas fa-building"></i>
                                    <div class="file-upload-text">Upload Company Logo</div>
                                    <div class="file-upload-hint">Max file size: 2MB (JPG, PNG)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="jobCompanyLogoPreview"></div>
                        </div>
                        
                        <div class="form-group">
                            <label class="form-label">Offer Letter Sample / Certificate</label>
                            <div class="file-upload">
                                <input type="file" class="file-upload-input" id="jobOfferSample" accept=".jpg,.jpeg,.png,.pdf">
                                <label for="jobOfferSample" class="file-upload-label">
                                    <i class="fas fa-file-contract"></i>
                                    <div class="file-upload-text">Upload Offer Letter Sample</div>
                                    <div class="file-upload-hint">Max file size: 5MB (JPG, PNG, PDF)</div>
                                </label>
                            </div>
                            <div class="file-preview" id="jobOfferSamplePreview"></div>
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'job')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(4, 'job')">Next</button>
                    </div>
                </div>
                
                <div class="form-tab" data-tab="5">
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-credit-card"></i> Subscription Plan</div>
                        
                        <div class="subscription-plans">
                            <div class="subscription-plan" onclick="selectPlan(this, 'basic', 'job')">
                                <div class="subscription-plan-name">Basic</div>
                                <div class="subscription-plan-price">₹300</div>
                                <div class="subscription-plan-duration">1 Month Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Basic listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Standard support</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan active" onclick="selectPlan(this, 'standard', 'job')">
                                <div class="subscription-plan-name">Standard</div>
                                <div class="subscription-plan-price">₹800</div>
                                <div class="subscription-plan-duration">3 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Higher listing visibility</li>
                                    <li>Contact information</li>
                                    <li>Priority support</li>
                                    <li>Basic analytics</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'premium', 'job')">
                                <div class="subscription-plan-name">Premium</div>
                                <div class="subscription-plan-price">₹1200</div>
                                <div class="subscription-plan-duration">6 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Top listing visibility</li>
                                    <li>Contact information</li>
                                    <li>24/7 support</li>
                                    <li>Advanced analytics</li>
                                    <li>Featured badge</li>
                                </ul>
                            </div>
                            
                            <div class="subscription-plan" onclick="selectPlan(this, 'enterprise', 'job')">
                                <div class="subscription-plan-name">Enterprise</div>
                                <div class="subscription-plan-price">₹2000</div>
                                <div class="subscription-plan-duration">12 Months Listing</div>
                                <ul class="subscription-plan-features">
                                    <li>Highest listing visibility</li>
                                    <li>Contact information</li>
                                    <li>24/7 VIP support</li>
                                    <li>Full analytics</li>
                                    <li>Featured badge</li>
                                    <li>Social media promotion</li>
                                </ul>
                            </div>
                        </div>
                        
                        <input type="hidden" id="jobPlan" value="standard">
                        
                        <div class="form-group">
                            <div class="form-checkbox">
                                <input type="checkbox" id="jobVerification" name="verification">
                                <label for="jobVerification" class="form-checkbox-label">Verified Listing (Additional ₹200)</label>
                                <span class="tooltip">
                                    <i class="fas fa-info-circle tooltip-icon"></i>
                                    <span class="tooltip-text">Verified listings include a verification badge after our team confirms your details</span>
                                </span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-section">
                        <div class="form-section-title"><i class="fas fa-share-alt"></i> Social Media Links</div>
                        
                        <div class="form-group">
                            <label for="jobInstagram" class="form-label">Instagram Link</label>
                            <input type="url" class="form-control" id="jobInstagram" placeholder="https://instagram.com/yourcompany">
                        </div>
                        
                        <div class="form-group">
                            <label for="jobFacebook" class="form-label">Facebook Link</label>
                            <input type="url" class="form-control" id="jobFacebook" placeholder="https://facebook.com/yourcompany">
                        </div>
                        
                        <div class="form-group">
                            <label for="jobLinkedIn" class="form-label">LinkedIn Link</label>
                            <input type="url" class="form-control" id="jobLinkedIn" placeholder="https://linkedin.com/company/yourcompany">
                        </div>
                    </div>
                    
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(5, 'job')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        </div>
    </div>

    <!-- Confirmation Modal -->
    <div class="confirmation-modal" id="confirmationModal">
        <div class="confirmation-content">
            <div class="confirmation-icon">
                <i class="fas fa-check-circle"></i>
            </div>
            <h2 class="confirmation-title">Listing Submitted Successfully!</h2>
            <p class="confirmation-message">Your listing has been successfully submitted and is pending review by our team. You will receive a confirmation email shortly.</p>
            <p class="confirmation-message">All details have been sent to nysaworldofficial@gmail.com for verification.</p>
            <button class="confirmation-button" onclick="hideConfirmation()">Return to Dashboard</button>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/flatpickr"></script>
    <script>
        // Initialize date pickers
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize any date/time pickers if needed
            // flatpickr(".date-picker", {});
        });

        // Show form function
        function showForm(formId) {
            // Hide all forms first
            document.querySelectorAll('.form-container').forEach(form => {
                form.classList.remove('active-form');
            });
            
            // Show the selected form
            document.getElementById(formId).classList.add('active-form');
            
            // Reset to first tab
            resetFormTabs(formId);
            
            // Scroll to the form
            document.getElementById(formId).scrollIntoView({ behavior: 'smooth' });
        }
        
        // Hide all forms
        function hideForms() {
            document.querySelectorAll('.form-container').forEach(form => {
                form.classList.remove('active-form');
            });
        }
        
        // Show confirmation modal
        function showConfirmation() {
            document.getElementById('confirmationModal').classList.add('active');
        }
        
        // Hide confirmation modal
        function hideConfirmation() {
            document.getElementById('confirmationModal').classList.remove('active');
            hideForms();
        }
        
        // Reset form tabs to first step
        function resetFormTabs(formId) {
            const form = document.getElementById(formId);
            const tabs = form.querySelectorAll('.form-tab');
            const steps = form.querySelectorAll('.form-step');
            
            tabs.forEach(tab => {
                tab.classList.remove('active');
                if (tab.dataset.tab === '1') {
                    tab.classList.add('active');
                }
            });
            
            steps.forEach(step => {
                step.classList.remove('active');
                if (step.dataset.step === '1') {
                    step.classList.add('active');
                }
            });
            
            // Reset progress bar
            const progressBar = form.querySelector('.form-steps-progress');
            if (progressBar) {
                const totalSteps = steps.length;
                progressBar.style.width = `${100/totalSteps}%`;
            }
        }
        
        // Next tab function
        function nextTab(currentTab, formType = 'serviceProvider') {
            const form = document.getElementById(`${formType}Form`);
            const tabs = form.querySelectorAll('.form-tab');
            const steps = form.querySelectorAll('.form-step');
            const progressBar = form.querySelector('.form-steps-progress');
            
            // Validate current tab before proceeding
            if (!validateTab(currentTab, formType)) {
                return;
            }
            
            const nextTabNum = parseInt(currentTab) + 1;
            
            // Hide current tab
            tabs.forEach(tab => {
                if (tab.dataset.tab === currentTab.toString()) {
                    tab.classList.remove('active');
                }
            });
            
            // Show next tab
            tabs.forEach(tab => {
                if (tab.dataset.tab === nextTabNum.toString()) {
                    tab.classList.add('active');
                }
            });
            
            // Update steps
            steps.forEach(step => {
                step.classList.remove('active');
                if (step.dataset.step === nextTabNum.toString()) {
                    step.classList.add('active');
                }
            });
            
            // Update progress bar
            if (progressBar) {
                const totalSteps = steps.length;
                const progressPercentage = (nextTabNum / totalSteps) * 100;
                progressBar.style.width = `${progressPercentage}%`;
            }
            
            // Scroll to top of form
            form.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
        
        // Previous tab function
        function prevTab(currentTab, formType = 'serviceProvider') {
            const form = document.getElementById(`${formType}Form`);
            const tabs = form.querySelectorAll('.form-tab');
            const steps = form.querySelectorAll('.form-step');
            const progressBar = form.querySelector('.form-steps-progress');
            
            const prevTabNum = parseInt(currentTab) - 1;
            
            // Hide current tab
            tabs.forEach(tab => {
                if (tab.dataset.tab === currentTab.toString()) {
                    tab.classList.remove('active');
                }
            });
            
            // Show previous tab
            tabs.forEach(tab => {
                if (tab.dataset.tab === prevTabNum.toString()) {
                    tab.classList.add('active');
                }
            });
            
            // Update steps
            steps.forEach(step => {
                step.classList.remove('active');
                if (step.dataset.step === prevTabNum.toString()) {
                    step.classList.add('active');
                }
            });
            
            // Update progress bar
            if (progressBar) {
                const totalSteps = steps.length;
                const progressPercentage = ((prevTabNum - 1) / totalSteps) * 100;
                progressBar.style.width = `${progressPercentage}%`;
            }
            
            // Scroll to top of form
            form.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
        
        // Validate tab before proceeding
        function validateTab(tabNum, formType) {
            const form = document.getElementById(`${formType}Form`);
            const currentTab = form.querySelector(`.form-tab[data-tab="${tabNum}"]`);
            const requiredFields = currentTab.querySelectorAll('[required]');
            let isValid = true;
            
            requiredFields.forEach(field => {
                if (!field.value.trim()) {
                    field.classList.add('error');
                    isValid = false;
                    
                    // Add error message if not exists
                    if (!field.nextElementSibling || !field.nextElementSibling.classList.contains('form-feedback')) {
                        const errorMsg = document.createElement('div');
                        errorMsg.className = 'form-feedback error';
                        errorMsg.textContent = 'This field is required';
                        field.parentNode.insertBefore(errorMsg, field.nextSibling);
                    }
                } else {
                    field.classList.remove('error');
                    // Remove error message if exists
                    if (field.nextElementSibling && field.nextElementSibling.classList.contains('form-feedback')) {
                        field.nextElementSibling.remove();
                    }
                }
            });
            
            if (!isValid) {
                // Scroll to first error
                const firstError = currentTab.querySelector('.error');
                if (firstError) {
                    firstError.scrollIntoView({ behavior: 'smooth', block: 'center' });
                }
            }
            
            return isValid;
        }
        
        // Select subscription plan
        function selectPlan(planElement, planType, formType = 'serviceProvider') {
            const form = document.getElementById(`${formType}Form`);
            const plans = form.querySelectorAll('.subscription-plan');
            
            plans.forEach(plan => {
                plan.classList.remove('active');
            });
            
            planElement.classList.add('active');
            document.getElementById(`${formType}Plan`).value = planType;
        }
        
        // Function to collect form data and create email body
        function getFormData(formId) {
            const form = document.getElementById(formId);
            const inputs = form.querySelectorAll('input, select, textarea');
            let formData = [];
            
            inputs.forEach(input => {
                if (input.id && input.type !== 'submit' && input.type !== 'button' && !input.classList.contains('file-upload-input')) {
                    const label = form.querySelector(`label[for="${input.id}"]`) || 
                                  form.querySelector(`label:has(+ #${input.id})`);
                    let labelText = label ? label.textContent.trim() : input.id;
                    
                    // Remove required asterisk if present
                    labelText = labelText.replace(' *', '');
                    
                    let value = input.value;
                    if (input.type === 'select-one') {
                        const select = input;
                        value = select.options[select.selectedIndex].text;
                    } else if (input.type === 'checkbox' || input.type === 'radio') {
                        if (input.checked) {
                            value = input.nextElementSibling.textContent.trim();
                        } else {
                            return; // Skip unchecked checkboxes/radios
                        }
                    }
                    
                    if (value) {
                        formData.push(`${labelText}: ${value}`);
                    }
                }
            });
            
            return formData.join('\n');
        }
        
        // Function to send form data via email
        function sendFormData(formId, formType) {
            const formData = getFormData(formId);
            const subject = `New ${formType} Listing Submission`;
            const body = `New listing submission details:\n\n${formData}\n\nSubmitted via Nysa Lister`;
            
            // Create mailto link
            const mailtoLink = `mailto:nysaworldofficial@gmail.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
            
            // Open email client
            window.location.href = mailtoLink;
            
            // Show confirmation
            showConfirmation();
        }
        
        // Form submission handlers
        document.getElementById('serviceProviderFormData').addEventListener('submit', function(e) {
            e.preventDefault();
            sendFormData('serviceProviderFormData', 'Service Provider');
        });
        
        document.getElementById('storeFormData').addEventListener('submit', function(e) {
            e.preventDefault();
            sendFormData('storeFormData', 'Store');
        });
        
        document.getElementById('publicPlaceFormData').addEventListener('submit', function(e) {
            e.preventDefault();
            sendFormData('publicPlaceFormData', 'Public Place');
        });
        
        document.getElementById('realEstateFormData').addEventListener('submit', function(e) {
            e.preventDefault();
            sendFormData('realEstateFormData', 'Real Estate');
        });
        
        document.getElementById('jobFormData').addEventListener('submit', function(e) {
            e.preventDefault();
            sendFormData('jobFormData', 'Job');
        });
        
        // File upload preview functionality
        document.querySelectorAll('.file-upload-input').forEach(input => {
            input.addEventListener('change', function() {
                const previewContainerId = this.id + 'Preview';
                const previewContainer = document.getElementById(previewContainerId);
                previewContainer.innerHTML = '';
                
                if (this.files) {
                    Array.from(this.files).forEach(file => {
                        const reader = new FileReader();
                        
                        reader.onload = function(e) {
                            const previewItem = document.createElement('div');
                            previewItem.className = 'file-preview-item';
                            
                            if (file.type.startsWith('image/')) {
                                previewItem.innerHTML = `
                                    <img src="${e.target.result}" alt="${file.name}">
                                    <div class="file-preview-item-remove" onclick="this.parentElement.remove()">
                                        <i class="fas fa-times"></i>
                                    </div>
                                `;
                            } else {
                                previewItem.innerHTML = `
                                    <div style="background: rgba(255,215,0,0.1); height: 100%; display: flex; align-items: center; justify-content: center;">
                                        <i class="fas fa-file-alt" style="font-size: 24px; color: var(--primary-color);"></i>
                                        <div style="position: absolute; bottom: 5px; left: 0; right: 0; text-align: center; font-size: 10px; padding: 0 5px; overflow: hidden; text-overflow: ellipsis; white-space: nowrap;">${file.name}</div>
                                    </div>
                                    <div class="file-preview-item-remove" onclick="this.parentElement.remove()">
                                        <i class="fas fa-times"></i>
                                    </div>
                                `;
                            }
                            
                            previewContainer.appendChild(previewItem);
                        };
                        
                        reader.readAsDataURL(file);
                    });
                }
            });
        });
        
        // Toggle other language input
        document.getElementById('serviceLangOther').addEventListener('change', function() {
            const container = document.getElementById('serviceLangOtherContainer');
            container.style.display = this.checked ? 'block' : 'none';
        });
        
        // Toggle other payment options input
        document.getElementById('storePaymentOther').addEventListener('change', function() {
            const container = document.getElementById('storePaymentOtherContainer');
            container.style.display = this.checked ? 'block' : 'none';
        });
        
        // Toggle delivery details
        document.getElementById('storeDeliveryYes').addEventListener('change', function() {
            const container = document.getElementById('storeDeliveryDetails');
            container.style.display = this.checked ? 'block' : 'none';
        });
        
        // Toggle other facilities input
        document.getElementById('placeFacilityOther').addEventListener('change', function() {
            const container = document.getElementById('placeFacilityOtherContainer');
            container.style.display = this.checked ? 'block' : 'none';
        });
        
        // Toggle other amenities input
        document.getElementById('propertyAmenityOther').addEventListener('change', function() {
            const container = document.getElementById('propertyAmenityOtherContainer');
            container.style.display = this.checked ? 'block' : 'none';
        });
        
        // Property type change handler
        document.getElementById('propertyType').addEventListener('change', function() {
            const residentialContainer = document.getElementById('propertyResidentialContainer');
            const commercialContainer = document.getElementById('propertyCommercialContainer');
            
            if (this.value === 'residential') {
                residentialContainer.style.display = 'block';
                commercialContainer.style.display = 'none';
            } else if (this.value === 'commercial') {
                residentialContainer.style.display = 'none';
                commercialContainer.style.display = 'block';
            } else {
                residentialContainer.style.display = 'none';
                commercialContainer.style.display = 'none';
            }
        });
        
        // Character counter for short description
        document.getElementById('storeShortDescription').addEventListener('input', function() {
            const counter = document.getElementById('storeShortDescriptionCounter');
            counter.textContent = `${this.value.length}/150`;
        });
        
        // Real-time form validation
        document.querySelectorAll('.form-control[required]').forEach(input => {
            input.addEventListener('blur', function() {
                if (!this.value.trim()) {
                    this.classList.add('error');
                    // Add error message if not exists
                    if (!this.nextElementSibling || !this.nextElementSibling.classList.contains('form-feedback')) {
                        const errorMsg = document.createElement('div');
                        errorMsg.className = 'form-feedback error';
                        errorMsg.textContent = 'This field is required';
                        this.parentNode.insertBefore(errorMsg, this.nextSibling);
                    }
                } else {
                    this.classList.remove('error');
                    // Remove error message if exists
                    if (this.nextElementSibling && this.nextElementSibling.classList.contains('form-feedback')) {
                        this.nextElementSibling.remove();
                    }
                }
            });
        });
    </script>
</body>
</html>
