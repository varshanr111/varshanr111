<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Varshan R - Software Engineer & Web Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* ===================================================
           CSS VARIABLES - EDIT HERE TO CHANGE ENTIRE PALETTE
           =================================================== */
        :root {
            --color-primary: #2563eb;
            --color-primary-dark: #1e40af;
            --color-accent: #f59e0b;
            --color-accent-light: #fbbf24;
            --color-bg: #0f172a;
            --color-bg-secondary: #1e293b;
            --color-text: #f1f5f9;
            --color-text-secondary: #cbd5e1;
            --color-border: #334155;
            --color-success: #10b981;
            --color-warning: #f59e0b;
            
            --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
            --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1);
            --shadow-lg: 0 10px 25px rgba(0, 0, 0, 0.2);
            --shadow-xl: 0 20px 50px rgba(0, 0, 0, 0.3);
            
            --transition-fast: 0.2s ease-in-out;
            --transition-base: 0.3s ease-in-out;
            --transition-slow: 0.5s ease-in-out;
        }

        /* ===================================================
           GLOBAL STYLES
           =================================================== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--color-bg);
            color: var(--color-text);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* ===================================================
           UTILITY CLASSES
           =================================================== */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .section {
            padding: 100px 0;
            position: relative;
        }

        .section-title {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 50px;
            text-align: center;
            background: linear-gradient(135deg, var(--color-primary), var(--color-accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 12px 28px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            border: none;
            text-decoration: none;
            transition: all var(--transition-base);
            font-size: 1rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--color-primary), var(--color-primary-dark));
            color: white;
            box-shadow: var(--shadow-lg);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 40px rgba(37, 99, 235, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: var(--color-primary);
            border: 2px solid var(--color-primary);
        }

        .btn-secondary:hover {
            background: var(--color-primary);
            color: white;
        }

        .btn-accent {
            background: linear-gradient(135deg, var(--color-accent), var(--color-accent-light));
            color: #000;
            font-weight: 700;
        }

        .btn-accent:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 40px rgba(245, 158, 11, 0.4);
        }

        /* ===================================================
           NAVBAR
           =================================================== */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            backdrop-filter: blur(10px);
            background: rgba(15, 23, 42, 0.8);
            border-bottom: 1px solid var(--color-border);
            transition: all var(--transition-base);
            padding: 20px 0;
        }

        .navbar.scrolled {
            padding: 10px 0;
            box-shadow: var(--shadow-lg);
        }

        .navbar-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .navbar-logo {
            font-size: 1.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--color-primary), var(--color-accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-menu {
            display: flex;
            gap: 40px;
            align-items: center;
            list-style: none;
        }

        .nav-link {
            color: var(--color-text-secondary);
            text-decoration: none;
            font-weight: 500;
            transition: all var(--transition-base);
            position: relative;
        }

        .nav-link:hover,
        .nav-link.active {
            color: var(--color-primary);
        }

        .nav-link.active::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--color-primary), var(--color-accent));
            animation: slideIn 0.3s ease-in-out;
        }

        @keyframes slideIn {
            from {
                transform: scaleX(0);
                transform-origin: left;
            }
            to {
                transform: scaleX(1);
            }
        }

        .theme-toggle {
            background: var(--color-bg-secondary);
            border: 1px solid var(--color-border);
            color: var(--color-text);
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all var(--transition-base);
        }

        .theme-toggle:hover {
            background: var(--color-primary);
            color: white;
        }

        .hamburger {
            display: none;
            flex-direction: column;
            cursor: pointer;
            gap: 5px;
        }

        .hamburger span {
            width: 25px;
            height: 3px;
            background: var(--color-text);
            border-radius: 2px;
            transition: all var(--transition-base);
        }

        /* ===================================================
           LOADING SCREEN
           =================================================== */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: var(--color-bg);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2000;
            animation: fadeOut 0.8s ease-in-out 1.2s forwards;
        }

        @keyframes fadeOut {
            to {
                opacity: 0;
                visibility: hidden;
            }
        }

        .loader {
            width: 50px;
            height: 50px;
            border: 4px solid var(--color-border);
            border-top: 4px solid var(--color-primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }

        /* ===================================================
           HERO SECTION
           =================================================== */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            padding-top: 80px;
        }

        .hero-background {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: -1;
        }

        .blob-1 {
            position: absolute;
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(37, 99, 235, 0.2), transparent);
            border-radius: 50%;
            top: -50px;
            right: -50px;
            animation: float 8s ease-in-out infinite;
        }

        .blob-2 {
            position: absolute;
            width: 250px;
            height: 250px;
            background: radial-gradient(circle, rgba(245, 158, 11, 0.1), transparent);
            border-radius: 50%;
            bottom: 50px;
            left: -50px;
            animation: float 10s ease-in-out infinite reverse;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(30px);
            }
        }

        .hero-content {
            text-align: center;
            z-index: 1;
        }

        .hero-image-wrapper {
            width: 200px;
            height: 200px;
            margin: 0 auto 40px;
            position: relative;
            animation: scaleInDown 0.8s ease-out;
        }

        @keyframes scaleInDown {
            from {
                opacity: 0;
                transform: scale(0.8) translateY(-30px);
            }
            to {
                opacity: 1;
                transform: scale(1) translateY(0);
            }
        }

        .hero-image {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--color-primary);
            box-shadow: 0 0 50px rgba(37, 99, 235, 0.3), inset 0 0 30px rgba(37, 99, 235, 0.1);
            animation: floatImage 4s ease-in-out infinite;
        }

        @keyframes floatImage {
            0%, 100% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-15px);
            }
        }

        .hero-name {
            font-size: 3.5rem;
            font-weight: 800;
            margin-bottom: 10px;
            animation: fadeInUp 0.8s ease-out 0.2s backwards;
        }

        .hero-title {
            font-size: 1.5rem;
            color: var(--color-text-secondary);
            margin-bottom: 10px;
            animation: fadeInUp 0.8s ease-out 0.3s backwards;
        }

        .typing-effect {
            color: var(--color-primary);
            font-weight: 700;
            min-height: 2rem;
        }

        .hero-bio {
            font-size: 1.1rem;
            color: var(--color-text-secondary);
            max-width: 600px;
            margin: 30px auto;
            line-height: 1.8;
            animation: fadeInUp 0.8s ease-out 0.4s backwards;
        }

        .hero-buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 40px;
            flex-wrap: wrap;
            animation: fadeInUp 0.8s ease-out 0.5s backwards;
        }

        .hero-socials {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 50px;
            animation: fadeInUp 0.8s ease-out 0.6s backwards;
        }

        .social-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--color-bg-secondary);
            border: 2px solid var(--color-border);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--color-text);
            text-decoration: none;
            transition: all var(--transition-base);
        }

        .social-icon:hover {
            background: var(--color-primary);
            border-color: var(--color-primary);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(37, 99, 235, 0.3);
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateX(-50%) translateY(0);
            }
            40% {
                transform: translateX(-50%) translateY(-10px);
            }
            60% {
                transform: translateX(-50%) translateY(-5px);
            }
        }

        /* ===================================================
           ABOUT SECTION
           =================================================== */
        .about {
            background: var(--color-bg-secondary);
            border-top: 1px solid var(--color-border);
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
            animation: fadeInSection 0.8s ease-out;
        }

        .about-text h3 {
            font-size: 1.3rem;
            color: var(--color-primary);
            margin-bottom: 20px;
        }

        .about-text p {
            font-size: 1.05rem;
            line-height: 1.8;
            color: var(--color-text-secondary);
            margin-bottom: 20px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }

        .stat-card {
            background: var(--color-bg);
            padding: 30px 20px;
            border-radius: 12px;
            border: 1px solid var(--color-border);
            text-align: center;
            transition: all var(--transition-base);
        }

        .stat-card:hover {
            border-color: var(--color-primary);
            box-shadow: 0 10px 30px rgba(37, 99, 235, 0.2);
            transform: translateY(-5px);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 800;
            color: var(--color-primary);
        }

        .stat-label {
            font-size: 0.9rem;
            color: var(--color-text-secondary);
            margin-top: 10px;
        }

        @keyframes fadeInSection {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* ===================================================
           SKILLS SECTION
           =================================================== */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
        }

        .skill-category {
            background: var(--color-bg-secondary);
            padding: 30px;
            border-radius: 12px;
            border: 1px solid var(--color-border);
            transition: all var(--transition-base);
        }

        .skill-category:hover {
            border-color: var(--color-primary);
            box-shadow: 0 10px 30px rgba(37, 99, 235, 0.2);
            transform: translateY(-5px);
        }

        .skill-category h4 {
            color: var(--color-primary);
            margin-bottom: 20px;
            font-size: 1.1rem;
        }

        .skill-badge {
            display: inline-block;
            background: linear-gradient(135deg, var(--color-primary), var(--color-primary-dark));
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.85rem;
            margin-bottom: 10px;
            margin-right: 10px;
            animation: fadeInBadge 0.5s ease-out;
        }

        @keyframes fadeInBadge {
            from {
                opacity: 0;
                transform: scale(0.8);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        /* ===================================================
           EDUCATION SECTION
           =================================================== */
        .education-timeline {
            max-width: 700px;
            margin: 0 auto;
            position: relative;
            padding: 30px 0;
        }

        .timeline-item {
            display: grid;
            grid-template-columns: 1fr 50px 1fr;
            gap: 20px;
            margin-bottom: 40px;
            animation: fadeInUp 0.8s ease-out;
        }

        .timeline-item:nth-child(even) {
            direction: rtl;
        }

        .timeline-item:nth-child(even) > * {
            direction: ltr;
        }

        .timeline-content {
            background: var(--color-bg-secondary);
            padding: 25px;
            border-radius: 12px;
            border: 1px solid var(--color-border);
            transition: all var(--transition-base);
        }

        .timeline-content:hover {
            border-color: var(--color-primary);
            box-shadow: 0 10px 30px rgba(37, 99, 235, 0.2);
        }

        .timeline-dot {
            width: 50px;
            height: 50px;
            background: var(--color-primary);
            border: 4px solid var(--color-bg);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: 700;
        }

        .timeline-year {
            color: var(--color-accent);
            font-weight: 700;
            margin-bottom: 5px;
        }

        .timeline-title {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 5px;
        }

        .timeline-subtitle {
            color: var(--color-text-secondary);
            font-size: 0.95rem;
        }

        .timeline-gpa {
            color: var(--color-success);
            font-weight: 600;
            margin-top: 10px;
        }

        /* ===================================================
           PROJECTS SECTION
           =================================================== */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 40px;
        }

        .project-card {
            background: var(--color-bg-secondary);
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid var(--color-border);
            transition: all var(--transition-base);
            animation: fadeInUp 0.8s ease-out;
        }

        .project-card:hover {
            border-color: var(--color-primary);
            box-shadow: 0 15px 40px rgba(37, 99, 235, 0.3);
            transform: translateY(-10px);
        }

        .project-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, var(--color-primary), var(--color-accent));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            overflow: hidden;
            position: relative;
        }

        .project-image::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.1), transparent);
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0% {
                transform: translate(0, 0);
            }
            50% {
                transform: translate(25%, 25%);
            }
            100% {
                transform: translate(0, 0);
            }
        }

        .project-content {
            padding: 30px;
        }

        .project-title {
            font-size: 1.3rem;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .project-description {
            color: var(--color-text-secondary);
            font-size: 0.95rem;
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }

        .project-tag {
            background: var(--color-primary);
            color: white;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        .project-links {
            display: flex;
            gap: 15px;
        }

        .project-link {
            flex: 1;
            padding: 10px;
            border-radius: 6px;
            text-align: center;
            text-decoration: none;
            font-weight: 600;
            font-size: 0.9rem;
            transition: all var(--transition-base);
            border: 2px solid var(--color-primary);
            color: var(--color-primary);
        }

        .project-link:hover {
            background: var(--color-primary);
            color: white;
        }

        /* ===================================================
           CERTIFICATIONS SECTION
           =================================================== */
        .certifications-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .cert-card {
            background: var(--color-bg-secondary);
            padding: 30px;
            border-radius: 12px;
            border: 1px solid var(--color-border);
            transition: all var(--transition-base);
            position: relative;
            overflow: hidden;
        }

        .cert-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--color-primary), var(--color-accent));
        }

        .cert-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(37, 99, 235, 0.2);
        }

        .cert-icon {
            font-size: 2rem;
            color: var(--color-accent);
            margin-bottom: 15px;
        }

        .cert-name {
            font-size: 1.1rem;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .cert-issuer {
            color: var(--color-text-secondary);
            font-size: 0.95rem;
            margin-bottom: 5px;
        }

        .cert-year {
            color: var(--color-primary);
            font-weight: 600;
        }

        /* ===================================================
           CONTACT SECTION
           =================================================== */
        .contact {
            background: var(--color-bg-secondary);
            border-top: 1px solid var(--color-border);
        }

        .contact-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }

        .contact-info h3 {
            font-size: 1.3rem;
            color: var(--color-primary);
            margin-bottom: 30px;
        }

        .contact-info-item {
            margin-bottom: 25px;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .contact-info-icon {
            width: 50px;
            height: 50px;
            background: var(--color-primary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
        }

        .contact-info-text {
            flex: 1;
        }

        .contact-info-label {
            color: var(--color-text-secondary);
            font-size: 0.9rem;
        }

        .contact-info-value {
            font-weight: 600;
            margin-top: 3px;
        }

        .contact-info-value a {
            color: var(--color-primary);
            text-decoration: none;
            transition: all var(--transition-base);
        }

        .contact-info-value a:hover {
            text-decoration: underline;
        }

        .contact-form {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            font-weight: 600;
            margin-bottom: 8px;
            color: var(--color-text);
        }

        .form-group input,
        .form-group textarea {
            background: var(--color-bg);
            border: 2px solid var(--color-border);
            border-radius: 8px;
            padding: 12px 15px;
            color: var(--color-text);
            font-family: 'Poppins', sans-serif;
            font-size: 1rem;
            transition: all var(--transition-base);
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--color-primary);
            box-shadow: 0 0 15px rgba(37, 99, 235, 0.3);
        }

        .form-group textarea {
            resize: vertical;
            min-height: 120px;
        }

        .form-group input::placeholder,
        .form-group textarea::placeholder {
            color: var(--color-text-secondary);
        }

        .form-submit {
            align-self: flex-start;
        }

        .success-message {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: var(--color-success);
            color: white;
            padding: 20px 30px;
            border-radius: 8px;
            box-shadow: var(--shadow-lg);
            animation: slideInRight 0.5s ease-out, slideOutRight 0.5s ease-out 2.5s forwards;
            z-index: 2000;
        }

        @keyframes slideInRight {
            from {
                transform: translateX(400px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        @keyframes slideOutRight {
            to {
                transform: translateX(400px);
                opacity: 0;
            }
        }

        /* ===================================================
           FOOTER
           =================================================== */
        .footer {
            background: var(--color-bg-secondary);
            border-top: 1px solid var(--color-border);
            padding: 40px 0;
            text-align: center;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }

        .footer-socials {
            display: flex;
            gap: 15px;
        }

        .footer-socials a {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--color-bg);
            border: 1px solid var(--color-border);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--color-text);
            text-decoration: none;
            transition: all var(--transition-base);
        }

        .footer-socials a:hover {
            background: var(--color-primary);
            border-color: var(--color-primary);
            transform: translateY(-3px);
        }

        .footer-text {
            color: var(--color-text-secondary);
            font-size: 0.9rem;
        }

        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            background: var(--color-primary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            cursor: pointer;
            box-shadow: var(--shadow-lg);
            opacity: 0;
            visibility: hidden;
            transition: all var(--transition-base);
            z-index: 999;
        }

        .back-to-top.show {
            opacity: 1;
            visibility: visible;
        }

        .back-to-top:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(37, 99, 235, 0.4);
        }

        /* ===================================================
           LIGHT MODE (Optional)
           =================================================== */
        body.light-mode {
            --color-bg: #f8fafc;
            --color-bg-secondary: #f1f5f9;
            --color-text: #1e293b;
            --color-text-secondary: #64748b;
            --color-border: #cbd5e1;
        }

        /* ===================================================
           RESPONSIVE DESIGN
           =================================================== */
        @media (max-width: 1024px) {
            .section {
                padding: 60px 0;
            }

            .section-title {
                font-size: 2rem;
            }

            .about-content {
                grid-template-columns: 1fr;
                gap: 40px;
            }

            .contact-content {
                grid-template-columns: 1fr;
                gap: 40px;
            }

            .hero-name {
                font-size: 2.5rem;
            }

            .nav-menu {
                gap: 25px;
            }

            .timeline-item {
                grid-template-columns: 1fr;
                gap: 10px;
            }

            .timeline-item:nth-child(even) {
                direction: ltr;
            }

            .timeline-item:nth-child(even) > * {
                direction: ltr;
            }
        }

        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }

            .nav-menu {
                position: absolute;
                top: 70px;
                left: 0;
                right: 0;
                background: var(--color-bg);
                flex-direction: column;
                gap: 0;
                list-style: none;
                max-height: 0;
                overflow: hidden;
                transition: max-height 0.3s ease-out;
                border-bottom: 1px solid var(--color-border);
            }

            .nav-menu.active {
                max-height: 500px;
            }

            .nav-link {
                padding: 15px 20px;
                border-bottom: 1px solid var(--color-border);
            }

            .hero-name {
                font-size: 2rem;
            }

            .hero-title {
                font-size: 1.2rem;
            }

            .hero-buttons {
                flex-direction: column;
                width: 100%;
            }

            .btn {
                width: 100%;
                justify-content: center;
            }

            .section-title {
                font-size: 1.8rem;
                margin-bottom: 40px;
            }

            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .certifications-grid {
                grid-template-columns: 1fr;
            }

            .skills-grid {
                grid-template-columns: 1fr;
            }

            .hero-buttons {
                gap: 10px;
            }

            .back-to-top {
                width: 45px;
                height: 45px;
                bottom: 20px;
                right: 20px;
            }

            .footer-content {
                flex-direction: column;
                gap: 20px;
            }
        }

        @media (max-width: 480px) {
            .container {
                padding: 0 15px;
            }

            .hero {
                padding-top: 60px;
            }

            .hero-name {
                font-size: 1.8rem;
            }

            .hero-title {
                font-size: 1rem;
            }

            .hero-bio {
                font-size: 1rem;
            }

            .section-title {
                font-size: 1.5rem;
            }

            .hero-image-wrapper {
                width: 150px;
                height: 150px;
            }

            .stat-card {
                padding: 20px 15px;
            }

            .stat-number {
                font-size: 1.5rem;
            }

            .timeline-dot {
                width: 40px;
                height: 40px;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- ===================================================
         LOADING SCREEN
         =================================================== -->
    <div class="loading-screen">
        <div class="loader"></div>
    </div>

    <!-- ===================================================
         NAVBAR
         =================================================== -->
    <nav class="navbar">
        <div class="navbar-container container">
            <div class="navbar-logo">VR</div>
            <ul class="nav-menu">
                <li><a href="#home" class="nav-link active">Home</a></li>
                <li><a href="#about" class="nav-link">About</a></li>
                <li><a href="#skills" class="nav-link">Skills</a></li>
                <li><a href="#education" class="nav-link">Education</a></li>
                <li><a href="#projects" class="nav-link">Projects</a></li>
                <li><a href="#certifications" class="nav-link">Certifications</a></li>
                <li><a href="#contact" class="nav-link">Contact</a></li>
            </ul>
            <div style="display: flex; gap: 15px; align-items: center;">
                <button class="theme-toggle" id="themeToggle">
                    <i class="fas fa-moon"></i>
                </button>
                <div class="hamburger" id="hamburger">
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </div>
        </div>
    </nav>

    <!-- ===================================================
         HERO SECTION
         =================================================== -->
    <section class="hero" id="home">
        <div class="hero-background">
            <div class="blob-1"></div>
            <div class="blob-2"></div>
        </div>

        <div class="container" style="width: 100%; text-align: center;">
            <div class="hero-content">
                <div class="hero-image-wrapper">
                    <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 200'%3E%3Ccircle cx='100' cy='100' r='95' fill='%232563eb' opacity='0.1'/%3E%3Ctext x='50%' y='50%' font-size='60' font-weight='bold' fill='%232563eb' text-anchor='middle' dominant-baseline='middle'%3EVR%3C/text%3E%3C/svg%3E" alt="Varshan R" class="hero-image" id="heroImage">
                </div>
                <h1 class="hero-name">Varshan R</h1>
                <p class="hero-title">ISE Student | Aspiring Software Engineer</p>
                <p class="typing-effect" id="typingEffect">AI Enthusiast</p>
                <p class="hero-bio">
                    Information Science & Engineering student with a strong interest in web development and software engineering. Passionate about building innovative digital solutions, learning emerging technologies, and continuously developing technical and problem-solving skills.
                </p>
                <div class="hero-buttons">
                    <a href="#" class="btn btn-primary" id="resumeBtn">
                        <i class="fas fa-download"></i> Download Resume
                    </a>
                    <a href="#contact" class="btn btn-secondary">Contact Me</a>
                </div>
                <div class="hero-socials">
                    <a href="https://linkedin.com/in/varshan-r" target="_blank" class="social-icon" title="LinkedIn">
                        <i class="fab fa-linkedin-in"></i>
                    </a>
                    <a href="https://github.com/varshanr111" target="_blank" class="social-icon" title="GitHub">
                        <i class="fab fa-github"></i>
                    </a>
                    <a href="https://instagram.com" target="_blank" class="social-icon" title="Instagram">
                        <i class="fab fa-instagram"></i>
                    </a>
                </div>
            </div>
            <div class="scroll-indicator">
                <i class="fas fa-chevron-down" style="color: var(--color-primary); font-size: 1.5rem;"></i>
            </div>
        </div>
    </section>

    <!-- ===================================================
         ABOUT SECTION
         =================================================== -->
    <section class="about section" id="about">
        <div class="container">
            <h2 class="section-title">About Me</h2>
            <div class="about-content">
                <div class="about-text">
                    <h3>Who I Am</h3>
                    <p>
                        I'm an Information Science & Engineering (ISE) student currently studying at Amruta Institution of Engineering and Management Sciences. My journey in tech has been driven by a passion for solving real-world problems through code and innovation.
                    </p>
                    <p>
                        I specialize in web development and have a strong foundation in multiple programming languages. I'm constantly learning new technologies and frameworks to stay updated with industry trends. My goal is to create impactful software solutions that make a difference.
                    </p>
                    <p>
                        Beyond academics, I actively participate in coding competitions, collaborate on open-source projects, and contribute to the developer community.
                    </p>
                </div>
                <div>
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-number">5+</div>
                            <div class="stat-label">Projects</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">3</div>
                            <div class="stat-label">Certifications</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">7.2</div>
                            <div class="stat-label">CGPA</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">100%</div>
                            <div class="stat-label">Dedication</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ===================================================
         SKILLS SECTION
         =================================================== -->
    <section class="section" id="skills">
        <div class="container">
            <h2 class="section-title">Skills & Expertise</h2>
            <div class="skills-grid">
                <div class="skill-category">
                    <h4>Programming Languages</h4>
                    <div>
                        <span class="skill-badge">Python</span>
                        <span class="skill-badge">Java</span>
                        <span class="skill-badge">C</span>
                        <span class="skill-badge">JavaScript</span>
                        <span class="skill-badge">SQL</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h4>Web Development</h4>
                    <div>
                        <span class="skill-badge">HTML</span>
                        <span class="skill-badge">CSS</span>
                        <span class="skill-badge">React</span>
                        <span class="skill-badge">Node.js</span>
                        <span class="skill-badge">REST APIs</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h4>Tools & Platforms</h4>
                    <div>
                        <span class="skill-badge">Git</span>
                        <span class="skill-badge">GitHub</span>
                        <span class="skill-badge">VS Code</span>
                        <span class="skill-badge">MySQL</span>
                        <span class="skill-badge">Linux</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h4>Soft Skills</h4>
                    <div>
                        <span class="skill-badge">Problem Solving</span>
                        <span class="skill-badge">Leadership</span>
                        <span class="skill-badge">Team Collaboration</span>
                        <span class="skill-badge">Communication</span>
                        <span class="skill-badge">Adaptability</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ===================================================
         EDUCATION SECTION
         =================================================== -->
    <section class="section" id="education" style="background: var(--color-bg-secondary);">
        <div class="container">
            <h2 class="section-title">Education</h2>
            <div class="education-timeline">
                <div class="timeline-item">
                    <div class="timeline-content">
                        <div class="timeline-year">2024 - 2028</div>
                        <div class="timeline-title">B.E. in Information Science Engineering</div>
                        <div class="timeline-subtitle">Amruta Institution of Engineering and Management Sciences, Bangalore</div>
                        <div class="timeline-gpa">CGPA: 7.2</div>
                    </div>
                    <div class="timeline-dot">
                        <i class="fas fa-graduation-cap"></i>
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-content">
                        <div class="timeline-year">2024</div>
                        <div class="timeline-title">PUC (Pre-University Course)</div>
                        <div class="timeline-subtitle">Vikas PU College, Belagumba, Tumkur</div>
                        <div class="timeline-gpa">Score: 86.5%</div>
                    </div>
                    <div class="timeline-dot">
                        <i class="fas fa-book"></i>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ===================================================
         PROJECTS SECTION
         =================================================== -->
    <section class="section" id="projects">
        <div class="container">
            <h2 class="section-title">Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-image">
                        <i class="fas fa-laptop-code"></i>
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">Portfolio Website</h3>
                        <p class="project-description">A modern, responsive portfolio website built with HTML, CSS, and JavaScript featuring smooth animations, dark/light mode, and a professional design.</p>
                        <div class="project-tags">
                            <span class="project-tag">HTML</span>
                            <span class="project-tag">CSS</span>
                            <span class="project-tag">JavaScript</span>
                        </div>
                        <div class="project-links">
                            <a href="https://github.com/varshanr111" class="project-link">
                                <i class="fab fa-github"></i> GitHub
                            </a>
                            <a href="#" class="project-link">
                                <i class="fas fa-globe"></i> Demo
                            </a>
                        </div>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-image">
                        <i class="fas fa-database"></i>
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">Task Management App</h3>
                        <p class="project-description">A full-stack web application for task management with user authentication, database integration, and a clean user interface.</p>
                        <div class="project-tags">
                            <span class="project-tag">Python</span>
                            <span class="project-tag">Flask</span>
                            <span class="project-tag">MySQL</span>
                        </div>
                        <div class="project-links">
                            <a href="https://github.com/varshanr111" class="project-link">
                                <i class="fab fa-github"></i> GitHub
                            </a>
                            <a href="#" class="project-link">
                                <i class="fas fa-globe"></i> Demo
                            </a>
                        </div>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-image">
                        <i class="fas fa-brain"></i>
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">AI Chatbot</h3>
                        <p class="project-description">An intelligent chatbot powered by natural language processing, capable of understanding user queries and providing helpful responses.</p>
                        <div class="project-tags">
                            <span class="project-tag">Python</span>
                            <span class="project-tag">NLP</span>
                            <span class="project-tag">TensorFlow</span>
                        </div>
                        <div class="project-links">
                            <a href="https://github.com/varshanr111" class="project-link">
                                <i class="fab fa-github"></i> GitHub
                            </a>
                            <a href="#" class="project-link">
                                <i class="fas fa-globe"></i> Demo
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ===================================================
         CERTIFICATIONS SECTION
         =================================================== -->
    <section class="section" id="certifications" style="background: var(--color-bg-secondary);">
        <div class="container">
            <h2 class="section-title">Certifications & Achievements</h2>
            <div class="certifications-grid">
                <div class="cert-card">
                    <div class="cert-icon">
                        <i class="fas fa-certificate"></i>
                    </div>
                    <div class="cert-name">Python Programming Fundamentals</div>
                    <div class="cert-issuer">Coursera</div>
                    <div class="cert-year">2023</div>
                </div>

                <div class="cert-card">
                    <div class="cert-icon">
                        <i class="fas fa-certificate"></i>
                    </div>
                    <div class="cert-name">Web Development Bootcamp</div>
                    <div class="cert-issuer">Udemy</div>
                    <div class="cert-year">2023</div>
                </div>

                <div class="cert-card">
                    <div class="cert-icon">
                        <i class="fas fa-certificate"></i>
                    </div>
                    <div class="cert-name">SQL and Database Design</div>
                    <div class="cert-issuer">LinkedIn Learning</div>
                    <div class="cert-year">2024</div>
                </div>
            </div>
        </div>
    </section>

    <!-- ===================================================
         CONTACT SECTION
         =================================================== -->
    <section class="contact section" id="contact">
        <div class="container">
            <h2 class="section-title">Get In Touch</h2>
            <div class="contact-content">
                <div class="contact-info">
                    <h3>Contact Information</h3>
                    <div class="contact-info-item">
                        <div class="contact-info-icon">
                            <i class="fas fa-map-marker-alt"></i>
                        </div>
                        <div class="contact-info-text">
                            <div class="contact-info-label">Location</div>
                            <div class="contact-info-value">Ramanagara, Karnataka, India</div>
                        </div>
                    </div>
                    <div class="contact-info-item">
                        <div class="contact-info-icon">
                            <i class="fas fa-envelope"></i>
                        </div>
                        <div class="contact-info-text">
                            <div class="contact-info-label">Email</div>
                            <div class="contact-info-value">
                                <a href="mailto:varshanr111@gmail.com">varshanr111@gmail.com</a>
                            </div>
                        </div>
                    </div>
                    <div class="contact-info-item">
                        <div class="contact-info-icon">
                            <i class="fas fa-phone"></i>
                        </div>
                        <div class="contact-info-text">
                            <div class="contact-info-label">Phone</div>
                            <div class="contact-info-value">
                                <a href="tel:+917411750122">+91 7411750122</a>
                            </div>
                        </div>
                    </div>
                </div>

                <div>
                    <form class="contact-form" id="contactForm">
                        <div class="form-group">
                            <label for="name">Full Name</label>
                            <input type="text" id="name" name="name" placeholder="Your Name" required>
                        </div>
                        <div class="form-group">
                            <label for="email">Email Address</label>
                            <input type="email" id="email" name="email" placeholder="your.email@example.com" required>
                        </div>
                        <div class="form-group">
                            <label for="message">Message</label>
                            <textarea id="message" name="message" placeholder="Your message here..." required></textarea>
                        </div>
                        <button type="submit" class="btn btn-accent form-submit">
                            <i class="fas fa-paper-plane"></i> Send Message
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- ===================================================
         FOOTER
         =================================================== -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <div class="footer-socials">
                    <a href="https://linkedin.com/in/varshan-r" target="_blank" title="LinkedIn">
                        <i class="fab fa-linkedin-in"></i>
                    </a>
                    <a href="https://github.com/varshanr111" target="_blank" title="GitHub">
                        <i class="fab fa-github"></i>
                    </a>
                    <a href="https://instagram.com" target="_blank" title="Instagram">
                        <i class="fab fa-instagram"></i>
                    </a>
                </div>
                <div class="footer-text">
                    © 2026 Varshan R. All rights reserved.
                </div>
            </div>
            <div class="footer-text" style="font-size: 0.8rem; color: var(--color-text-secondary);">
                Crafted with <i class="fas fa-heart" style="color: var(--color-primary);"></i> and coffee
            </div>
        </div>
    </footer>

    <!-- ===================================================
         BACK TO TOP BUTTON
         =================================================== -->
    <div class="back-to-top" id="backToTop">
        <i class="fas fa-arrow-up"></i>
    </div>

    <script>
        // ===================================================
        // CONFIGURATION
        // ===================================================
        const config = {
            typingTexts: ['AI Enthusiast', 'Python Developer', 'Problem Solver', 'Web Developer'],
            typingSpeed: 100,
            deletingSpeed: 50,
            delayBetweenWords: 2000
        };

        // ===================================================
        // TYPING EFFECT
        // ===================================================
        let typeIndex = 0;
        let charIndex = 0;
        let isDeleting = false;

        function typeEffect() {
            const typingElement = document.getElementById('typingEffect');
            const currentText = config.typingTexts[typeIndex];

            if (isDeleting) {
                charIndex--;
            } else {
                charIndex++;
            }

            typingElement.textContent = currentText.substring(0, charIndex);

            let typeSpeed = isDeleting ? config.deletingSpeed : config.typingSpeed;

            if (!isDeleting && charIndex === currentText.length) {
                typeSpeed = config.delayBetweenWords;
                isDeleting = true;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                typeIndex = (typeIndex + 1) % config.typingTexts.length;
                typeSpeed = 500;
            }

            setTimeout(typeEffect, typeSpeed);
        }

        // ===================================================
        // NAVBAR FUNCTIONALITY
        // ===================================================
        const navbar = document.querySelector('.navbar');
        const navLinks = document.querySelectorAll('.nav-link');
        const hamburger = document.getElementById('hamburger');
        const navMenu = document.querySelector('.nav-menu');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
            updateActiveNavLink();
        });

        function updateActiveNavLink() {
            const sections = document.querySelectorAll('section');
            let current = '';

            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                if (window.scrollY >= sectionTop - 200) {
                    current = section.getAttribute('id');
                }
            });

            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('href').slice(1) === current) {
                    link.classList.add('active');
                }
            });
        }

        hamburger.addEventListener('click', () => {
            navMenu.classList.toggle('active');
        });

        navLinks.forEach(link => {
            link.addEventListener('click', () => {
                navMenu.classList.remove('active');
            });
        });

        // ===================================================
        // THEME TOGGLE
        // ===================================================
        const themeToggle = document.getElementById('themeToggle');
        let isDarkMode = true;

        themeToggle.addEventListener('click', () => {
            isDarkMode = !isDarkMode;
            document.body.classList.toggle('light-mode');
            
            const icon = themeToggle.querySelector('i');
            if (isDarkMode) {
                icon.classList.remove('fa-sun');
                icon.classList.add('fa-moon');
            } else {
                icon.classList.remove('fa-moon');
                icon.classList.add('fa-sun');
            }
        });

        // ===================================================
        // SCROLL ANIMATIONS
        // ===================================================
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.project-card, .cert-card, .skill-category, .timeline-item').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'opacity 0.8s ease-out, transform 0.8s ease-out';
            observer.observe(el);
        });

        // ===================================================
        // BACK TO TOP BUTTON
        // ===================================================
        const backToTop = document.getElementById('backToTop');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 500) {
                backToTop.classList.add('show');
            } else {
                backToTop.classList.remove('show');
            }
        });

        backToTop.addEventListener('click', () => {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });

        // ===================================================
        // CONTACT FORM
        // ===================================================
        const contactForm = document.getElementById('contactForm');

        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();

            // Validate form
            const name = document.getElementById('name').value.trim();
            const email = document.getElementById('email').value.trim();
            const message = document.getElementById('message').value.trim();

            if (!name || !email || !message) {
                alert('Please fill in all fields');
                return;
            }

            // Show success message
            const successMessage = document.createElement('div');
            successMessage.className = 'success-message';
            successMessage.innerHTML = '✓ Message sent successfully! I\'ll get back to you soon.';
            document.body.appendChild(successMessage);

            // Reset form
            contactForm.reset();

            // Remove success message after 3 seconds
            setTimeout(() => {
                successMessage.remove();
            }, 3000);
        });

        // ===================================================
        // RESUME DOWNLOAD
        // ===================================================
        const resumeBtn = document.getElementById('resumeBtn');
        resumeBtn.addEventListener('click', (e) => {
            e.preventDefault();
            alert('Resume download link will be added here. Replace with your actual resume PDF URL.');
            // Example: window.open('path/to/your/resume.pdf');
        });

        // ===================================================
        // INITIALIZATION
        // ===================================================
        typeEffect();
        updateActiveNavLink();
    </script>
</body>
</html>
