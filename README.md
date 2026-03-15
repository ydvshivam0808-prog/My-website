# My-website<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ETERNAL — Timeless Luxury</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Cinzel:wght@400;600;900&family=Raleway:wght@200;300;400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg:#0a0804;--surface:#111009;--surface2:#16140e;
  --accent:#c9a84c;--accent2:#e8d5a3;--accent-dim:rgba(201,168,76,0.15);
  --text:#f0ead6;--text-muted:#8a7e68;--text-dim:#4a4438;
  --fd:'Cinzel',serif;--fb:'Cormorant Garamond',serif;--fu:'Raleway',sans-serif;
  --r:0px;
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{background:var(--bg);color:var(--text);font-family:var(--fb);overflow-x:hidden;}
::-webkit-scrollbar{width:4px;}
::-webkit-scrollbar-track{background:var(--bg);}
::-webkit-scrollbar-thumb{background:var(--accent);border-radius:2px;}

/* CURSOR */
.cur,.cur-r{position:fixed;pointer-events:none;z-index:9999;border-radius:50%;transform:translate(-50%,-50%);}
.cur{width:8px;height:8px;background:var(--accent);transition:width .2s,height .2s;}
.cur-r{width:32px;height:32px;border:1px solid var(--accent);opacity:.4;transition:left .12s ease-out,top .12s ease-out;}

/* ── NAV ── */
nav{position:fixed;top:0;left:0;right:0;z-index:300;backdrop-filter:blur(24px);background:rgba(10,8,4,.85);border-bottom:1px solid rgba(201,168,76,.1);}
.nav-top{display:flex;align-items:center;justify-content:space-between;padding:20px 60px;}
.nav-logo{font-family:var(--fd);font-size:20px;font-weight:900;letter-spacing:.4em;color:var(--accent);text-decoration:none;cursor:pointer;}
.nav-logo img{height:30px;object-fit:contain;}
.nav-bottom{display:flex;align-items:center;gap:0;border-top:1px solid rgba(201,168,76,.07);position:relative;}
.nav-item{font-family:var(--fu);font-size:10px;letter-spacing:.3em;text-transform:uppercase;font-weight:400;color:var(--text-muted);padding:13px 28px;cursor:pointer;transition:color .3s;position:relative;white-space:nowrap;}
.nav-item:hover,.nav-item.active{color:var(--accent);}
.nav-item::after{content:'';position:absolute;bottom:0;left:20px;right:20px;height:1px;background:var(--accent);transform:scaleX(0);transition:transform .3s;}
.nav-item:hover::after,.nav-item.active::after{transform:scaleX(1);}

/* CATEGORY DROPDOWN */
.cat-dropdown{position:absolute;top:100%;left:0;right:0;background:rgba(10,8,4,.97);backdrop-filter:blur(20px);border-bottom:1px solid rgba(201,168,76,.1);padding:32px 60px;display:none;z-index:200;}
.cat-dropdown.open{display:flex;gap:16px;flex-wrap:wrap;}
.cat-chip{font-family:var(--fu);font-size:10px;letter-spacing:.3em;text-transform:uppercase;color:var(--text-muted);border:1px solid rgba(201,168,76,.2);padding:10px 24px;cursor:pointer;transition:all .3s;}
.cat-chip:hover,.cat-chip.active{color:var(--accent);border-color:var(--accent);background:rgba(201,168,76,.06);}

/* ── PAGES ── */
.page{display:none;padding-top:100px;min-height:100vh;}
.page.active{display:block;}

/* ── HERO PAGE ── */
#page-home{padding-top:0;}
.hero{min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;position:relative;overflow:hidden;}
.hero-bg{position:absolute;inset:0;background:radial-gradient(ellipse 80% 60% at 50% 55%,rgba(201,168,76,.06),transparent 70%);}
.hero-grain{position:absolute;inset:0;opacity:.035;background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='4'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");background-size:200px;}
.hero-eyebrow{font-family:var(--fu);font-size:10px;letter-spacing:.5em;text-transform:uppercase;color:var(--accent);margin-bottom:24px;opacity:0;animation:fadeUp 1s .4s forwards;}
.hero-title{font-family:var(--fd);font-size:clamp(64px,11vw,148px);font-weight:900;letter-spacing:.18em;background:linear-gradient(135deg,var(--accent),var(--accent2) 40%,var(--accent));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;opacity:0;animation:fadeUp 1s .6s forwards;}
.hero-tag{font-family:var(--fb);font-style:italic;font-size:clamp(15px,1.8vw,20px);color:var(--text-muted);margin-top:16px;letter-spacing:.1em;opacity:0;animation:fadeUp 1s .8s forwards;}
.hero-div{width:70px;height:1px;background:linear-gradient(to right,transparent,var(--accent),transparent);margin:32px auto;opacity:0;animation:fadeUp 1s 1s forwards;}
.hero-cta{display:flex;gap:20px;opacity:0;animation:fadeUp 1s 1.1s forwards;}
.scroll-ind{position:absolute;bottom:36px;left:50%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;gap:8px;opacity:0;animation:fadeUp 1s 1.8s forwards;}
.scroll-ind span{font-family:var(--fu);font-size:9px;letter-spacing:.4em;text-transform:uppercase;color:var(--text-muted);}
.scroll-line{width:1px;height:44px;background:linear-gradient(to bottom,var(--accent),transparent);animation:pulse 2s infinite;}
@keyframes fadeUp{from{opacity:0;transform:translateY(26px)}to{opacity:1;transform:translateY(0)}}
@keyframes pulse{0%,100%{opacity:.3}50%{opacity:1}}

/* MARQUEE */
.mq{overflow:hidden;border-top:1px solid rgba(201,168,76,.12);border-bottom:1px solid rgba(201,168,76,.12);padding:18px 0;background:var(--surface);}
.mq-track{display:flex;animation:mq 22s linear infinite;white-space:nowrap;}
.mq-item{font-family:var(--fd);font-size:12px;letter-spacing:.3em;text-transform:uppercase;color:var(--text-muted);padding:0 44px;flex-shrink:0;}
.mq-item span{color:var(--accent);margin-right:44px;}
@keyframes mq{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* ── BTNS ── */
.btn-p{font-family:var(--fu);font-size:10px;letter-spacing:.35em;text-transform:uppercase;color:var(--bg);background:var(--accent);border:none;padding:14px 36px;cursor:pointer;transition:all .3s;text-decoration:none;display:inline-block;}
.btn-p:hover{background:var(--accent2);transform:translateY(-2px);}
.btn-g{font-family:var(--fu);font-size:10px;letter-spacing:.35em;text-transform:uppercase;color:var(--accent);background:transparent;border:1px solid rgba(201,168,76,.35);padding:14px 36px;cursor:pointer;transition:all .3s;text-decoration:none;display:inline-block;}
.btn-g:hover{border-color:var(--accent);background:rgba(201,168,76,.05);transform:translateY(-2px);}

/* ── SECTION COMMONS ── */
.sec{padding:100px 60px;}
.sec-label{font-family:var(--fu);font-size:9px;letter-spacing:.6em;text-transform:uppercase;color:var(--accent);text-align:center;margin-bottom:14px;}
.sec-title{font-family:var(--fd);font-size:clamp(28px,4vw,50px);font-weight:400;text-align:center;letter-spacing:.1em;margin-bottom:72px;}

/* ── FEATURED (HOME) ── */
.featured-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:3px;max-width:1300px;margin:0 auto;}
.prod-card{position:relative;overflow:hidden;cursor:pointer;background:var(--surface);aspect-ratio:3/4;}
.prod-card::after{content:'';position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.85) 0%,transparent 55%);z-index:2;transition:opacity .5s;}
.prod-card:hover::after{opacity:.97;}
.prod-card-img{width:100%;height:100%;object-fit:cover;transition:transform .8s cubic-bezier(.25,.46,.45,.94);display:block;}
.prod-card-ph{width:100%;height:100%;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:16px;background:var(--surface);transition:transform .8s cubic-bezier(.25,.46,.45,.94);}
.prod-card:hover .prod-card-img,.prod-card:hover .prod-card-ph{transform:scale(1.06);}
.prod-card-info{position:absolute;bottom:0;left:0;right:0;padding:36px 32px;z-index:3;transform:translateY(14px);transition:transform .4s;}
.prod-card:hover .prod-card-info{transform:translateY(0);}
.pc-num{font-family:var(--fu);font-size:9px;letter-spacing:.45em;color:var(--accent);text-transform:uppercase;margin-bottom:8px;}
.pc-name{font-family:var(--fd);font-size:22px;letter-spacing:.07em;font-weight:600;margin-bottom:5px;}
.pc-sub{font-family:var(--fb);font-style:italic;font-size:14px;color:var(--text-muted);margin-bottom:12px;}
.pc-price{font-family:var(--fu);font-size:12px;letter-spacing:.2em;color:var(--accent);}
.pc-btn{display:inline-block;margin-top:16px;font-family:var(--fu);font-size:9px;letter-spacing:.35em;text-transform:uppercase;color:var(--bg);background:var(--accent);border:none;padding:10px 22px;cursor:pointer;transition:all .3s;opacity:0;transform:translateY(8px);transition:opacity .35s .05s,transform .35s .05s,background .3s;}
.prod-card:hover .pc-btn{opacity:1;transform:translateY(0);}

/* HOT BADGE */
.hot-badge{position:absolute;top:16px;right:16px;z-index:4;font-family:var(--fu);font-size:8px;letter-spacing:.3em;text-transform:uppercase;background:var(--accent);color:var(--bg);padding:5px 12px;}

