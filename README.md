<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Site Brasil | Página inicial</title>
<style>
        body {
            background-color: #121212;
            color: white;
            margin: 0;
            scroll-behavior: smooth;
        }
    
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 25px;
    background-color: #1e1e1e;
}

header h2 {
    margin: 0;
    font-size: 22px;
}

nav {
    display: flex;
    gap: 10px;
}

button {
    padding: 10px 15px;
    background-color: #333;
    color: white;
    border: 1px solid #444;
    border-radius: 6px;
    cursor: pointer;
}

nav button:last-child {
    background-color: white;
    color: #121212;
}

.carrossel {
    width: 80%;
    max-width: 900px;
    height: 350px;
    margin: 40px auto;
    position: relative;
    overflow: hidden;
    border-radius: 12px;
}

.slide {
    width: 100%;
    height: 100%;
    background-color: #252525;
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    transition: opacity 0.8s ease;
}


.slide:nth-child(1) {
    background-color: #e74c3c;
}

.slide:nth-child(2) {
    background-color: #3498db;
}

.slide:nth-child(3) {
    background-color: #2ecc71;
}

.slide.ativo {
    opacity: 1;
}


.seta {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    z-index: 2;
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    border: none;
    border-radius: 50%;
    width: 42px;
    height: 42px;
    padding: 0;
    font-size: 20px;
}

.seta.anterior {
    left: 15px;
}

.seta.proxima {
    right: 15px;
}

.indicadores {
    position: absolute;
    bottom: 15px;
    left: 0;
    width: 100%;
    display: flex;
    justify-content: center;
    gap: 10px;
    z-index: 2;
}

.ponto {
    width: 10px;
    height: 10px;
    padding: 0;
    border: none;
    border-radius: 50%;
    background-color: #888;
}

.ponto.ativo {
    background-color: white;
    transform: scale(1.3);
}


.experiencia {
    position: relative;
    min-height: auto;
}

.bloco-texto {
    min-height: 65vh;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 35px 10%;
    width: 55%;
}

.bloco-texto h1 {
    font-size: 36px;
    margin-bottom: 12px;
}

.bloco-texto p {
    color: #bdbdbd;
    font-size: 17px;
    line-height: 1.5;
    max-width: 420px;
    margin-top: 0;
}


.bloco-texto:nth-child(2) {
    margin-left: auto;
}

.cubo-fixo {
    position: fixed;
    top: 80%;
    left: 0;
    width: 100%;
    height: 0;
    z-index: 5;
    pointer-events: none;
    perspective: 900px;
    visibility: hidden;
}

.cubo {
    position: absolute;
    left: calc(50% - var(--tam) * 1.5);
    top: calc(var(--tam) * -1.5);
    width: calc(var(--tam) * 3);
    height: calc(var(--tam) * 3);
    transform-style: preserve-3d;
    transform: rotateX(-20deg) rotateY(0deg);
}

.peca {
    position: absolute;
    left: var(--tam);
    top: var(--tam);
    width: var(--tam);
    height: var(--tam);
    transform-style: preserve-3d;
}

.face {
    position: absolute;
    width: var(--tam);
    height: var(--tam);
    box-sizing: border-box;
    border: 2px solid #111;
    border-radius: 4px;
    backface-visibility: hidden;
}

.frente {
    transform: translateZ(calc(var(--tam) / 2));
}

.tras {
    transform: rotateY(180deg) translateZ(calc(var(--tam) / 2));
}

.direita {
    transform: rotateY(90deg) translateZ(calc(var(--tam) / 2));
}

.esquerda {
    transform: rotateY(-90deg) translateZ(calc(var(--tam) / 2));
}

.cima {
    transform: rotateX(90deg) translateZ(calc(var(--tam) / 2));
}

.baixo {
    transform: rotateX(-90deg) translateZ(calc(var(--tam) / 2));
}


