<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Gestão de Gerências</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f2f5;
        }
        .sidebar {
            transition: transform 0.3s ease-in-out;
        }
        .sidebar-open {
            transform: translateX(0);
        }
        .sidebar-closed {
            transform: translateX(-100%);
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
        .modal-backdrop {
            background-color: rgba(0,0,0,0.5);
            z-index: 40;
        }
        .modal {
            z-index: 50;
        }
         #app-container { display: none; }
    </style>
</head>
<body class="bg-gray-100">

    <!-- Auth Container -->
    <div id="auth-container" class="min-h-screen flex items-center justify-center bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
        <div class="max-w-md w-full space-y-8">
            <div>
                <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-900">
                    Diretoria de Inclusão
                </h2>
                <p class="mt-2 text-center text-sm text-gray-600">
                    Acesse sua conta para continuar
                </p>
            </div>
            <form id="login-form" class="mt-8 space-y-6">
                <div class="rounded-md shadow-sm -space-y-px">
                    <div>
                        <input id="login-email" name="email" type="email" autocomplete="email" required class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm" placeholder="Endereço de e-mail">
                    </div>
                    <div>
                        <input id="login-password" name="password" type="password" autocomplete="current-password" required class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm" placeholder="Senha">
                    </div>
                </div>
                <div>
                    <button type="submit" class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                        Entrar
                    </button>
                </div>
                 <p id="login-error" class="text-sm text-red-500 text-center"></p>
            </form>
            <div class="text-sm text-center">
                <a href="#" id="show-register" class="font-medium text-indigo-600 hover:text-indigo-500">
                    Não tem uma conta? Cadastre-se
                </a>
            </div>
        </div>
    </div>
    
     <!-- Register Container -->
    <div id="register-container" class="hidden min-h-screen flex items-center justify-center bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
        <div class="max-w-md w-full space-y-8">
            <div>
                <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-900">
                    Criar Nova Conta
                </h2>
            </div>
            <form id="register-form" class="mt-8 space-y-6">
                <div class="rounded-md shadow-sm">
                    <div>
                        <input id="register-email" name="email" type="email" required class="appearance-none rounded-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" placeholder="Endereço de e-mail">
                    </div>
                    <div class="mt-4">
                        <input id="register-password" name="password" type="password" required class="appearance-none rounded-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" placeholder="Senha (mínimo 6 caracteres)">
                    </div>
                </div>
                <div>
                    <button type="submit" class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                        Cadastrar
                    </button>
                </div>
                <p id="register-error" class="text-sm text-red-500 text-center"></p>
            </form>
            <div class="text-sm text-center">
                <a href="#" id="show-login" class="font-medium text-indigo-600 hover:text-indigo-500">
                    Já tem uma conta? Entre
                </a>
            </div>
        </div>
    </div>


    <!-- App Container -->
    <div id="app-container" class="flex h-screen overflow-hidden">
        <!-- Sidebar -->
        <aside id="sidebar" class="bg-gray-800 text-white w-64 space-y-6 py-7 px-2 absolute inset-y-0 left-0 transform md:relative md:translate-x-0 transition duration-200 ease-in-out sidebar-closed md:sidebar-open">
            <a href="#" class="text-white flex items-center space-x-2 px-4">
                <i class="fas fa-universal-access text-2xl"></i>
                <span class="text-xl font-extrabold">Diretoria de Inclusão</span>
            </a>
            <nav id="nav-gerencias">
                <!-- As gerências serão carregadas aqui pelo JS -->
            </nav>
            <div class="px-4 mt-6">
                <h3 class="text-xs font-semibold text-gray-400 uppercase tracking-wider">Recursos</h3>
                <a href="#" data-gerencia="documentos" class="gerencia-link flex items-center space-x-3 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 transition-colors duration-200 mt-2">
                    <i class="fas fa-file-alt w-6 text-center"></i>
                    <span>Documentos</span>
                </a>
            </div>
        </aside>

        <!-- Content -->
        <div class="flex-1 flex flex-col overflow-hidden">
            <header class="flex justify-between items-center p-4 bg-white border-b">
                <div class="flex items-center">
                    <button id="menu-button" class="text-gray-500 focus:outline-none md:hidden">
                        <i class="fas fa-bars text-2xl"></i>
                    </button>
                    <h1 id="header-title" class="text-2xl font-bold text-gray-800 ml-4">Bem-vindo!</h1>
                </div>
                <div class="flex items-center space-x-4">
                    <div class="text-sm text-right">
                        <p id="user-email" class="font-medium text-gray-700"></p>
                        <p id="user-role" class="text-xs text-gray-500 capitalize"></p>
                    </div>
                    <button id="logout-button" class="bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded-lg shadow-md transition-transform transform hover:scale-105">
                        <i class="fas fa-sign-out-alt"></i> Sair
                    </button>
                </div>
            </header>

            <main class="flex-1 overflow-x-hidden overflow-y-auto bg-gray-100 p-6">
                <div id="content-area" class="container mx-auto">
                    <!-- Conteúdo dinâmico será carregado aqui -->
                </div>
            </main>
        </div>
    </div>


    <!-- Modal Genérico -->
    <div id="modal" class="hidden fixed inset-0 w-full h-full modal-backdrop flex items-center justify-center">
        <div class="modal bg-white rounded-lg shadow-2xl w-11/12 md:w-1/2 lg:w-1/3 p-6 transform transition-all duration-300 ease-in-out scale-95 opacity-0">
            <div class="flex justify-between items-center border-b pb-3">
                <h3 id="modal-title" class="text-2xl font-bold text-gray-800"></h3>
                <button id="modal-close" class="text-gray-500 hover:text-gray-800">&times;</button>
            </div>
            <div id="modal-body" class="mt-4">
                <!-- Formulário do modal será injetado aqui -->
            </div>
        </div>
    </div>
    
    <!-- Bibliotecas de exportação -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.23/jspdf.plugin.autotable.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
    
    <!-- Módulo Firebase -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, onAuthStateChanged, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, setDoc, getDoc, onSnapshot, updateDoc, arrayUnion, arrayRemove, setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // --- CONFIGURAÇÃO E INICIALIZAÇÃO ---
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : { apiKey: "DEMO", authDomain: "DEMO", projectId: "DEMO" };
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        
        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);
        const auth = getAuth(app);

        const GERENCIAS_INFO = {
            'inclusao': { nome: 'Diretoria de Inclusão', icon: 'fa-universal-access' },
            'quilombola': { nome: 'Quilombola', icon: 'fa-landmark' },
            'indigena': { nome: 'Indígena', icon: 'fa-feather-alt' },
            'campo': { nome: 'Educação do Campo', icon: 'fa-tractor' },
            'ameei': { nome: 'AMEEI', icon: 'fa-hands-helping' },
            'multimidia': { nome: 'Multimídia', icon: 'fa-photo-video' },
            'documentos': { nome: 'Documentos', icon: 'fa-file-alt' }
        };

        const gerenciaIds = Object.keys(GERENCIAS_INFO).filter(g => g !== 'multimidia' && g !== 'documentos');
        let state = {
            selectedGerencia: null,
            selectedAba: null,
            data: {},
            currentUser: null
        };

        // --- AUTENTICAÇÃO E CONTROLE DE ACESSO ---
        onAuthStateChanged(auth, async (user) => {
            const authContainer = document.getElementById('auth-container');
            const registerContainer = document.getElementById('register-container');
            const appContainer = document.getElementById('app-container');

            if (user) {
                const userDocRef = doc(db, `users`, user.uid);
                const userDocSnap = await getDoc(userDocRef);
                if(userDocSnap.exists()){
                    state.currentUser = { uid: user.uid, email: user.email, ...userDocSnap.data() };
                    document.getElementById('user-email').textContent = state.currentUser.email;
                    document.getElementById('user-role').textContent = state.currentUser.role;

                    authContainer.style.display = 'none';
                    registerContainer.style.display = 'none';
                    appContainer.style.display = 'flex';
                    initializeAppState();
                } else { // Caso o documento do usuário ainda não exista
                    await signOut(auth);
                }
            } else {
                state.currentUser = null;
                appContainer.style.display = 'none';
                registerContainer.style.display = 'none';
                authContainer.style.display = 'flex';
            }
        });

        // --- LÓGICA DE LOGIN, CADASTRO E LOGOUT ---
        document.getElementById('login-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;
            const errorP = document.getElementById('login-error');
            errorP.textContent = '';
            try {
                await signInWithEmailAndPassword(auth, email, password);
            } catch (error) {
                errorP.textContent = 'E-mail ou senha inválidos.';
                console.error("Login failed:", error);
            }
        });

        document.getElementById('register-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const email = document.getElementById('register-email').value;
            const password = document.getElementById('register-password').value;
            const errorP = document.getElementById('register-error');
            errorP.textContent = '';
            try {
                const userCredential = await createUserWithEmailAndPassword(auth, email, password);
                const user = userCredential.user;
                // Cria um documento para o usuário com permissão padrão
                await setDoc(doc(db, `users`, user.uid), {
                    email: user.email,
                    role: 'viewer' // Permissão padrão: apenas visualização
                });
            } catch (error) {
                errorP.textContent = 'Erro ao criar conta. Verifique o e-mail e a senha (mínimo 6 caracteres).';
                console.error("Registration failed:", error);
            }
        });

        document.getElementById('logout-button').addEventListener('click', () => {
            signOut(auth);
        });
        
        document.getElementById('show-register').addEventListener('click', (e) => {
             e.preventDefault();
             document.getElementById('auth-container').style.display = 'none';
             document.getElementById('register-container').style.display = 'flex';
        });

        document.getElementById('show-login').addEventListener('click', (e) => {
             e.preventDefault();
             document.getElementById('register-container').style.display = 'none';
             document.getElementById('auth-container').style.display = 'flex';
        });

        // --- FUNÇÕES DE EXPORTAÇÃO ---
        function exportToPdf(headers, data, title) {
            const { jsPDF } = window.jspdf;
            const doc = new jsPDF();
            doc.autoTable({
                head: [headers],
                body: data,
                startY: 10,
            });
            doc.save(`${title}.pdf`);
        }

        function exportToExcel(data, filename) {
            const ws = XLSX.utils.json_to_sheet(data);
            const wb = XLSX.utils.book_new();
            XLSX.utils.book_append_sheet(wb, ws, "Dados");
            XLSX.writeFile(wb, `${filename}.xlsx`);
        }

        // --- FUNÇÕES AUXILIARES DE RENDERIZAÇÃO ---
        function canEdit() {
            if (!state.currentUser) return false;
            return state.currentUser.role === 'admin' || state.currentUser.role === 'editor';
        }

        function createActionButton(id, text, icon, color) {
            if (!canEdit()) return '';
            return `<button id="${id}" class="${color} hover:opacity-80 text-white font-bold py-2 px-4 rounded-lg shadow-md transition-transform transform hover:scale-105">
                        <i class="fas ${icon} mr-2"></i>${text}
                    </button>`;
        }
        
        // --- GERENCIAMENTO DE ESTADO E RENDERIZAÇÃO PRINCIPAL ---
        
        function setState(newState) {
            state = { ...state, ...newState };
            render();
        }

        async function initializeAppState() {
            // Código de inicialização do estado da aplicação...
            if (!state.currentUser) return; // Garante que só inicializa se logado
             gerenciaIds.forEach(id => {
                const docRef = doc(db, `artifacts/${appId}/public/data/gerencias`, id);
                onSnapshot(docRef, (docSnap) => {
                    if (docSnap.exists()) {
                        state.data[id] = docSnap.data();
                    } else {
                        const baseData = {
                            id: id, nome: GERENCIAS_INFO[id].nome, escolas: [], projetosAtivos: [], profissionaisLibra: 0, formacoes: [],
                            ...(id === 'inclusao' && { alunosLaudados: 0, alunosNaoLaudados: 0, alunosEmInvestigacao: 0 })
                        };
                        if(canEdit()) setDoc(docRef, baseData).catch(e => console.error("Erro ao criar documento:", e));
                        state.data[id] = baseData;
                    }
                    if (state.selectedGerencia === id) render();
                });
            });
            const multimidiaDocRef = doc(db, `artifacts/${appId}/public/data/gerencias`, 'multimidia');
            onSnapshot(multimidiaDocRef, (docSnap) => {
                if (docSnap.exists()) { state.data.multimidia = docSnap.data(); } 
                else { 
                    const baseData = { id: 'multimidia', midias: [] };
                    if(canEdit()) setDoc(multimidiaDocRef, baseData).catch(e => console.error("Erro ao criar doc multimidia:", e));
                    state.data.multimidia = baseData;
                }
                if (state.selectedGerencia === 'multimidia') render();
            });
            initializeDocuments();
            renderSidebar();
            if(!state.selectedGerencia) setState({selectedGerencia: 'inclusao'});
            else render();
        }

        function initializeDocuments() {
            const docRef = doc(db, `artifacts/${appId}/public/data/gerencias`, 'documentos');
            onSnapshot(docRef, (docSnap) => {
                if (docSnap.exists()) { state.data.documentos = docSnap.data(); }
                 else {
                     const baseData = {
                        id: 'documentos',
                        documentos: [
                            { id: 'lbi', nome: 'LEI BRASILEIRA DE INCLUSÃO.docx', categoria: 'Legislação', tipo: 'docx' },
                            { id: 'ldb', nome: 'LEI DIRETRIZES E BASES DA EDUCAÇÃO.docx', categoria: 'Legislação', tipo: 'docx' },
                            { id: 'bilingue', nome: 'LEI DE EDUCAÇÃO BILINGUE.pdf', categoria: 'Legislação', tipo: 'pdf' },
                            { id: 'lei18182', nome: 'Lei_18.182.pdf', categoria: 'Legislação', tipo: 'pdf' },
                            { id: 'cartilha', nome: 'CartilhaSMESP.pdf', categoria: 'Material de Apoio', tipo: 'pdf' },
                            { id: 'plano2025', nome: 'PLANO AÇÃO 2025 (1).doc', categoria: 'Planos e Projetos', tipo: 'doc' },
                            { id: 'projReflito', nome: 'Projeto Reflito.docx', categoria: 'Planos e Projetos', tipo: 'docx' },
                            { id: 'projEscritas', nome: 'PROJETO ESCRITAS QUE TRASNFORMAM IMPRESSÃO.docx', categoria: 'Planos e Projetos', tipo: 'docx' },
                            { id: 'listApoio', nome: 'Listagem de Profissionais de Apoio Efetivo.docx', categoria: 'Listagens', tipo: 'docx' },
                            { id: 'listLibras', nome: 'LISTAGEM DOS INTERPRETES DE LIBRAS EFETIVOS DA REDE.docx', categoria: 'Listagens', tipo: 'docx' }
                        ]
                    };
                    if(canEdit()) setDoc(docRef, baseData).catch(e => console.error("Erro ao criar doc documentos:", e));
                    state.data.documentos = baseData;
                }
                if (state.selectedGerencia === 'documentos') render();
            });
        }

        function render() {
            if (!state.selectedGerencia || !state.currentUser) {
                document.getElementById('content-area').innerHTML = `<div class="text-center p-10 bg-white rounded-lg shadow-md">
                    <i class="fas fa-spinner fa-spin text-5xl text-blue-500 mb-4"></i>
                    <h2 class="text-3xl font-semibold text-gray-700">Carregando...</h2>
                </div>`;
                return;
            }
            renderHeader();
            renderContent();
            updateSidebarActiveState();
        }
        
        function renderSidebar() {
            // ... (código de renderSidebar inalterado)
             const nav = document.getElementById('nav-gerencias');
            let navItems = '';
            const allGerencias = {...GERENCIAS_INFO};
            const sortedKeys = Object.keys(allGerencias).sort((a, b) => {
                if (a === 'inclusao') return -1; if (b === 'inclusao') return 1;
                if (a === 'multimidia') return 1; if (b === 'multimidia') return -1;
                if (a === 'documentos') return 1; if (b === 'documentos') return -1;
                return a.localeCompare(b);
            });

            sortedKeys.forEach(id => {
                if (id === 'documentos') return; 
                const gerencia = allGerencias[id];
                navItems += `
                    <a href="#" data-gerencia="${id}" class="gerencia-link flex items-center space-x-3 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 transition-colors duration-200">
                        <i class="fas ${gerencia.icon} w-6 text-center"></i>
                        <span>${gerencia.nome}</span>
                    </a>`;
            });
            nav.innerHTML = navItems;
        }

        function updateSidebarActiveState() {
            // ... (código de updateSidebarActiveState inalterado)
            document.querySelectorAll('.gerencia-link').forEach(link => {
                if (link.dataset.gerencia === state.selectedGerencia) {
                    link.classList.add('bg-gray-900', 'text-white');
                    link.classList.remove('text-gray-300');
                } else {
                    link.classList.remove('bg-gray-900', 'text-white');
                    link.classList.add('text-gray-300');
                }
            });
        }

        function renderHeader() {
            // ... (código de renderHeader inalterado)
             const title = document.getElementById('header-title');
            if (state.selectedGerencia) {
                title.innerHTML = `<i class="fas ${GERENCIAS_INFO[state.selectedGerencia].icon} text-blue-500"></i> ${GERENCIAS_INFO[state.selectedGerencia].nome}`;
            } else {
                 title.textContent = 'Bem-vindo!';
            }
        }
        
        function renderContent() {
             const contentArea = document.getElementById('content-area');
            const data = state.data[state.selectedGerencia] || {};
            
            const abasComuns = [ { id: 'escolas', nome: 'Unidades Escolares' }, { id: 'projetos', nome: 'Projetos Ativos' }, { id: 'libra', nome: 'Profissionais de LIBRAS' }, { id: 'formacao', nome: 'Formações' }, ];
            const abasInclusao = [ { id: 'alunos', nome: 'Quantitativo de Alunos' }, ...abasComuns ];
            
            let abas = (state.selectedGerencia === 'inclusao') ? abasInclusao : abasComuns;
            if (state.selectedGerencia === 'multimidia' || state.selectedGerencia === 'documentos') abas = [];

            if (!state.selectedAba || !abas.find(a => a.id === state.selectedAba)) {
                if (state.selectedGerencia === 'multimidia') { state.selectedAba = 'midias' } 
                else if (state.selectedGerencia === 'documentos') { state.selectedAba = 'docs' } 
                else if (abas.length > 0) { state.selectedAba = abas[0].id; }
                else { state.selectedAba = null; }
            }
            
            let abasHtml = abas.map(aba => ` <button data-aba="${aba.id}" class="aba-link px-4 py-2 text-sm font-medium rounded-t-lg transition-colors duration-200 ${state.selectedAba === aba.id ? 'bg-white text-blue-600 border-b-2 border-blue-600' : 'text-gray-500 hover:text-gray-700'}"> ${aba.nome} </button>`).join('');

            let contentHtml = '';
            switch(state.selectedAba) {
                case 'alunos': contentHtml = renderAlunos(data); break;
                case 'escolas': contentHtml = renderEscolas(data); break;
                case 'projetos': contentHtml = renderProjetos(data); break;
                case 'libra': contentHtml = renderLibra(data); break;
                case 'formacao': contentHtml = renderFormacao(data); break;
                case 'midias': contentHtml = renderMultimidia(state.data.multimidia || { midias: [] }); break;
                case 'docs': contentHtml = renderDocumentos(state.data.documentos || { documentos: [] }); break;
                default: contentHtml = `<div class="text-center p-10"><h2 class="text-2xl font-semibold text-gray-600">Selecione uma aba para visualizar o conteúdo.</h2></div>`;
            }

            const finalHtml = `
                ${abas.length > 0 ? `<div class="border-b border-gray-200 mb-6">${abasHtml}</div>` : ''}
                <div class="bg-white p-6 rounded-lg shadow-md">
                    ${contentHtml}
                </div>
            `;
            contentArea.innerHTML = finalHtml;
        }
        function createCard(title, value, icon) {
             return `<div class="bg-white p-6 rounded-lg shadow-lg border border-gray-200 flex items-center space-x-4">
                <div class="bg-blue-100 text-blue-500 rounded-full p-3">
                    <i class="fas ${icon} fa-2x"></i>
                </div>
                <div>
                    <p class="text-gray-500 text-sm font-medium">${title}</p>
                    <p class="text-3xl font-bold text-gray-800">${value}</p>
                </div>
            </div>`;
        }

        // --- RENDERIZAÇÃO DAS ABAS ESPECÍFICAS (com controle de permissão) ---
        
        function renderAlunos(data) {
             const cards = `<div class="grid grid-cols-1 md:grid-cols-3 gap-6"> ${createCard('Alunos Laudados', data.alunosLaudados || 0, 'fa-user-check')} ${createCard('Alunos Não Laudados', data.alunosNaoLaudados || 0, 'fa-user-clock')} ${createCard('Alunos em Investigação', data.alunosEmInvestigacao || 0, 'fa-user-magnifying-glass')} </div>`;
             return `<div class="flex justify-between items-center mb-6"> <h2 class="text-2xl font-bold text-gray-700">Situação dos Alunos</h2> ${createActionButton('btn-edit-alunos', 'Editar Quantitativos', 'fa-edit', 'bg-blue-500')} </div> ${cards}`;
        }
        
        function renderEscolas(data) {
            const total = data.escolas ? data.escolas.length : 0;
            const escolasHtml = (data.escolas && data.escolas.length > 0) ? data.escolas.map((escola) => `
                <div class="bg-gray-50 p-4 rounded-lg flex justify-between items-center border">
                    <div> <p class="font-semibold text-gray-800">${escola.nome}</p> <p class="text-sm text-gray-500">${escola.detalhes || 'Sem detalhes adicionais'}</p> </div>
                    ${canEdit() ? `<button class="btn-delete-item text-red-500 hover:text-red-700" data-type="escolas" data-item='${JSON.stringify(escola)}'><i class="fas fa-trash"></i></button>` : ''}
                </div>`).join('') : '<p class="text-gray-500 text-center col-span-full">Nenhuma unidade escolar cadastrada.</p>';

            return `<div class="flex justify-between items-center mb-6">
                        <div>
                            <h2 class="text-2xl font-bold text-gray-700">Unidades Escolares (${total})</h2>
                        </div>
                        <div class="flex space-x-2">
                           <button id="btn-export-escolas-pdf" class="bg-gray-700 hover:opacity-80 text-white font-bold py-2 px-4 rounded-lg shadow-md"><i class="fas fa-file-pdf"></i> PDF</button>
                           <button id="btn-export-escolas-excel" class="bg-gray-700 hover:opacity-80 text-white font-bold py-2 px-4 rounded-lg shadow-md"><i class="fas fa-file-excel"></i> Excel</button>
                           ${createActionButton('btn-add-escola', 'Adicionar Escola', 'fa-plus', 'bg-green-500')}
                        </div>
                    </div> <div class="space-y-4">${escolasHtml}</div>`;
        }

        function renderProjetos(data) {
            const total = data.projetosAtivos ? data.projetosAtivos.length : 0;
            const projetosHtml = (data.projetosAtivos && data.projetosAtivos.length > 0) ? data.projetosAtivos.map((projeto) => `
                <div class="bg-gray-50 p-4 rounded-lg border">
                    <div class="flex justify-between items-start">
                         <p class="font-semibold text-gray-800">${projeto.nome}</p>
                         ${canEdit() ? `<button class="btn-delete-item text-red-500 hover:text-red-700" data-type="projetosAtivos" data-item='${JSON.stringify(projeto)}'><i class="fas fa-trash"></i></button>` : ''}
                    </div>
                    <p class="text-sm text-gray-600 mt-2">${projeto.descricao || 'Sem descrição.'}</p>
                </div>`).join('') : '<p class="text-gray-500 text-center col-span-full">Nenhum projeto ativo cadastrado.</p>';
            return `<div class="flex justify-between items-center mb-6">
                        <h2 class="text-2xl font-bold text-gray-700">Projetos Ativos (${total})</h2>
                        <div class="flex space-x-2">
                            <button id="btn-export-projetos-pdf" class="bg-gray-700 hover:opacity-80 text-white font-bold py-2 px-4 rounded-lg shadow-md"><i class="fas fa-file-pdf"></i> PDF</button>
                           <button id="btn-export-projetos-excel" class="bg-gray-700 hover:opacity-80 text-white font-bold py-2 px-4 rounded-lg shadow-md"><i class="fas fa-file-excel"></i> Excel</button>
                            ${createActionButton('btn-add-projeto', 'Adicionar Projeto', 'fa-plus', 'bg-green-500')}
                        </div>
                    </div> <div class="space-y-4">${projetosHtml}</div>`;
        }

        function renderLibra(data) {
            return `<div class="flex justify-between items-center mb-6"> <h2 class="text-2xl font-bold text-gray-700">Profissionais de LIBRAS</h2> ${createActionButton('btn-edit-libra', 'Editar Quantitativo', 'fa-edit', 'bg-blue-500')} </div> <div class="flex justify-center"> ${createCard('Total de Profissionais', data.profissionaisLibra || 0, 'fa-sign-language')} </div>`;
        }
        
        function renderFormacao(data) {
             const total = data.formacoes ? data.formacoes.length : 0;
            const formacoesHtml = (data.formacoes && data.formacoes.length > 0) ? data.formacoes.map((formacao) => `
                <div class="bg-gray-50 p-4 rounded-lg border">
                    <div class="flex justify-between items-start">
                         <div> <p class="font-semibold text-gray-800">${formacao.nome}</p> <p class="text-sm text-gray-500">${formacao.data || 'Data a definir'}</p> </div>
                        ${canEdit() ? `<button class="btn-delete-item text-red-500 hover:text-red-700" data-type="formacoes" data-item='${JSON.stringify(formacao)}'><i class="fas fa-trash"></i></button>`: ''}
                    </div> <p class="text-sm text-gray-600 mt-2">${formacao.descricao || 'Sem descrição.'}</p>
                </div>`).join('') : '<p class="text-gray-500 text-center col-span-full">Nenhuma formação cadastrada.</p>';
             return `<div class="flex justify-between items-center mb-6"> <h2 class="text-2xl font-bold text-gray-700">Próximas Formações (${total})</h2> ${createActionButton('btn-add-formacao', 'Adicionar Formação', 'fa-plus', 'bg-green-500')} </div> <div class="space-y-4">${formacoesHtml}</div>`;
        }

        function renderMultimidia(data) {
            const total = data.midias ? data.midias.length : 0;
            const midiasHtml = (data.midias && data.midias.length > 0) ? data.midias.map((midia) => {
                const gerenciaInfo = GERENCIAS_INFO[midia.gerencia] || { nome: 'Desconhecida', icon: 'fa-question-circle' };
                return `<div class="bg-gray-50 p-4 rounded-lg border">
                    <div class="flex justify-between items-start">
                         <div> <p class="font-semibold text-gray-800">${midia.titulo}</p> <p class="text-sm text-gray-500"> <i class="fas ${gerenciaInfo.icon} mr-1"></i> ${gerenciaInfo.nome} </p> </div>
                        ${canEdit() ? `<button class="btn-delete-item text-red-500 hover:text-red-700" data-type="midias" data-item='${JSON.stringify(midia)}'><i class="fas fa-trash"></i></button>`: ''}
                    </div> <a href="${midia.url}" target="_blank" rel="noopener noreferrer" class="text-sm text-blue-500 hover:underline mt-2 inline-block truncate w-full">${midia.url}</a>
                </div>`}).join('') : '<p class="text-gray-500 text-center col-span-full">Nenhum item de multimídia cadastrado.</p>';
             return `<div class="flex justify-between items-center mb-6"> <h2 class="text-2xl font-bold text-gray-700">Multimídia (${total})</h2> ${createActionButton('btn-add-midia', 'Adicionar Mídia', 'fa-plus', 'bg-green-500')} </div> <div class="space-y-4">${midiasHtml}</div>`;
        }

        function renderDocumentos(data) {
            const categorias = { 'Legislação': [], 'Planos e Projetos': [], 'Material de Apoio': [], 'Listagens': [] };
            const iconMap = { 'pdf': 'fa-file-pdf text-red-500', 'docx': 'fa-file-word text-blue-500', 'doc': 'fa-file-word text-blue-500' };
            if (data.documentos) { data.documentos.forEach(doc => { if (categorias[doc.categoria]) { categorias[doc.categoria].push(doc); } }); }
            let html = `<div class="flex justify-between items-center mb-6"> <h2 class="text-2xl font-bold text-gray-700">Documentos de Referência</h2> ${createActionButton('btn-add-documento', 'Adicionar Documento', 'fa-plus', 'bg-green-500')} </div>`;
            for (const categoria in categorias) {
                html += `<h3 class="text-xl font-semibold text-gray-600 mt-6 mb-3 border-b pb-2">${categoria}</h3>`;
                if (categorias[categoria].length > 0) {
                    html += '<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">';
                    categorias[categoria].forEach(doc => {
                        html += `<div class="bg-gray-50 p-4 rounded-lg border flex items-center justify-between hover:shadow-lg transition-shadow">
                                <div class="flex items-center space-x-3 overflow-hidden">
                                     <i class="fas ${iconMap[doc.tipo] || 'fa-file-alt'} fa-2x"></i>
                                     <span class="font-medium text-gray-700 truncate" title="${doc.nome}">${doc.nome}</span>
                                </div>
                                ${canEdit() ? `<button class="btn-delete-item text-red-500 hover:text-red-700" data-type="documentos" data-item='${JSON.stringify(doc)}'><i class="fas fa-trash"></i></button>` : ''}
                            </div>`;
                    });
                    html += '</div>';
                } else { html += '<p class="text-gray-500">Nenhum documento nesta categoria.</p>'; }
            }
             return html;
        }
        
        // --- MODAIS E FORMULÁRIOS ---
        function openModal(title, formHtml) {
             document.getElementById('modal-title').innerText = title;
            document.getElementById('modal-body').innerHTML = formHtml;
            const modal = document.getElementById('modal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.querySelector('.modal').classList.remove('scale-95', 'opacity-0');
                modal.querySelector('.modal').classList.add('scale-100', 'opacity-100');
            }, 10);
        }

        function closeModal() {
             const modal = document.getElementById('modal');
             modal.querySelector('.modal').classList.add('scale-95', 'opacity-0');
            modal.querySelector('.modal').classList.remove('scale-100', 'opacity-100');
            setTimeout(() => modal.classList.add('hidden'), 300);
        }

        function createInput(id, label, type = 'text', value = '', placeholder = '') {
            return ` <div class="mb-4"> <label for="${id}" class="block text-gray-700 text-sm font-bold mb-2">${label}</label> <input type="${type}" id="${id}" value="${value}" placeholder="${placeholder}" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline focus:ring-2 focus:ring-blue-500"> </div>`;
        }
         function createTextarea(id, label, value = '', placeholder = '') {
            return ` <div class="mb-4"> <label for="${id}" class="block text-gray-700 text-sm font-bold mb-2">${label}</label> <textarea id="${id}" placeholder="${placeholder}" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline focus:ring-2 focus:ring-blue-500 h-24">${value}</textarea> </div>`;
        }

        function createSubmitButton(text) {
             return `<button type="submit" class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded-lg focus:outline-none focus:shadow-outline transition-transform transform hover:scale-105">${text}</button>`;
        }
        
        // --- MANIPULADORES DE EVENTOS ---

        document.addEventListener('click', async (e) => {
            // Navegação
            const gerenciaLink = e.target.closest('.gerencia-link');
            if (gerenciaLink) { e.preventDefault(); setState({ selectedGerencia: gerenciaLink.dataset.gerencia, selectedAba: null }); if(window.innerWidth < 768) { document.getElementById('sidebar').classList.add('sidebar-closed'); document.getElementById('sidebar').classList.remove('sidebar-open'); } }
            
            const abaLink = e.target.closest('.aba-link');
            if (abaLink) { e.preventDefault(); setState({ selectedAba: abaLink.dataset.aba }); }

            // Exclusão
            const deleteBtn = e.target.closest('.btn-delete-item');
            if (deleteBtn && canEdit()) {
                const type = deleteBtn.dataset.type;
                const item = JSON.parse(deleteBtn.dataset.item);
                const gerencia = (type === 'midias') ? 'multimidia' : (type === 'documentos' ? 'documentos' : state.selectedGerencia);
                const field = (type === 'midias') ? 'midias' : (type === 'documentos' ? 'documentos' : type);
                if (confirm(`Tem certeza que deseja excluir "${item.nome || item.titulo}"?`)) {
                    const docRef = doc(db, `artifacts/${appId}/public/data/gerencias`, gerencia);
                    await updateDoc(docRef, { [field]: arrayRemove(item) }).catch(err => console.error("Erro ao excluir item:", err));
                }
            }
            
            // Botões de Ação
            const actionButton = e.target.closest('button');
            if (!actionButton) return;
            const gerenciaData = state.data[state.selectedGerencia] || {};

            switch (actionButton.id) {
                // Exportação
                 case 'btn-export-escolas-pdf':
                    exportToPdf(
                        ['Nome', 'Detalhes'], 
                        state.data[state.selectedGerencia]?.escolas.map(e => [e.nome, e.detalhes]) || [],
                        'Unidades_Escolares'
                    );
                    break;
                case 'btn-export-escolas-excel':
                    exportToExcel(state.data[state.selectedGerencia]?.escolas || [], 'Unidades_Escolares');
                    break;
                case 'btn-export-projetos-pdf':
                     exportToPdf(
                        ['Nome', 'Descrição'], 
                        state.data[state.selectedGerencia]?.projetosAtivos.map(p => [p.nome, p.descricao]) || [],
                        'Projetos_Ativos'
                    );
                    break;
                case 'btn-export-projetos-excel':
                    exportToExcel(state.data[state.selectedGerencia]?.projetosAtivos || [], 'Projetos_Ativos');
                    break;
                
                // Outras Ações
                case 'menu-button': document.getElementById('sidebar').classList.toggle('sidebar-closed'); document.getElementById('sidebar').classList.toggle('sidebar-open'); break;
                case 'modal-close': closeModal(); break;
                case 'btn-edit-alunos': openModal('Editar Quantitativos de Alunos', `<form id="form-edit-alunos"> ${createInput('alunosLaudados', 'Alunos Laudados', 'number', gerenciaData.alunosLaudados || 0)} ${createInput('alunosNaoLaudados', 'Alunos Não Laudados', 'number', gerenciaData.alunosNaoLaudados || 0)} ${createInput('alunosEmInvestigacao', 'Alunos em Investigação', 'number', gerenciaData.alunosEmInvestigacao || 0)} ${createSubmitButton('Salvar Alterações')} </form>`); break;
                case 'btn-add-escola': openModal('Adicionar Unidade Escolar', `<form id="form-add-escola"> ${createInput('escolaNome', 'Nome da Escola', 'text', '', 'Ex: E.M. Prof. João da Silva')} ${createTextarea('escolaDetalhes', 'Detalhes (Endereço, etc)', '', 'Ex: Rua Principal, 123, Centro')} ${createSubmitButton('Adicionar Escola')} </form>`); break;
                case 'btn-add-projeto': openModal('Adicionar Projeto Ativo', `<form id="form-add-projeto"> ${createInput('projetoNome', 'Nome do Projeto', 'text', '', 'Ex: Inclusão Digital na Escola')} ${createTextarea('projetoDescricao', 'Descrição do Projeto')} ${createSubmitButton('Adicionar Projeto')} </form>`); break;
                case 'btn-edit-libra': openModal('Editar Quantitativo de Prof. de LIBRAS', `<form id="form-edit-libra"> ${createInput('profissionaisLibra', 'Total de Profissionais', 'number', gerenciaData.profissionaisLibra || 0)} ${createSubmitButton('Salvar Alterações')} </form>`); break;
                case 'btn-add-formacao': openModal('Adicionar Formação', `<form id="form-add-formacao"> ${createInput('formacaoNome', 'Nome da Formação', 'text', '', 'Ex: Capacitação em Autismo')} ${createInput('formacaoData', 'Data da Formação', 'date')} ${createTextarea('formacaoDescricao', 'Descrição da Formação')} ${createSubmitButton('Adicionar Formação')} </form>`); break;
                case 'btn-add-midia': let options = gerenciaIds.map(id => `<option value="${id}">${GERENCIAS_INFO[id].nome}</option>`).join(''); openModal('Adicionar Mídia', `<form id="form-add-midia"> ${createInput('midiaTitulo', 'Título da Mídia', 'text', '', 'Ex: Vídeo da Formação de Inclusão')} ${createInput('midiaUrl', 'URL do Recurso', 'url', '', 'https://www.youtube.com/watch?v=...')} <div class="mb-4"> <label for="midiaGerencia" class="block text-gray-700 text-sm font-bold mb-2">Gerência Associada</label> <select id="midiaGerencia" class="shadow border rounded w-full py-2 px-3 text-gray-700">${options}</select> </div> ${createSubmitButton('Adicionar Mídia')} </form>`); break;
                case 'btn-add-documento':
                    let catOptions = ['Legislação', 'Planos e Projetos', 'Material de Apoio', 'Listagens'].map(c => `<option value="${c}">${c}</option>`).join('');
                    openModal('Adicionar Documento', `
                        <form id="form-add-documento">
                            ${createInput('docNomeFake', 'Selecione o arquivo', 'file')}
                             <div class="mb-4">
                               <label for="docCategoria" class="block text-gray-700 text-sm font-bold mb-2">Categoria</label>
                               <select id="docCategoria" class="shadow border rounded w-full py-2 px-3 text-gray-700">${catOptions}</select>
                            </div>
                            <p class="text-xs text-gray-500 mb-4">Nota: O upload real do arquivo não é suportado. Apenas o nome do arquivo será salvo como referência.</p>
                            ${createSubmitButton('Adicionar Referência do Documento')}
                        </form>
                    `);
                    break;
            }
        });
        
        // --- MANIPULADORES DE SUBMISSÃO DE FORMULÁRIO ---
        document.addEventListener('submit', async (e) => {
            e.preventDefault();
            if(!canEdit()) return; // Impede submissão se não tiver permissão
            const form = e.target;
            const docRef = doc(db, `artifacts/${appId}/public/data/gerencias`, state.selectedGerencia);
            
            switch (form.id) {
                case 'form-edit-alunos': await updateDoc(docRef, { alunosLaudados: parseInt(form.alunosLaudados.value, 10), alunosNaoLaudados: parseInt(form.alunosNaoLaudados.value, 10), alunosEmInvestigacao: parseInt(form.alunosEmInvestigacao.value, 10), }); break;
                case 'form-add-escola': await updateDoc(docRef, { escolas: arrayUnion({ id: crypto.randomUUID(), nome: form.escolaNome.value, detalhes: form.escolaDetalhes.value }) }); break;
                case 'form-add-projeto': await updateDoc(docRef, { projetosAtivos: arrayUnion({ id: crypto.randomUUID(), nome: form.projetoNome.value, descricao: form.projetoDescricao.value }) }); break;
                case 'form-edit-libra': await updateDoc(docRef, { profissionaisLibra: parseInt(form.profissionaisLibra.value, 10) }); break;
                case 'form-add-formacao': await updateDoc(docRef, { formacoes: arrayUnion({ id: crypto.randomUUID(), nome: form.formacaoNome.value, data: form.formacaoData.value, descricao: form.formacaoDescricao.value }) }); break;
                case 'form-add-midia': const midiaDocRef = doc(db, `artifacts/${appId}/public/data/gerencias`, 'multimidia'); await updateDoc(midiaDocRef, { midias: arrayUnion({ id: crypto.randomUUID(), titulo: form.midiaTitulo.value, url: form.midiaUrl.value, gerencia: form.midiaGerencia.value }) }); break;
                case 'form-add-documento': {
                    const fileInput = form.querySelector('#docNomeFake');
                    if (fileInput.files.length > 0) {
                        const nome = fileInput.files[0].name;
                        const tipo = nome.split('.').pop().toLowerCase();
                        const newItem = { id: crypto.randomUUID(), nome: nome, categoria: form.docCategoria.value, tipo: tipo };
                        const docRefDocs = doc(db, `artifacts/${appId}/public/data/gerencias`, 'documentos');
                        await updateDoc(docRefDocs, { documentos: arrayUnion(newItem) });
                    } else {
                        alert("Por favor, selecione um arquivo.");
                        return; // Não fecha o modal se nenhum arquivo for selecionado
                    }
                    break;
                }
            }
            closeModal();
        });
    </script>
</body>
</html>