/* ── LIST PAGE ── */
.list-container{max-width:1100px;margin:0 auto;padding:0 60px 80px;}
.list-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:48px;padding-bottom:20px;border-bottom:1px solid rgba(201,168,76,.12);}
.list-header h2{font-family:var(--fd);font-size:32px;letter-spacing:.1em;font-weight:400;}
.list-count{font-family:var(--fu);font-size:10px;letter-spacing:.3em;color:var(--text-muted);text-transform:uppercase;}
.list-item{display:flex;align-items:center;gap:32px;padding:24px 0;border-bottom:1px solid rgba(201,168,76,.06);cursor:pointer;transition:all .3s;position:relative;}
.list-item::before{content:'';position:absolute;left:-16px;top:0;bottom:0;width:2px;background:var(--accent);transform:scaleY(0);transition:transform .3s;}
.list-item:hover{padding-left:20px;}
.list-item:hover::before{transform:scaleY(1);}
.list-img{width:80px;height:80px;object-fit:cover;flex-shrink:0;background:var(--surface);}
.list-img-ph{width:80px;height:80px;flex-shrink:0;background:var(--surface);display:flex;align-items:center;justify-content:center;}
.list-info{flex:1;}
.li-name{font-family:var(--fd);font-size:20px;letter-spacing:.06em;font-weight:600;margin-bottom:6px;}
.li-sub{font-family:var(--fb);font-style:italic;font-size:14px;color:var(--text-muted);margin-bottom:8px;}
.li-desc{font-family:var(--fu);font-size:11px;color:var(--text-dim);letter-spacing:.05em;line-height:1.7;max-width:500px;}
.list-meta{text-align:right;flex-shrink:0;}
.li-price{font-family:var(--fu);font-size:14px;letter-spacing:.15em;color:var(--accent);margin-bottom:8px;}
.li-cat{font-family:var(--fu);font-size:9px;letter-spacing:.3em;text-transform:uppercase;color:var(--text-dim);}
.li-views{font-family:var(--fu);font-size:9px;letter-spacing:.2em;color:var(--text-muted);margin-top:6px;}

/* ── PRODUCT DETAIL PAGE ── */
#page-product{padding-top:110px;}
.prod-detail{max-width:1300px;margin:0 auto;padding:0 60px 120px;}
.pd-back{font-family:var(--fu);font-size:10px;letter-spacing:.3em;text-transform:uppercase;color:var(--text-muted);cursor:pointer;transition:color .3s;margin-bottom:48px;display:inline-flex;align-items:center;gap:10px;}
.pd-back:hover{color:var(--accent);}
.pd-grid{display:grid;grid-template-columns:1fr 1fr;gap:80px;align-items:start;}
.pd-img-main{aspect-ratio:1;background:var(--surface);overflow:hidden;border:1px solid rgba(201,168,76,.1);position:relative;}
.pd-img-main img{width:100%;height:100%;object-fit:cover;}
.pd-img-ph{width:100%;height:100%;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:20px;}
.pd-img-thumbs{display:flex;gap:10px;margin-top:12px;}
.pd-thumb{width:70px;height:70px;background:var(--surface);border:1px solid rgba(201,168,76,.1);overflow:hidden;cursor:pointer;transition:border-color .3s;flex-shrink:0;}
.pd-thumb.active,.pd-thumb:hover{border-color:var(--accent);}
.pd-thumb img{width:100%;height:100%;object-fit:cover;}
.pd-info{}
.pd-eyebrow{font-family:var(--fu);font-size:9px;letter-spacing:.5em;text-transform:uppercase;color:var(--accent);margin-bottom:18px;}
.pd-name{font-family:var(--fd);font-size:clamp(32px,4vw,52px);letter-spacing:.06em;font-weight:600;line-height:1.1;margin-bottom:12px;}
.pd-subtitle{font-family:var(--fb);font-style:italic;font-size:20px;color:var(--text-muted);margin-bottom:24px;}
.pd-price{font-family:var(--fd);font-size:28px;letter-spacing:.1em;color:var(--accent);margin-bottom:32px;}
.pd-divider{width:100%;height:1px;background:rgba(201,168,76,.12);margin:32px 0;}
.pd-desc{font-size:17px;line-height:1.9;color:var(--text-muted);font-weight:300;margin-bottom:36px;}
.pd-features{margin-bottom:36px;}
.pd-feat-title{font-family:var(--fu);font-size:10px;letter-spacing:.4em;text-transform:uppercase;color:var(--accent);margin-bottom:20px;}
.pd-feat-list{display:flex;flex-direction:column;gap:12px;}
.pd-feat-item{display:flex;align-items:flex-start;gap:14px;font-family:var(--fb);font-size:16px;color:var(--text-muted);line-height:1.6;}
.pd-feat-dot{width:6px;height:6px;border-radius:50%;background:var(--accent);flex-shrink:0;margin-top:8px;}
.pd-specs-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:40px;}
.pd-spec{border-left:2px solid rgba(201,168,76,.25);padding-left:16px;}
.pd-spec-label{font-family:var(--fu);font-size:9px;letter-spacing:.4em;text-transform:uppercase;color:var(--text-dim);margin-bottom:5px;}
.pd-spec-val{font-family:var(--fb);font-size:16px;color:var(--text);}
.pd-actions{display:flex;gap:16px;}

/* ── HOT PAGE ── */
.hot-section{max-width:1200px;margin:0 auto;padding:0 60px 80px;}
.hot-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:3px;}
.hot-rank{position:absolute;top:14px;left:14px;z-index:4;font-family:var(--fd);font-size:28px;font-weight:900;color:rgba(201,168,76,.15);letter-spacing:.05em;}

/* ── CATEGORY PAGE ── */
.cat-section{max-width:1200px;margin:0 auto;padding:0 60px 80px;}
.cat-filter-bar{display:flex;gap:12px;flex-wrap:wrap;margin-bottom:64px;justify-content:center;}
.cat-products{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:3px;}

/* ── HELP / AI PAGE ── */
.help-section{max-width:1000px;margin:0 auto;padding:0 60px 80px;}
.help-grid{display:grid;grid-template-columns:1fr 1fr;gap:48px;margin-bottom:64px;}
.help-card{background:var(--surface);border:1px solid rgba(201,168,76,.1);padding:40px;}
.help-card h3{font-family:var(--fd);font-size:22px;letter-spacing:.1em;margin-bottom:16px;}
.help-card p{font-family:var(--fb);font-size:16px;color:var(--text-muted);line-height:1.8;margin-bottom:16px;}
.help-info-item{display:flex;align-items:flex-start;gap:14px;margin-bottom:16px;}
.help-icon{color:var(--accent);font-size:16px;flex-shrink:0;margin-top:2px;}
.help-info-text{font-family:var(--fb);font-size:15px;color:var(--text-muted);line-height:1.7;}
.ai-chat{background:var(--surface);border:1px solid rgba(201,168,76,.12);}
.ai-chat-head{padding:24px 28px;border-bottom:1px solid rgba(201,168,76,.08);display:flex;align-items:center;gap:14px;}
.ai-dot{width:8px;height:8px;border-radius:50%;background:var(--accent);animation:pulse 2s infinite;}
.ai-chat-title{font-family:var(--fd);font-size:16px;letter-spacing:.1em;}
.ai-messages{padding:24px 28px;min-height:340px;max-height:400px;overflow-y:auto;display:flex;flex-direction:column;gap:16px;}
.ai-msg{max-width:82%;font-family:var(--fb);font-size:15px;line-height:1.75;padding:14px 18px;}
.ai-msg.bot{background:rgba(201,168,76,.07);border-left:2px solid var(--accent);align-self:flex-start;color:var(--text-muted);}
.ai-msg.user{background:rgba(201,168,76,.12);align-self:flex-end;color:var(--text);text-align:right;}
.ai-typing{display:flex;gap:5px;padding:14px 18px;align-self:flex-start;}
.ai-typing span{width:6px;height:6px;border-radius:50%;background:var(--accent);animation:typing 1.2s infinite;}
.ai-typing span:nth-child(2){animation-delay:.2s;}
.ai-typing span:nth-child(3){animation-delay:.4s;}
@keyframes typing{0%,60%,100%{opacity:.2;transform:translateY(0)}30%{opacity:1;transform:translateY(-4px)}}
.ai-input-row{display:flex;border-top:1px solid rgba(201,168,76,.08);}
.ai-input{flex:1;background:transparent;border:none;color:var(--text);font-family:var(--fb);font-size:15px;padding:18px 24px;outline:none;}
.ai-input::placeholder{color:var(--text-dim);}
.ai-send{background:var(--accent);border:none;color:var(--bg);font-family:var(--fu);font-size:9px;letter-spacing:.3em;text-transform:uppercase;padding:0 24px;cursor:pointer;transition:background .3s;}
.ai-send:hover{background:var(--accent2);}
.ai-suggestions{display:flex;flex-wrap:wrap;gap:8px;padding:0 28px 20px;}
.ai-sug{font-family:var(--fu);font-size:9px;letter-spacing:.2em;text-transform:uppercase;color:var(--text-muted);border:1px solid rgba(201,168,76,.15);padding:7px 14px;cursor:pointer;transition:all .3s;}
.ai-sug:hover{color:var(--accent);border-color:var(--accent);}

/* ── ADMIN ── */
.admin-trigger{position:fixed;bottom:28px;right:28px;width:46px;height:46px;border-radius:50%;border:1px solid rgba(201,168,76,.3);background:rgba(10,8,4,.92);backdrop-filter:blur(10px);cursor:pointer;display:flex;align-items:center;justify-content:center;z-index:400;color:var(--text-muted);font-size:16px;transition:all .3s;}
.admin-trigger:hover{border-color:var(--accent);color:var(--accent);}

