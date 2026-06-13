<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Data Foundation Class | One-Day In-Person Bootcamp</title>
<link href="https://fonts.googleapis.com/css2?family=Alfa+Slab+One&family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #f8d618;
    --navy: #111835;
    --white: #ffffff;
    --navy-light: #1e2d5a;
    --navy-mid: #1a2448;
    --text-muted: #6b7a99;
    --border: #e8ecf5;
    --section-bg: #f5f7fc;

    --discover: #f8d618;
    --discover-bg: #fef9e6;
    --discover-text: #a37e00;

    --analyze: #217346;
    --analyze-bg: #e8f5ee;
    --analyze-dark: #1a5c38;

    --tell: #2563eb;
    --tell-bg: #eff6ff;
    --tell-dark: #1d4ed8;

    --act: #e2574c;
    --act-bg: #fdeeec;
    --act-dark: #b8392f;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body { font-family: 'Inter', sans-serif; background: var(--white); color: var(--navy); line-height: 1.6; }

  /* COVER */
  .cover { background: var(--navy); color: var(--white); padding: 64px 48px 56px; position: relative; overflow: hidden; }
  .cover::before { content: ''; position: absolute; top: -60px; right: -60px; width: 340px; height: 340px; background: var(--gold); opacity: 0.08; border-radius: 50%; }
  .cover::after { content: ''; position: absolute; bottom: -80px; left: 30%; width: 220px; height: 220px; background: var(--gold); opacity: 0.05; border-radius: 50%; }
  .cover-top { display: flex; align-items: center; gap: 12px; margin-bottom: 48px; }
  .brand-dot { width: 10px; height: 10px; background: var(--gold); border-radius: 50%; }
  .brand-name { font-family: 'Alfa Slab One', serif; font-size: 13px; letter-spacing: 2px; color: var(--gold); text-transform: uppercase; }
  .cover-badge { display: inline-block; background: var(--gold); color: var(--navy); font-size: 11px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; padding: 6px 16px; border-radius: 2px; margin-bottom: 24px; }
  .cover h1 { font-family: 'Alfa Slab One', serif; font-size: 50px; line-height: 1.1; color: var(--white); margin-bottom: 8px; }
  .cover h1 span { color: var(--gold); }
  .cover-subtitle { font-size: 16px; color: rgba(255,255,255,0.6); margin-bottom: 48px; font-weight: 400; max-width: 720px; }
  .cover-meta { display: flex; gap: 40px; flex-wrap: wrap; border-top: 1px solid rgba(255,255,255,0.1); padding-top: 32px; position: relative; z-index: 1; }
  .meta-item label { display: block; font-size: 10px; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); font-weight: 600; margin-bottom: 4px; }
  .meta-item span { font-size: 14px; color: var(--white); font-weight: 500; }

  /* CONTEXT BAND */
  .context-band { padding: 56px 48px; background: var(--gold); display: grid; grid-template-columns: 1fr 1fr; gap: 48px; align-items: center; }
  .context-left h2 { font-family: 'Alfa Slab One', serif; font-size: 30px; color: var(--navy); line-height: 1.2; margin-bottom: 16px; }
  .context-left p { font-size: 15px; color: var(--navy); opacity: 0.8; line-height: 1.7; }
  .context-left p + p { margin-top: 12px; }
  .context-right { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  .stat-card { background: var(--navy); color: var(--white); padding: 24px; border-radius: 4px; }
  .stat-card .number { font-family: 'Alfa Slab One', serif; font-size: 36px; color: var(--gold); line-height: 1; margin-bottom: 6px; }
  .stat-card .label { font-size: 12px; color: rgba(255,255,255,0.6); letter-spacing: 1px; text-transform: uppercase; }

  /* FRAMEWORK SECTION */
  .framework-section { padding: 56px 48px; background: var(--section-bg); }
  .framework-section h2 { font-family: 'Alfa Slab One', serif; font-size: 28px; color: var(--navy); margin-bottom: 8px; }
  .framework-section .sub { font-size: 14px; color: var(--text-muted); margin-bottom: 32px; max-width: 680px; line-height: 1.7; }
  .framework-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; }
  .framework-card { background: var(--white); border: 1px solid var(--border); border-radius: 4px; padding: 28px 24px; border-top: 5px solid var(--navy); }
  .framework-card .fc-letter { font-family: 'Alfa Slab One', serif; font-size: 40px; line-height: 1; margin-bottom: 10px; }
  .framework-card h4 { font-size: 16px; font-weight: 700; color: var(--navy); margin-bottom: 8px; }
  .framework-card p { font-size: 13px; color: var(--text-muted); line-height: 1.6; margin-bottom: 14px; }
  .fc-tag { font-size: 10px; font-weight: 700; letter-spacing: 1.5px; text-transform: uppercase; padding: 4px 10px; border-radius: 2px; display: inline-block; }
  .fc-discover { border-top-color: var(--discover); }
  .fc-discover .fc-letter { color: var(--discover-text); }
  .fc-discover .fc-tag { background: var(--discover-bg); color: var(--discover-text); }
  .fc-analyze { border-top-color: var(--analyze); }
  .fc-analyze .fc-letter { color: var(--analyze); }
  .fc-analyze .fc-tag { background: var(--analyze-bg); color: var(--analyze); }
  .fc-tell { border-top-color: var(--tell); }
  .fc-tell .fc-letter { color: var(--tell); }
  .fc-tell .fc-tag { background: var(--tell-bg); color: var(--tell); }
  .fc-act { border-top-color: var(--act); }
  .fc-act .fc-letter { color: var(--act); }
  .fc-act .fc-tag { background: var(--act-bg); color: var(--act); }

  /* BLUEPRINT TABLE */
  .blueprint-section { padding: 56px 48px; }
  .blueprint-section h2 { font-family: 'Alfa Slab One', serif; font-size: 28px; color: var(--navy); margin-bottom: 8px; }
  .blueprint-section .sub { font-size: 14px; color: var(--text-muted); margin-bottom: 28px; }
  .blueprint-table-wrap { border: 1px solid var(--border); border-radius: 4px; overflow: hidden; overflow-x: auto; }
  .blueprint-table { width: 100%; border-collapse: collapse; min-width: 760px; }
  .blueprint-table thead th { background: var(--navy); color: var(--gold); font-size: 10.5px; letter-spacing: 2px; text-transform: uppercase; padding: 14px 18px; text-align: left; font-weight: 700; white-space: nowrap; }
  .blueprint-table tbody td { padding: 13px 18px; font-size: 13px; color: var(--navy); border-bottom: 1px solid var(--border); vertical-align: top; }
  .blueprint-table tbody tr:last-child td { border-bottom: none; }
  .blueprint-table tbody tr:nth-child(even):not(.bp-break) { background: var(--section-bg); }
  .blueprint-table .bp-time { font-weight: 700; white-space: nowrap; width: 14%; }
  .blueprint-table .bp-session { font-weight: 600; width: 27%; }
  .blueprint-table .bp-lens { width: 22%; }
  .lens-chip { font-size: 10.5px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; padding: 3px 9px; border-radius: 2px; white-space: nowrap; display: inline-block; }
  .lens-discover { background: var(--discover-bg); color: var(--discover-text); }
  .lens-analyze { background: var(--analyze-bg); color: var(--analyze); }
  .lens-tell { background: var(--tell-bg); color: var(--tell); }
  .lens-act { background: var(--act-bg); color: var(--act); }
  tr.bp-break td { background: var(--white); font-style: italic; color: var(--text-muted); font-size: 12.5px; border-left: 3px solid var(--gold); }
  tr.bp-break .bp-time { font-style: normal; color: var(--text-muted); }

  /* PHASE DIVIDER */
  .phase-divider { display: flex; align-items: center; gap: 0; padding: 0 48px; margin: 48px 0 0; }
  .phase-label { padding: 14px 32px; font-family: 'Alfa Slab One', serif; font-size: 15px; letter-spacing: 1px; text-transform: uppercase; }
  .phase-line { flex: 1; height: 3px; }
  .phase-days { padding: 14px 24px; font-size: 13px; font-weight: 700; letter-spacing: 1px; white-space: nowrap; }
  .phase-discover .phase-label { background: var(--discover); color: var(--navy); }
  .phase-discover .phase-line { background: var(--discover); }
  .phase-discover .phase-days { background: var(--navy); color: var(--gold); }
  .phase-analyze .phase-label { background: var(--analyze); color: var(--white); }
  .phase-analyze .phase-line { background: var(--analyze); }
  .phase-analyze .phase-days { background: var(--analyze-dark); color: rgba(255,255,255,0.85); }
  .phase-tell .phase-label { background: var(--tell); color: var(--white); }
  .phase-tell .phase-line { background: var(--tell); }
  .phase-tell .phase-days { background: var(--tell-dark); color: rgba(255,255,255,0.85); }
  .phase-act .phase-label { background: var(--act); color: var(--white); }
  .phase-act .phase-line { background: var(--act); }
  .phase-act .phase-days { background: var(--act-dark); color: rgba(255,255,255,0.9); }

  /* SESSIONS GRID & CARDS */
  .sessions-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 24px; padding: 24px 48px 8px; }
  .sessions-grid.single { grid-template-columns: 1fr; }
  .sessions-grid.last { padding-bottom: 48px; }
  .session-card { border-radius: 4px; overflow: hidden; border: 1px solid var(--border); }
  .sc-discover { border-top: 4px solid var(--discover); }
  .sc-analyze { border-top: 4px solid var(--analyze); }
  .sc-tell { border-top: 4px solid var(--tell); }
  .sc-act { border-top: 4px solid var(--act); }
  .session-header { padding: 20px 24px 16px; display: flex; align-items: flex-start; justify-content: space-between; gap: 12px; flex-wrap: wrap; }
  .session-number { font-family: 'Alfa Slab One', serif; font-size: 11px; letter-spacing: 2px; text-transform: uppercase; color: var(--text-muted); }
  .lens-tag { font-size: 10px; font-weight: 700; letter-spacing: 1.5px; text-transform: uppercase; padding: 4px 10px; border-radius: 2px; white-space: nowrap; }
  .sc-discover .lens-tag { background: var(--discover-bg); color: var(--discover-text); }
  .sc-analyze .lens-tag { background: var(--analyze-bg); color: var(--analyze); }
  .sc-tell .lens-tag { background: var(--tell-bg); color: var(--tell); }
  .sc-act .lens-tag { background: var(--act-bg); color: var(--act); }
  .session-title { padding: 0 24px 12px; font-size: 18px; font-weight: 700; color: var(--navy); line-height: 1.35; }
  .session-divider { height: 1px; background: var(--border); margin: 0 24px; }
  .session-body { padding: 16px 24px 22px; }
  .session-card.single .session-body { display: grid; grid-template-columns: 1.05fr 1fr; gap: 32px; }
  .section-title { font-size: 10px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--text-muted); margin-bottom: 10px; margin-top: 14px; }
  .section-title:first-child { margin-top: 0; }
  .topics-list { list-style: none; padding: 0; }
  .topics-list li { font-size: 13px; color: var(--navy); padding: 5px 0 5px 16px; position: relative; line-height: 1.5; }
  .topics-list li::before { content: ''; position: absolute; left: 0; top: 11px; width: 6px; height: 6px; border-radius: 50%; }
  .sc-discover .topics-list li::before { background: var(--discover); border: 1px solid #c9a800; }
  .sc-analyze .topics-list li::before { background: var(--analyze); }
  .sc-tell .topics-list li::before { background: var(--tell); }
  .sc-act .topics-list li::before { background: var(--act); }
  .func-tags { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 4px; }
  .func-tag { font-family: 'Courier New', monospace; font-size: 10.5px; font-weight: 700; padding: 3px 10px; border-radius: 2px; border: 1px solid var(--border); white-space: nowrap; background: var(--analyze-bg); color: var(--analyze); }
  .activity-box { background: var(--section-bg); padding: 14px 16px; border-radius: 0 3px 3px 0; margin-top: 6px; font-size: 13px; color: var(--navy); line-height: 1.65; }
  .sc-discover .activity-box { border-left: 3px solid var(--discover); }
  .sc-analyze .activity-box { border-left: 3px solid var(--analyze); }
  .sc-tell .activity-box { border-left: 3px solid var(--tell); }
  .sc-act .activity-box { border-left: 3px solid var(--act); }
  .outcome-text { font-size: 13px; color: var(--navy); line-height: 1.6; }
  .speed-pill { display: inline-flex; align-items: center; gap: 6px; background: var(--navy); color: var(--gold); font-size: 10.5px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; padding: 6px 12px; border-radius: 20px; margin-top: 14px; }
  .deliverable-box { background: var(--navy); color: var(--white); padding: 12px 16px; border-radius: 3px; margin-top: 14px; border-left: 4px solid var(--gold); }
  .deliverable-box .del-label { font-size: 9px; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); font-weight: 700; margin-bottom: 4px; }
  .deliverable-box p { font-size: 12px; color: rgba(255,255,255,0.85); line-height: 1.5; }

  /* BREAK BANDS */
  .break-band { margin: 24px 48px; padding: 18px 28px; border-radius: 4px; background: var(--section-bg); border-left: 4px solid var(--gold); display: flex; align-items: center; gap: 24px; flex-wrap: wrap; }
  .break-band.reset { border-left-color: var(--act); }
  .break-time { font-family: 'Alfa Slab One', serif; font-size: 13px; letter-spacing: 1.5px; text-transform: uppercase; color: var(--navy); white-space: nowrap; }
  .break-divider { width: 1px; height: 32px; background: var(--border); }
  .break-content { flex: 1; min-width: 220px; }
  .break-label { font-size: 10.5px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--discover-text); margin-bottom: 3px; }
  .break-band.reset .break-label { color: var(--act); }
  .break-note { font-size: 13px; color: var(--text-muted); line-height: 1.5; }

  /* CAPSTONE (Session 6) */
  .capstone-wrap { padding: 24px 48px 8px; }
  .capstone-inner { background: var(--navy); border-radius: 4px; padding: 36px 40px; }
  .capstone-header { display: flex; align-items: flex-start; justify-content: space-between; gap: 12px; flex-wrap: wrap; margin-bottom: 14px; }
  .capstone-header .session-number { color: rgba(255,255,255,0.45); }
  .capstone-header .lens-tag { background: rgba(248,214,24,0.12); color: var(--gold); }
  .capstone-inner h3 { font-family: 'Alfa Slab One', serif; font-size: 28px; color: var(--gold); line-height: 1.2; margin-bottom: 18px; }
  .capstone-body { display: grid; grid-template-columns: 1fr 1fr; gap: 36px; }
  .capstone-body h4 { font-size: 11px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); margin-bottom: 12px; }
  .brief-steps { list-style: none; padding: 0; counter-reset: step; }
  .brief-steps li { position: relative; padding: 9px 0 9px 38px; font-size: 13.5px; color: rgba(255,255,255,0.85); border-bottom: 1px solid rgba(255,255,255,0.08); }
  .brief-steps li:last-child { border-bottom: none; }
  .brief-steps li::before { counter-increment: step; content: counter(step); position: absolute; left: 0; top: 7px; width: 22px; height: 22px; border-radius: 50%; background: var(--gold); color: var(--navy); font-family: 'Alfa Slab One', serif; font-size: 11px; display: flex; align-items: center; justify-content: center; }
  .judging-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .judging-item { background: rgba(255,255,255,0.06); border: 1px solid rgba(248,214,24,0.2); border-radius: 3px; padding: 14px 16px; }
  .judging-item .ji-label { font-family: 'Alfa Slab One', serif; font-size: 13px; color: var(--gold); letter-spacing: 1px; text-transform: uppercase; margin-bottom: 6px; }
  .judging-item p { font-size: 12px; color: rgba(255,255,255,0.7); line-height: 1.5; }
  .capstone-outcome { margin-top: 24px; padding-top: 20px; border-top: 1px solid rgba(255,255,255,0.1); font-size: 13.5px; color: rgba(255,255,255,0.7); font-style: italic; }

  /* GUIDELINES */
  .guidelines-section { padding: 56px 48px; background: var(--section-bg); }
  .guidelines-section h2 { font-family: 'Alfa Slab One', serif; font-size: 28px; color: var(--navy); margin-bottom: 8px; }
  .guidelines-section .sub { font-size: 14px; color: var(--text-muted); margin-bottom: 32px; max-width: 680px; line-height: 1.7; }
  .guidelines-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
  .guideline-card { background: var(--white); border: 1px solid var(--border); border-radius: 4px; padding: 24px; }
  .guideline-card .gc-num { font-family: 'Alfa Slab One', serif; font-size: 28px; color: var(--gold); line-height: 1; margin-bottom: 10px; -webkit-text-stroke: 1px var(--navy); }
  .guideline-card h4 { font-size: 14px; font-weight: 700; color: var(--navy); margin-bottom: 8px; }
  .guideline-card p { font-size: 12.5px; color: var(--text-muted); line-height: 1.65; }

  /* OUTCOMES */
  .outcomes2-section { padding: 56px 48px; }
  .outcomes2-section h2 { font-family: 'Alfa Slab One', serif; font-size: 28px; color: var(--navy); margin-bottom: 28px; }
  .outcomes-cols { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
  .outcome-col { border-radius: 4px; padding: 32px; }
  .outcome-col.tangible { background: var(--navy); color: var(--white); }
  .outcome-col.intangible { background: var(--gold); color: var(--navy); }
  .outcome-col h3 { font-family: 'Alfa Slab One', serif; font-size: 19px; margin-bottom: 18px; }
  .outcome-col.tangible h3 { color: var(--gold); }
  .outcome-col.intangible h3 { color: var(--navy); }
  .outcome-col ul { list-style: none; }
  .outcome-col li { padding: 10px 0 10px 26px; position: relative; font-size: 14px; line-height: 1.5; }
  .outcome-col.tangible li { border-bottom: 1px solid rgba(255,255,255,0.1); }
  .outcome-col.intangible li { border-bottom: 1px solid rgba(17,24,53,0.12); }
  .outcome-col li:last-child { border-bottom: none; padding-bottom: 0; }
  .outcome-col li::before { content: '\2713'; position: absolute; left: 0; top: 10px; font-weight: 700; font-size: 13px; }
  .outcome-col.tangible li::before { color: var(--gold); }
  .outcome-col.intangible li::before { color: var(--navy); }

  /* PATHWAY */
  .pathway-section { background: var(--navy); padding: 56px 48px; }
  .pathway-section h2 { font-family: 'Alfa Slab One', serif; font-size: 28px; color: var(--gold); margin-bottom: 8px; text-align: center; }
  .pathway-section .sub { text-align: center; color: rgba(255,255,255,0.6); margin-bottom: 36px; font-size: 14px; }
  .pathway-grid { display: grid; grid-template-columns: 1fr auto 1fr; gap: 24px; align-items: center; margin-bottom: 32px; }
  .pathway-card { background: rgba(255,255,255,0.05); border: 1px solid rgba(248,214,24,0.15); border-radius: 4px; padding: 28px; }
  .pathway-card .pc-label { font-size: 10px; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); font-weight: 700; margin-bottom: 10px; }
  .pathway-card h4 { font-family: 'Alfa Slab One', serif; font-size: 19px; color: var(--white); margin-bottom: 14px; }
  .pathway-card ul { list-style: none; }
  .pathway-card li { font-size: 13px; color: rgba(255,255,255,0.75); padding: 5px 0 5px 16px; position: relative; line-height: 1.5; }
  .pathway-card li::before { content: ''; position: absolute; left: 0; top: 12px; width: 6px; height: 6px; border-radius: 50%; background: var(--gold); }
  .pathway-arrow { font-family: 'Alfa Slab One', serif; font-size: 28px; color: var(--gold); text-align: center; }
  .pathway-quote { background: rgba(248,214,24,0.07); border-left: 4px solid var(--gold); padding: 24px 28px; border-radius: 0 4px 4px 0; font-size: 15px; color: rgba(255,255,255,0.85); line-height: 1.75; font-style: italic; }
  .pathway-quote strong { color: var(--gold); font-style: normal; }
  .pathway-quote .pq-attr { display: block; margin-top: 12px; font-size: 12px; color: rgba(255,255,255,0.5); font-style: normal; letter-spacing: 1px; text-transform: uppercase; }

  /* FOOTER */
  .footer { background: var(--navy); padding: 40px 48px; display: flex; align-items: center; justify-content: space-between; gap: 24px; flex-wrap: wrap; border-top: 1px solid rgba(255,255,255,0.06); }
  .footer-brand { font-family: 'Alfa Slab One', serif; font-size: 16px; color: var(--white); }
  .footer-brand span { color: var(--gold); }
  .footer-note { font-size: 12px; color: rgba(255,255,255,0.4); }

  @media (max-width: 900px) {
    .cover h1 { font-size: 34px; }
    .context-band { grid-template-columns: 1fr; }
    .context-right { grid-template-columns: 1fr 1fr; }
    .framework-grid { grid-template-columns: 1fr 1fr; }
    .sessions-grid { grid-template-columns: 1fr; }
    .session-card.single .session-body { grid-template-columns: 1fr; gap: 0; }
    .capstone-body { grid-template-columns: 1fr; gap: 24px; }
    .judging-grid { grid-template-columns: 1fr 1fr; }
    .guidelines-grid { grid-template-columns: 1fr 1fr; }
    .outcomes-cols { grid-template-columns: 1fr; }
    .pathway-grid { grid-template-columns: 1fr; }
    .pathway-arrow { transform: rotate(90deg); }
    .break-band { flex-direction: column; align-items: flex-start; gap: 8px; }
    .break-divider { display: none; }
  }