/* Fundo escuro atrás da janela */
.fundo-modal {
    position: fixed;
    inset: 0;
    background-color: rgba(0, 0, 0, 0.75);
    display: none;
    justify-content: center;
    align-items: center;
    z-index: 100;
    padding: 20px;
    box-sizing: border-box;
}

/* Janela de login e cadastro */
.modal {
    width: 100%;
    max-width: 400px;
    padding: 30px;
    box-sizing: border-box;
    background-color: #1e1e1e;
    border: 1px solid #333;
    border-radius: 14px;
    position: relative;
    box-shadow: 0 15px 50px rgba(0, 0, 0, 0.5);
}

/* Botão de fechar */
.fechar-modal {
    position: absolute;
    top: 10px;
    right: 10px;
    padding: 5px 10px;
    font-size: 22px;
    background: transparent;
    border: none;
    color: #aaa;
}

/* Título */
.modal h2 {
    margin-top: 10px;
    margin-bottom: 8px;
    font-size: 27px;
}

.modal p {
    color: #aaa;
    margin-bottom: 25px;
}

/* Campos do formulário */
.modal label {
    display: block;
    margin-bottom: 7px;
    font-size: 14px;
}

.modal input {
    width: 100%;
    padding: 12px;
    margin-bottom: 18px;
    box-sizing: border-box;
    background-color: #121212;
    color: white;
    border: 1px solid #444;
    border-radius: 6px;
    outline: none;
}

.modal input:focus {
    border-color: #3498db;
}

/* Botão principal */
.botao-principal {
    width: 100%;
    background-color: white;
    color: #121212;
    font-weight: bold;
    margin-top: 5px;
}

.botao-principal:hover {
    background-color: #ddd;
}

/* Alternar entre login e cadastro */
.alternar-formulario {
    text-align: center;
    font-size: 14px;
    margin-top: 20px;
    color: #aaa;
}

.alternar-formulario button {
    padding: 0;
    border: none;
    background: transparent;
    color: #3498db;
    cursor: pointer;
    font-size: 14px;
}

.mensagem {
    color: #2ecc71;
    font-size: 14px;
    margin-top: 12px;
}


    </style>
</head>
<body>
<header>
    <h2>Site Brasil</h2>

    <nav>
        <button type="button">Logar</button>
        <button type="button">Novo usuário</button>
    </nav>
</header>


<!-- Fundo e janela de autenticação -->
<div class="fundo-modal" id="fundoModal">

    <section class="modal" aria-labelledby="tituloModal">

        <button
            class="fechar-modal"
            id="fecharModal"
            type="button"
            aria-label="Fechar"
        >×</button>

        <h2 id="tituloModal">Bem-vindo de volta</h2>

        <p id="descricaoModal">
            Entre na sua conta para continuar.
        </p>

        <form id="formularioConta">

            <div id="campoNome" hidden>
                <label for="nome">Nome</label>
                <input
                    type="text"
                    id="nome"
                    name="nome"
                    autocomplete="name"
                    placeholder="Seu nome"
                >
            </div>

            <label for="email">E-mail</label>
            <input
                type="email"
                id="email"
                name="email"
                autocomplete="email"
                placeholder="seu@email.com"
                required
            >

            <label for="senha">Senha</label>
            <input
                type="password"
                id="senha"
                name="senha"
                autocomplete="current-password"
                placeholder="Sua senha"
                required
            >

            <button
                class="botao-principal"
                id="botaoEnviar"
                type="submit"
            >Entrar</button>

            <p class="mensagem" id="mensagem" aria-live="polite"></p>

        </form>

        <div class="alternar-formulario">
            <span id="textoAlternar">Ainda não tem uma conta?</span>
            <button id="botaoAlternar" type="button">
                Criar conta
            </button>
        </div>

    </section>

</div>

    <main>
        <section class="carrossel">
<div class="slide ativo"></div>
<div class="slide"></div>
<div class="slide"></div>

