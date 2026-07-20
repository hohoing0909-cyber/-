# -<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>모바일 신분증</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Apple SD Gothic Neo", "Noto Sans KR", sans-serif;
            user-select: none;
        }

        body {
            background-color: #f4f6f9;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .mobile-container {
            width: 100%;
            max-width: 400px;
            height: 100vh;
            max-height: 850px;
            background: #ffffff;
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
            display: flex;
            flex-direction: column;
            position: relative;
            overflow: hidden;
            border-radius: 20px;
        }

        /* Top Bar */
        .app-header {
            background-color: #0b2545;
            color: #ffffff;
            padding: 45px 20px 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .app-header .title {
            font-size: 16px;
            font-weight: 600;
            letter-spacing: -0.5px;
        }

        /* Card Section */
        .card-body {
            flex: 1;
            padding: 20px;
            display: flex;
            flex-direction: column;
            gap: 15px;
            overflow-y: auto;
        }

        .id-badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-size: 18px;
            font-weight: 700;
            color: #111;
            margin-bottom: 5px;
        }

        .id-badge-icon {
            width: 24px;
            height: 24px;
            background: #0052cc;
            border-radius: 50%;
            display: inline-block;
        }

        /* Profile & QR Layout */
        .profile-section {
            display: flex;
            gap: 15px;
            background: #f8fafc;
            padding: 15px;
            border-radius: 12px;
            border: 1px solid #e2e8f0;
        }

        .profile-img {
            width: 110px;
            height: 140px;
            object-fit: cover;
            border-radius: 8px;
            border: 1px solid #cbd5e1;
            background-color: #e2e8f0;
        }

        .qr-box {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background: #ffffff;
            padding: 10px;
            border-radius: 8px;
            border: 1px solid #e2e8f0;
        }

        .qr-placeholder {
            width: 90px;
            height: 90px;
            background: url('https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=PROD_ID_VERIFY') center/cover;
        }

        .qr-timer {
            font-size: 11px;
            color: #64748b;
            margin-top: 6px;
            font-weight: 500;
        }

        /* User Details */
        .info-group {
            background: #ffffff;
            padding: 15px;
            border-radius: 12px;
            border: 1px solid #f1f5f9;
        }

        .user-name {
            font-size: 22px;
            font-weight: 700;
            color: #0f172a;
            margin-bottom: 12px;
        }

        .info-label {
            font-size: 12px;
            color: #64748b;
            margin-bottom: 4px;
            font-weight: 600;
        }

        .info-value {
            font-size: 14px;
            color: #1e293b;
            line-height: 1.4;
            font-weight: 500;
            margin-bottom: 12px;
        }

        /* Dynamic Animation (Anti-spoofing effect) */
        .watermark-banner {
            background: linear-gradient(90deg, #e0e7ff, #f3e8ff, #e0e7ff);
            background-size: 200% 200%;
            animation: gradientShift 3s ease infinite;
            padding: 10px;
            border-radius: 8px;
            text-align: center;
            font-size: 12px;
            color: #4338ca;
            font-weight: 600;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Bottom Status */
        .footer-stamp {
            text-align: center;
            padding: 15px;
            font-size: 12px;
            color: #94a3b8;
            border-top: 1px solid #f1f5f9;
        }
    </style>
</head>
<body>

<div class="mobile-container">
    <!-- 앱 상단 헤더 -->
    <div class="app-header">
        <span class="title">대한민국 정부 모바일 신분증</span>
        <span style="font-size: 20px;">≡</span>
    </div>

    <!-- 신분증 본문 영역 -->
    <div class="card-body">
        <div class="id-badge">
            <span class="id-badge-icon"></span>
            모바일 주민등록증
        </div>

        <!-- 사진 및 동적 QR 코드 영역 -->
        <div class="profile-section">
            <!-- 소품에 사용할 프로필 이미지 경로 -->
            <img src="profile.jpg" alt="증명사진" class="profile-img" id="profileImage">
            
            <div class="qr-box">
                <div class="qr-placeholder"></div>
                <div class="qr-timer">남은시간 <span id="timer">30</span>초</div>
            </div>
        </div>

        <!-- 위변조 방지 캡션 효과 -->
        <div class="watermark-banner">
            ● 진위확인용 캡쳐방지 모션 작동 중
        </div>

        <!-- 개인정보 영역 -->
        <div class="info-group">
            <div class="user-name">김 민 준</div>
            
            <div class="info-label">주소</div>
            <div class="info-value">경상남도 창원시 마산합포구 현동1길 8<br>308동 2001호</div>

            <div class="info-label">발급일자</div>
            <div class="info-value">2024. 03. 15</div>

            <div class="info-label">발급기관</div>
            <div class="info-value">행정안전부</div>
        </div>
    </div>

    <div class="footer-stamp">
        대한민국 정부 OFFICIAL ID SYSTEM
    </div>
</div>

<script>
    // QR 타이머 동적 카운트다운 효과 (촬영 시 리얼리티 제공)
    let timeLeft = 30;
    const timerElement = document.getElementById('timer');

    setInterval(() => {
        timeLeft--;
        if (timeLeft < 0) {
            timeLeft = 30;
        }
        timerElement.textContent = timeLeft;
    }, 1000);
</script>

</body>
</html>
