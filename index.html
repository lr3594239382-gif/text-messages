<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>ChargeLens · 充电数据面板</title>
<style>
/* ========== 全局 ========== */
* { margin:0; padding:0; box-sizing:border-box; -webkit-tap-highlight-color:transparent; }

:root {
  --glass-bg: rgba(255,255,255,0.07);
  --glass-border: rgba(255,255,255,0.16);
  --glass-highlight: rgba(255,255,255,0.28);
  --accent-1: #6ee7ff;
  --accent-2: #a78bfa;
  --accent-3: #f0abfc;
  --text-primary: rgba(255,255,255,0.95);
  --text-secondary: rgba(255,255,255,0.55);
  --text-dim: rgba(255,255,255,0.3);
}

html, body { height:100%; overflow:hidden; }

body {
  font-family: -apple-system, 'SF Pro Display', 'HarmonyOS Sans', 'MiSans', 'PingFang SC', 'Segoe UI', sans-serif;
  background: #06080f;
  color: var(--text-primary);
  display:flex; align-items:center; justify-content:center;
  position:relative;
}

/* ========== 背景层：流动极光 ========== */
.bg-aurora {
  position:fixed; inset:0; z-index:0;
  background:
    radial-gradient(ellipse 80% 60% at 20% 10%, rgba(110,231,255,0.18), transparent 60%),
    radial-gradient(ellipse 60% 80% at 80% 20%, rgba(167,139,250,0.15), transparent 55%),
    radial-gradient(ellipse 70% 50% at 50% 90%, rgba(240,171,252,0.12), transparent 60%),
    radial-gradient(ellipse 50% 40% at 10% 70%, rgba(96,165,250,0.1), transparent 50%);
  animation: auroraShift 20s ease-in-out infinite alternate;
}
@keyframes auroraShift {
  0%   { transform: scale(1) rotate(0deg); opacity:1; }
  50%  { transform: scale(1.15) rotate(3deg); opacity:0.85; }
  100% { transform: scale(1.05) rotate(-2deg); opacity:1; }
}

/* 背景光斑呼吸 */
.bg-blob {
  position:fixed; border-radius:50%; filter:blur(80px); opacity:0.35; z-index:0;
  animation: blobFloat 14s ease-in-out infinite alternate;
}
.bg-blob.b1 { width:280px; height:280px; background:var(--accent-1); top:-80px; left:-60px; }
.bg-blob.b2 { width:220px; height:220px; background:var(--accent-2); bottom:-60px; right:-40px; animation-delay:-5s; }
.bg-blob.b3 { width:180px; height:180px; background:var(--accent-3); top:50%; left:60%; animation-delay:-9s; }
@keyframes blobFloat {
  0%   { transform: translate(0,0) scale(1); }
  100% { transform: translate(30px,-30px) scale(1.2); }
}

/* ========== 粒子画布 ========== */
#particleCanvas {
  position:fixed; inset:0; z-index:1; pointer-events:none;
}

/* ========== 主容器 ========== */
.app-container {
  position:relative; z-index:2;
  width:100%; max-width:420px;
  padding: 0 16px;
  display:flex; flex-direction:column;
  gap:14px;
  max-height:100vh;
  overflow-y:auto;
  scrollbar-width:none;
  -webkit-overflow-scrolling: touch;
}
.app-container::-webkit-scrollbar { display:none; }

/* ========== 液态玻璃卡片 ========== */
.glass-card {
  position:relative;
  background: var(--glass-bg);
  backdrop-filter: blur(24px) saturate(1.5) brightness(1.08);
  -webkit-backdrop-filter: blur(24px) saturate(1.5) brightness(1.08);
  border-radius: 22px;
  border: 1px solid var(--glass-border);
  box-shadow:
    inset 0 1px 0 var(--glass-highlight),
    inset 0 -1px 0 rgba(255,255,255,0.05),
    0 8px 32px rgba(0,0,0,0.4),
    0 2px 8px rgba(0,0,0,0.2);
  padding: 20px 18px;
  overflow:hidden;
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1);
}

/* 液态玻璃高光边缘（模拟折射） */
.glass-card::before {
  content:'';
  position:absolute; inset:0;
  border-radius:inherit;
  background: linear-gradient(135deg, rgba(255,255,255,0.12) 0%, transparent 40%, transparent 60%, rgba(255,255,255,0.06) 100%);
  pointer-events:none;
  z-index:0;
}