<button class="seta anterior" type="button" aria-label="Slide anterior">&#10094;</button>
<button class="seta proxima" type="button" aria-label="Próximo slide">&#10095;</button>

<div class="indicadores">
    <button class="ponto ativo" type="button" aria-label="Ir para o slide 1"></button>
    <button class="ponto" type="button" aria-label="Ir para o slide 2"></button>
    <button class="ponto" type="button" aria-label="Ir para o slide 3"></button>
</div>
        </section>

<section class="experiencia">

    <div class="bloco-texto">
        <h1>O futuro começa aqui</h1>
        <p>A tecnologia transforma a maneira como pensamos, criamos e vivemos.</p>
    </div>

    <div class="bloco-texto">
        <h1>Ideias ganham forma</h1>
        <p>Tudo começa com uma ideia. Com conhecimento e criatividade, ela se transforma em algo real.</p>
    </div>

    <div class="bloco-texto">
        <h1>Construindo o amanhã</h1>
        <p>O futuro não aparece pronto. Nós o construímos, linha por linha.</p>
    </div>

<div class="cubo-fixo">
    <div class="cubo"></div>
</div>

</section>

    </main>


<script>

const slides = document.querySelectorAll(".slide");
const pontos = document.querySelectorAll(".ponto");
const anterior = document.querySelector(".anterior");
const proxima = document.querySelector(".proxima");

let slideAtual = 0;
let temporizador;

function mostrarSlide(indice) {
    slides[slideAtual].classList.remove("ativo");
    pontos[slideAtual].classList.remove("ativo");

    slideAtual = (indice + slides.length) % slides.length;

    slides[slideAtual].classList.add("ativo");
    pontos[slideAtual].classList.add("ativo");
}

function avancar() {
    mostrarSlide(slideAtual + 1);
}

function voltar() {
    mostrarSlide(slideAtual - 1);
}

function reiniciarTemporizador() {
    clearInterval(temporizador);
    temporizador = setInterval(avancar, 5500);
}

proxima.addEventListener("click", () => {
    avancar();
    reiniciarTemporizador();
});

anterior.addEventListener("click", () => {
    voltar();
    reiniciarTemporizador();
});

pontos.forEach((ponto, indice) => {
    ponto.addEventListener("click", () => {
        mostrarSlide(indice);
        reiniciarTemporizador();
    });
});

reiniciarTemporizador();

// Elementos do cubo
const experiencia = document.querySelector(".experiencia");
const cuboFixo = document.querySelector(".cubo-fixo");
const cubo = document.querySelector(".cubo");
const carrossel = document.querySelector(".carrossel");
const blocos = document.querySelectorAll(".bloco-texto");

// Ajustes do movimento lateral (em pixels)
const zonaPerto = 180;
const zonaLonge = 340;

// Controle da suavidade do movimento lateral
let deslocamentoAtual = 0;
let deslocamentoDesejado = 0;

// Mantém um número entre um mínimo e um máximo
function limitar(valor, minimo, maximo) {
    return Math.max(minimo, Math.min(maximo, valor));
}

// ----- Montagem do cubo mágico -----
const TAM = 40;   // tamanho de cada peça, em pixels
cuboFixo.style.setProperty("--tam", TAM + "px");

const cores = {
    frente: "#009b48",    // verde
    tras: "#0046ad",      // azul
    direita: "#b71234",   // vermelho
    esquerda: "#ff5800",  // laranja
    cima: "#ffffff",      // branco
    baixo: "#ffd500"      // amarelo
};

const nomesDasFaces = ["frente", "tras", "direita", "esquerda", "cima", "baixo"];

// Guarda cada peça criada (vamos usar isso na etapa B)
const pecas = [];