</style>
</head>
<body>

<!-- COVER -->
<div class="cover">
  <div class="cover-top">
    <div class="brand-dot"></div>
    <div class="brand-name">The Digital College &nbsp;/&nbsp; Data with Miss Mailiana</div>
  </div>
  <div class="cover-badge">In-Person Bootcamp &middot; One Day</div>
  <h1>From Raw Data to <span>Business Insights</span><br>in One Day</h1>
  <p class="cover-subtitle">The Data Foundation Class &mdash; In-Person Bootcamp &middot; A full day of practical application, networking, and collaboration that ends with one completed project and a memorable experience &mdash; not just notes.</p>
  <div class="cover-meta">
    <div class="meta-item"><label>Duration</label><span>9:00 AM &ndash; 6:00 PM &nbsp;|&nbsp; 9 Hours On-Site</span></div>
    <div class="meta-item"><label>Format</label><span>8 Sessions + Graduation</span></div>
    <div class="meta-item"><label>Approach</label><span>The D.A.T.A. Framework</span></div>
    <div class="meta-item"><label>Audience</label><span>Beginners, Students, Career-Switchers &amp; Entrepreneurs</span></div>
  </div>
</div>

<!-- CONTEXT BAND -->
<div class="context-band">
  <div class="context-left">
    <h2>Built For The Room, Not Just The Screen</h2>
    <p>The online Data Foundation Class is about learning tools. This in-person day is different: it's about practical application, networking, collaboration, confidence, and project execution &mdash; in real time, alongside other people.</p>
    <p>Because everyone is physically in the room, every session is designed to produce something. By 6:00 PM, each participant walks out with a completed analysis, a working dashboard, a five-canvas workbook, and a cohort of people who were there with them.</p>
  </div>
  <div class="context-right">
    <div class="stat-card"><div class="number">8</div><div class="label">Live Sessions</div></div>
    <div class="stat-card"><div class="number">5</div><div class="label">Take-Home Canvases</div></div>
    <div class="stat-card"><div class="number">1</div><div class="label">Completed Project</div></div>
    <div class="stat-card"><div class="number">4</div><div class="label">Framework Phases</div></div>
  </div>