.auth-ov{position:fixed;inset:0;background:rgba(0,0,0,.94);z-index:600;display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transition:opacity .4s;backdrop-filter:blur(16px);}
.auth-ov.open{opacity:1;pointer-events:all;}
.auth-box{background:var(--surface);border:1px solid rgba(201,168,76,.2);padding:60px 52px;width:400px;text-align:center;position:relative;}
.auth-logo{font-family:var(--fd);font-size:26px;letter-spacing:.3em;color:var(--accent);margin-bottom:6px;font-weight:900;}
.auth-sub{font-family:var(--fu);font-size:9px;letter-spacing:.5em;text-transform:uppercase;color:var(--text-muted);margin-bottom:44px;}
.auth-input{width:100%;background:rgba(201,168,76,.05);border:1px solid rgba(201,168,76,.2);color:var(--text);font-family:var(--fu);font-size:14px;letter-spacing:.3em;padding:14px 18px;text-align:center;outline:none;margin-bottom:16px;transition:border-color .3s;}
.auth-input:focus{border-color:var(--accent);}
.auth-err{font-family:var(--fu);font-size:10px;letter-spacing:.15em;color:#c44;min-height:16px;margin-bottom:14px;}
.auth-hint{margin-top:18px;font-family:var(--fu);font-size:9px;color:var(--text-muted);letter-spacing:.15em;}
.auth-close{position:absolute;top:18px;right:20px;background:none;border:none;color:var(--text-muted);font-size:20px;cursor:pointer;transition:color .2s;}
.auth-close:hover{color:var(--accent);}

.admin-panel{position:fixed;top:0;right:0;bottom:0;width:440px;background:var(--surface);border-left:1px solid rgba(201,168,76,.12);z-index:700;transform:translateX(100%);transition:transform .5s cubic-bezier(.25,.46,.45,.94);overflow-y:auto;}
.admin-panel.open{transform:translateX(0);}
.adm-head{padding:32px;border-bottom:1px solid rgba(201,168,76,.1);position:sticky;top:0;background:var(--surface);z-index:10;display:flex;justify-content:space-between;align-items:center;}
.adm-title{font-family:var(--fd);font-size:16px;letter-spacing:.2em;color:var(--accent);font-weight:600;}
.adm-close{background:none;border:none;color:var(--text-muted);font-size:20px;cursor:pointer;transition:color .2s;}
.adm-close:hover{color:var(--accent);}
.adm-body{padding:32px;}
.adm-sec{margin-bottom:40px;}
.adm-sec-title{font-family:var(--fu);font-size:9px;letter-spacing:.5em;text-transform:uppercase;color:var(--accent);margin-bottom:18px;padding-bottom:8px;border-bottom:1px solid rgba(201,168,76,.08);}
.adm-field{margin-bottom:16px;}
.adm-label{font-family:var(--fu);font-size:9px;letter-spacing:.2em;text-transform:uppercase;color:var(--text-muted);display:block;margin-bottom:7px;}
.adm-input,.adm-sel,.adm-ta{width:100%;background:rgba(255,255,255,.04);border:1px solid rgba(201,168,76,.12);color:var(--text);font-family:var(--fu);font-size:12px;padding:9px 12px;outline:none;transition:border-color .3s;letter-spacing:.04em;}
.adm-input:focus,.adm-sel:focus,.adm-ta:focus{border-color:rgba(201,168,76,.45);}
.adm-sel{appearance:none;cursor:pointer;}
.adm-ta{resize:vertical;min-height:72px;}
.adm-color-row{display:flex;gap:10px;align-items:center;}
.adm-color{width:48px;height:36px;border:1px solid rgba(201,168,76,.2);background:none;cursor:pointer;padding:2px;}
.adm-upload{width:100%;border:1px dashed rgba(201,168,76,.22);background:rgba(201,168,76,.03);padding:18px;text-align:center;cursor:pointer;transition:all .3s;font-family:var(--fu);font-size:9px;letter-spacing:.2em;color:var(--text-muted);text-transform:uppercase;position:relative;overflow:hidden;}
.adm-upload:hover{border-color:var(--accent);color:var(--accent);}
.adm-upload input[type=file]{position:absolute;inset:0;opacity:0;cursor:pointer;}
.adm-prev{width:100%;height:90px;object-fit:cover;display:none;margin-top:8px;border:1px solid rgba(201,168,76,.12);}
.adm-product-card{background:rgba(201,168,76,.04);border:1px solid rgba(201,168,76,.1);padding:20px;margin-bottom:12px;position:relative;}
.adm-prod-name{font-family:var(--fd);font-size:14px;letter-spacing:.1em;color:var(--text);margin-bottom:6px;}
.adm-prod-meta{font-family:var(--fu);font-size:10px;letter-spacing:.2em;color:var(--text-muted);}
.adm-prod-actions{display:flex;gap:8px;margin-top:12px;}
.adm-prod-btn{font-family:var(--fu);font-size:9px;letter-spacing:.2em;text-transform:uppercase;padding:7px 14px;border:none;cursor:pointer;transition:all .3s;}
.adm-prod-btn.edit{background:rgba(201,168,76,.15);color:var(--accent);}
.adm-prod-btn.edit:hover{background:rgba(201,168,76,.25);}
.adm-prod-btn.del{background:rgba(200,60,60,.12);color:#c45;}
.adm-prod-btn.del:hover{background:rgba(200,60,60,.22);}
.btn-save{width:100%;background:var(--accent);color:var(--bg);border:none;padding:14px;font-family:var(--fu);font-size:10px;letter-spacing:.4em;text-transform:uppercase;cursor:pointer;transition:background .3s;margin-top:8px;}
.btn-save:hover{background:var(--accent2);}
.btn-add{width:100%;background:transparent;color:var(--accent);border:1px solid rgba(201,168,76,.3);padding:12px;font-family:var(--fu);font-size:10px;letter-spacing:.35em;text-transform:uppercase;cursor:pointer;transition:all .3s;margin-bottom:16px;}
.btn-add:hover{background:rgba(201,168,76,.07);border-color:var(--accent);}

/* PRODUCT FORM IN ADMIN */
.prod-form{background:rgba(0,0,0,.3);border:1px solid rgba(201,168,76,.15);padding:24px;margin-bottom:16px;display:none;}
.prod-form.open{display:block;}
.prod-form-title{font-family:var(--fd);font-size:14px;letter-spacing:.1em;color:var(--accent);margin-bottom:20px;}

/* TOAST */
.toast{position:fixed;bottom:80px;right:28px;background:var(--accent);color:var(--bg);font-family:var(--fu);font-size:9px;letter-spacing:.3em;text-transform:uppercase;padding:12px 22px;opacity:0;transition:opacity .4s;z-index:800;pointer-events:none;}
.toast.show{opacity:1;}

/* FEATURES PAGE */
.feat-section{max-width:1100px;margin:0 auto;padding:0 60px 80px;}
.feat-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:2px;}
.feat-block{background:var(--surface);padding:48px 40px;border:1px solid rgba(201,168,76,.06);transition:border-color .3s;}
.feat-block:hover{border-color:rgba(201,168,76,.2);}
.feat-icon{font-size:28px;margin-bottom:20px;color:var(--accent);}
.feat-name{font-family:var(--fd);font-size:20px;letter-spacing:.1em;margin-bottom:14px;}
.feat-desc{font-family:var(--fb);font-size:15px;color:var(--text-muted);line-height:1.8;}

/* FOOTER */
footer{padding:72px 60px 40px;border-top:1px solid rgba(201,168,76,.1);display:grid;grid-template-columns:1.5fr 1fr 1fr 1fr;gap:48px;}
.ft-brand .nav-logo{display:block;margin-bottom:16px;font-family:var(--fd);font-size:18px;font-weight:900;letter-spacing:.4em;color:var(--accent);text-decoration:none;}
.ft-brand p{font-family:var(--fb);font-style:italic;font-size:14px;color:var(--text-muted);line-height:1.8;}
.ft-col h4{font-family:var(--fu);font-size:9px;letter-spacing:.5em;text-transform:uppercase;color:var(--accent);margin-bottom:20px;}
.ft-col ul{list-style:none;}
.ft-col li{font-family:var(--fb);font-size:14px;color:var(--text-muted);margin-bottom:10px;}
.ft-bottom{padding:20px 60px;border-top:1px solid rgba(201,168,76,.06);display:flex;justify-content:space-between;align-items:center;font-family:var(--fu);font-size:9px;letter-spacing:.25em;text-transform:uppercase;color:var(--text-dim);}
.ft-domain{color:var(--accent);}

/* EMPTY STATE */
.empty-state{text-align:center;padding:80px 0;}
.empty-state p{font-family:var(--fb);font-style:italic;font-size:20px;color:var(--text-muted);}

/* RESPONSIVE */
@media(max-width:900px){
  nav .nav-top{padding:16px 20px;}
  .nav-item{padding:12px 16px;font-size:9px;}
  .sec{padding:72px 20px;}
  .list-container,.hot-section,.cat-section,.help-section,.feat-section,.prod-detail{padding-left:20px;padding-right:20px;}
  .pd-grid{grid-template-columns:1fr;}
  footer{grid-template-columns:1fr 1fr;padding:48px 20px 32px;}
  .ft-bottom{padding:16px 20px;flex-direction:column;gap:8px;}
  .help-grid{grid-template-columns:1fr;}
  .feat-grid{grid-template-columns:1fr;}
  .admin-panel{width:100%;}
}
</style>
</head>
<body>

<div class="cur" id="cur"></div>
<div class="cur-r" id="curR"></div>

<!-- ═══════════ NAV ═══════════ -->
<nav id="mainNav">
  <div class="nav-top">
    <span class="nav-logo" id="navLogo" onclick="goPage('home')">ETERNAL</span>
    <div style="font-family:var(--fu);font-size:10px;letter-spacing:.3em;color:var(--text-muted)" id="navRight">etrnl.com</div>
  </div>
  <div class="nav-bottom">
    <div class="nav-item active" onclick="goPage('home')" id="ni-home">Home</div>
    <div class="nav-item" onclick="goPage('features')" id="ni-features">Features</div>
    <div class="nav-item" onclick="goPage('hot')" id="ni-hot">Hot 🔥</div>
    <div class="nav-item" onclick="goPage('list')" id="ni-list">List</div>
    <div class="nav-item" onclick="toggleCat()" id="ni-category">Category ▾</div>
    <div class="nav-item" onclick="goPage('help')" id="ni-help">Help</div>
  </div>
  <div class="cat-dropdown" id="catDropdown"></div>
</nav>

<!-- ═══════════ PAGE: HOME ═══════════ -->
<div class="page active" id="page-home">
  <section class="hero" id="home">
    <div class="hero-bg"></div>
    <div class="hero-grain"></div>
    <div class="hero-eyebrow" id="heroEyebrow">The Art of Time</div>
    <div class="hero-title" id="heroTitle">ETERNAL</div>
    <div class="hero-tag"><em id="heroTag">Where craftsmanship meets infinity</em></div>
    <div class="hero-div"></div>
    <div class="hero-cta">
      <span class="btn-p" onclick="goPage('list')">Explore Collection</span>
      <span class="btn-g" onclick="goPage('features')">Our Heritage</span>
    </div>
    <div class="scroll-ind"><span>Scroll</span><div class="scroll-line"></div></div>
  </section>

  <div class="mq"><div class="mq-track" id="mqTrack">
    <span class="mq-item"><span>✦</span>Precision Engineered</span>
    <span class="mq-item"><span>✦</span>Handcrafted Excellence</span>
    <span class="mq-item"><span>✦</span>Timeless Design</span>
    <span class="mq-item"><span>✦</span>Limited Edition</span>
    <span class="mq-item"><span>✦</span>Swiss Movement</span>
    <span class="mq-item"><span>✦</span>Precision Engineered</span>
    <span class="mq-item"><span>✦</span>Handcrafted Excellence</span>
    <span class="mq-item"><span>✦</span>Timeless Design</span>
    <span class="mq-item"><span>✦</span>Limited Edition</span>
    <span class="mq-item"><span>✦</span>Swiss Movement</span>
  </div></div>

  <section class="sec">
    <div class="sec-label">The Collection</div>
    <h2 class="sec-title" id="homeSectionTitle">Featured Pieces</h2>
    <div class="featured-grid" id="homeFeaturedGrid"></div>
  </section>
</div>

<!-- ═══════════ PAGE: FEATURES ═══════════ -->
<div class="page" id="page-features">
  <section class="sec">
    <div class="sec-label">Why Eternal</div>
    <h2 class="sec-title" id="featuresTitle">The Eternal Difference</h2>
  </section>
  <div class="feat-section">
    <div class="feat-grid" id="featuresGrid">
      <div class="feat-block"><div class="feat-icon">⏱</div><div class="feat-name">Precision Movement</div><div class="feat-desc">Every caliber is assembled and regulated by master watchmakers with over 20 years of experience, achieving ±1 second per day accuracy.</div></div>
      <div class="feat-block"><div class="feat-icon">💎</div><div class="feat-name">Premium Materials</div><div class="feat-desc">From Grade 5 titanium to 18K gold and sapphire crystal glass, we source only the finest materials from certified suppliers worldwide.</div></div>
      <div class="feat-block"><div class="feat-icon">🛡</div><div class="feat-name">Lifetime Warranty</div><div class="feat-desc">Every Eternal piece comes with a comprehensive lifetime service warranty — because a true masterpiece should last for generations.</div></div>
      <div class="feat-block"><div class="feat-icon">✋</div><div class="feat-name">Handcrafted</div><div class="feat-desc">800+ hours of individual attention go into each timepiece, from the first raw movement to the final hand-polished dial and case.</div></div>
      <div class="feat-block"><div class="feat-icon">🌍</div><div class="feat-name">Geneva Heritage</div><div class="feat-desc">Our atelier sits in the heart of Geneva, Switzerland — the epicenter of watchmaking excellence for over three centuries.</div></div>
      <div class="feat-block"><div class="feat-icon">📦</div><div class="feat-name">Exclusive Packaging</div><div class="feat-desc">Each watch is presented in a handmade lacquered case with a certificate of authenticity, travel pouch, and full service documentation.</div></div>
    </div>
    <div style="text-align:center;margin-top:80px;">
      <h3 style="font-family:var(--fd);font-size:clamp(26px,4vw,44px);letter-spacing:.08em;font-weight:300;margin-bottom:24px;" id="detailTitle1">Every Second<br><em style="color:var(--accent)">Deserves a Masterpiece</em></h3>
      <p style="font-family:var(--fb);font-size:17px;color:var(--text-muted);line-height:1.9;max-width:640px;margin:0 auto 40px;" id="detailBody1">We believe that luxury is not merely an aesthetic — it is a commitment. Every timepiece undergoes 800 hours of individual attention, from the first raw movement to the final polished dial.</p>
      <span class="btn-p" onclick="goPage('list')">View Collection</span>
    </div>
  </div>
</div>

<!-- ═══════════ PAGE: HOT ═══════════ -->
<div class="page" id="page-hot">
  <section class="sec">
    <div class="sec-label">Most Popular</div>
    <h2 class="sec-title">Trending Now</h2>
  </section>
  <div class="hot-section">
    <div class="hot-grid" id="hotGrid"></div>
  </div>
</div>

<!-- ═══════════ PAGE: LIST ═══════════ -->
<div class="page" id="page-list">
  <div class="list-container" style="padding-top:40px;">
    <div class="list-header">
      <h2 id="listTitle">All Products</h2>
      <span class="list-count" id="listCount">0 pieces</span>
    </div>
    <div id="listItems"></div>
  </div>
</div>

<!-- ═══════════ PAGE: CATEGORY ═══════════ -->
<div class="page" id="page-category">
  <section class="sec" style="padding-bottom:40px;">
    <div class="sec-label">Browse By</div>
    <h2 class="sec-title" id="catPageTitle">Categories</h2>
  </section>
  <div class="cat-section">
    <div class="cat-filter-bar" id="catFilterBar"></div>
    <div class="cat-products" id="catProducts"></div>
  </div>
</div>

<!-- ═══════════ PAGE: HELP ═══════════ -->
<div class="page" id="page-help">
  <section class="sec" style="padding-bottom:40px;">
    <div class="sec-label">Support</div>
    <h2 class="sec-title">How Can We Help?</h2>
  </section>
  <div class="help-section">
    <div class="help-grid">
      <div class="help-card">
        <h3>Contact Us</h3>
        <div class="help-info-item"><div class="help-icon">📞</div><div class="help-info-text"><strong id="contactPhone">+41 22 000 0000</strong><br>Mon–Fri, 9am–6pm CET</div></div>
        <div class="help-info-item"><div class="help-icon">✉️</div><div class="help-info-text" id="contactEmail">contact@etrnl.com</div></div>
        <div class="help-info-item"><div class="help-icon">📍</div><div class="help-info-text" id="contactAddr">Rue du Rhône 80<br>Geneva, Switzerland</div></div>
        <div class="help-info-item"><div class="help-icon">🕐</div><div class="help-info-text" id="contactHours">Monday–Friday: 9:00–18:00 CET<br>Saturday: 10:00–16:00 CET</div></div>
      </div>
      <div class="help-card">
        <h3>About Eternal</h3>
        <p id="aboutText">Founded in 1924 in Geneva, Switzerland, Eternal has been crafting timepieces of extraordinary precision and beauty for over a century. Each watch is a testament to the art of horology, produced in strictly limited quantities by our master watchmakers.</p>
        <p id="aboutText2">We believe in the philosophy that a watch is not merely a tool — it is an heirloom, a legacy, and a work of art.</p>
      </div>
    </div>

    <div class="ai-chat" id="aiChat">
      <div class="ai-chat-head">
        <div class="ai-dot"></div>
        <div class="ai-chat-title">Eternal Concierge — AI Assistant</div>
      </div>
      <div class="ai-messages" id="aiMessages">
        <div class="ai-msg bot">Welcome to Eternal. I'm your personal concierge. Ask me anything about our collection, craftsmanship, pricing, or services — I'm here to assist.</div>
      </div>
      <div class="ai-suggestions" id="aiSuggestions">
        <div class="ai-sug" onclick="aiQuick('What watches do you have?')">What watches do you have?</div>
        <div class="ai-sug" onclick="aiQuick('Tell me about your warranty')">Warranty info</div>
        <div class="ai-sug" onclick="aiQuick('How do I care for my watch?')">Watch care</div>
        <div class="ai-sug" onclick="aiQuick('What is your most popular product?')">Most popular</div>
        <div class="ai-sug" onclick="aiQuick('How can I contact you?')">Contact info</div>
      </div>
      <div class="ai-input-row">
        <input class="ai-input" id="aiInput" placeholder="Ask anything about our collection…" onkeydown="if(event.key==='Enter')sendAI()">
        <button class="ai-send" onclick="sendAI()">Send</button>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════ PAGE: PRODUCT DETAIL ═══════════ -->
<div class="page" id="page-product">
  <div class="prod-detail">
    <div class="pd-back" onclick="goBack()">← Back</div>
    <div class="pd-grid">
      <div>
        <div class="pd-img-main" id="pdMainImg">
          <div class="pd-img-ph" id="pdImgPh">
            <svg width="90" height="90" viewBox="0 0 90 90" fill="none"><circle cx="45" cy="45" r="36" stroke="#c9a84c" stroke-width="1" opacity=".4"/><line x1="45" y1="14" x2="45" y2="45" stroke="#c9a84c" stroke-width="2" opacity=".8"/><line x1="45" y1="45" x2="62" y2="57" stroke="#c9a84c" stroke-width="1.5" opacity=".6"/><circle cx="45" cy="45" r="4" fill="#c9a84c"/></svg>
          </div>
        </div>
        <div class="pd-img-thumbs" id="pdThumbs"></div>
      </div>
      <div class="pd-info">
        <div class="pd-eyebrow" id="pdEyebrow">No. 001</div>
        <div class="pd-name" id="pdName">Product Name</div>
        <div class="pd-subtitle" id="pdSubtitle">Subtitle</div>
        <div class="pd-price" id="pdPrice">$0</div>
        <div class="pd-divider"></div>
        <p class="pd-desc" id="pdDesc">Description</p>
        <div class="pd-features">
          <div class="pd-feat-title">Key Features</div>
          <div class="pd-feat-list" id="pdFeats"></div>
        </div>
        <div class="pd-divider"></div>
        <div class="pd-specs-grid" id="pdSpecs"></div>
        <div class="pd-actions">
          <span class="btn-p">Request Inquiry</span>
          <span class="btn-g">Add to Wishlist</span>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════ FOOTER ═══════════ -->
<footer id="mainFooter">
  <div class="ft-brand">
    <span class="nav-logo" onclick="goPage('home')">ETERNAL</span>
    <p id="footerTagline">Timeless precision for those who understand that true luxury is measured in lifetimes, not moments.</p>
  </div>
  <div class="ft-col">
    <h4>Collection</h4>
    <ul id="footerCol1">
      <li>The Meridian Series</li><li>The Solstice Series</li><li>The Noir Edition</li><li>Bespoke Commissions</li>
    </ul>
  </div>
  <div class="ft-col">
    <h4>Company</h4>
    <ul>
      <li onclick="goPage('features')" style="cursor:pointer">About Us</li>
      <li onclick="goPage('help')" style="cursor:pointer">Contact</li>
      <li>Careers</li><li>Press</li>
    </ul>
  </div>
  <div class="ft-col">
    <h4>Contact</h4>
    <ul>
      <li id="ftEmail">contact@etrnl.com</li>
      <li id="ftPhone">+41 22 000 0000</li>
      <li id="ftAddr">Rue du Rhône 80, Geneva</li>
    </ul>
  </div>
</footer>
<div class="ft-bottom">
  <span id="ftCopy">© 2024 Eternal — All Rights Reserved</span>
  <span class="ft-domain">etrnl.com</span>
</div>

<!-- ═══════════ AUTH ═══════════ -->
<div class="auth-ov" id="authOv">
  <div class="auth-box">
    <button class="auth-close" onclick="closeAuth()">✕</button>
    <div class="auth-logo">ETERNAL</div>
    <div class="auth-sub">Admin Studio Access</div>
    <input type="password" class="auth-input" id="authIn" placeholder="Enter password" onkeydown="if(event.key==='Enter')checkAuth()">
    <div class="auth-err" id="authErr"></div>
    <button class="btn-p" style="width:100%" onclick="checkAuth()">Enter Studio</button>
    <p class="auth-hint">Default: <strong style="color:var(--accent)">eternal2024</strong></p>
  </div>
</div>

<!-- ═══════════ ADMIN PANEL ═══════════ -->
<div class="admin-panel" id="adminPanel">
  <div class="adm-head">
    <div class="adm-title">⚙ Admin Studio</div>
    <button class="adm-close" onclick="closeAdmin()">✕</button>
  </div>
  <div class="adm-body">

    <!-- BRAND -->
    <div class="adm-sec">
      <div class="adm-sec-title">Brand & Hero</div>
      <div class="adm-field"><label class="adm-label">Site Name</label><input class="adm-input" id="a_siteName" value="ETERNAL"></div>
      <div class="adm-field"><label class="adm-label">Hero Eyebrow</label><input class="adm-input" id="a_eyebrow" value="The Art of Time"></div>
      <div class="adm-field"><label class="adm-label">Hero Tagline</label><input class="adm-input" id="a_tag" value="Where craftsmanship meets infinity"></div>
      <div class="adm-field"><label class="adm-label">Nav Right Text</label><input class="adm-input" id="a_navRight" value="etrnl.com"></div>
      <div class="adm-field"><label class="adm-label">Home Section Title</label><input class="adm-input" id="a_homeSecTitle" value="Featured Pieces"></div>
      <div class="adm-field"><label class="adm-label">Footer Tagline</label><textarea class="adm-ta" id="a_ftTag">Timeless precision for those who understand that true luxury is measured in lifetimes, not moments.</textarea></div>
      <div class="adm-field"><label class="adm-label">Copyright Text</label><input class="adm-input" id="a_copy" value="© 2024 Eternal — All Rights Reserved"></div>
      <div class="adm-field">
        <label class="adm-label">Logo Image (replaces text)</label>
        <div class="adm-upload">📷 Upload Logo<input type="file" accept="image/*" onchange="handleLogo(event)"></div>
        <img class="adm-prev" id="logoPrev">
      </div>
    </div>

    <!-- COLORS -->
    <div class="adm-sec">
      <div class="adm-sec-title">Colors</div>
      <div class="adm-field"><label class="adm-label">Background</label><div class="adm-color-row"><input type="color" class="adm-color" id="c_bg" value="#0a0804" oninput="applyColors()"><input class="adm-input" id="c_bgH" value="#0a0804" oninput="syncHex('bg')"></div></div>
      <div class="adm-field"><label class="adm-label">Accent</label><div class="adm-color-row"><input type="color" class="adm-color" id="c_ac" value="#c9a84c" oninput="applyColors()"><input class="adm-input" id="c_acH" value="#c9a84c" oninput="syncHex('ac')"></div></div>
      <div class="adm-field"><label class="adm-label">Text</label><div class="adm-color-row"><input type="color" class="adm-color" id="c_tx" value="#f0ead6" oninput="applyColors()"><input class="adm-input" id="c_txH" value="#f0ead6" oninput="syncHex('tx')"></div></div>
      <div class="adm-field"><label class="adm-label">Surface</label><div class="adm-color-row"><input type="color" class="adm-color" id="c_sf" value="#111009" oninput="applyColors()"><input class="adm-input" id="c_sfH" value="#111009" oninput="syncHex('sf')"></div></div>
    </div>

    <!-- FONTS -->
    <div class="adm-sec">
      <div class="adm-sec-title">Fonts</div>
      <div class="adm-field"><label class="adm-label">Display Font</label>
        <select class="adm-sel" id="f_disp" onchange="applyFonts()">
          <option value="'Cinzel',serif">Cinzel (Classic)</option>
          <option value="'Playfair Display',serif">Playfair Display</option>
          <option value="'Cormorant Garamond',serif">Cormorant Garamond</option>
          <option value="'Raleway',sans-serif">Raleway (Modern)</option>
          <option value="'Montserrat',sans-serif">Montserrat</option>
        </select>
      </div>
      <div class="adm-field"><label class="adm-label">Body Font</label>
        <select class="adm-sel" id="f_body" onchange="applyFonts()">
          <option value="'Cormorant Garamond',serif">Cormorant Garamond</option>
          <option value="'Playfair Display',serif">Playfair Display</option>
          <option value="'Lora',serif">Lora</option>
          <option value="'Raleway',sans-serif">Raleway</option>
        </select>
      </div>
    </div>

    <!-- CONTACT -->
    <div class="adm-sec">
      <div class="adm-sec-title">Contact Info</div>
      <div class="adm-field"><label class="adm-label">Phone</label><input class="adm-input" id="a_phone" value="+41 22 000 0000"></div>
      <div class="adm-field"><label class="adm-label">Email</label><input class="adm-input" id="a_email" value="contact@etrnl.com"></div>
      <div class="adm-field"><label class="adm-label">Address</label><textarea class="adm-ta" id="a_addr">Rue du Rhône 80
Geneva, Switzerland</textarea></div>
      <div class="adm-field"><label class="adm-label">Opening Hours</label><textarea class="adm-ta" id="a_hours">Monday–Friday: 9:00–18:00 CET
Saturday: 10:00–16:00 CET</textarea></div>
      <div class="adm-field"><label class="adm-label">Footer Col 1 (one per line)</label><textarea class="adm-ta" id="a_ftCol1">The Meridian Series
The Solstice Series
The Noir Edition
Bespoke Commissions</textarea></div>
    </div>

    <!-- ABOUT -->
    <div class="adm-sec">
      <div class="adm-sec-title">About / Help Page</div>
      <div class="adm-field"><label class="adm-label">About Paragraph 1</label><textarea class="adm-ta" id="a_about1">Founded in 1924 in Geneva, Switzerland, Eternal has been crafting timepieces of extraordinary precision and beauty for over a century. Each watch is a testament to the art of horology, produced in strictly limited quantities by our master watchmakers.</textarea></div>
      <div class="adm-field"><label class="adm-label">About Paragraph 2</label><textarea class="adm-ta" id="a_about2">We believe in the philosophy that a watch is not merely a tool — it is an heirloom, a legacy, and a work of art.</textarea></div>
    </div>

    <!-- CATEGORIES -->
    <div class="adm-sec">
      <div class="adm-sec-title">Categories (comma-separated)</div>
      <div class="adm-field"><label class="adm-label">Category List</label><input class="adm-input" id="a_cats" value="Chronograph,Tourbillon,Dress Watch,Sport,Limited Edition,Bespoke"></div>
    </div>

    <!-- PRODUCTS -->
    <div class="adm-sec">
      <div class="adm-sec-title">Products</div>
      <div id="adminProductList"></div>
      <button class="btn-add" onclick="openNewProductForm()">+ Add New Product</button>
      <div class="prod-form" id="prodFormWrap">
        <div class="prod-form-title" id="prodFormTitle">New Product</div>
        <div class="adm-field"><label class="adm-label">Product Number (e.g. No. 001)</label><input class="adm-input" id="pf_num" value="No. 003"></div>
        <div class="adm-field"><label class="adm-label">Name</label><input class="adm-input" id="pf_name" placeholder="Product Name"></div>
        <div class="adm-field"><label class="adm-label">Subtitle</label><input class="adm-input" id="pf_sub" placeholder="e.g. Chronograph Edition"></div>
        <div class="adm-field"><label class="adm-label">Price</label><input class="adm-input" id="pf_price" placeholder="e.g. $9,800"></div>
        <div class="adm-field"><label class="adm-label">Category</label><input class="adm-input" id="pf_cat" placeholder="e.g. Chronograph"></div>
        <div class="adm-field"><label class="adm-label">Short Description (for list view)</label><textarea class="adm-ta" id="pf_shortDesc" placeholder="Brief summary…"></textarea></div>
        <div class="adm-field"><label class="adm-label">Full Description</label><textarea class="adm-ta" id="pf_desc" placeholder="Detailed description…" style="min-height:100px"></textarea></div>
        <div class="adm-field"><label class="adm-label">Features (one per line)</label><textarea class="adm-ta" id="pf_feats" placeholder="Feature 1
Feature 2
Feature 3"></textarea></div>
        <div class="adm-field"><label class="adm-label">Specs (Label: Value, one per line)</label><textarea class="adm-ta" id="pf_specs" placeholder="Movement: ETE-7001
Case: 42mm
Material: Titanium
Water: 100m"></textarea></div>
        <div class="adm-field"><label class="adm-label">Hot/Trending?</label>
          <select class="adm-sel" id="pf_hot"><option value="0">No</option><option value="1">Yes — Mark as Hot</option></select>
        </div>
        <div class="adm-field"><label class="adm-label">Front Image (card + detail)</label>
          <div class="adm-upload">📷 Upload Image<input type="file" accept="image/*" onchange="handleProdImg(event,'main')"></div>
          <img class="adm-prev" id="pf_imgPrev">
        </div>
        <div style="display:flex;gap:10px;margin-top:12px;">
          <button class="btn-save" onclick="saveProduct()">Save Product</button>
          <button class="btn-save" style="background:rgba(200,60,60,.3);color:#f88" onclick="cancelProdForm()">Cancel</button>
        </div>
      </div>
    </div>

    <!-- MARQUEE -->
    <div class="adm-sec">
      <div class="adm-sec-title">Marquee Text (pipe-separated)</div>
      <div class="adm-field"><input class="adm-input" id="a_mq" value="Precision Engineered|Handcrafted Excellence|Timeless Design|Limited Edition|Swiss Movement"></div>
    </div>

    <!-- PASSWORD -->
    <div class="adm-sec">
      <div class="adm-sec-title">Admin Password</div>
      <div class="adm-field"><label class="adm-label">New Password</label><input type="password" class="adm-input" id="a_newPass" placeholder="Enter new password"></div>
      <button class="btn-save" onclick="changePass()">Update Password</button>
    </div>

    <button class="btn-save" onclick="applyAll()" style="font-size:11px;letter-spacing:.3em;padding:18px;">✦ Apply All Changes</button>
  </div>
</div>

<button class="admin-trigger" onclick="openAuth()">⚙</button>
<div class="toast" id="toast"></div>

<script>
// ─── CURSOR ───
const cur=document.getElementById('cur'),curR=document.getElementById('curR');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;});
(function anim(){cur.style.left=mx+'px';cur.style.top=my+'px';rx+=(mx-rx)*.11;ry+=(my-ry)*.11;curR.style.left=rx+'px';curR.style.top=ry+'px';requestAnimationFrame(anim);})();

