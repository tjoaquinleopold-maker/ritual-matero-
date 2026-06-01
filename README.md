# ritual-matero-<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0"/>
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>
<meta name="apple-mobile-web-app-title" content="Ritual Matero"/>
<meta name="theme-color" content="#1a0a00"/>
<title>Ritual Matero — Control</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Lato:wght@300;400;700&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #100700;
    --bg2: #1e0d00;
    --bg3: #2d1600;
    --accent: #c8860a;
    --accent2: #f5c842;
    --text: #f0e0c8;
    --muted: #9a7050;
    --border: #3a2010;
    --green: #5dba60;
    --red: #d96060;
    --card: rgba(255,255,255,0.03);
  }
  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Lato', sans-serif;
    min-height: 100vh;
    max-width: 480px;
    margin: 0 auto;
  }

  /* HEADER */
  .header {
    background: linear-gradient(135deg, #1e0d00, #3d1f00);
    padding: 14px 18px;
    border-bottom: 1px solid var(--accent);
    display: flex;
    align-items: center;
    gap: 12px;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .header-logo { font-size: 26px; }
  .header-title { font-family: 'Playfair Display', serif; font-size: 17px; color: var(--accent2); }
  .header-sub { font-size: 10px; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; }
  .header-stats { margin-left: auto; display: flex; gap: 8px; }
  .stat-chip {
    background: rgba(0,0,0,0.3);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 5px 10px;
    text-align: center;
  }
  .stat-chip .label { font-size: 9px; color: var(--muted); letter-spacing: 1px; }
  .stat-chip .value { font-size: 13px; font-weight: 700; }

  /* TABS */
  .tabs {
    display: flex;
    background: var(--bg2);
    border-bottom: 1px solid var(--border);
    position: sticky;
    top: 68px;
    z-index: 99;
  }
  .tab-btn {
    flex: 1;
    padding: 11px 4px;
    background: none;
    border: none;
    border-bottom: 2px solid transparent;
    color: var(--muted);
    font-size: 12px;
    font-family: 'Lato', sans-serif;
    cursor: pointer;
    transition: all 0.2s;
  }
  .tab-btn.active {
    color: var(--accent2);
    border-bottom-color: var(--accent2);
    background: rgba(200,134,10,0.06);
  }

  /* MAIN */
  .main { padding: 16px; }

  /* MODE TOGGLE */
  .mode-toggle { display: flex; gap: 8px; margin-bottom: 16px; }
  .mode-btn {
    flex: 1; padding: 10px 8px; border-radius: 10px;
    border: 1px solid var(--border);
    background: var(--card);
    color: var(--muted);
    font-size: 13px;
    font-family: 'Lato', sans-serif;
    cursor: pointer;
    transition: all 0.2s;
  }
  .mode-btn.active {
    background: var(--accent);
    border-color: var(--accent2);
    color: #1a0a00;
    font-weight: 700;
  }

  /* NATURAL INPUT */
  .natural-hint {
    font-size: 12px;
    color: var(--muted);
    margin-bottom: 8px;
    line-height: 1.6;
  }
  .natural-hint em { color: #7a5a30; font-style: italic; }
  textarea {
    width: 100%;
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px;
    color: var(--text);
    font-size: 14px;
    font-family: 'Lato', sans-serif;
    resize: vertical;
    outline: none;
    transition: border-color 0.2s;
  }
  textarea:focus { border-color: var(--accent); }

  /* FORM */
  .field { margin-bottom: 12px; }
  .field label {
    display: block;
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 1.5px;
    text-transform: uppercase;
    margin-bottom: 5px;
  }
  input[type="text"], input[type="number"], input[type="date"], select {
    width: 100%;
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 11px 14px;
    color: var(--text);
    font-size: 14px;
    font-family: 'Lato', sans-serif;
    outline: none;
    transition: border-color 0.2s;
    -webkit-appearance: none;
  }
  input:focus, select:focus { border-color: var(--accent); }
  select option { background: #1e0d00; }

  /* TIPO TOGGLE */
  .tipo-toggle { display: flex; gap: 8px; margin-bottom: 14px; }
  .tipo-btn {
    flex: 1; padding: 11px; border-radius: 10px;
    border: 1px solid var(--border);
    background: var(--card);
    color: var(--muted);
    font-size: 14px;
    font-family: 'Lato', sans-serif;
    cursor: pointer;
    font-weight: 700;
    transition: all 0.2s;
  }
  .tipo-btn.venta.active { background: rgba(93,186,96,0.15); border-color: var(--green); color: var(--green); }
  .tipo-btn.compra.active { background: rgba(217,96,96,0.15); border-color: var(--red); color: var(--red); }

  /* CATEGORIAS */
  .cats { display: flex; flex-wrap: wrap; gap: 6px; }
  .cat-btn {
    padding: 6px 13px; border-radius: 20px;
    border: 1px solid var(--border);
    background: var(--card);
    color: var(--muted);
    font-size: 12px;
    font-family: 'Lato', sans-serif;
    cursor: pointer;
    transition: all 0.2s;
  }
  .cat-btn.active { background: var(--bg3); border-color: var(--accent); color: var(--accent2); }

  /* BUTTONS */
  .btn-primary {
    width: 100%; padding: 14px; border-radius: 12px;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    border: none;
    color: #1a0a00;
    font-size: 15px;
    font-weight: 700;
    font-family: 'Playfair Display', serif;
    cursor: pointer;
    letter-spacing: 0.5px;
    box-shadow: 0 4px 20px rgba(200,134,10,0.25);
    transition: all 0.2s;
    margin-top: 8px;
  }
  .btn-primary:disabled { background: var(--border); color: var(--muted); box-shadow: none; cursor: not-allowed; }
  .btn-primary:not(:disabled):active { transform: scale(0.98); }

  .btn-secondary {
    width: 100%; padding: 13px; border-radius: 12px;
    background: rgba(255,255,255,0.05);
    border: 1px solid var(--border);
    color: var(--text);
    font-size: 14px;
    font-family: 'Lato', sans-serif;
    cursor: pointer;
    transition: all 0.2s;
    margin-top: 8px;
  }
  .btn-secondary:active { background: rgba(255,255,255,0.1); }

  .btn-blue {
    width: 100%; padding: 14px; border-radius: 12px;
    background: linear-gradient(135deg, #1a3a6b, #2a5ab0);
    border: none;
    color: var(--text);
    font-size: 15px;
    font-weight: 700;
    font-family: 'Lato', sans-serif;
    cursor: pointer;
    transition: all 0.2s;
    margin-top: 4px;
  }
  .btn-blue:disabled { opacity: 0.5; cursor: not-allowed; }

  /* STATUS */
  .status {
    padding: 11px 14px;
    border-radius: 10px;
    font-size: 13px;
    margin-top: 10px;
    line-height: 1.5;
  }
  .status.ok { background: rgba(93,186,96,0.1); border: 1px solid var(--green); color: var(--green); }
  .status.error { background: rgba(217,96,96,0.1); border: 1px solid var(--red); color: var(--red); }
  .status.info { background: rgba(200,134,10,0.1); border: 1px solid var(--accent); color: var(--accent2); }

  /* HISTORIAL */
  .filters { display: flex; gap: 8px; margin-bottom: 14px; }
  .filters select { flex: 1; }

  .registro-card {
    background: var(--card);
    border-radius: 10px;
    padding: 12px 14px;
    margin-bottom: 8px;
    border-left: 3px solid var(--border);
    border-top: 1px solid var(--border);
    border-right: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
  }
  .registro-card.venta { border-left-color: var(--green); }
  .registro-card.compra { border-left-color: var(--red); }
  .reg-nombre { font-size: 14px; font-weight: 700; color: var(--text); margin-bottom: 3px; }
  .reg-meta { font-size: 11px; color: var(--muted); }
  .reg-precio { font-size: 15px; font-weight: 700; text-align: right; }
  .reg-tipo { font-size: 10px; color: var(--muted); text-align: right; text-transform: uppercase; }
  .empty { text-align: center; color: var(--muted); padding: 40px 0; font-size: 14px; line-height: 2; }

  /* BACKUP */
  .backup-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 22px;
    text-align: center;
    margin-bottom: 14px;
  }
  .backup-icon { font-size: 36px; margin-bottom: 10px; }
  .backup-title { font-family: 'Playfair Display', serif; font-size: 17px; color: var(--accent2); margin-bottom: 6px; }
  .backup-desc { font-size: 13px; color: var(--muted); line-height: 1.6; margin-bottom: 14px; }
  .backup-last { font-size: 12px; color: var(--muted); margin-bottom: 10px; }

  .summary-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 16px;
  }
  .summary-title { font-size: 13px; color: var(--accent2); font-weight: 700; margin-bottom: 10px; }
  .summary-row { font-size: 13px; color: var(--muted); margin-bottom: 5px; }
  .summary-row strong { color: var(--text); }

  /* SPINNER */
  @keyframes spin { to { transform: rotate(360deg); } }
  .spinner {
    display: inline-block;
    width: 14px; height: 14px;
    border: 2px solid rgba(255,255,255,0.2);
    border-top-color: var(--text);
    border-radius: 50%;
    animation: spin 0.7s linear infinite;
    vertical-align: middle;
    margin-right: 6px;
  }

  /* FADE IN */
  @keyframes fadeIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: none; } }
  .fade-in { animation: fadeIn 0.3s ease; }
</style>
</head>
<body>

<!-- HEADER -->
<div class="header">
  <div class="header-logo">🧉</div>
  <div>
    <div class="header-title">Ritual Matero</div>
    <div class="header-sub">Control de emprendimiento</div>
  </div>
  <div class="header-stats">
    <div class="stat-chip">
      <div class="label">VENTAS</div>
      <div class="value" id="stat-ventas" style="color:#5dba60">$0</div>
    </div>
    <div class="stat-chip">
      <div class="label">COMPRAS</div>
      <div class="value" id="stat-compras" style="color:#d96060">$0</div>
    </div>
  </div>
</div>

<!-- TABS -->
<div class="tabs">
  <button class="tab-btn active" onclick="showTab('registrar')">📝 Registrar</button>
  <button class="tab-btn" onclick="showTab('historial')">📋 Historial</button>
  <button class="tab-btn" onclick="showTab('backup')">💾 Backup</button>
</div>

<!-- MAIN -->
<div class="main">

  <!-- TAB REGISTRAR -->
  <div id="tab-registrar" class="fade-in">
    <div class="mode-toggle">
      <button class="mode-btn active" id="btn-natural" onclick="setModo('natural')">💬 Lenguaje natural</button>
      <button class="mode-btn" id="btn-formulario" onclick="setModo('formulario')">📋 Formulario</button>
    </div>

    <!-- NATURAL -->
    <div id="panel-natural">
      <div class="natural-hint">
        Escribí como le hablarías a alguien:<br>
        <em>"vendí 1 kg de canarias a Alfarano hoy $11000"</em><br>
        <em>"compré 2 imperiales crocco a Mateados el 8/5 $38000"</em>
      </div>
      <textarea id="natural-input" rows="3" placeholder="Escribí la venta o compra acá..."></textarea>
      <button class="btn-primary" id="btn-interpretar" onclick="interpretar()">🔍 Interpretar</button>
    </div>

    <!-- FORMULARIO -->
    <div id="panel-formulario" style="display:none;">
      <div class="tipo-toggle">
        <button class="tipo-btn venta active" id="tipo-venta" onclick="setTipo('venta')">📈 Venta</button>
        <button class="tipo-btn compra" id="tipo-compra" onclick="setTipo('compra')">📦 Compra</button>
      </div>

      <div class="field">
        <label>Fecha</label>
        <input type="text" id="f-fecha" placeholder="DD/MM/YYYY"/>
      </div>
      <div class="field">
        <label>Producto</label>
        <input type="text" id="f-producto" placeholder="Ej: Mate imperial algarrobo"/>
      </div>
      <div class="field">
        <label>Categoría</label>
        <div class="cats" id="cats-container"></div>
      </div>
      <div style="display:flex;gap:8px;">
        <div class="field" style="flex:1">
          <label>Cantidad</label>
          <input type="number" id="f-cantidad" value="1" min="1"/>
        </div>
        <div class="field" style="flex:2">
          <label id="precio-label">Precio unitario ($)</label>
          <input type="number" id="f-precio" placeholder="Ej: 11000"/>
        </div>
      </div>
      <div class="field">
        <label>Notas / Cliente</label>
        <input type="text" id="f-notas" placeholder="Ej: Alfarano, regalo, etc."/>
      </div>
      <div class="field" id="field-proveedor" style="display:none;">
        <label>Proveedor</label>
        <input type="text" id="f-proveedor" placeholder="Ej: Mateados, MateCo"/>
      </div>

      <div id="form-status"></div>
      <button class="btn-primary" id="btn-guardar" onclick="guardar()">✅ Guardar</button>
    </div>
  </div>

  <!-- TAB HISTORIAL -->
  <div id="tab-historial" style="display:none;" class="fade-in">
    <div class="filters">
      <select id="filtro-tipo" onchange="renderHistorial()">
        <option value="todos">Todos</option>
        <option value="venta">Ventas</option>
        <option value="compra">Compras</option>
      </select>
      <select id="filtro-cat" onchange="renderHistorial()">
        <option value="todas">Todas las categorías</option>
      </select>
    </div>
    <div id="historial-list"></div>
  </div>

  <!-- TAB BACKUP -->
  <div id="tab-backup" style="display:none;" class="fade-in">
    <div class="backup-card">
      <div class="backup-icon">💾</div>
      <div class="backup-title">Backup semanal</div>
      <div class="backup-desc">
        Descargá una copia de todos tus registros locales como archivo JSON.<br>
        Guardala en tu Drive o en el celu. Recomendado: 1 vez por semana.
      </div>
      <div class="backup-last" id="backup-last"></div>
      <div id="backup-status"></div>
      <button class="btn-blue" onclick="hacerBackup()">📁 Descargar backup ahora</button>
    </div>
    <div class="summary-card">
      <div class="summary-title">📊 Resumen local</div>
      <div id="summary-content"></div>
    </div>
  </div>

</div>

<script>
// ─── ESTADO GLOBAL ────────────────────────────────────────
const STORAGE_KEY = 'ritualmatero_registros';
const BACKUP_DATE_KEY = 'ritualmatero_backup';
const CLAUDE_KEY = ''; // La app usa la API de Anthropic vía proxy de Claude.ai

const CATEGORIAS = ['Mate','Mates + bombilla','Bombilla','Yerba','Accesorio','Combo','Termo','Otro'];

let estado = {
  tipo: 'venta',
  modo: 'natural',
  categoria: '',
};

let registros = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');

// ─── INIT ──────────────────────────────────────────────────
window.onload = () => {
  // Setear fecha de hoy
  const hoy = new Date();
  const dd = String(hoy.getDate()).padStart(2,'0');
  const mm = String(hoy.getMonth()+1).padStart(2,'0');
  const yyyy = hoy.getFullYear();
  document.getElementById('f-fecha').value = `${dd}/${mm}/${yyyy}`;

  // Render categorías
  const cont = document.getElementById('cats-container');
  CATEGORIAS.forEach(cat => {
    const btn = document.createElement('button');
    btn.className = 'cat-btn';
    btn.textContent = cat;
    btn.onclick = () => selCat(cat);
    btn.id = `cat-${cat}`;
    cont.appendChild(btn);
  });

  // Filtro categorías en historial
  const sel = document.getElementById('filtro-cat');
  CATEGORIAS.forEach(cat => {
    const opt = document.createElement('option');
    opt.value = cat; opt.textContent = cat;
    sel.appendChild(opt);
  });

  actualizarStats();
  renderBackupSummary();
};

// ─── TABS ──────────────────────────────────────────────────
function showTab(tab) {
  ['registrar','historial','backup'].forEach(t => {
    document.getElementById(`tab-${t}`).style.display = t === tab ? 'block' : 'none';
  });
  document.querySelectorAll('.tab-btn').forEach((btn, i) => {
    btn.classList.toggle('active', ['registrar','historial','backup'][i] === tab);
  });
  if (tab === 'historial') renderHistorial();
  if (tab === 'backup') renderBackupSummary();
}

// ─── MODO ──────────────────────────────────────────────────
function setModo(modo) {
  estado.modo = modo;
  document.getElementById('panel-natural').style.display = modo === 'natural' ? 'block' : 'none';
  document.getElementById('panel-formulario').style.display = modo === 'formulario' ? 'block' : 'none';
  document.getElementById('btn-natural').classList.toggle('active', modo === 'natural');
  document.getElementById('btn-formulario').classList.toggle('active', modo === 'formulario');
}

// ─── TIPO ──────────────────────────────────────────────────
function setTipo(tipo) {
  estado.tipo = tipo;
  document.getElementById('tipo-venta').classList.toggle('active', tipo === 'venta');
  document.getElementById('tipo-compra').classList.toggle('active', tipo === 'compra');
  document.getElementById('field-proveedor').style.display = tipo === 'compra' ? 'block' : 'none';
  document.getElementById('precio-label').textContent = tipo === 'venta' ? 'Precio unitario ($)' : 'Costo total ($)';
}

// ─── CATEGORÍAS ────────────────────────────────────────────
function selCat(cat) {
  estado.categoria = cat;
  CATEGORIAS.forEach(c => {
    document.getElementById(`cat-${c}`)?.classList.toggle('active', c === cat);
  });
}

// ─── INTERPRETAR LENGUAJE NATURAL ─────────────────────────
async function interpretar() {
  const texto = document.getElementById('natural-input').value.trim();
  if (!texto) return;

  const btn = document.getElementById('btn-interpretar');
  btn.disabled = true;
  btn.innerHTML = '<span class="spinner"></span>Interpretando...';

  try {
    const hoy = new Date();
    const dd = String(hoy.getDate()).padStart(2,'0');
    const mm = String(hoy.getMonth()+1).padStart(2,'0');
    const yyyy = hoy.getFullYear();
    const fechaHoy = `${dd}/${mm}/${yyyy}`;

    const res = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 500,
        system: `Extraé datos de un registro de venta/compra escrito en español rioplatense informal.
Devolvé SOLO un JSON válido sin backticks ni texto extra con estos campos:
{
  "tipo": "venta" o "compra",
  "fecha": "DD/MM/YYYY",
  "producto": "nombre del producto",
  "categoria": una de exactamente: Mate, Mates + bombilla, Bombilla, Yerba, Accesorio, Combo, Termo, Otro,
  "cantidad": número entero,
  "precio": número sin símbolo ni puntos (ej: 11000),
  "notas": "cliente u otras notas",
  "proveedor": "nombre del proveedor si es compra, sino vacío"
}
Si no hay fecha usa: ${fechaHoy}`,
        messages: [{ role: 'user', content: texto }]
      })
    });

    const data = await res.json();
    const raw = data.content?.[0]?.text || '';
    const clean = raw.replace(/```json|```/g,'').trim();
    const parsed = JSON.parse(clean);

    // Llenar formulario
    setModo('formulario');
    setTipo(parsed.tipo || 'venta');
    document.getElementById('f-fecha').value = parsed.fecha || fechaHoy;
    document.getElementById('f-producto').value = parsed.producto || '';
    document.getElementById('f-cantidad').value = parsed.cantidad || 1;
    document.getElementById('f-precio').value = parsed.precio || '';
    document.getElementById('f-notas').value = parsed.notas || '';
    document.getElementById('f-proveedor').value = parsed.proveedor || '';
    if (parsed.categoria) selCat(parsed.categoria);

    setStatus('form-status', 'info', '✅ Datos detectados. Revisá y tocá Guardar.');

  } catch(e) {
    setStatus('form-status', 'error', '❌ No pude interpretar. Usá el formulario directo.');
    setModo('formulario');
  }

  btn.disabled = false;
  btn.innerHTML = '🔍 Interpretar';
}