</div>

<!-- D.A.T.A. FRAMEWORK -->
<div class="framework-section">
  <h2>Today's Framework: D.A.T.A.</h2>
  <p class="sub">Every session sits inside one of four phases. Together they form a repeatable thinking pattern &mdash; participants can run it again on any dataset, long after the bootcamp ends.</p>
  <div class="framework-grid">
    <div class="framework-card fc-discover">
      <div class="fc-letter">D</div>
      <h4>Discover</h4>
      <p>Find your place in the data world, then learn to think like an analyst &mdash; turning a vague business problem into a clear question.</p>
      <div class="fc-tag">Sessions 1 &ndash; 2</div>
    </div>
    <div class="framework-card fc-analyze">
      <div class="fc-letter">A</div>
      <h4>Analyze</h4>
      <p>Get hands-on with a real dataset in Excel and produce a genuine first business insight &mdash; start to finish, independently.</p>
      <div class="fc-tag">Session 3</div>
    </div>
    <div class="framework-card fc-tell">
      <div class="fc-letter">T</div>
      <h4>Tell</h4>
      <p>Turn that insight into a dashboard and a story, then see the same idea rebuilt at business scale inside Power BI.</p>
      <div class="fc-tag">Sessions 4 &ndash; 5</div>
    </div>
    <div class="framework-card fc-act">
      <div class="fc-letter">A</div>
      <h4>Act</h4>
      <p>Compete on a live business challenge, map the next 90 days, and join a community that keeps the momentum going.</p>
      <div class="fc-tag">Sessions 6 &ndash; 8</div>
    </div>
  </div>
