
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=VT323&display=swap');

  .crt-wrap {
    background: #0a0800;
    font-family: 'Share Tech Mono', monospace;
    color: #ffb000;
    padding: 0;
    min-height: 100vh;
    position: relative;
    overflow: hidden;
  }
  .scanlines {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    pointer-events: none;
    background: repeating-linear-gradient(
      to bottom,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.08) 2px,
      rgba(0,0,0,0.08) 4px
    );
    z-index: 100;
  }
  .terminal-header {
    border-bottom: 1px solid #ffb000;
    padding: 12px 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    background: #0d0a00;
  }
  .dot { width: 10px; height: 10px; border-radius: 50%; display: inline-block; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #febc2e; }
  .dot-g { background: #28c840; }
  .term-title { color: #ffb000aa; font-size: 13px; margin-left: auto; }
  .section { padding: 20px; }
  .prompt { color: #ff8c00; font-size: 13px; }
  .cmd { color: #ffb000; font-size: 13px; }
  .output { color: #ffd060; font-size: 13px; }
  .dim { color: #ffb00066; font-size: 12px; }
  .blink { animation: blink 1.1s step-end infinite; }
  @keyframes blink { 50% { opacity: 0; } }
  .ascii-banner {
    font-family: 'VT323', monospace;
    font-size: 22px;
    color: #ff8c00;
    line-height: 1.1;
    white-space: pre;
    margin: 10px 0;
    letter-spacing: 1px;
  }
  .amber-box {
    border: 1px solid #ffb000;
    padding: 14px 16px;
    margin: 10px 0;
    background: #0d0900;
    position: relative;
  }
  .amber-box::before {
    content: attr(data-label);
    position: absolute;
    top: -9px;
    left: 12px;
    background: #0a0800;
    padding: 0 6px;
    font-size: 11px;
    color: #ff8c00;
    letter-spacing: 2px;
    text-transform: uppercase;
  }
  .stat-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 8px;
    margin: 10px 0;
  }
  .stat-cell {
    border: 1px solid #ffb00055;
    padding: 10px;
    text-align: center;
    background: #0d0900;
  }
  .stat-num {
    font-family: 'VT323', monospace;
    font-size: 26px;
    color: #ff8c00;
    line-height: 1;
  }
  .stat-lbl { font-size: 10px; color: #ffb00077; letter-spacing: 1px; margin-top: 2px; }
  .skill-tag {
    display: inline-block;
    border: 1px solid #ffb00066;
    padding: 2px 8px;
    margin: 3px 2px;
    font-size: 11px;
    color: #ffd060;
    background: #0d0900;
  }
  .skill-tag.hot {
    border-color: #ff8c00;
    color: #ff8c00;
    background: #1a0c00;
  }
  .progress-bar {
    background: #1a1000;
    height: 8px;
    border: 1px solid #ffb00044;
    margin: 4px 0;
    position: relative;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    background: #ff8c00;
    position: relative;
  }
  .progress-fill::after {
    content: '';
    position: absolute;
    right: 0; top: 0; bottom: 0;
    width: 2px;
    background: #fff5cc;
    animation: scan 2s linear infinite;
  }
  @keyframes scan { 0%,100% { opacity: 1; } 50% { opacity: 0.3; } }
  .lang-row { display: flex; align-items: center; gap: 8px; margin: 5px 0; font-size: 12px; }
  .lang-name { width: 90px; color: #ffd060; }
  .lang-bar { flex: 1; }
  .lang-pct { width: 40px; text-align: right; color: #ff8c00; }
  .about-line { color: #ffd060; font-size: 13px; line-height: 1.8; }
  .about-key { color: #ff8c00; }
  .funny-box {
    border: 1px dashed #ffb00055;
    padding: 12px;
    margin: 10px 0;
    background: #0a0800;
    font-size: 12px;
    color: #ffb000aa;
    font-style: italic;
  }
  .badge {
    display: inline-block;
    background: #1a0c00;
    border: 1px solid #ff8c00;
    color: #ffd060;
    font-size: 10px;
    padding: 2px 7px;
    margin: 2px;
    letter-spacing: 1px;
  }
  .divider { border: none; border-top: 1px solid #ffb00033; margin: 12px 0; }
  .cursor-block { display: inline-block; width: 9px; height: 14px; background: #ffb000; vertical-align: middle; animation: blink 1.1s step-end infinite; margin-left: 2px; }
  .trophy { color: #ffd060; font-size: 12px; }
  .section-cmd { color: #ff8c00; font-size: 12px; margin: 14px 0 4px; letter-spacing: 1px; }
  .glitch {
    position: relative;
    display: inline-block;
    animation: glitch 5s infinite;
  }
  @keyframes glitch {
    0%,95%,100% { transform: none; text-shadow: none; }
    96% { transform: translateX(-2px); text-shadow: 2px 0 #ff0000; }
    97% { transform: translateX(2px); text-shadow: -2px 0 #00ffff; }
    98% { transform: none; }
  }
</style>

<div class="crt-wrap">
  <div class="scanlines"></div>

  <div class="terminal-header">
    <span class="dot dot-r"></span>
    <span class="dot dot-y"></span>
    <span class="dot dot-g"></span>
    <span class="term-title">ragini@kali:~/github/README.md — bash</span>
  </div>

  <div class="section">
    <div class="prompt">root@kali:~# <span class="cmd">cat ./identity.sh</span></div>
    <br>
    <div class="ascii-banner glitch">██████╗  █████╗  ██████╗ ██╗███╗  ██╗██╗
██╔══██╗██╔══██╗██╔════╝ ██║████╗ ██║██║
██████╔╝███████║██║  ███╗██║██╔██╗██║██║
██╔══██╗██╔══██║██║   ██║██║██║╚████║██║
██║  ██║██║  ██║╚██████╔╝██║██║ ╚███║██║
╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝╚═╝  ╚══╝╚═╝</div>
    <div style="margin-top:6px; font-family:'VT323',monospace; font-size:20px; color:#ffb000aa; letter-spacing:3px;">SINGH</div>

    <br>
    <div class="output">
      <span style="color:#ff8c00;">[ </span>Cybersecurity Student<span style="color:#ff8c00;"> | </span>CTF Player<span style="color:#ff8c00;"> | </span>Linux Dweller<span style="color:#ff8c00;"> | </span>Breaker of Things<span style="color:#ff8c00;"> ]</span>
    </div>

    <div class="badge">PWN</div>
    <div class="badge">WEB-HACK</div>
    <div class="badge">REV-ENG</div>
    <div class="badge">MALWARE</div>
    <div class="badge">CTF</div>
    <div class="badge">KALI-LINUX</div>

    <hr class="divider">

    <div class="section-cmd"># --- SYSTEM INFO ---</div>
    <div class="amber-box" data-label="whoami">
      <div class="about-line"><span class="about-key">name</span>       : Ragini Singh</div>
      <div class="about-line"><span class="about-key">handle</span>     : Raagini-Singh</div>
      <div class="about-line"><span class="about-key">os</span>         : Kali Linux (permanent resident, no plans to leave)</div>
      <div class="about-line"><span class="about-key">specialty</span>  : All of the above chaos</div>
      <div class="about-line"><span class="about-key">philosophy</span> : breaks things first, asks questions <span style="color:#ff4444;">never</span></div>
      <div class="about-line"><span class="about-key">status</span>     : currently pwning something<span class="cursor-block"></span></div>
    </div>

    <hr class="divider">

    <div class="section-cmd"># --- GITHUB STATS (live) ---</div>
    <div class="prompt" style="font-size:11px; margin-bottom:8px;">root@kali:~# <span class="cmd">curl -s https://api.github.com/users/Raagini-Singh/stats | jq</span></div>

    <div class="stat-grid">
      <div class="stat-cell">
        <div class="stat-num" id="s-commits">...</div>
        <div class="stat-lbl">COMMITS</div>
      </div>
      <div class="stat-cell">
        <div class="stat-num" id="s-repos">...</div>
        <div class="stat-lbl">REPOS</div>
      </div>
      <div class="stat-cell">
        <div class="stat-num" id="s-stars">...</div>
        <div class="stat-lbl">STARS</div>
      </div>
    </div>

    <hr class="divider">

    <div class="section-cmd"># --- TOP LANGUAGES ---</div>
    <div class="amber-box" data-label="lang-profile">
      <div class="lang-row"><span class="lang-name">Python</span><div class="lang-bar"><div class="progress-bar"><div class="progress-fill" style="width:85%"></div></div></div><span class="lang-pct">85%</span></div>
      <div class="lang-row"><span class="lang-name">Bash</span><div class="lang-bar"><div class="progress-bar"><div class="progress-fill" style="width:78%"></div></div></div><span class="lang-pct">78%</span></div>
      <div class="lang-row"><span class="lang-name">C / C++</span><div class="lang-bar"><div class="progress-bar"><div class="progress-fill" style="width:60%"></div></div></div><span class="lang-pct">60%</span></div>
      <div class="lang-row"><span class="lang-name">JavaScript</span><div class="lang-bar"><div class="progress-bar"><div class="progress-fill" style="width:45%"></div></div></div><span class="lang-pct">45%</span></div>
      <div class="lang-row"><span class="lang-name">SQL</span><div class="lang-bar"><div class="progress-bar"><div class="progress-fill" style="width:38%"></div></div></div><span class="lang-pct">38%</span></div>
    </div>

    <hr class="divider">

    <div class="section-cmd"># --- ARSENAL (tools i use to cause problems) ---</div>
    <div class="amber-box" data-label="tools">
      <div style="margin-bottom:6px; font-size:11px; color:#ff8c0088;">[ PWN / EXPLOIT ]</div>
      <span class="skill-tag hot">pwntools</span><span class="skill-tag hot">GDB</span><span class="skill-tag hot">ROPgadget</span><span class="skill-tag">checksec</span><span class="skill-tag">ltrace</span>
      <div style="margin: 8px 0 6px; font-size:11px; color:#ff8c0088;">[ WEB HACKING ]</div>
      <span class="skill-tag hot">Burp Suite</span><span class="skill-tag hot">SQLmap</span><span class="skill-tag">ffuf</span><span class="skill-tag">Nikto</span><span class="skill-tag">hydra</span>
      <div style="margin: 8px 0 6px; font-size:11px; color:#ff8c0088;">[ REVERSE ENGINEERING ]</div>
      <span class="skill-tag hot">Ghidra</span><span class="skill-tag hot">radare2</span><span class="skill-tag">strings</span><span class="skill-tag">objdump</span><span class="skill-tag">strace</span>
      <div style="margin: 8px 0 6px; font-size:11px; color:#ff8c0088;">[ NETWORK / OSINT ]</div>
      <span class="skill-tag">Nmap</span><span class="skill-tag">Wireshark</span><span class="skill-tag">Metasploit</span><span class="skill-tag">netcat</span><span class="skill-tag hot">curl</span>
    </div>

    <hr class="divider">

    <div class="section-cmd"># --- CTF PLATFORMS ---</div>
    <div style="margin: 8px 0;">
      <span class="badge" style="border-color:#22ff88; color:#22ff88;">HTB</span>
      <span class="badge" style="border-color:#ff4422; color:#ff4422;">TryHackMe</span>
      <span class="badge" style="border-color:#4488ff; color:#4488ff;">PicoCTF</span>
      <span class="badge">CTFtime</span>
      <span class="badge">pwn.college</span>
    </div>

    <hr class="divider">

    <div class="section-cmd"># --- /etc/ragini/about_me.log ---</div>
    <div class="funny-box">
      <div style="color:#ff8c00; font-style:normal; font-size:11px; margin-bottom:6px; letter-spacing:2px;">[ CLASSIFIED — HUMOR CLEARANCE REQUIRED ]</div>
      <div style="line-height:2;">
        &gt; Her terminal has more uptime than most relationships.<br>
        &gt; Once ran `rm -rf /` on a CTF box and called it "aggressive enumeration."<br>
        &gt; Reads man pages for fun. Voluntarily.<br>
        &gt; Considers 3am "early" if there's a CTF running.<br>
        &gt; Current threat level to CTF organizers: <span style="color:#ff4444; font-style:normal;">elevated.</span><br>
        &gt; Error 404: sleep not found.<br>
        &gt; Her approach to new systems: <span style="color:#ff8c00; font-style:normal;">break first, patch never, blame the binary.</span>
      </div>
    </div>

    <hr class="divider">

    <div class="section-cmd"># --- CURRENT LEARNING ---</div>
    <div class="amber-box" data-label="learning.log">
      <div class="output" style="line-height:2;">
        <span style="color:#ff8c00;">[+]</span> Advanced binary exploitation<br>
        <span style="color:#ff8c00;">[+]</span> Kernel pwn & privilege escalation<br>
        <span style="color:#ff8c00;">[+]</span> Malware analysis & reverse engineering<br>
        <span style="color:#ff8c00;">[~]</span> Web app security (OWASP Top 10 + beyond)<br>
        <span style="color:#ff8c00;">[~]</span> Network protocol fuzzing<br>
        <span style="color:#ffb00066;">[ ]</span> Sleeping. (someday.)
      </div>
    </div>

    <hr class="divider">

    <div class="prompt" style="margin-top:16px;">root@kali:~# <span class="cmd">echo "reach me at:"</span></div>
    <div style="margin: 8px 0; font-size:13px; color:#ffd060;">
      <span style="color:#ff8c00;">github</span>  → github.com/Raagini-Singh<br>
      <span style="color:#ff8c00;">status</span>  → actively breaking things
    </div>

    <div style="margin-top:20px; font-size:11px; color:#ffb00044; letter-spacing:1px; text-align:center;">
      — made with <span style="color:#ff8c00;">chaos</span>, caffeine & a love for root shells —<br>
      <span class="dim">last boot: kali linux | uptime: ∞</span>
    </div>

    <div style="height:16px; display:flex; align-items:center; margin-top:12px;">
      <span class="prompt" style="font-size:12px;">root@kali:~# </span><span class="cursor-block"></span>
    </div>
  </div>
</div>

<script>
async function fetchStats() {
  try {
    const r = await fetch('https://api.github.com/users/Raagini-Singh');
    const d = await r.json();
    document.getElementById('s-repos').textContent = d.public_repos || '—';
    const rr = await fetch('https://api.github.com/users/Raagini-Singh/repos?per_page=100');
    const repos = await rr.json();
    let stars = 0;
    if (Array.isArray(repos)) repos.forEach(r => stars += r.stargazers_count || 0);
    document.getElementById('s-stars').textContent = stars;
    document.getElementById('s-commits').textContent = '∞';
  } catch(e) {
    document.getElementById('s-commits').textContent = '9k+';
    document.getElementById('s-repos').textContent = '—';
    document.getElementById('s-stars').textContent = '—';
  }
}
fetchStats();
</script>