for (let x = -1; x <= 1; x++) {
    for (let y = -1; y <= 1; y++) {
        for (let z = -1; z <= 1; z++) {

            // O miolo do cubo nunca aparece
            if (x === 0 && y === 0 && z === 0) {
                continue;
            }

            const elemento = document.createElement("div");
            elemento.className = "peca";

            // Quais faces desta peça apontam para fora do cubo
            const estaNaBorda = {
                frente: z === 1,
                tras: z === -1,
                direita: x === 1,
                esquerda: x === -1,
                cima: y === -1,
                baixo: y === 1
            };

            nomesDasFaces.forEach((nome) => {
                const face = document.createElement("div");
                face.className = "face " + nome;
                face.style.backgroundColor = estaNaBorda[nome] ? cores[nome] : "#111";
                elemento.appendChild(face);
            });

            // Leva a peça do centro até a posição dela no cubo
            elemento.style.transform =
                `translate3d(${x * TAM}px, ${y * TAM}px, ${z * TAM}px)`;

            cubo.appendChild(elemento);
            pecas.push({ elemento, x, y, z });
        }
    }
}

// ----- Embaralhar e resolver -----
const JOGADAS = 12;   // quantas jogadas de embaralhamento

const eixos = ["x", "y", "z"];
const embaralhamento = [];

while (embaralhamento.length < JOGADAS) {
    const eixo = eixos[Math.floor(Math.random() * 3)];
    const camada = Math.random() < 0.5 ? -1 : 1;
    const sentido = Math.random() < 0.5 ? -1 : 1;

    // Não repete a mesma camada duas vezes seguidas
    const ultima = embaralhamento[embaralhamento.length - 1];
    if (ultima && ultima.eixo === eixo && ultima.camada === camada) {
        continue;
    }

    embaralhamento.push({ eixo, camada, sentido });
}

// A solução é o embaralhamento de trás para frente, desfazendo cada jogada
const solucao = embaralhamento
    .slice()
    .reverse()
    .map((jogada) => ({
        eixo: jogada.eixo,
        camada: jogada.camada,
        sentido: -jogada.sentido
    }));

    // Gira a posição de uma peça em 90° em volta de um eixo
function girarPosicao(peca, eixo, sentido) {
    if (eixo === "x") {
        return { x: peca.x, y: -sentido * peca.z, z: sentido * peca.y };
    }
    if (eixo === "y") {
        return { x: sentido * peca.z, y: peca.y, z: -sentido * peca.x };
    }
    return { x: -sentido * peca.y, y: sentido * peca.x, z: peca.z };
}

// Aplica uma jogada em um estado do cubo e devolve o novo estado
function aplicarJogada(estado, jogada) {
    return estado.map((peca) => {
        // Peça fora da camada: continua igual
        if (peca[jogada.eixo] !== jogada.camada) {
            return peca;
        }

        // Peça na camada: muda de posição e ganha mais uma rotação na lista
        const nova = girarPosicao(peca, jogada.eixo, jogada.sentido);
        nova.giro =
            `rotate${jogada.eixo.toUpperCase()}(${jogada.sentido * 90}deg) ` + peca.giro;
        return nova;
    });
}

// Estado inicial: cubo resolvido
const cuboResolvido = pecas.map((peca) => ({
    x: peca.x,
    y: peca.y,
    z: peca.z,
    giro: ""
}));

// Aplica o embaralhamento para chegar no cubo embaralhado
let cuboEmbaralhado = cuboResolvido;
embaralhamento.forEach((jogada) => {
    cuboEmbaralhado = aplicarJogada(cuboEmbaralhado, jogada);
});

// estados[k] = o cubo depois de k jogadas da solução.
// O primeiro está embaralhado e o último está resolvido.
const estados = [cuboEmbaralhado];
solucao.forEach((jogada) => {
    const ultimo = estados[estados.length - 1];
    estados.push(aplicarJogada(ultimo, jogada));
});