</div>

<!-- TRAINER BLUEPRINT TABLE -->
<div class="blueprint-section">
  <h2>Trainer's Day-at-a-Glance</h2>
  <p class="sub">Every session, framework lens, and deliverable for the day in a single view.</p>
  <div class="blueprint-table-wrap">
    <table class="blueprint-table">
      <thead>
        <tr><th>Time</th><th>Session</th><th>Framework Lens</th><th>Deliverable &amp; Output</th></tr>
      </thead>
      <tbody>
        <tr>
          <td class="bp-time">9:00 &ndash; 9:45 AM</td>
          <td class="bp-session">Welcome &amp; Data Career Roadmap</td>
          <td class="bp-lens"><span class="lens-chip lens-discover">Career Compass</span></td>
          <td>Personal career-goal statement; cohort introductions</td>
        </tr>
        <tr>
          <td class="bp-time">9:45 &ndash; 10:45 AM</td>
          <td class="bp-session">Understanding Data</td>
          <td class="bp-lens"><span class="lens-chip lens-discover">Question Translator</span></td>
          <td>Business-to-data question worksheet &mdash; reviewed live (Speed Coaching)</td>
        </tr>
        <tr class="bp-break">
          <td class="bp-time">10:45 &ndash; 11:00 AM</td>
          <td class="bp-session">Tea Break</td>
          <td class="bp-lens">Peer Reflection Circle</td>
          <td>Peer feedback exchanged on Sessions 1 &amp; 2 canvases</td>
        </tr>
        <tr>
          <td class="bp-time">11:00 AM &ndash; 12:30 PM</td>
          <td class="bp-session">Excel for Data Analysis</td>
          <td class="bp-lens"><span class="lens-chip lens-analyze">First Insight Sprint</span></td>
          <td>First completed analysis &mdash; 3 business questions answered (Speed Coaching)</td>
        </tr>
        <tr class="bp-break">
          <td class="bp-time">12:30 &ndash; 1:30 PM</td>
          <td class="bp-session">Lunch Break</td>
          <td class="bp-lens">Peer Reflection Circle</td>
          <td>Small groups share their First Insight Card finding</td>
        </tr>
        <tr>
          <td class="bp-time">1:30 &ndash; 2:45 PM</td>
          <td class="bp-session">Dashboard Building</td>
          <td class="bp-lens"><span class="lens-chip lens-tell">Data Story Canvas</span></td>
          <td>Mini dashboard + one-sentence data story (Speed Coaching)</td>
        </tr>
        <tr>
          <td class="bp-time">2:45 &ndash; 3:45 PM</td>
          <td class="bp-session">Power BI Demonstration</td>
          <td class="bp-lens"><span class="lens-chip lens-tell">Scale-Up Walkthrough</span></td>
          <td>Excel-to-Power BI translation map</td>
        </tr>
        <tr class="bp-break">
          <td class="bp-time">3:45 &ndash; 4:00 PM</td>
          <td class="bp-session">Break</td>
          <td class="bp-lens">Energy Reset</td>
          <td>Short reset ritual ahead of the final sprint</td>
        </tr>
        <tr>
          <td class="bp-time">4:00 &ndash; 4:45 PM</td>
          <td class="bp-session">Business Challenge Competition</td>
          <td class="bp-lens"><span class="lens-chip lens-act">The Execution Sprint</span></td>
          <td>Team dashboard + live judged presentation</td>
        </tr>
        <tr>
          <td class="bp-time">4:45 &ndash; 5:15 PM</td>
          <td class="bp-session">Career Launch Session</td>
          <td class="bp-lens"><span class="lens-chip lens-act">90-Day Portfolio Pathway</span></td>
          <td>Completed "My Next 90 Days" canvas</td>
        </tr>
        <tr>
          <td class="bp-time">5:15 &ndash; 6:00 PM</td>
          <td class="bp-session">Graduation &amp; Networking</td>
          <td class="bp-lens"><span class="lens-chip lens-act">Community Circle</span></td>
          <td>Certificate, community access &amp; program registration</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<!-- PHASE 1: DISCOVER -->
