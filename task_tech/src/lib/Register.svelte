<script>
    import { navigate } from './router.js';
    
    let formData = {
        firstName: '',
        lastName: '',
        email: '',
        phone: '',
        company: '',
        jobTitle: '',
        experience: '',
        interests: [],
        ticketType: 'standard',
        dietary: '',
        specialRequests: '',
        newsletter: true,
        terms: false
    };

    const interestOptions = [
        'AI & Machine Learning',
        'Cloud Computing',
        'Cybersecurity',
        'Data Science',
        'Frontend Development',
        'Backend Development',
        'Mobile Development',
        'DevOps',
        'Blockchain',
        'IoT',
        'UX/UI Design',
        'Startup Ecosystem'
    ];

    function handleInterestChange(interest) {
        if (formData.interests.includes(interest)) {
            formData.interests = formData.interests.filter(i => i !== interest);
        } else {
            formData.interests = [...formData.interests, interest];
        }
    }

    function handleSubmit(event) {
        event.preventDefault();
        
        if (!formData.terms) {
            alert('Please accept the terms and conditions to proceed.');
            return;
        }

        // Simulate form submission
        alert('Registration submitted successfully! You will receive a confirmation email shortly.');
        
        // Reset form
        formData = {
            firstName: '',
            lastName: '',
            email: '',
            phone: '',
            company: '',
            jobTitle: '',
            experience: '',
            interests: [],
            ticketType: 'standard',
            dietary: '',
            specialRequests: '',
            newsletter: true,
            terms: false
        };
    }
</script>

