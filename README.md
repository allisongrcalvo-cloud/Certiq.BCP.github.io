<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>CertiQ · CV con QR | Empleo, Becas y Crecimiento Joven</title>
  <!-- Tailwind + Font Awesome + Google Fonts -->
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700&display=swap" rel="stylesheet">
  <!-- QR Code Library -->
  <script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js"></script>
  <style>
    * { font-family: 'Inter', sans-serif; }
    body { background: #0c2e4e; scroll-behavior: smooth; } /* Fondo azul principal */
    .card-hover:hover { transform: translateY(-4px); transition: all 0.2s ease; box-shadow: 0 20px 25px -12px rgba(0,0,0,0.2); }
    .gradient-bg { background: linear-gradient(135deg, #f97316 0%, #1e3a8a 100%); } /* Naranja a azul oscuro */
    .badge-skill { background: #e0f2fe; color: #0369a1; font-size: 0.75rem; font-weight: 500; padding: 0.25rem 0.75rem; border-radius: 9999px; }
    .qr-container { background: white; padding: 0.75rem; border-radius: 1rem; box-shadow: 0 8px 20px rgba(0,0,0,0.1); display: inline-block; }
    .cv-preview { background: white; border-radius: 1.5rem; box-shadow: 0 10px 25px -5px rgba(0,0,0,0.1); transition: all 0.2s; }
    .opportunity-card { background: #ffffff; border-radius: 1.25rem; transition: 0.2s; border: 1px solid #bfdbfe; }
    .opportunity-card:hover { border-color: #f97316; background: #fef9f0; } /* sutil hover naranja */
    .btn-orange { background-color: #f97316; }
    .btn-orange:hover { background-color: #ea580c; }
    .text-orange { color: #f97316; }
    .border-orange { border-color: #f97316; }
    /* Fondo para secciones internas, mantener tarjetas blancas, pero fondo general azul */
    .section-bg { background: #0c2e4e; } /* mismo que body para consistencia */
    .card-white { background: white; }
  </style>
</head>
<body class="antialiased">

  <!-- NAVBAR (fondo blanco pero con sombra, se adapta) -->
  <nav class="bg-white border-b border-blue-200 sticky top-0 z-30 shadow-sm">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <div class="flex items-center gap-2">
          <i class="fas fa-qrcode text-2xl text-orange-500"></i>
          <span class="font-bold text-xl tracking-tight text-gray-800">Certi<span class="text-orange-500">Q</span></span>
          <span class="hidden sm:inline-block ml-2 text-xs bg-orange-100 text-orange-700 px-2 py-0.5 rounded-full">+QR skills</span>
        </div>
        <div class="hidden md:flex space-x-6 text-gray-600 font-medium">
          <a href="#cv-builder" class="hover:text-orange-500">Crea tu CV</a>
          <a href="#oportunidades" class="hover:text-orange-500">Oportunidades</a>
          <a href="#becas" class="hover:text-orange-500">Becas + eventos</a>
        </div>
        <div class="flex items-center gap-2">
          <i class="fas fa-user-circle text-2xl text-gray-500"></i>
        </div>
      </div>
    </div>
  </nav>

  <!-- HERO SECTION con gradiente naranja-azul -->
  <section class="gradient-bg text-white py-12 md:py-16">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <h1 class="text-3xl md:text-5xl font-extrabold tracking-tight mb-4">Tu primer trabajo <span class="text-yellow-200">empieza con CertiQ</span></h1>
      <p class="text-lg md:text-xl text-orange-100 max-w-2xl mx-auto">Crea tu CV profesional, acredita tus habilidades blandas con QR, y accede a trabajo, voluntariados, becas, eventos y certificaciones.</p>
      <div class="mt-6 flex flex-wrap justify-center gap-4">
        <a href="#cv-builder" class="bg-white text-orange-600 px-6 py-3 rounded-full font-semibold shadow-lg hover:shadow-xl transition flex items-center gap-2"><i class="fas fa-file-alt"></i> Armar CV ahora</a>
        <a href="#oportunidades" class="bg-transparent border border-white px-6 py-3 rounded-full font-semibold hover:bg-white/10 transition"><i class="fas fa-briefcase"></i> Ver oportunidades</a>
      </div>
    </div>
  </section>

  <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    <!-- SECCIÓN CV + QR (dos columnas) -->
    <div id="cv-builder" class="scroll-mt-20">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        <!-- COLUMNA IZQUIERDA: FORMULARIO CV (fondo blanco) -->
        <div class="bg-white rounded-2xl shadow-md p-6 border border-blue-200">
          <div class="flex items-center gap-2 border-b border-gray-200 pb-4 mb-5">
            <i class="fas fa-pen-fancy text-orange-500 text-xl"></i>
            <h2 class="text-2xl font-bold text-gray-800">📄 Construye tu CV</h2>
          </div>
          <form id="cvForm" class="space-y-4">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-semibold text-gray-700">Nombre completo *</label>
                <input type="text" id="fullName" class="mt-1 w-full border border-gray-300 rounded-xl p-2.5 focus:ring-2 focus:ring-orange-400 outline-none" placeholder="Ana Rodríguez" value="María González">
              </div>
              <div>
                <label class="block text-sm font-semibold text-gray-700">Correo electrónico</label>
                <input type="email" id="email" class="mt-1 w-full border border-gray-300 rounded-xl p-2.5 focus:ring-2 focus:ring-orange-400" placeholder="joven@email.com" value="maria.g@certiq.com">
              </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div>
                <label class="block text-sm font-semibold text-gray-700">Teléfono</label>
                <input type="text" id="phone" class="mt-1 w-full border border-gray-300 rounded-xl p-2.5" placeholder="+56 9 1234 5678" value="+56 9 8765 4321">
              </div>
              <div>
                <label class="block text-sm font-semibold text-gray-700">Profesión / Rol</label>
                <input type="text" id="role" class="mt-1 w-full border border-gray-300 rounded-xl p-2.5" placeholder="Estudiante / Desarrollador" value="Desarrolladora Frontend Jr">
              </div>
            </div>
            <div>
              <label class="block text-sm font-semibold text-gray-700">Resumen profesional</label>
              <textarea id="summary" rows="2" class="mt-1 w-full border border-gray-300 rounded-xl p-2.5" placeholder="Joven proactivo con habilidades en liderazgo...">Apasionada por la tecnología y el trabajo colaborativo. Experiencia en proyectos sociales y voluntariados. Motivada por el aprendizaje continuo.</textarea>
            </div>
            <div>
              <label class="block text-sm font-semibold text-gray-700">Experiencia (último puesto)</label>
              <textarea id="experience" rows="2" class="mt-1 w-full border border-gray-300 rounded-xl p-2.5" placeholder="Ej: Voluntaria en ONG, Community Manager">Asistente en marketing digital (Freelance) · 2023 - actualidad<br>Voluntaria en TECHsinFronteras</textarea>
            </div>
            <div>
              <label class="block text-sm font-semibold text-gray-700">Educación</label>
              <textarea id="education" rows="2" class="mt-1 w-full border border-gray-300 rounded-xl p-2.5" placeholder="Técnico / Universidad">Bootcamp Desarrollo Web - 2024<br>Estudiante de Ingeniería Informática (3er año)</textarea>
            </div>
            <div>
              <label class="block text-sm font-semibold text-gray-700">Habilidades técnicas</label>
              <input type="text" id="techSkills" class="mt-1 w-full border border-gray-300 rounded-xl p-2.5" placeholder="JavaScript, React, Figma, Python" value="JavaScript, React, Tailwind, SQL, Gestión de proyectos">
            </div>

            <!-- Habilidades blandas con checkboxes -->
            <div>
              <label class="block text-sm font-semibold text-gray-700 mb-2">✨ Habilidades blandas (selecciona las tuyas)</label>
              <div class="flex flex-wrap gap-2" id="softSkillsCheckboxGroup">
                <!-- Lista dinámica predefinida -->
              </div>
              <p class="text-xs text-gray-500 mt-2">Estas habilidades serán acreditadas mediante código QR verificable.</p>
            </div>
            <button type="button" id="updateCvBtn" class="w-full bg-orange-500 hover:bg-orange-600 text-white font-bold py-3 rounded-xl transition shadow-md flex items-center justify-center gap-2"><i class="fas fa-sync-alt"></i> Actualizar CV y QR</button>
          </form>
        </div>

        <!-- COLUMNA DERECHA: VISTA PREVIA CV + QR -->
        <div class="space-y-6">
          <!-- Vista previa del CV -->
          <div class="cv-preview p-5 bg-white border border-blue-200 rounded-2xl">
            <div class="flex justify-between items-start border-b border-gray-100 pb-3 mb-3">
              <h3 class="font-bold text-xl text-gray-800"><i class="fas fa-id-card text-orange-500 mr-2"></i>Mi CV digital</h3>
              <i class="fas fa-download text-gray-400 hover:text-orange-500 cursor-pointer" id="mockDownloadCv" title="Descargar como plantilla (demo)"></i>
            </div>
            <div id="cvPreviewContent">
              <div class="animate-pulse space-y-2">Cargando vista previa...</div>
            </div>
          </div>
          <!-- Sección QR habilidades blandas acreditadas (fondo azul claro) -->
          <div class="bg-gradient-to-br from-blue-800 to-blue-900 rounded-2xl p-5 border border-blue-400 shadow-lg">
            <div class="flex items-center gap-3 mb-3">
              <i class="fas fa-qrcode text-2xl text-orange-300"></i>
              <h3 class="font-bold text-lg text-white">🎓 Habilidades blandas acreditadas con QR · CertiQ</h3>
            </div>
            <p class="text-sm text-blue-100 mb-4">Escanea este código para verificar tus habilidades blandas certificadas. Compártelo con empleadores y aumenta tu credibilidad.</p>
            <div class="flex flex-col sm:flex-row items-center gap-6 justify-between">
              <div id="qrCodeContainer" class="qr-container flex justify-center bg-white p-3 rounded-xl mx-auto sm:mx-0"></div>
              <div class="text-sm text-blue-100 max-w-xs">
                <i class="fas fa-check-circle text-green-300"></i> <span class="font-semibold">Acreditación CertiQ</span><br>
                <span id="qrSkillsList" class="text-xs text-blue-200">Selecciona habilidades blandas</span>
                <div class="mt-2 text-xs bg-blue-700/50 rounded-lg p-2 text-white">✅ Certificado por red de talento joven</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- SECCIÓN OPORTUNIDADES (fondo azul, tarjetas blancas) -->
    <div id="oportunidades" class="scroll-mt-16 mt-20">
      <div class="flex items-center gap-3 mb-8">
        <div class="h-10 w-1 bg-orange-500 rounded-full"></div>
        <h2 class="text-3xl font-bold text-white">🚀 Oportunidades para crecer</h2>
      </div>
      <p class="text-blue-100 mb-8">Encuentra trabajo, voluntariados, eventos, certificaciones y becas diseñadas para jóvenes como tú.</p>
      
      <div class="space-y-12">
        <!-- TRABAJOS -->
        <div>
          <div class="flex items-center gap-2 mb-4"><i class="fas fa-briefcase text-orange-400 text-xl"></i><h3 class="text-2xl font-semibold text-white">Ofertas de Trabajo</h3></div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-5" id="jobsList"></div>
        </div>
        <!-- VOLUNTARIADOS -->
        <div>
          <div class="flex items-center gap-2 mb-4"><i class="fas fa-hand-holding-heart text-blue-300 text-xl"></i><h3 class="text-2xl font-semibold text-white">Voluntariados</h3></div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-5" id="volunteerList"></div>
        </div>
        <!-- EVENTOS -->
        <div>
          <div class="flex items-center gap-2 mb-4"><i class="fas fa-calendar-alt text-orange-400 text-xl"></i><h3 class="text-2xl font-semibold text-white">Eventos + Networking</h3></div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-5" id="eventsList"></div>
        </div>
        <!-- CERTIFICADOS -->
        <div>
          <div class="flex items-center gap-2 mb-4"><i class="fas fa-certificate text-blue-300 text-xl"></i><h3 class="text-2xl font-semibold text-white">Certificados / Cursos oficiales</h3></div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-5" id="certificatesList"></div>
        </div>
        <!-- BECAS -->
        <div id="becas">
          <div class="flex items-center gap-2 mb-4"><i class="fas fa-graduation-cap text-orange-400 text-xl"></i><h3 class="text-2xl font-semibold text-white">Becas y financiamiento</h3></div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-5" id="scholarshipsList"></div>
        </div>
      </div>
    </div>
  </main>

  <footer class="bg-gray-900 text-gray-300 mt-20 py-8">
    <div class="max-w-7xl mx-auto px-4 text-center">
      <p class="text-sm"><i class="fas fa-qrcode mr-1 text-orange-400"></i> CertiQ · Acredita tu talento blando con QR, conecta con empleadores y construye tu futuro.</p>
      <p class="text-xs mt-2">© 2025 CertiQ - Impulsando la empleabilidad joven</p>
    </div>
  </footer>

  <script>
    // ---------- DATOS DE OPORTUNIDADES ----------
    const jobsData = [
      { title: "Desarrollador Frontend Junior", company: "TechStart Chile", location: "Remoto", desc: "React + Tailwind. Buscamos joven talento con ganas de aprender.", link: "#" },
      { title: "Community Manager", company: "Agència Creativa", location: "Híbrido", desc: "Gestión de redes sociales, creatividad y comunicación. Se valoran habilidades blandas.", link: "#" },
    ];
    const volunteerData = [
      { title: "Mentoría Digital para adultos mayores", organization: "Fundación Conecta", desc: "Enseñar herramientas básicas tecnológicas, 4h semanales. Certificado de voluntariado.", link: "#" },
      { title: "Eco Voluntariado: Reforestación", organization: "Jóvenes por el Clima", desc: "Actividades al aire libre, trabajo en equipo y liderazgo ambiental.", link: "#" },
    ];
    const eventsData = [
      { title: "Hackathon Youth Innovation 2025", date: "15-17 Mayo", lugar: "Online + Presencial", desc: "Desarrolla soluciones para empleabilidad. Premios y networking.", link: "#" },
      { title: "Taller: Cómo destacar en entrevistas", date: "28 Mayo 2025", lugar: "Zoom", desc: "Potencia tus soft skills y prepara tu mejor versión.", link: "#" },
    ];
    const certificatesData = [
      { title: "Certificación en Habilidades Blandas (CertiQ + Google)", provider: "CertiQ Academy", desc: "Curso gratuito + acreditación oficial con QR. Potencia comunicación y liderazgo.", link: "#" },
      { title: "Diplomado en Marketing Digital para Jóvenes", provider: "HubSpot Academy", desc: "Certificado internacional, incluye módulo de empleabilidad.", link: "#" },
    ];
    const scholarshipsData = [
      { title: "Beca ‘Talento Digital 2025’", amount: "100% cobertura", desc: "Bootcamp full-stack para menores de 30 años. Inscripciones abiertas.", link: "#" },
      { title: "Beca Liderazgo Femenino Tech", amount: "$500.000 CLP", desc: "Apoyo para estudios en tecnología y mentoría con empresas líderes.", link: "#" },
    ];

    function renderOpportunities() {
      renderCards("jobsList", jobsData, (item) => `<i class="fas fa-building mr-1 text-orange-500"></i> ${item.company}`);
      renderCards("volunteerList", volunteerData, (item) => `<i class="fas fa-heart text-blue-600"></i> ${item.organization}`);
      renderCards("eventsList", eventsData, (item) => `<i class="fas fa-calendar-week text-orange-500"></i> ${item.date} · ${item.lugar}`);
      renderCards("certificatesList", certificatesData, (item) => `<i class="fas fa-award text-blue-600"></i> ${item.provider}`);
      renderCards("scholarshipsList", scholarshipsData, (item) => `<i class="fas fa-coins text-orange-500"></i> ${item.amount}`);
    }

    function renderCards(containerId, data, extraInfoCallback) {
      const container = document.getElementById(containerId);
      if (!container) return;
      container.innerHTML = data.map(item => `
        <div class="opportunity-card p-5 card-hover cursor-pointer" onclick="alert('📌 Demo: Más información en breve. ¡Regístrate para postular!')">
          <h4 class="font-bold text-lg text-gray-800">${item.title}</h4>
          <div class="text-sm text-gray-500 mt-1 flex items-center gap-1">${extraInfoCallback(item)}</div>
          <p class="text-gray-600 text-sm mt-2">${item.desc}</p>
          <div class="mt-3"><span class="text-orange-500 text-xs font-semibold inline-flex items-center gap-1">Postular / Saber más <i class="fas fa-arrow-right"></i></span></div>
        </div>
      `).join('');
    }

    // Soft skills list
    const softSkillsList = [
      "Comunicación efectiva", "Trabajo en equipo", "Liderazgo", "Resolución de conflictos",
      "Adaptabilidad", "Pensamiento crítico", "Creatividad", "Gestión del tiempo", "Empatía", "Negociación"
    ];
    
    function buildSoftSkillsCheckboxes() {
      const container = document.getElementById("softSkillsCheckboxGroup");
      container.innerHTML = "";
      softSkillsList.forEach(skill => {
        const label = document.createElement("label");
        label.className = "flex items-center gap-1.5 bg-gray-50 px-3 py-1.5 rounded-full border border-gray-200 text-sm cursor-pointer hover:bg-orange-50 transition";
        const cb = document.createElement("input");
        cb.type = "checkbox";
        cb.value = skill;
        cb.className = "w-4 h-4 text-orange-500 rounded focus:ring-orange-400";
        if (skill === "Comunicación efectiva" || skill === "Trabajo en equipo" || skill === "Adaptabilidad") cb.checked = true;
        label.appendChild(cb);
        label.appendChild(document.createTextNode(skill));
        container.appendChild(label);
      });
    }

    function getSelectedSoftSkills() {
      const checkboxes = document.querySelectorAll("#softSkillsCheckboxGroup input[type='checkbox']");
      const selected = [];
      checkboxes.forEach(cb => { if (cb.checked) selected.push(cb.value); });
      return selected;
    }

    function escapeHtml(str) {
      if (!str) return '';
      return str.replace(/[&<>]/g, function(m) {
        if (m === '&') return '&amp;';
        if (m === '<') return '&lt;';
        if (m === '>') return '&gt;';
        return m;
      });
    }

    function updateCVAndQR() {
      const fullName = document.getElementById("fullName").value.trim() || "Joven Talento";
      const email = document.getElementById("email").value.trim() || "correo@ejemplo.com";
      const phone = document.getElementById("phone").value.trim() || "---";
      const role = document.getElementById("role").value.trim() || "Profesional en formación";
      const summary = document.getElementById("summary").value.trim() || "Sin resumen";
      const experience = document.getElementById("experience").value.trim() || "Sin experiencia registrada";
      const education = document.getElementById("education").value.trim() || "---";
      const techSkills = document.getElementById("techSkills").value.trim() || "No especificadas";
      const selectedSoft = getSelectedSoftSkills();
      
      const cvHtml = `
        <div class="space-y-2">
          <div class="flex justify-between items-start flex-wrap">
            <div><h4 class="font-extrabold text-xl text-gray-900">${escapeHtml(fullName)}</h4><p class="text-orange-600 font-medium">${escapeHtml(role)}</p></div>
            <div class="text-right text-xs text-gray-500">${escapeHtml(email)}<br>${escapeHtml(phone)}</div>
          </div>
          <div class="border-t border-gray-100 pt-2"><span class="font-semibold text-gray-700">📌 Resumen:</span><p class="text-sm text-gray-600">${escapeHtml(summary)}</p></div>
          <div><span class="font-semibold text-gray-700">💼 Experiencia:</span><p class="text-sm text-gray-600 whitespace-pre-line">${escapeHtml(experience)}</p></div>
          <div><span class="font-semibold text-gray-700">🎓 Educación:</span><p class="text-sm text-gray-600">${escapeHtml(education)}</p></div>
          <div><span class="font-semibold text-gray-700">⚙️ Habilidades técnicas:</span><p class="text-sm text-gray-600">${escapeHtml(techSkills)}</p></div>
          <div><span class="font-semibold text-gray-700">🤝 Habilidades blandas:</span><div class="flex flex-wrap gap-1 mt-1">${selectedSoft.map(s => `<span class="badge-skill">${escapeHtml(s)}</span>`).join('') || '<span class="text-gray-400 text-sm">No seleccionadas</span>'}</div></div>
        </div>
      `;
      document.getElementById("cvPreviewContent").innerHTML = cvHtml;
      
      const softSkillsText = selectedSoft.length ? selectedSoft.join(", ") : "habilidades blandas en desarrollo";
      const qrData = `CertiQ Acreditación | Nombre: ${fullName} | Habilidades verificadas: ${softSkillsText} | Fecha: ${new Date().toLocaleDateString()} | www.certiq.demo/valida`;
      const qrContainer = document.getElementById("qrCodeContainer");
      qrContainer.innerHTML = "";
      try {
        new QRCode(qrContainer, {
          text: qrData,
          width: 130,
          height: 130,
          colorDark: "#f97316",
          colorLight: "#ffffff",
          correctLevel: QRCode.CorrectLevel.M
        });
      } catch(e) {
        qrContainer.innerHTML = `<div class="text-red-500 text-xs">Error QR, recarga</div>`;
      }
      document.getElementById("qrSkillsList").innerHTML = `<strong>${selectedSoft.length} habilidades acreditadas:</strong> ${softSkillsText.substring(0, 80)}${softSkillsText.length>80?'...':''}`;
    }
    
    document.addEventListener("DOMContentLoaded", () => {
      buildSoftSkillsCheckboxes();
      renderOpportunities();
      updateCVAndQR();
      
      const updateBtn = document.getElementById("updateCvBtn");
      updateBtn.addEventListener("click", updateCVAndQR);
      
      const formInputs = ["fullName", "email", "phone", "role", "summary", "experience", "education", "techSkills"];
      const updateOnChange = () => updateCVAndQR();
      formInputs.forEach(id => {
        const el = document.getElementById(id);
        if (el) el.addEventListener("input", updateOnChange);
      });
      document.querySelectorAll("#softSkillsCheckboxGroup input").forEach(cb => {
        cb.addEventListener("change", updateOnChange);
      });
      const mockDownload = document.getElementById("mockDownloadCv");
      if(mockDownload) mockDownload.addEventListener("click", () => alert("📄 Tu CV está listo para ser exportado (versión demo). Próximamente descarga en PDF. ¡Súbelo a tu perfil!"));
    });
  </script>
</body>
</html>