// ─── GUARDAR ───────────────────────────────────────────────
async function guardar() {
  const producto = document.getElementById('f-producto').value.trim();
  const precio = document.getElementById('f-precio').value.trim();
  const fecha = document.getElementById('f-fecha').value.trim();

  if (!producto || !precio || !estado.categoria) {
    setStatus('form-status', 'error', 'Completá producto, categoría y precio.');
    return;
  }

  const btn = document.getElementById('btn-guardar');
  btn.disabled = true;
  btn.innerHTML = '<span class="spinner"></span>Guardando...';

  const registro = {
    tipo: estado.tipo,
    fecha,
    producto,
    categoria: estado.categoria,
    cantidad: parseInt(document.getElementById('f-cantidad').value) || 1,
    precio: parseInt(precio),
    notas: document.getElementById('f-notas').value.trim(),
    proveedor: document.getElementById('f-proveedor').value.trim(),
    timestamp: new Date().toISOString(),
    id: Date.now(),
  };

  // Guardar localmente primero (siempre)
  registros.unshift(registro);
  localStorage.setItem(STORAGE_KEY, JSON.stringify(registros));
  actualizarStats();

  // Intentar guardar en Drive via Claude API
  let driveOk = false;
  try {
    const hoja = registro.tipo === 'venta' ? '📦 Ventas' : '🛒 Compras de Stock';
    const res = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 500,
        system: `Agregá una fila al archivo de Google Drive ID: 1raUfbpIiJ8siMxDG8tjHlIRPXkbOdSOM en la hoja "${hoja}".
La fila tiene estos campos en orden: Fecha, Producto, Categoría, Cantidad, Precio, Notas.
Después de agregar respondé SOLO con JSON: {"success":true} o {"success":false,"error":"msg"}`,
        messages: [{
          role: 'user',
          content: `Fecha: ${registro.fecha}\nProducto: ${registro.producto}\nCategoría: ${registro.categoria}\nCantidad: ${registro.cantidad}\nPrecio: $${registro.precio.toLocaleString('es-AR')}\nNotas: ${registro.notas}${registro.proveedor ? ' | Proveedor: '+registro.proveedor : ''}`
        }],
        mcp_servers: [{ type: 'url', url: 'https://drivemcp.googleapis.com/mcp/v1', name: 'gdrive' }]
      })
    });
    const data = await res.json();
    const txt = (data.content?.filter(i=>i.type==='text')||[]).map(i=>i.text).join('');
    const result = JSON.parse(txt.replace(/```json|```/g,'').trim());
    driveOk = result.success;
  } catch(e) {
    driveOk = false;
  }

  if (driveOk) {
    setStatus('form-status', 'ok', `✅ ${registro.tipo === 'venta' ? 'Venta' : 'Compra'} guardada en Drive y localmente.`);
  } else {
    setStatus('form-status', 'info', `✅ Guardado localmente. Se sincronizará con Drive la próxima vez.`);
  }

  // Limpiar
  document.getElementById('f-producto').value = '';
  document.getElementById('f-precio').value = '';
  document.getElementById('f-notas').value = '';
  document.getElementById('f-proveedor').value = '';
  document.getElementById('f-cantidad').value = '1';
  estado.categoria = '';
  CATEGORIAS.forEach(c => document.getElementById(`cat-${c}`)?.classList.remove('active'));

  btn.disabled = false;
  btn.innerHTML = '✅ Guardar';
}