// ─── STATE ───
const PASS_KEY='eternal_pass';
let adminPass=localStorage.getItem(PASS_KEY)||'eternal2024';
let prevPage='home';
let editingProductId=null;
let pfImg=null;

let siteData={
  siteName:'ETERNAL',eyebrow:'The Art of Time',tag:'Where craftsmanship meets infinity',
  navRight:'etrnl.com',homeSecTitle:'Featured Pieces',
  ftTag:'Timeless precision for those who understand that true luxury is measured in lifetimes, not moments.',
  copy:'© 2024 Eternal — All Rights Reserved',
  phone:'+41 22 000 0000',email:'contact@etrnl.com',addr:'Rue du Rhône 80\nGeneva, Switzerland',hours:'Monday–Friday: 9:00–18:00 CET\nSaturday: 10:00–16:00 CET',
  about1:'Founded in 1924 in Geneva, Switzerland, Eternal has been crafting timepieces of extraordinary precision and beauty for over a century.',
  about2:'We believe in the philosophy that a watch is not merely a tool — it is an heirloom, a legacy, and a work of art.',
  ftCol1:'The Meridian Series\nThe Solstice Series\nThe Noir Edition\nBespoke Commissions',
  cats:'Chronograph,Tourbillon,Dress Watch,Sport,Limited Edition,Bespoke',
  mq:'Precision Engineered|Handcrafted Excellence|Timeless Design|Limited Edition|Swiss Movement',
  logoImg:null
};

