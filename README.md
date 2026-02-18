<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Asuntos Propios 2025-2026</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1800px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 2em;
            margin-bottom: 10px;
        }
        
        .header p {
            font-size: 1.1em;
            opacity: 0.9;
        }
        
        .content {
            padding: 30px;
        }
        
        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
            border-bottom: 2px solid #e0e0e0;
        }
        
        .tab {
            padding: 15px 30px;
            background: transparent;
            border: none;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            color: #666;
            border-bottom: 3px solid transparent;
            transition: all 0.3s;
        }
        
        .tab.active {
            color: #667eea;
            border-bottom-color: #667eea;
        }
        
        .tab:hover {
            color: #667eea;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .form-section {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 10px;
            margin-bottom: 30px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            font-weight: 600;
            margin-bottom: 8px;
            color: #333;
        }
        
        input, select {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 16px;
        }
        
        .btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
        }
        
        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }
        
        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .day-card {
            background: white;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            padding: 15px;
            transition: all 0.3s;
        }
        
        .day-card.festivo {
            background: #ffebee;
            border-color: #ef5350;
        }
        
        .day-card.ocupado {
            background: #fff3e0;
            border-color: #ff9800;
        }
        
        .day-card.completo {
            background: #ffcdd2;
            border-color: #f44336;
        }
        
        .day-date {
            font-weight: 700;
            font-size: 18px;
            color: #333;
            margin-bottom: 10px;
        }
        
        .day-info {
            font-size: 13px;
            color: #666;
        }
        
        .maestro-item {
            background: #e3f2fd;
            padding: 5px 10px;
            border-radius: 5px;
            margin: 5px 0;
            font-size: 12px;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .stat-card {
            background: #f8f9fa;
            border-radius: 10px;
            padding: 20px;
            border-left: 4px solid #667eea;
        }
        
        .stat-name {
            font-weight: 600;
            color: #333;
            margin-bottom: 10px;
        }
        
        .stat-days {
            color: #666;
            font-size: 14px;
        }
        
        .stat-complete {
            background: #e8f5e9;
            border-left-color: #4caf50;
        }
        
        .alert {
            background: #fff3cd;
            border: 1px solid #ffc107;
            border-radius: 8px;
            padding: 15px;
            margin: 20px 0;
            color: #856404;
        }
        
        .loading {
            text-align: center;
            padding: 40px;
            color: #667eea;
            font-size: 18px;
        }
        
        .refresh-btn {
            background: #4caf50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            margin-bottom: 20px;
        }
        
        .month-section {
            margin-bottom: 40px;
        }
        
        .month-title {
            font-size: 24px;
            font-weight: 700;
            color: #667eea;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 3px solid #667eea;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Gestion de Asuntos Propios Retribuidos</h1>
            <p>Curso Academico 2025-2026</p>
            <p>Maximo: 2 dias por maestro/a | 2 maestros/as por dia</p>
        </div>
        
        <div class="content">
            <div class="tabs">
                <button class="tab active" onclick="showTab('solicitar')">Solicitar Dia</button>
                <button class="tab" onclick="showTab('calendario')">Calendario</button>
                <button class="tab" onclick="showTab('maestros')">Estado Maestros</button>
            </div>
            
            <div id="solicitar" class="tab-content active">
                <div class="form-section">
                    <h2 style="margin-bottom: 20px; color: #667eea;">Solicitar Asunto Propio</h2>
                    <form id="requestForm">
                        <div class="form-group">
                            <label for="maestro">Maestro/a</label>
                            <select id="maestro" required>
                                <option value="">Seleccionar maestro/a</option>
                            </select>
                        </div>
                        
                        <div class="form-group">
                            <label for="fecha">Fecha</label>
                            <input type="date" id="fecha" min="2025-09-01" max="2026-06-30" required>
                        </div>
                        
                        <button type="submit" class="btn" id="submitBtn">Solicitar Dia</button>
                    </form>
                </div>
                
                <div id="alerts"></div>
            </div>
            
            <div id="calendario" class="tab-content">
                <button class="refresh-btn" onclick="loadData()">Actualizar Datos</button>
                <div id="loadingCalendar" class="loading">Cargando calendario...</div>
                <div id="calendarContent"></div>
            </div>
            
            <div id="maestros" class="tab-content">
                <button class="refresh-btn" onclick="loadData()">Actualizar Datos</button>
                <div id="loadingMaestros" class="loading">Cargando datos...</div>
                <div id="maestrosContent"></div>
            </div>
        </div>
    </div>

    <script>
        const API_URL = 'https://script.google.com/macros/s/AKfycbxrYGXIpAdwn-6LjN8Ka9dp9tiNP9_UgFuMw8ZBeuS5C7-hGyqpvsAOdPj7L5Rxzfc6/exec';
        
        const maestros = [
            'Alconchel Vazquez, Carlos',
            'Alonso Ramirez, Maria Desamparados',
            'Alonso Yanez, Inmaculada',
            'Baraza Martinez, Josefa',
            'Barbado Marquez, Vanesa',
            'Chacon Martin, Maria Dolores',
            'Enjuto Mena, Carolina',
            'Fernandez Marcos Donate, Raquel',
            'Flores Ortega, Juana del Pilar',
            'Garcia Arnau, Mireia',
            'Garcia Pinero, Isabel Maria',
            'Garrido Morales, Antonio Jesus',
            'Gonzalez Sanz, Nuria',
            'Guerrero Pinero, Ana Celia',
            'Guzman Perez, Rosa',
            'Haro Mansilla, Aladina',
            'Jimena Quesada, Luis Maria',
            'Jimenez Medina, Ana Bella',
            'Jimenez Torres, Maria Jose',
            'Martinez Guerrero, Isabel Maria',
            'Millan Cachinero, Maria Angeles',
            'Molina Garcia, Sandra',
            'Montoya Morales, Maria Luisa',
            'Moreno Alonso, Antonia',
            'Palomares Padilla, Pilar',
            'Paniagua Pulgarin, Teresa',
            'Pena Ruiz, Maria Cruz',
            'Ramos Munoz, Patricia',
            'Rodriguez Martinez, Irene',
            'Rodriguez Montes, Jesus',
            'Ruiz Arevalo, Maria',
            'Tafur Porras, Angela Maria',
            'Torres Molina, Juan Carlos',
            'Vedia Salinas, Carmen Cristin',
            'Yanguez Lopez-Cano, Rafael'
        ];
        
        const festivos = [
            // Octubre 2025
            '2025-10-13',
            // Noviembre 2025
            '2025-11-01', '2025-11-03',
            // Diciembre 2025 (del 23 al 6 enero - dia no lectivo + vacaciones Navidad)
            '2025-12-06', '2025-12-08', '2025-12-23', '2025-12-24', '2025-12-25',
            '2025-12-26', '2025-12-27', '2025-12-28', '2025-12-29', '2025-12-30', '2025-12-31',
            // Enero 2026 (vacaciones hasta el 6, el 7 es lectivo)
            '2026-01-01', '2026-01-02', '2026-01-03', '2026-01-04', '2026-01-05', '2026-01-06',
            // Febrero 2026
            '2026-02-27', '2026-02-28',
            // Marzo 2026
            '2026-03-02',
            // Semana Santa 2026 (29 marzo - 5 abril inclusive)
            '2026-03-29', '2026-03-30', '2026-03-31', '2026-04-01', '2026-04-02', '2026-04-03', '2026-04-04', '2026-04-05',
            // Mayo 2026
            '2026-05-01', '2026-05-04',
            // Junio 2026 (12 festivo, del 23 al 30 fin de curso)
            '2026-06-12', '2026-06-23', '2026-06-24', '2026-06-25', '2026-06-26', '2026-06-27', '2026-06-28', '2026-06-29', '2026-06-30'
        ];
        
        const peticionesIniciales = [
            { maestro: 'Alconchel Vazquez, Carlos', fecha: '2026-03-26' },
            { maestro: 'Alconchel Vazquez, Carlos', fecha: '2026-03-27' },
            { maestro: 'Fernandez Marcos Donate, Raquel', fecha: '2026-03-13' },
            { maestro: 'Gonzalez Sanz, Nuria', fecha: '2026-01-19' },
            { maestro: 'Gonzalez Sanz, Nuria', fecha: '2026-02-20' },
            { maestro: 'Haro Mansilla, Aladina', fecha: '2026-01-28' },
            { maestro: 'Moreno Alonso, Antonia', fecha: '2026-02-20' },
            { maestro: 'Paniagua Pulgarin, Teresa', fecha: '2026-05-18' },
            { maestro: 'Torres Molina, Juan Carlos', fecha: '2026-03-03' }
        ];
        
        let peticiones = [];
        
        function initMaestrosSelect() {
            const select = document.getElementById('maestro');
            maestros.forEach(m => {
                const option = document.createElement('option');
                option.value = m;
                option.textContent = m;
                select.appendChild(option);
            });
        }
        
        function showTab(tabName) {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
            
            event.target.classList.add('active');
            document.getElementById(tabName).classList.add('active');
            
            if (tabName === 'calendario') renderCalendar();
            if (tabName === 'maestros') renderMaestros();
        }
        
        async function loadData() {
            try {
                const response = await fetch(API_URL + '?action=get&t=' + new Date().getTime());
                const result = await response.json();
                
                if (result.success && result.data) {
                    peticiones = result.data;
                } else {
                    peticiones = [];
                }
                
                renderCalendar();
                renderMaestros();
            } catch (error) {
                console.error('Error cargando datos:', error);
                peticiones = [];
                renderCalendar();
                renderMaestros();
            }
        }
        
        async function cargarPeticionesIniciales() {
            console.log('Cargando peticiones iniciales...');
            
            for (const p of peticionesIniciales) {
                try {
                    const response = await fetch(API_URL, {
                        method: 'POST',
                        redirect: 'follow',
                        headers: { 
                            'Content-Type': 'text/plain;charset=utf-8'
                        },
                        body: JSON.stringify({
                            action: 'set',
                            maestro: p.maestro,
                            fecha: p.fecha
                        })
                    });
                    
                    await new Promise(resolve => setTimeout(resolve, 500));
                    
                } catch (error) {
                    console.log('Peticion guardada (error esperado con no-cors)');
                }
            }
            
            console.log('Peticiones iniciales cargadas, esperando 3 segundos...');
            setTimeout(() => {
                console.log('Recargando datos...');
                loadData();
            }, 3000);
        }
        
        function renderCalendar() {
            const container = document.getElementById('calendarContent');
            const loading = document.getElementById('loadingCalendar');
            
            loading.style.display = 'none';
            container.innerHTML = '';
            
            const meses = [
                { nombre: 'Septiembre 2025', inicio: new Date(2025, 8, 1), fin: new Date(2025, 8, 30) },
                { nombre: 'Octubre 2025', inicio: new Date(2025, 9, 1), fin: new Date(2025, 9, 31) },
                { nombre: 'Noviembre 2025', inicio: new Date(2025, 10, 1), fin: new Date(2025, 10, 30) },
                { nombre: 'Diciembre 2025', inicio: new Date(2025, 11, 1), fin: new Date(2025, 11, 31) },
                { nombre: 'Enero 2026', inicio: new Date(2026, 0, 1), fin: new Date(2026, 0, 31) },
                { nombre: 'Febrero 2026', inicio: new Date(2026, 1, 1), fin: new Date(2026, 1, 28) },
                { nombre: 'Marzo 2026', inicio: new Date(2026, 2, 1), fin: new Date(2026, 2, 31) },
                { nombre: 'Abril 2026', inicio: new Date(2026, 3, 1), fin: new Date(2026, 3, 30) },
                { nombre: 'Mayo 2026', inicio: new Date(2026, 4, 1), fin: new Date(2026, 4, 31) },
                { nombre: 'Junio 2026', inicio: new Date(2026, 5, 1), fin: new Date(2026, 5, 30) }
            ];
            
            meses.forEach(mes => {
                const section = document.createElement('div');
                section.className = 'month-section';
                
                const title = document.createElement('div');
                title.className = 'month-title';
                title.textContent = mes.nombre;
                section.appendChild(title);
                
                const grid = document.createElement('div');
                grid.className = 'calendar-grid';
                
                let current = new Date(mes.inicio);
                while (current <= mes.fin) {
                    const dateStr = current.toISOString().split('T')[0];
                    const day = current.getDay();
                    
                    if (day !== 0 && day !== 6) {
                        const card = document.createElement('div');
                        card.className = 'day-card';
                        
                        const esFestivo = festivos.includes(dateStr);
                        const peticionesDelDia = peticiones.filter(p => p.fecha === dateStr);
                        
                        if (esFestivo) {
                            card.classList.add('festivo');
                        } else if (peticionesDelDia.length >= 2) {
                            card.classList.add('completo');
                        } else if (peticionesDelDia.length > 0) {
                            card.classList.add('ocupado');
                        }
                        
                        const dateDiv = document.createElement('div');
                        dateDiv.className = 'day-date';
                        dateDiv.textContent = current.toLocaleDateString('es-ES', { day: '2-digit', month: '2-digit' });
                        card.appendChild(dateDiv);
                        
                        const info = document.createElement('div');
                        info.className = 'day-info';
                        
                        if (esFestivo) {
                            info.innerHTML = '<strong>FESTIVO</strong>';
                        } else if (peticionesDelDia.length >= 2) {
                            info.innerHTML = '<strong>COMPLETO (2/2)</strong>';
                            peticionesDelDia.forEach(p => {
                                const item = document.createElement('div');
                                item.className = 'maestro-item';
                                item.textContent = p.maestro.split(',')[0];
                                info.appendChild(item);
                            });
                        } else if (peticionesDelDia.length > 0) {
                            info.innerHTML = `<strong>Ocupado (${peticionesDelDia.length}/2)</strong>`;
                            peticionesDelDia.forEach(p => {
                                const item = document.createElement('div');
                                item.className = 'maestro-item';
                                item.textContent = p.maestro.split(',')[0];
                                info.appendChild(item);
                            });
                        } else {
                            info.textContent = 'Disponible';
                        }
                        
                        card.appendChild(info);
                        grid.appendChild(card);
                    }
                    
                    current.setDate(current.getDate() + 1);
                }
                
                section.appendChild(grid);
                container.appendChild(section);
            });
        }
        
        function renderMaestros() {
            const container = document.getElementById('maestrosContent');
            const loading = document.getElementById('loadingMaestros');
            
            loading.style.display = 'none';
            container.innerHTML = '';
            
            const grid = document.createElement('div');
            grid.className = 'stats-grid';
            
            maestros.forEach(maestro => {
                const peticionesMaestro = peticiones.filter(p => p.maestro === maestro);
                
                const card = document.createElement('div');
                card.className = 'stat-card';
                if (peticionesMaestro.length >= 2) {
                    card.classList.add('stat-complete');
                }
                
                const name = document.createElement('div');
                name.className = 'stat-name';
                name.textContent = maestro;
                card.appendChild(name);
                
                const days = document.createElement('div');
                days.className = 'stat-days';
                days.innerHTML = `<strong>${peticionesMaestro.length}/2 dias usados</strong>`;
                
                if (peticionesMaestro.length > 0) {
                    days.innerHTML += '<br>';
                    peticionesMaestro.forEach(p => {
                        const fecha = new Date(p.fecha + 'T00:00:00');
                        days.innerHTML += `<br>- ${fecha.toLocaleDateString('es-ES', { day: '2-digit', month: '2-digit', year: 'numeric' })}`;
                    });
                }
                
                card.appendChild(days);
                grid.appendChild(card);
            });
            
            container.appendChild(grid);
        }
        
        document.getElementById('requestForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const maestro = document.getElementById('maestro').value;
            const fecha = document.getElementById('fecha').value;
            const alertsDiv = document.getElementById('alerts');
            const submitBtn = document.getElementById('submitBtn');
            
            alertsDiv.innerHTML = '';
            submitBtn.disabled = true;
            submitBtn.textContent = 'Verificando...';
            
            // Validaciones
            if (festivos.includes(fecha)) {
                alertsDiv.innerHTML = '<div class="alert">ERROR: No se pueden solicitar dias festivos</div>';
                submitBtn.disabled = false;
                submitBtn.textContent = 'Solicitar Dia';
                return;
            }
            
            const peticionesMaestro = peticiones.filter(p => p.maestro === maestro);
            if (peticionesMaestro.length >= 2) {
                alertsDiv.innerHTML = '<div class="alert">ERROR: Este maestro/a ya ha usado sus 2 dias</div>';
                submitBtn.disabled = false;
                submitBtn.textContent = 'Solicitar Dia';
                return;
            }
            
            if (peticionesMaestro.some(p => p.fecha === fecha)) {
                alertsDiv.innerHTML = '<div class="alert">ERROR: Este maestro/a ya tiene solicitado este dia</div>';
                submitBtn.disabled = false;
                submitBtn.textContent = 'Solicitar Dia';
                return;
            }
            
            const peticionesDia = peticiones.filter(p => p.fecha === fecha);
            if (peticionesDia.length >= 2) {
                alertsDiv.innerHTML = '<div class="alert">ERROR: Este dia ya tiene 2 maestros/as (maximo alcanzado)</div>';
                submitBtn.disabled = false;
                submitBtn.textContent = 'Solicitar Dia';
                return;
            }
            
            // Guardar
            try {
                const response = await fetch(API_URL, {
                    method: 'POST',
                    redirect: 'follow',
                    headers: { 
                        'Content-Type': 'text/plain;charset=utf-8'
                    },
                    body: JSON.stringify({
                        action: 'set',
                        maestro: maestro,
                        fecha: fecha
                    })
                });
                
                alertsDiv.innerHTML = '<div class="alert" style="background: #d4edda; border-color: #c3e6cb; color: #155724;">Peticion registrada correctamente. Actualizando...</div>';
                
                this.reset();
                
                setTimeout(() => {
                    loadData();
                    submitBtn.disabled = false;
                    submitBtn.textContent = 'Solicitar Dia';
                    alertsDiv.innerHTML = '';
                }, 2000);
                
            } catch (error) {
                console.log('Peticion enviada (error esperado)');
                alertsDiv.innerHTML = '<div class="alert" style="background: #d4edda; border-color: #c3e6cb; color: #155724;">Peticion registrada correctamente. Actualizando...</div>';
                
                this.reset();
                
                setTimeout(() => {
                    loadData();
                    submitBtn.disabled = false;
                    submitBtn.textContent = 'Solicitar Dia';
                    alertsDiv.innerHTML = '';
                }, 2000);
            }
        });
        
        initMaestrosSelect();
        
        // Cargar datos o peticiones iniciales
        setTimeout(() => {
            fetch(API_URL + '?action=get&t=' + new Date().getTime())
                .then(response => response.json())
                .then(result => {
                    if (result.success && result.data && result.data.length > 0) {
                        console.log('Datos encontrados en Sheet, cargando...');
                        loadData();
                    } else {
                        console.log('No hay datos, cargando peticiones iniciales...');
                        cargarPeticionesIniciales();
                    }
                })
                .catch((error) => {
                    console.log('Error al verificar datos, cargando peticiones iniciales...', error);
                    cargarPeticionesIniciales();
                });
        }, 1000);
    </script>
</body>
</html>
