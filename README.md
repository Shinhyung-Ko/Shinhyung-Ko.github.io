<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1.0" />
  <title>KAC공항서비스 윤리경영 로드맵 · 인쇄 고급 버전(텍스트 선명도 개선)</title>

  <!-- Tailwind -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Noto Sans KR -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;700&display=swap" rel="stylesheet">

  <!-- Animate.css (fadeInUp 등에 사용) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css" crossorigin="anonymous" referrerpolicy="no-referrer"/>

  <style>
    :root { color-scheme: light; --animate-duration: 1.1s; }
    html, body { height: 100%; }
    body {
      font-family: 'Noto Sans KR', sans-serif !important;
      background: radial-gradient(1200px 600px at 10% 0%, #eef2ff 0%, #f8fafc 40%, #ffffff 100%);
      word-break: keep-all; overflow-wrap: break-word; line-break: strict; hyphens: manual;
    }
    code, kbd, pre, samp { font-family: inherit !important; }

    /* 인쇄 최적화 + 배경 유지 */
    @page { size: A4; margin: 14mm 14mm 16mm 14mm; }
    * { -webkit-print-color-adjust: exact !important; print-color-adjust: exact !important; }

    /* 카드/리본 */
    .glass { background: linear-gradient(180deg, rgba(255,255,255,0.85), rgba(248,250,252,0.9)); backdrop-filter: blur(6px); }
    .soft-card, .soft-card-dark {
      position: relative; overflow: hidden; /* pseudo-layer용 */
      transition: transform .28s ease, box-shadow .28s ease;
    }
    /* 실제 시각 스타일 */
    .soft-card {
      background: linear-gradient(135deg, #ffffff 0%, #f1f5ff 100%);
      box-shadow: 0 10px 30px rgba(30,64,175,0.08), inset 0 0 0 1px rgba(37,99,235,0.08);
    }
    .soft-card-dark {
      background: linear-gradient(135deg, #f8fafc 0%, #eef2ff 100%);
      box-shadow: 0 10px 30px rgba(2,6,23,0.06), inset 0 0 0 1px rgba(15,23,42,0.06);
    }
    /* 컨텐츠는 위 레이어로 */
    .soft-card > * , .soft-card-dark > * { position: relative; z-index: 1; }

    /* hover 시 살짝 띄우는 기본 효과(텍스트 블러 없음) */
    .soft-card:hover { transform: translateY(-2px); box-shadow: 0 14px 34px rgba(37,99,235,.16), inset 0 0 0 1px rgba(37,99,235,.10); }
    .soft-card-dark:hover { transform: translateY(-2px); box-shadow: 0 14px 34px rgba(2,6,23,.12), inset 0 0 0 1px rgba(15,23,42,0.12); }

    /* 상단 큰 박스: hover/애니메이션 없음 */
    .soft-card-static {
      background: linear-gradient(135deg, #ffffff 0%, #f1f5ff 100%);
      box-shadow: 0 10px 30px rgba(30,64,175,0.08), inset 0 0 0 1px rgba(37,99,235,0.08);
    }

    .ribbon {
      position: relative; display: inline-block; padding: 4px 10px; border-radius: 9999px; color: #fff;
      background: linear-gradient(90deg,#1e3a8a,#2563eb,#60a5fa); font-weight: 600; font-size: 0.875rem; box-shadow: 0 6px 16px rgba(37,99,235,0.35);
    }
    .ribbon::after { content: ""; position: absolute; inset: -2px; border-radius: 9999px;
      background: linear-gradient(90deg,rgba(96,165,250,.35),rgba(37,99,235,.35),rgba(30,58,138,.35));
      filter: blur(12px); z-index: -1; }
    .divider { height: 3px; background: linear-gradient(90deg, transparent, rgba(37,99,235,.35), transparent); }

    /* 타임라인 */
    .timeline { position: relative; padding-left: 22px; }
    .timeline::before {
      content: ""; position: absolute; left: 6px; top: -8px; bottom: -8px; width: 4px; border-radius: 2px;
      background: linear-gradient(180deg,#c7d2fe 0%,#2563eb 50%,#93c5fd 100%); box-shadow: inset 0 0 0 1px rgba(37,99,235,.22);
    }
    .dot {
      position: relative; margin-left: -2px; width: 16px; height: 16px; border-radius: 9999px;
      background: radial-gradient(circle at 30% 30%, #fff, #60a5fa 40%, #2563eb 80%); box-shadow: 0 0 0 4px rgba(59,130,246,.18), 0 6px 14px rgba(37,99,235,.25);
    }

    /* 단계 제목 효과 (텍스트 스케일 금지: 글로우만) */
    .stage-title {
      position: relative;
      transition: transform .25s ease, text-shadow .25s ease, letter-spacing .25s ease;
      letter-spacing: .1px; will-change: text-shadow, letter-spacing;
    }
    .stage-title::after {
      content: ""; position: absolute; left: 0; bottom: -6px; width: 100%; height: 2px;
      background: linear-gradient(90deg, rgba(30,58,138,.0), rgba(37,99,235,.55), rgba(30,58,138,.0));
      transform: scaleX(.25); transform-origin: left; transition: transform .35s ease; border-radius: 2px;
    }
    .stage-title:hover { letter-spacing: .2px; text-shadow: 0 3px 14px rgba(37,99,235,.22); }
    .stage-title:hover::after { transform: scaleX(1); }

    /* 텍스트-safe pulse: pseudo-layer만 살짝 scale */
    .pulse-host::after {
      content: ""; position: absolute; inset: 0; border-radius: inherit; pointer-events: none; z-index: 0;
      /* 투명 레이어에 그림자/윤곽만 */
      box-shadow: 0 0 0 0 rgba(37,99,235,0.0), inset 0 0 0 1px rgba(37,99,235,0.08);
      background: transparent;
      transform: scale(1);
    }
    @keyframes pulseSoftLayer {
      0%   { transform: scale(1); box-shadow: 0 10px 30px rgba(37,99,235,.08), inset 0 0 0 1px rgba(37,99,235,.08); }
      50%  { transform: scale(1.028); box-shadow: 0 18px 44px rgba(37,99,235,.18), inset 0 0 0 1px rgba(37,99,235,.10); }
      100% { transform: scale(1); box-shadow: 0 10px 30px rgba(37,99,235,.08), inset 0 0 0 1px rgba(37,99,235,.08); }
    }
    .pulse-host.is-pulsing::after { animation: pulseSoftLayer .85s ease-out both; }

    /* 대제목: 텍스트 글로우만 살짝 */
    @keyframes titleGlow {
      0% { text-shadow: 0 0 0 rgba(37,99,235,0); letter-spacing: .1px; }
      50% { text-shadow: 0 4px 18px rgba(37,99,235,.28); letter-spacing: .22px; }
      100% { text-shadow: 0 0 0 rgba(37,99,235,0); letter-spacing: .1px; }
    }
    .title-glow { animation: titleGlow .7s ease-out both; }

    /* 인쇄 */
    @media print {
      .screen-only { display: none !important; }
      .soft-card, .soft-card-dark, .soft-card-static { box-shadow: none !important; border: 1px solid #e5e7eb; }
      .page-break { break-after: page; }
      .avoid-break-inside { break-inside: avoid; }
      .stage-title::after { display: none; }
    }
  </style>
</head>

<body class="text-gray-800">

  <!-- 상단 고급 헤더(화면용) -->
  <div class="screen-only sticky top-0 z-30 glass border-b border-blue-100">
    <div class="max-w-6xl mx-auto px-4 py-3 flex items-center justify-between">
      <div class="flex items-center gap-3">
        <span class="inline-block w-8 h-8 rounded-xl" style="background: conic-gradient(from 0deg,#93c5fd,#2563eb,#1e3a8a,#93c5fd); box-shadow: 0 4px 12px rgba(37,99,235,.35);"></span>
        <h1 class="text-lg font-semibold text-blue-900">KAC공항서비스 윤리경영 로드맵 · 인쇄 고급 버전</h1>
      </div>
      <button onclick="window.print()" class="px-4 py-2 rounded-lg bg-blue-600 text-white font-medium hover:bg-blue-700 transition">PDF 저장</button>
    </div>
  </div>

  <!-- 커버/인트로 (큰 박스는 hover 없음) -->
  <section class="max-w-6xl mx-auto px-4 md:px-8 mt-8 md:mt-12">
    <div class="soft-card-static rounded-3xl p-8 md:p-12 relative overflow-hidden">
      <span class="inline-block px-4 py-1.5 rounded-full bg-blue-50 text-blue-700 text-base md:text-lg font-medium">지속 가능한 미래를 위한 투명한 약속</span>

      <!-- 메인 타이틀: 세련된 fade-in -->
      <h2 class="text-3xl md:text-5xl font-extrabold tracking-tight mt-4 text-blue-900 animate__animated animate__fadeInUp"
          style="--animate-duration:1.2s; --animate-delay:.08s;">
        KAC공항서비스 윤리경영 로드맵
      </h2>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-8">
        <div class="soft-card-dark pulse-host rounded-2xl p-6">
          <h3 class="text-blue-800 font-semibold text-lg mb-2">미션</h3>
          <p class="text-gray-700">우리는 효과적인 공항시설관리와 최고의 운영서비스로 고객만족과 공항안전을 실현한다.</p>
        </div>
        <div class="soft-card-dark pulse-host rounded-2xl p-6">
          <h3 class="text-blue-800 font-semibold text-lg mb-2">비전</h3>
          <p class="text-gray-700">우리는 투명성·공정성을 바탕으로 지속 가능한 공항 서비스를 제공한다.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- 전체 단계: 1 → 2 → 3 -->
  <main class="max-w-6xl mx-auto px-4 md:px-8 mt-10 space-y-16 timeline">

    <!-- 1단계 -->
    <section class="avoid-break-inside relative">
      <div class="flex items-center gap-3 mb-2">
        <span class="dot"></span>
        <span class="ribbon text-sm">1단계</span>
        <h3 class="stage-title text-2xl md:text-3xl font-bold text-gray-900">윤리경영 기반 구축 (2024 ~ 2026)</h3>
      </div>
      <p class="stage-subtitle text-gray-600 mb-5 before:content-['▸'] before:mr-1 before:text-blue-600">
        윤리경영 시스템 정립과 실천 환경 조성
      </p>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
            </svg>
            윤리헌장 실천체계 구축
          </h4>
          <p class="text-sm text-gray-700">핵심 가치(투명성, 국민 서비스 등) 기반 세부 행동 강령 및 지침 제정</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
            </svg>
            부패 방지 시스템 자체 구축
          </h4>
          <p class="text-sm text-gray-700">ISO 37001 원칙을 반영한 KAC공항서비스 맞춤형 부패 방지 시스템 및 매뉴얼 제정</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
            </svg>
            리스크 평가 및 통제
          </h4>
          <p class="text-sm text-gray-700">부패 취약 분야(계약, 인사 등) 리스크 평가 및 관리 체계 도입</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
            </svg>
            윤리적 리더십 강화
          </h4>
          <p class="text-sm text-gray-700">경영진의 윤리 서약과 솔선수범을 통한 윤리경영 의지 표명</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
            </svg>
            내부 윤리 교육 의무화
          </h4>
          <p class="text-sm text-gray-700">전 임직원 대상 정기 교육 및 신규/승진자 심화 교육 실시</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
            </svg>
            자체 윤리 평가 시스템 구축
          </h4>
          <p class="text-sm text-gray-700">내부 설문조사를 통한 윤리 의식 수준 측정 및 개선 방향 모색</p>
        </article>
      </div>
    </section>

    <div class="divider"></div>
    <div class="page-break"></div>

    <!-- 2단계 -->
    <section class="avoid-break-inside relative">
      <div class="flex items-center gap-3 mb-2">
        <span class="dot"></span>
        <span class="ribbon text-sm">2단계</span>
        <h3 class="stage-title text-2xl md:text-3xl font-bold text-gray-900">윤리경영 내재화 및 확산 (2027 ~ 2029)</h3>
      </div>
      <p class="stage-subtitle text-gray-600 mb-5 before:content-['▸'] before:mr-1 before:text-blue-600">
        구축된 시스템의 안정적 운영과 윤리 문화의 조직 내 확산
      </p>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.606 2.296.122 2.572-1.065z"/>
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
            부패 방지 시스템 운영 활성화
          </h4>
          <p class="text-sm text-gray-700">지속적 운영 및 주기적 내부 감사를 통한 실효성 점검</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.606 2.296.122 2.572-1.065z"/>
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
            자율적 윤리 실천 프로그램
          </h4>
          <p class="text-sm text-gray-700">청렴 실천 우수 부서 선정 등 임직원 참여형 프로그램 운영</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.606 2.296.122 2.572-1.065z"/>
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
            국민 중심 서비스 강화
          </h4>
          <p class="text-sm text-gray-700">윤리헌장 기반 국민 최우선 서비스 매뉴얼 적용 및 우수 사례 발굴</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.606 2.296.122 2.572-1.065z"/>
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
            협력사 윤리경영 지원
          </h4>
          <p class="text-sm text-gray-700">협력사 대상 청렴 서약 및 윤리 교육 지원을 통한 상생의 윤리 생태계 구축</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.606 2.296.122 2.572-1.065z"/>
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
            내부 신고 시스템 개선
          </h4>
          <p class="text-sm text-gray-700">익명성 보장 강화 및 처리 절차와 결과의 투명한 공개</p>
        </article>
      </div>
    </section>

    <div class="divider"></div>
    <div class="page-break"></div>

    <!-- 3단계 -->
    <section class="avoid-break-inside relative">
      <div class="flex items-center gap-3 mb-2">
        <span class="dot"></span>
        <span class="ribbon text-sm">3단계</span>
        <h3 class="stage-title text-2xl md:text-3xl font-bold text-gray-900">윤리경영 고도화 및 선도 (2030 ~ 2032)</h3>
      </div>
      <p class="stage-subtitle text-gray-600 mb-5 before:content-['▸'] before:mr-1 before:text-blue-600">
        윤리경영의 ESG 확장과 공공기관 윤리경영 선도
      </p>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
        <!-- 별 아이콘: 선형 -->
        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2 shrink-0 align-middle" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 3l2.6 5.27 5.8.42-4.4 3.83 1.32 5.69L12 15.9 6.68 18.21 8 12.52 3.6 8.69l5.8-.42L12 3z"/>
            </svg>
            ESG 기반 윤리경영 시스템 내재화
          </h4>
          <p class="text-sm text-gray-700">지속가능성을 위한 윤리적 가치와 시스템의 전사적 통합</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2 shrink-0 align-middle" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 3l2.6 5.27 5.8.42-4.4 3.83 1.32 5.69L12 15.9 6.68 18.21 8 12.52 3.6 8.69l5.8-.42L12 3z"/>
            </svg>
            사회적 책임 및 동반 성장 강화
          </h4>
          <p class="text-sm text-gray-700">협력사 윤리 가이드라인 제공, 지역사회 연계 사회공헌 활동 확대</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2 shrink-0 align-middle" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 3l2.6 5.27 5.8.42-4.4 3.83 1.32 5.69L12 15.9 6.68 18.21 8 12.52 3.6 8.69l5.8-.42L12 3z"/>
            </svg>
            투명성 및 신뢰성 제고
          </h4>
          <p class="text-sm text-gray-700">공공데이터 개방 확대 등 경영 관련 주요 정보의 투명한 공개</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2 shrink-0 align-middle" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 3l2.6 5.27 5.8.42-4.4 3.83 1.32 5.69L12 15.9 6.68 18.21 8 12.52 3.6 8.69l5.8-.42L12 3z"/>
            </svg>
            윤리경영 성과 공유
          </h4>
          <p class="text-sm text-gray-700">자체 시스템 운영 노하우 대외 공유 및 타 기관과 교류</p>
        </article>

        <article class="soft-card pulse-host rounded-2xl p-5">
          <h4 class="flex items-center font-semibold text-gray-900 mb-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-blue-600 mr-2 shrink-0 align-middle" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 3l2.6 5.27 5.8.42-4.4 3.83 1.32 5.69L12 15.9 6.68 18.21 8 12.52 3.6 8.69l5.8-.42L12 3z"/>
            </svg>
            지속적 시스템 개선
          </h4>
          <p class="text-sm text-gray-700">환경 변화에 맞춘 시스템 업데이트 및 내부 윤리 전문가 양성</p>
        </article>
      </div>
    </section>

  </main>

  <!-- 하단 워터마크 -->
  <footer class="max-w-6xl mx-auto px-4 md:px-8 mt-12 mb-10">
    <div class="soft-card-dark rounded-2xl p-4 text-center text-sm text-gray-600">
      KAC공항서비스 · 윤리경영 로드맵   </div>
  </footer>

  <!-- 스크립트: pseudo-layer 기반 pulse, 대제목 글로우, 소제목 동시 효과 -->
  <script>
    (function () {
      if (window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches) return;

      // 카드류(및 미션/비전 박스) hover 시 pseudo-layer만 애니메이션 → 텍스트 선명
      const pulseHosts = document.querySelectorAll('.pulse-host');
      pulseHosts.forEach((el) => {
        el.addEventListener('mouseenter', () => {
          if (el.classList.contains('is-pulsing')) return;
          el.classList.add('is-pulsing');
          // pseudo-element는 animationend 이벤트가 안 터지니 타임아웃으로 정리
          setTimeout(() => el.classList.remove('is-pulsing'), 900); // 0.85s + 여유
        });
      });

      // 단계 제목 hover: 텍스트 글로우 + 소제목 fadeInUp
      const stageTitles = document.querySelectorAll('.stage-title');
      stageTitles.forEach((titleEl) => {
        const section = titleEl.closest('section');
        const subtitle = section ? section.querySelector('.stage-subtitle') : null;

        titleEl.addEventListener('mouseenter', () => {
          // 제목 글로우
          titleEl.classList.add('title-glow');
          setTimeout(() => titleEl.classList.remove('title-glow'), 750);

          // 소제목 빠른 fadeInUp
          if (subtitle && !subtitle.classList.contains('animate__animated')) {
            subtitle.style.setProperty('--animate-duration', '0.7s');
            subtitle.style.setProperty('--animate-delay', '.02s');
            subtitle.classList.add('animate__animated', 'animate__fadeInUp');
            subtitle.addEventListener('animationend', () => {
              subtitle.classList.remove('animate__animated', 'animate__fadeInUp');
              subtitle.style.removeProperty('--animate-duration');
              subtitle.style.removeProperty('--animate-delay');
            }, { once: true });
          }
        });
      });
    })();
  </script>
</body>
</html>