let products=[
  {id:1,num:'No. 001',name:'The Meridian',sub:'Chronograph Masterpiece',price:'$12,400',cat:'Chronograph',shortDesc:'Our flagship chronograph with skeletonized dial and silicon escapement movement.',desc:'The Meridian is our flagship chronograph — born from a decade of development. Its skeletonized dial reveals the ETE-7001 movement, a hand-wound caliber with silicon escapement and 60-hour power reserve. Available in stainless steel and 18K white gold variants.',feats:['ETE-7001 hand-wound caliber','Silicon escapement for superior accuracy','60-hour power reserve','Skeletonized dial with sapphire crystal'],specs:[['Movement','ETE-7001'],['Case Diameter','42mm'],['Material','Grade 5 Titanium'],['Water Resistance','100m'],['Power Reserve','60 hours'],['Crystal','Sapphire, AR coated']],hot:true,views:4820,img:null},
  {id:2,num:'No. 002',name:'The Solstice',sub:'Tourbillon Edition',price:'$28,900',cat:'Tourbillon',shortDesc:'The pinnacle of our craft — triple-axis tourbillon, 12 pieces per year.',desc:'The Solstice houses our most complex movement — the ETE-9001 tourbillon with triple-axis rotation. Only 12 pieces are produced annually, each requiring 1,200 hours of expert assembly by a single watchmaker.',feats:['Triple-axis tourbillon ETE-9001','1,200 hours individual assembly','18K rose gold case','Meteorite dial insert'],specs:[['Movement','ETE-9001 Tourbillon'],['Case Diameter','44mm'],['Material','18K Rose Gold'],['Water Resistance','50m'],['Pieces Per Year','12'],['Crystal','Box sapphire']],hot:true,views:3210,img:null}
];
let nextId=3;

