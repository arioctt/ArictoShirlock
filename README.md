
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ApexGrid Community 2025 - Интерактивный цифровой хаб</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Roboto+Mono:wght@400;500;600&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        mono: ['Roboto Mono', 'monospace'],
                    },
                    animation: {
                        'blob': 'blob 7s infinite',
                        'pulse-slow': 'pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                        'typing': 'typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite',
                    },
                    keyframes: {
                        blob: {
                            '0%': { transform: 'translate(0px, 0px) scale(1)' },
                            '33%': { transform: 'translate(30px, -50px) scale(1.1)' },
                            '66%': { transform: 'translate(-20px, 20px) scale(0.9)' },
                            '100%': { transform: 'translate(0px, 0px) scale(1)' },
                        },
                        typing: {
                            'from': { width: '0' },
                            'to': { width: '100%' }
                        },
                        'blink-caret': {
                            'from, to': { 'border-color': 'transparent' },
                            '50%': { 'border-color': 'rgba(139, 92, 246, 0.8)' }
                        }
                    }
                }
            }
        }
    </script>
    <style>
        :root {
            --bg-color: #1a1a1d;
            --card-bg: rgba(255, 255, 255, 0.03);
            --text-color: #ffffff;
            --text-muted: #9ca3af;
            
            /* Gradients */
            --grad-1: rgba(16, 185, 129, 0.15);
            --grad-2: rgba(139, 92, 246, 0.15);
            --grad-3: rgba(59, 130, 246, 0.15);
        }

        body {
            background: linear-gradient(135deg, #1a1a1d 0%, #2d1b3d 25%, #1a1a2e 50%, #16213e 75%, #1a1a1d 100%);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            color: var(--text-color);
            overflow-x: hidden;
            transition: color 0.3s ease;
            min-height: 100vh;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Day/Night Mode Styles */
        body.light-theme {
            background: linear-gradient(135deg, #f8fafc 0%, #e0e7ff 25%, #f3e8ff 50%, #e0f2fe 75%, #f8fafc 100%);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            --bg-color: #f8fafc;
            --card-bg: rgba(255, 255, 255, 0.9);
            --text-color: #1e293b;
            --text-muted: #64748b;
            --grad-1: rgba(139, 92, 246, 0.1);
            --grad-2: rgba(59, 130, 246, 0.1);
            --grad-3: rgba(236, 72, 153, 0.1);
        }

        body.light-theme .glass-card {
            background: rgba(255, 255, 255, 0.9);
            border: 1px solid rgba(0, 0, 0, 0.1);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.1);
        }

        body.light-theme .neon-gradient-text {
            background: linear-gradient(to right, #7c3aed, #4f46e5, #db2777);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        body.light-theme .custom-cursor {
            border-color: #1e293b;
            mix-blend-mode: normal;
        }

        body.light-theme .custom-cursor::after {
            background: #1e293b;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 10px;
        }

        ::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.05);
        }

        ::-webkit-scrollbar-thumb {
            background: linear-gradient(180deg, #8b5cf6, #3b82f6);
            border-radius: 5px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: linear-gradient(180deg, #7c3aed, #2563eb);
        }

        body.light-theme ::-webkit-scrollbar-track {
            background: rgba(0, 0, 0, 0.05);
        }

        body.light-theme ::-webkit-scrollbar-thumb {
            background: linear-gradient(180deg, #7c3aed, #4f46e5);
        }

        /* Theme Toggle Button */
        #themeToggle {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background: linear-gradient(135deg, #8b5cf6 0%, #3b82f6 50%, #ec4899 100%);
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            z-index: 100;
            box-shadow: 0 4px 20px rgba(139, 92, 246, 0.4);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        #themeToggle:hover {
            transform: scale(1.1) rotate(180deg);
            box-shadow: 0 6px 30px rgba(139, 92, 246, 0.6);
        }

        body.light-theme #themeToggle {
            background: linear-gradient(135deg, #fbbf24 0%, #f59e0b 100%);
            box-shadow: 0 4px 20px rgba(251, 191, 36, 0.4);
        }

        /* Animated Grid Background */
        .grid-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            background-image: 
                linear-gradient(rgba(139, 92, 246, 0.1) 1px, transparent 1px),
                linear-gradient(90deg, rgba(139, 92, 246, 0.1) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: grid-move 20s linear infinite;
            opacity: 0.3;
        }

        @keyframes grid-move {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        /* Themes */
        body.theme-red {
            --bg-color: #1a0505;
            --grad-1: rgba(239, 68, 68, 0.2);
            --grad-2: rgba(249, 115, 22, 0.2);
            --grad-3: rgba(185, 28, 28, 0.2);
        }
        body.theme-red .neon-gradient-text {
            background: linear-gradient(to right, #f87171, #ef4444, #fca5a5);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-red .neon-gradient-btn {
            background: linear-gradient(135deg, #ef4444 0%, #b91c1c 50%, #f87171 100%);
        }

        body.theme-green {
            --bg-color: #02120a;
            --grad-1: rgba(16, 185, 129, 0.2);
            --grad-2: rgba(34, 197, 94, 0.2);
            --grad-3: rgba(6, 95, 70, 0.2);
        }
        body.theme-green .neon-gradient-text {
            background: linear-gradient(to right, #34d399, #10b981, #6ee7b7);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-green .neon-gradient-btn {
            background: linear-gradient(135deg, #10b981 0%, #059669 50%, #34d399 100%);
        }

        body.theme-blue {
            --bg-color: #050a1a;
            --grad-1: rgba(59, 130, 246, 0.2);
            --grad-2: rgba(37, 99, 235, 0.2);
            --grad-3: rgba(29, 78, 216, 0.2);
        }
        body.theme-blue .neon-gradient-text {
            background: linear-gradient(to right, #60a5fa, #3b82f6, #93c5fd);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-blue .neon-gradient-btn {
            background: linear-gradient(135deg, #3b82f6 0%, #2563eb 50%, #60a5fa 100%);
        }

        body.theme-yellow {
            --bg-color: #1a1500;
            --grad-1: rgba(234, 179, 8, 0.2);
            --grad-2: rgba(202, 138, 4, 0.2);
            --grad-3: rgba(161, 98, 7, 0.2);
        }
        body.theme-yellow .neon-gradient-text {
            background: linear-gradient(to right, #facc15, #eab308, #fde047);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-yellow .neon-gradient-btn {
            background: linear-gradient(135deg, #eab308 0%, #ca8a04 50%, #facc15 100%);
        }

        body.theme-orange {
            --bg-color: #1a0f00;
            --grad-1: rgba(249, 115, 22, 0.2);
            --grad-2: rgba(251, 146, 60, 0.2);
            --grad-3: rgba(234, 88, 12, 0.2);
        }
        body.theme-orange .neon-gradient-text {
            background: linear-gradient(to right, #fb923c, #f97316, #fdba74);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-orange .neon-gradient-btn {
            background: linear-gradient(135deg, #f97316 0%, #ea580c 50%, #fb923c 100%);
        }

        body.theme-pink {
            --bg-color: #1a0a14;
            --grad-1: rgba(236, 72, 153, 0.2);
            --grad-2: rgba(244, 114, 182, 0.2);
            --grad-3: rgba(219, 39, 119, 0.2);
        }
        body.theme-pink .neon-gradient-text {
            background: linear-gradient(to right, #f472b6, #ec4899, #f9a8d4);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-pink .neon-gradient-btn {
            background: linear-gradient(135deg, #ec4899 0%, #db2777 50%, #f472b6 100%);
        }

        body.theme-crimson {
            --bg-color: #1a0005;
            --grad-1: rgba(220, 38, 38, 0.2);
            --grad-2: rgba(248, 113, 113, 0.2);
            --grad-3: rgba(185, 28, 28, 0.2);
        }
        body.theme-crimson .neon-gradient-text {
            background: linear-gradient(to right, #f87171, #dc2626, #fca5a5);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-crimson .neon-gradient-btn {
            background: linear-gradient(135deg, #dc2626 0%, #b91c1c 50%, #f87171 100%);
        }

        body.theme-cyan {
            --bg-color: #001a1a;
            --grad-1: rgba(6, 182, 212, 0.2);
            --grad-2: rgba(34, 211, 238, 0.2);
            --grad-3: rgba(8, 145, 178, 0.2);
        }
        body.theme-cyan .neon-gradient-text {
            background: linear-gradient(to right, #22d3ee, #06b6d4, #67e8f9);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-cyan .neon-gradient-btn {
            background: linear-gradient(135deg, #06b6d4 0%, #0891b2 50%, #22d3ee 100%);
        }

        body.theme-rainbow {
            --bg-color: #1a1a1d;
            --grad-1: rgba(239, 68, 68, 0.15);
            --grad-2: rgba(234, 179, 8, 0.15);
            --grad-3: rgba(34, 197, 94, 0.15);
        }
        body.theme-rainbow .neon-gradient-text {
            background: linear-gradient(to right, #ef4444, #f59e0b, #10b981, #3b82f6, #8b5cf6, #ec4899);
            background-size: 200% 200%;
            animation: rainbow-text 3s ease infinite;
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        body.theme-rainbow .neon-gradient-btn {
            background: linear-gradient(135deg, #ef4444 0%, #f59e0b 20%, #10b981 40%, #3b82f6 60%, #8b5cf6 80%, #ec4899 100%);
            background-size: 200% 200%;
            animation: rainbow-btn 3s ease infinite;
        }

        @keyframes rainbow-text {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes rainbow-btn {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Эффект переливающегося фона */
        .bg-gradient-effect {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: -1;
            background: 
                radial-gradient(circle at 15% 50%, var(--grad-1), transparent 25%),
                radial-gradient(circle at 85% 30%, var(--grad-2), transparent 25%),
                radial-gradient(circle at 50% 80%, var(--grad-3), transparent 25%);
            filter: blur(40px);
            transition: background 1s ease;
        }

        /* Стекломорфизм с Glow */
        .glass-card {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.36);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .glass-card:hover {
            border-color: rgba(139, 92, 246, 0.3);
            box-shadow: 0 0 30px rgba(139, 92, 246, 0.3), 0 8px 32px 0 rgba(0, 0, 0, 0.36);
        }

        /* Градиент для кнопок и текста (Neon) */
        .neon-gradient-text {
            background: linear-gradient(to right, #c084fc, #6366f1, #ec4899);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .neon-gradient-btn {
            background: linear-gradient(135deg, #8b5cf6 0%, #3b82f6 50%, #ec4899 100%);
            background-size: 200% 200%;
            animation: gradient-move 3s ease infinite;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .neon-gradient-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 20px rgba(139, 92, 246, 0.6);
        }

        @keyframes gradient-move {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Анимация карточек */
        .hover-scale-up {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .hover-scale-up:hover {
            transform: translateY(-10px) scale(1.02);
            border-color: rgba(139, 92, 246, 0.3);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
        }

        .check-icon {
            text-shadow: 0 0 10px rgba(34, 197, 94, 0.5);
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
            animation: fadeIn 0.5s ease-out forwards;
        }

        /* Scroll Animations */
        .scroll-hidden {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s cubic-bezier(0.22, 1, 0.36, 1);
        }
        
        .scroll-show {
            opacity: 1;
            transform: translateY(0);
        }

        .delay-100 { transition-delay: 100ms; }
        .delay-200 { transition-delay: 200ms; }
        .delay-300 { transition-delay: 300ms; }
        .delay-400 { transition-delay: 400ms; }

        /* Typed Text Animation */
        .typed-text {
            overflow: hidden;
            border-right: 3px solid rgba(139, 92, 246, 0.8);
            white-space: nowrap;
            animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: rgba(139, 92, 246, 0.8); }
        }

        /* RGB Cursor */
        body {
            cursor: none;
        }
        
        .custom-cursor {
            position: fixed;
            top: 0;
            left: 0;
            width: 20px;
            height: 20px;
            border: 2px solid white;
            border-radius: 50%;
            pointer-events: none;
            z-index: 9999;
            transform: translate(-50%, -50%);
            transition: transform 0.1s ease;
            mix-blend-mode: difference;
            animation: rgb-border 2s linear infinite;
        }

        .custom-cursor::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            transform: translate(-50%, -50%);
        }

        @keyframes rgb-border {
            0% { border-color: #ff0000; box-shadow: 0 0 10px #ff0000; }
            33% { border-color: #00ff00; box-shadow: 0 0 10px #00ff00; }
            66% { border-color: #0000ff; box-shadow: 0 0 10px #0000ff; }
            100% { border-color: #ff0000; box-shadow: 0 0 10px #ff0000; }
        }

        /* Global cursor and selection rules */
        * {
            cursor: none !important;
            user-select: none;
            -webkit-user-select: none;
        }
        
        input, textarea {
            user-select: text;
            -webkit-user-select: text;
        }

        /* Smooth Scroll */
        html {
            scroll-behavior: smooth;
        }

        /* Section Spacing */
        section {
            scroll-margin-top: 100px;
        }

        /* Globe Container */
        #globe-container {
            width: 100%;
            height: 400px;
            position: relative;
            margin: 2rem 0;
        }

        /* Roadmap Timeline */
        .roadmap-timeline {
            position: relative;
            padding: 2rem 0;
        }

        .roadmap-item {
            position: relative;
            padding-left: 3rem;
            margin-bottom: 3rem;
        }

        .roadmap-item::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            width: 2px;
            height: 100%;
            background: linear-gradient(to bottom, rgba(139, 92, 246, 0.5), transparent);
        }

        .roadmap-item::after {
            content: '';
            position: absolute;
            left: -6px;
            top: 8px;
            width: 14px;
            height: 14px;
            border-radius: 50%;
            background: rgba(139, 92, 246, 0.8);
            box-shadow: 0 0 10px rgba(139, 92, 246, 0.6);
        }

        .roadmap-status {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            border-radius: 9999px;
            font-size: 0.75rem;
            font-weight: 600;
            margin-left: 0.5rem;
        }

        .status-completed {
            background: rgba(34, 197, 94, 0.2);
            color: #34d399;
            border: 1px solid rgba(34, 197, 94, 0.3);
        }

        .status-in-progress {
            background: rgba(59, 130, 246, 0.2);
            color: #60a5fa;
            border: 1px solid rgba(59, 130, 246, 0.3);
        }

        .status-planned {
            background: rgba(139, 92, 246, 0.2);
            color: #c084fc;
            border: 1px solid rgba(139, 92, 246, 0.3);
        }

        /* Demo Widget */
        .demo-widget {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 1.5rem;
            padding: 2rem;
            transition: all 0.4s ease;
        }

        .demo-widget:hover {
            border-color: rgba(139, 92, 246, 0.3);
            box-shadow: 0 0 30px rgba(139, 92, 246, 0.2);
        }

        .demo-result {
            display: none;
            margin-top: 1.5rem;
            padding: 1.5rem;
            background: rgba(16, 185, 129, 0.1);
            border: 1px solid rgba(16, 185, 129, 0.2);
            border-radius: 1rem;
            animation: fadeIn 0.5s ease-out;
        }

        .demo-result.show {
            display: block;
        }

        .demo-loading {
            display: none;
            text-align: center;
            padding: 1rem;
        }

        .demo-loading.show {
            display: block;
        }

        /* Team Cards */
        .team-card {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .team-card:hover {
            transform: translateY(-10px) scale(1.02);
        }

        .team-avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: linear-gradient(135deg, #8b5cf6 0%, #3b82f6 50%, #ec4899 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            margin: 0 auto 1rem;
            border: 3px solid rgba(139, 92, 246, 0.3);
            box-shadow: 0 0 20px rgba(139, 92, 246, 0.4);
        }

        /* Community Dashboard Styles */
        .stat-card {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 1.5rem;
            padding: 2rem;
            text-align: center;
            transition: all 0.4s ease;
        }

        .stat-card:hover {
            transform: translateY(-10px);
            border-color: rgba(139, 92, 246, 0.3);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .stat-number {
            font-size: 3rem;
            font-weight: 800;
            background: linear-gradient(to right, #c084fc, #6366f1, #ec4899);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            font-family: 'Roboto Mono', monospace;
        }

        .stat-label {
            color: var(--text-muted);
            font-size: 0.875rem;
            margin-top: 0.5rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Inline Demo Styles */
        .inline-demo {
            display: none;
            margin-top: 1.5rem;
            padding: 1.5rem;
            background: rgba(16, 185, 129, 0.1);
            border: 1px solid rgba(16, 185, 129, 0.2);
            border-radius: 1rem;
            animation: fadeIn 0.5s ease-out;
        }

        .inline-demo.show {
            display: block;
        }

        .card-demo-input {
            width: 100%;
            padding: 0.75rem;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 0.5rem;
            color: var(--text-color);
            margin-bottom: 1rem;
        }

        /* Animated Number Counter */
        @keyframes countUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .counting {
            animation: countUp 0.5s ease-out;
        }


        /* Tab Navigation Styles */
        .nav-tab {
            position: relative;
            padding: 0.75rem 1.5rem;
            color: var(--text-muted);
            transition: all 0.3s ease;
            cursor: pointer;
            border-bottom: 2px solid transparent;
        }

        .nav-tab:hover {
            color: var(--text-color);
        }

        .nav-tab.active {
            color: var(--text-color);
            border-bottom-color: #8b5cf6;
        }

        /* Search System Button Styles */
        .search-system-btn {
            padding: 1rem 1.5rem;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 0.75rem;
            color: var(--text-color);
            font-weight: 600;
            transition: all 0.3s ease;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .search-system-btn:hover {
            background: rgba(255, 255, 255, 0.1);
            border-color: rgba(139, 92, 246, 0.3);
            transform: translateY(-2px);
        }

        .search-system-btn.active {
            background: linear-gradient(135deg, rgba(139, 92, 246, 0.2), rgba(59, 130, 246, 0.2));
            border-color: #8b5cf6;
            box-shadow: 0 0 20px rgba(139, 92, 246, 0.3);
        }

        /* Demo Report Styles */
        .demo-report {
            display: none;
            margin-top: 2rem;
            padding: 2rem;
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 1.5rem;
            animation: fadeIn 0.5s ease-out;
        }

        .demo-report.show {
            display: block;
        }

        .demo-report.sherlock-style {
            border-left: 4px solid #ef4444;
        }

        .demo-report.vektor-style {
            border-left: 4px solid #3b82f6;
        }

        .demo-report.arictosearch-style {
            border-left: 4px solid #10b981;
        }

        .demo-report.eityu-style {
            border-left: 4px solid #f59e0b;
        }

        /* Loading Animation */
        .search-loading {
            display: none;
            text-align: center;
            padding: 2rem;
        }

        .search-loading.show {
            display: block;
        }

        .loading-spinner {
            width: 60px;
            height: 60px;
            border: 4px solid rgba(139, 92, 246, 0.2);
            border-top-color: #8b5cf6;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 1rem;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Page System Styles */
        .page {
            transition: opacity 0.3s ease;
            -webkit-overflow-scrolling: touch;
        }

        .page.hidden {
            display: none;
        }

        /* Mobile Optimizations */
        @media (max-width: 768px) {
            .page {
                padding-bottom: env(safe-area-inset-bottom);
            }
            
            /* Улучшаем читаемость на мобильных */
            .glass-card {
                backdrop-filter: blur(10px);
                -webkit-backdrop-filter: blur(10px);
            }
            
            /* Убираем hover эффекты на мобильных */
            @media (hover: none) {
                .hover-scale-up:hover {
                    transform: none;
                }
            }
        }

        /* Touch optimization */
        .touch-manipulation {
            touch-action: manipulation;
            -webkit-tap-highlight-color: transparent;
        }
    </style>
</head>
<body class="antialiased min-h-screen flex flex-col">
    <!-- Custom Cursor Element -->
    <div id="customCursor" class="custom-cursor"></div>

    <!-- Animated Grid Background -->
    <div class="grid-background"></div>

    <!-- Navbar -->
    <nav class="fixed top-0 left-0 right-0 z-50 glass-card border-b border-white/10 px-4 py-3 transition-all duration-300">
        <div class="max-w-7xl mx-auto flex items-center justify-between gap-4">
            <!-- Logo -->
            <div class="font-bold text-xl tracking-tight flex items-center gap-2 text-white">
                 <i class="fa-solid fa-bolt text-purple-500"></i> ApexGrid 2025
            </div>
    
            <!-- Navigation Tabs -->
            <div class="hidden md:flex items-center gap-1">
                <a href="#hero" class="nav-tab active" onclick="setActiveTab(this, 'hero')">Главная</a>
                <a href="#search" class="nav-tab" onclick="setActiveTab(this, 'search')">Поиск Информации</a>
                <a href="#projects" class="nav-tab" onclick="setActiveTab(this, 'projects')">Проекты</a>
                <a href="#roadmap" class="nav-tab" onclick="setActiveTab(this, 'roadmap')">Roadmap</a>
            </div>

            <!-- OSINT Search -->
            <div class="relative flex-1 max-w-md hidden lg:flex">
                <div class="relative flex-1 group z-[60]">
                    <i class="fa-solid fa-globe absolute left-3 top-1/2 -translate-y-1/2 text-blue-400 z-[70]"></i>
                    <input type="text" id="osintSearchInput" placeholder="OSINT: IP, Nick, Domain..." class="w-full bg-[#050a10]/90 border border-blue-500/30 rounded-full py-2 pl-10 pr-4 text-sm focus:outline-none focus:border-blue-500 transition-colors text-white placeholder-blue-300/50 relative z-[60]">
                    
                    <!-- OSINT Results Dropdown -->
                    <div id="osintResults" class="absolute top-full left-0 right-0 mt-2 bg-[#02120a] border border-blue-500/20 rounded-xl p-4 hidden z-[100] shadow-2xl">
                        <div id="osintContent" class="text-sm text-gray-300 space-y-2 relative z-[110]">
                            <!-- Results will appear here -->
                        </div>
                    </div>
                </div>
            </div>
    
            <!-- Actions -->
            <div class="flex items-center gap-3">
                <a href="https://t.me/ArictoSintRobot" target="_blank" class="hidden sm:flex items-center gap-2 px-4 py-2 rounded-lg bg-white/5 hover:bg-white/10 transition-colors text-sm font-medium text-white border border-white/10">
                    <i class="fa-solid fa-robot text-pink-400"></i>
                    <span class="hidden lg:inline">Поиск информации</span>
                </a>

                <!-- Visual Settings -->
                <div class="relative">
                    <button id="visualSettingsBtn" class="w-10 h-10 rounded-full bg-white/5 flex items-center justify-center hover:bg-white/10 transition-all duration-300 text-white border border-white/10 outline-none">
                        <i class="fa-solid fa-sliders"></i>
                    </button>
                </div>
    
                <!-- Theme Selector -->
                <div class="relative">
                    <button id="themeMenuBtn" class="w-10 h-10 rounded-full bg-white/5 flex items-center justify-center hover:bg-white/10 transition-all duration-300 text-white border border-white/10 outline-none">
                        <i class="fa-solid fa-palette"></i>
                    </button>
                    <!-- Theme Dropdown -->
                    <div id="themeMenu" class="absolute right-0 mt-2 w-32 bg-dark-900 glass-card rounded-xl shadow-2xl p-2 hidden opacity-0 transition-all duration-300 z-50 transform origin-top-right scale-95">
                        <div class="space-y-1">
                            <button onclick="setTheme('theme-red')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-red-500"></div> Red
                            </button>
                            <button onclick="setTheme('theme-green')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-green-500"></div> Green
                            </button>
                            <button onclick="setTheme('theme-blue')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-blue-500"></div> Blue
                            </button>
                            <button onclick="setTheme('theme-yellow')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-yellow-500"></div> Yellow
                            </button>
                            <button onclick="setTheme('theme-orange')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-orange-500"></div> Orange
                            </button>
                            <button onclick="setTheme('theme-pink')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-pink-500"></div> Pink
                            </button>
                            <button onclick="setTheme('theme-crimson')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-crimson-500"></div> Crimson
                            </button>
                            <button onclick="setTheme('theme-cyan')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-cyan-500"></div> Cyan
                            </button>
                            <button onclick="setTheme('theme-rainbow')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-gradient-to-r from-red-500 via-yellow-500 via-green-500 via-blue-500 to-purple-500"></div> Rainbow
                            </button>
                            <button onclick="setTheme('')" class="w-full text-left px-3 py-2 rounded-lg hover:bg-white/5 text-xs flex items-center gap-2">
                                <div class="w-3 h-3 rounded-full bg-purple-500"></div> Default
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </nav>

    <!-- Фоновые элементы -->
    <div class="bg-gradient-effect"></div>
    
    <!-- Particle Background Canvas -->
    <canvas id="particlesCanvas" class="fixed inset-0 w-full h-full -z-10 pointer-events-none mix-blend-screen opacity-60"></canvas>
    
    <!-- Декоративные шары -->
    <div class="fixed top-0 left-1/4 w-96 h-96 bg-green-500/20 rounded-full mix-blend-screen filter blur-3xl opacity-30 animate-blob -z-10"></div>
    <div class="fixed top-0 right-1/4 w-96 h-96 bg-purple-500/20 rounded-full mix-blend-screen filter blur-3xl opacity-30 animate-blob animation-delay-2000 -z-10"></div>
    <div class="fixed -bottom-32 left-1/2 w-96 h-96 bg-pink-500/20 rounded-full mix-blend-screen filter blur-3xl opacity-30 animate-blob animation-delay-4000 -z-10"></div>

    <!-- Theme Toggle Button -->
    <button id="themeToggle" onclick="toggleTheme()" aria-label="Переключить тему">
        <i id="themeIcon" class="fa-solid fa-moon"></i>
    </button>


    <!-- HERO SECTION -->
    <header id="hero" class="w-full min-h-screen pt-32 pb-20 px-4 text-center relative z-10 flex items-center justify-center scroll-hidden">
        <div class="max-w-5xl mx-auto">
            <h1 class="text-6xl md:text-8xl font-extrabold mb-6 tracking-tight text-white drop-shadow-lg">
                <span id="typedTitle" class="neon-gradient-text"></span>
            </h1>
            <p class="text-xl md:text-3xl text-gray-300 mb-4 max-w-3xl mx-auto font-light leading-relaxed scroll-hidden delay-200">
                Экосистема цифровых инструментов
            </p>
            <p class="text-lg md:text-xl text-purple-400 mb-8 max-w-3xl mx-auto font-medium scroll-hidden delay-200">
                Будущее OSINT уже здесь
            </p>
            
            <div class="flex flex-col md:flex-row items-center justify-center gap-4 scroll-hidden delay-300">
                <a href="#projects" class="inline-flex items-center justify-center px-8 py-4 text-lg font-bold text-white rounded-full neon-gradient-btn shadow-lg w-full md:w-auto hover:scale-105 transition-transform hover-sound">
                    <i class="fa-solid fa-rocket mr-2"></i>
                    Наши Проекты
                </a>
                <button onclick="openOSINTBotsPage()" class="inline-flex items-center justify-center px-8 py-4 text-lg font-bold text-white rounded-full border border-white/20 hover:bg-white/10 hover:border-purple-500/50 transition-all duration-300 w-full md:w-auto glass-card hover-sound">
                    <i class="fa-brands fa-telegram mr-2 text-purple-400"></i>
                    Полезные OSINT боты
                </button>
            </div>
        </div>
    </header>

    <!-- COMMUNITY DASHBOARD SECTION -->
    <section id="dashboard" class="max-w-7xl mx-auto px-4 py-20 relative z-10 scroll-hidden">
        <h2 class="text-4xl md:text-5xl font-bold mb-12 text-center neon-gradient-text uppercase tracking-wider">ApexGrid в цифрах</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
            
            <!-- Stat Card 1 -->
            <div class="stat-card scroll-hidden delay-100">
                <div class="stat-number" id="statUsers">0</div>
                <div class="stat-label">Активных пользователей</div>
            </div>

            <!-- Stat Card 2 -->
            <div class="stat-card scroll-hidden delay-200">
                <div class="stat-number" id="statRequests">0</div>
                <div class="stat-label">Запросов обработано</div>
            </div>

            <!-- Stat Card 3 -->
            <div class="stat-card scroll-hidden delay-300">
                <div class="stat-number" id="statProjects">0</div>
                <div class="stat-label">Проектов в экосистеме</div>
            </div>

            <!-- Stat Card 4 -->
            <div class="stat-card scroll-hidden delay-400">
                <div class="stat-number text-4xl">∞</div>
                <div class="stat-label">Чашек кофе выпито</div>
            </div>

        </div>
    </section>

    <!-- ABOUT SECTION -->
    <section id="about" class="max-w-5xl mx-auto px-4 py-20 relative z-10 scroll-hidden">
        <h2 class="text-4xl md:text-5xl font-bold mb-8 text-center neon-gradient-text uppercase tracking-wider">Что такое ApexGrid?</h2>
        <div class="glass-card rounded-3xl p-8 md:p-12 transform hover:scale-[1.01] transition-transform duration-500">
            <p class="text-lg md:text-xl text-gray-300 leading-relaxed font-light text-center">
                <strong class="text-white">ApexGrid</strong> — это не просто набор инструментов, это централизованная платформа для OSINT-специалистов, разработчиков и энтузиастов. Наша миссия — предоставлять мощные, удобные и доступные решения для работы с информацией и финансами.
            </p>
        </div>
    </section>

    <!-- SEARCH INFORMATION SECTION (Demo Center) -->
    <section id="search" class="max-w-6xl mx-auto px-4 py-20 relative z-10 scroll-hidden">
        <h2 class="text-4xl md:text-5xl font-bold mb-12 text-center neon-gradient-text uppercase tracking-wider">Демо-центр ApexGrid</h2>
        
        <div class="glass-card rounded-3xl p-8 md:p-12">
            <!-- Input Field -->
            <div class="mb-8">
                <label class="block text-sm text-gray-400 mb-3">Введите цель (IP, email, никнейм...)</label>
                <input 
                    type="text" 
                    id="searchTarget" 
                    placeholder="Например: demo@apex.com или 192.168.1.1" 
                    class="w-full bg-white/5 border border-white/10 rounded-xl py-4 px-6 text-white placeholder-gray-500 focus:outline-none focus:border-purple-500 transition-colors text-lg"
                >
            </div>

            <!-- Search System Selection -->
            <div class="mb-8">
                <label class="block text-sm text-gray-400 mb-4">Выберите систему поиска:</label>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
                    <button 
                        class="search-system-btn" 
                        onclick="selectSearchSystem('sherlock', this)"
                        data-system="sherlock"
                    >
                        <span class="text-2xl">🕵️‍♂️</span>
                        <span>Sherlock</span>
                    </button>
                    <button 
                        class="search-system-btn" 
                        onclick="selectSearchSystem('vektor', this)"
                        data-system="vektor"
                    >
                        <span class="text-2xl">🌐</span>
                        <span>Vektor</span>
                    </button>
                    <button 
                        class="search-system-btn" 
                        onclick="selectSearchSystem('arictosearch', this)"
                        data-system="arictosearch"
                    >
                        <span class="text-2xl">🚀</span>
                        <span>ArictoSearch</span>
                    </button>
                    <button 
                        class="search-system-btn" 
                        onclick="selectSearchSystem('eityu', this)"
                        data-system="eityu"
                    >
                        <span class="text-2xl">🔬</span>
                        <span>Eityu Search</span>
                    </button>
                </div>
            </div>

            <!-- Search Button -->
            <div class="text-center mb-6">
                <button 
                    id="startSearchBtn"
                    onclick="startSearch()" 
                    class="px-12 py-4 rounded-xl neon-gradient-btn text-white font-bold text-lg shadow-xl hover:scale-105 transition-transform hover-sound"
                >
                    <i class="fa-solid fa-search mr-2"></i>Начать поиск
                </button>
            </div>

            <!-- Loading Animation -->
            <div id="searchLoading" class="search-loading">
                <div class="loading-spinner"></div>
                <p class="text-purple-400 font-medium">Анализ данных...</p>
            </div>

            <!-- Demo Reports (Different styles for each system) -->
            
            <!-- Sherlock Report -->
            <div id="sherlockReport" class="demo-report sherlock-style">
                <div class="flex items-center gap-3 mb-4">
                    <span class="text-3xl">🕵️‍♂️</span>
                    <h3 class="text-2xl font-bold text-white">Sherlock - Результаты поиска</h3>
                </div>
                <div class="space-y-4">
                    <div class="bg-red-500/10 border border-red-500/20 p-4 rounded-lg">
                        <div class="text-sm text-gray-400 mb-2">Цель:</div>
                        <div class="text-white font-mono text-lg" id="sherlockTarget">demo@apex.com</div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">Найдено профилей:</div>
                            <div class="text-red-400 text-2xl font-bold">23</div>
                        </div>
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">Платформы:</div>
                            <div class="text-white">Twitter, Instagram, GitHub, LinkedIn</div>
                        </div>
                    </div>
                    <div class="bg-white/5 p-4 rounded-lg">
                        <div class="text-sm text-gray-400 mb-2">Детали:</div>
                        <div class="text-gray-300 space-y-1 text-sm">
                            <div>✓ Twitter: @demo_user (активен с 2020)</div>
                            <div>✓ Instagram: demo_user (публичный профиль)</div>
                            <div>✓ GitHub: demo-user (12 репозиториев)</div>
                            <div>✓ LinkedIn: Demo User (работает в Tech Corp)</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Vektor Report -->
            <div id="vektorReport" class="demo-report vektor-style">
                <div class="flex items-center gap-3 mb-4">
                    <span class="text-3xl">🌐</span>
                    <h3 class="text-2xl font-bold text-white">Vektor - Анализ сети</h3>
                </div>
                <div class="space-y-4">
                    <div class="bg-blue-500/10 border border-blue-500/20 p-4 rounded-lg">
                        <div class="text-sm text-gray-400 mb-2">Цель:</div>
                        <div class="text-white font-mono text-lg" id="vektorTarget">demo@apex.com</div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">IP-адреса:</div>
                            <div class="text-blue-400 text-xl font-bold">5</div>
                        </div>
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">Домены:</div>
                            <div class="text-blue-400 text-xl font-bold">3</div>
                        </div>
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">Связи:</div>
                            <div class="text-blue-400 text-xl font-bold">12</div>
                        </div>
                    </div>
                    <div class="bg-white/5 p-4 rounded-lg">
                        <div class="text-sm text-gray-400 mb-2">Сетевая карта:</div>
                        <div class="text-gray-300 space-y-1 text-sm font-mono">
                            <div>→ demo.apex.com (основной домен)</div>
                            <div>→ api.demo.apex.com (API сервер)</div>
                            <div>→ mail.demo.apex.com (почтовый сервер)</div>
                            <div>→ 192.168.1.100 (внутренняя сеть)</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ArictoSearch Report -->
            <div id="arictosearchReport" class="demo-report arictosearch-style">
                <div class="flex items-center gap-3 mb-4">
                    <span class="text-3xl">🚀</span>
                    <h3 class="text-2xl font-bold text-white">ArictoSearch - Комплексный анализ</h3>
                </div>
                <div class="space-y-4">
                    <div class="bg-green-500/10 border border-green-500/20 p-4 rounded-lg">
                        <div class="text-sm text-gray-400 mb-2">Цель:</div>
                        <div class="text-white font-mono text-lg" id="arictosearchTarget">demo@apex.com</div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">Источников данных:</div>
                            <div class="text-green-400 text-2xl font-bold">47</div>
                        </div>
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">Уровень достоверности:</div>
                            <div class="text-green-400 text-xl font-bold">94%</div>
                        </div>
                    </div>
                    <div class="bg-white/5 p-4 rounded-lg">
                        <div class="text-sm text-gray-400 mb-2">Сводка:</div>
                        <div class="text-gray-300 space-y-2 text-sm">
                            <div class="flex items-center gap-2">
                                <i class="fa-solid fa-check-circle text-green-400"></i>
                                <span>Email подтвержден в 8 базах данных</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <i class="fa-solid fa-check-circle text-green-400"></i>
                                <span>Найдено 15 связанных аккаунтов</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <i class="fa-solid fa-check-circle text-green-400"></i>
                                <span>Обнаружено 3 домена</span>
                            </div>
                            <div class="flex items-center gap-2">
                                <i class="fa-solid fa-check-circle text-green-400"></i>
                                <span>История активности: 3 года</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Eityu Search Report -->
            <div id="eityuReport" class="demo-report eityu-style">
                <div class="flex items-center gap-3 mb-4">
                    <span class="text-3xl">🔬</span>
                    <h3 class="text-2xl font-bold text-white">Eityu Search - Глубокий анализ</h3>
                </div>
                <div class="space-y-4">
                    <div class="bg-yellow-500/10 border border-yellow-500/20 p-4 rounded-lg">
                        <div class="text-sm text-gray-400 mb-2">Цель:</div>
                        <div class="text-white font-mono text-lg" id="eityuTarget">demo@apex.com</div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">Уникальных записей:</div>
                            <div class="text-yellow-400 text-2xl font-bold">156</div>
                        </div>
                        <div class="bg-white/5 p-4 rounded-lg">
                            <div class="text-sm text-gray-400 mb-1">Глубина анализа:</div>
                            <div class="text-yellow-400 text-xl font-bold">Максимальная</div>
                        </div>
                    </div>
                    <div class="bg-white/5 p-4 rounded-lg">
                        <div class="text-sm text-gray-400 mb-2">Детальный отчет:</div>
                        <div class="text-gray-300 space-y-2 text-sm">
                            <div><strong class="text-yellow-400">Метаданные:</strong> Извлечено 23 параметра</div>
                            <div><strong class="text-yellow-400">Временные метки:</strong> Первая активность - 2020-03-15</div>
                            <div><strong class="text-yellow-400">Геолокация:</strong> Определено 5 точек</div>
                            <div><strong class="text-yellow-400">Паттерны:</strong> Обнаружено 8 поведенческих паттернов</div>
                            <div><strong class="text-yellow-400">Связи:</strong> 34 связанных объекта в сети</div>
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- PROJECTS SECTION -->
    <section id="projects" class="max-w-7xl mx-auto px-4 py-20 relative z-10 scroll-hidden">
        <h2 class="text-4xl md:text-5xl font-bold mb-12 text-center neon-gradient-text uppercase tracking-wider">Наши Продукты</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8 md:gap-10">
            
            <!-- Card 1: ApexSearch -->
            <div class="glass-card rounded-3xl p-8 hover-scale-up flex flex-col h-full relative overflow-hidden group scroll-hidden delay-100">
                <div class="flex items-center justify-center mb-6">
                    <div class="w-20 h-20 rounded-2xl bg-gradient-to-br from-purple-500/20 to-pink-500/20 flex items-center justify-center text-4xl shadow-lg border border-purple-500/30">
                        🔎
                    </div>
                </div>

                <h3 class="text-2xl font-bold text-white mb-4 text-center">ApexGrid Searcher</h3>
                <p class="text-gray-300 text-center mb-6 flex-grow leading-relaxed">
                    Мощный OSINT-поисковик, объединяющий лучшие базы данных для максимально полного анализа.
                </p>

                <div class="flex gap-3 mb-4">
                    <button onclick="openPricingModal()" class="flex-1 py-3 rounded-xl text-white font-bold text-center neon-gradient-btn shadow-xl hover:scale-105 transition-transform hover-sound">
                        Цены
                    </button>
                    <button onclick="openVersionHistory()" class="flex-1 py-3 rounded-xl bg-white/5 hover:bg-white/10 border border-white/10 text-white font-bold transition-all hover-sound">
                        История версий
                    </button>
                </div>

                <!-- Inline Demo for ApexSearch -->
                <div id="apexDemo" class="inline-demo">
                    <input type="email" id="apexDemoInput" placeholder="Введите email..." class="card-demo-input">
                    <button onclick="runApexDemo()" class="w-full py-2 rounded-lg neon-gradient-btn text-white font-bold text-sm mb-3 hover-sound">
                        Найти
                    </button>
                    <div id="apexDemoResult" class="text-sm text-gray-300 space-y-2 hidden">
                        <div class="bg-white/5 p-2 rounded">Найдено: <span class="text-green-400">12 источников</span></div>
                        <div class="bg-white/5 p-2 rounded">Соцсети: Twitter, Instagram, Telegram</div>
                    </div>
                </div>
            </div>

            <!-- Card 2: A-Bank -->
            <div class="glass-card rounded-3xl p-8 hover-scale-up flex flex-col h-full relative overflow-hidden group scroll-hidden delay-200">
                <div class="flex items-center justify-center mb-6">
                    <div class="w-20 h-20 rounded-2xl bg-gradient-to-br from-blue-500/20 to-cyan-500/20 flex items-center justify-center text-4xl shadow-lg border border-blue-500/30">
                        💳
                    </div>
                </div>

                <h3 class="text-2xl font-bold text-white mb-4 text-center">A-Bank</h3>
                <p class="text-gray-300 text-center mb-6 flex-grow leading-relaxed">
                    Инновационная виртуальная карта и финансовый кошелек, интегрированный в Telegram.
                </p>

                <div class="flex gap-3 mb-4">
                    <a href="https://t.me/arictobankbot" target="_blank" class="flex-1 py-3 rounded-xl text-white font-bold text-center neon-gradient-btn shadow-xl hover:scale-105 transition-transform flex items-center justify-center gap-2 hover-sound">
                        <i class="fa-brands fa-telegram"></i>
                        Бот
                    </a>
                    <button onclick="toggleBankDemo()" class="flex-1 py-3 rounded-xl bg-white/5 hover:bg-white/10 border border-white/10 text-white font-bold transition-all hover-sound">
                        Демо
                    </button>
                </div>

                <!-- Inline Demo for A-Bank -->
                <div id="bankDemo" class="inline-demo">
                    <div class="bg-gradient-to-br from-blue-600 to-purple-600 rounded-xl p-4 mb-3 text-white">
                        <div class="text-xs opacity-75 mb-2">Виртуальная карта</div>
                        <div class="text-2xl font-mono mb-2">**** **** **** 1234</div>
                        <div class="flex justify-between text-sm">
                            <span>Баланс</span>
                            <span id="bankBalance" class="font-bold">0 ₽</span>
                        </div>
                    </div>
                    <button onclick="animateBankBalance()" class="w-full py-2 rounded-lg bg-white/10 hover:bg-white/20 text-white font-bold text-sm transition-all hover-sound">
                        Обновить баланс
                    </button>
                </div>
            </div>

            <!-- Card 3: Bot Constructor -->
            <div class="glass-card rounded-3xl p-8 hover-scale-up flex flex-col h-full relative overflow-hidden group scroll-hidden delay-300 opacity-75">
                <div class="flex items-center justify-center mb-6">
                    <div class="w-20 h-20 rounded-2xl bg-gradient-to-br from-gray-500/20 to-gray-600/20 flex items-center justify-center text-4xl shadow-lg border border-gray-500/30">
                        ⚙️
                    </div>
                </div>

                <h3 class="text-2xl font-bold text-white mb-4 text-center">Конструктор Ботов</h3>
                <p class="text-gray-300 text-center mb-6 flex-grow leading-relaxed">
                    Создавайте собственных Telegram-ботов без программирования. Интуитивный интерфейс и мощные возможности.
                </p>

                <div class="text-center mb-4">
                    <span class="text-purple-400 font-mono text-sm">Скоро в Q2 2025</span>
                </div>

                <button disabled class="w-full py-4 rounded-xl text-gray-500 font-bold text-center bg-white/5 border border-white/10 cursor-not-allowed">
                    В разработке
                </button>
            </div>

        </div>
    </section>

    <!-- LIVE DEMO SECTION -->
    <section id="demo" class="max-w-4xl mx-auto px-4 py-20 relative z-10 scroll-hidden">
        <h2 class="text-4xl md:text-5xl font-bold mb-12 text-center neon-gradient-text uppercase tracking-wider">Попробуйте в действии</h2>
        <div class="demo-widget">
            <p class="text-gray-300 text-center mb-6">Протестируйте возможности ApexGrid Searcher на демо-запросе</p>
            <div class="flex flex-col md:flex-row gap-4">
                <input 
                    type="email" 
                    id="demoInput" 
                    placeholder="Введите email для демо-поиска..." 
                    class="flex-1 bg-white/5 border border-white/10 rounded-xl py-3 px-4 text-white placeholder-gray-500 focus:outline-none focus:border-purple-500 transition-colors"
                >
                <button 
                    onclick="runDemo()" 
                    id="demoButton"
                    class="px-8 py-3 rounded-xl neon-gradient-btn text-white font-bold shadow-lg hover:scale-105 transition-transform"
                >
                    <i class="fa-solid fa-search mr-2"></i>Найти
                </button>
            </div>
            
            <!-- Loading Animation -->
            <div id="demoLoading" class="demo-loading">
                <div class="inline-flex items-center gap-2 text-purple-400">
                    <i class="fa-solid fa-circle-notch fa-spin"></i>
                    <span>Анализ данных...</span>
                </div>
            </div>
            
            <!-- Demo Result -->
            <div id="demoResult" class="demo-result">
                <div class="flex items-center gap-2 mb-4">
                    <i class="fa-solid fa-circle-check text-green-400 text-xl"></i>
                    <h3 class="text-xl font-bold text-white">Результаты поиска</h3>
                </div>
                <div class="space-y-3 text-sm">
                    <div class="bg-white/5 p-3 rounded-lg">
                        <div class="text-gray-400 mb-1">Email:</div>
                        <div class="text-white font-mono">demo@apex.com</div>
                    </div>
                    <div class="bg-white/5 p-3 rounded-lg">
                        <div class="text-gray-400 mb-1">Найдено совпадений:</div>
                        <div class="text-green-400 font-bold">12 источников</div>
                    </div>
                    <div class="bg-white/5 p-3 rounded-lg">
                        <div class="text-gray-400 mb-1">Социальные сети:</div>
                        <div class="flex gap-2 mt-2">
                            <span class="px-2 py-1 bg-blue-500/20 text-blue-400 rounded text-xs">Twitter</span>
                            <span class="px-2 py-1 bg-pink-500/20 text-pink-400 rounded text-xs">Instagram</span>
                            <span class="px-2 py-1 bg-sky-500/20 text-sky-400 rounded text-xs">Telegram</span>
                        </div>
                    </div>
                    <div class="bg-white/5 p-3 rounded-lg">
                        <div class="text-gray-400 mb-1">Дополнительная информация:</div>
                        <div class="text-gray-300">Профиль активен с 2020 года. Присутствует в 5 базах данных.</div>
                    </div>
                </div>
                <div class="mt-4 text-center">
                    <a href="#projects" class="text-purple-400 hover:text-purple-300 text-sm underline">
                        Узнать больше о ApexGrid Searcher →
                    </a>
                </div>
            </div>
        </div>
    </section>

    <!-- ROADMAP SECTION -->
    <section id="roadmap" class="max-w-5xl mx-auto px-4 py-20 relative z-10 scroll-hidden">
        <h2 class="text-4xl md:text-5xl font-bold mb-12 text-center neon-gradient-text uppercase tracking-wider">Наши планы на 2025 год</h2>
        <div class="roadmap-timeline">
            
            <!-- Q1 2025 -->
            <div class="roadmap-item scroll-hidden delay-100">
                <div class="glass-card rounded-2xl p-6">
                    <div class="flex items-center gap-3 mb-3">
                        <h3 class="text-2xl font-bold text-white">Q1 2025</h3>
                        <span class="roadmap-status status-in-progress">В разработке</span>
                    </div>
                    <ul class="space-y-2 text-gray-300">
                        <li class="flex items-start gap-2">
                            <i class="fa-solid fa-spinner text-blue-400 mt-1 fa-spin"></i>
                            <span>Запуск PRO-версии A-Bank</span>
                        </li>
                        <li class="flex items-start gap-2">
                            <i class="fa-solid fa-spinner text-blue-400 mt-1 fa-spin"></i>
                            <span>Интеграция новых баз в ApexGrid Searcher</span>
                        </li>
                    </ul>
                </div>
            </div>

            <!-- Q2 2025 -->
            <div class="roadmap-item scroll-hidden delay-200">
                <div class="glass-card rounded-2xl p-6">
                    <div class="flex items-center gap-3 mb-3">
                        <h3 class="text-2xl font-bold text-white">Q2 2025</h3>
                        <span class="roadmap-status status-planned">Планируется</span>
                    </div>
                    <ul class="space-y-2 text-gray-300">
                        <li class="flex items-start gap-2">
                            <i class="fa-solid fa-circle text-purple-400 mt-1"></i>
                            <span>Релиз конструктора ботов</span>
                        </li>
                        <li class="flex items-start gap-2">
                            <i class="fa-solid fa-circle text-purple-400 mt-1"></i>
                            <span>Обновление дизайна ApexGrid Community</span>
                        </li>
                    </ul>
                </div>
            </div>

            <!-- Q3 2025 -->
            <div class="roadmap-item scroll-hidden delay-300">
                <div class="glass-card rounded-2xl p-6">
                    <div class="flex items-center gap-3 mb-3">
                        <h3 class="text-2xl font-bold text-white">Q3 2025</h3>
                        <span class="roadmap-status status-planned">Планируется</span>
                    </div>
                    <ul class="space-y-2 text-gray-300">
                        <li class="flex items-start gap-2">
                            <i class="fa-solid fa-circle text-purple-400 mt-1"></i>
                            <span>Запуск нового проекта [Секрет]</span>
                        </li>
                        <li class="flex items-start gap-2">
                            <i class="fa-solid fa-circle text-purple-400 mt-1"></i>
                            <span>Расширение функционала ApexGrid Searcher</span>
                        </li>
                    </ul>
                </div>
            </div>

        </div>
    </section>

    <!-- NEWS SECTION -->
    <section id="news" class="max-w-6xl mx-auto px-4 py-20 relative z-10 scroll-hidden">
        <h2 class="text-4xl md:text-5xl font-bold mb-12 text-center neon-gradient-text uppercase tracking-wider">Последние Новости</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            
            <!-- News Card 1 -->
            <div class="glass-card rounded-2xl p-6 hover-scale-up scroll-hidden delay-100">
                <div class="flex items-center gap-3 mb-4">
                    <div class="w-12 h-12 rounded-xl bg-blue-500/20 flex items-center justify-center">
                        <i class="fa-solid fa-bank text-blue-400 text-xl"></i>
                    </div>
                    <div>
                        <div class="text-xs text-gray-500 font-mono">25.10.2024</div>
                        <h3 class="text-lg font-bold text-white">Обновление A-Bank 2.0</h3>
                    </div>
                </div>
                <p class="text-gray-300 text-sm leading-relaxed">
                    Добавлены групповые счета! Теперь вы можете создавать общие кошельки для совместных проектов.
                </p>
            </div>

            <!-- News Card 2 -->
            <div class="glass-card rounded-2xl p-6 hover-scale-up scroll-hidden delay-200">
                <div class="flex items-center gap-3 mb-4">
                    <div class="w-12 h-12 rounded-xl bg-purple-500/20 flex items-center justify-center">
                        <i class="fa-solid fa-gift text-purple-400 text-xl"></i>
                    </div>
                    <div>
                        <div class="text-xs text-gray-500 font-mono">24.10.2024</div>
                        <h3 class="text-lg font-bold text-white">Бесплатный промокод</h3>
                    </div>
                </div>
                <p class="text-gray-300 text-sm leading-relaxed">
                    Бесплатный промокод на 8 запросов в ApexGrid Searcher! Используйте код <span class="font-mono text-purple-400">WELCOME2024</span> при регистрации.
                </p>
            </div>

            <!-- News Card 3 -->
            <div class="glass-card rounded-2xl p-6 hover-scale-up scroll-hidden delay-300">
                <div class="flex items-center gap-3 mb-4">
                    <div class="w-12 h-12 rounded-xl bg-green-500/20 flex items-center justify-center">
                        <i class="fa-solid fa-rocket text-green-400 text-xl"></i>
                    </div>
                    <div>
                        <div class="text-xs text-gray-500 font-mono">23.10.2024</div>
                        <h3 class="text-lg font-bold text-white">Запуск сайта</h3>
                    </div>
                </div>
                <p class="text-gray-300 text-sm leading-relaxed">
                    Мы запустили наш официальный сайт! Теперь вся информация о проектах ApexGrid в одном месте.
                </p>
            </div>

        </div>
        
        <!-- Subscribe Button -->
        <div class="text-center mt-12 scroll-hidden delay-400">
            <button onclick="openSubscribeModal()" class="inline-flex items-center gap-2 px-8 py-4 rounded-full glass-card hover:bg-white/10 hover:border-purple-500/50 transition-all duration-300 text-white font-medium">
                <i class="fa-solid fa-bell text-purple-400"></i>
                Подписаться на обновления
            </button>
        </div>
    </section>

    <!-- TEAM SECTION -->
    <section id="team" class="max-w-6xl mx-auto px-4 py-20 relative z-10 scroll-hidden">
        <h2 class="text-4xl md:text-5xl font-bold mb-12 text-center neon-gradient-text uppercase tracking-wider">Создатели проекта</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-3xl mx-auto">
            
            <!-- Team Card 1: Аристо -->
            <div class="glass-card rounded-3xl p-8 team-card scroll-hidden delay-100">
                <div class="team-avatar">
                    <i class="fa-solid fa-user-astronaut text-white"></i>
                </div>
                <h3 class="text-2xl font-bold text-white mb-2 text-center">Аристо</h3>
                <p class="text-purple-400 text-center mb-4 font-mono">@arioctt</p>
                <p class="text-gray-300 text-center">Основатель и главный разработчик</p>
                <div class="flex justify-center gap-4 mt-6">
                    <a href="https://t.me/arioctt" target="_blank" class="w-10 h-10 rounded-full glass-card flex items-center justify-center hover:scale-110 transition-transform text-purple-400">
                        <i class="fa-brands fa-telegram"></i>
                    </a>
                </div>
            </div>

            <!-- Team Card 2: Placeholder for future team member -->
            <div class="glass-card rounded-3xl p-8 team-card scroll-hidden delay-200 opacity-75">
                <div class="team-avatar" style="background: linear-gradient(135deg, #6b7280 0%, #4b5563 100%);">
                    <i class="fa-solid fa-user-plus text-white"></i>
                </div>
                <h3 class="text-2xl font-bold text-white mb-2 text-center">Скоро</h3>
                <p class="text-gray-400 text-center mb-4 font-mono">@username</p>
                <p class="text-gray-400 text-center">Куратор, тех.поддержка</p>
            </div>

        </div>
    </section>

    <!-- FOOTER -->
    <footer class="w-full py-12 border-t border-white/5 bg-black/20 backdrop-blur-sm z-10 scroll-hidden">
        <div class="max-w-7xl mx-auto px-4">
            <div class="flex flex-col md:flex-row items-center justify-between gap-6 mb-8">
                <div class="text-center md:text-left">
                    <p class="text-2xl font-bold mb-2 neon-gradient-text">ApexGrid Community</p>
                    <p class="text-gray-500 text-sm">&copy; 2025 ApexGrid Community. Все права защищены.</p>
                </div>
                
                <div class="flex items-center gap-4">
                    <a href="https://t.me/ArictoProjectChat" target="_blank" class="w-12 h-12 rounded-full glass-card flex items-center justify-center hover:scale-110 transition-transform text-purple-400">
                        <i class="fa-brands fa-telegram text-xl"></i>
                    </a>
                    <a href="https://t.me/arioctt" target="_blank" class="px-6 py-3 rounded-lg border border-white/10 hover:bg-white/5 hover:border-purple-500/50 transition-all duration-300 text-sm font-medium text-gray-300 flex items-center gap-2">
                        <span>Разработано @arioctt</span>
                        <i class="fa-solid fa-code text-purple-400"></i>
                    </a>
                </div>
            </div>
        </div>
    </footer>

    <!-- Modal: Pricing for ApexGrid Searcher -->
    <div id="pricingModal" class="fixed inset-0 z-[100] hidden flex items-center justify-center bg-black/80 backdrop-blur-sm opacity-0 transition-opacity duration-300">
        <div class="glass-card p-8 rounded-2xl max-w-4xl w-full max-h-[90vh] overflow-y-auto relative transform scale-95 transition-transform duration-300" style="background: #1a1a1d;">
            <button onclick="closePricingModal()" class="absolute top-4 right-4 text-gray-400 hover:text-white transition-colors z-10"><i class="fa-solid fa-xmark text-xl"></i></button>
            
            <h3 class="text-3xl font-bold text-white mb-8 text-center neon-gradient-text">Тарифы ApexGrid Searcher</h3>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Card 1: 1 Day -->
                <div class="glass-card rounded-2xl p-6 hover-scale-up flex flex-col h-full relative overflow-hidden group" 
                     data-title="Подписка ApexGrid Searcher" data-price="80₽" data-period="1 день">
                    <div class="absolute top-0 right-0 bg-gradient-to-bl from-pink-500 to-purple-600 text-white text-xs font-bold px-3 py-1 rounded-bl-xl z-20 shadow-lg">
                        -15%
                    </div>
                    
                    <div class="flex items-center justify-center mb-4">
                        <div class="w-12 h-12 rounded-xl bg-white/10 flex items-center justify-center text-yellow-400 shadow-inner">
                            <i class="fa-solid fa-star text-xl"></i>
                        </div>
                    </div>

                    <h4 class="text-xl font-bold text-white mb-2 text-center">1 день</h4>
                    <div class="flex items-baseline justify-center gap-2 mb-4">
                        <span class="text-4xl font-extrabold text-white">80₽</span>
                    </div>

                    <ul class="space-y-3 mb-6 flex-grow text-gray-300 text-sm">
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Авто Выдача</span>
                        </li>
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Через FunPay</span>
                        </li>
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Отзывы</span>
                        </li>
                    </ul>

                    <button onclick="openPaymentModal(this)" class="w-full py-3 rounded-xl text-white font-bold text-center neon-gradient-btn shadow-xl">
                        Купить за 80₽
                    </button>
                </div>

                <!-- Card 2: 7 Days -->
                <div class="glass-card rounded-2xl p-6 hover-scale-up flex flex-col h-full relative overflow-hidden border-t-4 border-t-blue-500"
                     data-title="Подписка ApexGrid Searcher" data-price="460₽" data-period="7 дней">
                    
                    <div class="flex items-center justify-center mb-4">
                        <div class="w-12 h-12 rounded-xl bg-white/10 flex items-center justify-center text-blue-400 shadow-inner">
                            <i class="fa-solid fa-star text-xl"></i>
                        </div>
                    </div>

                    <h4 class="text-xl font-bold text-white mb-2 text-center">7 дней</h4>
                    <div class="flex items-baseline justify-center gap-2 mb-4">
                        <span class="text-4xl font-extrabold text-white">460₽</span>
                    </div>

                    <ul class="space-y-3 mb-6 flex-grow text-gray-300 text-sm">
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Авто Выдача</span>
                        </li>
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Через FunPay</span>
                        </li>
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Отзывы</span>
                        </li>
                    </ul>

                    <button onclick="openPaymentModal(this)" class="w-full py-3 rounded-xl text-white font-bold text-center neon-gradient-btn shadow-xl">
                        Купить за 460₽
                    </button>
                </div>

                <!-- Card 3: 1 Month -->
                <div class="glass-card rounded-2xl p-6 hover-scale-up flex flex-col h-full relative overflow-hidden"
                     data-title="Подписка ApexGrid Searcher" data-price="580₽" data-period="1 месяц">
                    
                    <div class="flex items-center justify-center mb-4">
                        <div class="w-12 h-12 rounded-xl bg-white/10 flex items-center justify-center text-purple-400 shadow-inner">
                            <i class="fa-solid fa-star text-xl"></i>
                        </div>
                    </div>

                    <h4 class="text-xl font-bold text-white mb-2 text-center">1 месяц</h4>
                    <div class="flex items-baseline justify-center gap-2 mb-4">
                        <span class="text-4xl font-extrabold text-white">580₽</span>
                    </div>

                    <ul class="space-y-3 mb-6 flex-grow text-gray-300 text-sm">
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Авто Выдача</span>
                        </li>
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Через FunPay</span>
                        </li>
                        <li class="flex items-center gap-2">
                            <i class="fa-solid fa-circle-check text-green-400 check-icon"></i>
                            <span>Отзывы</span>
                        </li>
                    </ul>

                    <button onclick="openPaymentModal(this)" class="w-full py-3 rounded-xl text-white font-bold text-center neon-gradient-btn shadow-xl">
                        Купить за 580₽
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal 1: Payment Method -->
    <div id="modal1" class="fixed inset-0 z-[100] hidden flex items-center justify-center bg-black/80 backdrop-blur-sm opacity-0 transition-opacity duration-300">
        <div class="glass-card p-8 rounded-2xl max-w-md w-full relative transform scale-95 transition-transform duration-300" style="background: #1a1a1d;">
            <button onclick="closeModals()" class="absolute top-4 right-4 text-gray-400 hover:text-white transition-colors"><i class="fa-solid fa-xmark text-xl"></i></button>
            <h3 id="modalTitle" class="text-2xl font-bold text-white mb-2">Подписка ApexGrid Searcher</h3>
            <p id="modalPrice" class="text-lg text-purple-400 mb-8 font-semibold">Цена: 80₽</p>
            
            <div class="space-y-4">
                <a href="https://t.me/arioctt" target="_blank" class="block w-full py-3 rounded-xl neon-gradient-btn text-white font-bold text-center shadow-lg hover:scale-105 transition-transform">
                    Купить в ЛС
                </a>
            </div>
        </div>
    </div>

    <!-- Page: Version History -->
    <div id="versionHistoryPage" class="page hidden fixed inset-0 z-[90] overflow-y-auto">
        <div class="min-h-screen bg-[#1a1a1d] pt-24 pb-20 px-4">
            <div class="max-w-4xl mx-auto">
                <button onclick="closeVersionHistory()" class="mb-6 text-gray-400 hover:text-white transition-colors flex items-center gap-2">
                    <i class="fa-solid fa-arrow-left"></i>
                    <span>Назад</span>
                </button>
                
                <h1 class="text-4xl md:text-5xl font-bold mb-12 text-center neon-gradient-text uppercase tracking-wider">История версий ApexGrid Searcher</h1>
                
                <div class="space-y-6">
                    <!-- Version 4.0 -->
                    <div class="glass-card rounded-2xl p-6 border-l-4 border-l-purple-500">
                        <div class="flex items-center justify-between mb-4">
                            <h2 class="text-2xl font-bold text-white">Версия 4.0</h2>
                            <span class="px-3 py-1 rounded-full bg-purple-500/20 text-purple-400 text-sm font-semibold">Текущая версия</span>
                        </div>
                        <p class="text-gray-300">Обновили дизайн, улучшили поисковики.</p>
                    </div>
                    
                    <!-- Version 3.0 -->
                    <div class="glass-card rounded-2xl p-6 border-l-4 border-l-blue-500">
                        <div class="flex items-center justify-between mb-4">
                            <h2 class="text-2xl font-bold text-white">Версия 3.0</h2>
                        </div>
                        <p class="text-gray-300">Перешли на бота @ArictoSintRobot</p>
                    </div>
                    
                    <!-- Version 2.0 -->
                    <div class="glass-card rounded-2xl p-6 border-l-4 border-l-green-500">
                        <div class="flex items-center justify-between mb-4">
                            <h2 class="text-2xl font-bold text-white">Версия 2.0</h2>
                        </div>
                        <p class="text-gray-300">Были на шерлоке, был устаревший вид.</p>
                    </div>
                    
                    <!-- Version 1.0 -->
                    <div class="glass-card rounded-2xl p-6 border-l-4 border-l-gray-500 opacity-60">
                        <div class="flex items-center justify-between mb-4">
                            <h2 class="text-2xl font-bold text-white">Версия 1.0</h2>
                        </div>
                        <p class="text-gray-300">Отсутствует</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Page: OSINT Bots -->
    <div id="osintBotsPage" class="page hidden fixed inset-0 z-[90] overflow-y-auto">
        <div class="min-h-screen bg-[#1a1a1d] pt-16 md:pt-24 pb-8 md:pb-20 px-3 md:px-4">
            <div class="max-w-7xl mx-auto">
                <button onclick="closeOSINTBotsPage()" class="mb-4 md:mb-6 text-gray-400 hover:text-white transition-colors flex items-center gap-2 text-sm md:text-base">
                    <i class="fa-solid fa-arrow-left"></i>
                    <span>Назад</span>
                </button>
                
                <!-- Header Section -->
                <div class="mb-8 md:mb-16">
                    <div class="grid md:grid-cols-2 gap-6 md:gap-8 items-center mb-8 md:mb-12">
                        <div>
                            <h1 class="text-2xl md:text-4xl lg:text-5xl font-bold mb-4 md:mb-6 neon-gradient-text leading-tight">Пробить номер телефона и узнать владельца бесплатно</h1>
                            <p class="text-sm md:text-base lg:text-lg text-gray-300 leading-relaxed">Номер телефона — ключ к данным человека. Наши боты помогут узнать имя, соцсети, историю звонков и даже местоположение. Проверьте, кто вам звонит, или защитите свои данные от утечек.</p>
                        </div>
                        <div class="hidden md:block">
                            <div class="relative h-64 bg-gradient-to-br from-purple-500/20 to-blue-500/20 rounded-3xl flex items-center justify-center">
                                <i class="fa-solid fa-magnifying-glass text-6xl text-purple-400 opacity-50"></i>
                                <div class="absolute top-4 right-4 w-16 h-16 bg-blue-500/30 rounded-full blur-xl"></div>
                                <div class="absolute bottom-4 left-4 w-20 h-20 bg-purple-500/30 rounded-full blur-xl"></div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- About Service Section -->
                <div class="grid md:grid-cols-2 gap-6 md:gap-8 mb-8 md:mb-12">
                    <div class="hidden md:block">
                        <div class="relative h-64 bg-gradient-to-br from-blue-500/20 to-cyan-500/20 rounded-3xl flex items-center justify-center">
                            <i class="fa-solid fa-mobile-screen-button text-6xl text-blue-400 opacity-50"></i>
                        </div>
                    </div>
                    <div class="glass-card rounded-2xl md:rounded-3xl p-4 md:p-8">
                        <h2 class="text-xl md:text-2xl lg:text-3xl font-bold text-white mb-3 md:mb-4">Об услуге</h2>
                        <p class="text-sm md:text-base text-gray-300 leading-relaxed">Хотите пробить номер телефона бесплатно и узнать владельца? Наши боты для пробива анализируют базы данных, соцсети и даже историю звонков. Проверьте, кому принадлежит номер, — возможно, это мошенник или старый знакомый. Поиск по номеру мобильного теперь занимает секунды!</p>
                    </div>
                </div>

                <!-- Navigation Filters -->
                <div class="flex flex-wrap gap-2 md:gap-3 mb-8 md:mb-12 overflow-x-auto pb-2 -mx-3 px-3 md:mx-0 md:px-0">
                    <button class="px-3 md:px-6 py-2 md:py-3 rounded-lg md:rounded-xl bg-white/5 hover:bg-white/10 border border-white/10 text-white text-xs md:text-sm font-medium transition-all whitespace-nowrap touch-manipulation">
                        Бот пробив по номеру телефона
                    </button>
                    <button class="px-3 md:px-6 py-2 md:py-3 rounded-lg md:rounded-xl bg-white/5 hover:bg-white/10 border border-white/10 text-white text-xs md:text-sm font-medium transition-all whitespace-nowrap touch-manipulation">
                        Информация по номеру телефона
                    </button>
                    <button class="px-3 md:px-6 py-2 md:py-3 rounded-lg md:rounded-xl bg-white/5 hover:bg-white/10 border border-white/10 text-white text-xs md:text-sm font-medium transition-all whitespace-nowrap touch-manipulation">
                        Узнать кто звонил по номеру
                    </button>
                    <button class="px-3 md:px-6 py-2 md:py-3 rounded-lg md:rounded-xl bg-white/5 hover:bg-white/10 border border-white/10 text-white text-xs md:text-sm font-medium transition-all whitespace-nowrap touch-manipulation">
                        Проверка номера на утечки данных
                    </button>
                </div>

                <!-- Bots Grid -->
                <div class="mb-8">
                    <h2 class="text-2xl md:text-3xl lg:text-4xl font-bold text-white mb-6 md:mb-8 text-center">Выберите подходящего бота</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">
                        <!-- Bot 1: D Dyxless -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-purple-500/20 to-pink-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    🔍
                                </div>
                                <a href="https://t.me/DyxlessBot" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">D Dyxless</h3>
                            <p class="text-gray-300 text-xs md:text-sm leading-relaxed">Поиск по номеру телефона, имени, паспорту, ИНН, СНИЛС, email, адресу, айпи, паролю, фото. Лучший поиск по тг.</p>
                        </div>

                        <!-- Bot 2: Шерлок -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10 border-l-4 border-l-blue-500">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-blue-500/20 to-cyan-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    ⚡
                                </div>
                                <a href="https://t.me/ArictoSearchFreeBot?start=_ref_MPk1s9_Nnpibw" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">⚡ Шерлок</h3>
                            <p class="text-gray-300 text-xs md:text-sm mb-2 leading-relaxed">⚡Лучший бот для пробива: узнавайте владельца номера телефона, историю авто по VIN, госномеру, доступ из открытых баз.</p>
                            <p class="text-purple-400 font-semibold text-xs md:text-sm">💎Только тут советую покупать подписку!</p>
                        </div>

                        <!-- Bot 3: Enigma Search (GridCMBot) -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10 border-l-4 border-l-green-500">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-green-500/20 to-emerald-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    🎁
                                </div>
                                <a href="https://t.me/GridCMBot" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">Enigma Search</h3>
                            <p class="text-gray-300 text-xs md:text-sm mb-2 leading-relaxed">Аналог получше Шерлока, Поиск по ФИО, номеру, и др.</p>
                            <p class="text-green-400 font-semibold text-xs md:text-sm">🎁 3 запроса бесплатно!</p>
                        </div>

                        <!-- Bot 4: UsersBox -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-orange-500/20 to-red-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    📦
                                </div>
                                <a href="https://t.me/UsersBoxBot" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">UsersBox</h3>
                            <p class="text-gray-300 text-xs md:text-sm leading-relaxed">Поиск по ФИО, телефону, адресу, IP и соцсетям. Советую покупать подписку для поиска по ФИО и другим данным!</p>
                        </div>

                        <!-- Bot 5: Himera Search -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-pink-500/20 to-rose-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    🔥
                                </div>
                                <a href="https://t.me/HimeraSearchBot" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">Himera Search</h3>
                            <p class="text-gray-300 text-xs md:text-sm leading-relaxed">Очень хороший бот для пробива по ФИО. Найдёт в 99% случаев!</p>
                        </div>

                        <!-- Bot 6: ВЕКТОР -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-cyan-500/20 to-blue-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    🌐
                                </div>
                                <a href="https://t.me/vektor_bot" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">ВЕКТОР</h3>
                            <p class="text-gray-300 text-xs md:text-sm mb-2 leading-relaxed">3 бесплатных запроса по ФИО, авто, контактам и документам.</p>
                        </div>

                        <!-- Bot 7: Leak OSINT -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10 border-l-4 border-l-yellow-500">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-yellow-500/20 to-orange-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    ⚠️
                                </div>
                                <a href="https://t.me/LeakOSINTBot" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">⚠️ Leak OSINT</h3>
                            <p class="text-gray-300 text-xs md:text-sm mb-2 leading-relaxed">⚠️ Для ру: поставьте язык в телеграм на английский ⚠️</p>
                            <p class="text-gray-300 text-xs md:text-sm leading-relaxed">Поиск по почте, имени, телефону, паролю, авто, Telegram, FB, VK, IP.</p>
                        </div>

                        <!-- Bot 8: InfoLab -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-indigo-500/20 to-purple-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    🧪
                                </div>
                                <a href="https://t.me/InfoLabBot" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">InfoLab</h3>
                            <p class="text-gray-300 text-xs md:text-sm leading-relaxed">Поиск по фото, ФИО, контактам, документам, авто, адресу, соцсетям и вебкам/эскорт.</p>
                        </div>

                        <!-- Bot 9: InfoTrackPeople -->
                        <div class="glass-card rounded-xl md:rounded-2xl p-4 md:p-6 hover-scale-up border border-white/10">
                            <div class="flex items-center justify-between mb-3 md:mb-4">
                                <div class="w-10 h-10 md:w-12 md:h-12 rounded-lg md:rounded-xl bg-gradient-to-br from-teal-500/20 to-cyan-500/20 flex items-center justify-center text-xl md:text-2xl">
                                    👤
                                </div>
                                <a href="https://t.me/InfoTrackPeopleBot" target="_blank" class="px-3 md:px-4 py-2 rounded-lg neon-gradient-btn text-white text-xs md:text-sm font-semibold hover:scale-105 transition-transform touch-manipulation min-h-[44px] flex items-center justify-center">
                                    Открыть
                                </a>
                            </div>
                            <h3 class="text-lg md:text-xl font-bold text-white mb-2">InfoTrackPeople</h3>
                            <p class="text-gray-300 text-xs md:text-sm mb-2 leading-relaxed">Найдет ФИО и дату, телефон, почту, ИНН, паспорт, СНИЛС, загран, адреса, номера авто, VIN-коды, аккаунты и пароли, ТГ сообщения и др.</p>
                            <p class="text-green-400 font-semibold text-xs md:text-sm">3 запроса в день бесплатно.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal 4: Subscribe to Updates -->
    <div id="subscribeModal" class="fixed inset-0 z-[100] hidden flex items-center justify-center bg-black/80 backdrop-blur-sm opacity-0 transition-opacity duration-300">
        <div class="glass-card p-8 rounded-2xl max-w-md w-full relative transform scale-95 transition-transform duration-300" style="background: #1a1a1d;">
            <button onclick="closeSubscribeModal()" class="absolute top-4 right-4 text-gray-400 hover:text-white transition-colors"><i class="fa-solid fa-xmark text-xl"></i></button>
            
            <div class="text-center mb-6">
                <div class="w-16 h-16 rounded-full bg-purple-500/20 flex items-center justify-center mx-auto mb-4">
                    <i class="fa-solid fa-bell text-purple-400 text-2xl"></i>
                </div>
                <h3 class="text-2xl font-bold text-white mb-2">Подписка на обновления</h3>
                <p class="text-gray-400 text-sm">Получайте уведомления о новых функциях и обновлениях</p>
            </div>
            
            <div class="space-y-4">
                <div>
                    <input 
                        id="subscribeEmail" 
                        type="email" 
                        placeholder="Ваш email" 
                        class="w-full bg-white/5 border border-white/10 rounded-xl py-3 px-4 text-white placeholder-gray-500 focus:outline-none focus:border-purple-500 transition-colors"
                    >
                </div>
                <button onclick="submitSubscribe()" class="w-full py-3 rounded-xl neon-gradient-btn text-white font-bold shadow-lg">
                    <i class="fa-solid fa-check mr-2"></i>Подписаться
                </button>
            </div>
        </div>
    </div>

    <!-- Modal 3: Visual Settings -->
    <div id="visualSettingsModal" class="fixed inset-0 z-[100] hidden flex items-center justify-center bg-black/80 backdrop-blur-sm opacity-0 transition-opacity duration-300">
        <div class="glass-card p-6 rounded-2xl max-w-2xl w-full max-h-[90vh] overflow-y-auto relative transform scale-95 transition-transform duration-300" style="background: #1a1a1d;">
            <button onclick="closeVisualSettings()" class="absolute top-4 right-4 text-gray-400 hover:text-white transition-colors z-10"><i class="fa-solid fa-xmark text-xl"></i></button>
            
            <h3 class="text-2xl font-bold text-white mb-6 flex items-center gap-2">
                <i class="fa-solid fa-sliders text-purple-400"></i> Настройки визуализации
            </h3>
            
            <div class="space-y-6">
                <!-- Particles Settings -->
                <div class="bg-white/5 p-4 rounded-xl border border-white/10">
                    <div class="flex items-center justify-between mb-4">
                        <label class="text-white font-medium flex items-center gap-2">
                            <i class="fa-solid fa-sparkles text-blue-400"></i> Частицы на фоне
                        </label>
                        <label class="relative inline-flex items-center cursor-pointer">
                            <input type="checkbox" id="particlesToggle" class="sr-only peer" checked onchange="toggleParticles()">
                            <div class="w-11 h-6 bg-gray-600 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-purple-600"></div>
                        </label>
                    </div>
                    <div id="particlesSettings" class="space-y-3">
                        <div>
                            <label class="block text-xs text-gray-400 mb-2">Плотность частиц: <span id="particlesDensityValue">50</span>%</label>
                            <input type="range" id="particlesDensity" min="0" max="100" value="50" class="w-full h-2 bg-gray-700 rounded-lg appearance-none cursor-pointer" oninput="updateParticlesDensity(this.value)">
                        </div>
                        <div>
                            <label class="block text-xs text-gray-400 mb-2">Прозрачность: <span id="particlesOpacityValue">60</span>%</label>
                            <input type="range" id="particlesOpacity" min="0" max="100" value="60" class="w-full h-2 bg-gray-700 rounded-lg appearance-none cursor-pointer" oninput="updateParticlesOpacity(this.value)">
                        </div>
                    </div>
                </div>

                <!-- Background Effects -->
                <div class="bg-white/5 p-4 rounded-xl border border-white/10">
                    <div class="flex items-center justify-between mb-4">
                        <label class="text-white font-medium flex items-center gap-2">
                            <i class="fa-solid fa-circle-nodes text-green-400"></i> Градиентные эффекты
                        </label>
                        <label class="relative inline-flex items-center cursor-pointer">
                            <input type="checkbox" id="gradientToggle" class="sr-only peer" checked onchange="toggleGradient()">
                            <div class="w-11 h-6 bg-gray-600 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-purple-600"></div>
                        </label>
                    </div>
                </div>

                <!-- Cursor Settings -->
                <div class="bg-white/5 p-4 rounded-xl border border-white/10">
                    <div class="flex items-center justify-between mb-4">
                        <label class="text-white font-medium flex items-center gap-2">
                            <i class="fa-solid fa-mouse-pointer text-yellow-400"></i> RGB Курсор
                        </label>
                        <label class="relative inline-flex items-center cursor-pointer">
                            <input type="checkbox" id="cursorToggle" class="sr-only peer" checked onchange="toggleCursor()">
                            <div class="w-11 h-6 bg-gray-600 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-purple-600"></div>
                        </label>
                    </div>
                    <div class="mt-4">
                        <label class="block text-sm text-gray-400 mb-2">Загрузить свой курсор (PNG, CUR)</label>
                        <input type="file" id="customCursorFile" accept=".png,.cur,.svg" class="w-full text-sm text-gray-400 file:mr-4 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-sm file:font-semibold file:bg-purple-500/10 file:text-purple-400 hover:file:bg-purple-500/20 cursor-pointer bg-white/5 rounded-xl p-1 border border-white/10" onchange="loadCustomCursor(this)">
                        <button onclick="resetCustomCursor()" class="mt-2 w-full py-2 rounded-lg bg-white/5 hover:bg-white/10 border border-white/10 text-white text-sm transition-colors">
                            <i class="fa-solid fa-rotate-left mr-2"></i> Сбросить на стандартный
                        </button>
                    </div>
                </div>

                <!-- Reset Button -->
                <div class="flex gap-3 pt-2">
                    <button onclick="resetVisualSettings()" class="flex-1 py-3 rounded-xl bg-red-500/10 hover:bg-red-500/20 border border-red-500/30 text-red-400 font-medium transition-colors">
                        <i class="fa-solid fa-rotate-left mr-2"></i> Сбросить
                    </button>
                    <button onclick="closeVisualSettings()" class="flex-1 py-3 rounded-xl neon-gradient-btn text-white font-bold shadow-lg">
                        <i class="fa-solid fa-check mr-2"></i> Применить
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Typed Text Animation for Hero Title
        function typeText(element, text, speed = 100) {
            let i = 0;
            element.textContent = '';
            function type() {
                if (i < text.length) {
                    element.textContent += text.charAt(i);
                    i++;
                    setTimeout(type, speed);
                } else {
                    element.classList.add('typed-text');
                }
            }
            type();
        }

        // Initialize typed text on load
        window.addEventListener('DOMContentLoaded', () => {
            const typedTitle = document.getElementById('typedTitle');
            if (typedTitle) {
                typeText(typedTitle, 'ApexGrid 2025', 80);
            }
        });

        // ==========================================
        // DAY/NIGHT MODE TOGGLE
        // ==========================================
        function toggleTheme() {
            const body = document.body;
            const themeIcon = document.getElementById('themeIcon');
            const isLight = body.classList.contains('light-theme');
            
            if (isLight) {
                body.classList.remove('light-theme');
                themeIcon.className = 'fa-solid fa-moon';
                localStorage.setItem('theme', 'dark');
                
            } else {
                body.classList.add('light-theme');
                themeIcon.className = 'fa-solid fa-sun';
                localStorage.setItem('theme', 'light');
                
            }
            
            playClickSound();
        }

        // Load saved day/night theme
        const savedDayNightTheme = localStorage.getItem('theme');
        if (savedDayNightTheme === 'light') {
            document.body.classList.add('light-theme');
            document.getElementById('themeIcon').className = 'fa-solid fa-sun';
        }

        // ==========================================
        // SOUND EFFECTS
        // ==========================================
        let soundsEnabled = localStorage.getItem('soundsEnabled') !== 'false';
        
        function playHoverSound() {
            if (!soundsEnabled) return;
            try {
                const audio = new Audio('data:audio/wav;base64,UklGRnoGAABXQVZFZm10IBAAAAABAAEAQB8AAEAfAAABAAgAZGF0YQoGAACBhYqFbF1fdJivrJBhNjVgodDbq2EcBj+a2/LDciUFLIHO8tiJNwgZaLvt559NEAxQp+PwtmMcBjiR1/LMeSwFJHfH8N2QQAoUXrTp66hVFApGn+DyvmwhBSuBzvLZiTYIG2m98OSfTgwMT6fj8LZjHAY4kdfyzHksBSR3x/DdkEAKFF606euoVRQKRp/g8r5sIQUrgc7y2Yk2CBtpvfDkn04MDE+n4/C2YxwGOJHX8sx5LAUkd8fw3ZBAC');
                audio.volume = 0.1;
                audio.play().catch(() => {});
            } catch (e) {}
        }

        function playClickSound() {
            if (!soundsEnabled) return;
            try {
                const audio = new Audio('data:audio/wav;base64,UklGRnoGAABXQVZFZm10IBAAAAABAAEAQB8AAEAfAAABAAgAZGF0YQoGAACBhYqFbF1fdJivrJBhNjVgodDbq2EcBj+a2/LDciUFLIHO8tiJNwgZaLvt559NEAxQp+PwtmMcBjiR1/LMeSwFJHfH8N2QQAoUXrTp66hVFApGn+DyvmwhBSuBzvLZiTYIG2m98OSfTgwMT6fj8LZjHAY4kdfyzHksBSR3x/DdkEAKFF606euoVRQKRp/g8r5sIQUrgc7y2Yk2CBtpvfDkn04MDE+n4/C2YxwGOJHX8sx5LAUkd8fw3ZBAC');
                audio.volume = 0.2;
                audio.play().catch(() => {});
            } catch (e) {}
        }

        // Add hover sound to all interactive elements
        document.addEventListener('DOMContentLoaded', () => {
            document.querySelectorAll('.hover-sound').forEach(el => {
                el.addEventListener('mouseenter', playHoverSound);
                el.addEventListener('click', playClickSound);
            });
        });

        // Theme Management
        const body = document.body;
        const themeMenuBtn = document.getElementById('themeMenuBtn');
        const themeMenu = document.getElementById('themeMenu');
        let isMenuOpen = false;
        
        // Check local storage for saved theme
        const savedTheme = localStorage.getItem('selectedTheme');
        if (savedTheme) {
            body.classList.add(savedTheme);
        }

        // Toggle Theme Menu Logic
        themeMenuBtn.addEventListener('click', (e) => {
            e.stopPropagation();
            isMenuOpen = !isMenuOpen;
            toggleMenuUI();
        });

        function toggleMenuUI() {
            if (isMenuOpen) {
                themeMenu.classList.remove('hidden', 'opacity-0', 'scale-95');
                themeMenu.classList.add('block', 'opacity-100', 'scale-100');
                themeMenuBtn.style.transform = 'scale(1.2)';
                themeMenuBtn.classList.add('bg-white/20');
            } else {
                themeMenu.classList.add('hidden', 'opacity-0', 'scale-95');
                themeMenu.classList.remove('block', 'opacity-100', 'scale-100');
                themeMenuBtn.style.transform = 'scale(1)';
                themeMenuBtn.classList.remove('bg-white/20');
            }
        }

        // Close menus when clicking outside
        document.addEventListener('click', (e) => {
            if (isMenuOpen && !themeMenu.contains(e.target) && e.target !== themeMenuBtn) {
                isMenuOpen = false;
                toggleMenuUI();
            }
        });

        function setTheme(themeName) {
            body.classList.remove('theme-red', 'theme-green', 'theme-blue', 'theme-yellow', 'theme-orange', 'theme-pink', 'theme-crimson', 'theme-cyan', 'theme-rainbow');
            if (themeName) {
                body.classList.add(themeName);
                localStorage.setItem('selectedTheme', themeName);
            } else {
                localStorage.removeItem('selectedTheme');
            }
            isMenuOpen = false;
            toggleMenuUI();
            
            // Показываем уведомление о применении темы
            showThemeNotification(themeName);
        }

        function showThemeNotification(themeName) {
            const themeNames = {
                'theme-red': 'Красная',
                'theme-green': 'Зелёная',
                'theme-blue': 'Синяя',
                'theme-yellow': 'Жёлтая',
                'theme-orange': 'Оранжевая',
                'theme-pink': 'Розовая',
                'theme-crimson': 'Малиновая',
                'theme-cyan': 'Голубая',
                'theme-rainbow': 'Радужная',
                '': 'Стандартная'
            };
            
            const themeNameText = themeNames[themeName] || 'Стандартная';
            
            // Создаем уведомление
            const notification = document.createElement('div');
            notification.className = 'fixed top-20 right-4 z-[9999] bg-white/10 backdrop-blur-md border border-white/20 rounded-xl px-6 py-4 shadow-2xl transform transition-all duration-300';
            notification.style.opacity = '0';
            notification.style.transform = 'translateX(400px)';
            notification.innerHTML = `
                <div class="flex items-center gap-3">
                    <i class="fa-solid fa-palette text-purple-400 text-xl"></i>
                    <div>
                        <div class="text-white font-semibold">Тема применена</div>
                        <div class="text-gray-400 text-sm">${themeNameText} тема</div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(notification);
            
            // Анимация появления
            setTimeout(() => {
                notification.style.opacity = '1';
                notification.style.transform = 'translateX(0)';
            }, 10);
            
            // Удаление через 3 секунды
            setTimeout(() => {
                notification.style.opacity = '0';
                notification.style.transform = 'translateX(400px)';
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 300);
            }, 3000);
        }


        // OSINT Search Functionality
        const osintInput = document.getElementById('osintSearchInput');
        const osintResults = document.getElementById('osintResults');
        const osintContent = document.getElementById('osintContent');
        let searchTimeout;

        if (osintInput) {
            osintInput.addEventListener('input', (e) => {
                clearTimeout(searchTimeout);
                const query = e.target.value.trim();
                
                if (!query) {
                    osintResults.classList.add('hidden');
                    return;
                }

                osintResults.classList.remove('hidden');
                osintContent.innerHTML = '<div class="text-center text-blue-400 py-2"><i class="fa-solid fa-circle-notch fa-spin"></i> Анализ данных...</div>';

                searchTimeout = setTimeout(() => performOsintSearch(query), 800);
            });

            document.addEventListener('click', (e) => {
                if (!osintInput.contains(e.target) && !osintResults.contains(e.target)) {
                    osintResults.classList.add('hidden');
                }
            });
        }

        async function performOsintSearch(query) {
            let resultsHtml = '';
            
            try {
                const isIP = /^(\d{1,3}\.){3}\d{1,3}$/.test(query);
                const isDomain = query.includes('.') && !query.includes(' ') && !isIP && query.length > 4;
                
                if (isIP) {
                    try {
                        const res = await fetch(`https://ipwho.is/${query}`);
                        const data = await res.json();
                        if(data.success) {
                            resultsHtml += `
                                <div class="font-bold text-white mb-2 border-b border-white/10 pb-1"><i class="fa-solid fa-location-dot text-red-400"></i> IP Разведка</div>
                                <div class="grid grid-cols-2 gap-x-4 gap-y-2 text-xs">
                                    <div><span class="text-gray-500">Страна:</span> ${data.country} ${data.flag.emoji}</div>
                                    <div><span class="text-gray-500">Город:</span> ${data.city}</div>
                                    <div><span class="text-gray-500">ISP:</span> ${data.connection.isp}</div>
                                    <div><span class="text-gray-500">IP:</span> ${data.ip}</div>
                                </div>
                            `;
                        }
                    } catch (e) {
                        resultsHtml = `<div class="text-red-400 text-xs">Информация об IP недоступна.</div>`;
                    }
                } else if (isDomain) {
                     resultsHtml += `
                        <div class="font-bold text-white mb-2 border-b border-white/10 pb-1"><i class="fa-solid fa-network-wired text-green-400"></i> Домен</div>
                        <div class="space-y-2 text-xs">
                             <a href="https://who.is/whois/${query}" target="_blank" class="block bg-white/5 p-2 rounded hover:bg-white/10 transition">WHOIS Lookup</a>
                             <a href="https://crt.sh/?q=${query}" target="_blank" class="block bg-white/5 p-2 rounded hover:bg-white/10 transition">SSL Сертификаты</a>
                        </div>
                     `;
                } else {
                    resultsHtml += `<div class="font-bold text-white mb-2 border-b border-white/10 pb-1"><i class="fa-solid fa-user-secret text-purple-400"></i> Цифровой след</div>`;
                    resultsHtml += `
                        <div class="grid grid-cols-2 gap-2 text-xs">
                             <a href="https://www.google.com/search?q=site:instagram.com+${query}" target="_blank" class="bg-white/5 p-2 rounded hover:bg-white/10 transition">Instagram</a>
                             <a href="https://t.me/${query}" target="_blank" class="bg-white/5 p-2 rounded hover:bg-white/10 transition">Telegram</a>
                        </div>
                    `;
                }

                if (!resultsHtml) {
                    resultsHtml = '<div class="text-gray-500 text-center py-2">Нет данных.</div>';
                }

                osintContent.innerHTML = resultsHtml;
            
            } catch (error) {
                osintContent.innerHTML = '<div class="text-red-400 text-center py-2 text-xs">Ошибка соединения.</div>';
            }
        }

        // Scroll Animation Observer
        const observerOptions = {
            root: null,
            rootMargin: '0px',
            threshold: 0.1
        };

        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('scroll-show');
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        document.querySelectorAll('.scroll-hidden').forEach((el) => {
            observer.observe(el);
        });

        // Custom Cursor Logic
        const cursor = document.getElementById('customCursor');
        
        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
        });

        document.addEventListener('mousedown', () => {
            cursor.style.transform = 'translate(-50%, -50%) scale(0.8)';
        });

        document.addEventListener('mouseup', () => {
            cursor.style.transform = 'translate(-50%, -50%) scale(1)';
        });

        const interactables = document.querySelectorAll('a, button, input');
        interactables.forEach(el => {
            el.addEventListener('mouseenter', () => {
                cursor.style.transform = 'translate(-50%, -50%) scale(1.5)';
                cursor.style.backgroundColor = 'rgba(255, 255, 255, 0.1)';
            });
            el.addEventListener('mouseleave', () => {
                cursor.style.transform = 'translate(-50%, -50%) scale(1)';
                cursor.style.backgroundColor = 'transparent';
            });
        });

        // Particle Background Animation
        const canvas = document.getElementById('particlesCanvas');
        const ctx = canvas.getContext('2d');
        window.particlesArray = [];

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        window.Particle = class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.directionX = (Math.random() * 0.4) - 0.2;
                this.directionY = (Math.random() * 0.4) - 0.2;
                this.size = Math.random() * 2;
                this.color = 'rgba(255, 255, 255, 0.3)';
            }
            
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2, false);
                ctx.fillStyle = this.color;
                ctx.fill();
            }

            update() {
                if (this.x > canvas.width || this.x < 0) {
                    this.directionX = -this.directionX;
                }
                if (this.y > canvas.height || this.y < 0) {
                    this.directionY = -this.directionY;
                }
                this.x += this.directionX;
                this.y += this.directionY;
                this.draw();
            }
        }

        window.initParticles = function() {
            window.particlesArray = [];
            let numberOfParticles = (canvas.height * canvas.width) / 15000;
            for (let i = 0; i < numberOfParticles; i++) {
                window.particlesArray.push(new window.Particle());
            }
        }

        function animateParticles() {
            requestAnimationFrame(animateParticles);
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            for (let i = 0; i < window.particlesArray.length; i++) {
                window.particlesArray[i].update();
            }
        }

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            window.initParticles();
        });

        window.initParticles();
        animateParticles();

        // Pricing Modal Functions
        function openPricingModal() {
            const modal = document.getElementById('pricingModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.remove('opacity-0');
                modal.querySelector('div').classList.remove('scale-95');
                modal.querySelector('div').classList.add('scale-100');
            }, 10);
        }

        function closePricingModal() {
            const modal = document.getElementById('pricingModal');
            modal.classList.add('opacity-0');
            modal.querySelector('div').classList.add('scale-95');
            modal.querySelector('div').classList.remove('scale-100');
            setTimeout(() => modal.classList.add('hidden'), 300);
        }

        document.getElementById('pricingModal').addEventListener('click', (e) => {
            if (e.target.id === 'pricingModal') closePricingModal();
        });

        // Payment Modal Functions
        const modal1 = document.getElementById('modal1');
        const modalTitle = document.getElementById('modalTitle');
        const modalPrice = document.getElementById('modalPrice');
        let currentPrice = '';
        let currentTitle = '';
        let currentPeriod = '';

        function openPaymentModal(btn) {
            closePricingModal();
            const card = btn.closest('.glass-card');
            const title = card.getAttribute('data-title');
            const price = card.getAttribute('data-price');
            const period = card.getAttribute('data-period');
            
            currentPrice = price;
            currentTitle = title;
            currentPeriod = period;
            modalTitle.textContent = `${title} (${period})`;
            modalPrice.textContent = `Цена: ${price}`;
            
            showModal(modal1);
        }

        function closeModals() {
            hideModal(modal1);
        }

        function showModal(modal) {
            modal.classList.remove('hidden');
            void modal.offsetWidth;
            modal.classList.remove('opacity-0');
            modal.querySelector('div').classList.remove('scale-95');
            modal.querySelector('div').classList.add('scale-100');
        }

        function hideModal(modal) {
            modal.classList.add('opacity-0');
            modal.querySelector('div').classList.add('scale-95');
            modal.querySelector('div').classList.remove('scale-100');
            setTimeout(() => modal.classList.add('hidden'), 300);
        }

        modal1.addEventListener('click', (e) => {
            if (e.target === modal1) closeModals();
        });

        function copyText(btn, text) {
            navigator.clipboard.writeText(text).then(() => {
                const icon = btn.querySelector('i');
                const originalClass = icon.className;
                icon.className = 'fa-solid fa-check';
                btn.classList.add('text-green-400');
                setTimeout(() => {
                    icon.className = originalClass;
                    btn.classList.remove('text-green-400');
                }, 2000);
            });
        }

        // Page System Functions
        function showPage(pageId) {
            const page = document.getElementById(pageId);
            if (page) {
                page.classList.remove('hidden');
                document.body.style.overflow = 'hidden';
            }
        }

        function hidePage(pageId) {
            const page = document.getElementById(pageId);
            if (page) {
                page.classList.add('hidden');
                document.body.style.overflow = '';
            }
        }

        function openVersionHistory() {
            showPage('versionHistoryPage');
            playClickSound();
        }

        function closeVersionHistory() {
            hidePage('versionHistoryPage');
            playClickSound();
        }

        function openOSINTBotsPage() {
            showPage('osintBotsPage');
            playClickSound();
        }

        function closeOSINTBotsPage() {
            hidePage('osintBotsPage');
            playClickSound();
        }

        // Visual Settings
        const visualSettingsModal = document.getElementById('visualSettingsModal');
        const visualSettingsBtn = document.getElementById('visualSettingsBtn');
        let particlesEnabled = true;
        let gradientEnabled = true;
        let cursorEnabled = true;

        visualSettingsBtn.addEventListener('click', () => {
            visualSettingsModal.classList.remove('hidden');
            setTimeout(() => {
                visualSettingsModal.classList.remove('opacity-0');
                visualSettingsModal.querySelector('div').classList.remove('scale-95');
                visualSettingsModal.querySelector('div').classList.add('scale-100');
            }, 10);
        });

        function closeVisualSettings() {
            visualSettingsModal.classList.add('opacity-0');
            visualSettingsModal.querySelector('div').classList.add('scale-95');
            visualSettingsModal.querySelector('div').classList.remove('scale-100');
            setTimeout(() => visualSettingsModal.classList.add('hidden'), 300);
        }

        visualSettingsModal.addEventListener('click', (e) => {
            if (e.target === visualSettingsModal) closeVisualSettings();
        });

        function toggleParticles() {
            particlesEnabled = document.getElementById('particlesToggle').checked;
            const canvas = document.getElementById('particlesCanvas');
            if (canvas) {
                canvas.style.display = particlesEnabled ? 'block' : 'none';
            }
        }

        function updateParticlesDensity(value) {
            document.getElementById('particlesDensityValue').textContent = value;
            if (particlesEnabled && window.Particle) {
                const canvas = document.getElementById('particlesCanvas');
                const density = value / 100;
                window.particlesArray = [];
                let numberOfParticles = ((canvas.height * canvas.width) / 15000) * density;
                for (let i = 0; i < numberOfParticles; i++) {
                    window.particlesArray.push(new window.Particle());
                }
            }
        }

        function updateParticlesOpacity(value) {
            document.getElementById('particlesOpacityValue').textContent = value;
            const canvas = document.getElementById('particlesCanvas');
            if (canvas) {
                canvas.style.opacity = value / 100;
            }
        }

        function toggleGradient() {
            gradientEnabled = document.getElementById('gradientToggle').checked;
            const gradient = document.querySelector('.bg-gradient-effect');
            if (gradient) {
                gradient.style.display = gradientEnabled ? 'block' : 'none';
            }
        }

        function toggleCursor() {
            cursorEnabled = document.getElementById('cursorToggle').checked;
            const cursor = document.getElementById('customCursor');
            if (cursor) {
                cursor.style.display = cursorEnabled ? 'block' : 'none';
            }
        }

        function loadCustomCursor(input) {
            const file = input.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const cursor = document.getElementById('customCursor');
                    if (cursor) {
                        // Сохраняем оригинальный курсор в data-атрибут
                        if (!cursor.dataset.originalStyle) {
                            cursor.dataset.originalStyle = cursor.style.cssText;
                        }
                        // Применяем кастомный курсор
                        cursor.style.backgroundImage = `url(${e.target.result})`;
                        cursor.style.backgroundSize = 'contain';
                        cursor.style.backgroundRepeat = 'no-repeat';
                        cursor.style.backgroundPosition = 'center';
                        cursor.style.border = 'none';
                        cursor.style.width = '32px';
                        cursor.style.height = '32px';
                        cursor.style.borderRadius = '0';
                        
                        // Сохраняем в localStorage
                        localStorage.setItem('customCursor', e.target.result);
                        
                        // Показываем уведомление
                        showNotification('Кастомный курсор загружен!', 'success');
                    }
                };
                reader.readAsDataURL(file);
            }
        }

        function resetCustomCursor() {
            const cursor = document.getElementById('customCursor');
            if (cursor) {
                // Восстанавливаем оригинальный стиль
                if (cursor.dataset.originalStyle) {
                    cursor.style.cssText = cursor.dataset.originalStyle;
                } else {
                    // Сбрасываем к стандартному RGB курсору
                    cursor.style.backgroundImage = 'none';
                    cursor.style.backgroundSize = '';
                    cursor.style.backgroundRepeat = '';
                    cursor.style.backgroundPosition = '';
                    cursor.style.border = '2px solid white';
                    cursor.style.width = '20px';
                    cursor.style.height = '20px';
                    cursor.style.borderRadius = '50%';
                }
                cursor.removeAttribute('data-original-style');
                
                // Удаляем из localStorage
                localStorage.removeItem('customCursor');
                
                // Очищаем input
                document.getElementById('customCursorFile').value = '';
                
                // Показываем уведомление
                showNotification('Курсор сброшен на стандартный', 'info');
            }
        }

        function showNotification(message, type = 'info') {
            const notification = document.createElement('div');
            notification.className = `fixed top-20 right-4 z-[9999] bg-white/10 backdrop-blur-md border border-white/20 rounded-xl px-6 py-4 shadow-2xl transform transition-all duration-300`;
            notification.style.opacity = '0';
            notification.style.transform = 'translateX(400px)';
            
            const icons = {
                success: 'fa-check-circle text-green-400',
                error: 'fa-exclamation-circle text-red-400',
                info: 'fa-info-circle text-blue-400'
            };
            
            notification.innerHTML = `
                <div class="flex items-center gap-3">
                    <i class="fa-solid ${icons[type] || icons.info} text-xl"></i>
                    <div class="text-white font-semibold">${message}</div>
                </div>
            `;
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.style.opacity = '1';
                notification.style.transform = 'translateX(0)';
            }, 10);
            
            setTimeout(() => {
                notification.style.opacity = '0';
                notification.style.transform = 'translateX(400px)';
                setTimeout(() => {
                    if (document.body.contains(notification)) {
                        document.body.removeChild(notification);
                    }
                }, 300);
            }, 3000);
        }

        // Загружаем сохраненный кастомный курсор при загрузке страницы
        window.addEventListener('DOMContentLoaded', () => {
            const savedCursor = localStorage.getItem('customCursor');
            if (savedCursor) {
                const cursor = document.getElementById('customCursor');
                if (cursor) {
                    if (!cursor.dataset.originalStyle) {
                        cursor.dataset.originalStyle = cursor.style.cssText;
                    }
                    cursor.style.backgroundImage = `url(${savedCursor})`;
                    cursor.style.backgroundSize = 'contain';
                    cursor.style.backgroundRepeat = 'no-repeat';
                    cursor.style.backgroundPosition = 'center';
                    cursor.style.border = 'none';
                    cursor.style.width = '32px';
                    cursor.style.height = '32px';
                    cursor.style.borderRadius = '0';
                }
            }
        });

        function resetVisualSettings() {
            if (confirm('Сбросить все настройки визуализации?')) {
                location.reload();
            }
        }


        // ==========================================
        // ANIMATED NUMBER COUNTER
        // ==========================================
        function animateNumber(element, target, duration = 2000, suffix = '') {
            const start = 0;
            const increment = target / (duration / 16);
            let current = start;
            
            const timer = setInterval(() => {
                current += increment;
                if (current >= target) {
                    current = target;
                    clearInterval(timer);
                }
                element.textContent = Math.floor(current).toLocaleString('ru-RU') + suffix;
            }, 16);
        }

        // Observe dashboard section for number animation
        const dashboardObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateNumber(document.getElementById('statUsers'), 10000, 2000, '+');
                    animateNumber(document.getElementById('statRequests'), 5000000, 2500, '+');
                    animateNumber(document.getElementById('statProjects'), 3, 1000);
                    dashboardObserver.unobserve(entry.target);
                }
            });
        }, { threshold: 0.5 });

        const dashboardSection = document.getElementById('dashboard');
        if (dashboardSection) {
            dashboardObserver.observe(dashboardSection);
        }

        // ==========================================
        // INLINE DEMO FUNCTIONS
        // ==========================================
        function toggleApexDemo() {
            const demo = document.getElementById('apexDemo');
            demo.classList.toggle('show');
            playClickSound();
        }

        function runApexDemo() {
            const input = document.getElementById('apexDemoInput');
            const result = document.getElementById('apexDemoResult');
            const email = input.value.trim();
            
            if (!email || !email.includes('@')) {
                input.style.borderColor = '#ef4444';
                setTimeout(() => input.style.borderColor = '', 2000);
                return;
            }

            result.classList.remove('hidden');
            playClickSound();
        }

        function toggleBankDemo() {
            const demo = document.getElementById('bankDemo');
            demo.classList.toggle('show');
            playClickSound();
        }

        function animateBankBalance() {
            const balanceEl = document.getElementById('bankBalance');
            let balance = parseInt(balanceEl.textContent.replace(/\s/g, '').replace('₽', '')) || 0;
            const target = Math.floor(Math.random() * 50000) + 10000;
            const increment = (target - balance) / 30;
            
            const timer = setInterval(() => {
                balance += increment;
                if ((increment > 0 && balance >= target) || (increment < 0 && balance <= target)) {
                    balance = target;
                    clearInterval(timer);
                }
                balanceEl.textContent = Math.floor(balance).toLocaleString('ru-RU') + ' ₽';
            }, 50);
            
            playClickSound();
        }


        // ==========================================
        // LIVE DEMO FUNCTIONALITY
        // ==========================================
        function runDemo() {
            const demoInput = document.getElementById('demoInput');
            const demoButton = document.getElementById('demoButton');
            const demoLoading = document.getElementById('demoLoading');
            const demoResult = document.getElementById('demoResult');
            
            // Validate input
            const email = demoInput.value.trim();
            if (!email || !email.includes('@')) {
                demoInput.style.borderColor = '#ef4444';
                setTimeout(() => {
                    demoInput.style.borderColor = '';
                }, 2000);
                return;
            }

            // Disable button and show loading
            demoButton.disabled = true;
            demoResult.classList.remove('show');
            demoLoading.classList.add('show');
            demoButton.innerHTML = '<i class="fa-solid fa-spinner fa-spin mr-2"></i>Поиск...';

            // Simulate search delay
            setTimeout(() => {
                demoLoading.classList.remove('show');
                demoResult.classList.add('show');
                demoButton.disabled = false;
                demoButton.innerHTML = '<i class="fa-solid fa-search mr-2"></i>Найти';
                
                // Scroll to result
                demoResult.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
            }, 2500);
        }

        // Allow Enter key to trigger demo
        const demoInput = document.getElementById('demoInput');
        if (demoInput) {
            demoInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    runDemo();
                }
            });
        }

        // ==========================================
        // SUBSCRIBE MODAL FUNCTIONS
        // ==========================================
        function openSubscribeModal() {
            const modal = document.getElementById('subscribeModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.remove('opacity-0');
                modal.querySelector('div').classList.remove('scale-95');
                modal.querySelector('div').classList.add('scale-100');
            }, 10);
        }

        function closeSubscribeModal() {
            const modal = document.getElementById('subscribeModal');
            modal.classList.add('opacity-0');
            modal.querySelector('div').classList.add('scale-95');
            modal.querySelector('div').classList.remove('scale-100');
            setTimeout(() => modal.classList.add('hidden'), 300);
        }

        function submitSubscribe() {
            const emailInput = document.getElementById('subscribeEmail');
            const email = emailInput.value.trim();
            
            if (!email || !email.includes('@')) {
                emailInput.style.borderColor = '#ef4444';
                setTimeout(() => {
                    emailInput.style.borderColor = '';
                }, 2000);
                return;
            }

            // Simulate subscription
            const btn = document.querySelector('#subscribeModal button:last-child');
            const originalText = btn.innerHTML;
            btn.disabled = true;
            btn.innerHTML = '<i class="fa-solid fa-spinner fa-spin mr-2"></i>Подписка...';

            setTimeout(() => {
                btn.innerHTML = '<i class="fa-solid fa-check mr-2"></i>Подписка оформлена!';
                btn.classList.remove('neon-gradient-btn');
                btn.classList.add('bg-green-600');
                
                setTimeout(() => {
                    closeSubscribeModal();
                    emailInput.value = '';
                    btn.innerHTML = originalText;
                    btn.classList.remove('bg-green-600');
                    btn.classList.add('neon-gradient-btn');
                    btn.disabled = false;
                }, 2000);
            }, 1500);
        }

        // Close subscribe modal on outside click
        document.getElementById('subscribeModal').addEventListener('click', (e) => {
            if (e.target.id === 'subscribeModal') {
                closeSubscribeModal();
            }
        });

        // ==========================================
        // TAB NAVIGATION MANAGEMENT
        // ==========================================
        function setActiveTab(element, sectionId) {
            // Remove active class from all tabs
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Add active class to clicked tab
            element.classList.add('active');
            
            // Smooth scroll to section
            const target = document.getElementById(sectionId);
            if (target) {
                target.scrollIntoView({
                    behavior: 'smooth',
                    block: 'start'
                });
            }
            
            playClickSound();
        }

        // Update active tab on scroll
        window.addEventListener('scroll', () => {
            const sections = ['hero', 'search', 'projects', 'roadmap'];
            const scrollPos = window.scrollY + 200;
            
            sections.forEach(sectionId => {
                const section = document.getElementById(sectionId);
                if (section) {
                    const top = section.offsetTop;
                    const bottom = top + section.offsetHeight;
                    
                    if (scrollPos >= top && scrollPos < bottom) {
                        document.querySelectorAll('.nav-tab').forEach(tab => {
                            tab.classList.remove('active');
                            if (tab.getAttribute('href') === `#${sectionId}`) {
                                tab.classList.add('active');
                            }
                        });
                    }
                }
            });
        });

        // ==========================================
        // SEARCH DEMO CENTER LOGIC
        // ==========================================
        let selectedSearchSystem = null;

        function selectSearchSystem(system, button) {
            // Remove active class from all buttons
            document.querySelectorAll('.search-system-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // Add active class to clicked button
            button.classList.add('active');
            selectedSearchSystem = system;
            
            playClickSound();
        }

        function startSearch() {
            const targetInput = document.getElementById('searchTarget');
            const target = targetInput.value.trim();
            
            if (!target) {
                targetInput.style.borderColor = '#ef4444';
                setTimeout(() => {
                    targetInput.style.borderColor = '';
                }, 2000);
                return;
            }

            if (!selectedSearchSystem) {
                alert('Пожалуйста, выберите систему поиска');
                return;
            }

            // Hide all reports
            document.querySelectorAll('.demo-report').forEach(report => {
                report.classList.remove('show');
            });

            // Show loading
            const loading = document.getElementById('searchLoading');
            loading.classList.add('show');
            
            // Disable search button
            const searchBtn = document.getElementById('startSearchBtn');
            searchBtn.disabled = true;
            searchBtn.innerHTML = '<i class="fa-solid fa-spinner fa-spin mr-2"></i>Поиск...';

            playClickSound();

            // Simulate search delay (3-5 seconds)
            const delay = Math.random() * 2000 + 3000; // 3000-5000ms
            
            setTimeout(() => {
                // Hide loading
                loading.classList.remove('show');
                
                // Show appropriate report based on selected system
                let reportId = '';
                let targetId = '';
                
                switch(selectedSearchSystem) {
                    case 'sherlock':
                        reportId = 'sherlockReport';
                        targetId = 'sherlockTarget';
                        break;
                    case 'vektor':
                        reportId = 'vektorReport';
                        targetId = 'vektorTarget';
                        break;
                    case 'arictosearch':
                        reportId = 'arictosearchReport';
                        targetId = 'arictosearchTarget';
                        break;
                    case 'eityu':
                        reportId = 'eityuReport';
                        targetId = 'eityuTarget';
                        break;
                }

                // Update target in report
                const targetElement = document.getElementById(targetId);
                if (targetElement) {
                    targetElement.textContent = target;
                }

                // Show report
                const report = document.getElementById(reportId);
                if (report) {
                    report.classList.add('show');
                    report.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
                }

                // Re-enable search button
                searchBtn.disabled = false;
                searchBtn.innerHTML = '<i class="fa-solid fa-search mr-2"></i>Начать поиск';
            }, delay);
        }

        // Allow Enter key to start search
        const searchTargetInput = document.getElementById('searchTarget');
        if (searchTargetInput) {
            searchTargetInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    startSearch();
                }
            });
        }

        // ==========================================
        // SMOOTH SCROLL FOR ALL ANCHOR LINKS
        // ==========================================
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
</body>
</html>