// Desenha o cubo para um progresso de 0 (embaralhado) a 1 (resolvido)
function desenharCubo(progresso) {
    const total = solucao.length;
    const andamento = progresso * total;                   // de 0 até JOGADAS
    const k = Math.min(Math.floor(andamento), total - 1);  // jogada em andamento
    const fracao = andamento - k;                          // quanto dela já foi feito (0 a 1)

    const jogada = solucao[k];
    const estadoAtual = estados[k];

    estadoAtual.forEach((peca, i) => {
        let giro = peca.giro;

        // As peças da camada que está girando ganham a rotação parcial
        if (peca[jogada.eixo] === jogada.camada) {
            const angulo = jogada.sentido * 90 * fracao;
            giro = `rotate${jogada.eixo.toUpperCase()}(${angulo}deg) ` + giro;
        }

        const inicial = pecas[i];
        inicial.elemento.style.transform =
            `${giro} translate3d(${inicial.x * TAM}px, ${inicial.y * TAM}px, ${inicial.z * TAM}px)`;
    });
}

function atualizarCubo() {
    const area = experiencia.getBoundingClientRect();
    const baseDoCarrossel = carrossel.getBoundingClientRect().bottom;
    const centroDoCubo = cuboFixo.getBoundingClientRect().top;

    // Esconde o cubo enquanto os slides ainda estão na altura dele,
    // e também depois que a seção termina.
    if (
        area.bottom <= 0 ||
        baseDoCarrossel > centroDoCubo - 110
    ) {
        cuboFixo.style.visibility = "hidden";
        return;
    }

    cuboFixo.style.visibility = "visible";

    // Cada texto empurra o cubo para o lado contrário ao dele.
    // lado: -1 = esquerda, 0 = centro, 1 = direita
    let lado = 0;

    blocos.forEach((bloco, indice) => {
        const retangulo = bloco.getBoundingClientRect();
        const centroBloco = retangulo.top + retangulo.height / 2;
        const distancia = Math.abs(centroBloco - centroDoCubo);

        // 1 = texto na altura do cubo, 0 = texto longe
        const intensidade = limitar(
            (zonaLonge - distancia) / (zonaLonge - zonaPerto),
            0,
            1
        );

        // Textos 1 e 3 ficam à esquerda: empurram o cubo para a direita (+1).
        // O texto 2 fica à direita: empurra o cubo para a esquerda (-1).
        const direcao = indice % 2 === 0 ? 1 : -1;

        lado += direcao * intensidade;
    });

    // No topo da página o cubo fica no centro:
    // o empurrão vai crescendo nos primeiros 200px de rolagem.
    lado = lado * limitar(window.scrollY / 200, 0, 1);

    // Quantos pixels o cubo anda do centro até cada lateral.
    const alcance = window.innerWidth * 0.4 - 50;
    const deslocamentoX = lado * alcance;
    
    // de textos termina. Ele gira o cubo e também resolve o cubo mágico.
    const topoDaSecao = area.top + window.scrollY;
    const fimDaRolagem = Math.max(
        1,
        topoDaSecao + area.height - window.innerHeight
    );
    const progresso = limitar(window.scrollY / fimDaRolagem, 0, 1);

    // Rotação do cubo inteiro.
    const rotacaoX = -15 + progresso * 180;
    const rotacaoY = progresso * 540;
    const rotacaoZ = Math.sin(progresso * Math.PI * 2) * 8;
    const movimentoY = Math.sin(progresso * Math.PI * 4) * 12;

    cubo.style.transform = `
        translateX(${deslocamentoX}px)
        translateY(${movimentoY}px)
        rotateX(${rotacaoX}deg)
        rotateY(${rotacaoY}deg)
        rotateZ(${rotacaoZ}deg)
    `;

    // Gira as camadas do cubo mágico de acordo com o progresso.
    desenharCubo(progresso);
}

window.addEventListener("scroll", atualizarCubo);
window.addEventListener("resize", atualizarCubo);