// ─── PAGE NAVIGATION ───
function goPage(page){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
  const pg=document.getElementById('page-'+page);
  if(pg){pg.classList.add('active');}
  const ni=document.getElementById('ni-'+page);
  if(ni){ni.classList.add('active');}
  if(page!=='product')prevPage=page;
  window.scrollTo({top:0,behavior:'smooth'});
  closeCatDropdown();
  if(page==='home')renderHome();
  if(page==='hot')renderHot();
  if(page==='list')renderList();
  if(page==='category')renderCategory();
}

function goBack(){goPage(prevPage);}

function openProductPage(id){
  const p=products.find(x=>x.id===id);
  if(!p)return;
  p.views=(p.views||0)+1;
  document.getElementById('pdEyebrow').textContent=p.num;
  document.getElementById('pdName').textContent=p.name;
  document.getElementById('pdSubtitle').textContent=p.sub;
  document.getElementById('pdPrice').textContent=p.price;
  document.getElementById('pdDesc').textContent=p.desc;
  // features
  const fl=document.getElementById('pdFeats');
  fl.innerHTML=(p.feats||[]).map(f=>`<div class="pd-feat-item"><div class="pd-feat-dot"></div><span>${f}</span></div>`).join('');
  // specs
  const sg=document.getElementById('pdSpecs');
  sg.innerHTML=(p.specs||[]).map(s=>`<div class="pd-spec"><div class="pd-spec-label">${s[0]}</div><div class="pd-spec-val">${s[1]}</div></div>`).join('');
  // image
  const mi=document.getElementById('pdMainImg');
  const ph=document.getElementById('pdImgPh');
  const existImg=mi.querySelector('img.real');
  if(existImg)existImg.remove();
  if(p.img){ph.style.display='none';const img=document.createElement('img');img.src=p.img;img.className='real';img.style.cssText='width:100%;height:100%;object-fit:cover;position:absolute;inset:0;';mi.appendChild(img);}
  else{ph.style.display='flex';}
  document.getElementById('pdThumbs').innerHTML='';
  goPage('product');
}

// ─── RENDER FUNCTIONS ───
function renderHome(){
  const g=document.getElementById('homeFeaturedGrid');
  if(!products.length){g.innerHTML='<div class="empty-state"><p>No products yet. Add some in the Admin Studio.</p></div>';return;}
  g.innerHTML=products.map(p=>prodCardHTML(p)).join('');
}

function renderHot(){
  const sorted=[...products].sort((a,b)=>(b.views||0)-(a.views||0));
  const g=document.getElementById('hotGrid');
  if(!sorted.length){g.innerHTML='<div class="empty-state"><p>No products yet.</p></div>';return;}
  g.innerHTML=sorted.map((p,i)=>`
    <div class="prod-card" onclick="openProductPage(${p.id})">
      <div class="hot-rank">${i<9?'0':''}${i+1}</div>
      ${p.hot?'<div class="hot-badge">🔥 Hot</div>':''}
      ${p.img?`<img class="prod-card-img" src="${p.img}" alt="${p.name}">`:`<div class="prod-card-ph">${watchSVG()}</div>`}
      <div class="prod-card-info">
        <div class="pc-num">${p.num}</div>
        <div class="pc-name">${p.name}</div>
        <div class="pc-sub">${p.sub}</div>
        <div class="pc-price">${p.price}</div>
        <div class="li-views">👁 ${(p.views||0).toLocaleString()} views</div>
        <button class="pc-btn">View Details</button>
      </div>
    </div>`).join('');
}