<div class="phase-divider phase-discover">
  <div class="phase-label">Phase 1 &nbsp; Discover</div>
  <div class="phase-line"></div>
  <div class="phase-days">Sessions 1 &ndash; 2 &nbsp;&bull;&nbsp; 9:00 &ndash; 10:45 AM</div>
</div>

<div class="sessions-grid">

  <!-- SESSION 1 -->
  <div class="session-card sc-discover">
    <div class="session-header">
      <div class="session-number">Session 01 &middot; 9:00 &ndash; 9:45 AM</div>
      <div class="lens-tag">Career Compass</div>
    </div>
    <div class="session-title">Welcome &amp; Data Career Roadmap</div>
    <div class="session-divider"></div>
    <div class="session-body">
      <div class="section-title">What We Cover</div>
      <ul class="topics-list">
        <li>What is Data Analytics?</li>
        <li>Career opportunities in data</li>
        <li>Data Analyst vs Business Analyst vs BI Analyst</li>
        <li>The data ecosystem</li>
        <li>How to build a data portfolio</li>
      </ul>
      <div class="section-title">Activity</div>
      <div class="activity-box">Round-robin introductions &mdash; every participant shares their background, their career goal, and why they're in the room today.</div>
      <div class="section-title">Outcome</div>
      <p class="outcome-text">Participants understand where data skills can take them &mdash; and where they currently stand on that map.</p>
      <div class="deliverable-box">
        <div class="del-label">Take-Home Canvas 1 &middot; Career Compass</div>
        <p>Plot your current starting point, your target data role, and the one skill gap to close first.</p>
      </div>
    </div>
  </div>

  <!-- SESSION 2 -->
  <div class="session-card sc-discover">
    <div class="session-header">
      <div class="session-number">Session 02 &middot; 9:45 &ndash; 10:45 AM</div>
      <div class="lens-tag">Question Translator</div>
    </div>
    <div class="session-title">Understanding Data</div>
    <div class="session-divider"></div>
    <div class="session-body">
      <div class="section-title">What We Cover</div>
      <ul class="topics-list">
        <li>Types of data</li>
        <li>Structured vs unstructured data</li>
        <li>The data analytics process</li>
        <li>Business questions vs data questions</li>
      </ul>
      <div class="section-title">Group Activity</div>
      <div class="activity-box">Scenario: <strong>a supermarket wants to increase revenue.</strong> In small groups &mdash; what questions should management ask, and what data would you need to answer them?</div>
      <div class="section-title">Outcome</div>
      <p class="outcome-text">Participants learn to think analytically: translating a business goal into the data questions that can actually be investigated.</p>
      <div class="speed-pill">&#9889; Speed Coaching &middot; Final 10 Minutes</div>
      <div class="deliverable-box">
        <div class="del-label">Take-Home Canvas 2 &middot; Question Translator</div>
        <p>Convert 3 real questions from your own work, business, or industry into data questions you could investigate.</p>
      </div>
    </div>
  </div>

