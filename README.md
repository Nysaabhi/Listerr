<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Nysa Lister</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap" rel="stylesheet">
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
}

.header { 
    padding: 8px 16px; 
    background: rgba(26, 26, 31, 0.95); 
    position: fixed; 
    width: 100%; 
    top: 0; 
    left: 0; 
    z-index: 30; 
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
}

.menu-button { 
    padding: 10px 20px; 
    background: var(--accent-gradient); 
    border: none; 
    border-radius: 50px; 
    color: var(--text-dark); 
    font-weight: 600; 
    cursor: pointer; 
    transition: all 0.3s ease; 
    font-size: 0.95em; 
}

.main-container {
    margin-top: 60px;
    padding: 20px;
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
}

.listing-types {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
    margin-bottom: 30px;
}

.listing-card {
    background: rgba(255, 255, 255, 0.05);
    border-radius: 12px;
    padding: 25px;
    transition: all 0.3s ease;
    cursor: pointer;
    border: 1px solid rgba(255, 215, 0, 0.1);
    text-align: center;
}

.listing-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
    border-color: var(--primary-color);
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
}

.listing-description {
    font-size: 0.9em;
    opacity: 0.8;
    margin-bottom: 20px;
}

.listing-button {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 10px 20px;
    border-radius: 6px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    width: 100%;
}

.listing-button:hover {
    opacity: 0.9;
}

.form-container {
    background: rgba(26, 26, 31, 0.95);
    border-radius: 12px;
    padding: 30px;
    margin-top: 30px;
    border: 1px solid rgba(255, 215, 0, 0.2);
    display: none;
}

.active-form {
    display: block;
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
    font-weight: 600;
    color: var(--primary-color);
    display: flex;
    align-items: center;
}

.form-title i {
    margin-right: 10px;
}

.close-form {
    background: none;
    border: none;
    color: var(--primary-color);
    font-size: 1.5em;
    cursor: pointer;
    padding: 5px;
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

.form-control {
    width: 100%;
    padding: 12px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 215, 0, 0.2);
    border-radius: 6px;
    color: var(--text-light);
    font-size: 14px;
    font-family: 'Poppins', sans-serif;
}

.form-control:focus {
    outline: none;
    border-color: var(--primary-color);
}

.form-select {
    width: 100%;
    padding: 12px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 215, 0, 0.2);
    border-radius: 6px;
    color: var(--text-light);
    font-size: 14px;
}

.form-textarea {
    min-height: 120px;
    resize: vertical;
}

.form-checkbox {
    margin-right: 10px;
}

.form-submit {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 12px 25px;
    border-radius: 6px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    width: 100%;
    margin-top: 20px;
    font-size: 1em;
}

.form-submit:hover {
    opacity: 0.9;
}

.form-section {
    margin-bottom: 25px;
    padding-bottom: 20px;
    border-bottom: 1px solid rgba(255, 215, 0, 0.1);
}

.form-section-title {
    color: var(--primary-color);
    font-size: 1.1em;
    margin-bottom: 15px;
    display: flex;
    align-items: center;
}

.form-section-title i {
    margin-right: 10px;
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
    border-radius: 6px;
    text-align: center;
    cursor: pointer;
    transition: all 0.3s ease;
}

.file-upload-label:hover {
    border-color: var(--primary-color);
}

.file-upload-label i {
    font-size: 24px;
    color: var(--primary-color);
    margin-bottom: 10px;
    display: block;
}

.file-preview {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 10px;
}

.file-preview-item {
    position: relative;
    width: 80px;
    height: 80px;
    border-radius: 4px;
    overflow: hidden;
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
    width: 20px;
    height: 20px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
}

.subscription-plans {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 20px;
}

.subscription-plan {
    flex: 1;
    min-width: 120px;
    background: rgba(255, 255, 255, 0.05);
    border-radius: 6px;
    padding: 15px;
    text-align: center;
    cursor: pointer;
    transition: all 0.3s ease;
    border: 1px solid transparent;
}