// ─── HISTORIAL ─────────────────────────────────────────────
function renderHistorial() {
  const tipo = document.getElementById('filtro-tipo').value;
  const cat = document.getElementById('filtro-cat').value;
  const lista = document.getElementById('historial-list');

  const filtrados = registros.filter(r => {
    if (tipo !== 'todos' && r.tipo !== tipo) return false;
    if (cat !== 'todas' && r.categoria !== cat) return false;
    return true;
  });

  if (!filtrados.length) {
    lista.innerHTML = '<div class="empty">Sin registros todavía.<br><small>Los registros aparecen acá al guardar.</small></div>';
    return;
  }

  lista.innerHTML = filtrados.map(r => {
    const total = (r.precio || 0) * (r.cantidad || 1);
    const signo = r.tipo === 'venta' ? '+' : '-';
    const color = r.tipo === 'venta' ? 'var(--green)' : 'var(--red)';
    return `
      <div class="registro-card ${r.tipo}">
        <div>
          <div class="reg-nombre">${r.producto}</div>
          <div class="reg-meta">${r.categoria} · ${r.fecha} · x${r.cantidad}${r.notas ? ' · '+r.notas : ''}</div>
        </div>
        <div>
          <div class="reg-precio" style="color:${color}">${signo}$${total.toLocaleString('es-AR')}</div>
          <div class="reg-tipo">${r.tipo}</div>
        </div>
      </div>`;
  }).join('');
}