</div>

<!-- TEA BREAK -->
<div class="break-band">
  <div class="break-time">Tea Break &middot; 10:45 &ndash; 11:00 AM</div>
  <div class="break-divider"></div>
  <div class="break-content">
    <div class="break-label">Peer Reflection Circle</div>
    <div class="break-note">In pairs or trios, swap Canvas 1 &amp; 2 and give each other one piece of feedback &mdash; one thing that's clear, and one question to sharpen.</div>
  </div>
</div>

<!-- PHASE 2: ANALYZE -->
<div class="phase-divider phase-analyze">
  <div class="phase-label">Phase 2 &nbsp; Analyze</div>
  <div class="phase-line"></div>
  <div class="phase-days">Session 3 &nbsp;&bull;&nbsp; 11:00 AM &ndash; 12:30 PM</div>
</div>

<div class="sessions-grid single">

  <!-- SESSION 3 -->
  <div class="session-card sc-analyze single">
    <div class="session-header">
      <div class="session-number">Session 03 &middot; 11:00 AM &ndash; 12:30 PM</div>
      <div class="lens-tag">First Insight Sprint</div>
    </div>
    <div class="session-title">Excel for Data Analysis</div>
    <div class="session-divider"></div>
    <div class="session-body">
      <div>
        <div class="section-title">What We Cover</div>
        <ul class="topics-list">
          <li>Data cleaning</li>
          <li>Sorting &amp; filtering</li>
        </ul>
        <div class="func-tags">
          <span class="func-tag">IF</span>
          <span class="func-tag">SUMIF</span>
          <span class="func-tag">VLOOKUP</span>
          <span class="func-tag">Pivot Tables</span>
        </div>
        <div class="section-title">Hands-On Exercise</div>
        <div class="activity-box">Analyze a real sales dataset and answer: which product earns the most revenue, which month performs best, and who is the top salesperson?</div>
      </div>
      <div>
        <div class="section-title">Outcome</div>
        <p class="outcome-text">Participants complete their first real analysis &mdash; start to finish, on their own, with answers they can defend.</p>
        <div class="speed-pill">&#9889; Speed Coaching &middot; Final 10 Minutes</div>
        <div class="deliverable-box">
          <div class="del-label">Take-Home Canvas 3 &middot; First Insight Card</div>
          <p>Write down your single most surprising finding from the sales data, and one action a manager could take because of it.</p>
        </div>
      </div>
    </div>
  </div>

</div>

<!-- LUNCH BREAK -->
<div class="break-band">
  <div class="break-time">Lunch Break &middot; 12:30 &ndash; 1:30 PM</div>
  <div class="break-divider"></div>
  <div class="break-content">
    <div class="break-label">Peer Reflection Circle</div>
    <div class="break-note">In small groups, each participant shares their First Insight Card finding in under a minute &mdash; practicing the pitch before the afternoon's dashboard work.</div>
  </div>
</div>

