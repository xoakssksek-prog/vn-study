[index.html](https://github.com/user-attachments/files/33954951/index.html)
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="베트남어공부">
    <link rel="apple-touch-icon" href="https://cdn-icons-png.flaticon.com/512/197/197473.png">
    
    <title>태만&명희의 프리미엄 베트남어</title>
    
    <style>
        :root {
            --bg-deep: #020617;
            --bg-card: rgba(15, 23, 42, 0.8);
            --accent-gold: #fbbf24;
            --accent-green: #10b981;
            --accent-red: #f43f5e;
            --text-main: #ffffff;
            --text-dim: #cbd5e1;
            --glass-border: rgba(255, 255, 255, 0.08);
        }

        html, body { height: 100%; margin: 0; padding: 0; overflow: hidden; background-color: var(--bg-deep); font-family: -apple-system, sans-serif; user-select: none; -webkit-user-select: none; }
        body { text-align: center; color: var(--text-main); display: flex; flex-direction: column; }
        
        .card { 
            background: var(--bg-deep);
            background-image: radial-gradient(circle at top, #1e293b 0%, #020617 100%);
            width: 100%; height: 100dvh; padding: 24px; box-sizing: border-box; 
            display: flex; flex-direction: column; justify-content: space-between; 
        }

        .content-wrap { flex: 1; display: flex; flex-direction: column; justify-content: center; width: 100%; }
        
        .star-btn { background: none !important; border: none !important; outline: none !important; font-size: 42px; color: rgba(255,255,255,0.15); cursor: pointer; transition: all 0.3s; }
        .star-btn.active { color: var(--accent-gold); filter: drop-shadow(0 0 12px rgba(251, 191, 36, 0.5)); }

        .vn { font-weight: 800; color: var(--accent-green); margin-bottom: 10px; word-break: break-word; line-height: 1.1; letter-spacing: -0.03em; text-shadow: 0 0 15px rgba(16, 185, 129, 0.3); }
        .pron { font-size: 22px; color: var(--accent-gold); margin-bottom: 10px; opacity: 0.8; }
        .kr { font-size: 26px; font-weight: 600; color: #fff; margin-bottom: 15px; }
        
        .ex-box { background: rgba(0,0,0,0.25); padding: 20px; border-radius: 20px; border: 1px solid var(--glass-border); margin-top: 10px; }
        .ex-vn { color: var(--accent-green); font-weight: 600; font-size: 22px; line-height: 1.3; }
        .ex-pron { font-size: 16px; color: var(--accent-gold); margin-top: 5px; }
        .ex-kr { font-size: 16px; color: var(--text-dim); margin-top: 5px; }
        
        .arrow-btn { background: none; border: none; color: rgba(255, 255, 255, 0.1); font-size: 50px; cursor: pointer; padding: 0 10px; }
        .arrow-btn:active { color: var(--accent-green); }

        .bottom-controls { width: 100%; padding-bottom: 15px; }
        .play-btn { height: 65px; width: 100%; border-radius: 18px; border: none; font-size: 24px; font-weight: 900; background: linear-gradient(135deg, #f43f5e, #be123c); color: white; margin-bottom: 12px; box-shadow: 0 8px 20px rgba(244, 63, 94, 0.3); cursor: pointer; letter-spacing: 0.15em; }

        .row { display: flex; gap: 10px; margin-bottom: 10px; }
        .row-btn { flex: 1; height: 55px; border-radius: 15px; border: none; font-size: 14px; font-weight: 600; cursor: pointer; display: flex; align-items: center; justify-content: center; }
        .btn-gold { background: linear-gradient(135deg, #fbbf24, #d97706); color: #451a03; }
        .btn-outline { background: rgba(255,255,255,0.05); color: #fff; border: 1px solid var(--glass-border); }
        .sheet-select { background: #0f172a; color: var(--accent-green); border: 1px solid var(--accent-green); text-align-last: center; appearance: none; }

        .quick-settings { display: flex; justify-content: space-around; padding: 12px; background: rgba(255,255,255,0.03); border-radius: 15px; font-size: 14px; margin-bottom: 10px; }
        .quick-settings label { display: flex; align-items: center; gap: 6px; color: var(--text-dim); cursor: pointer; }

        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.95); z-index: 100; padding-top: 20px; overflow-y: auto; }
        .modal-content { background: #0f172a; margin: 10px auto; width: 94%; max-width: 480px; border-radius: 24px; padding: 20px; border: 1px solid var(--glass-border); text-align: left; }
        .modal-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; color: white; }
        .close-btn { background: var(--accent-red); color: white; border: none; padding: 8px 16px; border-radius: 10px; cursor: pointer; }

        #blackoutOverlay { background: #000; position: fixed; top:0; left:0; width:100%; height:100%; z-index:9999; display:none; flex-direction:column; justify-content:center; align-items:center; cursor:pointer; }

        .cal-legend { display: flex; justify-content: center; align-items: center; gap: 12px; margin-bottom: 15px; font-size: 9px; color: #94a3b8; font-weight: 300; letter-spacing: -0.01em; opacity: 0.8; }
        .cal-grid { display: grid; grid-template-columns: repeat(7, 1fr); gap: 4px; background: rgba(0,0,0,0.2); padding: 8px; border-radius: 12px; }
        .cal-day { background: rgba(255,255,255,0.03); border-radius: 6px; aspect-ratio: 1/1; display: flex; flex-direction: column; align-items: center; justify-content: center; position: relative; min-height: 40px; font-size: 11px; color: white; }
        .cal-time { font-size: 9px; color: #ffffff; margin-top: 3px; font-weight: 400; letter-spacing: -0.01em; }

        .report-bar-container { display: flex; align-items: flex-end; justify-content: space-around; height: 100px; background: rgba(0,0,0,0.3); padding: 25px 10px 5px 10px; border-radius: 12px; margin-top: 20px; }
        .bar-wrapper { display: flex; flex-direction: column; align-items: center; gap: 5px; flex: 1; position: relative; }
        .bar-time-label { position: absolute; top: -20px; width: 100%; text-align: center; font-size: 9.5px; color: #ffffff; font-weight: bold; }
        .report-bar { width: 14px; background: var(--accent-green); border-radius: 4px 4px 0 0; min-height: 2px; }

        .stats-panel { background: rgba(255,255,255,0.02); border-radius: 18px; padding: 15px; margin-top: 15px; border: 1px solid var(--glass-border); }
        .stats-row { display: flex; justify-content: space-between; align-items: center; padding: 8px 5px; font-size: 13px; }
        .stats-label { color: var(--text-dim); font-weight: 300; }
        .stats-value { color: var(--accent-gold); font-weight: 600; font-size: 14px; }

        .comp-table-header { display: flex; padding: 12px 5px; border-bottom: 1.5px solid var(--accent-green); font-size: 11px; color: var(--accent-green); font-weight: 800; text-align: left; }
        .comp-row { display: flex; align-items: flex-start; padding: 12px 5px; border-bottom: 1px solid rgba(255,255,255,0.05); font-size: 12px; line-height: 1.4; }
        
        .c-vn { flex: 1; color: var(--accent-green); font-weight: bold; word-break: break-all; padding-right: 5px; }
        .c-pron { flex: 0.8; color: var(--accent-gold); word-break: break-all; padding-right: 5px; }
        .c-mean { flex: 1.2; color: #fff; word-break: keep-all; overflow-wrap: break-word; }
        .c-hit { width: 45px; text-align: center; font-size: 10px; color: var(--text-dim); font-weight: 300; }
        .c-del { width: 40px; text-align: right; }

        #noticeToast { display: none; position: fixed; top: 15%; left: 50%; transform: translateX(-50%); background: rgba(30, 41, 59, 0.9); backdrop-filter: blur(10px); -webkit-backdrop-filter: blur(10px); color: #e2e8f0; padding: 18px 28px; border-radius: 20px; font-size: 14px; font-weight: 300; z-index: 11000; box-shadow: 0 10px 30px rgba(0,0,0,0.5); width: 85%; max-width: 340px; text-align: center; pointer-events: none; line-height: 1.6; border: 1px solid rgba(255,255,255,0.1); }

        .count-ctrl-btn { background: var(--accent-green); color: #000; border: none; width: 28px; height: 28px; border-radius: 6px; font-weight: bold; cursor: pointer; display: flex; align-items: center; justify-content: center; }
        .vol-slider { -webkit-appearance: none; width: 120px; height: 4px; background: rgba(255,255,255,0.1); border-radius: 5px; outline: none; }
        .vol-slider::-webkit-slider-thumb { -webkit-appearance: none; width: 16px; height: 16px; background: var(--accent-gold); border-radius: 50%; cursor: pointer; box-shadow: 0 0 10px rgba(251, 191, 36, 0.5); }
        
        .pc-bar-container { display: flex; align-items: center; justify-content: space-between; width: 100%; height: 100dvh; background: #0f172a; padding: 0 15px; box-sizing: border-box; border-top: 2px solid var(--accent-green); }
        .pc-side-group { display: flex; align-items: center; gap: 8px; flex-shrink: 0; }
        .pc-content-area { display: flex; align-items: center; justify-content: center; flex: 1; overflow: hidden; }
        .pc-text-group { display: flex; align-items: center; gap: 10px; overflow: hidden; white-space: nowrap; padding: 0 15px; cursor: pointer; }
        
        .pc-vn { color: var(--accent-green); font-weight: 800; font-size: 20px; }
        .pc-pron { color: var(--accent-gold); font-size: 15px; font-weight: bold; opacity: 0.9; }
        .pc-kr { color: #fff; font-size: 16px; font-weight: bold; }
        .pc-ex { color: var(--accent-green); font-size: 18px; margin-left: 10px; border-left: 2px solid rgba(255,255,255,0.1); padding-left: 10px; font-weight: bold; opacity: 0.9; }
        .pc-ex-pron { color: var(--accent-gold); font-size: 14px; font-weight: bold; opacity: 0.9; }
        .pc-ex-kr { color: var(--text-dim); font-size: 15px; }

        .pc-btn { border: none; border-radius: 6px; padding: 8px 14px; cursor: pointer; font-weight: bold; font-size: 12px; transition: 0.2s; white-space: nowrap; }
        .pc-btn.start { background: var(--accent-green); color: #000; }
        .pc-btn.stop { background: var(--accent-red); color: #fff; }
        .pc-btn.mode { background: rgba(255,255,255,0.05); color: #cbd5e1; border: 1px solid rgba(255,255,255,0.1); }
        .pc-btn.hide { background: var(--accent-gold); color: #451a03; }
        .pc-nav-btn { background: none; border: none; color: var(--accent-gold); font-size: 28px; font-weight: bold; cursor: pointer; padding: 0 15px; opacity: 0.5; transition: 0.3s; }
        .pc-nav-btn:hover { opacity: 1; transform: scale(1.2); }

        .cheer-box { background: rgba(251, 191, 36, 0.1); border: 1px dashed var(--accent-gold); padding: 12px; border-radius: 15px; text-align: center; margin-bottom: 15px; color: var(--accent-gold); font-size: 14px; font-weight: 800; line-height: 1.4; }
        /* COURSE:CSS START */
        /* ---- 학습 코스 (오늘 메뉴) ---- */
        .top-pills { display: flex; justify-content: center; align-items: center; gap: 8px; flex-wrap: wrap; margin: 0 auto 10px; }
        .course-pill { cursor: pointer; padding: 6px 13px; border-radius: 20px; font-size: 12px; font-weight: 700; color: #fff; background: linear-gradient(135deg, rgba(244, 63, 94, 0.35), rgba(251, 191, 36, 0.25)); border: 1px solid rgba(251, 191, 36, 0.45); }
        .lv-chip { font-size: 11px; color: #94a3b8; margin-bottom: 4px; letter-spacing: 0.02em; }
        .ex-lit { font-size: 13px; color: #94a3b8; margin-top: 10px; line-height: 1.45; }
        .ex-lit b { color: #cbd5e1; font-weight: 600; }
        .ex-why { font-size: 13px; color: #fcd34d; margin-top: 6px; line-height: 1.5; text-align: left; }
        .cs-card { background: rgba(255, 255, 255, 0.04); border: 1px solid var(--glass-border); border-radius: 16px; padding: 14px; margin-bottom: 12px; }
        .cs-lv { display: flex; justify-content: space-between; align-items: baseline; gap: 8px; flex-wrap: wrap; }
        .cs-lv h3 { margin: 0; font-size: 17px; color: #fff; }
        .cs-sub { font-size: 12px; color: #94a3b8; line-height: 1.5; }
        .cs-bar { height: 8px; border-radius: 6px; background: rgba(255, 255, 255, 0.08); overflow: hidden; margin: 10px 0 6px; }
        .cs-bar > div { height: 100%; background: linear-gradient(90deg, var(--accent-green), var(--accent-gold)); border-radius: 6px; }
        .cs-h { font-size: 12px; font-weight: 800; letter-spacing: 0.06em; color: #94a3b8; margin: 2px 0 8px; }
        .cs-mission { display: flex; align-items: center; gap: 10px; padding: 9px 0; border-top: 1px solid rgba(255, 255, 255, 0.05); font-size: 14px; color: #e2e8f0; }
        .cs-h + .cs-mission { border-top: none; }
        .cs-check { width: 22px; height: 22px; border-radius: 50%; border: 2px solid rgba(255, 255, 255, 0.2); display: flex; align-items: center; justify-content: center; font-size: 12px; flex-shrink: 0; }
        .cs-check.on { background: var(--accent-green); border-color: var(--accent-green); color: #022c22; font-weight: 900; }
        .cs-btns { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
        .cs-btn { min-height: 56px; border-radius: 14px; border: 1px solid var(--glass-border); background: rgba(255, 255, 255, 0.05); color: #fff; font-weight: 700; font-size: 14px; cursor: pointer; padding: 8px; line-height: 1.25; }
        .cs-btn small { display: block; font-weight: 400; font-size: 11px; color: #94a3b8; margin-top: 3px; }
        .cs-btn.hot { background: linear-gradient(135deg, #f43f5e, #be123c); border-color: transparent; }
        .cs-btn.green { background: linear-gradient(135deg, #10b981, #047857); border-color: transparent; }
        .cs-btn.gold { background: linear-gradient(135deg, #fbbf24, #d97706); color: #451a03; border-color: transparent; }
        .cs-btn.hot small, .cs-btn.green small { color: rgba(255, 255, 255, 0.85); }
        .cs-btn.gold small { color: #78350f; }
        .cs-chips { display: flex; flex-wrap: wrap; gap: 6px; }
        .cs-chip { min-width: 40px; padding: 7px 10px; border-radius: 10px; border: 1px solid var(--glass-border); background: rgba(255, 255, 255, 0.04); color: #cbd5e1; font-size: 13px; font-weight: 700; cursor: pointer; }
        .cs-chip.on { background: var(--accent-green); color: #022c22; border-color: var(--accent-green); }
        .cs-chip:disabled { opacity: 0.35; cursor: not-allowed; }
        .cs-list { font-size: 13px; color: #cbd5e1; max-height: 170px; overflow-y: auto; }
        .cs-list div { display: flex; justify-content: space-between; gap: 10px; padding: 5px 0; border-top: 1px solid rgba(255, 255, 255, 0.04); }
        .cs-list span:first-child { color: var(--accent-green); font-weight: 700; }
        .cs-list span:last-child { text-align: right; }
        .cs-link { background: none; border: none; color: #94a3b8; font-size: 12px; text-decoration: underline; cursor: pointer; padding: 6px 0; }
        .cs-btn:focus-visible, .cs-chip:focus-visible, .bt-opt:focus-visible, .bt-tile:focus-visible, .bt-next:focus-visible, .course-pill:focus-visible { outline: 2px solid var(--accent-gold); outline-offset: 2px; }

        /* ---- ⚔️ 전투 퀴즈 ---- */
        .bt { display: none; position: fixed; top: 0; left: 0; right: 0; bottom: 0; z-index: 200; background: radial-gradient(circle at 50% 0%, #312e81 0%, #0f172a 45%, #020617 100%); overflow-y: auto; color: #fff; text-align: center; }
        .bt-inner { max-width: 520px; margin: 0 auto; min-height: 100%; display: flex; flex-direction: column; padding: calc(env(safe-area-inset-top, 0px) + 12px) 16px calc(env(safe-area-inset-bottom, 0px) + 24px); box-sizing: border-box; gap: 12px; }
        .bt-top { display: flex; align-items: center; justify-content: space-between; gap: 8px; }
        .bt-x { background: rgba(255, 255, 255, 0.08); border: none; color: #fff; width: 38px; height: 38px; border-radius: 10px; font-size: 16px; cursor: pointer; flex-shrink: 0; }
        .bt-title { font-size: 13px; font-weight: 800; color: #fcd34d; letter-spacing: 0.04em; }
        .bt-hearts { font-size: 15px; min-width: 38px; text-align: right; letter-spacing: 1px; white-space: nowrap; }
        .bt-arena { display: flex; flex-direction: column; align-items: center; gap: 6px; }
        .bt-mon { font-size: 60px; line-height: 1.1; filter: drop-shadow(0 6px 18px rgba(244, 63, 94, 0.35)); }
        .bt-mon.hit { animation: bt-hit 0.35s; }
        .bt-mon.dead { animation: bt-dead 0.6s forwards; }
        .bt-hp { width: 70%; max-width: 280px; height: 10px; border-radius: 6px; background: rgba(255, 255, 255, 0.1); overflow: hidden; }
        .bt-hp-fill { height: 100%; width: 100%; background: linear-gradient(90deg, #f43f5e, #fb923c); transition: width 0.3s; }
        .bt-meta { font-size: 12px; color: #cbd5e1; font-variant-numeric: tabular-nums; }
        .bt-combo { color: #fb923c; font-weight: 800; }
        .bt-q { background: rgba(15, 23, 42, 0.88); border: 1px solid rgba(255, 255, 255, 0.08); border-radius: 20px; padding: 16px; display: flex; flex-direction: column; gap: 12px; }
        .bt-kind { font-size: 11px; font-weight: 800; letter-spacing: 0.08em; color: #a5b4fc; }
        .bt-prompt { font-size: 32px; font-weight: 800; color: var(--accent-green); line-height: 1.2; word-break: keep-all; overflow-wrap: anywhere; }
        .bt-prompt.kr { color: #fff; font-size: 26px; }
        .bt-prompt.sent { font-size: 21px; color: #fff; line-height: 1.45; }
        .bt-hint { font-size: 13px; color: #94a3b8; line-height: 1.5; }
        .bt-opts { display: grid; gap: 8px; }
        .bt-opt { min-height: 52px; border-radius: 14px; border: 1px solid rgba(255, 255, 255, 0.12); background: rgba(255, 255, 255, 0.06); color: #fff; font-size: 17px; font-weight: 600; cursor: pointer; padding: 10px 12px; line-height: 1.3; display: flex; align-items: center; gap: 10px; text-align: left; }
        .bt-num { flex-shrink: 0; width: 24px; height: 24px; border-radius: 7px; background: rgba(255, 255, 255, 0.1); color: #cbd5e1; font-size: 12px; font-weight: 800; display: inline-flex; align-items: center; justify-content: center; }
        .bt-opt.ok { background: rgba(16, 185, 129, 0.25); border-color: var(--accent-green); }
        .bt-opt.no { background: rgba(244, 63, 94, 0.25); border-color: var(--accent-red); }
        .bt-opt.sel { border-color: var(--accent-gold); background: rgba(251, 191, 36, 0.18); }
        .bt-opt.done { opacity: 0.4; }
        .bt-opt.go { background: rgba(16, 185, 129, 0.25); border-color: rgba(16, 185, 129, 0.6); justify-content: center; }
        .bt-opt:disabled { cursor: default; }
        .bt-row .bt-opt { justify-content: center; }
        .bt-say { align-self: center; background: rgba(99, 102, 241, 0.25); border: 1px solid rgba(165, 180, 252, 0.4); color: #e0e7ff; border-radius: 999px; padding: 9px 18px; font-size: 15px; font-weight: 700; cursor: pointer; }
        .bt-say.big { font-size: 40px; padding: 14px 28px; }
        .bt-match { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
        .bt-match .bt-opt { font-size: 15px; min-height: 50px; padding: 8px 10px; min-width: 0; overflow-wrap: anywhere; }
        .bt-slots { min-height: 58px; display: flex; flex-wrap: wrap; gap: 6px; justify-content: center; align-content: flex-start; padding: 10px; border-radius: 14px; border: 1px dashed rgba(255, 255, 255, 0.25); }
        .bt-pool { display: flex; flex-wrap: wrap; gap: 6px; justify-content: center; }
        .bt-tile { border-radius: 10px; border: 1px solid rgba(255, 255, 255, 0.18); background: rgba(255, 255, 255, 0.09); color: #fff; font-size: 17px; font-weight: 700; padding: 9px 12px; cursor: pointer; }
        .bt-tile.used { visibility: hidden; }
        .bt-row { display: flex; gap: 8px; }
        .bt-row > * { flex: 1; }
        .bt-fb-box { border-radius: 18px; padding: 14px; text-align: left; display: flex; flex-direction: column; gap: 6px; animation: bt-pop 0.2s; }
        .bt-fb-box.ok { background: rgba(16, 185, 129, 0.14); border: 1px solid rgba(16, 185, 129, 0.5); }
        .bt-fb-box.no { background: rgba(244, 63, 94, 0.14); border: 1px solid rgba(244, 63, 94, 0.5); }
        .bt-fb-title { font-size: 16px; font-weight: 800; }
        .bt-fb-vn { font-size: 19px; font-weight: 800; color: var(--accent-green); }
        .bt-fb-pron { font-size: 13px; color: var(--accent-gold); font-weight: 600; }
        .bt-fb-line { font-size: 14px; color: #e2e8f0; line-height: 1.5; }
        .bt-fb-line.dim { color: #94a3b8; }
        .bt-fb-line.why { color: #fcd34d; }
        .bt-next { margin-top: 6px; min-height: 50px; border-radius: 14px; border: none; background: linear-gradient(135deg, #10b981, #047857); color: #fff; font-size: 16px; font-weight: 800; cursor: pointer; }
        .bt-next.ghost { background: rgba(255, 255, 255, 0.1); }
        .bt-result { display: flex; flex-direction: column; gap: 12px; }
        .bt-result h2 { margin: 0; font-size: 28px; }
        .bt-stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; }
        .bt-stat { background: rgba(255, 255, 255, 0.06); border-radius: 14px; padding: 10px 4px; }
        .bt-stat b { display: block; font-size: 21px; color: var(--accent-gold); font-variant-numeric: tabular-nums; }
        .bt-stat span { font-size: 11px; color: #94a3b8; }
        .bt.shake .bt-q { animation: bt-shake 0.35s; }
        @keyframes bt-hit { 0% { transform: none; } 30% { transform: translateX(-8px) scale(0.9); } 60% { transform: translateX(8px); } 100% { transform: none; } }
        @keyframes bt-dead { to { transform: scale(0.2) rotate(40deg); opacity: 0; } }
        @keyframes bt-shake { 0%, 100% { transform: none; } 25% { transform: translateX(-6px); } 75% { transform: translateX(6px); } }
        @keyframes bt-pop { from { transform: scale(0.97); opacity: 0.4; } to { transform: none; opacity: 1; } }
        @media (prefers-reduced-motion: reduce) { .bt-mon.hit, .bt-mon.dead, .bt.shake .bt-q, .bt-fb-box { animation: none; } }
        /* COURSE:CSS END */
    </style>
</head>
<body>

    <div id="noticeToast"></div>

    <div id="blackoutOverlay" onclick="toggleBlackout()">
        <p style="font-size: 20px; color: #1e293b; font-weight: bold;">LOW POWER MODE</p>
        <p style="font-size: 12px; color: #0f172a;">Touch to Wake</p>
    </div>

    <div id="app" style="height: 100%;"></div>

    <div id="listModal" class="modal">
        <div class="modal-content" style="max-width: 550px; height: 80vh; display: flex; flex-direction: column;">
            <div class="modal-header">
                <h3 style="margin:0; font-size:18px; color:var(--accent-gold);">전체 항목 리스트</h3>
                <button class="close-btn" onclick="closeListModal()">닫기</button>
            </div>
            
            <div style="background: rgba(255,255,255,0.05); padding: 12px; border-radius: 12px; margin-bottom: 10px; font-size: 14px;">
                <label style="color: var(--accent-gold); font-weight: bold; display: flex; align-items: center; gap: 8px; cursor: pointer;">
                    <input type="checkbox" id="rangeToggle" onchange="toggleRangeMode()" style="transform: scale(1.2);"> 🔄 지정 구간 반복 학습
                </label>
                <div id="rangeInputs" style="display:none; margin-top: 10px; align-items: center; gap: 8px;">
                    <input type="number" id="rangeStart" value="1" min="1" style="width: 60px; background: #020617; color: #fff; border: 1px solid var(--accent-green); border-radius: 6px; padding: 6px; text-align: center;"> <span style="color:#fff;">~</span>
                    <input type="number" id="rangeEnd" value="100" min="1" style="width: 60px; background: #020617; color: #fff; border: 1px solid var(--accent-green); border-radius: 6px; padding: 6px; text-align: center;"> 번
                    <button onclick="applyRange()" style="background: var(--accent-green); color: #000; border: none; padding: 6px 12px; border-radius: 6px; font-weight: bold; cursor: pointer; flex: 1;">구간 적용</button>
                </div>
            </div>
            <div id="listContainer" style="flex: 1; overflow-y: auto; background: rgba(0,0,0,0.2); border-radius: 12px; padding: 10px;"></div>
        </div>
    </div>

    <div id="settingsModal" class="modal">
        <div class="modal-content">
            <div id="cheerMessage" class="cheer-box">오늘 10분이 미래를 바꾼다</div>
            
            <div class="modal-header">
                <h2 style="color: var(--accent-green); margin:0; font-size: 20px;">SETTINGS (무료 모드)</h2>
                <button class="close-btn" onclick="closeSettings()">닫기</button>
            </div>
            <button class="btn-gold row-btn" style="width:100%; margin-bottom:15px;" onclick="openCalendar()">📊 학습 리포트 보기</button>
            <div style="background: rgba(255,255,255,0.03); padding: 15px; border-radius: 15px; margin-bottom: 15px;">
                
                <div style="margin-bottom: 18px; display:flex; justify-content:space-between; align-items:center; background: rgba(16, 185, 129, 0.15); padding: 12px; border-radius: 10px; border: 1px solid rgba(16, 185, 129, 0.4);">
                    <span style="color:var(--accent-green); font-weight:900; font-size: 14px;">🔇 사무실 무음 모드 (PC 보호)</span>
                    <input type="checkbox" id="muteModeToggle" style="transform: scale(1.3);" onchange="saveSettings(); notify(this, 'mute')">
                </div>

                <div style="margin-bottom: 18px; display:flex; justify-content:space-between; align-items:center;">
                    <span style="color:var(--accent-gold); font-weight:bold;">🔊 어플 단독 볼륨</span>
                    <div style="display:flex; align-items:center; gap:8px;">
                        <button class="count-ctrl-btn" onclick="adjustVolume('appVolume', -0.1)">-</button>
                        <input type="range" id="appVolume" class="vol-slider" min="0" max="1" step="0.1" onchange="saveSettings(); showNotice('🔊 볼륨이 조절되었습니다.')" style="width: 80px;">
                        <button class="count-ctrl-btn" onclick="adjustVolume('appVolume', 0.1)">+</button>
                    </div>
                </div>
                <div style="margin-bottom: 18px; display:flex; justify-content:space-between; align-items:center;">
                    <span style="color:var(--accent-gold); font-weight:bold;">🎵 수면 유도음 볼륨</span>
                    <div style="display:flex; align-items:center; gap:8px;">
                        <button class="count-ctrl-btn" onclick="adjustVolume('bgmVolume', -0.1)">-</button>
                        <input type="range" id="bgmVolume" class="vol-slider" min="0" max="1" step="0.1" onchange="saveSettings(); showNotice('🎵 수면 유도음 볼륨이 조절되었습니다.')" style="width: 80px;">
                        <button class="count-ctrl-btn" onclick="adjustVolume('bgmVolume', 0.1)">+</button>
                    </div>
                </div>

                <div style="margin-bottom: 15px; display:flex; justify-content:space-between; align-items:center;"><span style="color:var(--accent-red);">🔋 배터리 20% 보호</span><input type="checkbox" id="batteryProtect" onchange="saveSettings(); notify(this, 'battery')"></div>
                <div style="margin-bottom: 15px; display:flex; justify-content:space-between; align-items:center;"><span style="color:var(--accent-gold);">📉 점진적 볼륨 감소</span><input type="checkbox" id="fadeOutToggle" onchange="saveSettings(); notify(this, 'fade')"></div>
                
                <div style="margin-bottom: 10px; display:flex; justify-content:space-between; align-items:center;">
                    <span style="font-size: 13px;">🔁 본문 🇻🇳 반복</span>
                    <div style="display:flex; align-items:center; gap:10px;">
                        <button class="count-ctrl-btn" onclick="changeGlobalCount('wordVn', -1)">-</button>
                        <span id="wordVnCountDisplay" style="min-width:25px; text-align:center;">5</span>
                        <button class="count-ctrl-btn" onclick="changeGlobalCount('wordVn', 1)">+</button>
                    </div>
                </div>
                <div style="margin-bottom: 15px; display:flex; justify-content:space-between; align-items:center;">
                    <span style="font-size: 13px;">🔁 본문 🇰🇷 반복</span>
                    <div style="display:flex; align-items:center; gap:10px;">
                        <label style="font-size: 11px; color: var(--accent-gold); cursor:pointer;"><input type="checkbox" id="hideKrWord" onchange="saveSettings(); notify(this, 'krWord')"> KR OFF</label>
                        <button class="count-ctrl-btn" onclick="changeGlobalCount('wordKr', -1)">-</button>
                        <span id="wordKrCountDisplay" style="min-width:25px; text-align:center;">2</span>
                        <button class="count-ctrl-btn" onclick="changeGlobalCount('wordKr', 1)">+</button>
                    </div>
                </div>
                
                <div style="margin-bottom: 10px; display:flex; justify-content:space-between; align-items:center;">
                    <span style="font-size: 13px;">🔁 예문 🇻🇳 반복</span>
                    <div style="display:flex; align-items:center; gap:10px;">
                        <button class="count-ctrl-btn" onclick="changeGlobalCount('exVn', -1)">-</button>
                        <span id="exVnCountDisplay" style="min-width:25px; text-align:center;">1</span>
                        <button class="count-ctrl-btn" onclick="changeGlobalCount('exVn', 1)">+</button>
                    </div>
                </div>
                <div style="margin-bottom: 15px; display:flex; justify-content:space-between; align-items:center;">
                    <span style="font-size: 13px;">🔁 예문 🇰🇷 반복</span>
                    <div style="display:flex; align-items:center; gap:10px;">
                        <label style="font-size: 11px; color: var(--accent-gold); cursor:pointer;"><input type="checkbox" id="hideKrEx" onchange="saveSettings(); notify(this, 'krEx')"> KR OFF</label>
                        <button class="count-ctrl-btn" onclick="changeGlobalCount('exKr', -1)">-</button>
                        <span id="exKrCountDisplay" style="min-width:25px; text-align:center;">1</span>
                        <button class="count-ctrl-btn" onclick="changeGlobalCount('exKr', 1)">+</button>
                    </div>
                </div>
                <div style="margin-bottom: 15px; display:flex; justify-content:space-between; align-items:center;"><span>🔢 학습 횟수 기록</span><input type="checkbox" id="hitCountToggle" onchange="saveSettings(); notify(this, 'hit')"></div>
                <div style="margin-bottom: 15px; display:flex; justify-content:space-between; align-items:center;"><span>🌧️ 수면 유도음</span><select id="sleepSound" onchange="saveSettings(); if(isPlaying) playBackgroundSound();" style="background:#020617; color:#fff; border:none; padding:4px; border-radius:5px;"><option value="none">없음</option><option value="rain">빗소리</option><option value="ocean">파도 소리</option><option value="forest">숲 소리</option><option value="fire">장작 소리</option><option value="camping">캠핑장 소리</option></select></div>
                
                <div style="margin-bottom: 15px; display:flex; justify-content:space-between; align-items:center;"><span>⏰ 타이머</span><select id="sleepTimer" onchange="saveSettings()" style="background:#020617; color:#fff; border:none; padding:4px; border-radius:5px;"><option value="0">OFF</option><option value="60">60분</option><option value="120">120분</option><option value="240">240분</option><option value="300">300분</option><option value="360">360분</option><option value="420">420분</option><option value="480">480분</option><option value="540">540분</option></select></div>
                
                <div style="margin-bottom: 15px; display:flex; justify-content:space-between; align-items:center;"><span>⏳ 대기 시간</span><select id="delayTime" onchange="saveSettings(); showNotice('⏳ 대기 시간이 변경되었습니다.')" style="background:#020617; color:#fff; border:none; padding:4px; border-radius:5px;"><option value="0">없음</option><option value="1000">1초</option><option value="2000">2초</option><option value="3000">3초</option><option value="4000">4초</option><option value="5000">5초</option><option value="6000">6초</option><option value="7000">7초</option><option value="8000">8초</option><option value="9000">9초</option><option value="10000">10초</option></select></div>
                <div style="display:flex; justify-content:space-between; align-items:center;"><span>🗣️ 발음 속도</span><select id="voiceRate" onchange="saveSettings()" style="background:#020617; color:#fff; border:none; padding:4px; border-radius:5px;"><option value="0.6">느림</option><option value="0.9">표준</option><option value="1.3">빠름</option></select></div>
                <div style="display:flex; justify-content:space-between; align-items:center; gap:10px; margin-top:15px;"><span style="white-space:nowrap;">🇻🇳 베트남어 목소리</span><select id="vnVoice" onchange="saveVoice('vi', this.value)" style="background:#020617; color:#fff; border:none; padding:4px; border-radius:5px; max-width:62%;"></select></div>
                <div style="display:flex; justify-content:space-between; align-items:center; gap:10px; margin-top:15px;"><span style="white-space:nowrap;">🇰🇷 한국어 목소리</span><select id="koVoice" onchange="saveVoice('ko', this.value)" style="background:#020617; color:#fff; border:none; padding:4px; border-radius:5px; max-width:62%;"></select></div>
                <button class="row-btn btn-outline" style="width:100%; height:42px; margin-top:12px;" onclick="testVoices()">▶ 목소리 들어보기</button>
            </div>
            <div class="row"><button class="row-btn btn-outline" style="font-size: 12px; color: #aaa;" onclick="exportData()">💾 기록 백업</button><button class="row-btn btn-outline" style="font-size: 12px; color: #aaa;" onclick="importData()">📂 기록 복구</button></div>
        </div>
    </div>

    <div id="calendarModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <button class="row-btn btn-outline" style="flex:0; padding:5px 12px;" onclick="changeMonth(-1)">◀</button>
                <h3 id="calTitle" style="margin:0; font-size: 16px; color:#fff;">학습 리포트</h3>
                <button class="row-btn btn-outline" style="flex:0; padding:5px 12px;" onclick="changeMonth(1)">▶</button>
                <button class="close-btn" style="margin-left:10px;" onclick="closeCalendar()">닫기</button>
            </div>
            <div class="cal-legend"><span>💎 1h+</span><span style="opacity: 0.2; font-size: 8px;">|</span><span>🌟 30m+</span><span style="opacity: 0.2; font-size: 8px;">|</span><span>⚡ 10m+</span></div>
            <div id="calendarGrid" class="cal-grid"></div>
            <div id="weeklyBarChart" class="report-bar-container"></div>
            <div id="statsContent" class="stats-panel"></div>
        </div>
    </div>

    <div id="compModal" class="modal">
        <div class="modal-content" style="max-width: 550px;">
            <div class="modal-header"><h3>마스터 리스트</h3><button class="close-btn" onclick="closeModal()">닫기</button></div>
            <div class="comp-table-header">
                <div class="c-vn">베트남어</div>
                <div class="c-pron">발음</div>
                <div class="c-mean">뜻</div>
                <div class="c-hit">횟수</div>
                <div class="c-del">삭제</div>
            </div>
            <div id="compListContainer" style="max-height:65vh; overflow-y:auto; background: rgba(0,0,0,0.1); border-radius: 12px;"></div>
        </div>
    </div>

    <!-- COURSE:HTML START -->
    <div id="courseModal" class="modal">
        <div class="modal-content">
            <div class="modal-header"><h2 style="margin:0; font-size:19px; color:var(--accent-gold);">📅 오늘의 학습</h2><button class="close-btn" onclick="closeCourse()">닫기</button></div>
            <div id="courseBody"></div>
        </div>
    </div>

    <div id="battle" class="bt" role="dialog" aria-label="퀴즈 전투">
        <div class="bt-inner">
            <div class="bt-top">
                <button class="bt-x" onclick="exitBattle()" aria-label="전투 그만하기">✕</button>
                <div class="bt-title" id="btTitle"></div>
                <div class="bt-hearts" id="btHearts"></div>
            </div>
            <div class="bt-arena">
                <div class="bt-mon" id="btMon">👾</div>
                <div class="bt-hp"><div class="bt-hp-fill" id="btHp"></div></div>
                <div class="bt-meta" id="btMeta"></div>
            </div>
            <div class="bt-q" id="btQ"></div>
            <div id="btFb"></div>
        </div>
    </div>
    <!-- COURSE:HTML END -->
    <audio id="bgmPlayer" loop crossorigin="anonymous"></audio>
    <audio id="ttsPlayer" playsinline></audio>
    <input type="file" id="importFile" style="display:none" onchange="processFile(this)">

    <script>
        const sheetId = '1dFO9zjknCildZAQvZ5pT4nt0ZXMsKYskImaHwso3yyM'; // 회사 계정 구글 시트 (2026-10-26 새 단어장)
        const sheetNames = { '단어': '단어', '문장표현': '문장표현', '문법': '문법' };
        let allWords = []; let words = []; let isPlaying = false; let isSkipping = false; let skipDirection = 1; let sleepTimerId = null;
        let savedIndex = 0; let completedWords = {}; let starredWords = {}; let dailyTime = {}; let wakeLock = null;
        let hitCounts = {}; let startTime = null;
        let currentWordRep = 0; let currentExRep = 0; let currentPlayingIndex = -1;
        
        let masterWordList = [];
        let ttsToken = 0;

        window.keepAliveUtterances = [];
        let isAudioUnlocked = false; 

        function initAudioEngineSynchronously() {
            if (isAudioUnlocked) return;
            try {
                if (window.speechSynthesis) {
                    window.speechSynthesis.resume();
                    window.speechSynthesis.cancel();
                    
                    const silentMsg = new SpeechSynthesisUtterance('');
                    silentMsg.lang = 'ko-KR';
                    silentMsg.volume = 0; 
                    silentMsg.rate = 2.0;
                    window.speechSynthesis.speak(silentMsg);
                }

                const silentWav = 'data:audio/wav;base64,UklGRigAAABXQVZFZm10IBIAAAABAAEARKwAAIhYAQACABAAAABkYXRhAgAAAAEA';
                const ttsPlayer = document.getElementById('ttsPlayer');
                const bgmPlayer = document.getElementById('bgmPlayer');
                
                if (ttsPlayer) {
                    ttsPlayer.src = silentWav;
                    ttsPlayer.load();
                    ttsPlayer.play().then(() => { ttsPlayer.pause(); }).catch(() => {});
                }
                
                if (bgmPlayer) {
                    bgmPlayer.src = silentWav;
                    bgmPlayer.load();
                    bgmPlayer.play().then(() => { bgmPlayer.pause(); }).catch(() => {});
                }

                isAudioUnlocked = true;
            } catch(e) {}
        }

        const unlockEvents = ['touchstart', 'click'];
        const globalUnlockHandler = () => {
            if (!isAudioUnlocked) initAudioEngineSynchronously();
            unlockEvents.forEach(e => document.body.removeEventListener(e, globalUnlockHandler));
        };
        unlockEvents.forEach(e => document.body.addEventListener(e, globalUnlockHandler, { once: true }));

        function stopActiveAudio() {
            const ttsPlayer = document.getElementById('ttsPlayer');
            if (ttsPlayer) {
                try {
                    ttsPlayer.pause();
                    ttsPlayer.removeAttribute('src');
                    ttsPlayer.load();
                } catch(e) {}
            }
            window.speechSynthesis.cancel();
        }

        function normalizeText(t) { return t.replace(/[\r\n]+/g, ' ').replace(/\s+/g, ' ').trim(); }
        
        let isPcMode = localStorage.getItem('vn_pc_mode') === 'true';

        // 구간 반복 변수 추가
        let isRangeMode = localStorage.getItem('vn_rangeMode') === 'true';
        let rangeStart = parseInt(localStorage.getItem('vn_rangeStart') || '1');
        let rangeEnd = parseInt(localStorage.getItem('vn_rangeEnd') || '100');
        
        try { 
            savedIndex = parseInt(localStorage.getItem('vn_index') || '0');
            completedWords = JSON.parse(localStorage.getItem('vn_completed') || '{}');
            starredWords = JSON.parse(localStorage.getItem('vn_starred') || '{}');
            dailyTime = JSON.parse(localStorage.getItem('vn_daily_time') || '{}');
            hitCounts = JSON.parse(localStorage.getItem('vn_hit_counts') || '{}');
        } catch(e) {}

        let savedVoiceRate = localStorage.getItem('vn_voiceRate') || '0.9';
        let savedWordVnCount = localStorage.getItem('vn_wordVnCount') !== null ? parseInt(localStorage.getItem('vn_wordVnCount')) : 5;
        let savedWordKrCount = localStorage.getItem('vn_wordKrCount') !== null ? parseInt(localStorage.getItem('vn_wordKrCount')) : 2;
        let savedExVnCount = localStorage.getItem('vn_exVnCount') !== null ? parseInt(localStorage.getItem('vn_exVnCount')) : 1;
        let savedExKrCount = localStorage.getItem('vn_exKrCount') !== null ? parseInt(localStorage.getItem('vn_exKrCount')) : 1;
        let savedTimer = localStorage.getItem('vn_timer') || '240';
        let savedShuffle = localStorage.getItem('vn_shuffle') === 'true';
        let savedStudyMode = localStorage.getItem('vn_studyMode') || '단어'; 
        let savedDelayTime = localStorage.getItem('vn_delayTime') || '1000';
        let savedHideKrWord = localStorage.getItem('vn_hideKrWord') === 'true';
        let savedHideKrEx = localStorage.getItem('vn_hideKrEx') === 'true';
        let savedMuteMode = localStorage.getItem('vn_muteMode') === 'true';
        let reviewMode = localStorage.getItem('vn_reviewMode') === 'true';
        let savedBatteryProtect = localStorage.getItem('vn_batteryProtect') === 'true';
        let savedSleepSound = localStorage.getItem('vn_sleepSound') || 'none';
        let savedFadeOut = localStorage.getItem('vn_fade_out') === 'true';
        let savedHitCountToggle = localStorage.getItem('vn_hit_count_toggle') === 'true';
        let savedAppVolume = localStorage.getItem('vn_app_volume') || '0.8';
        let savedBgmVolume = localStorage.getItem('vn_bgm_volume') || '0.5';

        const cheerMessages = [
            "오늘 10분이 1년 뒤 차이를 만든다.", "하기 싫을 때 시작하면 진짜 실력이 된다.",
            "남들 잘 때 조금 더 하면 인생이 바뀐다.", "지금의 반복이 미래의 실력이다.",
            "포기하지 않는 사람이 결국 이긴다.", "오늘 외운 한 문장이 내일의 무기가 된다.",
            "천천히 가도 멈추지만 않으면 된다.", "꾸준함은 재능을 이긴다.",
            "시작하는 사람이 결국 도착한다.", "지금이 가장 빠른 시작이다.",
            "흔들려도 좋으니 꺾이지는 말자.", "어제의 나보다 단어 하나 더 아는 오늘.",
            "노력은 결코 배신하지 않는다.", "핑계를 찾지 말고 방법을 찾자.",
            "작은 성취가 모여 큰 기적을 만든다.", "하루 10분, 나를 바꾸는 가장 강력 무기."
        ];

        let currentCalDate = new Date();
        
        loadData(savedStudyMode).then(() => { courseAfterLoad(); });

        // 세 탭을 한꺼번에(동시에) 불러와 masterWordList 에 담는다. 단계(lv)·기록키 지도도 같이 만든다
        async function loadMasterList() {
            const lists = await Promise.all(Object.values(sheetNames).map(n => fetchSheetByName(n).catch(() => [])));
            masterWordList = [].concat(...lists);
            prepareMaster(masterWordList);
            return masterWordList;
        }
        
        setInterval(() => { if (isPlaying) { const todayStr = getTodayStr(new Date()); dailyTime[todayStr] = (dailyTime[todayStr] || 0) + 10; localStorage.setItem('vn_daily_time', JSON.stringify(dailyTime)); if (savedBatteryProtect && navigator.getBattery) { navigator.getBattery().then(bt => { if(bt.level <= 0.2) { stopSleepMode(); alert("배터리 20% 보호: 학습을 종료합니다."); } }); } } }, 10000);

        function showNotice(msg) { const toast = document.getElementById('noticeToast'); toast.innerText = msg; toast.style.display = 'block'; setTimeout(() => { toast.style.display = 'none'; }, 2000); }
        function notify(el, type) { const isOn = el.checked; let msg = ""; switch(type) { case 'review': msg = isOn ? "⭐ 별표 복습 모드" : "📚 일반 학습 모드"; break; case 'shuffle': msg = isOn ? "🔀 랜덤 재생" : "🔢 순차 재생"; break; case 'battery': msg = isOn ? "🔋 배터리 보호 작동" : "⚠️ 배터리 보호 해제"; break; case 'fade': msg = isOn ? "📉 서서히 볼륨 감소" : "🔇 일정 볼륨 유지"; break; case 'hit': msg = isOn ? "🔢 횟수 기록 시작" : "🚫 기록 중지"; break; case 'krWord': msg = isOn ? "🇰🇷 본문 한글 끔" : "🔊 한글 동시 학습"; break; case 'krEx': msg = isOn ? "🇰🇷 예문 한글 끔" : "🔊 예문 한글 켬"; break; case 'mute': msg = isOn ? "🔇 사무실 무음 모드 켜짐 (오디오 차단)" : "🔊 오디오 재생 켜짐"; break; } showNotice(msg); }
        
        // 모드를 바꿀 때마다 시트를 새로 읽는다 (시트를 고치면 바로 반영)
        async function loadData(mode) {
            allWords = [];
            try {
                await loadMasterList();
                if (mode === '오늘의 학습') allWords = getTodaySet();
                else if (mode === '전체랜덤') allWords = masterWordList.slice();
                else allWords = masterWordList.filter(w => w.S === sheetNames[mode]);
            } catch (e) { }
            allWords.forEach((w, i) => { w.P = i + 1; });
            applyModeFilter();
        }
        
        // 구간 모드 로직 통합
        function applyModeFilter() {
            navHistory = [];
            if (savedStudyMode === '오늘의 학습') { words = allWords; if (savedIndex >= words.length) savedIndex = 0; renderWord(); return; } // 오늘의 학습은 별표·구간 필터 없이 그대로
            if (reviewMode) {
                words = allWords.filter(w => starredWords[w.K]); 
                if (words.length === 0) { reviewMode = false; localStorage.setItem('vn_reviewMode', 'false'); words = allWords; } 
            } else { 
                words = allWords; 
            } 

            if (isRangeMode) {
                // 구간은 목록에 보이는 번호(P) 기준: 별표 복습 중이어도 "50~60번"은 같은 50~60번
                const s = Math.max(1, rangeStart), e = rangeEnd;
                const ranged = words.filter(w => w.P >= s && w.P <= e);
                if (ranged.length) words = ranged;
            }

            if (savedIndex >= words.length) savedIndex = 0; 
            renderWord(); 
        }

        // CSV 읽기: 따옴표("")·쉼표·줄바꿈이 들어간 칸도 깨지지 않게 한 글자씩 읽는다
        function parseCsv(text) {
            const rows = []; let row = [], field = '', inQ = false;
            for (let i = 0; i < text.length; i++) {
                const ch = text[i];
                if (inQ) {
                    if (ch === '"') { if (text[i + 1] === '"') { field += '"'; i++; } else inQ = false; }
                    else field += ch;
                } else if (ch === '"') inQ = true;
                else if (ch === ',') { row.push(field); field = ''; }
                else if (ch === '\n') { row.push(field); rows.push(row); row = []; field = ''; }
                else if (ch !== '\r') field += ch;
            }
            if (field !== '' || row.length) { row.push(field); rows.push(row); }
            return rows;
        }

        // 시트 읽기: headers=0 → 첫 줄도 데이터로 받는다 (시트에는 제목 줄이 없음)
        // K = 기록용 키. 같은 탭에 같은 단어가 또 나오면 'Thì#2' 처럼 따로 기록한다 (첫 번째는 예전과 같은 키라 기존 기록 유지)
        // PC에서 파일(index.html)을 바로 열면 주소가 file:// 이라 구글이 fetch를 막는다 → <script>로 받는 방식(JSONP)으로 읽는다
        function gvizJsonp(name) {
            return new Promise((resolve, reject) => {
                const cb = '__gv' + Math.random().toString(36).slice(2);
                const s = document.createElement('script');
                const timer = setTimeout(() => { cleanup(); reject(new Error('timeout')); }, 20000);
                function cleanup() { clearTimeout(timer); try { delete window[cb]; } catch (e) { window[cb] = undefined; } s.remove(); }
                window[cb] = resp => {
                    cleanup();
                    if (!resp || resp.status === 'error' || !resp.table) return reject(new Error('시트를 읽을 수 없어요'));
                    resolve((resp.table.rows || []).map(r => (r.c || []).map(c => (c && c.v != null) ? String(c.v) : '')));
                };
                s.onerror = () => { cleanup(); reject(new Error('시트를 불러오지 못했어요')); };
                s.src = `https://docs.google.com/spreadsheets/d/${sheetId}/gviz/tq?tqx=out:json;responseHandler:${cb}&headers=0&sheet=${encodeURIComponent(name)}`;
                document.head.appendChild(s);
            });
        }
        async function sheetRows(name) {
            if (location.protocol === 'file:') return gvizJsonp(name);
            try {
                const url = `https://docs.google.com/spreadsheets/d/${sheetId}/gviz/tq?tqx=out:csv&headers=0&sheet=${encodeURIComponent(name)}`;
                const res = await fetch(url); if (!res.ok) throw new Error('HTTP ' + res.status);
                return parseCsv(await res.text());
            } catch (e) { return gvizJsonp(name); } // fetch가 막히면 다른 방식으로 한 번 더
        }
        async function fetchSheetByName(name) {
            const rows = await sheetRows(name);
            const seen = {}; let n = 0;
            return rows
                .map(cols => ({ A: cols[0] || '', B: cols[1] || '', C: cols[2] || '', D: cols[3] || '', E: cols[4] || '', F: cols[5] || '', G: cols[6] || '', H: cols[7] || '', I: cols[8] || '', hn: cols[9] || '', lit: cols[10] || '', why: cols[11] || '' }))
                .filter(w => w.A.trim() !== '' && w.A.trim() !== '베트남어') // 1행 제목 줄('베트남어')은 건너뜀
                .map(w => { n++; seen[w.A] = (seen[w.A] || 0) + 1; w.S = name; w.N = n; w.K = seen[w.A] === 1 ? w.A : w.A + '#' + seen[w.A]; return w; });
        }
        function togglePcMode() { isPcMode = !isPcMode; localStorage.setItem('vn_pc_mode', isPcMode); renderWord(); }

        // 구간 모드 제어 기능 추가
        function toggleRangeMode() {
            isRangeMode = document.getElementById('rangeToggle').checked;
            localStorage.setItem('vn_rangeMode', isRangeMode);
            document.getElementById('rangeInputs').style.display = isRangeMode ? 'flex' : 'none';
            if (!isRangeMode) { applyRange(); }
        }

        function applyRange() {
            rangeStart = parseInt(document.getElementById('rangeStart').value) || 1;
            rangeEnd = parseInt(document.getElementById('rangeEnd').value) || 100;
            localStorage.setItem('vn_rangeStart', rangeStart);
            localStorage.setItem('vn_rangeEnd', rangeEnd);
            savedIndex = 0;
            const wasPlaying = isPlaying;
            if(wasPlaying) stopSleepMode();
            applyModeFilter();
            if(wasPlaying) startSleepMode();
            openListModal();
            showNotice(isRangeMode ? `${rangeStart}번 ~ ${rangeEnd}번 구간이 설정되었습니다.` : `전체 반복으로 변경되었습니다.`);
        }

        function renderWord() {
            const app = document.getElementById('app');
            if (words.length === 0 && savedStudyMode === '오늘의 학습' && masterWordList.length) { app.innerHTML = `<div class="card" style="justify-content:center; gap:16px;"><div class="top-pills">${coursePillHtml()}</div><div style="font-size:18px; line-height:1.6;">오늘 배울 항목이 없어요.<br><span style="color:#94a3b8; font-size:14px;">이 단계를 다 배웠다면 👑 승급 시험에 도전하거나,<br>다른 단계나 다른 모드를 골라 보세요.</span></div><button class="play-btn" onclick="openCourse()">📅 오늘 메뉴 열기</button><select class="row-btn btn-outline sheet-select" onchange="changeStudyModeMain(this)">${STUDY_MODES.map(m => `<option value="${m}" ${savedStudyMode === m ? 'selected' : ''}>${m}</option>`).join('')}</select></div>`; return; }
            if (words.length === 0) { app.innerHTML = '<div class="card" style="justify-content:center;"><div style="font-size:17px; line-height:1.8; color:#cbd5e1;">데이터 로딩 중...<br><span style="font-size:14px; color:#94a3b8;">계속 이 화면이면 구글 시트를 확인하세요.<br>① [공유]가 <b style="color:#fff;">링크가 있는 모든 사용자 · 뷰어</b>인지<br>② 엑셀(.xlsx)이 아니라 <b style="color:#fff;">구글 시트</b>인지<br>③ 아래 탭 이름이 <b style="color:#fff;">단어, 문장표현, 문법</b>인지</span></div></div>'; return; }
            const w = words[savedIndex]; const isCompleted = completedWords[w.K]; const isStarred = starredWords[w.K];
            
            if (isPcMode) {
                let html = `<div class="pc-bar-container">`;
                html += `<div class="pc-side-group"><button class="pc-btn mode" onclick="togglePcMode()">📱 일반 모드</button><button class="pc-btn hide" onclick="toggleComplete()">✅ 암기 끝</button>${('documentPictureInPicture' in window) ? '<button class="pc-btn mode" onclick="openPipBar()" title="다른 프로그램 위에 항상 떠 있는 자막창">📌 항상 위</button>' : ''}</div>`;
                html += `<div class="pc-content-area"><button class="pc-nav-btn" onclick="moveWord(-1)">‹</button><div class="pc-text-group" onclick="openListModal()" title="목록 열기"><span class="pc-vn">${w.A}</span>`;
                if (w.B) html += `<span class="pc-pron">[${w.B}]</span>`;
                if (w.C) html += `<span class="pc-kr">(${w.C})</span>`;
                if (w.D) { html += `<span class="pc-ex">${w.D}</span>`; if (w.E) html += `<span class="pc-ex-pron">[${w.E}]</span>`; if (w.F) html += `<span class="pc-ex-kr">(${w.F})</span>`; }
                html += `</div><button class="pc-nav-btn" onclick="moveWord(1)">›</button></div>`;
                html += `<div class="pc-side-group">`;
                if (!isPlaying) { html += `<button class="pc-btn start" onclick="initAudioEngineSynchronously(); startSleepMode();">▶ 시작</button>`; } else { html += `<button class="pc-btn stop" onclick="stopSleepMode()">⏸ 멈춤</button>`; }
                html += `</div></div>`;
                app.innerHTML = html; renderPip();
                return; 
            }

            let vnSize = w.A.length > 15 ? '34px' : (w.A.length > 8 ? '44px' : '52px');
            let html = '<div class="card">';
            html += `<div class="top-pills">` + coursePillHtml() + `<div class="status" style="cursor:pointer; display:inline-block; margin:0; padding:6px 15px; background:rgba(255,255,255,0.05); border-radius:20px; font-size:12px; color:var(--accent-gold); border: 1px solid var(--glass-border);" onclick="openListModal()">` + (reviewMode ? '⭐ REVIEW' : 'MODE: ' + savedStudyMode) + ' | ' + statusPos(w) + ' 🔍 </div></div><div class="content-wrap">' + lvChipHtml(w);
            html += `<button class="star-btn ${isStarred ? 'active' : ''}" onclick="toggleStar()">${isStarred ? '★' : '☆'}</button>`;
            if (isCompleted) html += '<div style="color:var(--accent-gold); font-size:14px; margin-bottom:5px; font-weight:bold;">✅ 마스터한 항목</div>';
            html += '<div style="display: flex; align-items: center; justify-content: space-between;"><button class="arrow-btn" onclick="moveWord(-1)">‹</button><div class="vn" style="font-size:' + vnSize + ';">' + w.A + '</div><button class="arrow-btn" onclick="moveWord(1)">›</button></div>';
            html += pronHtml(w);
            html += '<div class="kr">' + w.C + '</div>';
            if (w.G) { html += '<div style="font-size: 18px; color: #cbd5e1; margin-bottom: 15px; line-height: 1.4;">' + w.G + '</div>'; }
            if (w.D) { html += '<div class="ex-box"><div class="ex-vn">' + w.D + '</div>'; if (w.E) html += '<div class="ex-pron">[' + w.E + ']</div>'; html += '<div class="ex-kr">' + w.F + '</div>' + exExtraHtml(w) + '</div>'; }
            html += '</div><div class="bottom-controls">';
            if (!isPlaying) { html += '<button class="play-btn" onclick="initAudioEngineSynchronously(); startSleepMode();">START</button>'; }
            else { html += '<button class="play-btn" style="background:#334155;" onclick="stopSleepMode()">PAUSE (일시정지)</button>'; }
            html += `<div class="row"><button class="row-btn btn-gold" onclick="toggleComplete()">${isCompleted ? "숨김 해제" : "암기 끝! 숨기기"}</button><select class="row-btn btn-outline sheet-select" onchange="changeStudyModeMain(this)">`;
            STUDY_MODES.forEach(m => { html += `<option value="${m}" ${savedStudyMode === m ? 'selected' : ''}>${m}</option>`; });
            html += `</select></div><div class="row">`;
            if (!isPlaying) { html += `<button class="row-btn btn-outline" style="color:#fda4af; border-color:rgba(244,63,94,0.45);" onclick="startBattle(savedStudyMode === '오늘의 학습' ? 'today' : 'list')">⚔️ 퀴즈 전투</button>`; }
            else { html += `<button class="row-btn btn-outline" style="color:var(--accent-gold);" onclick="toggleBlackout()">💡 저전력 모드</button>`; }
            html += `<button class="row-btn btn-outline" onclick="openSettings()">⚙️ 설정</button></div>`;
            html += `<div class="quick-settings"><label><input type="checkbox" id="mainReviewMode" ${reviewMode ? 'checked' : ''} onchange="toggleMainReview(); notify(this, 'review')"> ⭐ 별표 복습</label><label><input type="checkbox" id="mainShuffleMode" ${savedShuffle ? 'checked' : ''} onchange="toggleMainShuffle(); notify(this, 'shuffle')"> 🔀 랜덤 재생</label>`;
            html += `<button onclick="togglePcMode()" style="background:none; border:none; color:#cbd5e1; cursor:pointer; font-weight:bold; font-size:13px; display:flex; align-items:center; gap:5px;">💻 PC 모드</button></div></div></div>`;
            app.innerHTML = html; renderPip();
        }

        function openListModal() { 
            // 모달 열 때 구간 설정 상태 업데이트
            document.getElementById('rangeToggle').checked = isRangeMode;
            document.getElementById('rangeStart').value = rangeStart;
            document.getElementById('rangeEnd').value = rangeEnd;
            document.getElementById('rangeInputs').style.display = isRangeMode ? 'flex' : 'none';

            const container = document.getElementById('listContainer'); 
            let html = ''; 
            // 번호는 화면 위쪽·구간 설정과 같은 목록 번호(P)로 표시

            words.forEach((w, idx) => { 
                const isCurrent = idx === savedIndex; 
                html += `<div onclick="jumpToWord(${idx})" style="padding: 12px; border-bottom: 1px solid rgba(255,255,255,0.05); display: flex; align-items: center; cursor: pointer; background: ${isCurrent ? 'rgba(16, 185, 129, 0.2)' : 'transparent'};"><div style="width: 40px; color: var(--accent-gold); font-size: 12px;">${w.P || (idx + 1)}</div><div style="flex: 1; color: var(--accent-green); font-weight: bold; font-size: 14px;">${w.A}</div><div style="flex: 1; color: #cbd5e1; font-size: 12px; text-align: right; white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">${w.C}</div></div>`; 
            }); 
            container.innerHTML = html; 
            document.getElementById('listModal').style.display = 'block'; 
            setTimeout(() => { const activeEl = container.children[savedIndex]; if(activeEl) activeEl.scrollIntoView({ behavior: 'smooth', block: 'center' }); }, 50); 
        }
        function closeListModal() { document.getElementById('listModal').style.display = 'none'; }
        
        function jumpToWord(index) { 
            savedIndex = index; localStorage.setItem('vn_index', savedIndex); 
            if (isPlaying) { isSkipping = true; ttsToken++; stopActiveAudio(); currentWordRep = 0; currentExRep = 0; } 
            closeListModal(); renderWord(); showNotice(`${(words[index] && words[index].P) || index + 1}번 항목으로 이동했습니다.`); 
        }
        
        async function requestWakeLock() { try { if ('wakeLock' in navigator) wakeLock = await navigator.wakeLock.request('screen'); } catch (err) {} }
        function releaseWakeLock() { if (wakeLock) { wakeLock.release(); wakeLock = null; } }
        // 다른 앱을 보다 돌아오면 화면 켜짐 유지가 풀려 있으므로 다시 요청
        document.addEventListener('visibilitychange', () => { if (document.visibilityState === 'visible' && isPlaying) requestWakeLock(); });
        function toggleStar() { const w = words[savedIndex]; if (starredWords[w.K]) delete starredWords[w.K]; else starredWords[w.K] = getTodayStr(new Date()); localStorage.setItem('vn_starred', JSON.stringify(starredWords)); renderWord(); }
        function toggleComplete() { let w = words[savedIndex]; if (completedWords[w.K]) { delete completedWords[w.K]; } else { completedWords[w.K] = getTodayStr(new Date()); showNotice('✅ 암기 끝! 숨김 처리되었습니다.'); moveWord(1); } localStorage.setItem('vn_completed', JSON.stringify(completedWords)); renderWord(); }
        function toggleMainReview() { reviewMode = document.getElementById('mainReviewMode').checked; localStorage.setItem('vn_reviewMode', reviewMode); savedIndex = 0; const wasPlaying = isPlaying; if(wasPlaying) stopSleepMode(); applyModeFilter(); if(wasPlaying) startSleepMode(); }
        function toggleMainShuffle() { savedShuffle = document.getElementById('mainShuffleMode').checked; localStorage.setItem('vn_shuffle', savedShuffle); if(isPlaying) { isSkipping = true; ttsToken++; stopActiveAudio(); } renderWord(); }
        
        async function changeStudyModeMain(el) { savedStudyMode = el.value; localStorage.setItem('vn_studyMode', savedStudyMode); savedIndex = 0; const wasPlaying = isPlaying; if(wasPlaying) stopSleepMode(); await loadData(savedStudyMode); if(wasPlaying) startSleepMode(); }

        function openSettings() { 
            document.getElementById('settingsModal').style.display = 'block'; 
            const randomIdx = Math.floor(Math.random() * cheerMessages.length); document.getElementById('cheerMessage').innerText = cheerMessages[randomIdx];
            document.getElementById('appVolume').value = savedAppVolume; document.getElementById('bgmVolume').value = savedBgmVolume; 
            document.getElementById('wordVnCountDisplay').innerText = savedWordVnCount; document.getElementById('wordKrCountDisplay').innerText = savedWordKrCount; 
            document.getElementById('exVnCountDisplay').innerText = savedExVnCount; document.getElementById('exKrCountDisplay').innerText = savedExKrCount; 
            document.getElementById('muteModeToggle').checked = savedMuteMode; 
            document.getElementById('fadeOutToggle').checked = savedFadeOut; document.getElementById('hitCountToggle').checked = savedHitCountToggle; 
            document.getElementById('batteryProtect').checked = savedBatteryProtect; document.getElementById('sleepSound').value = savedSleepSound; 
            document.getElementById('sleepTimer').value = savedTimer; document.getElementById('hideKrWord').checked = savedHideKrWord; 
            document.getElementById('hideKrEx').checked = savedHideKrEx; document.getElementById('delayTime').value = savedDelayTime; 
            document.getElementById('voiceRate').value = localStorage.getItem('vn_voiceRate') || '0.9'; fillVoiceSelect('vnVoice', 'vi'); fillVoiceSelect('koVoice', 'ko'); 
        }

        function closeSettings() { document.getElementById('settingsModal').style.display = 'none'; renderWord(); }
        
        function saveSettings() { 
            savedAppVolume = document.getElementById('appVolume').value; savedBgmVolume = document.getElementById('bgmVolume').value; 
            savedTimer = document.getElementById('sleepTimer').value; savedHideKrWord = document.getElementById('hideKrWord').checked; 
            savedHideKrEx = document.getElementById('hideKrEx').checked; savedMuteMode = document.getElementById('muteModeToggle').checked;
            localStorage.setItem('vn_muteMode', savedMuteMode);
            savedBatteryProtect = document.getElementById('batteryProtect').checked; savedSleepSound = document.getElementById('sleepSound').value; 
            savedFadeOut = document.getElementById('fadeOutToggle').checked; savedHitCountToggle = document.getElementById('hitCountToggle').checked; 
            savedDelayTime = document.getElementById('delayTime').value; let vr = document.getElementById('voiceRate').value; 
            localStorage.setItem('vn_app_volume', savedAppVolume); 
            localStorage.setItem('vn_bgm_volume', savedBgmVolume); localStorage.setItem('vn_timer', savedTimer); 
            localStorage.setItem('vn_hideKrWord', savedHideKrWord); localStorage.setItem('vn_hideKrEx', savedHideKrEx); 
            localStorage.setItem('vn_batteryProtect', savedBatteryProtect); localStorage.setItem('vn_sleepSound', savedSleepSound); 
            localStorage.setItem('vn_fade_out', savedFadeOut); localStorage.setItem('vn_hit_count_toggle', savedHitCountToggle); 
            localStorage.setItem('vn_delayTime', savedDelayTime); localStorage.setItem('vn_voiceRate', vr); 
            
            const p = document.getElementById('bgmPlayer'); 
            if (p) { p.volume = parseFloat(savedBgmVolume); if (savedMuteMode) p.pause(); else if (isPlaying) playBackgroundSound(); } 
            if(isPlaying) { isSkipping = true; ttsToken++; stopActiveAudio(); } 
        }

        function adjustVolume(targetId, amount) { const slider = document.getElementById(targetId); let newVal = parseFloat(slider.value) + amount; if (newVal > 1) newVal = 1; if (newVal < 0) newVal = 0; slider.value = newVal.toFixed(1); saveSettings(); if (targetId === 'appVolume') showNotice('🔊 볼륨이 조절되었습니다.'); else showNotice('🎵 수면 유도음 볼륨이 조절되었습니다.'); }
        function changeGlobalCount(type, n) { if (type === 'wordVn') { savedWordVnCount = Math.min(99, Math.max(0, savedWordVnCount + n)); localStorage.setItem('vn_wordVnCount', savedWordVnCount); document.getElementById('wordVnCountDisplay').innerText = savedWordVnCount; } else if (type === 'wordKr') { savedWordKrCount = Math.min(99, Math.max(0, savedWordKrCount + n)); localStorage.setItem('vn_wordKrCount', savedWordKrCount); document.getElementById('wordKrCountDisplay').innerText = savedWordKrCount; } else if (type === 'exVn') { savedExVnCount = Math.min(99, Math.max(0, savedExVnCount + n)); localStorage.setItem('vn_exVnCount', savedExVnCount); document.getElementById('exVnCountDisplay').innerText = savedExVnCount; } else if (type === 'exKr') { savedExKrCount = Math.min(99, Math.max(0, savedExKrCount + n)); localStorage.setItem('vn_exKrCount', savedExKrCount); document.getElementById('exKrCountDisplay').innerText = savedExKrCount; } if(isPlaying) { isSkipping = true; ttsToken++; stopActiveAudio(); } }
        
        function moveWord(direction) { 
            isSkipping = true; skipDirection = direction; 
            ttsToken++; stopActiveAudio(); 
            if (direction === 1) { advanceIndex(); }
            else if (savedShuffle && navHistory.length) { savedIndex = navHistory.pop(); if (savedIndex >= words.length) savedIndex = 0; } // 랜덤일 땐 방금 본 단어로
            else { savedIndex--; if (savedIndex < 0) savedIndex = words.length - 1; } 
            renderWord(); 
        }
        
        function playBackgroundSound() { 
            if (savedMuteMode) return;
            const p = document.getElementById('bgmPlayer'); 
            const s = { 
                none: 'data:audio/wav;base64,UklGRigAAABXQVZFZm10IBIAAAABAAEARKwAAIhYAQACABAAAABkYXRhAgAAAAEA', 
                rain: 'https://actions.google.com/sounds/v1/weather/light_rain.ogg', 
                ocean: 'https://actions.google.com/sounds/v1/water/waves_crashing_on_rock_beach.ogg', 
                forest: 'https://actions.google.com/sounds/v1/ambiences/jungle_atmosphere_night.ogg', 
                fire: 'https://actions.google.com/sounds/v1/ambiences/fire.ogg', 
                camping: 'https://actions.google.com/sounds/v1/ambiences/outdoor_summer_ambience.ogg' 
            }; 
            p.src = s[savedSleepSound] || s['none']; 
            p.volume = savedSleepSound === 'none' ? 0 : parseFloat(savedBgmVolume); 
            p.play().catch(e => {}); 
        }

        async function waitPhysically(text, type) {
            const rate = parseFloat(localStorage.getItem('vn_voiceRate') || '0.9');
            const estMs = Math.max(1000, (text.length * 150) / rate + 500); 
            const startTime = Date.now();
            
            while (Date.now() - startTime < estMs) {
                if (!isPlaying || isSkipping) break; 
                await new Promise(r => tick(r, 50));
            }

            if (type === 'kr') {
                const fallbackTime = Date.now();
                while (window.speechSynthesis.speaking && Date.now() - fallbackTime < 5000) {
                    if (!isPlaying || isSkipping) break;
                    await new Promise(r => tick(r, 50));
                }
                await new Promise(r => tick(r, 400));
            } else {
                const ttsPlayer = document.getElementById('ttsPlayer');
                if (ttsPlayer) {
                    const fallbackTime = Date.now();
                    while (!ttsPlayer.paused && Date.now() - fallbackTime < 5000) {
                        if (!isPlaying || isSkipping) break;
                        await new Promise(r => tick(r, 50));
                    }
                }
                await new Promise(r => tick(r, 100));
            }
        }

        async function startSleepMode() { 
            if (isPlaying) return; 
            isPlaying = true; 
            requestWakeLock(); 

            playBackgroundSound(); 
            startTime = Date.now(); 
            
            if (sleepTimerId) clearTimeout(sleepTimerId); const timerVal = parseInt(savedTimer); if (timerVal > 0) sleepTimerId = setTimeout(() => stopSleepMode(), timerVal * 60 * 1000); 
            while (isPlaying) { 
                if (!words.length || !playableIndices().length) { stopSleepMode(); showNotice("재생할 항목이 없어요. 전부 '암기 끝' 상태예요. 완료 목록에서 숨김을 풀거나 다른 모드를 골라 주세요."); return; }
                if (savedIndex >= words.length) savedIndex = 0; isSkipping = false; const w = words[savedIndex];
                if (!isPlayable(w)) { advanceIndex(); continue; } // 암기 끝 항목은 화면을 다시 그리지 않고 바로 건너뜀
                localStorage.setItem('vn_index', savedIndex); renderWord(); const itemStart = Date.now();
                if (currentPlayingIndex !== savedIndex) { currentWordRep = 0; currentExRep = 0; currentPlayingIndex = savedIndex; } 
                if (savedHitCountToggle && currentWordRep === 0 && currentExRep === 0) { hitCounts[w.K] = (hitCounts[w.K] || 0) + 1; localStorage.setItem('vn_hit_counts', JSON.stringify(hitCounts)); } 
                let maxWordReps = Math.max(savedWordVnCount, savedWordKrCount); 
                
                for (; currentWordRep < maxWordReps; currentWordRep++) { 
                    if (!isPlaying || isSkipping) break; 
                    
                    if (currentWordRep < savedWordVnCount) { 
                        playIOSVoice(w.A); 
                        await waitPhysically(w.A, 'vn'); 
                        if (!isPlaying || isSkipping) break; 
                        await new Promise(r => tick(r, 200)); 
                    } 
                    if (currentWordRep < savedWordKrCount && !savedHideKrWord) { 
                        speakKoreanLocal(w.C); 
                        await waitPhysically(w.C, 'kr'); 
                        if (!isPlaying || isSkipping) break; 
                        await new Promise(r => tick(r, 200)); 
                    } 
                    let delayMs = parseInt(savedDelayTime); for(let ms=0; ms<delayMs; ms+=100) { if(!isPlaying || isSkipping) break; await new Promise(r => tick(r, 100)); } 
                } 
                if (!isPlaying || isSkipping) continue; 
                
                if (w.D && (savedExVnCount > 0 || savedExKrCount > 0)) { 
                    let maxExReps = Math.max(savedExVnCount, savedExKrCount); 
                    for (; currentExRep < maxExReps; currentExRep++) { 
                        if (!isPlaying || isSkipping) break; 
                        
                        if (currentExRep < savedExVnCount) { 
                            playIOSVoice(w.D); 
                            await waitPhysically(w.D, 'vn'); 
                            if (!isPlaying || isSkipping) break; 
                            await new Promise(r => tick(r, 200));
                        } 
                        if (currentExRep < savedExKrCount && !savedHideKrEx) { 
                            speakKoreanLocal(w.F); 
                            await waitPhysically(w.F, 'kr'); 
                            if (!isPlaying || isSkipping) break; 
                            await new Promise(r => tick(r, 200));
                        } 
                        let delayMs = parseInt(savedDelayTime); for(let ms=0; ms<delayMs; ms+=100) { if(!isPlaying || isSkipping) break; await new Promise(r => tick(r, 100)); } 
                    } 
                } 
                if (!isPlaying || isSkipping) continue;
                if (Date.now() - itemStart < 300) await new Promise(r => tick(r, 300)); // 반복 횟수가 모두 0이어도 화면이 굳지 않게 숨 돌리기
                currentWordRep = 0; currentExRep = 0; if (!isSkipping) advanceIndex();
            } 
        }
        
        function stopSleepMode() { 
            isPlaying = false; ttsToken++; stopActiveAudio(); 
            document.getElementById('bgmPlayer').pause(); releaseWakeLock(); renderWord(); 
        }

        function speakKoreanLocal(text) { 
            if(savedMuteMode || !text || isSkipping || !isPlaying) return; 
            
            stopActiveAudio(); 
            window.speechSynthesis.cancel(); 
            
            const msg = new SpeechSynthesisUtterance(text); 
            window.keepAliveUtterances.push(msg); 
            
            msg.lang = 'ko-KR'; const koV = pickVoice('ko'); if (koV) msg.voice = koV; 
            msg.volume = parseFloat(savedAppVolume) * 0.85; 
            msg.rate = parseFloat(localStorage.getItem('vn_voiceRate') || '0.9'); 
            
            msg.onend = () => { 
                const idx = window.keepAliveUtterances.indexOf(msg);
                if (idx !== -1) window.keepAliveUtterances.splice(idx, 1);
            }; 
            msg.onerror = msg.onend;
            
            window.speechSynthesis.speak(msg); 
        }

        function playIOSVoice(text) { 
            if(savedMuteMode || !text || isSkipping || !isPlaying) return; 
            stopActiveAudio();
            window.speechSynthesis.cancel();
            
            const msg = new SpeechSynthesisUtterance(text); 
            window.keepAliveUtterances.push(msg);
            msg.lang = 'vi-VN'; 
            msg.volume = parseFloat(savedAppVolume) * 0.85; 
            msg.rate = parseFloat(localStorage.getItem('vn_voiceRate') || '0.9'); 
            let voices = window.speechSynthesis.getVoices(); 
            let vnVoices = voices.filter(v => v.lang.startsWith('vi')); 
            if(vnVoices.length > 0) { 
                msg.voice = pickVoice('vi') || vnVoices[0];
            } 
            
            msg.onend = () => { 
                const idx = window.keepAliveUtterances.indexOf(msg);
                if (idx !== -1) window.keepAliveUtterances.splice(idx, 1);
            }; 
            msg.onerror = msg.onend;
            window.speechSynthesis.speak(msg); 
        }
        
        // ---- 재생 순서 ----
        var navHistory = []; // 랜덤 재생에서 지나온 순서 (‹ 버튼용)
        function isPlayable(w) { return reviewMode || !completedWords[w.K]; }
        function playableIndices() { const a = []; words.forEach((w, i) => { if (isPlayable(w)) a.push(i); }); return a; }
        function advanceIndex() {
            if (savedShuffle && words.length > 1) {
                navHistory.push(savedIndex); if (navHistory.length > 100) navHistory.shift();
                let pool = playableIndices().filter(i => i !== savedIndex); // 같은 단어 연속 금지, 암기 끝은 건너뜀
                if (!pool.length) pool = words.map((_, i) => i).filter(i => i !== savedIndex);
                savedIndex = pool[Math.floor(Math.random() * pool.length)];
            } else { savedIndex++; if (savedIndex >= words.length) savedIndex = 0; }
        }
        function statusPos(w) { const p = w.P || (savedIndex + 1); return (words.length === allWords.length) ? (p + '/' + allWords.length) : (p + '번 · ' + (savedIndex + 1) + '/' + words.length); }

        // 대기 타이머: PC 자막창이 열려 있으면 그 창의 타이머를 쓴다 (본 창이 가려져도 느려지지 않게)
        function tick(fn, ms) { const host = (pipWin && !pipWin.closed) ? pipWin : window; return host.setTimeout(fn, ms); }

        // ---- 목소리 고르기: 저장한 목소리 → 없으면 고품질(Natural·Online·Premium 등) 우선 ----
        function voiceScore(v) { let s = 0; if (/natural|neural|online|premium|enhanced|향상/i.test(v.name)) s += 10; if (/google/i.test(v.name)) s += 3; if (v.localService === false) s += 1; return s; }
        var voiceCache = []; // 목소리 목록은 한 번 받아 두고 바뀔 때만 다시 받는다
        function allVoices() { if (!window.speechSynthesis) return []; if (!voiceCache.length) voiceCache = window.speechSynthesis.getVoices() || []; return voiceCache; }
        function voicesFor(prefix) { return allVoices().filter(v => (v.lang || '').toLowerCase().replace('_', '-').startsWith(prefix)); }
        function pickVoice(prefix) {
            const list = voicesFor(prefix); if (!list.length) return null;
            const saved = localStorage.getItem('vn_voice_' + prefix);
            if (saved) { const hit = list.find(v => v.name === saved); if (hit) return hit; }
            return list.slice().sort((a, b) => voiceScore(b) - voiceScore(a))[0];
        }
        function fillVoiceSelect(id, prefix) {
            const sel = document.getElementById(id); if (!sel) return;
            const list = voicesFor(prefix); const saved = localStorage.getItem('vn_voice_' + prefix) || '';
            if (!list.length) { sel.innerHTML = '<option value="">이 기기에 없음</option>'; return; }
            const best = list.slice().sort((a, b) => voiceScore(b) - voiceScore(a))[0];
            sel.innerHTML = `<option value="">자동 (${best.name})</option>` + list.map(v => `<option value="${v.name.replace(/"/g, '&quot;')}" ${v.name === saved ? 'selected' : ''}>${v.name}</option>`).join('');
        }
        function saveVoice(prefix, name) { if (name) localStorage.setItem('vn_voice_' + prefix, name); else localStorage.removeItem('vn_voice_' + prefix); showNotice('🗣️ 목소리를 바꿨습니다.'); }
        function testVoices() {
            if (!window.speechSynthesis) return; window.speechSynthesis.cancel();
            const w = words[savedIndex] || { A: 'Xin chào', C: '안녕하세요' };
            [['vi', 'vi-VN', w.A], ['ko', 'ko-KR', w.C]].forEach(([p, lang, text]) => {
                if (!text) return; const m = new SpeechSynthesisUtterance(text); m.lang = lang; const v = pickVoice(p); if (v) m.voice = v;
                m.rate = parseFloat(localStorage.getItem('vn_voiceRate') || '0.9'); m.volume = parseFloat(savedAppVolume);
                window.keepAliveUtterances.push(m); window.speechSynthesis.speak(m);
            });
        }

        // ---- PC 항상 위 자막창 (크롬·엣지의 Document Picture-in-Picture) ----
        var pipWin = null;
        async function openPipBar() {
            if (!('documentPictureInPicture' in window)) { showNotice('이 브라우저는 항상 위 자막창을 지원하지 않아요. 크롬이나 엣지에서 열어 주세요.'); return; }
            if (pipWin && !pipWin.closed) { pipWin.focus(); return; }
            try { pipWin = await documentPictureInPicture.requestWindow({ width: Math.min(1100, (screen.availWidth || 1200) - 40), height: 80 }); }
            catch (e) { pipWin = null; showNotice('자막창을 열 수 없어요: ' + e.message); return; }
            document.querySelectorAll('style').forEach(s => pipWin.document.head.appendChild(s.cloneNode(true)));
            pipWin.document.title = '베트남어 자막';
            pipWin.document.body.style.cssText = 'margin:0; background:#0f172a; overflow:hidden; height:100vh;';
            pipWin.document.body.addEventListener('click', e => {
                const b = e.target.closest('[data-act]'); if (!b) return;
                const a = b.dataset.act;
                if (a === 'prev') moveWord(-1); else if (a === 'next') moveWord(1);
                else if (a === 'play') { initAudioEngineSynchronously(); startSleepMode(); }
                else if (a === 'stop') stopSleepMode(); else if (a === 'done') toggleComplete();
            });
            pipWin.addEventListener('pagehide', () => { pipWin = null; });
            renderPip();
        }
        function renderPip() {
            if (!pipWin || pipWin.closed) return;
            if (!words.length) { pipWin.document.body.innerHTML = '<div class="pc-bar-container" style="height:100vh; border-top:none; justify-content:center; color:#cbd5e1;">데이터 로딩 중...</div>'; return; }
            const w = words[savedIndex];
            let h = '<div class="pc-bar-container" style="height:100vh; border-top:none;">';
            h += '<div class="pc-side-group"><button class="pc-btn hide" data-act="done" title="암기 끝">✅</button></div>';
            h += `<div class="pc-content-area"><button class="pc-nav-btn" data-act="prev">‹</button><div class="pc-text-group"><span class="pc-vn">${w.A}</span>`;
            if (w.B) h += `<span class="pc-pron">[${w.B}]</span>`;
            if (w.C) h += `<span class="pc-kr">(${w.C})</span>`;
            if (w.D) { h += `<span class="pc-ex">${w.D}</span>`; if (w.E) h += `<span class="pc-ex-pron">[${w.E}]</span>`; if (w.F) h += `<span class="pc-ex-kr">(${w.F})</span>`; }
            h += '</div><button class="pc-nav-btn" data-act="next">›</button></div>';
            h += '<div class="pc-side-group">' + (isPlaying ? '<button class="pc-btn stop" data-act="stop">⏸</button>' : '<button class="pc-btn start" data-act="play">▶</button>') + '</div></div>';
            pipWin.document.body.innerHTML = h;
        }
        function toggleBlackout() { const o = document.getElementById('blackoutOverlay'); o.style.display = (o.style.display === 'none') ? 'flex' : 'none'; }
        function getTodayStr(d) { return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; }
        function formatTimeText(seconds) { if (!seconds || seconds <= 0) return '0분'; const h = Math.floor(seconds / 3600); const m = Math.floor((seconds % 3600) / 60); return h > 0 ? `${h}h ${m}m` : `${m}m`; }
        function openCalendar() { document.getElementById('calendarModal').style.display = 'block'; renderCalendar(); renderWeeklyChart(); }
        function closeCalendar() { document.getElementById('calendarModal').style.display = 'none'; }
        function changeMonth(offset) { currentCalDate.setMonth(currentCalDate.getMonth() + offset); renderCalendar(); }
        function renderCalendar() { const year = currentCalDate.getFullYear(); const month = currentCalDate.getMonth(); document.getElementById('calTitle').innerText = `${year}년 ${month + 1}월`; const firstDay = new Date(year, month, 1).getDay(); const daysInMonth = new Date(year, month + 1, 0).getDate(); const grid = document.getElementById('calendarGrid'); grid.innerHTML = ''; ['일','월','화','수','목','금','토'].forEach(d => grid.innerHTML += `<div style="font-weight:bold; color:var(--accent-green); font-size:10px;">${d}</div>`); for(let i=0; i<firstDay; i++) grid.innerHTML += '<div style="opacity:0;"></div>'; for(let i=1; i<=daysInMonth; i++) { const ds = `${year}-${String(month+1).padStart(2,'0')}-${String(i).padStart(2,'0')}`; const sec = dailyTime[ds] || 0; let medal = sec >= 3600 ? '💎' : (sec >= 1800 ? '🌟' : (sec >= 600 ? '⚡' : '')); const timeStr = sec > 0 ? formatTimeText(sec) : ''; grid.innerHTML += `<div class="cal-day"><div style="position:absolute; top:2px; left:4px; font-size:9px; color:#fff;">${i}</div><div style="font-size:14px; margin-top:3px;">${medal}</div><div class="cal-time">${timeStr}</div></div>`; } const todayStr = getTodayStr(new Date()); const monthPrefix = `${year}-${String(month+1).padStart(2,'0')}`; const yearPrefix = todayStr.substring(0, 4); let todaySec = dailyTime[todayStr] || 0; let monthSec = 0; let yearSec = 0; for (const k in dailyTime) { if (k.startsWith(monthPrefix)) monthSec += dailyTime[k]; if (k.startsWith(yearPrefix)) yearSec += dailyTime[k]; } const stats = document.getElementById('statsContent'); stats.innerHTML = `<div class="stats-row"><span class="stats-label">- 오늘 학습 시간</span> <span class="stats-value">${formatTimeText(todaySec)}</span></div><div class="stats-row"><span class="stats-label">- 이달 누적 학습</span> <span class="stats-value" style="color:var(--accent-green);">${formatTimeText(monthSec)}</span></div><div class="stats-row"><span class="stats-label">- 올해 누적 학습</span> <span class="stats-value">${formatTimeText(yearSec)}</span></div><hr style="border:none; border-bottom:1px solid rgba(255,255,255,0.05); margin:8px 0;"><div class="stats-row"><span class="stats-label">- 정복한 단어 수</span> <span class="stats-value" style="color:var(--accent-green);">${Object.keys(completedWords).length}개</span></div>`; }
        function renderWeeklyChart() { const container = document.getElementById('weeklyBarChart'); container.innerHTML = ''; const today = new Date(); const dayMap = [6, 0, 1, 2, 3, 4, 5]; const currentDayIdx = dayMap[today.getDay()]; const monDate = new Date(today); monDate.setDate(today.getDate() - currentDayIdx); const dayLabels = ['월','화','수','목','금','토','일']; let maxSec = 1; const weekData = []; for (let i = 0; i < 7; i++) { const targetDate = new Date(monDate); targetDate.setDate(monDate.getDate() + i); const ds = getTodayStr(targetDate); const sec = dailyTime[ds] || 0; if (sec > maxSec) maxSec = sec; weekData.push({ label: dayLabels[i], sec: sec }); } weekData.forEach(data => { const h = Math.max(2, (data.sec / maxSec) * 55); const timeStr = data.sec > 0 ? formatTimeText(data.sec) : ''; container.innerHTML += `<div class="bar-wrapper"><div class="bar-time-label">${timeStr}</div><div class="report-bar" style="height:${h}px;"></div><div style="font-size:10px; color:#fff; font-weight:bold;">${data.label}</div></div>`; }); }
        // 완료 목록: 기록 키(K)로 찾고, 암기 끝 누른 날짜를 같이 보여준다. X 버튼은 번호로 넘겨서 ' 가 든 단어도 안전
        let compKeys = [];
        function openCompletedList() {
            const container = document.getElementById('compListContainer');
            compKeys = Object.keys(completedWords);
            let html = '';
            compKeys.forEach((key, i) => {
                const item = masterWordList.find(w => w.K === key) || allWords.find(w => w.K === key) || { A: key.replace(/#\d+$/, ''), B: '?', C: '?' };
                const hits = hitCounts[key] || 0;
                const day = typeof completedWords[key] === 'string' ? completedWords[key].slice(5).replace('-', '/') + ' 완료' : '';
                html += `<div class="comp-row"><div class="c-vn">${item.A}${day ? `<div style="font-size:10px; color:var(--text-dim); font-weight:300; margin-top:2px;">${day}</div>` : ''}</div><div class="c-pron">${item.B}</div><div class="c-mean">${item.C}</div><div class="c-hit">${hits}회</div><div class="c-del"><button onclick="uncheckWord(${i})" style="background:var(--accent-red); border:none; color:#fff; border-radius:5px; padding:6px 10px; font-size:10px; cursor:pointer;">X</button></div></div>`;
            });
            container.innerHTML = html;
            document.getElementById('compModal').style.display = 'block';
        }
        function closeModal() { document.getElementById('compModal').style.display = 'none'; renderWord(); }
        function uncheckWord(i) { const key = compKeys[i]; if (key === undefined) return; if (confirm('이 단어를 숨김 해제하고 다시 공부할까요?')) { delete completedWords[key]; localStorage.setItem('vn_completed', JSON.stringify(completedWords)); openCompletedList(); } }
        function exportData() { const data = { completed: completedWords, starred: starredWords, time: dailyTime, hits: hitCounts, srs: srs, course: course, streak: streak }; const blob = new Blob([JSON.stringify(data)], { type: 'text/plain' }); const url = URL.createObjectURL(blob); const a = document.createElement('a'); a.href = url; a.download = `viet_backup_${getTodayStr(new Date())}.txt`; a.click(); }
        function importData() { document.getElementById('importFile').click(); }
        function processFile(el) { const file = el.files[0]; if (!file) return; const reader = new FileReader(); reader.onload = e => { try { const data = JSON.parse(e.target.result); if (confirm("기존 기록이 덮어씌워집니다. 진행할까요?")) { localStorage.setItem('vn_completed', JSON.stringify(data.completed)); localStorage.setItem('vn_starred', JSON.stringify(data.starred)); localStorage.setItem('vn_daily_time', JSON.stringify(data.time)); localStorage.setItem('vn_hit_counts', JSON.stringify(data.hits)); if (data.srs) localStorage.setItem('vn_srs', JSON.stringify(data.srs)); if (data.course) localStorage.setItem('vn_course', JSON.stringify(data.course)); if (data.streak) localStorage.setItem('vn_streak', JSON.stringify(data.streak)); localStorage.removeItem('vn_today'); location.reload(); } } catch(err) { alert("파일 오류"); } }; reader.readAsText(file); }
        
        if (window.speechSynthesis) {
            window.speechSynthesis.getVoices();
            window.speechSynthesis.onvoiceschanged = () => { const v = window.speechSynthesis.getVoices() || []; if (v.length === voiceCache.length) return; voiceCache = v; if (document.getElementById('settingsModal').style.display === 'block') { fillVoiceSelect('vnVoice', 'vi'); fillVoiceSelect('koVoice', 'ko'); } };
        }
        // COURSE:JS START
        // ===================== 학습 코스: 오늘의 학습 · 단계 · 미션 · 전투 퀴즈 =====================
        const STUDY_MODES = ['오늘의 학습', '단어', '문장표현', '문법', '전체랜덤'];
        const LEVEL_NAMES = ['', '왕기초', '생활 기초', '문장 만들기', '회사 생활', '현장 1', '현장 2', '업무 소통', '관리자', '고급 업무', '전문가'];
        const SRS_DAYS = [1, 1, 3, 7, 14, 30]; // 복습 상자 1~5 → 다음 복습까지 날짜
        const TAB_ORDER = ['단어', '문법', '문장표현'];
        function lsGet(k, d) { try { const v = localStorage.getItem(k); return v === null ? d : JSON.parse(v); } catch (e) { return d; } }
        function lsSet(k, v) { try { localStorage.setItem(k, JSON.stringify(v)); } catch (e) {} }
        let course = Object.assign({ level: 1, maxLevel: 1, perDay: 10, pron: 'hcm', xp: 0 }, lsGet('vn_course', {}));
        let srs = lsGet('vn_srs', {});            // { '탭|키': { b: 상자, d: 다음 복습일, c: 맞힌 수, w: 틀린 수, f: 처음 배운 날 } }
        let todayPlan = lsGet('vn_today', null);  // 오늘 뽑아 둔 새 항목·복습 항목
        let streak = lsGet('vn_streak', { last: '', count: 0 });
        let masterMap = {};
        function saveCourse() { lsSet('vn_course', course); }
        function itemKey(w) { return w.S + '|' + w.K; }
        function dayStr(offset) { const d = new Date(); d.setDate(d.getDate() + (offset || 0)); return getTodayStr(d); }
        function addDays(ds, n) { const p = ds.split('-').map(Number); const d = new Date(p[0], p[1] - 1, p[2]); d.setDate(d.getDate() + n); return getTodayStr(d); }
        function shuffleArr(a) { a = a.slice(); for (let i = a.length - 1; i > 0; i--) { const j = Math.floor(Math.random() * (i + 1)); [a[i], a[j]] = [a[j], a[i]]; } return a; }
        function chunkArr(a, n) { const out = []; for (let i = 0; i < a.length; i += n) out.push(a.slice(i, i + n)); return out; }

        // 단계(H칸 1~10). 비어 있으면 탭 안의 순서로 자동 배정 (단어 80개, 나머지 20개씩)
        function prepareMaster(list) {
            const pos = {};
            list.forEach(w => {
                pos[w.S] = (pos[w.S] || 0) + 1;
                const h = parseInt(w.H, 10);
                if (h >= 1 && h <= 10) { w.lv = h; w.lvAuto = false; }
                else { w.lv = Math.min(10, Math.floor((pos[w.S] - 1) / (w.S === '단어' ? 80 : 20)) + 1); w.lvAuto = true; }
            });
            masterMap = {}; list.forEach(w => { masterMap[itemKey(w)] = w; });
        }
        function isLearned(w) { return !!srs[itemKey(w)] || !!completedWords[w.K]; }

        // 오늘 새로 배울 항목: 지금 단계에서 아직 안 배운 것을 시트 순서대로, 단어 6 : 문법 2 : 문장 2 비율로 섞어서
        function pickNew(level, n) {
            const by = { '단어': [], '문법': [], '문장표현': [] };
            masterWordList.forEach(w => { if (w.lv === level && !isLearned(w) && by[w.S]) by[w.S].push(w); });
            const quota = { '단어': Math.round(n * 0.6), '문법': Math.round(n * 0.2) }; quota['문장표현'] = n - quota['단어'] - quota['문법'];
            const picked = {}; let count = 0;
            TAB_ORDER.forEach(t => { picked[t] = by[t].splice(0, quota[t]); count += picked[t].length; });
            TAB_ORDER.forEach(t => { while (count < n && by[t].length) { picked[t].push(by[t].shift()); count++; } });
            const out = [];
            for (let i = 0; out.length < count; i++) TAB_ORDER.forEach(t => { if (picked[t][i]) out.push(picked[t][i]); });
            return out;
        }
        function dueKeys() { const d = dayStr(0); return Object.keys(srs).filter(k => srs[k].d <= d && masterMap[k]).sort((a, b) => srs[a].d.localeCompare(srs[b].d)); }
        function ensureToday(force) {
            if (!masterWordList.length) return;
            const d = dayStr(0);
            if (!force && todayPlan && todayPlan.date === d && todayPlan.level === course.level && todayPlan.perDay === course.perDay) return;
            const same = todayPlan && todayPlan.date === d;
            const fresh = pickNew(course.level, course.perDay), freshSet = new Set(fresh.map(itemKey));
            const due = dueKeys().filter(k => !freshSet.has(k)).slice(0, Math.max(10, course.perDay * 2));
            const old = Object.keys(srs).filter(k => masterMap[k] && srs[k].b >= 2 && srs[k].d > d); // 예전에 배운 것 몇 개를 툭툭 섞는다
            todayPlan = { date: d, level: course.level, perDay: course.perDay, newKeys: fresh.map(itemKey), dueKeys: due, surpriseKeys: shuffleArr(old).slice(0, 3), done: same ? todayPlan.done : { battle: false, review: false } };
            lsSet('vn_today', todayPlan);
        }
        // 듣기용 오늘 목록: 새 항목 2개마다 복습 1개를 끼워 넣는다
        function getTodaySet() {
            ensureToday();
            if (!todayPlan) return [];
            const nw = todayPlan.newKeys.map(k => masterMap[k]).filter(Boolean);
            const rv = todayPlan.dueKeys.concat(todayPlan.surpriseKeys).map(k => masterMap[k]).filter(Boolean);
            const out = []; let r = 0;
            nw.forEach((w, i) => { out.push(w); if (i % 2 === 1 && r < rv.length) out.push(rv[r++]); });
            while (r < rv.length) out.push(rv[r++]);
            return out;
        }
        function srsAnswer(w, ok) {
            const k = itemKey(w), d = dayStr(0), s = srs[k] || { b: 0, d: d, c: 0, w: 0, f: d };
            if (ok) { s.b = Math.min(5, s.b + 1); s.c++; } else { s.b = 1; s.w++; }
            s.d = addDays(d, SRS_DAYS[s.b] || 1); s.l = d;
            srs[k] = s; lsSet('vn_srs', srs);
        }

        // ---- 미션 · 연속 학습 ----
        function missions() {
            const d = dayStr(0), plan = todayPlan && todayPlan.date === d ? todayPlan : null;
            const listen = (dailyTime[d] || 0) >= 600;
            const battle = !!(plan && (plan.done.battle || plan.newKeys.length === 0));
            const dueCount = dueKeys().length;
            const review = !!(plan && plan.done.review) || dueCount === 0;
            return { listen, battle, review, dueCount, listenMin: Math.floor((dailyTime[d] || 0) / 60), count: [listen, battle, review].filter(Boolean).length };
        }
        function streakDays() { const d = dayStr(0); return (streak.last === d || streak.last === addDays(d, -1)) ? streak.count : 0; }
        function checkStreak() {
            if (!masterWordList.length) return;
            const d = dayStr(0); if (streak.last === d) return;
            if (missions().count === 3) {
                streak.count = streak.last === addDays(d, -1) ? streak.count + 1 : 1; streak.last = d; lsSet('vn_streak', streak);
                showNotice('🔥 오늘 미션 3개 완료! 연속 ' + streak.count + '일째예요');
            }
        }
        function courseAfterLoad() { ensureToday(); renderWord(); }

        // ---- 카드에 붙는 작은 조각들 ----
        function coursePillHtml() {
            if (!masterWordList.length) return '';
            checkStreak();
            const m = missions();
            return `<div class="course-pill" onclick="openCourse()">🔥 ${streakDays()}일 · Lv.${course.level} · 미션 ${m.count}/3</div>`;
        }
        function pronText(w) { const hn = (w.hn || '').trim(); if (course.pron === 'hn' && hn) return hn; if (course.pron === 'both' && hn && hn !== w.B) return w.B + ' · 북 ' + hn; return w.B; }
        function pronHtml(w) { const t = pronText(w); return t ? '<div class="pron">[' + t + ']</div>' : ''; }
        function exExtraHtml(w) { let h = ''; if (w.lit) h += '<div class="ex-lit">직역 <b>' + w.lit + '</b></div>'; if (w.why) h += '<div class="ex-why">💡 ' + w.why + '</div>'; return h; }
        function lvChipHtml(w) { return (w.lv && !w.lvAuto) ? `<div class="lv-chip">Lv.${w.lv} ${LEVEL_NAMES[w.lv] || ''}${w.I ? ' · ' + w.I : ''}</div>` : ''; }

        // ---- 📅 오늘 메뉴 ----
        function levelStats(lv) { const items = masterWordList.filter(w => w.lv === lv); return { total: items.length, learned: items.filter(isLearned).length }; }
        function openCourse() { ensureToday(); renderCourse(); document.getElementById('courseModal').style.display = 'block'; }
        function closeCourse() { document.getElementById('courseModal').style.display = 'none'; renderWord(); }
        function missionRow(on, label) { return `<div class="cs-mission"><span class="cs-check ${on ? 'on' : ''}">${on ? '✓' : ''}</span><span>${label}</span></div>`; }
        function renderCourse() {
            const body = document.getElementById('courseBody'); if (!body) return;
            if (!masterWordList.length || !todayPlan) { body.innerHTML = '<div class="cs-card">데이터를 불러오는 중이에요…</div>'; return; }
            const m = missions(), st = levelStats(course.level), pct = st.total ? Math.round(st.learned / st.total * 100) : 0;
            const nw = todayPlan.newKeys.map(k => masterMap[k]).filter(Boolean);
            const rvN = todayPlan.dueKeys.length + todayPlan.surpriseKeys.length;
            let h = `<div class="cs-card"><div class="cs-lv"><h3>Lv.${course.level} · ${LEVEL_NAMES[course.level]}</h3><span class="cs-sub">🔥 ${streakDays()}일 연속 · ⭐ ${course.xp.toLocaleString()} XP</span></div>`;
            h += `<div class="cs-bar"><div style="width:${pct}%"></div></div><div class="cs-sub">이 단계 ${st.learned} / ${st.total}개 배움 (${pct}%)${st.total && st.learned >= st.total ? ' · 다 배웠어요! 승급 시험에 도전하세요' : ''}</div></div>`;
            h += `<div class="cs-card"><div class="cs-h">오늘 미션 ${m.count}/3</div>`;
            h += missionRow(m.listen, `🎧 듣기 10분 <span class="cs-sub">(지금 ${m.listenMin}분)</span>`);
            h += missionRow(m.battle, `⚔️ 오늘의 전투 이기기 <span class="cs-sub">(${nw.length ? '새 ' + nw.length + '개' : '새로 배울 것 없음'})</span>`);
            h += missionRow(m.review, `🔁 복습 전투 이기기 <span class="cs-sub">(${m.dueCount ? '복습할 것 ' + m.dueCount + '개' : '오늘 복습할 것 없음'})</span>`);
            h += `</div><div class="cs-btns" style="margin-bottom:12px;">`;
            h += `<button class="cs-btn green" onclick="playToday()">▶ 오늘 학습 듣기<small>새 ${nw.length} + 복습 ${rvN} · 무한 반복</small></button>`;
            h += `<button class="cs-btn hot" onclick="startBattle('today')">⚔️ 오늘의 전투<small>5문제씩 섞어서 다 맞힐 때까지</small></button>`;
            h += `<button class="cs-btn" onclick="startBattle('review')">🔁 복습 전투<small>${m.dueCount ? m.dueCount + '개 대기 중' : '예전 것 랜덤'}</small></button>`;
            h += `<button class="cs-btn gold" onclick="startBattle('boss')">👑 승급 시험<small>Lv.${course.level} 20문제 · 80% 합격</small></button>`;
            h += `</div>`;
            if (nw.length) h += `<div class="cs-card"><div class="cs-h">오늘 새로 배울 것</div><div class="cs-list">${nw.map(w => `<div><span>${w.A}</span><span>${w.C}</span></div>`).join('')}</div></div>`;
            h += `<div class="cs-card"><div class="cs-h">단계 고르기 (낮은 단계로 돌아가 복습해도 돼요)</div><div class="cs-chips">`;
            for (let i = 1; i <= 10; i++) { const ok = i <= course.maxLevel; h += `<button class="cs-chip ${i === course.level ? 'on' : ''}" ${ok ? '' : 'disabled'} onclick="setLevel(${i})" title="${LEVEL_NAMES[i]}">${ok ? '' : '🔒'}${i}</button>`; }
            h += `</div><div class="cs-sub" style="margin-top:8px;">${LEVEL_NAMES.slice(1).map((n, i) => (i + 1) + ' ' + n).join(' · ')}<br>승급 시험에 합격하면 다음 단계가 열려요.</div></div>`;
            h += `<div class="cs-card"><div class="cs-h">하루에 새로 배울 개수</div><div class="cs-chips">${[5, 10, 15, 20, 30].map(n => `<button class="cs-chip ${course.perDay === n ? 'on' : ''}" onclick="setPerDay(${n})">${n}개</button>`).join('')}</div>`;
            h += `<div class="cs-h" style="margin-top:14px;">발음 표기</div><div class="cs-chips">${[['hcm', '호치민(남부)'], ['hn', '하노이(북부)'], ['both', '둘 다']].map(([v, t]) => `<button class="cs-chip ${course.pron === v ? 'on' : ''}" onclick="setPron('${v}')">${t}</button>`).join('')}</div></div>`;
            h += `<div style="display:flex; gap:14px; flex-wrap:wrap;"><button class="cs-link" onclick="closeCourse(); openCompletedList();">📋 암기 끝 목록</button><button class="cs-link" onclick="replanToday()">🔄 오늘 배울 것 다시 뽑기</button></div>`;
            body.innerHTML = h;
        }
        function setLevel(n) { if (n > course.maxLevel) return; course.level = n; saveCourse(); ensureToday(true); if (savedStudyMode === '오늘의 학습') reloadTodayList(); renderCourse(); showNotice(`Lv.${n} ${LEVEL_NAMES[n]} 단계로 바꿨어요.`); }
        function setPerDay(n) { course.perDay = n; saveCourse(); ensureToday(true); if (savedStudyMode === '오늘의 학습') reloadTodayList(); renderCourse(); }
        function setPron(v) { course.pron = v; saveCourse(); renderCourse(); renderWord(); }
        function replanToday() { ensureToday(true); if (savedStudyMode === '오늘의 학습') reloadTodayList(); renderCourse(); showNotice('오늘 배울 것을 새로 뽑았어요.'); }
        function reloadTodayList(keepIndex) {
            const wasPlaying = isPlaying; if (wasPlaying) stopSleepMode();
            allWords = getTodaySet(); allWords.forEach((w, i) => { w.P = i + 1; });
            if (!keepIndex) savedIndex = 0;
            applyModeFilter();
            if (wasPlaying) startSleepMode();
        }
        function playToday() {
            document.getElementById('courseModal').style.display = 'none';
            savedStudyMode = '오늘의 학습'; localStorage.setItem('vn_studyMode', savedStudyMode);
            if (isPlaying) stopSleepMode();
            reloadTodayList(); initAudioEngineSynchronously(); startSleepMode();
        }

        // ===================== ⚔️ 전투 퀴즈 =====================
        // 5개씩 한 마리 몬스터. 짝 맞추기 1번 + 항목마다 문제 1개(뜻/반대로/듣기/빈칸/어순 중 랜덤).
        // 틀리면 하트 -1, 그 항목은 맨 뒤로 다시. 하트가 다 떨어지면 같은 5개로 재도전.
        const MONSTERS = ['👾', '🐲', '🦖', '🐙', '👹', '🤖', '🦂', '🐊', '🦈', '👻', '🦇', '🐺'];
        const KIND_LABEL = { vk: '뜻 고르기', kv: '베트남어 고르기 (반대로)', listen: '듣고 뜻 고르기', blank: '빈칸 채우기', order: '어순 맞추기', match: '짝 맞추기' };
        let BT = null;
        function vnTokens(s) { return String(s || '').replace(/[.,!?;:"“”…]/g, ' ').split(/\s+/).filter(Boolean); }
        function canOrder(w) { const n = vnTokens(w.D).length; return n >= 3 && n <= 9; }
        function canBlank(w) { return !!w.D && w.A.length <= 25 && w.D.toLowerCase().includes(w.A.toLowerCase()) && w.D.trim().toLowerCase() !== w.A.trim().toLowerCase(); }
        function pickType(w, prev) {
            let t = ['vk', 'kv', 'vk', 'kv'];
            if (!savedMuteMode && window.speechSynthesis) t.push('listen', 'listen');
            if (canOrder(w)) t.push('order', 'order');
            if (w.S !== '단어' && canBlank(w)) t.push('blank', 'blank', 'blank');
            if (prev) { const f = t.filter(x => x !== prev); if (f.length) t = f; }
            return t[Math.floor(Math.random() * t.length)];
        }
        // 보기 4개: 같은 탭·비슷한 단계에서 오답 3개를 뽑는다
        function optionPool(w, field) {
            const v0 = (w[field] || '').trim();
            let pool = masterWordList.filter(x => x !== w && (x[field] || '').trim() && (x[field] || '').trim() !== v0);
            const near = pool.filter(x => x.S === w.S && Math.abs((x.lv || 1) - (w.lv || 1)) <= 1);
            if (near.length >= 8) pool = near; else { const same = pool.filter(x => x.S === w.S); if (same.length >= 8) pool = same; }
            const out = [], seen = new Set([v0]);
            for (const x of shuffleArr(pool)) { const v = x[field].trim(); if (!seen.has(v)) { seen.add(v); out.push(v); } if (out.length >= 3) break; }
            return shuffleArr(out.concat([v0]));
        }
        function sayVN(text) {
            if (savedMuteMode || !window.speechSynthesis || !text) return;
            try {
                if (window.speechSynthesis.speaking || window.speechSynthesis.pending) window.speechSynthesis.cancel();
                const m = new SpeechSynthesisUtterance(text); m.lang = 'vi-VN'; const v = pickVoice('vi'); if (v) m.voice = v;
                m.rate = parseFloat(localStorage.getItem('vn_voiceRate') || '0.9'); m.volume = parseFloat(savedAppVolume);
                window.keepAliveUtterances.push(m);
                m.onend = m.onerror = () => { const i = window.keepAliveUtterances.indexOf(m); if (i > -1) window.keepAliveUtterances.splice(i, 1); };
                window.speechSynthesis.speak(m);
            } catch (e) {}
        }
        function startBattle(kind) {
            if (!masterWordList.length) { showNotice('데이터를 불러오는 중이에요. 잠시 후 다시 눌러 주세요.'); return; }
            ensureToday();
            let items = [], title = '';
            if (kind === 'today') {
                items = todayPlan.newKeys.map(k => masterMap[k]).filter(Boolean); title = '⚔️ 오늘의 전투';
                if (!items.length) { showNotice('오늘 새로 배울 것이 없어요. 승급 시험에 도전하거나 단계를 바꿔 보세요.'); return; }
            } else if (kind === 'review') {
                items = dueKeys().map(k => masterMap[k]); title = '🔁 복습 전투';
                if (!items.length) { items = shuffleArr(Object.keys(srs).filter(k => masterMap[k])).slice(0, 10).map(k => masterMap[k]); title = '🔁 랜덤 복습 전투'; }
                if (!items.length) { showNotice('아직 배운 게 없어요. 오늘의 전투부터 해 보세요!'); return; }
                items = items.slice(0, 30);
            } else if (kind === 'boss') {
                const lvItems = masterWordList.filter(w => w.lv === course.level);
                if (lvItems.length < 4) { showNotice('이 단계에는 항목이 부족해요.'); return; }
                const learned = lvItems.filter(isLearned);
                items = shuffleArr(learned.length >= 20 ? learned : lvItems).slice(0, 20); title = `👑 Lv.${course.level} 승급 시험`;
            } else {
                const list = words.length ? words : allWords;
                const s = Math.max(0, Math.min(savedIndex, list.length - 10)); items = list.slice(s, s + 10); title = '⚔️ 지금 목록 전투';
            }
            if (items.length < 2) { showNotice('문제를 내려면 항목이 2개 이상 필요해요.'); return; }
            if (isPlaying) stopSleepMode();
            document.getElementById('courseModal').style.display = 'none';
            BT = { kind, title, items, squads: [], si: 0, queue: [], hearts: 3, maxHearts: 3, combo: 0, maxCombo: 0, firstOk: 0, firstTotal: 0, xp: 0, seen: {}, q: null, locked: false, lastType: null };
            if (kind === 'boss') { BT.maxHearts = BT.hearts = 5; BT.mon = '🐉'; BT.queue = items.map(w => mkQ(w)); BT.monMax = BT.queue.length; }
            else {
                BT.squads = chunkArr(shuffleArr(items), 5);
                if (BT.squads.length > 1 && BT.squads[BT.squads.length - 1].length < 3) { const last = BT.squads.pop(); BT.squads[BT.squads.length - 1].push(...last); }
                startSquad();
            }
            document.getElementById('battle').style.display = 'block';
            nextQ();
        }
        function mkQ(w) { const type = pickType(w, BT.lastType); BT.lastType = type; return { w, type }; }
        function startSquad() {
            const sq = BT.squads[BT.si];
            BT.queue = [];
            if (sq.length >= 3) BT.queue.push({ type: 'match', ws: sq.slice(0, 6) });
            shuffleArr(sq).forEach(w => BT.queue.push(mkQ(w)));
            BT.monMax = BT.queue.length; BT.hearts = BT.maxHearts; BT.mon = MONSTERS[Math.floor(Math.random() * MONSTERS.length)];
        }
        function btTop() {
            document.getElementById('btTitle').textContent = BT.title + (BT.squads.length > 1 ? ` · ${BT.si + 1}/${BT.squads.length}` : '');
            document.getElementById('btHearts').textContent = '❤️'.repeat(Math.max(0, BT.hearts)) + '🤍'.repeat(Math.max(0, BT.maxHearts - BT.hearts));
            const mon = document.getElementById('btMon'); if (mon.textContent !== BT.mon) { mon.textContent = BT.mon; mon.className = 'bt-mon'; }
            document.getElementById('btHp').style.width = (BT.monMax ? BT.queue.length / BT.monMax * 100 : 0) + '%';
            document.getElementById('btMeta').innerHTML = `남은 공격 ${BT.queue.length}${BT.combo >= 2 ? ` · <span class="bt-combo">🔥 ${BT.combo} 콤보</span>` : ''} · ⭐ ${BT.xp} XP`;
        }
        function nextQ() {
            if (!BT) return;
            clearTimeout(BT.autoNext);
            document.getElementById('btFb').innerHTML = '';
            document.getElementById('battle').classList.remove('shake');
            if (!BT.queue.length) return squadWin();
            const mon = document.getElementById('btMon'); mon.className = 'bt-mon';
            btTop();
            BT.q = BT.queue[0]; BT.locked = false;
            const q = BT.q, el = document.getElementById('btQ');
            let h = `<div class="bt-kind">${KIND_LABEL[q.type]}</div>`;
            if (q.type === 'match') { el.innerHTML = h + matchHtml(q); bindMatch(q); return; }
            const w = q.w;
            if (q.type === 'vk') { h += `<div class="bt-prompt">${w.A}</div><button class="bt-say" onclick="sayVN(BT.q.w.A)">🔊 발음 듣기</button>` + optsHtml(optionPool(w, 'C')); setTimeout(() => sayVN(w.A), 120); }
            else if (q.type === 'listen') { h += `<button class="bt-say big" onclick="sayVN(BT.q.w.A)" aria-label="다시 듣기">🔊</button><div class="bt-hint">잘 듣고 뜻을 고르세요 (스피커를 누르면 다시 들려요)</div>` + optsHtml(optionPool(w, 'C')); setTimeout(() => sayVN(w.A), 150); }
            else if (q.type === 'kv') { h += `<div class="bt-prompt kr">${w.C}</div><div class="bt-hint">베트남어로 뭐라고 할까요?</div>` + optsHtml(optionPool(w, 'A')); }
            else if (q.type === 'blank') {
                const re = new RegExp(w.A.trim().replace(/[.*+?^${}()|[\]\\]/g, '\\$&'), 'i');
                h += `<div class="bt-prompt sent">${w.D.replace(re, '<span style="color:var(--accent-gold)">____</span>')}</div><div class="bt-hint">${w.F}</div>` + optsHtml(optionPool(w, 'A'));
            }
            else if (q.type === 'order') h += orderHtml(w);
            el.innerHTML = h;
            if (q.type === 'order') bindOrder();
        }
        function optsHtml(opts) { BT.opts = opts; return '<div class="bt-opts">' + opts.map((o, i) => `<button class="bt-opt" onclick="pickOpt(${i})"><span class="bt-num">${i + 1}</span>${o}</button>`).join('') + '</div>'; }
        function correctValue(q) { return (q.type === 'kv' || q.type === 'blank') ? q.w.A.trim() : q.w.C.trim(); }
        function pickOpt(i) {
            if (!BT || BT.locked) return; BT.locked = true;
            const q = BT.q, right = correctValue(q), ok = BT.opts[i] === right;
            document.querySelectorAll('#btQ .bt-opts .bt-opt').forEach((b, j) => { b.disabled = true; if (BT.opts[j] === right) b.classList.add('ok'); else if (j === i) b.classList.add('no'); });
            answer(ok);
        }
        function hitMonster() { const mon = document.getElementById('btMon'); mon.classList.remove('hit'); void mon.offsetWidth; mon.classList.add('hit'); }
        function answer(ok) {
            const q = BT.q, w = q.w;
            if (w) { const k = itemKey(w); if (!(k in BT.seen)) { BT.seen[k] = ok; BT.firstTotal++; if (ok) BT.firstOk++; srsAnswer(w, ok); } }
            if (ok) { BT.combo++; BT.maxCombo = Math.max(BT.maxCombo, BT.combo); BT.xp += 10 + Math.min(BT.combo, 10) * 2; BT.queue.shift(); hitMonster(); }
            else {
                BT.combo = 0; BT.hearts--;
                const cur = BT.queue.shift(); BT.queue.push(mkQ(cur.w));
                const bt = document.getElementById('battle'); bt.classList.remove('shake'); void bt.offsetWidth; bt.classList.add('shake');
            }
            btTop();
            showFb(ok, q);
        }
        const OK_MSG = ['✔ 정답! 공격 성공', '✔ 좋아요! 몬스터가 휘청해요', '✔ 맞았어요!', '✔ 크리티컬 히트!'];
        function showFb(ok, q, extra) {
            const w = q.w;
            let h = `<div class="bt-fb-box ${ok ? 'ok' : 'no'}"><div class="bt-fb-title">${ok ? OK_MSG[Math.floor(Math.random() * OK_MSG.length)] : '✖ 아까워요! 이 문제는 다시 나와요'}</div>`;
            if (w) {
                h += `<div class="bt-fb-vn">${w.A} <span class="bt-fb-pron">[${pronText(w)}]</span></div><div class="bt-fb-line">${w.C}</div>`;
                if (q.type === 'order' || q.type === 'blank' || !ok) {
                    if (w.D) h += `<div class="bt-fb-line"><b style="color:var(--accent-green)">${w.D}</b><br>${w.F}</div>`;
                    if (w.lit) h += `<div class="bt-fb-line dim">직역: ${w.lit}</div>`;
                    if (w.why) h += `<div class="bt-fb-line why">💡 ${w.why}</div>`;
                }
            }
            if (extra) h += `<div class="bt-fb-line">${extra}</div>`;
            h += `<button class="bt-next" id="btNext" onclick="afterFb()">${BT.hearts <= 0 ? '결과 보기' : '다음 ▶'}</button></div>`;
            const fb = document.getElementById('btFb'); fb.innerHTML = h;
            const nb = document.getElementById('btNext'); if (nb) nb.focus({ preventScroll: true });
            fb.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
            if (w) sayVN(q.type === 'order' || q.type === 'blank' ? w.D : w.A);
            if (ok && q.type !== 'order' && q.type !== 'blank') BT.autoNext = setTimeout(afterFb, 1800);
        }
        function afterFb() { if (!BT) return; clearTimeout(BT.autoNext); if (BT.hearts <= 0) return defeat(); nextQ(); }

        // 짝 맞추기: 왼쪽 번호(1~5)와 오른쪽 글자(가~마)를 짝짓기. 실수해도 하트는 안 깎인다
        function matchHtml(q) {
            q.left = shuffleArr(q.ws); q.right = shuffleArr(q.ws); q.sel = -1; q.done = 0; q.miss = 0;
            const ko = '가나다라마바';
            return `<div class="bt-hint">왼쪽 베트남어를 누르고, 맞는 뜻을 오른쪽에서 고르세요</div><div class="bt-match">` +
                `<div class="bt-opts">${q.left.map((w, i) => `<button class="bt-opt" data-side="L" data-i="${i}"><span class="bt-num">${i + 1}</span>${w.A}</button>`).join('')}</div>` +
                `<div class="bt-opts">${q.right.map((w, i) => `<button class="bt-opt" data-side="R" data-i="${i}"><span class="bt-num">${ko[i]}</span>${w.C}</button>`).join('')}</div></div>`;
        }
        function bindMatch(q) {
            const root = document.getElementById('btQ');
            root.querySelectorAll('.bt-match .bt-opt').forEach(b => b.addEventListener('click', () => {
                if (!BT || BT.locked || b.classList.contains('done')) return;
                const i = +b.dataset.i;
                if (b.dataset.side === 'L') { q.sel = i; root.querySelectorAll('[data-side="L"]').forEach(x => x.classList.toggle('sel', x === b)); sayVN(q.left[i].A); return; }
                if (q.sel < 0) { showNotice('왼쪽 베트남어를 먼저 고르세요'); return; }
                const L = root.querySelector(`[data-side="L"][data-i="${q.sel}"]`);
                if (q.left[q.sel] === q.right[i]) {
                    L.classList.remove('sel'); L.classList.add('ok', 'done'); b.classList.add('ok', 'done'); q.sel = -1; q.done++;
                    BT.combo++; BT.maxCombo = Math.max(BT.maxCombo, BT.combo); btTop();
                    if (q.done === q.left.length) { BT.locked = true; BT.xp += 10 * q.left.length; BT.queue.shift(); hitMonster(); btTop(); showFb(true, q, q.miss ? `실수 ${q.miss}번. 헷갈린 건 다음 문제에서 하나씩 다시 나와요.` : '실수 없이 전부 맞혔어요!'); }
                } else { q.miss++; BT.combo = 0; b.classList.add('no'); setTimeout(() => b.classList.remove('no'), 500); btTop(); }
            }));
        }
        // 어순 맞추기: 한국어 뜻을 보고 베트남어 조각을 순서대로 누른다
        function orderHtml(w) {
            const toks = vnTokens(w.D);
            let pool = shuffleArr(toks.map((t, i) => ({ t, i })));
            if (pool.every((p, j) => p.i === j)) pool = pool.reverse();
            BT.ord = { toks, pool, placed: [] };
            return `<div class="bt-prompt kr" style="font-size:20px;">${w.F}</div><div class="bt-hint">베트남어 어순대로 조각을 눌러 문장을 만드세요</div><div class="bt-slots" id="btSlots"></div>` +
                `<div class="bt-pool" id="btPool">${pool.map((p, j) => `<button class="bt-tile" data-j="${j}">${p.t}</button>`).join('')}</div>` +
                `<div class="bt-row"><button class="bt-opt" onclick="ordClear()">↺ 다시 놓기</button><button class="bt-opt go" onclick="ordCheck()">확인</button></div>`;
        }
        function bindOrder() { document.querySelectorAll('#btPool .bt-tile').forEach(b => b.addEventListener('click', () => { if (BT.locked || b.classList.contains('used')) return; b.classList.add('used'); BT.ord.placed.push(+b.dataset.j); ordRender(); })); }
        function ordRender() { document.getElementById('btSlots').innerHTML = BT.ord.placed.map((j, n) => `<button class="bt-tile" onclick="ordUndo(${n})">${BT.ord.pool[j].t}</button>`).join(''); }
        function ordUndo(n) { if (BT.locked) return; const j = BT.ord.placed.splice(n, 1)[0]; const b = document.querySelector(`#btPool .bt-tile[data-j="${j}"]`); if (b) b.classList.remove('used'); ordRender(); }
        function ordClear() { if (BT.locked) return; BT.ord.placed = []; document.querySelectorAll('#btPool .bt-tile').forEach(b => b.classList.remove('used')); ordRender(); }
        function ordCheck() {
            if (!BT || BT.locked) return;
            if (BT.ord.placed.length < BT.ord.toks.length) { showNotice('조각을 모두 놓아 주세요'); return; }
            BT.locked = true;
            const built = BT.ord.placed.map(j => BT.ord.pool[j].t.toLowerCase()).join(' ');
            const ok = built === BT.ord.toks.map(t => t.toLowerCase()).join(' ');
            document.getElementById('btSlots').style.borderColor = ok ? 'var(--accent-green)' : 'var(--accent-red)';
            answer(ok);
        }
        function squadWin() {
            BT.xp += 30;
            document.getElementById('btMon').className = 'bt-mon dead';
            document.getElementById('btHp').style.width = '0%';
            if (BT.kind !== 'boss' && BT.si < BT.squads.length - 1) {
                BT.si++; startSquad();
                document.getElementById('btQ').innerHTML = `<div class="bt-result"><h2>💥 몬스터 처치!</h2><div class="bt-hint">다음 몬스터가 다가와요 (${BT.si + 1}/${BT.squads.length})</div><button class="bt-next" onclick="nextQ()">다음 전투 ▶</button></div>`;
                return;
            }
            finish(true);
        }
        function defeat() {
            if (BT.kind === 'boss') return finish(false);
            document.getElementById('btQ').innerHTML = `<div class="bt-result"><h2>💔 이번엔 졌어요</h2><div class="bt-hint">하트가 다 떨어졌어요. 같은 문제들로 다시 붙어 봐요. 틀린 건 또 나와요!</div><button class="bt-next" onclick="retrySquad()">다시 도전 ▶</button></div>`;
            document.getElementById('btFb').innerHTML = '';
        }
        function retrySquad() { startSquad(); nextQ(); }
        function finish(win) {
            const acc = BT.firstTotal ? Math.round(BT.firstOk / BT.firstTotal * 100) : 0, d = dayStr(0);
            let head, sub;
            if (BT.kind === 'boss') {
                const pass = win && acc >= 80;
                if (pass) {
                    const from = course.level;
                    if (course.level < 10) { course.maxLevel = Math.max(course.maxLevel, course.level + 1); course.level++; }
                    BT.xp += 200;
                    head = course.level > from ? `🎉 합격! Lv.${course.level} 승급` : '🏆 최고 단계 합격!';
                    sub = course.level > from ? `${LEVEL_NAMES[course.level]} 단계가 열렸어요. 오늘 배울 것도 새 단계로 바꿨어요.` : '10단계 전문가 시험까지 통과했어요!';
                    ensureToday(true);
                } else { head = '😤 아쉽게 불합격'; sub = `첫 시도 정답률 ${acc}% (합격은 80%). 틀린 건 내일 복습에 나와요. 다시 도전!`; }
            } else {
                head = '🏆 승리!'; sub = '모든 몬스터를 물리쳤어요. 맞힌 건 1일 → 3일 → 7일 간격으로 복습에 다시 나와요.';
                if (todayPlan && todayPlan.date === d) { if (BT.kind === 'today') todayPlan.done.battle = true; if (BT.kind === 'review') todayPlan.done.review = true; lsSet('vn_today', todayPlan); }
            }
            course.xp += BT.xp; saveCourse(); checkStreak();
            document.getElementById('btQ').innerHTML = `<div class="bt-result"><h2>${head}</h2><div class="bt-hint">${sub}</div>` +
                `<div class="bt-stats"><div class="bt-stat"><b>${acc}%</b><span>첫 시도 정답률</span></div><div class="bt-stat"><b>${BT.maxCombo}</b><span>최대 콤보</span></div><div class="bt-stat"><b>+${BT.xp}</b><span>XP</span></div></div>` +
                `<div class="bt-row"><button class="bt-next ghost" onclick="exitBattle()">닫기</button><button class="bt-next" onclick="startBattle('${BT.kind}')">한 번 더 (섞어서)</button></div></div>`;
            document.getElementById('btFb').innerHTML = '';
            document.getElementById('btMeta').innerHTML = `⭐ 총 ${course.xp.toLocaleString()} XP`;
        }
        function exitBattle() {
            if (BT) clearTimeout(BT.autoNext);
            BT = null;
            if (window.speechSynthesis) window.speechSynthesis.cancel();
            const bt = document.getElementById('battle'); bt.style.display = 'none'; bt.classList.remove('shake');
            if (savedStudyMode === '오늘의 학습') reloadTodayList(true); else renderWord();
        }
        // PC에서는 키보드로: 1~4 보기 고르기, Enter 다음, Esc 나가기
        document.addEventListener('keydown', e => {
            if (!BT || document.getElementById('battle').style.display !== 'block') return;
            if (e.key === 'Escape') { exitBattle(); return; }
            if (e.key === 'Enter' && document.getElementById('btNext')) { e.preventDefault(); afterFb(); return; }
            const n = parseInt(e.key, 10);
            if (n >= 1 && n <= 4 && BT.q && ['vk', 'kv', 'listen', 'blank'].includes(BT.q.type) && !BT.locked) pickOpt(n - 1);
        });
        // COURSE:JS END
    </script>
</body>
</html>