function renderList(){
  const items=document.getElementById('listItems');
  const count=document.getElementById('listCount');
  count.textContent=`${products.length} piece${products.length!==1?'s':''}`;
  if(!products.length){items.innerHTML='<div class="empty-state"><p>No products yet.</p></div>';return;}
  items.innerHTML=products.map(p=>`
    <div class="list-item" onclick="openProductPage(${p.id})">
      ${p.img?`<img class="list-img" src="${p.img}" alt="${p.name}">`:`<div class="list-img-ph">${watchSVGSmall()}</div>`}
      <div class="list-info">
        <div class="li-name">${p.name}</div>
        <div class="li-sub">${p.sub}</div>
        <div class="li-desc">${p.shortDesc||p.desc.substring(0,120)+'…'}</div>
      </div>
      <div class="list-meta">
        <div class="li-price">${p.price}</div>
        <div class="li-cat">${p.cat||'—'}</div>
        <div class="li-views">👁 ${(p.views||0).toLocaleString()}</div>
      </div>
    </div>`).join('');
}

function renderCategory(activeCat){
  const cats=siteData.cats.split(',').map(c=>c.trim()).filter(Boolean);
  const bar=document.getElementById('catFilterBar');
  const grid=document.getElementById('catProducts');
  bar.innerHTML=`<div class="cat-chip ${!activeCat?'active':''}" onclick="renderCategory(null)">All</div>`+
    cats.map(c=>`<div class="cat-chip ${activeCat===c?'active':''}" onclick="renderCategory('${c}')">${c}</div>`).join('');
  const filtered=activeCat?products.filter(p=>p.cat===activeCat):products;
  if(!filtered.length){grid.innerHTML='<div class="empty-state"><p>No products in this category.</p></div>';return;}
  grid.innerHTML=filtered.map(p=>prodCardHTML(p)).join('');
}

function renderCatDropdown(){
  const cats=siteData.cats.split(',').map(c=>c.trim()).filter(Boolean);
  document.getElementById('catDropdown').innerHTML=cats.map(c=>
    `<div class="cat-chip" onclick="selectCat('${c}')">${c}</div>`).join('');
}

function selectCat(cat){
  goPage('category');
  setTimeout(()=>renderCategory(cat),50);
  closeCatDropdown();
}

function toggleCat(){
  const d=document.getElementById('catDropdown');
  d.classList.toggle('open');
  renderCatDropdown();
}
function closeCatDropdown(){document.getElementById('catDropdown').classList.remove('open');}

function prodCardHTML(p){
  return`<div class="prod-card" onclick="openProductPage(${p.id})">
    ${p.hot?'<div class="hot-badge">🔥</div>':''}
    ${p.img?`<img class="prod-card-img" src="${p.img}" alt="${p.name}">`:`<div class="prod-card-ph">${watchSVG()}</div>`}
    <div class="prod-card-info">
      <div class="pc-num">${p.num}</div>
      <div class="pc-name">${p.name}</div>
      <div class="pc-sub">${p.sub}</div>
      <div class="pc-price">${p.price}</div>
      <button class="pc-btn">Discover More</button>
    </div>
  </div>`;
}

function watchSVG(){return`<svg width="70" height="70" viewBox="0 0 70 70" fill="none"><circle cx="35" cy="35" r="28" stroke="#c9a84c" stroke-width="1" opacity=".4"/><line x1="35" y1="10" x2="35" y2="35" stroke="#c9a84c" stroke-width="1.5" opacity=".8"/><line x1="35" y1="35" x2="48" y2="44" stroke="#c9a84c" stroke-width="1" opacity=".6"/><circle cx="35" cy="35" r="3" fill="#c9a84c"/></svg><span style="font-family:var(--fu);font-size:9px;letter-spacing:.4em;color:var(--text-muted);text-transform:uppercase;">No Image</span>`;}
function watchSVGSmall(){return`<svg width="32" height="32" viewBox="0 0 32 32" fill="none"><circle cx="16" cy="16" r="12" stroke="#c9a84c" stroke-width="1" opacity=".4"/><line x1="16" y1="6" x2="16" y2="16" stroke="#c9a84c" stroke-width="1" opacity=".8"/><circle cx="16" cy="16" r="2" fill="#c9a84c"/></svg>`;}

// ─── AI CHAT ───
function sendAI(){
  const inp=document.getElementById('aiInput');
  const msg=inp.value.trim();
  if(!msg)return;
  addMsg(msg,'user');
  inp.value='';
  showTyping();
  setTimeout(()=>{removeTyping();addMsg(getAIReply(msg),'bot');},1200);
}

function aiQuick(q){
  document.getElementById('aiInput').value=q;
  sendAI();
}

function addMsg(text,type){
  const msgs=document.getElementById('aiMessages');
  const d=document.createElement('div');
  d.className='ai-msg '+type;
  d.textContent=text;
  msgs.appendChild(d);
  msgs.scrollTop=msgs.scrollHeight;
}

let typingEl=null;
function showTyping(){
  const msgs=document.getElementById('aiMessages');
  typingEl=document.createElement('div');
  typingEl.className='ai-typing';
  typingEl.innerHTML='<span></span><span></span><span></span>';
  msgs.appendChild(typingEl);
  msgs.scrollTop=msgs.scrollHeight;
}
function removeTyping(){if(typingEl){typingEl.remove();typingEl=null;}}

function getAIReply(msg){
  const m=msg.toLowerCase();
  if(m.includes('watch')||m.includes('product')||m.includes('collection')){
    return`We currently offer ${products.length} exquisite pieces in our collection: ${products.map(p=>p.name).join(', ')}. Each is crafted to perfection. Visit the List or Collection page to explore them all.`;}
  if(m.includes('price')||m.includes('cost')||m.includes('how much')){
    return`Our pieces range from ${products.length?products.map(p=>p.price).join(' to '):'contact us for pricing'}. Each piece represents decades of expertise. We also offer bespoke commissions — please contact our team for a personal consultation.`;}
  if(m.includes('warranty')||m.includes('guarantee')){
    return`Every Eternal timepiece comes with a comprehensive lifetime service warranty. This covers all mechanical servicing, movement overhauls, and restoration for the life of the watch. Your piece is protected forever.`;}
  if(m.includes('contact')||m.includes('phone')||m.includes('call')){
    return`You can reach us at ${siteData.phone} or by email at ${siteData.email}. Our boutique is located at ${siteData.addr.replace('\n',', ')}. We're available ${siteData.hours.split('\n')[0]}.`;}
  if(m.includes('shipping')||m.includes('deliver')){
    return`We offer complimentary worldwide shipping with full insurance on all orders. Delivery is handled by our dedicated logistics partners in secure, climate-controlled packaging. Estimated delivery: 5–10 business days.`;}
  if(m.includes('care')||m.includes('maintain')||m.includes('service')){
    return`We recommend servicing your Eternal timepiece every 5–7 years. Avoid exposing the watch to extreme temperatures or magnetic fields. Use a soft cloth for cleaning. All servicing is covered under our lifetime warranty.`;}
  if(m.includes('popular')||m.includes('best')||m.includes('hot')){
    const hot=products.filter(p=>p.hot);
    return hot.length?`Our most popular pieces are: ${hot.map(p=>p.name).join(', ')}. These can be viewed on the Hot 🔥 page. Each is a limited-edition masterpiece.`:`Browse our full collection on the Hot page to see our most-viewed pieces.`;}
  if(m.includes('material')||m.includes('gold')||m.includes('steel')){
    return`We use only the finest materials — Grade 5 titanium, 18K gold alloys, and certified sapphire crystal glass. Each material is sourced from verified suppliers and tested extensively before use in our ateliers.`;}
  if(m.includes('about')||m.includes('who')||m.includes('company')){
    return`${siteData.about1} ${siteData.about2}`;}
  if(m.includes('hello')||m.includes('hi')||m.includes('hey')){
    return`Welcome to Eternal. It's a pleasure to assist you. Whether you're exploring our collection, learning about our craftsmanship, or need assistance with an order — I'm here for you. What can I help with?`;}
  return`Thank you for your question. For the most accurate and personalized guidance, I'd recommend speaking directly with our team at ${siteData.phone} or emailing us at ${siteData.email}. Is there anything else I can assist you with today?`;
}

// ─── ADMIN AUTH ───
function openAuth(){document.getElementById('authOv').classList.add('open');setTimeout(()=>document.getElementById('authIn').focus(),300);}
function closeAuth(){document.getElementById('authOv').classList.remove('open');document.getElementById('authIn').value='';document.getElementById('authErr').textContent='';}
function checkAuth(){
  const v=document.getElementById('authIn').value;
  if(v===adminPass){closeAuth();openAdmin();}
  else{document.getElementById('authErr').textContent='Incorrect password.';document.getElementById('authIn').value='';}
}

function openAdmin(){document.getElementById('adminPanel').classList.add('open');renderAdminProducts();}
function closeAdmin(){document.getElementById('adminPanel').classList.remove('open');}

// ─── PRODUCT FORM ───
function openNewProductForm(){
  editingProductId=null;pfImg=null;
  document.getElementById('prodFormTitle').textContent='New Product';
  document.getElementById('pf_num').value='No. 00'+nextId;
  document.getElementById('pf_name').value='';
  document.getElementById('pf_sub').value='';
  document.getElementById('pf_price').value='';
  document.getElementById('pf_cat').value='';
  document.getElementById('pf_shortDesc').value='';
  document.getElementById('pf_desc').value='';
  document.getElementById('pf_feats').value='';
  document.getElementById('pf_specs').value='';
  document.getElementById('pf_hot').value='0';
  document.getElementById('pf_imgPrev').style.display='none';
  document.getElementById('prodFormWrap').classList.add('open');
  document.getElementById('prodFormWrap').scrollIntoView({behavior:'smooth',block:'start'});
}