<!-- PHASE 3: TELL -->
<div class="phase-divider phase-tell">
  <div class="phase-label">Phase 3 &nbsp; Tell</div>
  <div class="phase-line"></div>
  <div class="phase-days">Sessions 4 &ndash; 5 &nbsp;&bull;&nbsp; 1:30 &ndash; 3:45 PM</div>
</div>

<div class="sessions-grid">

  <!-- SESSION 4 -->
  <div class="session-card sc-tell">
    <div class="session-header">
      <div class="session-number">Session 04 &middot; 1:30 &ndash; 2:45 PM</div>
      <div class="lens-tag">Data Story Canvas</div>
    </div>
    <div class="session-title">Dashboard Building</div>
    <div class="session-divider"></div>
    <div class="session-body">
      <div class="section-title">What We Cover</div>
      <ul class="topics-list">
        <li>Charts</li>
        <li>KPI cards</li>
        <li>Dashboard design</li>
        <li>Storytelling with data</li>
      </ul>
      <div class="section-title">Activity</div>
      <div class="activity-box">As a group, build a mini dashboard live from the Session 3 dataset &mdash; choosing the charts and KPIs that tell the clearest story.</div>
      <div class="section-title">Outcome</div>
      <p class="outcome-text">Participants create a dashboard they can screenshot and share immediately.</p>
      <div class="speed-pill">&#9889; Speed Coaching &middot; Final 10 Minutes</div>
      <div class="deliverable-box">
        <div class="del-label">Take-Home Canvas 4 &middot; Data Story Canvas</div>
        <p>Sketch your dashboard's headline number, supporting chart, and one-sentence "so what" for a non-technical reader.</p>
      </div>
    </div>
  </div>

  <!-- SESSION 5 -->
  <div class="session-card sc-tell">
    <div class="session-header">
      <div class="session-number">Session 05 &middot; 2:45 &ndash; 3:45 PM</div>
      <div class="lens-tag">Scale-Up Walkthrough</div>
    </div>
    <div class="session-title">Power BI Demonstration</div>
    <div class="session-divider"></div>
    <div class="session-body">
      <div class="section-title">What We Cover</div>
      <ul class="topics-list">
        <li>Importing data</li>
        <li>Power Query</li>
        <li>Visualizations</li>
        <li>Interactive dashboards</li>
      </ul>
      <div class="section-title">Activity</div>
      <div class="activity-box">Watch the Session 3 &amp; 4 Excel analysis rebuilt live in Power BI &mdash; the same questions, the same answers, at business scale.</div>
      <div class="section-title">Outcome</div>
      <p class="outcome-text">Participants see how the skills they just practiced map directly onto the tools real businesses use to build interactive dashboards.</p>
    </div>
  </div>

</div>

<!-- BREAK / ENERGY RESET -->
<div class="break-band reset">
  <div class="break-time">Break &middot; 3:45 &ndash; 4:00 PM</div>
  <div class="break-divider"></div>
  <div class="break-content">
    <div class="break-label">Energy Reset</div>
    <div class="break-note">A 5-minute physical reset &mdash; stretch, music, or a quick movement game &mdash; to bring the room's energy back up before the day's biggest sprint.</div>
  </div>
</div>

<!-- PHASE 4: ACT -->
<div class="phase-divider phase-act">
  <div class="phase-label">Phase 4 &nbsp; Act</div>
  <div class="phase-line"></div>
  <div class="phase-days">Sessions 6 &ndash; 8 &nbsp;&bull;&nbsp; 4:00 &ndash; 6:00 PM</div>
</div>

<!-- SESSION 6: CAPSTONE -->
<div class="capstone-wrap">
  <div class="capstone-inner">
    <div class="capstone-header">
      <div class="session-number">Session 06 &middot; 4:00 &ndash; 4:45 PM</div>
      <div class="lens-tag">The Execution Sprint</div>
    </div>
    <h3>Business Challenge Competition</h3>
    <div class="capstone-body">
      <div>
        <h4>The Brief</h4>
        <ol class="brief-steps">
          <li>Clean the data</li>
          <li>Analyze the data</li>
          <li>Create visuals</li>
          <li>Present findings</li>
        </ol>
      </div>
      <div>
        <h4>Judged On</h4>
        <div class="judging-grid">
          <div class="judging-item">
            <div class="ji-label">Accuracy</div>
            <p>Are the numbers correct and the dataset genuinely cleaned?</p>
          </div>
          <div class="judging-item">
            <div class="ji-label">Insights</div>
            <p>Do the findings actually answer the brief?</p>
          </div>
          <div class="judging-item">
            <div class="ji-label">Creativity</div>
            <p>Is the approach original, sharp, or memorable?</p>
          </div>
          <div class="judging-item">
            <div class="ji-label">Presentation</div>
            <p>Is it clear, confident, and well-structured?</p>
          </div>
        </div>
      </div>
    </div>
    <p class="capstone-outcome">Outcome: participants apply everything from the day under real time pressure &mdash; teams receive a fresh dataset and have 45 minutes to clean it, analyze it, visualize it, and defend their thinking in front of the room.</p>
  </div>
</div>

