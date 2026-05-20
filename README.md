<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dashboard Executivo · Assessorias · Mai/26 · UME</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,400;12..96,500;12..96,600;12..96,700;12..96,800&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --ume-green: #14CB53;
    --ume-green-dark: #0FA943;
    --ume-green-soft: #E8FBF0;
    --ink: #00170D;
    --ink-2: #0A2418;
    --ink-3: #163728;
    --paper: #F6F8F5;
    --paper-2: #FFFFFF;
    --line: rgba(0, 23, 13, 0.08);
    --muted: #5B6B62;
    --red: #E63946;
    --red-soft: #FFE8EB;
    --yellow: #F4B400;
    --yellow-soft: #FFF7DD;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  html, body {
    background: var(--paper);
    color: var(--ink);
    font-family: 'Bricolage Grotesque', sans-serif;
    -webkit-font-smoothing: antialiased;
    font-feature-settings: "ss01", "ss02";
  }
  .mono { font-family: 'JetBrains Mono', monospace; font-feature-settings: "tnum"; }

  /* ===== TOP BAR ===== */
  .topbar {
    background: var(--ink);
    color: #fff;
    padding: 20px 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid rgba(255,255,255,0.06);
  }
  .brand { display: flex; align-items: center; gap: 16px; }
  .logo-img {
    height: 38px;
    width: auto;
    display: block;
  }
  .brand-sep {
    width: 1px; height: 28px; background: rgba(255,255,255,0.15);
  }
  .brand-text { line-height: 1.2; }
  .brand-text .name {
    font-size: 14px; font-weight: 600; color: #fff;
    letter-spacing: -0.01em;
  }
  .brand-text .sub {
    font-size: 11px; color: rgba(255,255,255,0.55);
    text-transform: uppercase; letter-spacing: 0.16em; margin-top: 2px;
  }
  .top-meta { display: flex; gap: 14px; align-items: center; font-size: 13px; }
  .top-meta .chip {
    background: rgba(20, 203, 83, 0.12);
    color: var(--ume-green);
    padding: 6px 12px;
    border-radius: 999px;
    border: 1px solid rgba(20, 203, 83, 0.25);
    font-weight: 600; font-size: 12px;
    letter-spacing: 0.04em;
  }
  .top-meta .date { color: rgba(255,255,255,0.7); }

  /* ===== HERO ===== */
  .hero {
    padding: 40px 40px 32px;
    background: linear-gradient(180deg, var(--ink) 0%, var(--ink-2) 100%);
    color: #fff;
    position: relative; overflow: hidden;
  }
  .hero::before {
    content: ''; position: absolute; top: -120px; right: -80px;
    width: 420px; height: 420px; border-radius: 50%;
    background: radial-gradient(circle, rgba(20, 203, 83, 0.18), transparent 70%);
  }
  .hero-inner { position: relative; z-index: 1; }
  .hero h1 {
    font-size: 40px; font-weight: 700; letter-spacing: -0.03em;
    line-height: 1.05; margin-bottom: 12px;
  }
  .hero h1 .accent { color: var(--ume-green); }
  .hero p {
    color: rgba(255,255,255,0.65); font-size: 14px;
    max-width: 540px; line-height: 1.55;
  }

  /* ===== STATUS BAR ===== */
  .status-bar {
    background: var(--paper-2);
    padding: 22px 40px;
    border-bottom: 1px solid var(--line);
    display: flex; gap: 32px; align-items: center;
    flex-wrap: wrap;
  }
  .status-item { display: flex; align-items: center; gap: 10px; font-size: 13px; }
  .dot {
    width: 10px; height: 10px; border-radius: 50%;
    background: currentColor;
  }
  .dot-wrap { position: relative; width: 16px; height: 16px;
    display: flex; align-items: center; justify-content: center; }
  .dot-wrap::after {
    content: ''; position: absolute; inset: 2px;
    border-radius: 50%; background: currentColor; opacity: 0.25;
  }
  .status-item.green { color: var(--ume-green-dark); }
  .status-item.yellow { color: #B88600; }
  .status-item.red { color: var(--red); }
  .status-item strong { color: var(--ink); font-size: 15px; }
  .status-divider {
    flex: 1; height: 1px; background: var(--line);
    margin: 0 8px;
  }

  /* ===== MAIN ===== */
  .main {
    padding: 32px 40px 40px;
  }
  .section-title {
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 20px;
  }
  .section-title h2 {
    font-size: 20px; font-weight: 700; letter-spacing: -0.01em;
  }
  .section-title .marker {
    width: 6px; height: 22px; background: var(--ume-green);
    border-radius: 2px;
  }
  .section-title .count {
    font-size: 13px; color: var(--muted); font-weight: 500;
  }

  /* ===== ASSESSORIAS LIST ===== */
  .assessorias { display: flex; flex-direction: column; gap: 12px; }
  .asses-row {
    background: var(--paper-2);
    border: 1px solid var(--line);
    border-radius: 16px;
    padding: 20px 24px;
    display: grid;
    grid-template-columns: 1.5fr 1fr 1fr 1fr 1fr 0.9fr;
    gap: 20px;
    align-items: center;
    transition: all 0.2s ease;
    position: relative;
    overflow: hidden;
  }
  .asses-row::before {
    content: ''; position: absolute; left: 0; top: 0; bottom: 0;
    width: 4px; background: var(--line);
  }
  .asses-row.status-green::before { background: var(--ume-green); }
  .asses-row.status-yellow::before { background: var(--yellow); }
  .asses-row.status-red::before { background: var(--red); }
  .asses-row:hover {
    transform: translateY(-2px);
    box-shadow: 0 12px 32px rgba(0, 23, 13, 0.08);
  }
  .asses-name {
    font-weight: 700; font-size: 16px; letter-spacing: -0.01em;
    display: flex; align-items: center; gap: 10px;
    flex-wrap: wrap;
  }
  .asses-name .tag {
    font-size: 10px; padding: 3px 8px; border-radius: 6px;
    font-weight: 700; letter-spacing: 0.05em;
    background: var(--ume-green-soft); color: var(--ume-green-dark);
    text-transform: uppercase;
  }
  .asses-col .col-label {
    font-size: 10px; text-transform: uppercase;
    letter-spacing: 0.1em; color: var(--muted);
    margin-bottom: 6px; font-weight: 600;
  }
  .asses-col .col-value {
    font-size: 15px; font-weight: 600;
    font-family: 'JetBrains Mono', monospace;
    font-feature-settings: "tnum";
    letter-spacing: -0.02em;
    color: var(--ink);
  }
  .asses-col .col-value.proj {
    color: var(--ume-green-dark);
  }
  .status-pill {
    display: inline-flex; align-items: center; gap: 7px;
    padding: 7px 14px; border-radius: 999px;
    font-size: 11px; font-weight: 700;
    letter-spacing: 0.06em; text-transform: uppercase;
    justify-self: end;
  }
  .status-pill.green { background: var(--ume-green-soft); color: var(--ume-green-dark); }
  .status-pill.yellow { background: var(--yellow-soft); color: #B88600; }
  .status-pill.red { background: var(--red-soft); color: var(--red); }
  .status-pill .dot { width: 8px; height: 8px; }

  /* FOOTER */
  .footer {
    padding: 24px 40px;
    border-top: 1px solid var(--line);
    color: var(--muted); font-size: 12px;
    display: flex; justify-content: space-between; align-items: center;
    background: var(--paper-2);
  }
  .footer .signature {
    display: flex; align-items: center; gap: 10px;
  }
  .footer .signature img {
    height: 18px;
    width: auto;
  }

  @media (max-width: 1100px) {
    .asses-row { grid-template-columns: 1fr 1fr; gap: 14px; }
    .status-pill { justify-self: start; }
  }
</style>
</head>
<body>

<!-- TOP BAR -->
<div class="topbar">
  <div class="brand">
    <img src="data:image/png;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/4gHYSUNDX1BST0ZJTEUAAQEAAAHIAAAAAAQwAABtbnRyUkdCIFhZWiAH4AABAAEAAAAAAABhY3NwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQAA9tYAAQAAAADTLQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAlkZXNjAAAA8AAAACRyWFlaAAABFAAAABRnWFlaAAABKAAAABRiWFlaAAABPAAAABR3dHB0AAABUAAAABRyVFJDAAABZAAAAChnVFJDAAABZAAAAChiVFJDAAABZAAAAChjcHJ0AAABjAAAADxtbHVjAAAAAAAAAAEAAAAMZW5VUwAAAAgAAAAcAHMAUgBHAEJYWVogAAAAAAAAb6IAADj1AAADkFhZWiAAAAAAAABimQAAt4UAABjaWFlaIAAAAAAAACSgAAAPhAAAts9YWVogAAAAAAAA9tYAAQAAAADTLXBhcmEAAAAAAAQAAAACZmYAAPKnAAANWQAAE9AAAApbAAAAAAAAAABtbHVjAAAAAAAAAAEAAAAMZW5VUwAAACAAAAAcAEcAbwBvAGcAbABlACAASQBuAGMALgAgADIAMAAxADb/2wBDAAUDBAQEAwUEBAQFBQUGBwwIBwcHBw8LCwkMEQ8SEhEPERETFhwXExQaFRERGCEYGh0dHx8fExciJCIeJBweHx7/2wBDAQUFBQcGBw4ICA4eFBEUHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh7/wAARCAAnAI4DASIAAhEBAxEB/8QAGwAAAwEBAQEBAAAAAAAAAAAAAAcIBgUEAwH/xABIEAABAgUCAgUFCwcNAAAAAAABAgMABAUGEQchEjETQVFhcSIygZGyCBQVFzdCUlR0lKEWIzVTwtHhJjNDRFZicoOSo7Gz0v/EABsBAAEFAQEAAAAAAAAAAAAAAAIBAwQGBwUA/8QAMBEAAQIFAwIDBwUBAAAAAAAAAQIRAAMEBSEGEjFBYVFxkQcTFCJSgbEyM0Kh0cH/2gAMAwEAAhEDEQA/APj+TNt/2epP3Nv90TXrZKy0nqVVJeTl2ZdlHR8LbSAlI/Np5AbRVUS3rv8AKlVv8r/rTEeUcxk+hZ0xdwWFKJ+Q8numMNGq0ll2JrUeiS80w0+yuZwttxAUlQ4TsQdjGVjXaN/KfQftX7Jh9XBjSroSKGcR9KvwYptFs23xj+T1J5/U2/3QkNJ9PZW5LgqVWqzRNJlJtbbbCfJD7gUTw7fNAxnHaB2xQgOCDE+6mXdNWoo2Pas69Lsyq1rnJsYDrjriispBHIDiA2327ojoJOBGUabnV1QJtLTLIWsDJJ+VIdz55AHXPZ4fMhTpKmsBiQkJeTaAwEMshA/ARlNRNPaNdNKf6GSl5SrJSVS8y0gIKlDklePOB5b7iJ5t697mo1VZnmqzPPBCwXGnX1LQ4nO6SCcbxW0u6l5hqYb8xxCXE+BGR/zHlJKC8NXW2VunqiXOTNcqyCH5DOD6/eJf0lsVd13M9L1AOMyFPOZzGyirJAbB6iSDnsAMUtSKJS6NLJYpdLlpJpIwOiaAJ8Vcz6TCr1UrA06kZmQtt1TVSr845PPvEDLCDgYR4nOD1bwn5O77olJ5M6zcFSDyVcWVTKlAnvBOCO4wZSV5iyVVurtTJ+JTM2Sv4pL58Sfu4Bzj+6hu6zrfuiRcl6lIMh5QPBNNoCXmz1EKG58DsYlypWzVZO73bXSwp+oImOgQhA/nCfNI7iMHwisLUqZrVsUyrKQELm5VDq0jkFEb49OY5jNss/GZM3UtpJPwe2w0cf0mVBSvHgCR6TAIXteODYr/ADrQZ0maXABYHooFvTx8ozlh6RUCiyrb9bYbq1RIysObsNnsSn53ifUI3vFSaUhLPFT6ekjyUZQ0CPDaOFqpcE1bVmTVQp6CudWpLEvhPFwKVnysdwBPjiJYnvhWfm3JudE5MPuHK3HApSlHvJhUpK8kxIttprNRhVTVT2S7DrnsHAAiu6lQ7erktmepVNn2l8nC0lRPgsb+owk9W9KEUSSdrtuF1yQb8qYlVniUwPpJPWntzuO/qyenFy1y069LvspmjIrcCZqXKVFC0E7nH0hzBirHENPNqbcSHGXElKkkbKSRuD4iPF5ZhKj47S1UjZN3y1dOhA5DZY9x/oiI4I6950r4DuyqUkZ4JWZWhGfo58n8MRyIkRrMqambLTMTwQCPvFuxLmvAI1Sq2evoj/tpijbOqbdZtSl1RtQUJiVQVYPJYGFD0KBhd62abVK5Kk3XqCG3Zrog1MS61hJXw+apJO2cbEHsERpZ2qzGPaUq5Vtuik1J24KXPALjn0ifI3uglOentS6e62D0cmFzDp7AEkD1kgR85HSe/JqYDSqKZZJ5uPvISkeok+oQ17UpElptMUKhsuMzlXr03wTjygRwtJST5A6gFEDfnv6HVqDMIvN9vlMaRdPTLC5i0kAAgsGLkkcMHhnIxxpzyzEaXVMOTdz1SZdJK3Zx1RJ71mLLR548Yi2ufpue+0ue0YCT1iuez4D3s89k/kx44tCgb0Gmk/U2fYTEXxaFA/QFN+xs+wmFndIle0L9uR5q/wCRPPuj3lOajlo54WZJlKd+0FX7ULWGL7on5TJj7Kx7ELqHEfpEW3T4AtdO30j8RWekRJ0zoOT/AFb9pUarujK6Q/JnQfsx9tUftVuBql6k0ykTToQzVJBSWiTsHkueSPSMjxxEYhyYxisp1z6+elAyFLPoST/UeTV65KjalDp1Yp6QtKKghMy2QMONFKspJ6skDcRzJfWqynGELdNRYWRlTZlgopPZkHBjW3vb7F0WvOUR9fRl5ILTmM9G4k5Srwzz7iYmCvWNddFnVS03RJxeDhLjDSnG1jtCkjEGhKVDMWPTtutVzpvdVJ2zEk8EAkHz5bPcQ9fjnsb9fUPun8YPjmsb9fUPuv8AGFRp3phXq7Vpd6qU9+n0pCwp5x9BQpxI+alJ3JPLPIQ/XbSs1ptbz1t0VpptJWtapVACUgZJO3UI8oIGIG60Vgt80Sk75h67VDHbjmJi1Jq0lXb4qlXpxcMrMuhbZWnhVjhAOR4gxnYclC0zl76mp+5kzKKNSZqZWJCXl5cEltJ4QrGQEjb15jx3tovUqVLszFBm11VKl8DjSmghaNieLmQRtj1Q6FpGIvNJqC2SCiiMzapIAYvggcFTM44PeObpFqU5aJVTKm05M0h1fHhG62FHmpOeYPWPT40Fbtw0e4ZUTNIm/fDZGd2lII/1AQQQE1I5jgazstKiUa1AZZOW4Pcjx8o5F56g25aza0zrzz82AeCWaaVlR/xEcIHphH0a9Xqzq9TLlrzwl5dp8YQkFSWGwDhIAGTz9JJMEEKhAaJunrDSIt5nAHdMSQT4AjLYxDyRqNZgUCayef1V3/zErVdxDtVnHWzxIW+tSTjmCo4gghUJCYn6essi2qmGUSdzct0fwAjyxU9G1Cs9mjSDLlXKVtyrSFD3s6cEIAI82CCFWkKh3UNok3JMsTSRtfhureIMJDW6rU+tX69PUyY6eXVLtJC+BSdwnB2UAYw8EEEAwaOvb6dNNSy5KOEgDPaKQ00vm1qbYVHkJ2qdFMMscLiPe7iuE8RPMJxGA90BcVLrdapEzRZ1Twl5dQUsIWgoVx5GOIA+qCCASgBTxXKCwU1PcjVJUrcSo5Zsu/Tv4xodP9amBKtyF3Nu9IgBKZ9lHFxj++kb57xz7IbtFrNOq8uJilzfTtkZyEKR7QEEEBMQBkRXtXafo6OV8TIBSSeOnp09Wjn3LeNvW8hS6tPqaUPmpZWtRPZsMfjCP1T1Wmblll0ejMuyNLUcOqWfzswOw481Pd19fZBBBS0Bnjo6U09RGSisWCpfR+B3A/14Yfufbjp9Qs1ihJUpE/T+MLbKThSCoqCgeXXjHPaOxqTqDTbMTLsraXNTrys9AkEcLeDlRVy54GIIIHaCto5c2y00/UiqdblJdRz1If0eP//Z" alt="UME" class="logo-img">
    <div class="brand-sep"></div>
    <div class="brand-text">
      <div class="name">Dashboard Executivo</div>
      <div class="sub">Assessorias</div>
    </div>
  </div>
  <div class="top-meta">
    <span class="chip">● Mai · 2026</span>
    <span class="date">Visibilidade do resultado atual</span>
  </div>
</div>

<!-- HERO -->
<div class="hero">
  <div class="hero-inner">
    <h1>Resultado <span class="accent">Mai/26</span> · Assessorias</h1>
    <p>Acompanhamento consolidado de recebimentos, colchão e projeção de entrega por parceiro.</p>
  </div>
</div>

<!-- STATUS BAR -->
<div class="status-bar">
  <div class="status-item green">
    <div class="dot-wrap"><div class="dot"></div></div>
    <strong>6</strong>&nbsp;no verde
  </div>
  <div class="status-item yellow">
    <div class="dot-wrap"><div class="dot"></div></div>
    <strong>1</strong>&nbsp;em atenção (amarelo)
  </div>
  <div class="status-item red">
    <div class="dot-wrap"><div class="dot"></div></div>
    <strong>2</strong>&nbsp;críticos (vermelho)
  </div>
  <div class="status-divider"></div>
  <div class="status-item" style="color: var(--muted);">
    Total · <strong style="margin-left:6px;">9 assessorias</strong>
  </div>
</div>

<!-- MAIN -->
<div class="main">
  <div class="section-title">
    <div class="marker"></div>
    <h2>Visão por Assessoria</h2>
    <span class="count">· 9 parceiros</span>
  </div>
  <div class="assessorias" id="assessoriasList"></div>
</div>

<div class="footer">
  <div>Fonte: Visibilidade do resultado atual · Mai/26 · Assessorias</div>
  <div class="signature">
    <span>Powered by</span>
    <img src="data:image/png;base64,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" alt="UME">
  </div>
</div>

<script>
const data = [
  { name: 'Facto', abr: 72497.55, mai: 55711.07, colchao: 24249.18, proj: 101292.85, status: 'yellow', tag: '' },
  { name: 'CSA', abr: 22667.98, mai: 27642.10, colchao: 8520.63, proj: 50258.36, status: 'green', tag: 'UME EXCLUSIVA' },
  { name: 'CSA', abr: 38116.74, mai: 49038.99, colchao: 2998.81, proj: 89161.80, status: 'green', tag: 'NM' },
  { name: 'Vertice', abr: 11692.79, mai: 6785.40, colchao: 5001.77, proj: 12337.09, status: 'red', tag: 'UME EXCLUSIVA' },
  { name: 'Amaral', abr: 88804.37, mai: 38739.78, colchao: 30122.77, proj: 70435.96, status: 'red', tag: 'ODRES' },
  { name: 'Amaral', abr: 146256.45, mai: 115928.21, colchao: 37523.83, proj: 210778.56, status: 'green', tag: 'NM' },
  { name: 'Renova', abr: 49749.94, mai: 34651.32, colchao: 4136.75, proj: 63002.40, status: 'green', tag: 'BY UME' },
  { name: 'Renova', abr: 448283.99, mai: 294352.51, colchao: 61760.73, proj: 535186.38, status: 'green', tag: 'NM' },
  { name: 'Souza', abr: 72551.94, mai: 88795.12, colchao: 11880.57, proj: 161445.67, status: 'green', tag: 'NM' },
];

const fmt = v => 'R$ ' + v.toLocaleString('pt-BR', { minimumFractionDigits: 2, maximumFractionDigits: 2 });

const list = document.getElementById('assessoriasList');
data.forEach(d => {
  const statusLabel = d.status === 'green' ? 'No verde' : d.status === 'yellow' ? 'Atenção' : 'Crítico';
  const tagHtml = d.tag ? `<span class="tag">${d.tag}</span>` : '';

  list.insertAdjacentHTML('beforeend', `
    <div class="asses-row status-${d.status}">
      <div class="asses-name">
        ${d.name}
        ${tagHtml}
      </div>
      <div class="asses-col">
        <div class="col-label">Recebimento Abr/26</div>
        <div class="col-value">${fmt(d.abr)}</div>
      </div>
      <div class="asses-col">
        <div class="col-label">Recebimento Mai/26</div>
        <div class="col-value">${fmt(d.mai)}</div>
      </div>
      <div class="asses-col">
        <div class="col-label">Recebimento Colchão</div>
        <div class="col-value">${fmt(d.colchao)}</div>
      </div>
      <div class="asses-col">
        <div class="col-label">Projeção Entrega Mai/26</div>
        <div class="col-value proj">${fmt(d.proj)}</div>
      </div>
      <span class="status-pill ${d.status}"><span class="dot"></span>${statusLabel}</span>
    </div>
  `);
});
</script>

</body>
</html>
