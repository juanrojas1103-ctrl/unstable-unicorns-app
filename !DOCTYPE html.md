<!DOCTYPE html>  
<html lang="es">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">  
    <title>Unstable Unicorns - Deck Master Pro</title>  
    <style>  
        :root {  
            --bg-color: #0b0f19;  
            --surface-bg: rgba(30, 41, 59, 0.7);  
            --card-bg: #1e293b;  
            --card-border: rgba(139, 92, 246, 0.25);  
            --accent-glow: #a855f7;  
            --accent-gradient: linear-gradient(135deg, #a855f7 0%, #6366f1 100%);  
            --accent-btn: #8b5cf6;  
            --text-main: #f8fafc;  
            --text-sub: #94a3b8;  
            --danger: #ef4444;  
            --glass-bg: rgba(15, 23, 42, 0.85);  
        }  
        * {  
            box-sizing: border-box;  
            margin: 0;  
            padding: 0;  
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;  
            -webkit-tap-highlight-color: transparent;  
        }  
        body {  
            background-color: var(--bg-color);  
            background-image:   
                radial-gradient(at 0% 0%, rgba(168, 85, 247, 0.12) 0px, transparent 50%),  
                radial-gradient(at 100% 100%, rgba(99, 102, 241, 0.12) 0px, transparent 50%);  
            color: var(--text-main);  
            padding: 12px;  
            padding-bottom: 250px;  
            min-height: 100vh;  
        }  
  
        /* Top Launcher Navbar */  
        .app-launcher {  
            display: flex;  
            justify-content: space-between;  
            align-items: center;  
            background: var(--glass-bg);  
            backdrop-filter: blur(12px);  
            -webkit-backdrop-filter: blur(12px);  
            border: 1px solid var(--card-border);  
            padding: 10px 16px;  
            border-radius: 18px;  
            margin-bottom: 14px;  
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);  
            position: sticky;  
            top: 10px;  
            z-index: 800;  
        }  
        .launcher-title {  
            display: flex;  
            align-items: center;  
            gap: 8px;  
        }  
        .launcher-title h1 {  
            font-size: 1.1rem;  
            background: linear-gradient(135deg, #c084fc, #818cf8);  
            -webkit-background-clip: text;  
            -webkit-text-fill-color: transparent;  
            font-weight: 800;  
            letter-spacing: -0.5px;  
        }  
        .menu-trigger-btn {  
            background: var(--accent-gradient);  
            color: white;  
            border: none;  
            padding: 8px 14px;  
            border-radius: 12px;  
            font-size: 0.8rem;  
            font-weight: 700;  
            cursor: pointer;  
            box-shadow: 0 4px 14px rgba(168, 85, 247, 0.35);  
            display: flex;  
            align-items: center;  
            gap: 6px;  
            transition: transform 0.2s;  
        }  
        .menu-trigger-btn:active { transform: scale(0.96); }  
  
        /* Quick Action Quick Bar inside Launcher */  
        .quick-drawer {  
            display: none;  
            position: fixed;  
            top: 70px;  
            right: 12px;  
            left: 12px;  
            background: #0f172a;  
            border: 1px solid var(--card-border);  
            border-radius: 16px;  
            padding: 12px;  
            z-index: 850;  
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.7);  
            flex-direction: column;  
            gap: 8px;  
        }  
        .drawer-btn {  
            background-color: #1e293b;  
            color: #f8fafc;  
            border: 1px solid rgba(255, 255, 255, 0.1);  
            padding: 12px;  
            border-radius: 10px;  
            font-size: 0.85rem;  
            font-weight: 600;  
            text-align: left;  
            cursor: pointer;  
            display: flex;  
            align-items: center;  
            gap: 8px;  
        }  
        .drawer-btn.danger { color: #fca5a5; border-color: rgba(239, 68, 68, 0.3); }  
  
        /* Search & Categories Tabs */  
        .search-box {  
            width: 100%;  
            padding: 12px 16px;  
            background-color: rgba(30, 41, 59, 0.6);  
            border: 1px solid var(--card-border);  
            border-radius: 14px;  
            color: white;  
            font-size: 0.95rem;  
            margin-bottom: 12px;  
            backdrop-filter: blur(8px);  
        }  
        .search-box:focus {  
            outline: none;  
            border-color: var(--accent-glow);  
            box-shadow: 0 0 12px rgba(168, 85, 247, 0.3);  
        }  
        .nav-tabs {  
            display: flex;  
            gap: 8px;  
            overflow-x: auto;  
            padding-bottom: 6px;  
            margin-bottom: 14px;  
            scrollbar-width: none;  
        }  
        .nav-tabs::-webkit-scrollbar { display: none; }  
        .tab-btn {  
            background-color: rgba(30, 41, 59, 0.6);  
            color: var(--text-sub);  
            border: 1px solid rgba(255,255,255,0.08);  
            padding: 8px 14px;  
            border-radius: 20px;  
            font-size: 0.8rem;  
            font-weight: 600;  
            white-space: nowrap;  
            cursor: pointer;  
            transition: all 0.2s;  
        }  
        .tab-btn.active {  
            background: var(--accent-gradient);  
            color: white;  
            border-color: transparent;  
            box-shadow: 0 4px 12px rgba(168, 85, 247, 0.3);  
        }  
  
        /* Card Grid Layout */  
        .card-grid {  
            display: grid;  
            grid-template-columns: 1fr;  
            gap: 12px;  
        }  
        @media(min-width: 600px) {  
            .card-grid { grid-template-columns: repeat(2, 1fr); }  
        }  
        .card-item {  
            background: rgba(30, 41, 59, 0.65);  
            border: 1px solid var(--card-border);  
            border-radius: 16px;  
            padding: 12px;  
            display: flex;  
            flex-direction: column;  
            justify-content: space-between;  
            backdrop-filter: blur(10px);  
            box-shadow: 0 4px 16px rgba(0,0,0,0.25);  
        }  
        .card-top {  
            display: flex;  
            gap: 12px;  
            align-items: flex-start;  
            margin-bottom: 10px;  
        }  
        .card-photo {  
            width: 72px;  
            height: 98px;  
            border-radius: 10px;  
            object-fit: cover;  
            border: 1px solid rgba(255,255,255,0.2);  
            background-color: #0f172a;  
            flex-shrink: 0;  
            cursor: pointer;  
            box-shadow: 0 4px 8px rgba(0,0,0,0.4);  
        }  
        .card-info { flex-grow: 1; }  
        .card-header-row {  
            display: flex;  
            justify-content: space-between;  
            align-items: flex-start;  
            margin-bottom: 6px;  
        }  
        .card-name {  
            font-size: 0.95rem;  
            font-weight: 700;  
            color: #f3e8ff;  
        }  
        .card-type {  
            font-size: 0.6rem;  
            text-transform: uppercase;  
            padding: 3px 7px;  
            border-radius: 6px;  
            font-weight: 800;  
            letter-spacing: 0.5px;  
        }  
        .type-bebe { background-color: #f472b6; color: #fff; }  
        .type-basico { background-color: #60a5fa; color: #fff; }  
        .type-magico { background-color: #a78bfa; color: #fff; }  
        .type-mejora { background-color: #34d399; color: #fff; }  
        .type-deterioro { background-color: #f87171; color: #fff; }  
        .type-magica { background-color: #fbbf24; color: #000; }  
        .type-instantanea { background-color: #fb7185; color: #fff; }  
  
        .card-desc {  
            font-size: 0.8rem;  
            color: var(--text-sub);  
            line-height: 1.35;  
        }  
        .add-btn {  
            background: var(--accent-gradient);  
            color: white;  
            border: none;  
            padding: 10px;  
            border-radius: 10px;  
            font-size: 0.85rem;  
            font-weight: 700;  
            cursor: pointer;  
            width: 100%;  
            box-shadow: 0 4px 12px rgba(168, 85, 247, 0.25);  
            transition: opacity 0.2s;  
        }  
        .add-btn:active { opacity: 0.85; }  
  
        /* Floating Horizontal Swipable Hand Drawer */  
        .hand-container {  
            position: fixed;  
            bottom: 0;  
            left: 0;  
            right: 0;  
            background: rgba(11, 15, 25, 0.94);  
            border-top: 2px solid var(--accent-glow);  
            padding: 12px 14px 16px 14px;  
            box-shadow: 0 -10px 30px rgba(0, 0, 0, 0.95);  
            backdrop-filter: blur(16px);  
            -webkit-backdrop-filter: blur(16px);  
            z-index: 900;  
        }  
        .hand-header {  
            display: flex;  
            justify-content: space-between;  
            align-items: center;  
            margin-bottom: 10px;  
        }  
        .hand-header h3 {  
            font-size: 1rem;  
            color: #c084fc;  
            display: flex;  
            align-items: center;  
            gap: 6px;  
        }  
        .hand-scroll-wrapper {  
            display: flex;  
            gap: 12px;  
            overflow-x: auto;  
            scroll-snap-type: x mandatory;  
            padding-bottom: 8px;  
            scrollbar-width: thin;  
            scrollbar-color: var(--accent-btn) transparent;  
        }  
        .hand-scroll-wrapper::-webkit-scrollbar {  
            height: 6px;  
        }  
        .hand-scroll-wrapper::-webkit-scrollbar-thumb {  
            background: var(--accent-btn);  
            border-radius: 10px;  
        }  
        .hand-card-swipe {  
            min-width: 240px;  
            max-width: 260px;  
            scroll-snap-align: center;  
            background: #1e293b;  
            border: 1px solid var(--card-border);  
            border-radius: 16px;  
            padding: 12px;  
            display: flex;  
            gap: 12px;  
            align-items: flex-start;  
            box-shadow: 0 6px 16px rgba(0,0,0,0.5);  
            position: relative;  
            flex-shrink: 0;  
        }  
        .hand-swipe-thumb {  
            width: 70px;  
            height: 95px;  
            border-radius: 8px;  
            object-fit: cover;  
            border: 1px solid rgba(255,255,255,0.25);  
            flex-shrink: 0;  
            background-color: #0f172a;  
        }  
        .hand-swipe-info {  
            flex-grow: 1;  
        }  
        .hand-swipe-title {  
            font-size: 0.9rem;  
            font-weight: 700;  
            color: #f3e8ff;  
            margin-bottom: 4px;  
        }  
        .hand-swipe-desc {  
            font-size: 0.75rem;  
            color: #cbd5e1;  
            line-height: 1.3;  
            max-height: 60px;  
            overflow-y: auto;  
        }  
        .remove-card-btn {  
            position: absolute;  
            top: 6px;  
            right: 8px;  
            background: rgba(239, 68, 68, 0.2);  
            color: #ef4444;  
            border: none;  
            width: 24px;  
            height: 24px;  
            border-radius: 50%;  
            font-size: 1rem;  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            cursor: pointer;  
        }  
  
        .empty-hand-msg {  
            color: var(--text-sub);  
            font-size: 0.85rem;  
            text-align: center;  
            width: 100%;  
            padding: 16px 0;  
        }  
  
        /* Modal styling */  
        .modal {  
            display: none;  
            position: fixed;  
            top: 0; left: 0; right: 0; bottom: 0;  
            background-color: rgba(0,0,0,0.85);  
            z-index: 1000;  
            justify-content: center;  
            align-items: center;  
            padding: 16px;  
            backdrop-filter: blur(6px);  
        }  
        .modal-content {  
            background-color: #1e293b;  
            border: 1px solid var(--card-border);  
            border-radius: 18px;  
            padding: 20px;  
            width: 100%;  
            max-width: 400px;  
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);  
        }  
        .modal-content h2 {  
            font-size: 1.1rem;  
            color: #c084fc;  
            margin-bottom: 12px;  
        }  
        .form-group { margin-bottom: 12px; }  
        .form-group label {  
            display: block;  
            font-size: 0.8rem;  
            color: var(--text-sub);  
            margin-bottom: 4px;  
        }  
        .form-group input, .form-group select, .form-group textarea {  
            width: 100%;  
            padding: 10px;  
            background-color: #0f172a;  
            border: 1px solid var(--card-border);  
            border-radius: 8px;  
            color: white;  
            font-size: 0.9rem;  
        }  
        .form-group textarea { resize: vertical; height: 70px; }  
        .modal-buttons {  
            display: flex;  
            gap: 8px;  
            margin-top: 16px;  
        }  
        .btn-cancel {  
            background-color: #334155;  
            color: white;  
            border: none;  
            padding: 10px;  
            border-radius: 8px;  
            flex: 1;  
            font-weight: bold;  
            cursor: pointer;  
        }  
        .btn-save {  
            background: var(--accent-gradient);  
            color: white;  
            border: none;  
            padding: 10px;  
            border-radius: 8px;  
            flex: 1;  
            font-weight: bold;  
            cursor: pointer;  
        }  
    </style>  
</head>  
<body>  
  
    <!-- Launcher Header -->  
    <div class="app-launcher">  
        <div class="launcher-title">  
            <span>🦄</span>  
            <h1>Unstable Unicorns</h1>  
        </div>  
        <button class="menu-trigger-btn" onclick="toggleLauncherDrawer()">  
            <span>⚡ Menú Launcher</span>  
        </button>  
    </div>  
  
    <!-- Quick Launcher Drawer -->  
    <div class="quick-drawer" id="quickDrawer">  
        <button class="drawer-btn" onclick="abrirModalCrear(); toggleLauncherDrawer();">➕ Añadir Carta Personalizada</button>  
        <button class="drawer-btn" onclick="exportarDatos(); toggleLauncherDrawer();">📥 Guardar / Exportar Copia JSON</button>  
        <button class="drawer-btn danger" onclick="restaurarPorDefecto(); toggleLauncherDrawer();">🔄 Restaurar Baraja por Defecto</button>  
    </div>  
  
    <input type="text" id="searchInput" class="search-box" placeholder="🔍 Buscar por nombre o efecto..." oninput="filtrarCartas()">  
  
    <div class="nav-tabs" id="categoryTabs">  
        <button class="tab-btn active" onclick="cambiarCategoria('todos', event)">🌟 Todas</button>  
        <button class="tab-btn" onclick="cambiarCategoria('deterioro', event)">⚡ Deterioro</button>  
        <button class="tab-btn" onclick="cambiarCategoria('mejora', event)">🛡️ Mejoras</button>  
        <button class="tab-btn" onclick="cambiarCategoria('magico', event)">🦄 Mágicos</button>  
        <button class="tab-btn" onclick="cambiarCategoria('magica', event)">🔮 Mágicas</button>  
        <button class="tab-btn" onclick="cambiarCategoria('bebe', event)">👶 Bebés</button>  
        <button class="tab-btn" onclick="cambiarCategoria('basico', event)">🐴 Básicos</button>  
        <button class="tab-btn" onclick="cambiarCategoria('instantanea', event)">🛑 Instantáneas</button>  
    </div>  
  
    <div id="cardsContainer" class="card-grid"></div>  
  
    <!-- Swipable Horizontal Hand Slider -->  
    <div class="hand-container" id="handContainer">  
        <div class="hand-header">  
            <h3>✋ Mi Mano (<span id="handCount">0</span> cartas) <span style="font-size:0.75rem; color:var(--text-sub); font-weight:normal;">(Desliza horizontalmente ↔️)</span></h3>  
        </div>  
        <div class="hand-scroll-wrapper" id="handContent">  
            <p class="empty-hand-msg">No tienes cartas en la mano. Presiona "+ Añadir a mano".</p>  
        </div>  
    </div>  
  
    <!-- Modal Añadir / Editar Carta -->  
    <div class="modal" id="modalCarta">  
        <div class="modal-content">  
            <h2 id="modalTitle">Añadir Carta Nueva</h2>  
            <div class="form-group">  
                <label>Nombre de la carta</label>  
                <input type="text" id="inputNombre" placeholder="Ej. Súper Unicornio">  
            </div>  
            <div class="form-group">  
                <label>Tipo de carta</label>  
                <select id="inputTipo">  
                    <option value="magico">Unicornio Mágico</option>  
                    <option value="mejora">Mejora</option>  
                    <option value="deterioro">Deterioro</option>  
                    <option value="magica">Mágica</option>  
                    <option value="instantanea">Instantánea</option>  
                    <option value="bebe">Bebé</option>  
                    <option value="basico">Básico</option>  
                </select>  
            </div>  
            <div class="form-group">  
                <label>Descripción / Efecto</label>  
                <textarea id="inputDesc" placeholder="Escribe lo que hace la carta..."></textarea>  
            </div>  
            <div class="form-group">  
                <label>Foto de la Portada (Archivo o URL)</label>  
                <input type="file" id="inputFile" accept="image/*" onchange="cargarImagenLocal(event)">  
                <input type="text" id="inputFoto" placeholder="O pega un enlace de imagen aquí" style="margin-top: 6px;">  
            </div>  
            <div class="modal-buttons">  
                <button class="btn-cancel" onclick="cerrarModal()">Cancelar</button>  
                <button class="btn-save" onclick="guardarCartaNueva()">Guardar</button>  
            </div>  
        </div>  
    </div>  
  
    <script>  
        const CARTAS_DEFAULT = [  
            { id: 1, name: "Establo Pequeño", type: "deterioro", typeName: "Deterioro", photo: "https://images.unsplash.com/photo-1563089145-599997674d42?w=300", desc: "Mientras esté en tu Establo, solo puedes tener 5 Unicornios." },  
            { id: 2, name: "Ritual Sádico", type: "deterioro", typeName: "Deterioro", photo: "https://images.unsplash.com/photo-1518709268805-4e9042af9f23?w=300", desc: "Al comienzo de tu turno, SACRIFICA un Unicornio, luego ROBA una carta extra." },  
            { id: 9, name: "Doble Comba", type: "mejora", typeName: "Mejora", photo: "https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=300", desc: "Al comienzo de tu turno, puedes jugar dos cartas en vez de una." },  
            { id: 16, name: "Unicornio Angelical", type: "magico", typeName: "Unicornio Mágico", photo: "https://images.unsplash.com/photo-1534447677768-be436bb09401?w=300", desc: "Sacrifícalo para traer un Unicornio del descarte a tu Establo." },  
            { id: 32, name: "Intercambio de Unicornios", type: "magica", typeName: "Mágica", photo: "https://images.unsplash.com/photo-1579546929518-9e396f3cc809?w=300", desc: "Intercambia todas las cartas de tu mano por las de un rival." },  
            { id: 46, name: "Relinchar (Neigh)", type: "instantanea", typeName: "Instantánea", photo: "https://images.unsplash.com/photo-1550684848-fac1c5b4e853?w=300", desc: "Úsalo cuando alguien juegue una carta para evitar que entre en juego." }  
        ];  
  
        let cartas = [];  
        try {  
            const guardadas = localStorage.getItem('uu_cartas');  
            if (guardadas) cartas = JSON.parse(guardadas);  
        } catch(e) { cartas = []; }  
  
        if (!Array.isArray(cartas) || cartas.length === 0) {  
            cartas = [...CARTAS_DEFAULT];  
            guardarEnStorage('uu_cartas', cartas);  
        }  
  
        let miMano = [];  
        try {  
            const manoGuardada = localStorage.getItem('uu_mano');  
            if (manoGuardada) miMano = JSON.parse(manoGuardada);  
        } catch(e) { miMano = []; }  
  
        let fotoTemporal = "";  
        let editandoId = null;  
        let categoriaActual = 'todos';  
  
        const tiposMap = {  
            deterioro: "Deterioro",  
            mejora: "Mejora",  
            magico: "Unicornio Mágico",  
            magica: "Mágica",  
            instantanea: "Instantánea",  
            bebe: "Bebé",  
            basico: "Básico"  
        };  
  
        function guardarEnStorage(key, value) {  
            try { localStorage.setItem(key, JSON.stringify(value)); }   
            catch (e) { console.warn("Memoria llena", e); }  
        }  
  
        function toggleLauncherDrawer() {  
            const drawer = document.getElementById('quickDrawer');  
            drawer.style.display = drawer.style.display === 'flex' ? 'none' : 'flex';  
        }  
  
        function renderizarCartas(filtro = '') {  
            const container = document.getElementById('cardsContainer');  
            if (!container) return;  
            container.innerHTML = '';  
  
            const filtradas = cartas.filter(c => {  
                const matchCat = categoriaActual === 'todos' || c.type === categoriaActual;  
                const matchText = c.name.toLowerCase().includes(filtro.toLowerCase()) || (c.desc && c.desc.toLowerCase().includes(filtro.toLowerCase()));  
                return matchCat && matchText;  
            });  
  
            if (filtradas.length === 0) {  
                container.innerHTML = `<p style="text-align:center; color: var(--text-sub); grid-column: 1/-1; padding: 20px;">No se encontraron cartas.</p>`;  
                return;  
            }  
  
            filtradas.forEach(c => {  
                const div = document.createElement('div');  
                div.className = 'card-item';  
                div.innerHTML = `  
                    <div>  
                        <div class="card-top">  
                            <img src="${c.photo || 'https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=300'}" class="card-photo" onclick="abrirEditorFoto(${c.id})" title="Toca para cambiar portada">  
                            <div class="card-info">  
                                <div class="card-header-row">  
                                    <span class="card-name">${escapeHtml(c.name)}</span>  
                                    <span class="card-type type-${c.type}">${c.typeName || tiposMap[c.type] || 'Carta'}</span>  
                                </div>  
                                <p class="card-desc">${escapeHtml(c.desc || '')}</p>  
                            </div>  
                        </div>  
                    </div>  
                    <button class="add-btn" onclick="agregarAMano(${c.id})">+ Añadir a mano</button>  
                `;  
                container.appendChild(div);  
            });  
        }  
  
        function cambiarCategoria(cat, ev) {  
            categoriaActual = cat;  
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));  
            if (ev && ev.target) ev.target.classList.add('active');  
            renderizarCartas(document.getElementById('searchInput').value);  
        }  
  
        function filtrarCartas() {  
            renderizarCartas(document.getElementById('searchInput').value);  
        }  
  
        function abrirModalCrear() {  
            editandoId = null;  
            document.getElementById('modalTitle').textContent = "Añadir Carta Nueva";  
            document.getElementById('inputNombre').value = "";  
            document.getElementById('inputDesc').value = "";  
            document.getElementById('inputFoto').value = "";  
            document.getElementById('inputFile').value = "";  
            fotoTemporal = "";  
            document.getElementById('modalCarta').style.display = 'flex';  
        }  
  
        function abrirEditorFoto(id) {  
            const carta = cartas.find(c => c.id === id);  
            if (!carta) return;  
            editandoId = id;  
            document.getElementById('modalTitle').textContent = `Editar Carta: ${carta.name}`;  
            document.getElementById('inputNombre').value = carta.name;  
            document.getElementById('inputTipo').value = carta.type;  
            document.getElementById('inputDesc').value = carta.desc || "";  
            document.getElementById('inputFoto').value = carta.photo || "";  
            fotoTemporal = carta.photo || "";  
            document.getElementById('modalCarta').style.display = 'flex';  
        }  
  
        function cerrarModal() {  
            document.getElementById('modalCarta').style.display = 'none';  
        }  
  
        function cargarImagenLocal(event) {  
            const file = event.target.files[0];  
            if (file) {  
                const img = new Image();  
                const reader = new FileReader();  
                reader.onload = function(e) {  
                    img.src = e.target.result;  
                    img.onload = function() {  
                        const canvas = document.createElement('canvas');  
                        const ctx = canvas.getContext('2d');  
                        const maxWidth = 300;  
                        const scaleSize = maxWidth / img.width;  
                        canvas.width = maxWidth;  
                        canvas.height = img.height * scaleSize;  
                        ctx.drawImage(img, 0, 0, canvas.width, canvas.height);  
                        fotoTemporal = canvas.toDataURL('image/jpeg', 0.7);  
                        document.getElementById('inputFoto').value = "[Imagen cargada correctamente]";  
                    };  
                };  
                reader.readAsDataURL(file);  
            }  
        }  
  
        function guardarCartaNueva() {  
            const nombre = document.getElementById('inputNombre').value.trim();  
            const tipo = document.getElementById('inputTipo').value;  
            const desc = document.getElementById('inputDesc').value.trim();  
            const fotoUrl = document.getElementById('inputFoto').value.trim();  
  
            if (!nombre) {  
                alert("Por favor ingresa el nombre de la carta.");  
                return;  
            }  
  
            let fotoFinal = fotoTemporal;  
            if (!fotoFinal) {  
                if (fotoUrl && !fotoUrl.startsWith('[')) {  
                    fotoFinal = fotoUrl;  
                } else {  
                    fotoFinal = 'https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=300';  
                }  
            }  
  
            if (editandoId !== null) {  
                const index = cartas.findIndex(c => c.id === editandoId);  
                if (index !== -1) {  
                    cartas[index].name = nombre;  
                    cartas[index].type = tipo;  
                    cartas[index].typeName = tiposMap[tipo];  
                    cartas[index].desc = desc;  
                    cartas[index].photo = fotoFinal;  
                }  
            } else {  
                const nueva = {  
                    id: Date.now(),  
                    name: nombre,  
                    type: tipo,  
                    typeName: tiposMap[tipo],  
                    photo: fotoFinal,  
                    desc: desc || "Sin descripción."  
                };  
                cartas.push(nueva);  
            }  
  
            guardarEnStorage('uu_cartas', cartas);  
            cerrarModal();  
            renderizarCartas(document.getElementById('searchInput').value);  
        }  
  
        function agregarAMano(idCarta) {  
            const carta = cartas.find(c => c.id === idCarta);  
            if (carta) {  
                miMano.push({ ...carta, instanceId: Date.now() + Math.random() });  
                guardarEnStorage('uu_mano', miMano);  
                actualizarManoUI();  
            }  
        }  
  
        function quitarDeMano(instanceId) {  
            miMano = miMano.filter(item => item.instanceId !== instanceId);  
            guardarEnStorage('uu_mano', miMano);  
            actualizarManoUI();  
        }  
  
        function actualizarManoUI() {  
            const countElem = document.getElementById('handCount');  
            if (countElem) countElem.textContent = miMano.length;  
              
            const handContent = document.getElementById('handContent');  
            if (!handContent) return;  
  
            if (miMano.length === 0) {  
                handContent.innerHTML = `<p class="empty-hand-msg">No tienes cartas en la mano. Presiona "+ Añadir a mano".</p>`;  
                return;  
            }  
  
            let html = '';  
            miMano.forEach(item => {  
                html += `  
                    <div class="hand-card-swipe">  
                        <button class="remove-card-btn" onclick="quitarDeMano(${item.instanceId})" title="Quitar de mano">&times;</button>  
                        <img src="${item.photo || 'https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=300'}" class="hand-swipe-thumb">  
                        <div class="hand-swipe-info">  
                            <div class="hand-swipe-title">${escapeHtml(item.name)}</div>  
                            <div class="hand-swipe-desc">${escapeHtml(item.desc || '')}</div>  
                        </div>  
                    </div>  
                `;  
            });  
            handContent.innerHTML = html;  
        }  
  
        function restaurarPorDefecto() {  
            if (confirm("¿Quieres restaurar la lista de cartas por defecto?")) {  
                cartas = [...CARTAS_DEFAULT];  
                miMano = [];  
                guardarEnStorage('uu_cartas', cartas);  
                guardarEnStorage('uu_mano', miMano);  
                renderizarCartas();  
                actualizarManoUI();  
            }  
        }  
  
        function exportarDatos() {  
            const datos = { cartas, mano: miMano };  
            const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(datos));  
            const downloadAnchor = document.createElement('a');  
            downloadAnchor.setAttribute("href", dataStr);  
            downloadAnchor.setAttribute("download", "unstable_unicorns_backup.json");  
            document.body.appendChild(downloadAnchor);  
            downloadAnchor.click();  
            downloadAnchor.remove();  
        }  
  
        function escapeHtml(str) {  
            return String(str).replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');  
        }  
  
        renderizarCartas();  
        actualizarManoUI();  
    </script>  
</body>  
</html>  