atualizarCubo();


const fundoModal = document.querySelector("#fundoModal");
const formulario = document.querySelector("#formularioConta");

const tituloModal = document.querySelector("#tituloModal");
const descricaoModal = document.querySelector("#descricaoModal");
const campoNome = document.querySelector("#campoNome");
const nome = document.querySelector("#nome");
const senha = document.querySelector("#senha");

const botaoEnviar = document.querySelector("#botaoEnviar");
const botaoAlternar = document.querySelector("#botaoAlternar");
const textoAlternar = document.querySelector("#textoAlternar");
const mensagem = document.querySelector("#mensagem");

let modoCadastro = false;

// Abre a janela de login ou cadastro
function abrirModal(cadastro) {
    modoCadastro = cadastro;

    tituloModal.textContent = cadastro
        ? "Criar sua conta"
        : "Bem-vindo de volta";

    descricaoModal.textContent = cadastro
        ? "Preencha seus dados para começar."
        : "Entre na sua conta para continuar.";

    campoNome.hidden = !cadastro;
    nome.required = cadastro;

    senha.autocomplete = cadastro
        ? "new-password"
        : "current-password";

    botaoEnviar.textContent = cadastro
        ? "Criar conta"
        : "Entrar";

    textoAlternar.textContent = cadastro
        ? "Já tem uma conta?"
        : "Ainda não tem uma conta?";

    botaoAlternar.textContent = cadastro
        ? "Fazer login"
        : "Criar conta";

    mensagem.textContent = "";
    formulario.reset();

    fundoModal.style.display = "flex";
}

// Botão Logar
document.querySelector("nav button:first-child")
    .addEventListener("click", () => {
        abrirModal(false);
    });

// Botão Novo usuário
document.querySelector("nav button:last-child")
    .addEventListener("click", () => {
        abrirModal(true);
    });

// Alterna entre login e cadastro
botaoAlternar.addEventListener("click", () => {
    abrirModal(!modoCadastro);
});

// Fecha pelo X
document.querySelector("#fecharModal")
    .addEventListener("click", () => {
        fundoModal.style.display = "none";
    });

// Fecha ao clicar fora da janela
fundoModal.addEventListener("click", (evento) => {
    if (evento.target === fundoModal) {
        fundoModal.style.display = "none";
    }
});

// Fecha a janela ao pressionar Esc
document.addEventListener("keydown", (evento) => {
    if (evento.key === "Escape") {
        fundoModal.style.display = "none";
    }
});

// Demonstração visual, sem autenticação real
formulario.addEventListener("submit", (evento) => {
    evento.preventDefault();

    mensagem.textContent = modoCadastro
        ? "Interface de cadastro funcionando! Falta conectar o sistema de contas."
        : "Interface de login funcionando! Falta verificar suas credenciais.";

    mensagem.style.color = "#2ecc71";
});

/* Rolagem suave da página */
let destinoScroll = window.scrollY;
let animacaoScroll = false;

function animarScroll() {
    const atual = window.scrollY;
    const diferenca = destinoScroll - atual;

    if (Math.abs(diferenca) < 0.8) {
        window.scrollTo(0, destinoScroll);
        animacaoScroll = false;
        return;
    }

    window.scrollTo(0, atual + diferenca * 0.08);
    requestAnimationFrame(animarScroll);
}

window.addEventListener("wheel", (evento) => {
    // Respeita gestos de zoom
    if (evento.ctrlKey) return;

    evento.preventDefault();

    destinoScroll += evento.deltaY * 0.5;

    destinoScroll = Math.max(
        0,
        Math.min(
            destinoScroll,
            document.documentElement.scrollHeight - window.innerHeight
        )
    );

    if (!animacaoScroll) {
        animacaoScroll = true;
        requestAnimationFrame(animarScroll);
    }
}, { passive: false });

</script>

</body>
</html>