function openEditProductForm(id){
  const p=products.find(x=>x.id===id);if(!p)return;
  editingProductId=id;pfImg=p.img||null;
  document.getElementById('prodFormTitle').textContent='Edit: '+p.name;
  document.getElementById('pf_num').value=p.num;
  document.getElementById('pf_name').value=p.name;
  document.getElementById('pf_sub').value=p.sub;
  document.getElementById('pf_price').value=p.price;
  document.getElementById('pf_cat').value=p.cat||'';
  document.getElementById('pf_shortDesc').value=p.shortDesc||'';
  document.getElementById('pf_desc').value=p.desc;
  document.getElementById('pf_feats').value=(p.feats||[]).join('\n');
  document.getElementById('pf_specs').value=(p.specs||[]).map(s=>s[0]+': '+s[1]).join('\n');
  document.getElementById('pf_hot').value=p.hot?'1':'0';
  const prev=document.getElementById('pf_imgPrev');
  if(p.img){prev.src=p.img;prev.style.display='block';}else{prev.style.display='none';}
  document.getElementById('prodFormWrap').classList.add('open');
  document.getElementById('prodFormWrap').scrollIntoView({behavior:'smooth',block:'start'});
}

function cancelProdForm(){document.getElementById('prodFormWrap').classList.remove('open');editingProductId=null;pfImg=null;}

function saveProduct(){
  const name=document.getElementById('pf_name').value.trim();
  if(!name){alert('Please enter a product name.');return;}
  const featsRaw=document.getElementById('pf_feats').value.trim();
  const feats=featsRaw?featsRaw.split('\n').map(f=>f.trim()).filter(Boolean):[];
  const specsRaw=document.getElementById('pf_specs').value.trim();
  const specs=specsRaw?specsRaw.split('\n').map(l=>{const[k,...v]=l.split(':');return[k.trim(),v.join(':').trim()];}).filter(s=>s[0]&&s[1]):[];

  const prod={
    id:editingProductId||nextId,
    num:document.getElementById('pf_num').value.trim(),
    name,sub:document.getElementById('pf_sub').value.trim(),
    price:document.getElementById('pf_price').value.trim(),
    cat:document.getElementById('pf_cat').value.trim(),
    shortDesc:document.getElementById('pf_shortDesc').value.trim(),
    desc:document.getElementById('pf_desc').value.trim(),
    feats,specs,
    hot:document.getElementById('pf_hot').value==='1',
    views:editingProductId?products.find(x=>x.id===editingProductId)?.views||0:0,
    img:pfImg
  };

  if(editingProductId){
    const idx=products.findIndex(x=>x.id===editingProductId);
    if(idx!==-1)products[idx]=prod;
  }else{
    products.push(prod);
    nextId++;
  }
  cancelProdForm();
  renderAdminProducts();
  renderHome();
  showToast(editingProductId?'Product Updated':'Product Added ✦');
}

function deleteProduct(id){
  if(!confirm('Delete this product?'))return;
  products=products.filter(x=>x.id!==id);
  renderAdminProducts();renderHome();
  showToast('Product Removed');
}

function renderAdminProducts(){
  const el=document.getElementById('adminProductList');
  if(!products.length){el.innerHTML='<p style="font-family:var(--fu);font-size:10px;color:var(--text-muted);letter-spacing:.2em;margin-bottom:16px">No products yet.</p>';return;}
  el.innerHTML=products.map(p=>`
    <div class="adm-product-card">
      <div class="adm-prod-name">${p.name}</div>
      <div class="adm-prod-meta">${p.num} · ${p.price} · ${p.cat||'—'}</div>
      <div class="adm-prod-actions">
        <button class="adm-prod-btn edit" onclick="openEditProductForm(${p.id})">Edit</button>
        <button class="adm-prod-btn del" onclick="deleteProduct(${p.id})">Delete</button>
      </div>
    </div>`).join('');
}

function handleProdImg(e,type){
  const f=e.target.files[0];if(!f)return;
  const r=new FileReader();
  r.onload=ev=>{pfImg=ev.target.result;document.getElementById('pf_imgPrev').src=pfImg;document.getElementById('pf_imgPrev').style.display='block';};
  r.readAsDataURL(f);
}

function handleLogo(e){
  const f=e.target.files[0];if(!f)return;
  const r=new FileReader();
  r.onload=ev=>{
    siteData.logoImg=ev.target.result;
    const prev=document.getElementById('logoPrev');prev.src=ev.target.result;prev.style.display='block';
    applyLogoToPage();
  };r.readAsDataURL(f);
}

function applyLogoToPage(){
  const els=['navLogo'];
  els.forEach(id=>{
    const el=document.getElementById(id);if(!el)return;
    if(siteData.logoImg){el.innerHTML=`<img src="${siteData.logoImg}" style="height:28px;object-fit:contain;">`;}
    else{el.textContent=siteData.siteName;}
  });
}

// ─── APPLY ALL ───
function applyAll(){
  siteData.siteName=document.getElementById('a_siteName').value;
  siteData.eyebrow=document.getElementById('a_eyebrow').value;
  siteData.tag=document.getElementById('a_tag').value;
  siteData.navRight=document.getElementById('a_navRight').value;
  siteData.homeSecTitle=document.getElementById('a_homeSecTitle').value;
  siteData.ftTag=document.getElementById('a_ftTag').value;
  siteData.copy=document.getElementById('a_copy').value;
  siteData.phone=document.getElementById('a_phone').value;
  siteData.email=document.getElementById('a_email').value;
  siteData.addr=document.getElementById('a_addr').value;
  siteData.hours=document.getElementById('a_hours').value;
  siteData.about1=document.getElementById('a_about1').value;
  siteData.about2=document.getElementById('a_about2').value;
  siteData.ftCol1=document.getElementById('a_ftCol1').value;
  siteData.cats=document.getElementById('a_cats').value;
  siteData.mq=document.getElementById('a_mq').value;

  // Apply to DOM
  if(!siteData.logoImg){
    document.getElementById('navLogo').textContent=siteData.siteName;
  }
  document.getElementById('heroEyebrow').textContent=siteData.eyebrow;
  document.getElementById('heroTitle').textContent=siteData.siteName;
  document.getElementById('heroTag').textContent=siteData.tag;
  document.getElementById('navRight').textContent=siteData.navRight;
  document.getElementById('homeSectionTitle').textContent=siteData.homeSecTitle;
  document.getElementById('footerTagline').textContent=siteData.ftTag;
  document.getElementById('ftCopy').textContent=siteData.copy;
  document.getElementById('contactPhone').innerHTML=`<strong>${siteData.phone}</strong><br>Mon–Fri, 9am–6pm CET`;
  document.getElementById('contactEmail').textContent=siteData.email;
  document.getElementById('contactAddr').innerHTML=siteData.addr.replace('\n','<br>');
  document.getElementById('contactHours').innerHTML=siteData.hours.replace('\n','<br>');
  document.getElementById('aboutText').textContent=siteData.about1;
  document.getElementById('aboutText2').textContent=siteData.about2;
  document.getElementById('ftEmail').textContent=siteData.email;
  document.getElementById('ftPhone').textContent=siteData.phone;
  document.getElementById('ftAddr').textContent=siteData.addr.split('\n')[0];
  document.getElementById('ftCopy').textContent=siteData.copy;
  // Footer col1
  const col1Lines=siteData.ftCol1.split('\n').filter(Boolean);
  document.getElementById('footerCol1').innerHTML=col1Lines.map(l=>`<li>${l}</li>`).join('');
  // Marquee
  const mqItems=siteData.mq.split('|').map(i=>i.trim()).filter(Boolean);
  const track=document.getElementById('mqTrack');
  const doubled=[...mqItems,...mqItems];
  track.innerHTML=doubled.map(i=>`<span class="mq-item"><span>✦</span>${i}</span>`).join('');

  applyColors();applyFonts();applyLogoToPage();
  renderHome();renderCatDropdown();
  showToast('✦ All Changes Applied');
}

function applyColors(){
  const bg=document.getElementById('c_bg').value;
  const ac=document.getElementById('c_ac').value;
  const tx=document.getElementById('c_tx').value;
  const sf=document.getElementById('c_sf').value;
  document.documentElement.style.setProperty('--bg',bg);
  document.documentElement.style.setProperty('--accent',ac);
  document.documentElement.style.setProperty('--text',tx);
  document.documentElement.style.setProperty('--surface',sf);
  ['c_bgH','c_acH','c_txH','c_sfH'].forEach((id,i)=>{
    document.getElementById(id).value=[bg,ac,tx,sf][i];
  });
}

function syncHex(k){
  const map={bg:['c_bg','c_bgH'],ac:['c_ac','c_acH'],tx:['c_tx','c_txH'],sf:['c_sf','c_sfH']};
  const [cid,hid]=map[k];
  const val=document.getElementById(hid).value;
  if(/^#[0-9a-fA-F]{6}$/.test(val)){document.getElementById(cid).value=val;applyColors();}
}

function applyFonts(){
  document.documentElement.style.setProperty('--fd',document.getElementById('f_disp').value);
  document.documentElement.style.setProperty('--fb',document.getElementById('f_body').value);
}

function changePass(){
  const np=document.getElementById('a_newPass').value.trim();
  if(!np)return;
  adminPass=np;localStorage.setItem(PASS_KEY,adminPass);
  document.getElementById('a_newPass').value='';
  showToast('Password Updated');
}

function showToast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg;t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2600);
}

// ─── ESC ───
document.addEventListener('keydown',e=>{
  if(e.key==='Escape'){closeAuth();closeAdmin();closeCatDropdown();}
});

// ─── INIT ───
renderHome();
renderCatDropdown();
</script>
</body>
</html>