/* 液态玻璃顶部高光线 */
.glass-card::after {
  content:'';
  position:absolute; top:0; left:10%; right:10%; height:1px;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.5), transparent);
  pointer-events:none;
}

/* 内部光效层（跟随手指/鼠标） */
.glass-card .light-follow {
  position:absolute; width:200px; height:200px;
  border-radius:50%; pointer-events:none;
  background: radial-gradient(circle, rgba(255,255,255,0.12), transparent 70%);
  transform: translate(-50%,-50%);
  opacity:0; transition: opacity 0.3s;
  z-index:1;
}
.glass-card:active .light-follow,
.glass-card:hover .light-follow { opacity:1; }

/* ========== 顶部状态栏 ========== */
.top-bar {
  display:flex; align-items:center; justify-content:space-between;
  padding: 8px 4px 0;
}
.top-bar .app-name {
  font-size:15px; font-weight:600; letter-spacing:0.5px;
  background: linear-gradient(135deg, var(--accent-1), var(--accent-2));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
}
.top-bar .status-dot {
  width:8px; height:8px; border-radius:50%;
  background: var(--accent-1);
  box-shadow: 0 0 8px var(--accent-1);
  animation: pulseDot 2s ease-in-out infinite;
}
@keyframes pulseDot {
  0%,100% { opacity:1; transform:scale(1); }
  50% { opacity:0.5; transform:scale(0.8); }
}

/* ========== 电量主卡 ========== */
.battery-main {
  text-align:center;
  padding: 28px 18px 24px;
}
.battery-main .device-name {
  font-size:16px; font-weight:600; margin-bottom:4px;
  letter-spacing:0.3px;
}
.battery-main .device-sub {
  font-size:11px; color:var(--text-dim); margin-bottom:18px;
  letter-spacing:0.5px;
}