<div class="sessions-grid last">

  <!-- SESSION 7 -->
  <div class="session-card sc-act">
    <div class="session-header">
      <div class="session-number">Session 07 &middot; 4:45 &ndash; 5:15 PM</div>
      <div class="lens-tag">90-Day Portfolio Pathway</div>
    </div>
    <div class="session-title">Career Launch Session</div>
    <div class="session-divider"></div>
    <div class="session-body">
      <div class="section-title">What We Cover</div>
      <ul class="topics-list">
        <li>How to build a portfolio</li>
        <li>GitHub introduction</li>
        <li>LinkedIn optimization</li>
        <li>Freelancing opportunities</li>
        <li>The Data Foundation learning path</li>
      </ul>
      <div class="section-title">Outcome</div>
      <p class="outcome-text">Participants leave knowing exactly what to do in the next 24 hours, the next week, and the next 90 days.</p>
      <div class="deliverable-box">
        <div class="del-label">Take-Home Canvas 5 &middot; My Next 90 Days</div>
        <p>Three concrete actions &mdash; with dates &mdash; for your 30-, 60-, and 90-day milestones after today.</p>
      </div>
    </div>
  </div>

  <!-- GRADUATION -->
  <div class="session-card sc-act">
    <div class="session-header">
      <div class="session-number">Graduation &amp; Closing &middot; 5:15 &ndash; 6:00 PM</div>
      <div class="lens-tag">Community Circle</div>
    </div>
    <div class="session-title">Graduation &amp; Networking</div>
    <div class="session-divider"></div>
    <div class="session-body">
      <div class="section-title">Activities</div>
      <ul class="topics-list">
        <li>Certificates</li>
        <li>Photos</li>
        <li>Open networking</li>
        <li>Community introduction</li>
        <li>Registration for the full Data Foundation Class</li>
      </ul>
      <div class="section-title">Outcome</div>
      <p class="outcome-text">Participants close the day connected to each other, to the wider community, and to a clear next step.</p>
    </div>
  </div>

</div>

<!-- TRAINER IMPLEMENTATION GUIDELINES -->
<div class="guidelines-section">
  <h2>Trainer Implementation Guidelines</h2>
  <p class="sub">Six practical habits that turn this outline into the experience described on the cover &mdash; tested for an intensive, full-day physical room.</p>
  <div class="guidelines-grid">
    <div class="guideline-card">
      <div class="gc-num">01</div>
      <h4>Speed Coaching Intervals</h4>
      <p>Reserve the final 10 minutes of Sessions 2, 3, and 4 for rapid-fire feedback. Walk the room, glance at one worksheet per group, and give one specific correction or one specific win &mdash; out loud, in seconds, not paragraphs.</p>
    </div>
    <div class="guideline-card">
      <div class="gc-num">02</div>
      <h4>The Bootcamp Workbook</h4>
      <p>Print the five take-home canvases as a single bound booklet, handed out at registration. Participants fill it in across the day; by 6:00 PM it's a finished artifact, not a stack of loose handouts.</p>
    </div>
    <div class="guideline-card">
      <div class="gc-num">03</div>
      <h4>Peer Reflection Circles</h4>
      <p>Use both the tea break and lunch break for 3&ndash;4 person reflection circles, each with one simple prompt. Breaks become part of the curriculum, not a pause from it.</p>
    </div>
    <div class="guideline-card">
      <div class="gc-num">04</div>
      <h4>The Energy Reset</h4>
      <p>Before Session 6, lead a 5-minute physical reset &mdash; stretch, music, or a quick movement game. The room's energy at 4:00 PM decides how the final sprint goes.</p>
    </div>
    <div class="guideline-card">
      <div class="gc-num">05</div>
      <h4>Facilitator Ratio</h4>
      <p>Aim for one facilitator or assistant per 8&ndash;10 participants during Sessions 3, 4, and 6. No one should be stuck on a formula or a chart for more than two minutes.</p>
    </div>
    <div class="guideline-card">
      <div class="gc-num">06</div>
      <h4>Room &amp; Pod Setup</h4>
      <p>Seat participants in pods of 4&ndash;6 from the start, and keep those pods consistent through the Session 6 challenge. Today's pod becomes tomorrow's network.</p>
    </div>
  </div>
</div>

<!-- OUTCOMES -->
<div class="outcomes2-section">
  <h2>What Participants Leave With</h2>
  <div class="outcomes-cols">
    <div class="outcome-col tangible">
      <h3>Tangible Outcomes</h3>
      <ul>
        <li>A cleaned, analyzed sales dataset</li>
        <li>A completed Excel dashboard</li>
        <li>A Power BI walkthrough file</li>
        <li>A 5-canvas Bootcamp Workbook</li>
        <li>A digital resource pack</li>
        <li>A Certificate of Completion</li>
      </ul>
    </div>
    <div class="outcome-col intangible">
      <h3>Intangible Outcomes</h3>
      <ul>
        <li>Career clarity on the data analyst pathway</li>
        <li>Confidence using core Excel formulas under time pressure</li>
        <li>A new peer network from the cohort</li>
        <li>A working mental model of the full analytics process</li>
        <li>First-hand experience presenting findings live</li>
      </ul>
    </div>
  </div>
</div>

<!-- PATHWAY -->
<div class="pathway-section">
  <h2>Where This Leads</h2>
  <p class="sub">Today is the spark. The Data Foundation Class is where it becomes a career move.</p>
  <div class="pathway-grid">
    <div class="pathway-card">
      <div class="pc-label">Today</div>
      <h4>The One-Day Bootcamp</h4>
      <ul>
        <li>8 sessions across 1 day</li>
        <li>1 completed analysis + dashboard</li>
        <li>5-canvas Bootcamp Workbook</li>
        <li>A certificate and a cohort</li>
      </ul>
    </div>
    <div class="pathway-arrow">&rarr;</div>
    <div class="pathway-card">
      <div class="pc-label">Next</div>
      <h4>The Data Foundation Class</h4>
      <ul>
        <li>8 sessions across 4 weekends</li>
        <li>2 portfolio projects &mdash; Excel &amp; Power BI, or SQL &amp; Python</li>
        <li>A GitHub repo and a LinkedIn post</li>
        <li>A career roadmap, certificate &amp; community access</li>
      </ul>
    </div>
  </div>
  <div class="pathway-quote">
    "Today was an introduction. The full Data Foundation Class helps you master Excel &amp; Power BI or SQL &amp; Python, build portfolio projects, and become job-ready."
    <span class="pq-attr">The conversion message &middot; shared at graduation</span>
  </div>
</div>

<!-- FOOTER -->
<div class="footer">
  <div class="footer-brand">The Digital College &nbsp;<span>/</span>&nbsp; Data with Miss Mailiana</div>
  <div class="footer-note">One-Day In-Person Bootcamp &nbsp;&bull;&nbsp; The Data Foundation Class</div>
</div>

</body>
</html>