<div class="register-page">
    <!-- Back to site button -->
    <div class="back-navigation">
        <button on:click={() => navigate('home')} class="back-btn" aria-label="Back to CodeVibe 2025">
            <i class="bi bi-arrow-left"></i>
            <span>Back to CodeVibe 2025</span>
        </button>
    </div>

    <div class="page-header">
        <h1>Register for CodeVibe 2025</h1>
        <p>Secure your spot at the most innovative tech conference of the year</p>
    </div>

    <div class="registration-container">
        <div class="registration-content">
            <!-- Conference Info -->
            <div class="conference-info">
                <div class="info-card">
                    <h3>📅 Conference Details</h3>
                    <div class="detail-item">
                        <strong>Date:</strong> March 15-17, 2025
                    </div>
                    <div class="detail-item">
                        <strong>Location:</strong> KTPO Center, Whitefield, Bangalore
                    </div>
                    <div class="detail-item">
                        <strong>Duration:</strong> 3 Days
                    </div>
                    <div class="detail-item">
                        <strong>Expected Attendees:</strong> 2000+
                    </div>
                </div>

                <div class="info-card">
                    <h3>🎫 Ticket Prices</h3>
                    <div class="ticket-price">
                        <strong>Early Bird:</strong> ₹8,999 <span class="original-price">₹12,999</span>
                    </div>
                    <div class="ticket-price">
                        <strong>Standard:</strong> ₹12,999
                    </div>
                    <div class="ticket-price">
                        <strong>VIP:</strong> ₹24,999
                    </div>
                    <div class="ticket-price">
                        <strong>Student:</strong> ₹2,999 <span class="discount">(70% off)</span>
                    </div>
                </div>

                <div class="info-card">
                    <h3>✨ What's Included</h3>
                    <ul class="included-list">
                        <li>✅ Access to all sessions</li>
                        <li>✅ Networking events</li>
                        <li>✅ Conference swag bag</li>
                        <li>✅ Lunch & refreshments</li>
                        <li>✅ Digital resources</li>
                        <li>✅ Certificate of attendance</li>
                    </ul>
                </div>
            </div>

            <!-- Registration Form -->
            <div class="registration-form">
                <form on:submit={handleSubmit}>
                    <h2>Registration Form</h2>
                    
                    <!-- Personal Information -->
                    <div class="form-section">
                        <h3>Personal Information</h3>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="firstName">First Name *</label>
                                <input 
                                    type="text" 
                                    id="firstName" 
                                    bind:value={formData.firstName}
                                    class="form-control" 
                                    required 
                                    placeholder="Enter your first name"
                                />
                            </div>
                            <div class="form-group">
                                <label for="lastName">Last Name *</label>
                                <input 
                                    type="text" 
                                    id="lastName" 
                                    bind:value={formData.lastName}
                                    class="form-control" 
                                    required 
                                    placeholder="Enter your last name"
                                />
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label for="email">Email Address *</label>
                                <input 
                                    type="email" 
                                    id="email" 
                                    bind:value={formData.email}
                                    class="form-control" 
                                    required 
                                    placeholder="your.email@example.com"
                                />
                            </div>
                            <div class="form-group">
                                <label for="phone">Phone Number</label>
                                <input 
                                    type="tel" 
                                    id="phone" 
                                    bind:value={formData.phone}
                                    class="form-control" 
                                    placeholder="+91 98765 43210"
                                />
                            </div>
                        </div>
                    </div>

                    <!-- Professional Information -->
                    <div class="form-section">
                        <h3>Professional Information</h3>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="company">Company/Organization</label>
                                <input 
                                    type="text" 
                                    id="company" 
                                    bind:value={formData.company}
                                    class="form-control" 
                                    placeholder="Your company name"
                                />
                            </div>
                            <div class="form-group">
                                <label for="jobTitle">Job Title</label>
                                <input 
                                    type="text" 
                                    id="jobTitle" 
                                    bind:value={formData.jobTitle}
                                    class="form-control" 
                                    placeholder="Your job title"
                                />
                            </div>
                        </div>

                        <div class="form-group">
                            <label for="experience">Years of Experience</label>
                            <select id="experience" bind:value={formData.experience} class="form-control">
                                <option value="">Select experience level</option>
                                <option value="0-1">0-1 years (Student/Entry Level)</option>
                                <option value="2-5">2-5 years</option>
                                <option value="6-10">6-10 years</option>
                                <option value="11-15">11-15 years</option>
                                <option value="16+">16+ years</option>
                            </select>
                        </div>
                    </div>

                    <!-- Interests -->
                    <div class="form-section">
                        <h3>Areas of Interest</h3>
                        <div class="interests-grid">
                            {#each interestOptions as interest}
                                <label class="interest-checkbox">
                                    <input 
                                        type="checkbox" 
                                        checked={formData.interests.includes(interest)}
                                        on:change={() => handleInterestChange(interest)}
                                    />
                                    <span class="checkmark"></span>
                                    <span>{interest}</span>
                                </label>
                            {/each}
                        </div>
                    </div>

                    <!-- Ticket Selection -->
                    <div class="form-section">
                        <h3>Ticket Type</h3>
                        <div class="ticket-options">
                            <label class="ticket-option">
                                <input type="radio" name="ticketType" value="early-bird" bind:group={formData.ticketType} />
                                <div class="ticket-card">
                                    <h4>Early Bird</h4>
                                    <div class="price">₹8,999 <span class="original">₹12,999</span></div>
                                    <p>Limited time offer</p>
                                </div>
                            </label>
                            <label class="ticket-option">
                                <input type="radio" name="ticketType" value="standard" bind:group={formData.ticketType} />
                                <div class="ticket-card">
                                    <h4>Standard</h4>
                                    <div class="price">₹12,999</div>
                                    <p>Regular pricing</p>
                                </div>
                            </label>
                            <label class="ticket-option">
                                <input type="radio" name="ticketType" value="vip" bind:group={formData.ticketType} />
                                <div class="ticket-card">
                                    <h4>VIP</h4>
                                    <div class="price">₹24,999</div>
                                    <p>Premium experience</p>
                                </div>
                            </label>
                            <label class="ticket-option">
                                <input type="radio" name="ticketType" value="student" bind:group={formData.ticketType} />
                                <div class="ticket-card">
                                    <h4>Student</h4>
                                    <div class="price">₹2,999</div>
                                    <p>Student ID required</p>
                                </div>
                            </label>
                        </div>
                    </div>

                    <!-- Additional Information -->
                    <div class="form-section">
                        <h3>Additional Information</h3>
                        <div class="form-group">
                            <label for="dietary">Dietary Restrictions</label>
                            <input 
                                type="text" 
                                id="dietary" 
                                bind:value={formData.dietary}
                                class="form-control" 
                                placeholder="Any dietary restrictions or allergies"
                            />
                        </div>
                        <div class="form-group">
                            <label for="specialRequests">Special Requests</label>
                            <textarea 
                                id="specialRequests" 
                                bind:value={formData.specialRequests}
                                class="form-control" 
                                rows="3"
                                placeholder="Any special accommodations or requests"
                            ></textarea>
                        </div>
                    </div>

                    <!-- Agreements -->
                    <div class="form-section">
                        <label class="checkbox-label">
                            <input type="checkbox" bind:checked={formData.newsletter} />
                            <span class="checkmark"></span>
                            Subscribe to newsletter for updates and offers
                        </label>
                        <label class="checkbox-label required">
                            <input type="checkbox" bind:checked={formData.terms} required />
                            <span class="checkmark"></span>
                            I accept the <a href="#terms" target="_blank">Terms & Conditions</a> and <a href="#privacy" target="_blank">Privacy Policy</a> *
                        </label>
                    </div>

                    <!-- Submit Button -->
                    <div class="form-actions">
                        <button type="submit" class="btn btn-primary register-btn">
                            Complete Registration
                            <i class="bi bi-arrow-right"></i>
                        </button>
                        <p class="form-note">
                            Secure payment processing. You'll receive a confirmation email after registration.
                        </p>
                    </div>
                </form>
            </div>
        </div>
    </div>
</div>

<style>
    .register-page {
        padding-top: 0; /* Main content handles navbar spacing */
        min-height: 100vh;
        background: linear-gradient(135deg, rgba(32, 178, 170, 0.05) 0%, rgba(78, 205, 196, 0.05) 100%);
        overflow-x: hidden; /* Prevent horizontal scroll */
    }

    .back-navigation {
        position: fixed;
        top: 20px;
        left: 20px;
        z-index: 1000;
    }

    .back-btn {
        display: flex;
        align-items: center;
        gap: 0.5rem;
        background: rgba(32, 178, 170, 0.9);
        color: white;
        border: none;
        padding: 0.75rem 1.5rem;
        border-radius: 50px;
        font-size: 0.9rem;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease;
        box-shadow: 0 4px 15px rgba(32, 178, 170, 0.3);
        backdrop-filter: blur(10px);
    }

    .back-btn:hover {
        background: rgba(32, 178, 170, 1);
        transform: translateY(-2px);
        box-shadow: 0 8px 25px rgba(32, 178, 170, 0.4);
    }

    .back-btn i {
        font-size: 1rem;
    }

    .page-header {
        text-align: center;
        padding: 5rem 2rem 2rem; /* Increased top padding to account for back button */
        background: linear-gradient(135deg, #20b2aa 0%, #4ecdc4 100%);
        color: white;
        margin-bottom: 0;
    }

    .page-header h1 {
        font-size: 3rem;
        margin-bottom: 1rem;
        font-weight: 800;
    }

    .page-header p {
        font-size: 1.2rem;
        opacity: 0.9;
        max-width: 600px;
        margin: 0 auto;
    }

    .registration-container {
        max-width: 1400px;
        margin: 0 auto;
        padding: 1rem 2rem;
        min-height: calc(100vh - 200px); /* Ensure enough space for content */
    }

    .registration-content {
        display: grid;
        grid-template-columns: 1fr 1.5fr; /* Adjust column ratio */
        gap: 2rem; /* Reduce gap */
        align-items: start;
    }

    .conference-info {
        position: sticky;
        top: 1rem; /* Reduce top spacing */
    }

    .info-card {
        background: white;
        border-radius: 15px;
        padding: 1.5rem; /* Reduce padding */
        margin-bottom: 1.5rem; /* Reduce margin */
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        border-left: 4px solid #20b2aa;
    }

    .info-card h3 {
        color: #20b2aa;
        margin-bottom: 1.5rem;
        font-size: 1.3rem;
        font-weight: 700;
    }

    .detail-item {
        margin-bottom: 0.8rem;
        color: #555;
    }

    .ticket-price {
        margin-bottom: 0.8rem;
        color: #333;
    }

    .original-price {
        text-decoration: line-through;
        color: #999;
        font-size: 0.9rem;
    }

    .discount {
        color: #e74c3c;
        font-weight: 600;
    }

    .included-list {
        list-style: none;
        padding: 0;
    }

    .included-list li {
        margin-bottom: 0.5rem;
        color: #555;
    }

    .registration-form {
        background: white;
        border-radius: 20px;
        padding: 2rem;
        box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
        width: 100%;
        min-height: fit-content;
    }

    .registration-form h2 {
        color: #20b2aa;
        font-size: 2rem;
        margin-bottom: 2rem;
        font-weight: 700;
        text-align: center;
    }

    .form-section {
        margin-bottom: 2rem; /* Reduce margin */
        padding-bottom: 1.5rem; /* Reduce padding */
        border-bottom: 1px solid #f0f0f0;
    }

    .form-section:last-of-type {
        border-bottom: none;
    }

    .form-section h3 {
        color: #333;
        font-size: 1.3rem;
        margin-bottom: 1.5rem;
        font-weight: 600;
    }

    .form-row {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1.5rem;
        margin-bottom: 1.5rem;
    }

    .form-group {
        margin-bottom: 1.5rem;
    }

    .form-group label {
        display: block;
        margin-bottom: 0.5rem;
        color: #333;
        font-weight: 600;
    }

    .form-control {
        width: 100%;
        padding: 0.8rem 1rem;
        border: 2px solid #e0e0e0;
        border-radius: 8px;
        font-size: 1rem;
        transition: all 0.3s ease;
        background: white;
    }

    .form-control:focus {
        border-color: #20b2aa;
        box-shadow: 0 0 0 3px rgba(32, 178, 170, 0.1);
        outline: none;
    }

    .interests-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 0.75rem;
        margin-top: 1rem;
    }

    .interest-checkbox {
        display: flex;
        align-items: center;
        cursor: pointer;
        padding: 0.75rem 1rem;
        border: 2px solid #e8f4f3;
        border-radius: 12px;
        background: #ffffff;
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        color: #2d3748;
        font-weight: 500;
        font-size: 0.95rem;
        line-height: 1.5;
        position: relative;
        overflow: hidden;
    }

    .interest-checkbox::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: linear-gradient(135deg, rgba(32, 178, 170, 0.08), rgba(78, 205, 196, 0.08));
        opacity: 0;
        transition: opacity 0.3s ease;
        z-index: 0;
    }

    .interest-checkbox:hover {
        border-color: #20b2aa;
        box-shadow: 0 4px 12px rgba(32, 178, 170, 0.15);
        transform: translateY(-1px);
    }

    .interest-checkbox:hover::before {
        opacity: 1;
    }

    .interest-checkbox input[type="checkbox"] {
        position: absolute;
        opacity: 0;
        cursor: pointer;
        height: 0;
        width: 0;
    }

    .checkmark {
        width: 20px;
        height: 20px;
        border: 2px solid #cbd5e0;
        border-radius: 6px;
        margin-right: 0.75rem;
        position: relative;
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        background: white;
        flex-shrink: 0;
        z-index: 1;
    }

    .interest-checkbox input[type="checkbox"]:checked + .checkmark {
        background: linear-gradient(135deg, #20b2aa, #4ecdc4);
        border-color: #20b2aa;
        transform: scale(1.05);
    }

    .interest-checkbox input[type="checkbox"]:checked + .checkmark::after {
        content: '';
        position: absolute;
        left: 6px;
        top: 2px;
        width: 6px;
        height: 10px;
        border: solid white;
        border-width: 0 2px 2px 0;
        transform: rotate(45deg);
        animation: checkmark-appear 0.3s ease-in-out;
    }

    .interest-checkbox input[type="checkbox"]:checked ~ span {
        color: #20b2aa;
        font-weight: 600;
    }

    .interest-checkbox input[type="checkbox"]:checked {
        ~ .checkmark {
            box-shadow: 0 0 0 3px rgba(32, 178, 170, 0.2);
        }
    }

    .interest-checkbox span:not(.checkmark) {
        z-index: 1;
        position: relative;
        transition: color 0.3s ease;
    }

    @keyframes checkmark-appear {
        0% {
            opacity: 0;
            transform: rotate(45deg) scale(0.5);
        }
        50% {
            opacity: 1;
            transform: rotate(45deg) scale(1.2);
        }
        100% {
            opacity: 1;
            transform: rotate(45deg) scale(1);
        }
    }

    .ticket-options {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 1rem;
    }

    .ticket-option {
        cursor: pointer;
    }

    .ticket-option input[type="radio"] {
        display: none;
    }

    .ticket-card {
        background: #f8f9fa;
        border: 2px solid #e0e0e0;
        border-radius: 15px;
        padding: 1.5rem;
        text-align: center;
        transition: all 0.3s ease;
    }

    .ticket-option input[type="radio"]:checked + .ticket-card {
        border-color: #20b2aa;
        background: rgba(32, 178, 170, 0.05);
    }

    .ticket-card h4 {
        color: #333;
        margin-bottom: 0.5rem;
        font-weight: 600;
    }

    .ticket-card .price {
        font-size: 1.5rem;
        font-weight: 700;
        color: #20b2aa;
        margin-bottom: 0.5rem;
    }

    .ticket-card .price .original {
        font-size: 1rem;
        color: #999;
        text-decoration: line-through;
    }

    .ticket-card p {
        color: #666;
        margin: 0;
        font-size: 0.9rem;
    }

    .checkbox-label {
        display: flex;
        align-items: flex-start;
        cursor: pointer;
        margin-bottom: 1rem;
        line-height: 1.4;
    }

    .checkbox-label.required {
        color: #333;
    }

    .checkbox-label input[type="checkbox"] {
        display: none;
    }

    .checkbox-label .checkmark {
        margin-top: 2px;
    }

    .checkbox-label a {
        color: #20b2aa;
        text-decoration: none;
    }

    .checkbox-label a:hover {
        text-decoration: underline;
    }

    .form-actions {
        text-align: center;
        padding-top: 2rem;
    }

    .register-btn {
        background: linear-gradient(45deg, #20b2aa, #4ecdc4);
        border: none;
        color: white;
        padding: 1rem 3rem;
        border-radius: 50px;
        font-size: 1.1rem;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease;
        display: inline-flex;
        align-items: center;
        gap: 0.5rem;
    }

    .register-btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 15px 30px rgba(32, 178, 170, 0.3);
    }

    .form-note {
        margin-top: 1rem;
        color: #666;
        font-size: 0.9rem;
    }

    /* Dark mode styles */
    :global(body.dark-mode) .register-page {
        background: #1a1a1a;
    }

    :global(body.dark-mode) .info-card,
    :global(body.dark-mode) .registration-form {
        background: #2d2d2d;
        color: #e0e0e0;
    }

    :global(body.dark-mode) .info-card h3,
    :global(body.dark-mode) .registration-form h2 {
        color: #4ecdc4;
    }

    :global(body.dark-mode) .form-section h3,
    :global(body.dark-mode) .form-group label,
    :global(body.dark-mode) .ticket-card h4 {
        color: #e0e0e0;
    }

    :global(body.dark-mode) .form-control {
        background: #3a3a3a;
        border-color: #555;
        color: #e0e0e0;
    }

    :global(body.dark-mode) .form-control:focus {
        border-color: #4ecdc4;
        box-shadow: 0 0 0 3px rgba(78, 205, 196, 0.1);
    }

    :global(body.dark-mode) .ticket-card {
        background: #3a3a3a;
        border-color: #555;
    }

    :global(body.dark-mode) .ticket-option input[type="radio"]:checked + .ticket-card {
        border-color: #4ecdc4;
        background: rgba(78, 205, 196, 0.1);
    }

    :global(body.dark-mode) .checkmark {
        border-color: #555;
        background: #3a3a3a;
    }

    :global(body.dark-mode) .interest-checkbox input[type="checkbox"]:checked + .checkmark {
        background: linear-gradient(135deg, #4ecdc4, #20b2aa);
        border-color: #4ecdc4;
    }

    :global(body.dark-mode) .interest-checkbox {
        color: #e0e0e0;
        background: #3a3a3a;
        border-color: #555;
    }

    :global(body.dark-mode) .interest-checkbox::before {
        background: linear-gradient(135deg, rgba(78, 205, 196, 0.15), rgba(32, 178, 170, 0.15));
    }

    :global(body.dark-mode) .interest-checkbox:hover {
        border-color: #4ecdc4;
        box-shadow: 0 4px 12px rgba(78, 205, 196, 0.2);
    }

    :global(body.dark-mode) .interest-checkbox input[type="checkbox"]:checked ~ span:not(.checkmark) {
        color: #4ecdc4;
    }

    /* Responsive design */
    @media (max-width: 1024px) {
        .registration-content {
            grid-template-columns: 1fr;
            gap: 1.5rem;
            max-height: none; /* Remove height restriction on smaller screens */
        }

        .conference-info {
            position: static;
            max-height: none;
            overflow-y: visible;
        }

        .registration-form {
            max-height: none;
            overflow-y: visible;
        }

        .info-card {
            padding: 1rem;
            margin-bottom: 1rem;
        }
    }

    @media (max-width: 768px) {
        .page-header {
            padding: 4rem 1rem 2rem; /* Adjust padding for mobile */
        }

        .page-header h1 {
            font-size: 2.5rem;
        }

        .registration-form {
            padding: 1.5rem;
        }

        .registration-container {
            padding: 0.5rem 1rem;
        }

        .form-row {
            grid-template-columns: 1fr;
            gap: 1rem;
        }

        .ticket-options {
            grid-template-columns: 1fr;
        }

        .interests-grid {
            grid-template-columns: 1fr;
            gap: 0.5rem;
        }

        .interest-checkbox {
            padding: 0.6rem 0.8rem;
            font-size: 0.9rem;
        }

        .checkmark {
            width: 18px;
            height: 18px;
            margin-right: 0.6rem;
        }

        .back-btn span {
            display: none; /* Hide text on mobile, show only icon */
        }

        .back-btn {
            padding: 0.75rem;
            width: 48px;
            height: 48px;
            justify-content: center;
        }
    }

    /* Handle small viewport heights */
    @media (max-height: 800px) {
        .page-header {
            padding: 3rem 2rem 1rem !important;
        }

        .registration-container {
            padding: 0.5rem 2rem !important;
        }
    }

    /* Handle very small viewport heights */
    @media (max-height: 600px) {
        .page-header {
            padding: 1rem 2rem 0.5rem !important;
        }

        .page-header h1 {
            font-size: 2rem !important;
        }

        .page-header p {
            font-size: 1rem !important;
        }

        .registration-container {
            padding: 0.25rem 1rem !important;
        }
    }
</style>