/* 环形进度 */
.ring-wrap {
  position:relative;
  width:160px; height:160px;
  margin: 0 auto 16px;
}
.ring-wrap svg { transform: rotate(-90deg); width:100%; height:100%; }
.ring-wrap .ring-bg { fill:none; stroke:rgba(255,255,255,0.06); stroke-width:8; }
.ring-wrap .ring-fill {
  fill:none; stroke:url(#ringGrad); stroke-width:8;
  stroke-linecap:round;
  transition: stroke-dashoffset 0.8s cubic-bezier(0.34,1.56,0.64,1);
  filter: drop-shadow(0 0 6px rgba(110,231,255,0.5));
}

/* 中心数字 */
.ring-center {
  position:absolute; inset:0;
  display:flex; flex-direction:column; align-items:center; justify-content:center;
}
.ring-center .level-num {
  font-size:38px; font-weight:700; line-height:1;
  font-variant-numeric: tabular-nums;
  letter-spacing:-1px;
  background: linear-gradient(135deg, #fff, var(--accent-1));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
}
.ring-center .level-decimal {
  font-size:13px; font-weight:500; color:var(--text-secondary);
  font-variant-numeric: tabular-nums;
  margin-top:2px;
}
.ring-center .level-label {
  font-size:10px; color:var(--text-dim); margin-top:4px;
  letter-spacing:1px; text-transform:uppercase;
}

/* 充电状态徽章 */
.charge-badge {
  display:inline-flex; align-items:center; gap:6px;
  padding: 6px 14px; border-radius:20px;
  font-size:12px; font-weight:500;
  background: rgba(110,231,255,0.1);
  border: 1px solid rgba(110,231,255,0.2);
  color: var(--accent-1);
  margin-bottom:4px;
}
.charge-badge.charging {
  animation: badgeGlow 2s ease-in-out infinite;
}
@keyframes badgeGlow {
  0%,100% { box-shadow: 0 0 0 rgba(110,231,255,0); }
  50% { box-shadow: 0 0 16px rgba(110,231,255,0.25); }
}
.charge-badge .bolt {
  width:12px; height:12px; display:inline-block;
}

/* ========== 数据网格 ========== */
.data-grid {
  display:grid; grid-template-columns: 1fr 1fr;
  gap:10px;
}
.data-item {
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius:16px;
  padding: 16px 14px;
  position:relative; overflow:hidden;
  transition: background 0.3s, transform 0.2s;
}
.data-item:active { transform: scale(0.97); }
.data-item .data-label {
  font-size:10px; color:var(--text-dim); letter-spacing:0.8px;
  text-transform:uppercase; margin-bottom:8px;
  display:flex; align-items:center; gap:5px;
}
.data-item .data-value {
  font-size:20px; font-weight:600;
  font-variant-numeric: tabular-nums;
  line-height:1.1;
}
.data-item .data-unit {
  font-size:11px; font-weight:400; color:var(--text-secondary);
  margin-left:2px;
}
.data-item .data-sub {
  font-size:10px; color:var(--text-dim); margin-top:4px;
}

/* 图标 */
.data-icon {
  width:14px; height:14px; opacity:0.6;
}

/* ========== 实时功率模拟条 ========== */
.power-bar-wrap {
  grid-column: 1 / -1;
  padding: 16px 14px;
}
.power-bar-track {
  height:6px; border-radius:3px;
  background: rgba(255,255,255,0.06);
  overflow:hidden; margin-top:10px;
  position:relative;
}
.power-bar-fill {
  height:100%; border-radius:3px;
  background: linear-gradient(90deg, var(--accent-1), var(--accent-2), var(--accent-3));
  background-size: 200% 100%;
  animation: powerFlow 2s linear infinite;
  transition: width 0.5s ease;
  box-shadow: 0 0 10px rgba(110,231,255,0.4);
}
@keyframes powerFlow {
  0% { background-position: 0% 50%; }
  100% { background-position: 200% 50%; }
}

/* ========== 底部按钮 ========== */
.btn-row {
  display:flex; gap:10px;
}
.glass-btn {
  flex:1;
  padding: 14px;
  border-radius:16px;
  border: 1px solid var(--glass-border);
  background: var(--glass-bg);
  backdrop-filter: blur(16px) saturate(1.4);
  -webkit-backdrop-filter: blur(16px) saturate(1.4);
  color: var(--text-primary);
  font-size:13px; font-weight:500;
  cursor:pointer;
  position:relative; overflow:hidden;
  transition: all 0.25s cubic-bezier(0.34,1.56,0.64,1);
  box-shadow: inset 0 1px 0 rgba(255,255,255,0.15), 0 4px 16px rgba(0,0,0,0.2);
  font-family:inherit;
}
.glass-btn:active {
  transform: scale(0.96);
  background: rgba(255,255,255,0.12);
}
.glass-btn .btn-shine {
  position:absolute; inset:0;
  background: linear-gradient(105deg, transparent 40%, rgba(255,255,255,0.15) 50%, transparent 60%);
  transform: translateX(-100%);
  transition: transform 0.6s;
}
.glass-btn:active .btn-shine { transform: translateX(100%); }

/* ========== 不支持提示 ========== */
.unsupported-overlay {
  position:fixed; inset:0; z-index:100;
  background: rgba(6,8,15,0.92);
  backdrop-filter: blur(20px);
  display:none;
  align-items:center; justify-content:center;
  padding:24px;
  text-align:center;
}
.unsupported-overlay.show { display:flex; }
.unsupported-overlay .msg {
  max-width:320px;
  font-size:14px; line-height:1.7; color:var(--text-secondary);
}
.unsupported-overlay .msg strong {
  color: var(--accent-1); display:block; margin-bottom:8px; font-size:16px;
}

/* ========== 进场动画 ========== */
.fade-up {
  opacity:0; transform: translateY(24px);
  animation: fadeUp 0.7s cubic-bezier(0.22,1,0.36,1) forwards;
}
.fade-up:nth-child(1) { animation-delay:0.05s; }
.fade-up:nth-child(2) { animation-delay:0.12s; }
.fade-up:nth-child(3) { animation-delay:0.19s; }
.fade-up:nth-child(4) { animation-delay:0.26s; }
.fade-up:nth-child(5) { animation-delay:0.33s; }
@keyframes fadeUp {
  to { opacity:1; transform: translateY(0); }
}

/* ========== 响应式 ========== */
@media (max-width:380px) {
  .ring-wrap { width:130px; height:130px; }
  .ring-center .level-num { font-size:30px; }
  .data-item .data-value { font-size:17px; }
  .app-container { padding: 0 12px; gap:10px; }
}

/* 降级：不支持 backdrop-filter */
@supports not (backdrop-filter: blur(1px)) {
  .glass-card, .glass-btn {
    background: rgba(20,24,40,0.85);
  }
}
</style>
</head>
<body>

<!-- 背景层 -->
<div class="bg-aurora"></div>
<div class="bg-blob b1"></div>
<div class="bg-blob b2"></div>
<div class="bg-blob b3"></div>

<!-- 粒子画布 -->
<canvas id="particleCanvas"></canvas>

<!-- 主容器 -->
<div class="app-container">

  <!-- 顶栏 -->
  <div class="top-bar fade-up">
    <span class="app-name">ChargeLens</span>
    <span class="status-dot" id="statusDot"></span>
  </div>

  <!-- 电量主卡 -->
  <div class="glass-card battery-main fade-up">
    <div class="light-follow"></div>
    <div class="device-name" id="deviceName">正在识别设备…</div>
    <div class="device-sub" id="deviceSub">—</div>

    <div class="ring-wrap">
      <svg viewBox="0 0 160 160">
        <defs>
          <linearGradient id="ringGrad" x1="0%" y1="0%" x2="100%" y2="100%">
            <stop offset="0%" stop-color="#6ee7ff"/>
            <stop offset="50%" stop-color="#a78bfa"/>
            <stop offset="100%" stop-color="#f0abfc"/>
          </linearGradient>
        </defs>
        <circle class="ring-bg" cx="80" cy="80" r="66"/>
        <circle class="ring-fill" id="ringFill" cx="80" cy="80" r="66"
                stroke-dasharray="414.69" stroke-dashoffset="414.69"/>
      </svg>
      <div class="ring-center">
        <div class="level-num" id="levelInt">--</div>
        <div class="level-decimal" id="levelDec">.0000%</div>
        <div class="level-label">Battery</div>
      </div>
    </div>

    <div class="charge-badge" id="chargeBadge">
      <span class="bolt">⚡</span>
      <span id="chargeText">检测中…</span>
    </div>
  </div>

  <!-- 数据网格 -->
  <div class="data-grid fade-up">

    <div class="data-item">
      <div class="data-label">
        <svg class="data-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <rect x="3" y="4" width="18" height="16" rx="2"/><circle cx="12" cy="12" r="3"/>
        </svg>
        充电状态
      </div>
      <div class="data-value" id="chargingState">—</div>
      <div class="data-sub" id="chargingSub">—</div>
    </div>

    <div class="data-item">
      <div class="data-label">
        <svg class="data-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 3"/>
        </svg>
        剩余时间
      </div>
      <div class="data-value" id="timeRemaining">—</div>
      <div class="data-sub" id="timeSub">—</div>
    </div>

    <div class="data-item">
      <div class="data-label">
        <svg class="data-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/>
        </svg>
        设备内存
      </div>
      <div class="data-value" id="deviceMemory">—</div>
      <div class="data-sub" id="memorySub">估算值</div>
    </div>

    <div class="data-item">
      <div class="data-label">
        <svg class="data-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M4 20h16M4 16h16M4 12h16M4 8h16M4 4h16"/>
        </svg>
        逻辑核心
      </div>
      <div class="data-value" id="cpuCores">—</div>
      <div class="data-sub" id="cpuSub">—</div>
    </div>

    <!-- 功率模拟条（说明性） -->
    <div class="data-item power-bar-wrap">
      <div class="data-label">
        <svg class="data-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/>
        </svg>
        充电功率（模拟指示）
      </div>
      <div class="data-value" id="powerEstimate">— <span class="data-unit">W</span></div>
      <div class="data-sub">浏览器无法读取真实功率，此为基于充电状态的视觉反馈</div>
      <div class="power-bar-track">
        <div class="power-bar-fill" id="powerBar" style="width:0%"></div>
      </div>
    </div>

  </div>

  <!-- 底部按钮 -->
  <div class="btn-row fade-up">
    <button class="glass-btn" id="refreshBtn">
      <span class="btn-shine"></span>
      🔄 刷新数据
    </button>
    <button class="glass-btn" id="vibrateBtn">
      <span class="btn-shine"></span>
      📳 触感反馈
    </button>
  </div>

</div>

<!-- 不支持提示 -->
<div class="unsupported-overlay" id="unsupportedOverlay">
  <div class="msg">
    <strong>⚠️ 你的浏览器不支持 Battery API</strong>
    请使用 Chrome、Edge 等 Chromium 内核浏览器，并确保通过 HTTPS 访问。
    部分功能将无法使用。
  </div>
</div>

<script>
/* ================================================================
   1. 粒子系统（融合鸿蒙灵动粒子 + OPPO 水滴吸收动效）
   ================================================================ */
(function initParticles() {
  const canvas = document.getElementById('particleCanvas');
  const ctx = canvas.getContext('2d');
  let W, H;
  let particles = [];
  let mouse = { x: -999, y: -999 };
  let isCharging = false;
  let chargeProgress = 0;

  function resize() {
    W = canvas.width = window.innerWidth * devicePixelRatio;
    H = canvas.height = window.innerHeight * devicePixelRatio;
    canvas.style.width = window.innerWidth + 'px';
    canvas.style.height = window.innerHeight + 'px';
    ctx.scale(devicePixelRatio, devicePixelRatio);
    W = window.innerWidth;
    H = window.innerHeight;
  }
  resize();
  window.addEventListener('resize', resize);

  // 粒子类
  class Particle {
    constructor(x, y, opts = {}) {
      this.x = x;
      this.y = y;
      this.vx = (Math.random() - 0.5) * (opts.speed || 1.2);
      this.vy = (Math.random() - 0.5) * (opts.speed || 1.2);
      this.size = opts.size || (Math.random() * 2.5 + 1);
      this.life = 1;
      this.decay = opts.decay || (Math.random() * 0.008 + 0.003);
      this.hue = opts.hue || (Math.random() * 60 + 180); // 青紫色域
      this.sat = opts.sat || (Math.random() * 30 + 60);
      this.light = opts.light || (Math.random() * 20 + 65);
      this.gravity = opts.gravity || 0;
      this.friction = 0.985;
      this.attract = opts.attract || false;
    }
    update() {
      this.vx *= this.friction;
      this.vy *= this.friction;
      this.vy += this.gravity;
      if (this.attract && isCharging) {
        // 水滴吸收效果：向中心聚拢
        const cx = W / 2, cy = H / 2;
        const dx = cx - this.x, dy = cy - this.y;
        const dist = Math.sqrt(dx*dx + dy*dy) || 1;
        this.vx += (dx / dist) * 0.08;
        this.vy += (dy / dist) * 0.08;
      }
      this.x += this.vx;
      this.y += this.vy;
      this.life -= this.decay;
    }
    draw() {
      const alpha = Math.max(0, this.life) * 0.7;
      ctx.beginPath();
      const gradient = ctx.createRadialGradient(this.x, this.y, 0, this.x, this.y, this.size * 3);
      gradient.addColorStop(0, `hsla(${this.hue}, ${this.sat}%, ${this.light}%, ${alpha})`);
      gradient.addColorStop(1, `hsla(${this.hue}, ${this.sat}%, ${this.light}%, 0)`);
      ctx.fillStyle = gradient;
      ctx.arc(this.x, this.y, this.size * 3, 0, Math.PI * 2);
      ctx.fill();
    }
  }

  // 生成环境漂浮粒子
  function spawnAmbient() {
    if (particles.length > 120) return;
    const x = Math.random() * W;
    const y = Math.random() * H;
    particles.push(new Particle(x, y, {
      speed: 0.4,
      size: Math.random() * 1.5 + 0.8,
      decay: Math.random() * 0.004 + 0.001,
      hue: Math.random() * 80 + 170,
      sat: Math.random() * 40 + 50,
      light: Math.random() * 25 + 60,
      gravity: -0.02
    }));
  }

  // 鼠标/触摸轨迹粒子
  function spawnTrail(x, y) {
    for (let i = 0; i < 3; i++) {
      particles.push(new Particle(x + (Math.random()-0.5)*10, y + (Math.random()-0.5)*10, {
        speed: 2,
        size: Math.random() * 2 + 1,
        decay: Math.random() * 0.02 + 0.01,
        hue: Math.random() * 100 + 160,
        sat: Math.random() * 30 + 60,
        light: Math.random() * 20 + 70,
        gravity: 0.02,
        attract: isCharging
      }));
    }
  }

  // 充电动效：粒子向中心汇聚
  function spawnChargeParticles() {
    if (!isCharging) return;
    for (let i = 0; i < 2; i++) {
      const angle = Math.random() * Math.PI * 2;
      const dist = Math.max(W, H) * 0.5;
      const x = W/2 + Math.cos(angle) * dist;
      const y = H/2 + Math.sin(angle) * dist;
      particles.push(new Particle(x, y, {
        speed: 0,
        size: Math.random() * 2 + 1.2,
        decay: Math.random() * 0.006 + 0.002,
        hue: Math.random() * 60 + 190,
        sat: Math.random() * 30 + 65,
        light: Math.random() * 20 + 70,
        attract: true
      }));
    }
  }

  // 动画循环
  let lastSpawn = 0;
  function animate(t) {
    ctx.clearRect(0, 0, W, H);
    spawnAmbient();
    if (t - lastSpawn > 100) {
      spawnChargeParticles();
      lastSpawn = t;
    }
    particles = particles.filter(p => p.life > 0);
    particles.forEach(p => { p.update(); p.draw(); });
    requestAnimationFrame(animate);
  }
  requestAnimationFrame(animate);

  // 事件
  window.addEventListener('mousemove', e => {
    mouse.x = e.clientX; mouse.y = e.clientY;
    if (Math.random() < 0.3) spawnTrail(e.clientX, e.clientY);
  });
  window.addEventListener('touchmove', e => {
    const touch = e.touches[0];
    if (touch) {
      mouse.x = touch.clientX; mouse.y = touch.clientY;
      spawnTrail(touch.clientX, touch.clientY);
    }
  }, { passive: true });
  window.addEventListener('touchstart', e => {
    const touch = e.touches[0];
    if (touch) {
      for (let i = 0; i < 8; i++) spawnTrail(touch.clientX, touch.clientY);
    }
  }, { passive: true });

  // 暴露给外部
  window.__particleSystem = {
    setCharging(val) { isCharging = val; },
    setProgress(val) { chargeProgress = val; }
  };
})();

/* ================================================================
   2. 液态玻璃光效跟随
   ================================================================ */
document.querySelectorAll('.glass-card').forEach(card => {
  const light = card.querySelector('.light-follow');
  if (!light) return;
  card.addEventListener('mousemove', e => {
    const rect = card.getBoundingClientRect();
    light.style.left = (e.clientX - rect.left) + 'px';
    light.style.top = (e.clientY - rect.top) + 'px';
  });
  card.addEventListener('touchmove', e => {
    const touch = e.touches[0];
    if (!touch) return;
    const rect = card.getBoundingClientRect();
    light.style.left = (touch.clientX - rect.left) + 'px';
    light.style.top = (touch.clientY - rect.top) + 'px';
  }, { passive: true });
});

/* ================================================================
   3. 设备信息识别
   ================================================================ */
function getDeviceInfo() {
  const ua = navigator.userAgent;
  let brand = '未知', model = '未知', os = '未知';

  // 品牌识别
  if (/iPhone|iPad|iPod/.test(ua)) {
    brand = 'Apple';
    if (/iPhone/.test(ua)) model = 'iPhone';
    else if (/iPad/.test(ua)) model = 'iPad';
    os = 'iOS';
  } else if (/Huawei|HUAWEI/.test(ua)) { brand = 'Huawei'; os = 'HarmonyOS / Android'; }
  else if (/Xiaomi|Redmi|POCO/.test(ua)) { brand = 'Xiaomi'; os = 'HyperOS / Android'; }
  else if (/OPPO|Realme|OnePlus/.test(ua)) { brand = 'OPPO'; os = 'ColorOS / Android'; }
  else if (/vivo|iQOO/.test(ua)) { brand = 'vivo'; os = 'OriginOS / Android'; }
  else if (/Samsung|SM-/.test(ua)) { brand = 'Samsung'; os = 'One UI / Android'; }
  else if (/Android/.test(ua)) { brand = 'Android'; os = 'Android'; }
  else { brand = '桌面浏览器'; os = 'Desktop'; }

  // 型号（从 UA 中提取）
  const modelMatch = ua.match(/;\s*([^;)]+)\s+Build/);
  if (modelMatch) model = modelMatch[1].trim();

  // 系统版本
  const osMatch = ua.match(/(Android|iPhone OS|CPU OS)\s+([\d_]+)/);
  if (osMatch) os += ' ' + osMatch[2].replace(/_/g, '.');

  return { brand, model, os, ua };
}

function detectGPU() {
  try {
    const canvas = document.createElement('canvas');
    const gl = canvas.getContext('webgl') || canvas.getContext('experimental-webgl');
    if (!gl) return '—';
    const debugInfo = gl.getExtension('WEBGL_debug_renderer_info');
    if (debugInfo) {
      const renderer = gl.getParameter(debugInfo.UNMASKED_RENDERER_WEBGL);
      return renderer || '—';
    }
    return '—';
  } catch { return '—'; }
}

/* ================================================================
   4. Battery API
   ================================================================ */
let batteryObj = null;

function formatTime(seconds) {
  if (!isFinite(seconds) || seconds <= 0) return '—';
  const h = Math.floor(seconds / 3600);
  const m = Math.floor((seconds % 3600) / 60);
  if (h > 0) return `${h}h ${m}m`;
  return `${m} 分钟`;
}

function updateBatteryUI() {
  if (!batteryObj) return;
  const level = batteryObj.level; // 0.0 - 1.0
  const charging = batteryObj.charging;
  const pct = level * 100;

  // 整数部分
  const intPart = Math.floor(pct);
  // 小数部分（模拟 4 位精度，基于 API 原始浮点值）
  const decPart = (pct - intPart).toFixed(4).slice(1); // ".xxxx"

  document.getElementById('levelInt').textContent = intPart;
  document.getElementById('levelDec').textContent = decPart + '%';

  // 环形进度
  const circumference = 2 * Math.PI * 66; // ≈ 414.69
  const offset = circumference * (1 - level);
  document.getElementById('ringFill').style.strokeDashoffset = offset;

  // 充电状态
  const badge = document.getElementById('chargeBadge');
  const badgeText = document.getElementById('chargeText');
  const stateEl = document.getElementById('chargingState');
  const stateSub = document.getElementById('chargingSub');

  if (charging) {
    badge.classList.add('charging');
    badgeText.textContent = '正在充电';
    stateEl.textContent = '充电中';
    stateEl.style.color = '#6ee7ff';
    if (batteryObj.chargingTime > 0 && isFinite(batteryObj.chargingTime)) {
      stateSub.textContent = `预计 ${formatTime(batteryObj.chargingTime)} 充满`;
    } else {
      stateSub.textContent = '计算中…';
    }
  } else {
    badge.classList.remove('charging');
    badgeText.textContent = '未充电';
    stateEl.textContent = '未充电';
    stateEl.style.color = 'rgba(255,255,255,0.55)';
    if (batteryObj.dischargingTime > 0 && isFinite(batteryObj.dischargingTime)) {
      stateSub.textContent = `预计 ${formatTime(batteryObj.dischargingTime)} 耗尽`;
    } else {
      stateSub.textContent = '—';
    }
  }

  // 剩余时间卡片
  const timeEl = document.getElementById('timeRemaining');
  const timeSub = document.getElementById('timeSub');
  if (charging && batteryObj.chargingTime > 0 && isFinite(batteryObj.chargingTime)) {
    timeEl.textContent = formatTime(batteryObj.chargingTime);
    timeSub.textContent = '充满剩余';
  } else if (!charging && batteryObj.dischargingTime > 0 && isFinite(batteryObj.dischargingTime)) {
    timeEl.textContent = formatTime(batteryObj.dischargingTime);
    timeSub.textContent = '续航剩余';
  } else {
    timeEl.textContent = '—';
    timeSub.textContent = '—';
  }

  // 模拟功率指示
  const powerEl = document.getElementById('powerEstimate');
  const powerBar = document.getElementById('powerBar');
  if (charging) {
    // 基于电量反向推断（仅视觉反馈，非真实数据）
    const estPower = pct < 20 ? 5 : pct < 50 ? 15 : pct < 80 ? 10 : 5;
    powerEl.innerHTML = `${estPower} <span class="data-unit">W</span>`;
    powerBar.style.width = Math.min(pct, 100) + '%';
  } else {
    powerEl.innerHTML = `0 <span class="data-unit">W</span>`;
    powerBar.style.width = '0%';
  }

  // 通知粒子系统
  if (window.__particleSystem) {
    window.__particleSystem.setCharging(charging);
  }

  // 状态灯
  const dot = document.getElementById('statusDot');
  if (charging) {
    dot.style.background = '#6ee7ff';
    dot.style.boxShadow = '0 0 12px #6ee7ff';
  } else {
    dot.style.background = 'rgba(255,255,255,0.3)';
    dot.style.boxShadow = 'none';
  }
}

/* ================================================================
   5. 初始化
   ================================================================ */
async function init() {
  // 设备信息
  const dev = getDeviceInfo();
  document.getElementById('deviceName').textContent = dev.brand !== '未知' ? `${dev.brand} ${dev.model}` : '未知设备';
  document.getElementById('deviceSub').textContent = dev.os;

  // GPU
  const gpu = detectGPU();
  document.getElementById('cpuCores').textContent = navigator.hardwareConcurrency || '—';
  document.getElementById('cpuSub').textContent = gpu.length > 30 ? gpu.slice(0, 28) + '…' : gpu;

  // 内存
  const mem = navigator.deviceMemory;
  document.getElementById('deviceMemory').textContent = mem ? `≥ ${mem} GB` : '—';

  // Battery
  if ('getBattery' in navigator) {
    try {
      batteryObj = await navigator.getBattery();
      updateBatteryUI();

      batteryObj.addEventListener('levelchange', updateBatteryUI);
      batteryObj.addEventListener('chargingchange', updateBatteryUI);
      batteryObj.addEventListener('chargingtimechange', updateBatteryUI);
      batteryObj.addEventListener('dischargingtimechange', updateBatteryUI);
    } catch (e) {
      document.getElementById('unsupportedOverlay').classList.add('show');
    }
  } else {
    document.getElementById('unsupportedOverlay').classList.add('show');
  }

  // 请求动画帧更新小数点（基于原始浮点值展示更多位）
  setInterval(() => {
    if (batteryObj) {
      const pct = batteryObj.level * 100;
      const intPart = Math.floor(pct);
      // 用原始 level 的完整浮点值计算小数部分
      const decPart = (pct - intPart).toFixed(4).slice(1);
      document.getElementById('levelDec').textContent = decPart + '%';
    }
  }, 2000);
}

/* ================================================================
   6. 按钮交互
   ================================================================ */
document.getElementById('refreshBtn').addEventListener('click', () => {
  if (navigator.vibrate) navigator.vibrate(10);
  updateBatteryUI();
  // 重播进场动画
  document.querySelectorAll('.fade-up').forEach(el => {
    el.style.animation = 'none';
    el.offsetHeight;
    el.style.animation = '';
  });
});

document.getElementById('vibrateBtn').addEventListener('click', () => {
  if (navigator.vibrate) {
    navigator.vibrate([10, 30, 10]);
  } else {
    alert('此设备不支持振动 API');
  }
});

// 启动
init();

/* ================================================================
   7. 全局触摸涟漪（OPPO 水生动效）
   ================================================================ */
document.addEventListener('touchstart', e => {
  const touch = e.touches[0];
  if (!touch) return;
  const ripple = document.createElement('div');
  ripple.style.cssText = `
    position:fixed; left:${touch.clientX}px; top:${touch.clientY}px;
    width:10px; height:10px; border-radius:50%;
    background: radial-gradient(circle, rgba(110,231,255,0.4), transparent);
    transform: translate(-50%,-50%) scale(0);
    pointer-events:none; z-index:999;
    animation: rippleExpand 0.8s ease-out forwards;
  `;
  document.body.appendChild(ripple);
  setTimeout(() => ripple.remove(), 800);
}, { passive: true });

// 注入涟漪动画
const style = document.createElement('style');
style.textContent = `
  @keyframes rippleExpand {
    0% { transform: translate(-50%,-50%) scale(0); opacity:1; }
    100% { transform: translate(-50%,-50%) scale(20); opacity:0; }
  }
`;
document.head.appendChild(style);

</script>
</body>
</html>