// ─── STATS ────────────────────────────────────────────────
function actualizarStats() {
  const ventas = registros.filter(r=>r.tipo==='venta').reduce((s,r)=>s+(r.precio||0)*(r.cantidad||1),0);
  const compras = registros.filter(r=>r.tipo==='compra').reduce((s,r)=>s+(r.precio||0)*(r.cantidad||1),0);
  document.getElementById('stat-ventas').textContent = '$'+ventas.toLocaleString('es-AR');
  document.getElementById('stat-compras').textContent = '$'+compras.toLocaleString('es-AR');
}

// ─── BACKUP ───────────────────────────────────────────────
function hacerBackup() {
  const fecha = new Date().toLocaleDateString('es-AR');
  const nombre = `ritual-matero-backup-${fecha.replace(/\//g,'-')}.json`;
  const blob = new Blob([JSON.stringify({ fecha, registros }, null, 2)], { type: 'application/json' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url; a.download = nombre; a.click();
  URL.revokeObjectURL(url);
  localStorage.setItem(BACKUP_DATE_KEY, fecha);
  document.getElementById('backup-last').textContent = `Último backup: ${fecha}`;
  setStatus('backup-status', 'ok', '✅ Backup descargado. Guardalo en Drive o en el celu.');
}

function renderBackupSummary() {
  const ultima = localStorage.getItem(BACKUP_DATE_KEY);
  if (ultima) document.getElementById('backup-last').textContent = `Último backup: ${ultima}`;
  const ventas = registros.filter(r=>r.tipo==='venta').length;
  const compras = registros.filter(r=>r.tipo==='compra').length;
  document.getElementById('summary-content').innerHTML = `
    <div class="summary-row">Registros totales: <strong>${registros.length}</strong></div>
    <div class="summary-row">Ventas: <strong style="color:var(--green)">${ventas}</strong> · Compras: <strong style="color:var(--red)">${compras}</strong></div>
  `;
}

// ─── HELPERS ──────────────────────────────────────────────
function setStatus(id, tipo, msg) {
  const el = document.getElementById(id);
  if (!el) return;
  el.className = `status ${tipo}`;
  el.textContent = msg;
  el.style.display = 'block';
}
</script>
</body>
</html>
