<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TYPING TEXT - Prueba IES Ricardo Marín</title>
<style>
  /* ===== RESET Y ESTILOS BASE ===== */
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Segoe UI', 'Helvetica Neue', Arial, sans-serif;
    background: #f4f6f8;
    color: #1f2933;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px 16px 40px;
    font-size: 20px;
    line-height: 1.6;
  }

  /* ===== CABECERA ===== */
  header {
    width: 100%;
    max-width: 960px;
    text-align: center;
    margin-bottom: 24px;
  }

  header h1 {
    font-size: 1.8rem;
    color: #1f3a93;
    letter-spacing: 0.5px;
    font-weight: 700;
  }

  /* ===== TARJETA CONTENEDOR ===== */
  .card {
    background: #ffffff;
    border-radius: 14px;
    box-shadow: 0 4px 16px rgba(0,0,0,0.08);
    padding: 28px 32px;
    width: 100%;
    max-width: 960px;
    margin-bottom: 20px;
  }

  /* ===== FORMULARIO INICIAL ===== */
  .form-group {
    margin-bottom: 20px;
  }

  label {
    display: block;
    font-weight: 600;
    margin-bottom: 6px;
    color: #1f3a93;
  }

  input[type="text"], select {
    width: 100%;
    padding: 12px 14px;
    font-size: 20px;
    border: 2px solid #cbd2d9;
    border-radius: 8px;
    background: #fff;
    transition: border-color 0.2s;
    font-family: inherit;
  }

  input[type="text"]:focus, select:focus {
    outline: none;
    border-color: #1f3a93;
  }

  .hint {
    font-size: 0.85rem;
    color: #616e7c;
    margin-top: 6px;
  }

  .error {
    color: #c53030;
    font-size: 0.9rem;
    margin-top: 6px;
    font-weight: 600;
    display: none;
  }

  .error.visible { display: block; }

  /* ===== BOTONES ===== */
  button {
    font-family: inherit;
    font-size: 20px;
    padding: 14px 28px;
    border: none;
    border-radius: 10px;
    background: #1f3a93;
    color: #fff;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.2s, transform 0.1s;
    width: 100%;
  }

  button:hover { background: #16306e; }
  button:active { transform: scale(0.98); }

  button.secondary {
    background: #486581;
    margin-top: 12px;
  }
  button.secondary:hover { background: #334e68; }

  .button-row {
    display: flex;
    gap: 14px;
    flex-wrap: wrap;
    margin-top: 16px;
  }
  .button-row button { flex: 1; min-width: 200px; }

  /* ===== PANTALLA DE ESCRITURA ===== */
  .text-label {
    font-size: 0.9rem;
    font-weight: 600;
    color: #486581;
    margin-bottom: 8px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  #textoObjetivo {
    background: #f8fafc;
    border: 2px solid #e1e8ed;
    border-radius: 10px;
    padding: 18px 20px;
    font-size: 22px;
    line-height: 1.7;
    margin-bottom: 20px;
    letter-spacing: 0.3px;
    user-select: none;
    word-wrap: break-word;
  }

  #textoObjetivo span.ok { color: #2f855a; }
  #textoObjetivo span.ko { color: #c53030; background: #fed7d7; border-radius: 3px; }
  #textoObjetivo span.pending { color: #7b8794; }
  #textoObjetivo span.current { background: #ffe8a1; border-radius: 3px; }

  textarea {
    width: 100%;
    min-height: 140px;
    padding: 16px 18px;
    font-size: 22px;
    line-height: 1.7;
    font-family: inherit;
    border: 2px solid #1f3a93;
    border-radius: 10px;
    resize: vertical;
    background: #fff;
    color: #1f2933;
    letter-spacing: 0.3px;
  }
  textarea:focus { outline: none; box-shadow: 0 0 0 3px rgba(31,58,147,0.15); }

  .stats {
    display: flex;
    gap: 20px;
    justify-content: space-around;
    background: #f0f4f8;
    border-radius: 10px;
    padding: 14px 10px;
    margin-top: 18px;
    flex-wrap: wrap;
  }
  .stat { text-align: center; flex: 1; min-width: 100px; }
  .stat .value { font-size: 1.5rem; font-weight: 700; color: #1f3a93; }
  .stat .label { font-size: 0.85rem; color: #616e7c; text-transform: uppercase; letter-spacing: 0.5px; }

  .instruccion {
    background: #fffbea;
    border-left: 5px solid #f6ad55;
    padding: 12px 16px;
    border-radius: 8px;
    font-size: 0.95rem;
    color: #7b5e00;
    margin-top: 16px;
  }

  /* ===== PANTALLA RESULTADOS ===== */
  .resultado-titulo {
    text-align: center;
    font-size: 1.5rem;
    color: #2f855a;
    margin-bottom: 20px;
    font-weight: 700;
  }

  .resultado-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 16px;
    margin-bottom: 22px;
  }
  .resultado-item {
    background: #f0f4f8;
    border-radius: 10px;
    padding: 16px;
    text-align: center;
  }
  .resultado-item .label { font-size: 0.85rem; color: #616e7c; text-transform: uppercase; letter-spacing: 0.5px; }
  .resultado-item .value { font-size: 1.8rem; font-weight: 700; color: #1f3a93; margin-top: 4px; }

  .nota-final {
    text-align: center;
    font-size: 2.5rem;
    font-weight: 800;
    color: #1f3a93;
    margin: 10px 0;
  }

  .mensaje-motivador {
    text-align: center;
    font-size: 1.15rem;
    font-weight: 600;
    color: #2f855a;
    margin: 12px 0 20px;
    padding: 14px;
    background: #e6fffa;
    border-radius: 10px;
  }

  .captura-aviso {
    background: #fff4e6;
    border: 2px dashed #ed8936;
    border-radius: 10px;
    padding: 16px;
    text-align: center;
    font-size: 1rem;
    color: #7b341e;
    font-weight: 600;
    margin-bottom: 20px;
  }

  .data-line {
    text-align: center;
    color: #486581;
    margin-bottom: 8px;
    font-size: 1rem;
  }

  /* ===== UTILIDADES ===== */
  .hidden { display: none !important; }

  @media (max-width: 640px) {
    header h1 { font-size: 1.4rem; }
    .card { padding: 20px 18px; }
    body { font-size: 18px; }
    #textoObjetivo, textarea { font-size: 20px; }
  }
</style>
</head>
<body>

<header>
  <h1>TYPING TEXT - Prueba IES Ricardo Marín</h1>
</header>

<!-- ============================================================
     PANTALLA 1: REGISTRO
     ============================================================ -->
<section id="pantallaRegistro" class="card">
  <div class="form-group">
    <label for="nombreAlumno">Nombre y Apellidos</label>
    <input type="text" id="nombreAlumno" placeholder="Ej.: Juan Pérez García" autocomplete="off">
    <div class="hint">Escribe tu nombre completo, con la inicial de cada palabra en mayúscula.</div>
    <div id="errorNombre" class="error">El nombre debe tener la inicial de cada palabra en mayúscula (ej.: Juan Pérez García).</div>
  </div>

  <div class="form-group">
    <label for="cursoAlumno">Curso</label>
    <select id="cursoAlumno">
      <option value="">-- Selecciona tu curso --</option>
      <option value="2ESO">2º ESO</option>
      <option value="3ESO">3º ESO</option>
      <option value="4ESO">4º ESO</option>
      <option value="2BACH">2º Bachillerato</option>
    </select>
  </div>

  <div class="instruccion">
    💡 Intenta usar al menos los dedos <strong>índice, corazón y anular</strong> de ambas manos, manteniendo la postura correcta.
  </div>

  <div class="button-row">
    <button id="btnComenzar">Comenzar typing text</button>
  </div>
</section>

<!-- ============================================================
     PANTALLA 2: ESCRITURA
     ============================================================ -->
<section id="pantallaEscritura" class="card hidden">
  <div class="text-label" id="textoActivoLabel">Typing Text 1</div>
  <div id="textoObjetivo"></div>

  <textarea id="areaEscritura" placeholder="Empieza a escribir aquí..." autocomplete="off" spellcheck="false"></textarea>

  <div class="stats">
    <div class="stat"><div class="value" id="statTiempo">0s</div><div class="label">Tiempo</div></div>
    <div class="stat"><div class="value" id="statPPM">0</div><div class="label">PPM</div></div>
    <div class="stat"><div class="value" id="statPrecision">100%</div><div class="label">Precisión</div></div>
  </div>

  <div class="button-row">
    <button id="btnFinalizar" class="secondary">Finalizar</button>
  </div>
</section>

<!-- ============================================================
     PANTALLA 3: RESULTADOS
     ============================================================ -->
<section id="pantallaResultados" class="card hidden">
  <div class="resultado-titulo">✅ Prueba finalizada</div>

  <div class="data-line" id="dataAlumno"></div>
  <div class="data-line" id="dataTexto"></div>

  <div class="resultado-grid">
    <div class="resultado-item"><div class="label">PPM</div><div class="value" id="resPPM">0</div></div>
    <div class="resultado-item"><div class="label">Precisión</div><div class="value" id="resPrecision">0%</div></div>
    <div class="resultado-item"><div class="label">Tiempo</div><div class="value" id="resTiempo">0s</div></div>
  </div>

  <div class="nota-final" id="resNota">0 / 10</div>
  <div class="mensaje-motivador" id="resMensaje"></div>

  <div class="captura-aviso">
    📸 Haz una captura de pantalla de esta página y envíala por <strong>AULES</strong> para que tu profesor pueda verla.
  </div>

  <div class="button-row">
    <button id="btnRepetir">Repetir este texto</button>
    <button id="btnCambiar" class="secondary">Probar el otro texto</button>
  </div>
</section>

<script>
/* ================================================================
   CONFIGURACIÓN
   ================================================================ */
const TEXTOS = {
  1: "¿Qué hacía Íñigo en aquel viejo desván? Buscaba con avidez algún baúl vacío, lápices útiles, mapas húmedos y códigos cifrados. Aunque el frío húmedo calaba sus huesos, jamás perdió la calma ni cedió ante el pánico. Con manos ágiles, tecleó claves complejas, abrió cajas metálicas y revisó cada página sin cometer ningún desliz. Quien domina bien su técnica evita mirar abajo, mantiene el ritmo firme y logra un trabajo pulcro.",
  2: "¿Cómo logró Álvaro resolver aquel enigma tan rápido? Nadie imaginaba que detrás del muro húmedo hubiera un túnel secreto lleno de baúles, brújulas antiguas y cartas inéditas. Con mucha cautela, encendió la lámpara móvil, anotó varios números clave y cruzó el umbral sin hacer ruido. Quien practica cada día con constancia y buena postura alcanza una velocidad envidiable, evita errores tontos y domina cualquier teclado sin esfuerzo."
};

// Rangos de PPM objetivo por curso: [min, max]
const RANGOS_CURSO = {
  "2ESO":  { min: 18, max: 25, nombre: "2º ESO" },
  "3ESO":  { min: 25, max: 32, nombre: "3º ESO" },
  "4ESO":  { min: 32, max: 40, nombre: "4º ESO" },
  "2BACH": { min: 40, max: 50, nombre: "2º Bachillerato" }
};

/* ================================================================
   ESTADO DE LA APLICACIÓN
   ================================================================ */
const estado = {
  nombre: "",
  curso: "",
  textoActivo: 1,          // 1 o 2
  inicioTiempo: null,
  intervaloReloj: null,
  finalizado: false
};

/* ================================================================
   REFERENCIAS AL DOM
   ================================================================ */
const $ = id => document.getElementById(id);

const pantallaRegistro   = $("pantallaRegistro");
const pantallaEscritura  = $("pantallaEscritura");
const pantallaResultados = $("pantallaResultados");

const inputNombre  = $("nombreAlumno");
const selectCurso  = $("cursoAlumno");
const errorNombre  = $("errorNombre");
const btnComenzar  = $("btnComenzar");

const textoActivoLabel = $("textoActivoLabel");
const textoObjetivo    = $("textoObjetivo");
const areaEscritura    = $("areaEscritura");
const statTiempo       = $("statTiempo");
const statPPM          = $("statPPM");
const statPrecision    = $("statPrecision");
const btnFinalizar     = $("btnFinalizar");

const dataAlumno    = $("dataAlumno");
const dataTexto     = $("dataTexto");
const resPPM        = $("resPPM");
const resPrecision  = $("resPrecision");
const resTiempo     = $("resTiempo");
const resNota       = $("resNota");
const resMensaje    = $("resMensaje");
const btnRepetir    = $("btnRepetir");
const btnCambiar    = $("btnCambiar");

/* ================================================================
   VALIDACIÓN DEL NOMBRE
   Regla: cada palabra debe empezar por mayúscula (permite tildes y ñ).
   ================================================================ */
function validarNombre(nombre) {
  const limpio = nombre.trim().replace(/\s+/g, " ");
  if (limpio.length < 3) return false;
  // Cada palabra: primera letra mayúscula (incluye ÁÉÍÓÚÜÑ), resto minúsculas o lo que sea.
  const regex = /^([A-ZÁÉÍÓÚÜÑ][a-záéíóúüñ]*(?:\s+|$))+$/u;
  return regex.test(limpio);
}

function normalizarNombre(nombre) {
  return nombre.trim().replace(/\s+/g, " ");
}

/* ================================================================
   RENDERIZADO DEL TEXTO OBJETIVO (carácter a carácter)
   ================================================================ */
function renderTexto(escrito) {
  const objetivo = TEXTOS[estado.textoActivo];
  const fragment = document.createDocumentFragment();

  for (let i = 0; i < objetivo.length; i++) {
    const span = document.createElement("span");
    span.textContent = objetivo[i] === " " ? "\u00A0" : objetivo[i];

    if (i < escrito.length) {
      span.className = escrito[i] === objetivo[i] ? "ok" : "ko";
    } else if (i === escrito.length) {
      span.className = "current pending";
    } else {
      span.className = "pending";
    }
    fragment.appendChild(span);
  }
  textoObjetivo.innerHTML = "";
  textoObjetivo.appendChild(fragment);
}

/* ================================================================
   CÁLCULOS
   ================================================================ */
function calcularPPM(caracteresCorrectos, segundos) {
  if (segundos <= 0) return 0;
  const minutos = segundos / 60;
  return Math.round((caracteresCorrectos / 5) / minutos);
}

function calcularPrecision(correctos, totalEscritos) {
  if (totalEscritos === 0) return 100;
  return Math.round((correctos / totalEscritos) * 100);
}

/**
 * Nota sobre 10:
 *  - Si PPM < min  → nota proporcional desde 0 hasta 5 (regla de tres).
 *  - Si min ≤ PPM ≤ max → interpolación lineal entre 5 y 10.
 *  - Si PPM > max → 10.
 *  - Penalización por precisión: si precisión < 90%, se resta hasta 2 puntos
 *    proporcionalmente ((90 - precision) / 90) * 2.
 */
function calcularNota(ppm, precision, curso) {
  const r = RANGOS_CURSO[curso];
  let nota;

  if (ppm <= r.min) {
    nota = (ppm / r.min) * 5;
  } else if (ppm >= r.max) {
    nota = 10;
  } else {
    nota = 5 + ((ppm - r.min) / (r.max - r.min)) * 5;
  }

  if (precision < 90) {
    nota -= ((90 - precision) / 90) * 2;
  }

  return Math.max(0, Math.min(10, Math.round(nota * 10) / 10));
}

function obtenerMensaje(nota) {
  if (nota >= 9)   return "¡Excelente! Tus dedos vuelan. Sigue así. 🚀";
  if (nota >= 7)   return "¡Muy bien! Estás muy cerca de la perfección. 👏";
  if (nota >= 5)   return "¡Buen trabajo! Con un poco más de práctica lo bordas. 💪";
  return "¡No te rindas! La constancia es la clave del éxito. 🌱";
}

function formatearTiempo(segundos) {
  const m = Math.floor(segundos / 60);
  const s = Math.floor(segundos % 60);
  return m > 0 ? `${m}m ${s}s` : `${s}s`;
}

/* ================================================================
   CONTADORES EN VIVO
   ================================================================ */
function actualizarStats() {
  const objetivo = TEXTOS[estado.textoActivo];
  const escrito = areaEscritura.value;

  let correctos = 0;
  const total = Math.min(escrito.length, objetivo.length);
  for (let i = 0; i < total; i++) {
    if (escrito[i] === objetivo[i]) correctos++;
  }
  const precision = calcularPrecision(correctos, escrito.length);

  const segundos = (Date.now() - estado.inicioTiempo) / 1000;
  const ppm = calcularPPM(correctos, segundos);

  statTiempo.textContent = formatearTiempo(segundos);
  statPPM.textContent = ppm;
  statPrecision.textContent = precision + "%";
}

function iniciarCronometro() {
  detenerCronometro();
  estado.intervaloReloj = setInterval(actualizarStats, 200);
}

function detenerCronometro() {
  if (estado.intervaloReloj) {
    clearInterval(estado.intervaloReloj);
    estado.intervaloReloj = null;
  }
}

/* ================================================================
   FLUJO DE PANTALLAS
   ================================================================ */
function mostrarPantalla(pantalla) {
  [pantallaRegistro, pantallaEscritura, pantallaResultados].forEach(p =>
    p.classList.add("hidden")
  );
  pantalla.classList.remove("hidden");
}

function prepararTexto() {
  estado.finalizado = false;
  estado.inicioTiempo = null;
  textoActivoLabel.textContent = "Typing Text " + estado.textoActivo;
  areaEscritura.value = "";
  areaEscritura.disabled = false;
  renderTexto("");
  statTiempo.textContent = "0s";
  statPPM.textContent = "0";
  statPrecision.textContent = "100%";
}

function comenzarPrueba() {
  prepararTexto();
  mostrarPantalla(pantallaEscritura);
  areaEscritura.focus();
}

function finalizarPrueba() {
  if (estado.finalizado) return;
  estado.finalizado = true;
  detenerCronometro();
  areaEscritura.disabled = true;

  const objetivo = TEXTOS[estado.textoActivo];
  const escrito = areaEscritura.value;

  let correctos = 0;
  const total = Math.min(escrito.length, objetivo.length);
  for (let i = 0; i < total; i++) {
    if (escrito[i] === objetivo[i]) correctos++;
  }

  const segundos = Math.max(1, (Date.now() - estado.inicioTiempo) / 1000);
  const precision = calcularPrecision(correctos, escrito.length || 1);
  const ppm = calcularPPM(correctos, segundos);
  const nota = calcularNota(ppm, precision, estado.curso);

  // Pintar resultados
  dataAlumno.textContent = `${estado.nombre} — ${RANGOS_CURSO[estado.curso].nombre}`;
  dataTexto.textContent = "Texto realizado: Typing Text " + estado.textoActivo;
  resPPM.textContent = ppm;
  resPrecision.textContent = precision + "%";
  resTiempo.textContent = formatearTiempo(segundos);
  resNota.textContent = nota.toFixed(1) + " / 10";
  resMensaje.textContent = obtenerMensaje(nota);

  mostrarPantalla(pantallaResultados);
}

/* ================================================================
   EVENTOS
   ================================================================ */

// Validación en vivo del nombre
inputNombre.addEventListener("input", () => {
  if (validarNombre(inputNombre.value)) {
    errorNombre.classList.remove("visible");
    inputNombre.style.borderColor = "#2f855a";
  } else {
    inputNombre.style.borderColor = "#c53030";
  }
});

// Comenzar
btnComenzar.addEventListener("click", () => {
  const nombre = normalizarNombre(inputNombre.value);
  const curso = selectCurso.value;

  if (!validarNombre(nombre)) {
    errorNombre.classList.add("visible");
    inputNombre.focus();
    return;
  }
  if (!curso) {
    alert("Selecciona tu curso antes de comenzar.");
    selectCurso.focus();
    return;
  }

  errorNombre.classList.remove("visible");
  estado.nombre = nombre;
  estado.curso = curso;
  // Texto aleatorio la primera vez
  estado.textoActivo = Math.random() < 0.5 ? 1 : 2;

  comenzarPrueba();
});

// Escritura en el textarea
areaEscritura.addEventListener("input", () => {
  if (estado.finalizado) return;

  if (estado.inicioTiempo === null && areaEscritura.value.length > 0) {
    estado.inicioTiempo = Date.now();
    iniciarCronometro();
  }

  renderTexto(areaEscritura.value);
  actualizarStats();

  // Auto-finalizar si se ha alcanzado (o superado) la longitud del objetivo
  const objetivo = TEXTOS[estado.textoActivo];
  if (areaEscritura.value.length >= objetivo.length) {
    finalizarPrueba();
  }
});

// Finalizar manualmente
btnFinalizar.addEventListener("click", () => {
  if (estado.inicioTiempo === null) {
    // Si aún no ha empezado a escribir, no tiene sentido finalizar
    if (!confirm("Todavía no has empezado a escribir. ¿Quieres salir igualmente?")) return;
  }
  finalizarPrueba();
});

// Repetir el mismo texto
btnRepetir.addEventListener("click", () => {
  comenzarPrueba();
});

// Cambiar al otro texto
btnCambiar.addEventListener("click", () => {
  estado.textoActivo = estado.textoActivo === 1 ? 2 : 1;
  comenzarPrueba();
});
</script>

</body>
</html>
