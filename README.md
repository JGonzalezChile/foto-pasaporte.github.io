<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>ePhoto France — Formato ANTS 35×45 mm</title>
<style>
  :root{
    --bleu:#000091;
    --rouge:#E1000F;
    --ink:#14172B;
    --paper:#F7F8FA;
    --card:#FFFFFF;
    --line:#D8DDE4;
    --muted:#5B6470;
    --ok:#1E7F4F;
    --warn:#B05A00;
    --gris-photo:#E9EDF0;
    font-size:16px;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  body{
    background:var(--paper);
    color:var(--ink);
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
    line-height:1.45;
    -webkit-text-size-adjust:100%;
  }
  /* ---------- Encabezado estilo formulario oficial ---------- */
  header{
    background:var(--card);
    border-bottom:1px solid var(--line);
    padding:14px 20px 12px;
  }
  .tricolore{display:flex;height:4px;width:72px;margin-bottom:10px}
  .tricolore span{flex:1}
  .tricolore span:nth-child(1){background:var(--bleu)}
  .tricolore span:nth-child(2){background:#fff;border-top:1px solid var(--line);border-bottom:1px solid var(--line)}
  .tricolore span:nth-child(3){background:var(--rouge)}
  header h1{font-size:1.05rem;font-weight:700;letter-spacing:.02em}
  header .sub{
    font-size:.72rem;color:var(--muted);
    text-transform:uppercase;letter-spacing:.14em;margin-top:2px;
  }
  /* ---------- Layout ---------- */
  main{
    max-width:1060px;margin:0 auto;padding:18px 16px 60px;
    display:grid;grid-template-columns:minmax(0,1fr) minmax(0,1fr);gap:18px;
  }
  @media(max-width:860px){main{grid-template-columns:1fr}}
  section.card{
    background:var(--card);border:1px solid var(--line);border-radius:10px;
    padding:16px;
  }
  h2{
    font-size:.72rem;text-transform:uppercase;letter-spacing:.14em;
    color:var(--bleu);margin-bottom:12px;font-weight:700;
  }
  /* ---------- Zona de carga ---------- */
  #dropzone{
    border:1.5px dashed var(--bleu);border-radius:8px;
    padding:22px 14px;text-align:center;cursor:pointer;
    background:#F4F5FF;transition:background .15s;
    font-size:.9rem;
  }
  #dropzone:hover{background:#EBEDFF}
  #dropzone strong{color:var(--bleu)}
  #fileInput{display:none}
  /* ---------- Marco editor ---------- */
  #editorWrap{display:none}
  #frameOuter{
    position:relative;margin:6px auto 0;
    width:100%;max-width:380px;
    touch-action:none;
    user-select:none;-webkit-user-select:none;
  }
  #frameSvgWrap{position:relative;width:100%}
  #cv{
    position:absolute;
    background:#fff;
    cursor:grab;
    border:1px solid var(--ink);
  }
  #cv.dragging{cursor:grabbing}
  #overlay{position:absolute;pointer-events:none}
  #toggleGuides{
    position:absolute;z-index:5;
    width:32px;height:32px;padding:0;
    display:flex;align-items:center;justify-content:center;
    background:rgba(255,255,255,.92);color:var(--bleu);
    border:1px solid var(--line);border-radius:50%;
    box-shadow:0 1px 4px rgba(0,0,0,.18);cursor:pointer;
  }
  #toggleGuides:hover{background:#fff}
  .controls{margin-top:14px;display:grid;gap:12px}
  .ctl label{
    display:flex;justify-content:space-between;
    font-size:.78rem;color:var(--muted);margin-bottom:4px;
    text-transform:uppercase;letter-spacing:.08em;
  }
  .ctl output{font-variant-numeric:tabular-nums;color:var(--ink);font-weight:600}
  input[type=range]{width:100%;accent-color:var(--bleu)}
  .btnrow{display:flex;gap:8px;flex-wrap:wrap;margin-top:4px}
  button,.btn{
    font:inherit;font-size:.86rem;font-weight:600;
    padding:9px 16px;border-radius:7px;border:1px solid var(--bleu);
    background:var(--bleu);color:#fff;cursor:pointer;
    text-decoration:none;display:inline-block;
  }
  button.secondary{background:#fff;color:var(--bleu)}
  button:active{transform:translateY(1px)}
  .hint{font-size:.78rem;color:var(--muted);margin-top:8px}
  /* ---------- Exportación ---------- */
  .exportrow{display:flex;align-items:center;gap:10px;flex-wrap:wrap}
  select{
    font:inherit;font-size:.86rem;padding:8px 10px;
    border:1px solid var(--line);border-radius:7px;background:#fff;color:var(--ink);
  }
  #result{display:none;margin-top:14px;border-top:1px solid var(--line);padding-top:14px}
  #result img{
    width:120px;border:1px solid var(--ink);display:block;margin-bottom:8px;
  }
  .meta{font-size:.8rem;color:var(--muted);font-variant-numeric:tabular-nums}
  .meta b{color:var(--ink)}
  .check-ok{color:var(--ok);font-weight:600;font-size:.82rem}
  .check-warn{color:var(--warn);font-weight:600;font-size:.82rem}
  .check-err{color:var(--rouge);font-weight:600;font-size:.82rem}
  /* ---------- Checklist ---------- */
  ul.checklist{list-style:none;display:grid;gap:7px}
  ul.checklist li{
    display:flex;gap:9px;align-items:flex-start;
    font-size:.84rem;
  }
  ul.checklist input{margin-top:3px;accent-color:var(--bleu);flex-shrink:0}
  ul.checklist li.done span{color:var(--muted);text-decoration:line-through}
  /* ---------- Cajas info ---------- */
  .note{
    border-left:3px solid var(--bleu);background:#F4F5FF;
    padding:10px 12px;border-radius:0 7px 7px 0;
    font-size:.82rem;margin-top:12px;
  }
  .note.alert{border-left-color:var(--rouge);background:#FFF3F3}
  .note b{font-weight:700}
  code{
    font-family:ui-monospace,"SF Mono",Menlo,Consolas,monospace;
    font-size:.86em;background:#EEF0F4;padding:1px 5px;border-radius:4px;
  }
  footer{
    text-align:center;font-size:.72rem;color:var(--muted);
    padding:0 16px 30px;
  }
</style>
</head>
<body>

<header>
  <div class="tricolore"><span></span><span></span><span></span></div>
  <h1>ePhoto France — formato ANTS</h1>
  <div class="sub">Photo d'identité · 35 × 45 mm · 300 dpi · JPEG</div>
</header>

<main>
  <!-- ============ COLUMNA IZQUIERDA: EDITOR ============ -->
  <section class="card">
    <h2>1 · Cargar y encuadrar</h2>

    <div id="dropzone">
      <strong>Toca aquí o arrastra tu foto</strong><br>
      JPG, PNG o HEIC convertido · idealmente la foto original sin recortar
      <input type="file" id="fileInput" accept="image/*">
    </div>

    <div id="editorWrap">
      <div id="frameOuter">
        <svg id="frameSvgWrap" viewBox="-6 -6 47 57" xmlns="http://www.w3.org/2000/svg">
          <!-- Reglas milimétricas -->
          <g id="rulers" stroke="#9AA3AE" stroke-width="0.25" font-family="ui-monospace,Menlo,monospace" font-size="2" fill="#5B6470">
            <!-- regla superior (35 mm) -->
            <line x1="0" y1="-1.2" x2="0" y2="0"/><line x1="5" y1="-1.2" x2="5" y2="0"/>
            <line x1="10" y1="-1.8" x2="10" y2="0"/><line x1="15" y1="-1.2" x2="15" y2="0"/>
            <line x1="20" y1="-1.8" x2="20" y2="0"/><line x1="25" y1="-1.2" x2="25" y2="0"/>
            <line x1="30" y1="-1.8" x2="30" y2="0"/><line x1="35" y1="-1.2" x2="35" y2="0"/>
            <text x="-0.6" y="-2.6" stroke="none">0</text>
            <text x="33" y="-2.6" stroke="none">35</text>
            <!-- regla izquierda (45 mm) -->
            <line x1="-1.2" y1="0" x2="0" y2="0"/><line x1="-1.2" y1="5" x2="0" y2="5"/>
            <line x1="-1.8" y1="10" x2="0" y2="10"/><line x1="-1.2" y1="15" x2="0" y2="15"/>
            <line x1="-1.8" y1="20" x2="0" y2="20"/><line x1="-1.2" y1="25" x2="0" y2="25"/>
            <line x1="-1.8" y1="30" x2="0" y2="30"/><line x1="-1.2" y1="35" x2="0" y2="35"/>
            <line x1="-1.8" y1="40" x2="0" y2="40"/><line x1="-1.2" y1="45" x2="0" y2="45"/>
            <text x="-5.4" y="2" stroke="none">0</text>
            <text x="-5.6" y="46" stroke="none">45</text>
            <text x="-5.4" y="38.6" stroke="none" font-size="1.8">mm</text>
          </g>
        </svg>
        <canvas id="cv"></canvas>
        <!-- Guías superpuestas -->
        <svg id="overlay" viewBox="0 0 35 45" preserveAspectRatio="none" xmlns="http://www.w3.org/2000/svg">
          <!-- óvalo guía: dónde debe ir la cabeza (coronilla y=5, mentón y≈39) -->
          <ellipse cx="17.5" cy="22" rx="12" ry="17" fill="#7B8794" fill-opacity="0.12"
                   stroke="#6B7280" stroke-width="0.35" stroke-dasharray="1.3 1"/>
          <!-- zona aceptable del mentón: cabeza 32–36 mm bajo la coronilla -->
          <rect x="0" y="37" width="35" height="4" fill="#1E7F4F" opacity="0.16"/>
          <line x1="0" y1="37" x2="35" y2="37" stroke="#1E7F4F" stroke-width="0.25" stroke-dasharray="1 0.8"/>
          <line x1="0" y1="41" x2="35" y2="41" stroke="#1E7F4F" stroke-width="0.25" stroke-dasharray="1 0.8"/>
          <!-- línea de coronilla -->
          <line x1="0" y1="5" x2="35" y2="5" stroke="#000091" stroke-width="0.3"/>
          <!-- eje central punteado -->
          <line x1="17.5" y1="0" x2="17.5" y2="45" stroke="#000091" stroke-width="0.3" stroke-dasharray="1 1"/>
          <!-- etiquetas legibles sobre cualquier foto: relleno blanco + contorno oscuro -->
          <text x="0.8" y="4.2" font-size="2.1" font-weight="bold" font-family="sans-serif"
                fill="#FFFFFF" stroke="#14172B" stroke-width="0.34"
                paint-order="stroke" stroke-linejoin="round">CORONILLA aquí ↓</text>
          <text x="0.8" y="39.9" font-size="2.1" font-weight="bold" font-family="sans-serif"
                fill="#FFFFFF" stroke="#14532D" stroke-width="0.34"
                paint-order="stroke" stroke-linejoin="round">MENTÓN en esta banda</text>
        </svg>
        <button id="toggleGuides" type="button" aria-pressed="true" title="Mostrar / ocultar guías">
          <svg id="eyeOpen" viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/><circle cx="12" cy="12" r="3"/></svg>
          <svg id="eyeClosed" viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="display:none"><path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94"/><path d="M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19"/><line x1="1" y1="1" x2="23" y2="23"/></svg>
        </button>
      </div>

      <div class="controls">
        <div class="ctl">
          <label>Zoom <output id="zoomOut">1.00×</output></label>
          <input type="range" id="zoomSlider" min="1" max="6" step="0.01" value="1">
        </div>
        <div class="ctl">
          <label>Rotación fina <output id="rotOut">0.0°</output></label>
          <input type="range" id="rotSlider" min="-10" max="10" step="0.1" value="0">
        </div>
        <div class="btnrow">
          <button class="secondary" id="resetBtn" type="button">Reiniciar encuadre</button>
          <button class="secondary" id="newPhotoBtn" type="button">Otra foto</button>
        </div>
        <p class="hint">
          Arrastra la foto con el dedo o el mouse para moverla. Rueda del mouse o pellizco para
          hacer zoom. Objetivo: la parte superior del pelo toca la <b style="color:var(--bleu)">línea azul</b>
          y el mentón cae dentro de la <b style="color:var(--ok)">banda verde</b> — así la cabeza mide
          automáticamente entre 3,2 y 3,6 cm (70–80 % de la foto).
        </p>
      </div>
    </div>

    <div class="note">
      <b>¿Por qué el zoom de tu pantalla no cambia los cm?</b> Porque el tamaño físico de una
      foto digital no está en lo que ves, sino en dos números grabados dentro del archivo:
      los <b>píxeles</b> y los <b>DPI</b> (puntos por pulgada).
      Fórmula: <code>cm = píxeles ÷ DPI × 2,54</code>.
      Esta herramienta exporta exactamente <code>413 × 531 px a 300 DPI</code>
      → 413÷300×2,54 = <b>3,5 cm</b> y 531÷300×2,54 = <b>4,5 cm</b>, sin importar cuánto
      zoom le hagas en el PC.
    </div>
  </section>

  <!-- ============ COLUMNA DERECHA: EXPORT + CHECKLIST ============ -->
  <div style="display:grid;gap:18px;align-content:start">
    <section class="card">
      <h2>2 · Generar JPEG</h2>
      <div class="exportrow">
        <select id="dpiSel">
          <option value="300" selected>300 dpi · 413×531 px (estándar ANTS)</option>
          <option value="600">600 dpi · 827×1063 px (alta calidad)</option>
        </select>
        <button id="exportBtn" type="button">Generar JPEG 35×45</button>
      </div>
      <div id="result">
        <img id="resultImg" alt="ePhoto generada">
        <div class="meta" id="resultMeta"></div>
        <div id="bgCheck" style="margin-top:6px"></div>
        <div class="btnrow" style="margin-top:10px">
          <a id="downloadLink" class="btn" download="ephoto-ants-35x45.jpg">⬇ Descargar JPEG</a>
        </div>
      </div>
      <div class="note alert">
        <b>Ojo con el permiso de conducir:</b> para el <i>permis de conduire</i>, ANTS exige una
        <b>photo-signature numérique con código ePhoto de 22 caracteres</b>, que solo entregan
        fotógrafos o cabinas con la pegatina azul «Agréé services en ligne ANTS» (o apps
        homologadas). Un JPEG hecho en casa sirve para trámites que aceptan subir archivo
        (ANEF/titre de séjour según el caso, CV, tarjetas, etc.) y para <b>preparar y verificar
        tu encuadre antes de ir a la cabina</b> — pero no genera el código.
      </div>
    </section>

    <section class="card">
      <h2>3 · Checklist oficial ANTS</h2>
      <ul class="checklist" id="checklist">
        <li><input type="checkbox"><span>Foto tomada hace <b>menos de 6 meses</b></span></li>
        <li><input type="checkbox"><span>Cabeza de <b>3,2–3,6 cm</b> (mentón→coronilla), 70–80 % de la foto — usa las guías</span></li>
        <li><input type="checkbox"><span>Nítida, sin pliegues, manchas ni granulado</span></li>
        <li><input type="checkbox"><span>Fondo liso <b>gris claro o azul claro</b> — el blanco NO se acepta</span></li>
        <li><input type="checkbox"><span>Foto <b>a color</b></span></li>
        <li><input type="checkbox"><span>Exposición correcta: ni quemada ni oscura</span></li>
        <li><input type="checkbox"><span>Sin sombras en la cara ni en el fondo</span></li>
        <li><input type="checkbox"><span>Cabeza centrada y recta, sin inclinación (usa el slider de rotación)</span></li>
        <li><input type="checkbox"><span>Sin gorro, pañuelo, cintillo ni accesorios (aros grandes, piercings visibles…)</span></li>
        <li><input type="checkbox"><span>Ojos abiertos mirando de frente al lente</span></li>
        <li><input type="checkbox"><span>Boca cerrada, expresión neutra (sin sonreír)</span></li>
        <li><input type="checkbox"><span>El pelo no cubre ojos, orejas ni mejillas</span></li>
        <li><input type="checkbox"><span>Idealmente sin lentes; si los usas: marco fino, sin reflejos ni tinte</span></li>
      </ul>
      <p class="hint" style="margin-top:10px">
        Consejos de toma: luz natural de ventana, cámara a la altura de los ojos,
        ~1,5 m de distancia, fondo sin texturas ni objetos.
      </p>
    </section>
  </div>
</main>

<footer>Herramienta local sin conexión · ePhoto France 35×45 mm · guarda este archivo HTML y úsalo cuando quieras</footer>

<script>
(function(){
  'use strict';
  const MM_W = 35, MM_H = 45, RATIO = MM_H / MM_W;

  const fileInput = document.getElementById('fileInput');
  const dropzone  = document.getElementById('dropzone');
  const editorWrap= document.getElementById('editorWrap');
  const frameOuter= document.getElementById('frameOuter');
  const cv        = document.getElementById('cv');
  const overlay   = document.getElementById('overlay');
  const zoomSlider= document.getElementById('zoomSlider');
  const rotSlider = document.getElementById('rotSlider');
  const zoomOut   = document.getElementById('zoomOut');
  const rotOut    = document.getElementById('rotOut');

  const state = { img:null, natW:0, natH:0, z:1, rot:0, cx:0.5, cy:RATIO/2 };

  /* ---------- Geometría del marco dentro del SVG de reglas ---------- */
  // El SVG exterior tiene viewBox="-6 -6 47 57". El marco 35×45 ocupa (0,0)-(35,45).
  function layoutFrame(){
    const w = frameOuter.clientWidth;            // px del SVG exterior
    const unit = w / 47;                          // px por unidad (mm)
    const fx = 6*unit, fy = 6*unit;               // origen del marco
    const fw = 35*unit, fh = 45*unit;
    for(const el of [cv, overlay]){
      el.style.left   = fx+'px';
      el.style.top    = fy+'px';
      el.style.width  = fw+'px';
      el.style.height = fh+'px';
    }
    const dpr = Math.min(window.devicePixelRatio||1, 3);
    cv.width  = Math.round(fw*dpr);
    cv.height = Math.round(fh*dpr);
    // botón de guías en la esquina superior derecha del marco
    const btn = document.getElementById('toggleGuides');
    btn.style.left = (fx + fw - 38) + 'px';
    btn.style.top  = (fy + 6) + 'px';
    render();
  }
  window.addEventListener('resize', layoutFrame);

  /* ---------- Mostrar / ocultar guías (estilo "ver contraseña") ---------- */
  const toggleBtn = document.getElementById('toggleGuides');
  let guidesVisible = true;
  toggleBtn.addEventListener('click', ()=>{
    guidesVisible = !guidesVisible;
    overlay.style.display = guidesVisible ? '' : 'none';
    document.getElementById('eyeOpen').style.display   = guidesVisible ? '' : 'none';
    document.getElementById('eyeClosed').style.display = guidesVisible ? 'none' : '';
    toggleBtn.setAttribute('aria-pressed', guidesVisible);
  });

  /* ---------- Dibujo (compartido entre vista previa y exportación) ---------- */
  function baseScale(){ return Math.max(1/state.natW, RATIO/state.natH); }

  function draw(ctx, W){
    const H = W*RATIO;
    ctx.setTransform(1,0,0,1,0,0);
    ctx.fillStyle = '#fff';
    ctx.fillRect(0,0,W,H);
    if(!state.img) return;
    ctx.imageSmoothingEnabled = true;
    ctx.imageSmoothingQuality = 'high';
    const s = baseScale()*state.z;
    ctx.setTransform(W,0,0,W,0,0);          // 1 unidad = ancho del marco
    ctx.translate(state.cx, state.cy);
    ctx.rotate(state.rot*Math.PI/180);
    ctx.scale(s,s);
    ctx.drawImage(state.img, -state.natW/2, -state.natH/2);
  }

  function render(){
    const ctx = cv.getContext('2d');
    draw(ctx, cv.width);
  }

  /* ---------- Límites para que la imagen siempre cubra el marco ---------- */
  function clamp(){
    if(!state.img) return;
    const s = baseScale()*state.z;
    const th = Math.abs(state.rot*Math.PI/180);
    const hw = state.natW/2*s, hh = state.natH/2*s;
    const extX = hw*Math.cos(th) + hh*Math.sin(th);
    const extY = hw*Math.sin(th) + hh*Math.cos(th);
    if(extX >= 0.5) state.cx = Math.min(extX, Math.max(1-extX, state.cx));
    else state.cx = 0.5;
    if(extY >= RATIO/2) state.cy = Math.min(extY, Math.max(RATIO-extY, state.cy));
    else state.cy = RATIO/2;
  }

  /* ---------- Cargar imagen ---------- */
  function loadFile(file){
    if(!file || !file.type.startsWith('image/')){ alert('El archivo no es una imagen.'); return; }
    const url = URL.createObjectURL(file);
    const img = new Image();
    img.onload = function(){
      state.img = img; state.natW = img.naturalWidth; state.natH = img.naturalHeight;
      state.z = 1; state.rot = 0; state.cx = 0.5; state.cy = RATIO/2;
      zoomSlider.value = 1; rotSlider.value = 0; updateOutputs();
      dropzone.style.display = 'none';
      editorWrap.style.display = 'block';
      document.getElementById('result').style.display = 'none';
      layoutFrame();
    };
    img.onerror = function(){ alert('No se pudo leer la imagen. Si es HEIC, conviértela antes a JPG.'); };
    img.src = url;
  }

  dropzone.addEventListener('click', ()=>fileInput.click());
  fileInput.addEventListener('change', e=>loadFile(e.target.files[0]));
  document.addEventListener('dragover', e=>e.preventDefault());
  document.addEventListener('drop', e=>{ e.preventDefault(); if(e.dataTransfer.files.length) loadFile(e.dataTransfer.files[0]); });
  document.addEventListener('paste', e=>{
    for(const item of e.clipboardData.items)
      if(item.type.startsWith('image/')){ loadFile(item.getAsFile()); break; }
  });
  document.getElementById('newPhotoBtn').addEventListener('click', ()=>fileInput.click());
  document.getElementById('resetBtn').addEventListener('click', ()=>{
    state.z=1; state.rot=0; state.cx=0.5; state.cy=RATIO/2;
    zoomSlider.value=1; rotSlider.value=0; updateOutputs(); clamp(); render();
  });

  /* ---------- Zoom y rotación ---------- */
  function zoomAbout(f, px, py){           // f = factor, (px,py) punto fijo en unidades de marco
    const newZ = Math.min(6, Math.max(1, state.z*f));
    f = newZ/state.z;
    if(f === 1) return;
    state.cx = px - f*(px - state.cx);
    state.cy = py - f*(py - state.cy);
    state.z = newZ;
    zoomSlider.value = newZ;
    updateOutputs(); clamp(); render();
  }

  zoomSlider.addEventListener('input', ()=>{
    const target = parseFloat(zoomSlider.value);
    zoomAbout(target/state.z, 0.5, RATIO/2);
  });

  rotSlider.addEventListener('input', ()=>{
    const newRot = parseFloat(rotSlider.value);
    const d = (newRot - state.rot)*Math.PI/180;
    // rotar alrededor del centro del marco
    const vx = state.cx-0.5, vy = state.cy-RATIO/2;
    state.cx = 0.5 + vx*Math.cos(d) - vy*Math.sin(d);
    state.cy = RATIO/2 + vx*Math.sin(d) + vy*Math.cos(d);
    state.rot = newRot;
    updateOutputs(); clamp(); render();
  });

  function updateOutputs(){
    zoomOut.textContent = state.z.toFixed(2)+'×';
    rotOut.textContent  = state.rot.toFixed(1)+'°';
  }

  /* ---------- Pan / pinch con punteros ---------- */
  const pointers = new Map();
  let lastMid = null, lastDist = 0;

  cv.addEventListener('pointerdown', e=>{
    cv.setPointerCapture(e.pointerId);
    pointers.set(e.pointerId, {x:e.clientX, y:e.clientY});
    cv.classList.add('dragging');
    if(pointers.size === 2){
      const [a,b] = [...pointers.values()];
      lastDist = Math.hypot(a.x-b.x, a.y-b.y);
      lastMid  = {x:(a.x+b.x)/2, y:(a.y+b.y)/2};
    }
  });

  cv.addEventListener('pointermove', e=>{
    if(!pointers.has(e.pointerId)) return;
    const prev = pointers.get(e.pointerId);
    pointers.set(e.pointerId, {x:e.clientX, y:e.clientY});
    const W = cv.clientWidth;
    if(pointers.size === 1){
      state.cx += (e.clientX - prev.x)/W;
      state.cy += (e.clientY - prev.y)/W;
      clamp(); render();
    } else if(pointers.size === 2){
      const [a,b] = [...pointers.values()];
      const dist = Math.hypot(a.x-b.x, a.y-b.y);
      const mid  = {x:(a.x+b.x)/2, y:(a.y+b.y)/2};
      const rect = cv.getBoundingClientRect();
      const px = (mid.x-rect.left)/W, py = (mid.y-rect.top)/W;
      if(lastDist > 0) zoomAbout(dist/lastDist, px, py);
      if(lastMid){
        state.cx += (mid.x-lastMid.x)/W;
        state.cy += (mid.y-lastMid.y)/W;
        clamp(); render();
      }
      lastDist = dist; lastMid = mid;
    }
  });

  function endPointer(e){
    pointers.delete(e.pointerId);
    if(pointers.size < 2){ lastDist = 0; lastMid = null; }
    if(pointers.size === 0) cv.classList.remove('dragging');
  }
  cv.addEventListener('pointerup', endPointer);
  cv.addEventListener('pointercancel', endPointer);

  cv.addEventListener('wheel', e=>{
    e.preventDefault();
    const rect = cv.getBoundingClientRect();
    const W = cv.clientWidth;
    const px = (e.clientX-rect.left)/W, py = (e.clientY-rect.top)/W;
    zoomAbout(e.deltaY < 0 ? 1.08 : 1/1.08, px, py);
  }, {passive:false});

  /* ---------- Exportación JPEG con DPI real ---------- */
  function setJpegDpi(buf, dpi){
    const d = new Uint8Array(buf);
    if(d[0]!==0xFF || d[1]!==0xD8) return d;                 // no es JPEG
    // ¿APP0 JFIF justo después de SOI?
    if(d[2]===0xFF && d[3]===0xE0 &&
       d[6]===0x4A && d[7]===0x46 && d[8]===0x49 && d[9]===0x46 && d[10]===0x00){
      d[13]=1;                                                // unidades = ppp (dpi)
      d[14]=dpi>>8; d[15]=dpi&255;                            // densidad X
      d[16]=dpi>>8; d[17]=dpi&255;                            // densidad Y
      return d;
    }
    // insertar segmento APP0 JFIF tras SOI
    const seg = new Uint8Array([0xFF,0xE0,0x00,0x10,0x4A,0x46,0x49,0x46,0x00,
                                0x01,0x01,0x01,dpi>>8,dpi&255,dpi>>8,dpi&255,0x00,0x00]);
    const out = new Uint8Array(d.length + seg.length);
    out.set(d.subarray(0,2),0); out.set(seg,2); out.set(d.subarray(2), 2+seg.length);
    return out;
  }

  /* ================== VERIFICACIÓN AUTOMÁTICA ==================
     1) Fondo: promedio RGB de la mitad superior FUERA del óvalo guía.
     2) Uniformidad: desviación estándar de la luminancia de esa zona.
     3) Cobertura: comprobación geométrica exacta de que la foto rotada
        cubre las 4 esquinas del marco (sin bandas blancas).
     4) Nitidez: varianza del Laplaciano (detección de desenfoque).   */

  function frameFullyCovered(){
    // Transforma las 4 esquinas del marco al sistema de coordenadas de la
    // imagen original. Si alguna cae fuera del rectángulo de la imagen,
    // hay zonas blancas sin cubrir. Exacto incluso con rotación.
    const s  = baseScale()*state.z;
    const th = state.rot*Math.PI/180;
    const cos = Math.cos(-th), sin = Math.sin(-th);
    const corners = [[0,0],[1,0],[0,RATIO],[1,RATIO]];
    for(const [px,py] of corners){
      const dx = px - state.cx, dy = py - state.cy;
      const qx = (dx*cos - dy*sin)/s;
      const qy = (dx*sin + dy*cos)/s;
      if(Math.abs(qx) > state.natW/2 + 0.5 || Math.abs(qy) > state.natH/2 + 0.5)
        return false;
    }
    return true;
  }

  function analyze(ctx, W, H){
    const data = ctx.getImageData(0,0,W,H).data;

    // --- Fondo: mitad superior, excluyendo el interior del óvalo guía ---
    const ocx = 17.5/MM_W*W, ocy = 22/MM_H*H;
    const orx = 12/MM_W*W,  ory = 17/MM_H*H;
    let n=0, r=0, g=0, b=0, sumL=0, sumL2=0;
    const step = 2;
    for(let y=0; y<H/2; y+=step){
      for(let x=0; x<W; x+=step){
        const ex=(x-ocx)/orx, ey=(y-ocy)/ory;
        if(ex*ex + ey*ey <= 1) continue;          // dentro del óvalo → cabeza
        const i=(y*W+x)*4;
        const R=data[i], G=data[i+1], B=data[i+2];
        const L=0.2126*R + 0.7152*G + 0.0722*B;
        r+=R; g+=G; b+=B; sumL+=L; sumL2+=L*L; n++;
      }
    }
    const mr=Math.round(r/n), mg=Math.round(g/n), mb=Math.round(b/n);
    const mL=sumL/n;
    const sd=Math.sqrt(Math.max(0, sumL2/n - mL*mL));

    // --- Nitidez: varianza del Laplaciano sobre versión reducida a 200 px ---
    const sw=200, sh=Math.round(sw*RATIO);
    const sc=document.createElement('canvas'); sc.width=sw; sc.height=sh;
    const sctx=sc.getContext('2d');
    sctx.drawImage(ctx.canvas, 0, 0, sw, sh);
    const sdat=sctx.getImageData(0,0,sw,sh).data;
    const lum=new Float32Array(sw*sh);
    for(let i=0;i<sw*sh;i++)
      lum[i]=0.2126*sdat[i*4] + 0.7152*sdat[i*4+1] + 0.0722*sdat[i*4+2];
    let ls=0, ls2=0, ln=0;
    for(let y=1;y<sh-1;y++){
      for(let x=1;x<sw-1;x++){
        const i=y*sw+x;
        const v = 4*lum[i] - lum[i-1] - lum[i+1] - lum[i-sw] - lum[i+sw];
        ls+=v; ls2+=v*v; ln++;
      }
    }
    const lapVar = ls2/ln - (ls/ln)*(ls/ln);

    return {mr, mg, mb, mL, sd, lapVar, covered: frameFullyCovered()};
  }

  function row(status, txt){
    const cls  = status==='ok' ? 'check-ok' : status==='warn' ? 'check-warn' : 'check-err';
    const icon = status==='ok' ? '✓' : status==='warn' ? '⚠' : '✗';
    return '<div class="'+cls+'" style="margin-top:5px">'+icon+' '+txt+'</div>';
  }

  function renderReport(a){
    const sw = '<span style="display:inline-block;width:13px;height:13px;border:1px solid #999;'+
               'border-radius:3px;vertical-align:-2px;margin-right:2px;background:rgb('+
               a.mr+','+a.mg+','+a.mb+')"></span>';
    let html = '<div style="font-size:.78rem;color:var(--muted);text-transform:uppercase;'+
               'letter-spacing:.1em;margin-bottom:2px">Verificación automática</div>';

    // 1) Color medio del fondo
    if(a.mL > 242)
      html += row('err', sw+' Fondo casi blanco (L='+a.mL.toFixed(0)+') — ANTS no acepta fondo blanco.');
    else if(a.mL > 150)
      html += row('ok', sw+' Fondo claro (luminancia media '+a.mL.toFixed(0)+'/255).');
    else if(a.mL > 110)
      html += row('warn', sw+' Fondo algo oscuro (L='+a.mL.toFixed(0)+') — preferible gris/azul más claro.');
    else
      html += row('err', sw+' Fondo oscuro (L='+a.mL.toFixed(0)+') — usa un fondo claro.');

    // 2) Uniformidad (desviación estándar)
    if(a.sd <= 20)
      html += row('ok', 'Fondo uniforme (σ='+a.sd.toFixed(1)+') — sin mezclas de claros y oscuros.');
    else if(a.sd <= 40)
      html += row('warn', 'Variación moderada (σ='+a.sd.toFixed(1)+') — puede haber sombras, textura o pelo invadiendo el fondo.');
    else
      html += row('err', 'Fondo no uniforme (σ='+a.sd.toFixed(1)+') — hay zonas muy claras y muy oscuras mezcladas (objetos, sombras fuertes o el encuadre incluye cosas que no son fondo).');

    // 3) Cobertura del marco (bandas blancas por rotación/zoom)
    if(a.covered)
      html += row('ok', 'La foto cubre todo el marco — sin bandas blancas en los bordes.');
    else
      html += row('err', 'La rotación o el encuadre dejó zonas sin imagen (bandas blancas en bordes/esquinas). Aumenta el zoom o reduce la rotación.');

    // 4) Nitidez (varianza del Laplaciano)
    if(a.lapVar >= 80)
      html += row('ok', 'Imagen nítida (Laplaciano='+a.lapVar.toFixed(0)+').');
    else if(a.lapVar >= 30)
      html += row('warn', 'Nitidez justa (Laplaciano='+a.lapVar.toFixed(0)+') — revisa que la cara esté bien enfocada.');
    else
      html += row('err', 'Imagen probablemente borrosa (Laplaciano='+a.lapVar.toFixed(0)+') — vuelve a tomar la foto con mejor enfoque o más luz.');

    html += '<div class="hint" style="margin-top:6px">Umbrales orientativos: el veredicto final '+
            'siempre lo da la revisión visual y la administración.</div>';
    document.getElementById('bgCheck').innerHTML = html;
  }

  document.getElementById('exportBtn').addEventListener('click', ()=>{
    if(!state.img){ alert('Primero carga una foto.'); return; }
    const dpi = parseInt(document.getElementById('dpiSel').value, 10);
    const W = Math.round(MM_W/25.4*dpi);   // 413 ó 827
    const H = Math.round(MM_H/25.4*dpi);   // 531 ó 1063
    const c = document.createElement('canvas');
    c.width = W; c.height = H;
    const ctx = c.getContext('2d', {willReadFrequently:true});
    draw(ctx, W);
    renderReport(analyze(ctx, W, H));
    c.toBlob(blob=>{
      blob.arrayBuffer().then(buf=>{
        const patched = setJpegDpi(buf, dpi);
        const out = new Blob([patched], {type:'image/jpeg'});
        const url = URL.createObjectURL(out);
        const link = document.getElementById('downloadLink');
        link.href = url;
        link.download = 'ephoto-ants-35x45-'+dpi+'dpi.jpg';
        document.getElementById('resultImg').src = url;
        const kb = (out.size/1024).toFixed(0);
        document.getElementById('resultMeta').innerHTML =
          '<b>'+W+' × '+H+' px</b> · '+dpi+' dpi grabados en el archivo · '+
          '= <b>3,5 × 4,5 cm</b> físicos · '+kb+' KB · JPEG';
        document.getElementById('result').style.display = 'block';
        document.getElementById('result').scrollIntoView({behavior:'smooth', block:'nearest'});
      });
    }, 'image/jpeg', 0.92);
  });

  /* ---------- Checklist: tachar al marcar ---------- */
  document.getElementById('checklist').addEventListener('change', e=>{
    if(e.target.type==='checkbox')
      e.target.closest('li').classList.toggle('done', e.target.checked);
  });

  layoutFrame();
})();
</script>
</body>
</html>