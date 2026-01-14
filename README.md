# olivers-home-alone-real.html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Oliver’s Home Alone Games</title>
  <style>
    :root{
      --bg1:#0b1020; --bg2:#0a0f1a; --card:rgba(255,255,255,.06);
      --line:rgba(255,255,255,.14); --text:#e6edf6; --muted:#a7b3c7;
      --accent:#60a5fa; --good:#34d399; --bad:#fb7185;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;
      color:var(--text);
      background:
        radial-gradient(1200px 700px at 50% -10%, #1a2a55, transparent 60%),
        radial-gradient(900px 600px at 10% 20%, #0f3a2a, transparent 55%),
        linear-gradient(180deg, var(--bg1), var(--bg2));
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:18px;
    }
    .wrap{width:min(980px,100%); display:grid; gap:14px;}
    .header{
      border:1px solid var(--line);
      border-radius:16px;
      padding:16px 16px 14px;
      background: linear-gradient(180deg, rgba(255,255,255,.07), rgba(255,255,255,.03));
    }
    h1{margin:0 0 6px; font-size:26px; letter-spacing:.2px}
    p{margin:0; color:var(--muted); line-height:1.4}
    .grid{display:grid; grid-template-columns: 1.2fr .8fr; gap:14px}
    @media (max-width: 820px){ .grid{grid-template-columns:1fr} }
    .card{
      border:1px solid var(--line);
      border-radius:16px;
      background: var(--card);
      padding:14px;
    }
    .card h2{margin:0 0 8px; font-size:16px}
    .btns{display:grid; gap:10px; margin-top:12px}
    a.btn{
      display:flex; align-items:center; justify-content:space-between; gap:10px;
      text-decoration:none; color:var(--text);
      border:1px solid var(--line);
      border-radius:14px;
      padding:12px 12px;
      background: rgba(255,255,255,.05);
      transition: transform .08s ease, border-color .08s ease;
      font-weight:700;
    }
    a.btn:hover{ transform: translateY(-1px); border-color: rgba(96,165,250,.5); }
    .tag{
      font-size:12px;
      color:var(--muted);
      border:1px solid rgba(255,255,255,.16);
      padding:4px 8px;
      border-radius:999px;
      white-space:nowrap;
    }
    .small{font-size:13px; color:var(--muted); line-height:1.45}
    .kbd{
      font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
      font-size:12px;
      padding:2px 6px;
      border-radius:6px;
      border:1px solid rgba(255,255,255,.18);
      background: rgba(255,255,255,.06);
      color:var(--text);
    }
    .row{display:flex; gap:10px; flex-wrap:wrap; align-items:center; margin-top:10px}
    input{
      flex:1;
      min-width: 220px;
      padding:10px 12px;
      border-radius:12px;
      border:1px solid var(--line);
      background: rgba(0,0,0,.18);
      color:var(--text);
      outline:none;
    }
    button{
      padding:10px 12px;
      border-radius:12px;
      border:1px solid rgba(96,165,250,.45);
      background: rgba(96,165,250,.12);
      color:var(--text);
      font-weight:800;
      cursor:pointer;
    }
    .result{margin-top:10px; font-size:13px}
    .good{color:var(--good); font-weight:800}
    .bad{color:var(--bad); font-weight:800}
    .footer{font-size:12px; color:var(--muted); text-align:center; padding:6px}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="header">
      <h1>Oliver’s Home Alone</h1>
      <p>A little scary POV game hub. Click a version below.</p>
    </div>

    <div class="grid">
      <div class="card">
        <h2>🎮 Play</h2>

        <div class="btns">
          <!-- CHANGE these filenames to match EXACTLY what exists in your repo -->
          <a class="btn" href="./olivers-home-alone.html">
            Home Alone (Original)
            <span class="tag">2D / classic</span>
          </a>

          <a class="btn" href="./olivers-home-alone-v2.html">
            Home Alone (V2)
            <span class="tag">newest</span>
          </a>

          <a class="btn" href="./test.html">
            TEST page
            <span class="tag">should say “TEST OK”</span>
          </a>
        </div>

        <p class="small" style="margin-top:12px;">
          If you get a gray screen in POV games, click the game area to capture the mouse.
          Press <span class="kbd">Esc</span> to release the mouse.
        </p>

        <p class="small" style="margin-top:8px;">
          Controls usually: <span class="kbd">WASD</span> move • <span class="kbd">E</span> interact • <span class="kbd">F</span> flashlight • <span class="kbd">I</span> inventory
        </p>
      </div>

      <div class="card">
        <h2>🔎 Link Checker (stops 404 pain)</h2>
        <p class="small">
          Type the exact filename you created in GitHub (example: <span class="kbd">olivers-home-alone-v2.html</span>)
          and click Check. If it says “FOUND”, your link is correct.
        </p>

        <div class="row">
          <input id="fname" placeholder="Type filename… e.g. olivers-home-alone-v2.html" />
          <button id="checkBtn">Check</button>
        </div>

        <div class="result" id="result"></div>

        <p class="small" style="margin-top:10px;">
          Important: filenames must match EXACTLY (dashes vs underscores, spelling, and capital letters).
        </p>
      </div>
    </div>

    <div class="footer">
      Tip: If V2 shows 404, the file is either spelled differently or is inside a folder. Put it in the repo root.
    </div>
  </div>

  <script>
    const result = document.getElementById("result");
    const input = document.getElementById("fname");
    document.getElementById("checkBtn").addEventListener("click", async () => {
      const name = (input.value || "").trim();
      if (!name) {
        result.innerHTML = `<span class="bad">Type a filename first.</span>`;
        return;
      }
      try {
        const res = await fetch("./" + name, { method: "HEAD" });
        if (res.ok) {
          result.innerHTML = `<span class="good">FOUND ✅</span> Your link should be: <span class="kbd">https://ryant14.github.io/olivers-home-alone/${name}</span>`;
        } else {
          result.innerHTML = `<span class="bad">NOT FOUND ❌</span> That filename is not being served here. Check spelling OR if it’s in a folder.`;
        }
      } catch (e) {
        result.innerHTML = `<span class="bad">Couldn’t check.</span> Try refreshing and checking your internet.`;
      }
    });
  </script>
</body>
</html>