.subscription-plan.active {
    border-color: var(--primary-color);
    background: rgba(255, 215, 0, 0.1);
}

.subscription-plan-price {
    font-size: 18px;
    font-weight: 600;
    color: var(--primary-color);
    margin: 5px 0;
}

.subscription-plan-duration {
    font-size: 12px;
    opacity: 0.8;
}

.features-checklist {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    gap: 10px;
}

.feature-checkbox {
    display: flex;
    align-items: center;
    margin-bottom: 8px;
}

.feature-checkbox input {
    margin-right: 8px;
}

.confirmation-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
}

.confirmation-modal.active {
    opacity: 1;
    visibility: visible;
}

.confirmation-content {
    background-color: #1a1a1f;
    border-radius: 12px;
    padding: 30px;
    text-align: center;
    max-width: 500px;
    width: 90%;
    border: 1px solid var(--primary-color);
}

.confirmation-icon {
    font-size: 60px;
    color: var(--success-color);
    margin-bottom: 20px;
}

.confirmation-title {
    font-size: 1.5em;
    margin-bottom: 15px;
    color: var(--primary-color);
}

.confirmation-message {
    margin-bottom: 25px;
}

.confirmation-button {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 12px 25px;
    border-radius: 6px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
}

.confirmation-button:hover {
    opacity: 0.9;
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
}

@media (max-width: 480px) {
    .subscription-plans {
        flex-direction: column;
    }
    
    .form-header {
        flex-direction: column;
        align-items: flex-start;
    }
    
    .close-form {
        margin-top: 15px;
        align-self: flex-end;
    }
}

body > h1:first-of-type:not(.heading) { 
    display: none !important; 
}

.markdown-body h1:first-child { 
    display: none !important; 
}

.position-relative h1:first-child { 
    display: none !important; 
}


    </style>
