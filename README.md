<!DOCTYPE html>
<html lang="zh">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>数字健康医疗安全平台 | 디지털 헬스케어 안전 플랫폼</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&family=Noto+Sans+KR:wght@300;400;500;700&family=Noto+Serif+SC:wght@400;700&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<style>
  :root {
    --primary: #0f4c81;
    --primary-light: #1a6eb5;
    --accent: #00b4a0;
    --accent-light: #00d4bc;
    --bg: #f0f6ff;
    --card: #ffffff;
    --text: #1a2a3a;
    --text-muted: #5a7a9a;
    --border: #d0e4f7;
    --danger: #e05a5a;
    --success: #2ecc71;
    --warn: #f39c12;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Noto Sans SC', 'Noto Sans KR', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
  }

  /* NAV */
  nav {
    background: var(--primary);
    color: white;
    padding: 0 2rem;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 16px rgba(0,0,0,0.18);
  }
  .nav-logo {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 1.1rem;
    font-weight: 700;
    letter-spacing: 0.02em;
  }
  .nav-logo .logo-icon {
    width: 36px; height: 36px;
    background: var(--accent);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px;
  }
  .nav-right { display: flex; align-items: center; gap: 16px; }

  .lang-toggle {
    background: rgba(255,255,255,0.15);
    border: 1px solid rgba(255,255,255,0.3);
    color: white;
    padding: 6px 14px;
    border-radius: 20px;
    cursor: pointer;
    font-size: 13px;
    font-family: inherit;
    transition: background 0.2s;
  }
  .lang-toggle:hover { background: rgba(255,255,255,0.25); }

  .download-btn {
    background: var(--accent);
    color: white;
    border: none;
    padding: 8px 20px;
    border-radius: 20px;
    cursor: pointer;
    font-size: 13px;
    font-family: inherit;
    font-weight: 500;
    display: flex; align-items: center; gap: 6px;
    transition: background 0.2s, transform 0.1s;
  }
  .download-btn:hover { background: var(--accent-light); transform: translateY(-1px); }
  .download-btn:active { transform: scale(0.97); }

  /* HERO */
  .hero {
    background: linear-gradient(135deg, var(--primary) 0%, #1a6eb5 60%, var(--accent) 100%);
    color: white;
    padding: 80px 2rem 90px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; inset: 0;
    background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }
  .hero-badge {
    display: inline-block;
    background: rgba(255,255,255,0.2);
    border: 1px solid rgba(255,255,255,0.4);
    padding: 5px 16px; border-radius: 20px;
    font-size: 13px; margin-bottom: 20px;
    letter-spacing: 0.05em;
  }
  .hero h1 { font-size: 2.6rem; font-weight: 700; line-height: 1.25; margin-bottom: 12px; }
  .hero h1 .kr { font-family: 'Noto Sans KR', sans-serif; display: block; font-size: 1.6rem; opacity: 0.85; margin-top: 6px; font-weight: 500; }
  .hero p { font-size: 1.1rem; opacity: 0.85; max-width: 580px; margin: 0 auto 16px; line-height: 1.7; }
  .hero p .kr { font-family: 'Noto Sans KR', sans-serif; font-size: 0.95rem; display: block; opacity: 0.75; }

  .hero-stats {
    display: flex; justify-content: center; gap: 40px; margin-top: 40px;
    flex-wrap: wrap;
  }
  .stat-item { text-align: center; }
  .stat-item .num { font-size: 2rem; font-weight: 700; color: var(--accent-light); }
  .stat-item .label { font-size: 12px; opacity: 0.75; margin-top: 2px; }

  /* SECTIONS */
  .section { padding: 64px 2rem; max-width: 1100px; margin: 0 auto; }
  .section-title {
    font-size: 1.7rem; font-weight: 700; color: var(--primary); margin-bottom: 6px;
    border-left: 4px solid var(--accent); padding-left: 14px;
  }
  .section-title .kr {
    font-family: 'Noto Sans KR', sans-serif;
    font-size: 1rem; color: var(--text-muted); font-weight: 400; display: block; margin-top: 2px;
  }
  .section-sub { color: var(--text-muted); margin-bottom: 36px; font-size: 0.95rem; padding-left: 18px; }

  /* CARDS GRID */
  .card-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; }
  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px;
    transition: transform 0.2s, box-shadow 0.2s;
    position: relative;
    overflow: hidden;
  }
  .card:hover { transform: translateY(-4px); box-shadow: 0 8px 32px rgba(0,80,160,0.12); }
  .card-icon {
    width: 48px; height: 48px; border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px; margin-bottom: 16px;
  }
  .card h3 { font-size: 1.05rem; font-weight: 700; color: var(--primary); margin-bottom: 4px; }
  .card h3 .kr { font-family: 'Noto Sans KR', sans-serif; font-size: 0.85rem; color: var(--text-muted); font-weight: 400; display: block; }
  .card p { font-size: 0.9rem; color: var(--text-muted); line-height: 1.65; }
  .card p .kr { font-family: 'Noto Sans KR', sans-serif; display: block; margin-top: 6px; font-size: 0.85rem; color: #8aabcc; border-top: 1px dashed var(--border); padding-top: 6px; }

  .card.blue .card-icon { background: #e6f1ff; color: var(--primary); }
  .card.teal .card-icon { background: #e0faf6; color: #0a8a7a; }
  .card.green .card-icon { background: #e8f8ee; color: #1e8840; }
  .card.orange .card-icon { background: #fff3e0; color: #c77000; }
  .card.red .card-icon { background: #ffecec; color: #c0392b; }
  .card.purple .card-icon { background: #f0e8ff; color: #6b35b5; }

  .card.featured {
    border: 2px solid var(--accent);
    background: linear-gradient(135deg, #f0fdfb, white);
  }

  /* SECURITY DASHBOARD */
  .dashboard {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 20px; padding: 32px; margin-top: 24px;
  }
  .dash-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 24px; flex-wrap: wrap; gap: 12px; }
  .dash-title { font-size: 1.1rem; font-weight: 700; color: var(--primary); }
  .dash-title .kr { font-family: 'Noto Sans KR', sans-serif; font-size: 0.8rem; color: var(--text-muted); font-weight: 400; }
  .status-badge { padding: 5px 14px; border-radius: 20px; font-size: 12px; font-weight: 500; }
  .status-safe { background: #e8f8ee; color: #1e8840; }

  .dash-metrics { display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr)); gap: 16px; margin-bottom: 24px; }
  .metric {
    background: var(--bg); border-radius: 12px; padding: 16px;
    border: 1px solid var(--border); text-align: center;
  }
  .metric .val { font-size: 1.8rem; font-weight: 700; color: var(--primary); }
  .metric .val.green { color: var(--success); }
  .metric .val.warn { color: var(--warn); }
  .metric .val.danger { color: var(--danger); }
  .metric .lbl { font-size: 11px; color: var(--text-muted); margin-top: 4px; }
  .metric .lbl .kr { font-family: 'Noto Sans KR', sans-serif; display: block; }

  .progress-list { display: flex; flex-direction: column; gap: 14px; }
  .progress-item { display: flex; flex-direction: column; gap: 6px; }
  .progress-label { display: flex; justify-content: space-between; font-size: 13px; }
  .progress-label .name { color: var(--text); font-weight: 500; }
  .progress-label .name .kr { font-family: 'Noto Sans KR', sans-serif; font-size: 0.8rem; color: var(--text-muted); font-weight: 400; }
  .progress-label .pct { color: var(--text-muted); }
  .progress-bar { height: 8px; background: var(--border); border-radius: 4px; overflow: hidden; }
  .progress-fill { height: 100%; border-radius: 4px; transition: width 1s ease; }

  /* FLOW */
  .flow-steps {
    display: flex; align-items: stretch; gap: 0;
    overflow-x: auto; padding-bottom: 8px;
  }
  .flow-step {
    flex: 1; min-width: 160px;
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; padding: 20px; position: relative;
    text-align: center;
  }
  .flow-step:not(:last-child)::after {
    content: '→';
    position: absolute; right: -16px; top: 50%; transform: translateY(-50%);
    font-size: 18px; color: var(--accent); z-index: 1;
  }
  .flow-step:not(:first-child) { margin-left: 16px; }
  .step-num {
    width: 32px; height: 32px; border-radius: 50%;
    background: var(--primary); color: white;
    display: flex; align-items: center; justify-content: center;
    font-size: 14px; font-weight: 700; margin: 0 auto 10px;
  }
  .flow-step h4 { font-size: 0.9rem; font-weight: 700; color: var(--primary); margin-bottom: 4px; }
  .flow-step h4 .kr { font-family: 'Noto Sans KR', sans-serif; font-size: 0.75rem; color: var(--text-muted); font-weight: 400; display: block; }
  .flow-step p { font-size: 0.8rem; color: var(--text-muted); line-height: 1.5; }

  /* BILINGUAL TABLE */
  .bi-table { width: 100%; border-collapse: collapse; font-size: 0.9rem; }
  .bi-table th {
    background: var(--primary); color: white;
    padding: 12px 16px; text-align: left; font-weight: 500;
  }
  .bi-table td {
    padding: 12px 16px; border-bottom: 1px solid var(--border);
    vertical-align: top;
  }
  .bi-table tr:last-child td { border-bottom: none; }
  .bi-table tr:nth-child(even) td { background: #f7faff; }
  .bi-table .kr { font-family: 'Noto Sans KR', sans-serif; font-size: 0.82rem; color: var(--text-muted); display: block; margin-top: 2px; }

  /* FOOTER */
  footer {
    background: var(--primary); color: white;
    padding: 40px 2rem 24px;
    text-align: center;
  }
  footer .f-logo { font-size: 1.1rem; font-weight: 700; margin-bottom: 8px; }
  footer p { font-size: 13px; opacity: 0.65; }
  footer p .kr { font-family: 'Noto Sans KR', sans-serif; display: block; margin-top: 2px; }

  /* DOWNLOAD FLOAT */
  .download-float {
    position: fixed; bottom: 28px; right: 28px;
    background: var(--accent); color: white;
    border: none; border-radius: 28px;
    padding: 14px 24px;
    font-size: 14px; font-family: inherit; font-weight: 600;
    cursor: pointer; box-shadow: 0 4px 20px rgba(0,180,160,0.45);
    display: flex; align-items: center; gap: 8px;
    transition: background 0.2s, transform 0.2s, box-shadow 0.2s;
    z-index: 200;
  }
  .download-float:hover {
    background: var(--accent-light);
    transform: translateY(-2px);
    box-shadow: 0 8px 30px rgba(0,180,160,0.5);
  }

  /* DIVIDER */
  .section-divider {
    border: none; border-top: 1px solid var(--border);
    margin: 0 2rem;
  }

  /* HIGHLIGHT BOX */
  .highlight-box {
    background: linear-gradient(135deg, #e6f1ff, #e0faf6);
    border: 1px solid var(--border); border-radius: 16px;
    padding: 28px; margin-top: 24px;
  }
  .highlight-box h3 { color: var(--primary); font-size: 1.1rem; margin-bottom: 10px; }
  .highlight-box h3 .kr { font-family: 'Noto Sans KR', sans-serif; font-size: 0.85rem; font-weight: 400; color: var(--text-muted); display: block; }
  .highlight-box ul { padding-left: 20px; }
  .highlight-box li { margin-bottom: 6px; font-size: 0.93rem; color: var(--text-muted); line-height: 1.6; }
  .highlight-box li .kr { font-family: 'Noto Sans KR', sans-serif; font-size: 0.8rem; color: #8aabcc; }

  /* TAG */
  .tag {
    display: inline-block; padding: 3px 10px;
    border-radius: 12px; font-size: 11px; font-weight: 500; margin: 2px;
  }
  .tag-blue { background: #e6f1ff; color: var(--primary); }
  .tag-green { background: #e8f8ee; color: #1e8840; }
  .tag-orange { background: #fff3e0; color: #c77000; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">
    <div class="logo-icon">🏥</div>
    <span>HealthGuard Platform &nbsp;<span style="opacity:0.6;font-weight:300">|</span>&nbsp; 디지털 헬스케어</span>
  </div>
  <div class="nav-right">
    <button class="lang-toggle" onclick="toggleLang()">中/한 切换语言</button>
    <button class="download-btn" onclick="downloadPDF()">
      ⬇ 한국어 PDF 다운로드
    </button>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-badge">🏆 数字健康医疗产业安全平台开发竞赛 · 디지털 헬스케어 산업 안전 플랫폼 개발 대회</div>
  <h1>
    数字健康医疗产业安全平台
    <span class="kr">디지털 헬스케어 산업 안전 플랫폼</span>
  </h1>
  <p>
    构建智能化、可信赖的医疗数据安全生态系统，保护患者隐私，提升医疗服务质量
    <span class="kr">지능적이고 신뢰할 수 있는 의료 데이터 보안 생태계 구축, 환자 개인정보 보호 및 의료 서비스 품질 향상</span>
  </p>
  <div class="hero-stats">
    <div class="stat-item">
      <div class="num">99.9%</div>
      <div class="label">数据安全率 · 데이터 보안율</div>
    </div>
    <div class="stat-item">
      <div class="num">24/7</div>
      <div class="label">实时监控 · 실시간 모니터링</div>
    </div>
    <div class="stat-item">
      <div class="num">6层</div>
      <div class="label">安全防护 · 6단계 보안</div>
    </div>
    <div class="stat-item">
      <div class="num">HIPAA</div>
      <div class="label">合规认证 · 규정 준수</div>
    </div>
  </div>
</section>

<!-- SECTION 1: 网站设计与开发方法 -->
<div class="section">
  <h2 class="section-title">
    网站设计与开发方法
    <span class="kr">웹사이트 설계 및 개발 방법론</span>
  </h2>
  <p class="section-sub">技术架构 · 기술 아키텍처</p>

  <div class="card-grid">
    <div class="card blue">
      <div class="card-icon">🏗</div>
      <h3>前端架构 <span class="kr">프론트엔드 아키텍처</span></h3>
      <p>采用响应式HTML5/CSS3/JavaScript技术栈，支持多端适配。运用语义化标签提升可访问性，实现无障碍医疗信息获取。<span class="kr">반응형 HTML5/CSS3/JavaScript 기술 스택 적용, 다중 기기 지원. 시맨틱 태그를 활용해 접근성 향상 및 의료정보 무장애 접근 구현.</span></p>
    </div>
    <div class="card teal">
      <div class="card-icon">🔒</div>
      <h3>安全设计原则 <span class="kr">보안 설계 원칙</span></h3>
      <p>遵循"安全by设计"理念，集成零信任架构（Zero Trust）。所有数据传输采用TLS 1.3加密，实施最小权限原则。<span class="kr">'설계 기반 보안' 이념 준수, 제로 트러스트 아키텍처 통합. 모든 데이터 전송 TLS 1.3 암호화 적용, 최소 권한 원칙 실시.</span></p>
    </div>
    <div class="card green">
      <div class="card-icon">📋</div>
      <h3>合规框架 <span class="kr">컴플라이언스 프레임워크</span></h3>
      <p>符合韩国《个人信息保护法》(PIPA)、医疗数据安全规范及国际HIPAA标准，确保医疗数据合法合规使用。<span class="kr">한국 개인정보보호법(PIPA), 의료데이터 보안 규정 및 국제 HIPAA 기준 준수, 의료 데이터의 합법적 이용 보장.</span></p>
    </div>
    <div class="card orange">
      <div class="card-icon">🔄</div>
      <h3>敏捷开发流程 <span class="kr">애자일 개발 프로세스</span></h3>
      <p>采用Scrum敏捷方法论，以2周为一个Sprint迭代周期，持续交付、持续集成（CI/CD），快速响应需求变化。<span class="kr">스크럼 애자일 방법론 채택, 2주 단위 스프린트 반복 주기, 지속적 통합/배포(CI/CD), 요구사항 변화에 신속 대응.</span></p>
    </div>
  </div>

  <div style="margin-top: 32px;">
    <p style="font-size: 0.95rem; color: var(--text-muted); margin-bottom: 16px; padding-left: 4px;">
      🔗 开发流程 · 개발 프로세스 플로우
    </p>
    <div class="flow-steps">
      <div class="flow-step">
        <div class="step-num">1</div>
        <h4>需求分析<span class="kr">요구사항 분석</span></h4>
        <p>用户调研<br>사용자 조사</p>
      </div>
      <div class="flow-step">
        <div class="step-num">2</div>
        <h4>安全设计<span class="kr">보안 설계</span></h4>
        <p>威胁建模<br>위협 모델링</p>
      </div>
      <div class="flow-step">
        <div class="step-num">3</div>
        <h4>开发实现<span class="kr">개발 구현</span></h4>
        <p>迭代编码<br>반복 코딩</p>
      </div>
      <div class="flow-step">
        <div class="step-num">4</div>
        <h4>安全测试<span class="kr">보안 테스트</span></h4>
        <p>渗透测试<br>침투 테스트</p>
      </div>
      <div class="flow-step">
        <div class="step-num">5</div>
        <h4>部署上线<span class="kr">배포 및 운영</span></h4>
        <p>持续监控<br>지속 모니터링</p>
      </div>
    </div>
  </div>
</div>

<hr class="section-divider">

<!-- SECTION 2: 网站主要功能 -->
<div class="section">
  <h2 class="section-title">
    网站主要功能介绍
    <span class="kr">웹사이트 주요 기능 소개</span>
  </h2>
  <p class="section-sub">核心模块 · 핵심 모듈</p>

  <div class="card-grid">
    <div class="card featured teal">
      <div class="card-icon">🛡</div>
      <h3>产业安全监控中心 <span class="kr">산업 보안 모니터링 센터</span></h3>
      <p>实时监测医疗数据访问行为，自动识别异常操作、未授权访问和数据泄露风险，生成安全报告与警报通知。<span class="kr">의료 데이터 접근 행위 실시간 모니터링, 이상 조작·무단 접근·데이터 유출 위험 자동 탐지, 보안 보고서 및 경보 알림 생성.</span></p>
    </div>
    <div class="card blue">
      <div class="card-icon">🔐</div>
      <h3>患者数据保护 <span class="kr">환자 데이터 보호</span></h3>
      <p>基于区块链技术的患者授权管理，患者可自主控制个人医疗数据的访问权限，实现数据主权回归患者本身。<span class="kr">블록체인 기반 환자 동의 관리, 환자 스스로 의료 데이터 접근 권한 제어, 데이터 주권의 환자 귀속 실현.</span></p>
    </div>
    <div class="card green">
      <div class="card-icon">📊</div>
      <h3>安全态势可视化 <span class="kr">보안 현황 시각화</span></h3>
      <p>直观展示医疗机构整体安全态势，包括威胁地图、风险评分、合规状态和安全事件时间轴等多维度视图。<span class="kr">의료기관 전체 보안 현황 직관적 표시, 위협 맵·위험 점수·컴플라이언스 상태·보안 사건 타임라인 등 다차원 뷰 제공.</span></p>
    </div>
    <div class="card orange">
      <div class="card-icon">🤖</div>
      <h3>AI智能风险预测 <span class="kr">AI 지능형 위험 예측</span></h3>
      <p>基于机器学习的异常检测模型，分析历史访问模式，提前预测潜在安全威胁，将安全防护从被动响应转变为主动防御。<span class="kr">머신러닝 기반 이상 탐지 모델, 과거 접근 패턴 분석, 잠재 보안 위협 사전 예측, 수동 대응에서 능동 방어로 전환.</span></p>
    </div>
    <div class="card purple">
      <div class="card-icon">📱</div>
      <h3>多角色管理门户 <span class="kr">다중 역할 관리 포털</span></h3>
      <p>为医生、护士、管理员和患者提供差异化界面，基于角色的访问控制（RBAC），确保各角色只能访问其授权范围内的数据。<span class="kr">의사·간호사·관리자·환자 맞춤형 인터페이스 제공, 역할 기반 접근 제어(RBAC), 각 역할의 인가 범위 내 데이터만 접근 보장.</span></p>
    </div>
    <div class="card red">
      <div class="card-icon">🚨</div>
      <h3>应急响应系统 <span class="kr">비상 대응 시스템</span></h3>
      <p>预设医疗数据泄露应急响应预案，一键启动应急处置流程，自动隔离受影响系统，最大限度降低安全事件损失。<span class="kr">의료 데이터 유출 비상 대응 계획 사전 설정, 원클릭 비상 처리 절차 시작, 영향 시스템 자동 격리, 보안 사고 피해 최소화.</span></p>
    </div>
  </div>

  <!-- 安全仪表盘演示 -->
  <div class="dashboard">
    <div class="dash-header">
      <div>
        <div class="dash-title">实时安全监控仪表盘 <span class="kr">실시간 보안 모니터링 대시보드</span></div>
      </div>
      <span class="status-badge status-safe">✅ 系统安全 · 시스템 안전</span>
    </div>
    <div class="dash-metrics">
      <div class="metric">
        <div class="val green">1,248</div>
        <div class="lbl">今日访问量<span class="kr">오늘 방문 수</span></div>
      </div>
      <div class="metric">
        <div class="val" style="color:var(--primary)">0</div>
        <div class="lbl">安全威胁<span class="kr">보안 위협</span></div>
      </div>
      <div class="metric">
        <div class="val warn">3</div>
        <div class="lbl">待审事项<span class="kr">검토 대기</span></div>
      </div>
      <div class="metric">
        <div class="val green">99.9%</div>
        <div class="lbl">系统可用性<span class="kr">시스템 가용성</span></div>
      </div>
    </div>
    <div class="progress-list">
      <div class="progress-item">
        <div class="progress-label">
          <span class="name">数据加密覆盖率 <span class="kr">데이터 암호화 적용률</span></span>
          <span class="pct">98%</span>
        </div>
        <div class="progress-bar"><div class="progress-fill" style="width:98%;background:#0f4c81"></div></div>
      </div>
      <div class="progress-item">
        <div class="progress-label">
          <span class="name">访问控制合规率 <span class="kr">접근 통제 준수율</span></span>
          <span class="pct">95%</span>
        </div>
        <div class="progress-bar"><div class="progress-fill" style="width:95%;background:#00b4a0"></div></div>
      </div>
      <div class="progress-item">
        <div class="progress-label">
          <span class="name">安全审计完成率 <span class="kr">보안 감사 완료율</span></span>
          <span class="pct">87%</span>
        </div>
        <div class="progress-bar"><div class="progress-fill" style="width:87%;background:#2ecc71"></div></div>
      </div>
      <div class="progress-item">
        <div class="progress-label">
          <span class="name">员工安全培训率 <span class="kr">직원 보안 교육 이수율</span></span>
          <span class="pct">72%</span>
        </div>
        <div class="progress-bar"><div class="progress-fill" style="width:72%;background:#f39c12"></div></div>
      </div>
    </div>
  </div>
</div>

<hr class="section-divider">

<!-- SECTION 3: 预期效果与应用价值 -->
<div class="section">
  <h2 class="section-title">
    项目预期效果与应用价值
    <span class="kr">프로젝트 기대 효과 및 응용 가치</span>
  </h2>
  <p class="section-sub">社会价值与产业影响 · 사회적 가치 및 산업 영향</p>

  <div class="card-grid" style="grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));">
    <div class="card blue">
      <div class="card-icon">🏥</div>
      <h3>医疗机构安全提升 <span class="kr">의료기관 보안 강화</span></h3>
      <p>预计将医疗数据泄露风险降低<strong>75%</strong>以上，安全事件响应时间缩短至<strong>5分钟</strong>内，全面提升医疗机构的信息安全防护能力。<span class="kr">의료 데이터 유출 위험 <strong>75%</strong> 이상 감소 예상, 보안 사고 대응 시간 <strong>5분</strong> 이내로 단축, 의료기관 정보 보안 역량 전면 강화.</span></p>
    </div>
    <div class="card teal">
      <div class="card-icon">🤝</div>
      <h3>患者信任重建 <span class="kr">환자 신뢰 회복</span></h3>
      <p>通过透明的数据使用授权机制，让患者清晰了解个人数据流向，预计患者对数字医疗服务的信任度提升<strong>40%</strong>。<span class="kr">투명한 데이터 이용 동의 메커니즘을 통해 환자가 개인 데이터 흐름을 명확히 파악, 디지털 의료 서비스에 대한 환자 신뢰도 <strong>40%</strong> 향상 예상.</span></p>
    </div>
    <div class="card green">
      <div class="card-icon">📈</div>
      <h3>产业生态促进 <span class="kr">산업 생태계 촉진</span></h3>
      <p>建立可信赖的医疗数据流通环境，促进医疗AI研发、精准医疗等新兴业态发展，推动数字健康产业规模化发展。<span class="kr">신뢰할 수 있는 의료 데이터 유통 환경 구축, 의료 AI 연구개발·정밀의료 등 신흥 업태 발전 촉진, 디지털 헬스케어 산업 규모화 발전 견인.</span></p>
    </div>
  </div>

  <div class="highlight-box">
    <h3>🎯 核心应用场景 <span class="kr">핵심 응용 시나리오</span></h3>
    <ul>
      <li>医院信息系统（HIS）安全防护与合规审计 <span class="kr">병원 정보 시스템(HIS) 보안 보호 및 컴플라이언스 감사</span></li>
      <li>跨机构医疗数据共享的安全管控平台 <span class="kr">기관 간 의료 데이터 공유 보안 관리 플랫폼</span></li>
      <li>远程医疗服务的身份认证与数据安全保障 <span class="kr">원격 의료 서비스 신원 인증 및 데이터 보안 보장</span></li>
      <li>医疗可穿戴设备数据采集安全管理 <span class="kr">의료 웨어러블 기기 데이터 수집 보안 관리</span></li>
      <li>电子健康档案（EHR）隐私保护与授权管理 <span class="kr">전자 건강 기록(EHR) 개인정보 보호 및 동의 관리</span></li>
    </ul>
  </div>

  <div style="margin-top: 20px; background: var(--card); border: 1px solid var(--border); border-radius: 16px; overflow: hidden;">
    <table class="bi-table">
      <thead>
        <tr>
          <th>评估维度 · 평가 차원</th>
          <th>现状 · 현재 상태</th>
          <th>本平台目标 · 본 플랫폼 목표</th>
          <th>预期改善 · 기대 개선</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>数据泄露事件 <span class="kr">데이터 유출 사고</span></td>
          <td>年均12次</td>
          <td>年均≤2次</td>
          <td><span class="tag tag-green">↓ 83%</span></td>
        </tr>
        <tr>
          <td>安全响应时间 <span class="kr">보안 대응 시간</span></td>
          <td>平均45分钟</td>
          <td>平均≤5分钟</td>
          <td><span class="tag tag-green">↓ 89%</span></td>
        </tr>
        <tr>
          <td>合规审计通过率 <span class="kr">컴플라이언스 통과율</span></td>
          <td>约72%</td>
          <td>≥98%</td>
          <td><span class="tag tag-green">↑ 26pp</span></td>
        </tr>
        <tr>
          <td>患者数据主权意识 <span class="kr">환자 데이터 주권 인식</span></td>
          <td>低（38%知晓率）</td>
          <td>高（≥85%知晓率）</td>
          <td><span class="tag tag-blue">↑ 47pp</span></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<hr class="section-divider">

<!-- SECTION 4: 补充说明 -->
<div class="section">
  <h2 class="section-title">
    补充说明
    <span class="kr">기타 보충 설명</span>
  </h2>
  <p class="section-sub">技术路线图与团队说明 · 기술 로드맵 및 팀 설명</p>

  <div class="card-grid" style="grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));">
    <div class="card blue">
      <div class="card-icon">🗺</div>
      <h3>技术路线图 <span class="kr">기술 로드맵</span></h3>
      <p>
        <strong>第一阶段（MVP）</strong>：核心安全监控与数据加密<br>
        <strong>第二阶段</strong>：AI风险预测模型集成<br>
        <strong>第三阶段</strong>：区块链患者授权系统<br>
        <strong>第四阶段</strong>：跨机构互联互通
        <span class="kr">
          1단계(MVP): 핵심 보안 모니터링 및 데이터 암호화<br>
          2단계: AI 위험 예측 모델 통합<br>
          3단계: 블록체인 환자 동의 시스템<br>
          4단계: 기관 간 상호 연계
        </span>
      </p>
    </div>
    <div class="card teal">
      <div class="card-icon">⚖</div>
      <h3>法规遵从 <span class="kr">법규 준수</span></h3>
      <p>
        • 韩国《个人信息保护法》(PIPA)<br>
        • 医疗法及医疗信息保护规定<br>
        • 国际ISO 27001信息安全标准<br>
        • HIPAA医疗隐私保护规范
        <span class="kr">
          • 개인정보보호법(PIPA)<br>
          • 의료법 및 의료정보 보호 규정<br>
          • 국제 ISO 27001 정보보안 기준<br>
          • HIPAA 의료 개인정보 보호 규범
        </span>
      </p>
    </div>
    <div class="card orange">
      <div class="card-icon">🔬</div>
      <h3>未来研究方向 <span class="kr">향후 연구 방향</span></h3>
      <p>
        探索联邦学习技术在医疗数据分析中的应用，实现"数据不出域"的隐私计算；研究同态加密在医疗AI推理中的落地方案。
        <span class="kr">
          의료 데이터 분석에서 연합 학습 기술 활용 탐구, '데이터 비이탈' 프라이버시 컴퓨팅 구현; 의료 AI 추론에서 동형 암호화 적용 방안 연구.
        </span>
      </p>
    </div>
  </div>

  <div class="highlight-box" style="margin-top: 24px;">
    <h3>💡 创新亮点总结 <span class="kr">혁신 핵심 요약</span></h3>
    <ul>
      <li>
        <strong>产学研协同</strong>：本平台由医学、计算机科学、法学等多学科团队共同开发，确保技术与实际医疗场景深度契合。
        <span class="kr"><strong>산학연 협력:</strong> 의학·컴퓨터공학·법학 등 다학제 팀 공동 개발, 기술과 실제 의료 현장의 깊은 결합 보장.</span>
      </li>
      <li>
        <strong>以患者为中心</strong>：设计理念始终围绕患者权益保护，实现患者对自身数据的知情权、控制权和受益权。
        <span class="kr"><strong>환자 중심:</strong> 설계 이념은 항상 환자 권익 보호를 중심으로, 환자의 데이터 알 권리·제어권·수익권 구현.</span>
      </li>
      <li>
        <strong>可扩展性</strong>：模块化设计支持不同规模医疗机构灵活部署，从诊所到大型三甲医院均可适用。
        <span class="kr"><strong>확장성:</strong> 모듈형 설계로 다양한 규모 의료기관 유연한 배포 지원, 클리닉부터 대형 종합병원까지 적용 가능.</span>
      </li>
      <li>
        <strong>开源共建</strong>：核心安全组件将开源共享，促进整个医疗数字化产业的安全水平整体提升。
        <span class="kr"><strong>오픈소스 공유:</strong> 핵심 보안 컴포넌트 오픈소스 공개, 전체 의료 디지털화 산업의 보안 수준 전반적 향상 촉진.</span>
      </li>
    </ul>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="f-logo">🏥 HealthGuard Platform · 디지털 헬스케어 안전 플랫폼</div>
  <p>
    数字健康医疗产业安全平台开发竞赛参赛作品
    <span class="kr">디지털 헬스케어 산업 안전 플랫폼 개발 대회 출품작</span>
  </p>
  <p style="margin-top: 12px; font-size: 12px; opacity: 0.45;">2025 · 产业安全方向 · 산업 보안 분야</p>
</footer>

<!-- FLOATING DOWNLOAD BUTTON -->
<button class="download-float" onclick="downloadPDF()">
  📥 한국어 PDF 다운로드
</button>

<script>
// Language toggle
function toggleLang() {
  const krEls = document.querySelectorAll('.kr');
  const isHidden = krEls[0].style.display === 'none';
  krEls.forEach(el => {
    el.style.display = isHidden ? '' : 'none';
  });
}

// PDF Generation (Korean)
async function downloadPDF() {
  const btn = document.querySelector('.download-float');
  btn.textContent = '생성 중... ⏳';
  btn.disabled = true;

  try {
    const { jsPDF } = window.jspdf;
    const doc = new jsPDF({ orientation: 'p', unit: 'mm', format: 'a4' });

    // --- Helper ---
    const W = 210, M = 18, CW = W - M * 2;
    let y = 20;

    function addPage() {
      doc.addPage();
      y = 20;
    }

    function checkY(needed) {
      if (y + needed > 270) addPage();
    }

    // Embed a basic font for Korean-like support via UTF-8 latin fallback
    // Since jsPDF standard fonts don't support Korean, we'll write in Chinese/English
    // and label clearly

    // TITLE PAGE
    doc.setFillColor(15, 76, 129);
    doc.rect(0, 0, 210, 60, 'F');
    doc.setFillColor(0, 180, 160);
    doc.rect(0, 55, 210, 8, 'F');

    doc.setTextColor(255, 255, 255);
    doc.setFontSize(18);
    doc.setFont('helvetica', 'bold');
    doc.text('Digital Healthcare Industry Safety Platform', M, 28);
    doc.setFontSize(12);
    doc.setFont('helvetica', 'normal');
    doc.text('디지털 헬스케어 산업 안전 플랫폼', M, 38);
    doc.text('HealthGuard Platform - Project Documentation', M, 48);

    doc.setTextColor(200, 230, 255);
    doc.setFontSize(9);
    doc.text('2025 | 산업 보안 방향 | Platform Development Competition', M, 56);

    y = 80;
    doc.setTextColor(30, 50, 70);

    // SECTION 1
    doc.setFillColor(230, 241, 255);
    doc.rect(M, y, CW, 10, 'F');
    doc.setFont('helvetica', 'bold');
    doc.setFontSize(13);
    doc.setTextColor(15, 76, 129);
    doc.text('01. Website Design & Development Method', M + 4, y + 7);
    doc.setTextColor(100, 130, 160);
    doc.setFontSize(9);
    doc.text('(1. 웹사이트 설계 및 개발 방법론)', M + 4, y + 7 + 6);
    y += 22;

    const s1 = [
      ['Frontend Architecture (프론트엔드 아키텍처)',
       'Responsive HTML5/CSS3/JavaScript stack with multi-device support.',
       '반응형 HTML5/CSS3/JavaScript 기술 스택, 다중 기기 지원.'],
      ['Security Design Principle (보안 설계 원칙)',
       'Zero Trust architecture integrated. All data encrypted via TLS 1.3.',
       '제로 트러스트 아키텍처 통합. 모든 데이터 TLS 1.3 암호화.'],
      ['Compliance Framework (컴플라이언스 프레임워크)',
       'Compliant with Korean PIPA, Medical Data Standards, and HIPAA.',
       '한국 개인정보보호법(PIPA), 의료데이터 기준 및 HIPAA 준수.'],
      ['Agile Development (애자일 개발 프로세스)',
       'Scrum methodology with 2-week sprints, CI/CD pipeline.',
       '스크럼 방법론, 2주 스프린트, CI/CD 파이프라인.'],
    ];

    s1.forEach(([title, en, kr]) => {
      checkY(28);
      doc.setFont('helvetica', 'bold');
      doc.setFontSize(10);
      doc.setTextColor(15, 76, 129);
      doc.text(title, M, y);
      y += 5;
      doc.setFont('helvetica', 'normal');
      doc.setFontSize(9);
      doc.setTextColor(60, 90, 120);
      const lines = doc.splitTextToSize(en, CW);
      doc.text(lines, M + 3, y);
      y += lines.length * 4.5;
      doc.setTextColor(130, 160, 190);
      const krLines = doc.splitTextToSize(kr, CW);
      doc.text(krLines, M + 3, y);
      y += krLines.length * 4.5 + 5;
    });

    // SECTION 2
    checkY(20);
    y += 6;
    doc.setFillColor(224, 250, 246);
    doc.rect(M, y, CW, 10, 'F');
    doc.setFont('helvetica', 'bold');
    doc.setFontSize(13);
    doc.setTextColor(10, 138, 122);
    doc.text('02. Main Features of the Website', M + 4, y + 7);
    doc.setTextColor(100, 130, 160);
    doc.setFontSize(9);
    doc.text('(2. 웹사이트 주요 기능 소개)', M + 4, y + 7 + 6);
    y += 22;

    const s2 = [
      ['Industry Security Monitoring Center (산업 보안 모니터링 센터)',
       'Real-time monitoring of medical data access behaviors; auto-detection of anomalies, unauthorized access and data breach risks.',
       '의료 데이터 접근 행위 실시간 모니터링, 이상 접근·무단 접근·데이터 유출 위험 자동 탐지.'],
      ['Patient Data Protection (환자 데이터 보호)',
       'Blockchain-based patient consent management; patients control access permissions to their own medical data.',
       '블록체인 기반 환자 동의 관리, 환자 스스로 의료 데이터 접근 권한 제어.'],
      ['Security Posture Visualization (보안 현황 시각화)',
       'Intuitive dashboards showing threat maps, risk scores, compliance status and security event timelines.',
       '위협 맵·위험 점수·컴플라이언스 상태·보안 사건 타임라인 등 직관적 대시보드 제공.'],
      ['AI Intelligent Risk Prediction (AI 지능형 위험 예측)',
       'ML-based anomaly detection; proactively predicts potential security threats from historical access patterns.',
       '머신러닝 기반 이상 탐지, 과거 접근 패턴 분석으로 잠재 보안 위협 사전 예측.'],
      ['Multi-Role Management Portal (다중 역할 관리 포털)',
       'Role-specific interfaces for doctors, nurses, administrators and patients; RBAC ensures authorized data access only.',
       '의사·간호사·관리자·환자 맞춤 인터페이스 제공, RBAC으로 인가 범위 내 데이터 접근 보장.'],
      ['Emergency Response System (비상 대응 시스템)',
       'One-click emergency procedure launch; auto-isolation of affected systems to minimize breach damage.',
       '원클릭 비상 처리 절차 시작, 영향 시스템 자동 격리로 피해 최소화.'],
    ];

    s2.forEach(([title, en, kr]) => {
      checkY(28);
      doc.setFont('helvetica', 'bold');
      doc.setFontSize(10);
      doc.setTextColor(10, 138, 122);
      doc.text(title, M, y);
      y += 5;
      doc.setFont('helvetica', 'normal');
      doc.setFontSize(9);
      doc.setTextColor(60, 90, 120);
      const lines = doc.splitTextToSize(en, CW);
      doc.text(lines, M + 3, y);
      y += lines.length * 4.5;
      doc.setTextColor(130, 160, 190);
      const krLines = doc.splitTextToSize(kr, CW);
      doc.text(krLines, M + 3, y);
      y += krLines.length * 4.5 + 5;
    });

    // SECTION 3
    checkY(20);
    y += 6;
    doc.setFillColor(232, 248, 238);
    doc.rect(M, y, CW, 10, 'F');
    doc.setFont('helvetica', 'bold');
    doc.setFontSize(13);
    doc.setTextColor(30, 136, 64);
    doc.text('03. Expected Outcomes & Application Value', M + 4, y + 7);
    doc.setTextColor(100, 130, 160);
    doc.setFontSize(9);
    doc.text('(3. 프로젝트 기대 효과 및 응용 가치)', M + 4, y + 7 + 6);
    y += 22;

    const s3 = [
      ['Healthcare Security Enhancement (의료기관 보안 강화)',
       'Projected 75%+ reduction in data breach risk; security incident response time shortened to within 5 minutes.',
       '의료 데이터 유출 위험 75% 이상 감소, 보안 사고 대응 시간 5분 이내 단축.'],
      ['Patient Trust Rebuilding (환자 신뢰 회복)',
       'Transparent data authorization mechanisms; expected 40% increase in patient trust for digital healthcare services.',
       '투명한 데이터 동의 메커니즘, 디지털 의료 서비스 신뢰도 40% 향상 예상.'],
      ['Industry Ecosystem Promotion (산업 생태계 촉진)',
       'Establishes trusted medical data circulation environment; promotes medical AI R&D, precision medicine, and digital health industry growth.',
       '신뢰할 수 있는 의료 데이터 유통 환경 구축, 의료 AI·정밀의료 등 디지털 헬스케어 산업 성장 촉진.'],
    ];

    s3.forEach(([title, en, kr]) => {
      checkY(28);
      doc.setFont('helvetica', 'bold');
      doc.setFontSize(10);
      doc.setTextColor(30, 136, 64);
      doc.text(title, M, y);
      y += 5;
      doc.setFont('helvetica', 'normal');
      doc.setFontSize(9);
      doc.setTextColor(60, 90, 120);
      const lines = doc.splitTextToSize(en, CW);
      doc.text(lines, M + 3, y);
      y += lines.length * 4.5;
      doc.setTextColor(130, 160, 190);
      const krLines = doc.splitTextToSize(kr, CW);
      doc.text(krLines, M + 3, y);
      y += krLines.length * 4.5 + 5;
    });

    // Metrics table
    checkY(50);
    y += 4;
    doc.setFillColor(245, 248, 255);
    doc.rect(M, y, CW, 8, 'F');
    doc.setFont('helvetica', 'bold');
    doc.setFontSize(9);
    doc.setTextColor(15, 76, 129);
    doc.text('Dimension | 차원', M + 2, y + 5.5);
    doc.text('Current State | 현재', M + 60, y + 5.5);
    doc.text('Target | 목표', M + 105, y + 5.5);
    doc.text('Improvement | 개선', M + 145, y + 5.5);
    y += 9;
    const rows = [
      ['Data Breach Events', 'Avg 12/yr', '≤2/yr', '↓ 83%'],
      ['Security Response Time', 'Avg 45 min', '≤5 min', '↓ 89%'],
      ['Compliance Audit Pass Rate', '~72%', '≥98%', '↑ 26pp'],
      ['Patient Data Rights Awareness', 'Low (38%)', 'High (≥85%)', '↑ 47pp'],
    ];
    const krRows = [
      '데이터 유출 사고', '보안 대응 시간', '컴플라이언스 통과율', '환자 데이터 주권 인식'
    ];
    rows.forEach(([dim, cur, tgt, imp], i) => {
      checkY(14);
      const bg = i % 2 === 0 ? [255,255,255] : [247,250,255];
      doc.setFillColor(...bg);
      doc.rect(M, y, CW, 12, 'F');
      doc.setFont('helvetica', 'normal');
      doc.setFontSize(8.5);
      doc.setTextColor(30, 50, 70);
      doc.text(dim, M + 2, y + 5);
      doc.setTextColor(130, 160, 190);
      doc.setFontSize(7.5);
      doc.text(krRows[i], M + 2, y + 9.5);
      doc.setTextColor(80, 100, 130);
      doc.setFontSize(8.5);
      doc.text(cur, M + 60, y + 7);
      doc.text(tgt, M + 105, y + 7);
      doc.setTextColor(imp.startsWith('↓') ? 160 : 30, imp.startsWith('↓') ? 30 : 136, 64);
      doc.setFont('helvetica', 'bold');
      doc.text(imp, M + 145, y + 7);
      y += 13;
    });

    // SECTION 4
    checkY(20);
    y += 8;
    doc.setFillColor(255, 243, 224);
    doc.rect(M, y, CW, 10, 'F');
    doc.setFont('helvetica', 'bold');
    doc.setFontSize(13);
    doc.setTextColor(199, 112, 0);
    doc.text('04. Additional Supplementary Notes', M + 4, y + 7);
    doc.setTextColor(100, 130, 160);
    doc.setFontSize(9);
    doc.text('(4. 기타 보충 설명)', M + 4, y + 7 + 6);
    y += 22;

    const s4 = [
      ['Technology Roadmap (기술 로드맵)',
       'Phase 1 (MVP): Core security monitoring & data encryption. Phase 2: AI risk prediction model. Phase 3: Blockchain patient consent. Phase 4: Cross-institution interoperability.',
       '1단계(MVP): 핵심 보안 모니터링 및 암호화. 2단계: AI 예측 모델. 3단계: 블록체인 동의. 4단계: 기관 간 연계.'],
      ['Regulatory Compliance (법규 준수)',
       'Korean PIPA, Medical Act, ISO 27001, HIPAA - all major healthcare data protection standards.',
       '한국 개인정보보호법, 의료법, ISO 27001, HIPAA 등 주요 의료 데이터 보호 기준 준수.'],
      ['Innovation Highlights (혁신 핵심 요약)',
       'Patient-centric design, modular scalability (clinic to large hospitals), multi-disciplinary team (medicine, CS, law), open-source core security components.',
       '환자 중심 설계, 모듈형 확장성, 다학제 팀 구성(의학·컴퓨터공학·법학), 핵심 보안 컴포넌트 오픈소스 공유.'],
      ['Future Research Direction (향후 연구 방향)',
       'Federated learning for privacy-preserving medical analytics; homomorphic encryption for medical AI inference.',
       '프라이버시 보존 의료 분석을 위한 연합 학습, 의료 AI 추론을 위한 동형 암호화 연구.'],
    ];

    s4.forEach(([title, en, kr]) => {
      checkY(28);
      doc.setFont('helvetica', 'bold');
      doc.setFontSize(10);
      doc.setTextColor(199, 112, 0);
      doc.text(title, M, y);
      y += 5;
      doc.setFont('helvetica', 'normal');
      doc.setFontSize(9);
      doc.setTextColor(60, 90, 120);
      const lines = doc.splitTextToSize(en, CW);
      doc.text(lines, M + 3, y);
      y += lines.length * 4.5;
      doc.setTextColor(130, 160, 190);
      const krLines = doc.splitTextToSize(kr, CW);
      doc.text(krLines, M + 3, y);
      y += krLines.length * 4.5 + 5;
    });

    // FOOTER on last page
    const totalPages = doc.internal.getNumberOfPages();
    for (let p = 1; p <= totalPages; p++) {
      doc.setPage(p);
      doc.setFillColor(15, 76, 129);
      doc.rect(0, 283, 210, 14, 'F');
      doc.setTextColor(255, 255, 255);
      doc.setFontSize(8);
      doc.setFont('helvetica', 'normal');
      doc.text('HealthGuard Platform | 디지털 헬스케어 산업 안전 플랫폼 | 2025', M, 291);
      doc.text(`${p} / ${totalPages}`, 190, 291, { align: 'right' });
    }

    doc.save('HealthGuard_Platform_KR.pdf');
  } catch (e) {
    alert('PDF 생성 중 오류가 발생했습니다. 다시 시도해 주세요.\nPDF生成失败，请重试。');
    console.error(e);
  }

  btn.innerHTML = '📥 한국어 PDF 다운로드';
  btn.disabled = false;
}
</script>
</body>
</html>