</head>
<body>
    <header class="header">
        <div class="logo">Nysa Lister</div>
        <button class="menu-button" id="menuButton">
            <i class="fas fa-bars"></i> Menu
        </button>
    </header>

    <div class="main-container">
        <h2 style="text-align: center; margin-top: 20px; margin-bottom: 20px; color: var(--primary-color);">Create a New Listing</h2>
        
        <div class="listing-types">
            <div class="listing-card" onclick="showForm('serviceProviderForm')">
                <div class="listing-icon"><i class="fas fa-tools"></i></div>
                <h3 class="listing-title">Service Provider</h3>
                <p class="listing-description">List electricians, plumbers, cleaners, and other service professionals</p>
                <button class="listing-button">List Service</button>
            </div>
            
            <div class="listing-card" onclick="showForm('storeForm')">
                <div class="listing-icon"><i class="fas fa-store"></i></div>
                <h3 class="listing-title">Store</h3>
                <p class="listing-description">List retail stores, supermarkets, and other businesses</p>
                <button class="listing-button">List Store</button>
            </div>
            
            <div class="listing-card" onclick="showForm('publicPlaceForm')">
                <div class="listing-icon"><i class="fas fa-landmark"></i></div>
                <h3 class="listing-title">Public Place</h3>
                <p class="listing-description">List parks, malls, hospitals, and other public locations</p>
                <button class="listing-button">List Place</button>
            </div>
            
            <div class="listing-card" onclick="showForm('realEstateForm')">
                <div class="listing-icon"><i class="fas fa-home"></i></div>
                <h3 class="listing-title">Real Estate</h3>
                <p class="listing-description">List properties for sale or rent</p>
                <button class="listing-button">List Property</button>
            </div>
            
            <div class="listing-card" onclick="showForm('jobForm')">
                <div class="listing-icon"><i class="fas fa-briefcase"></i></div>
                <h3 class="listing-title">Job</h3>
                <p class="listing-description">List job opportunities and vacancies</p>
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
            <form id="serviceProviderFormData">
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-info-circle"></i> Basic Information</div>
                    <div class="form-group">
                        <label class="form-label">Business/Service Name</label>
                        <input type="text" class="form-control" id="serviceName" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Type of Service</label>
                        <select class="form-select" id="serviceType" required>
                            <option value="">Select service type</option>
                            <option value="electrician">Electrician</option>
                            <option value="plumber">Plumber</option>
                            <option value="carpenter">Carpenter</option>
                            <option value="painter">Painter</option>
                            <option value="pest-control">Pest Control</option>
                            <option value="cleaning">House Cleaning</option>
                            <option value="ac-repair">AC Repair</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Owner Name</label>
                        <input type="text" class="form-control" id="serviceOwner" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Phone Number</label>
                        <input type="tel" class="form-control" id="servicePhone" required>
                    </div>
                </div>
                
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-clipboard-list"></i> Service Details</div>
                    <div class="form-group">
                        <label class="form-label">Description of Services</label>
                        <textarea class="form-control form-textarea" id="serviceDescription" required></textarea>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Working Hours</label>
                        <input type="text" class="form-control" id="serviceHours" placeholder="e.g. 9AM-6PM, Monday-Saturday">
                    </div>
                </div>
                
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-map-marker-alt"></i> Location</div>
                    <div class="form-group">
                        <label class="form-label">Business Address</label>
                        <textarea class="form-control form-textarea" id="serviceAddress" required></textarea>
                    </div>
                    <div class="form-group">
                        <label class="form-label">City</label>
                        <input type="text" class="form-control" id="serviceCity" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Pincode</label>
                        <input type="text" class="form-control" id="servicePincode" required>
                    </div>
                </div>
                
                <button type="submit" class="form-submit">Submit Service Listing</button>
            </form>
        </div>

        <!-- Store Form -->
        <div id="storeForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-store"></i> Store Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            <form id="storeFormData">
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-info-circle"></i> Store Details</div>
                    <div class="form-group">
                        <label class="form-label">Store Name</label>
                        <input type="text" class="form-control" id="storeName" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Category</label>
                        <select class="form-select" id="storeCategory" required>
                            <option value="">Select store category</option>
                            <option value="grocery">Grocery Store</option>
                            <option value="electronics">Electronics</option>
                            <option value="clothing">Clothing</option>
                            <option value="pharmacy">Pharmacy</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Owner Name</label>
                        <input type="text" class="form-control" id="storeOwner" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Phone Number</label>
                        <input type="tel" class="form-control" id="storePhone" required>
                    </div>
                </div>
                
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-clipboard-list"></i> Store Information</div>
                    <div class="form-group">
                        <label class="form-label">Description</label>
                        <textarea class="form-control form-textarea" id="storeDescription"></textarea>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Store Timings</label>
                        <input type="text" class="form-control" id="storeTimings" placeholder="e.g. 10AM-9PM, 7 days a week">
                    </div>
                </div>
                
                <button type="submit" class="form-submit">Submit Store Listing</button>
            </form>
        </div>

        <!-- Public Place Form -->
        <div id="publicPlaceForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-landmark"></i> Public Place Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            <form id="publicPlaceFormData">
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-info-circle"></i> Place Information</div>
                    <div class="form-group">
                        <label class="form-label">Place Name</label>
                        <input type="text" class="form-control" id="placeName" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Category</label>
                        <select class="form-select" id="placeCategory" required>
                            <option value="">Select place category</option>
                            <option value="park">Park</option>
                            <option value="hospital">Hospital</option>
                            <option value="mall">Shopping Mall</option>
                            <option value="school">School</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Contact Number</label>
                        <input type="tel" class="form-control" id="placePhone">
                    </div>
                </div>
                
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-clipboard-list"></i> Place Details</div>
                    <div class="form-group">
                        <label class="form-label">Description</label>
                        <textarea class="form-control form-textarea" id="placeDescription"></textarea>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Open Hours</label>
                        <input type="text" class="form-control" id="placeHours" placeholder="e.g. 6AM-10PM daily">
                    </div>
                </div>
                
                <button type="submit" class="form-submit">Submit Public Place</button>
            </form>
        </div>

        <!-- Real Estate Form -->
        <div id="realEstateForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-home"></i> Real Estate Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            <form id="realEstateFormData">
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-home"></i> Property Type</div>
                    <div class="form-group">
                        <label class="form-label">Property Type</label>
                        <select class="form-select" id="propertyType" required>
                            <option value="">Select property type</option>
                            <option value="residential">Residential</option>
                            <option value="commercial">Commercial</option>
                            <option value="land">Land</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Property Name</label>
                        <input type="text" class="form-control" id="propertyName">
                    </div>
                </div>
                
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-user-tie"></i> Contact Information</div>
                    <div class="form-group">
                        <label class="form-label">Contact Name</label>
                        <input type="text" class="form-control" id="propertyContact" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Phone Number</label>
                        <input type="tel" class="form-control" id="propertyPhone" required>
                    </div>
                </div>
                
                <button type="submit" class="form-submit">Submit Property Listing</button>
            </form>
        </div>

        <!-- Job Form -->
        <div id="jobForm" class="form-container">
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-briefcase"></i> Job Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            <form id="jobFormData">
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-building"></i> Company Details</div>
                    <div class="form-group">
                        <label class="form-label">Company Name</label>
                        <input type="text" class="form-control" id="jobCompany" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Contact Person</label>
                        <input type="text" class="form-control" id="jobContact" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Phone Number</label>
                        <input type="tel" class="form-control" id="jobPhone" required>
                    </div>
                </div>
                
                <div class="form-section">
                    <div class="form-section-title"><i class="fas fa-clipboard-list"></i> Job Details</div>
                    <div class="form-group">
                        <label class="form-label">Job Title</label>
                        <input type="text" class="form-control" id="jobTitle" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Job Description</label>
                        <textarea class="form-control form-textarea" id="jobDescription"></textarea>
                    </div>
                </div>
                
                <button type="submit" class="form-submit">Submit Job Listing</button>
            </form>
        </div>
    </div>

    <!-- Confirmation Modal -->
    <div class="confirmation-modal" id="confirmationModal">
        <div class="confirmation-content">
            <div class="confirmation-icon">
                <i class="fas fa-check-circle"></i>
            </div>
            <h2 class="confirmation-title">Listing Submitted!</h2>
            <p class="confirmation-message">Your listing has been successfully submitted. Our team will review it shortly.</p>
            <p class="confirmation-message">All details have been sent to nysaworldofficial@gmail.com</p>
            <button class="confirmation-button" onclick="hideConfirmation()">OK</button>
        </div>
    </div>

    <script>
        // Show form function
        function showForm(formId) {
            // Hide all forms first
            document.querySelectorAll('.form-container').forEach(form => {
                form.classList.remove('active-form');
            });
            
            // Show the selected form
            document.getElementById(formId).classList.add('active-form');
            
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
        
        // Function to collect form data and create email body
        function getFormData(formId) {
            const form = document.getElementById(formId);
            const inputs = form.querySelectorAll('input, select, textarea');
            let formData = [];
            
            inputs.forEach(input => {
                if (input.id && input.type !== 'submit' && input.type !== 'button') {
                    const label = form.querySelector(`label[for="${input.id}"]`) || 
                                  form.querySelector(`label:has(+ #${input.id})`);
                    const labelText = label ? label.textContent.trim() : input.id;
                    
                    let value = input.value;
                    if (input.type === 'select-one') {
                        const select = input;
                        value = select.options[select.selectedIndex].text;
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
                const previewContainer = this.closest('.file-upload').querySelector('.file-preview');
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
        
        // Subscription plan selection
        document.querySelectorAll('.subscription-plan').forEach(plan => {
            plan.addEventListener('click', function() {
                this.closest('.subscription-plans').querySelectorAll('.subscription-plan').forEach(p => {
                    p.classList.remove('active');
                });
                this.classList.add('active');
            });
        });
    </script>
</body>
</html>
