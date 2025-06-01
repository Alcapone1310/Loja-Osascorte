<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Loja VIP - Seu Servidor FiveM</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap');
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    font-family: 'Montserrat', sans-serif;
    background: linear-gradient(135deg, #232526, #1c1c1c);
    color: #eee;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  header {
    padding: 2rem;
    text-align: center;
    background: #111;
    width: 100%;
    box-shadow: 0 2px 8px rgba(0,0,0,0.8);
    user-select: none;
  }
  header h1 {
    margin: 0;
    font-weight: 700;
    font-size: 2.5rem;
    letter-spacing: 2px;
    color: #ffd700;
    text-shadow: 0 0 8px #ffd700aa;
  }

  main {
    flex: 1;
    width: 100%;
    max-width: 1200px;
    padding: 2rem 1rem;
  }

  section {
    margin-bottom: 3rem;
  }

  h2.section-title {
    font-size: 2rem;
    font-weight: 700;
    color: #ffa500;
    border-bottom: 3px solid #ffd700;
    padding-bottom: 0.3rem;
    margin-bottom: 1rem;
    user-select: none;
  }

  .packs {
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(280px,1fr));
    gap: 1.5rem;
  }

  .pack-card {
    background: #2c2c2c;
    border-radius: 12px;
    padding: 1.5rem;
    box-shadow: 0 0 15px #ffd700aa;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  .pack-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 0 30px #ffd700ee;
  }
  .pack-title {
    font-size: 1.6rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    color: #ffd700;
  }
  .pack-price {
    font-size: 1.4rem;
    font-weight: 700;
    color: #ffa500;
    margin-bottom: 1rem;
  }
  .pack-benefits {
    flex: 1;
    font-size: 1rem;
    margin-bottom: 1.5rem;
    line-height: 1.4;
    color: #ddd;
  }
  .btn-buy {
    background: linear-gradient(45deg, #ffcc00, #ff9900);
    border: none;
    padding: 0.75rem 1.2rem;
    font-weight: 700;
    font-size: 1.1rem;
    border-radius: 8px;
    cursor: pointer;
    color: #222;
    box-shadow: 0 4px 10px #ffcc0088;
    transition: background 0.3s ease;
    align-self: center;
  }
  .btn-buy:hover {
    background: linear-gradient(45deg, #ffdd33, #ffaa00);
  }

  /* Modal styles */
  .modal-overlay {
    position: fixed;
    top:0; left:0; right:0; bottom:0;
    background: rgba(0,0,0,0.8);
    display: none;
    justify-content: center;
    align-items: center;
    z-index: 100;
  }
  .modal-overlay.active {
    display: flex;
  }
  .modal {
    background: #222;
    border-radius: 16px;
    padding: 2rem 2.5rem;
    max-width: 400px;
    width: 90%;
    box-shadow: 0 0 25px #ffd700bb;
    color: #eee;
    position: relative;
  }
  .modal h2 {
    margin-top: 0;
    color: #ffd700;
    font-weight: 700;
    text-align: center;
    margin-bottom: 1rem;
  }
  .modal label {
    display: block;
    font-weight: 600;
    margin: 1rem 0 0.3rem;
  }
  .modal input[type="text"], .modal input[type="email"] {
    width: 100%;
    padding: 0.55rem 0.8rem;
    border-radius: 8px;
    border: none;
    font-size: 1rem;
  }
  .modal button {
    margin-top: 1.5rem;
    width: 100%;
    background: #ffd700;
    border: none;
    padding: 0.75rem;
    font-weight: 700;
    cursor: pointer;
    font-size: 1.1rem;
    border-radius: 10px;
    color: #222;
    box-shadow: 0 3px 10px #ffcc0088;
    transition: background-color 0.3s ease;
  }
  .modal button:hover {
    background-color: #ffcc00;
  }
  .modal .close-btn {
    position: absolute;
    right: 1rem;
    top: 1rem;
    background: transparent;
    border: none;
    font-size: 1.8rem;
    font-weight: 700;
    cursor: pointer;
    color: #aaa;
    transition: color 0.3s ease;
  }
  .modal .close-btn:hover {
    color: #ffd700;
  }

  /* Purchased section */
  #purchased-section {
    margin-top: 3rem;
    background: #1b1b1b;
    box-shadow: 0 0 20px #444;
    border-radius: 12px;
    padding: 1.5rem;
    max-width: 1200px;
    color: #aaa;
  }
  #purchased-section h3 {
    margin-top: 0;
    color: #ffd700;
    font-weight: 700;
  }
  #purchased-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  #purchased-list li {
    padding: 0.6rem 0;
    border-bottom: 1px solid #333;
  }
</style>
</head>
<body>
<header>
  <h1>Loja VIP - Seu Servidor FiveM</h1>
</header>

<main>
  <section aria-label="Pacotes VIP" id="vip-section">
    <h2 class="section-title">Pacotes VIP</h2>
    <div class="packs" id="packs-vip">
      <!-- Pacotes VIP serão inseridos aqui pelo JS -->
    </div>
  </section>

  <section aria-label="Veículos à venda" id="vehicles-section">
    <h2 class="section-title">Veículos à Venda</h2>
    <div class="packs" id="packs-vehicles">
      <!-- Veículos serão inseridos aqui pelo JS -->
    </div>
  </section>

  <section aria-label="Mansões à venda" id="mansions-section">
    <h2 class="section-title">Mansões à Venda</h2>
    <div class="packs" id="packs-mansions">
      <!-- Mansões serão inseridas aqui pelo JS -->
    </div>
  </section>

  <section id="purchased-section" hidden>
    <h3>Itens Comprados:</h3>
    <ul id="purchased-list"></ul>
  </section>
</main>

<div class="modal-overlay" id="modal-overlay" aria-hidden="true" role="dialog" aria-modal="true">
  <div class="modal" role="document" aria-labelledby="modal-title">
    <button class="close-btn" id="close-modal" aria-label="Fechar">&times;</button>
    <h2 id="modal-title">Confirmar Compra</h2>
    <form id="purchase-form">
      <div>
        <label for="buyer-name">Nome no jogo:</label>
        <input type="text" id="buyer-name" name="buyerName" required minlength="3" placeholder="Seu nome no servidor"/>
      </div>
      <div>
        <label for="buyer-email">Email (para confirmação):</label>
        <input type="email" id="buyer-email" name="buyerEmail" required placeholder="seu@email.com"/>
      </div>
      <div style="margin-top: 1rem; font-weight: 600;" id="selected-pack-info"></div>
      <button type="submit">Confirmar Compra</button>
    </form>
  </div>
</div>

<script>
  // Dados dos pacotes VIP atualizados
  const vipPacks = [
    {
      id: "bronze",
      title: "VIP Bronze",
      price: 15.00,
      benefits: [
        "Acesso a comandos exclusivos básicos",
        "Spawn de veículos VIP básicos",
        "VIP ativo por 7 dias"
      ]
    },
    {
      id: "prata",
      title: "VIP Prata",
      price: 25.00,
      benefits: [
        "Tudo do VIP Bronze",
        "Spawn de veículos VIP intermediários",
        "VIP ativo por 30 dias",
        "Acesso à área VIP no servidor"
      ]
    },
    {
      id: "ouro",
      title: "VIP Ouro",
      price: 35.00,
      benefits: [
        "Tudo do VIP Prata",
        "Spawn de veículos VIP avançados",
        "VIP ativo por 90 dias",
        "Desconto em lojas do servidor",
        "Acesso prioritário no servidor"
      ]
    },
    {
      id: "diamante",
      title: "VIP Diamante",
      price: 50.00,
      benefits: [
        "Todos os benefícios do VIP Ouro",
        "Spawn de veículos exclusivos e raros",
        "VIP por tempo vitalício",
        "Suporte prioritário via Discord",
        "Itens exclusivos no jogo"
      ]
    }
  ];

  // Dados dos veículos
  const vehiclePacks = [
    {
      id: "x6blindada",
      title: "X6 Blindada",
      price: 20.00,
      benefits: [
        "Veículo blindado X6 com proteção avançada",
        "Performance com segurança no servidor"
      ]
    },
    {
      id: "x7blindada",
      title: "X7 Blindada",
      price: 25.00,
      benefits: [
        "Veículo blindado X7 com alto nível de proteção",
        "Ideal para missões perigosas"
      ]
    },
    {
      id: "bell412blindada",
      title: "Bell 412 Blindada",
      price: 50.00,
      benefits: [
        "Helicóptero Bell 412 blindado",
        "Transporte rápido e seguro",
        "Ideal para operações VIP"
      ]
    },
    {
      id: "cybertruckblind",
      title: "Cybertruck Blind",
      price: 30.00,
      benefits: [
        "Cybertruck com blindagem reforçada",
        "Design futurista e protegido"
      ]
    }
  ];

  // Dados das mansões
  const mansionPacks = [
    {id:"mansao1", title:"Mansão 1", price: 30.00, benefits:["Design elegante, piscina, garagem para 2 veículos"]},
    {id:"mansao2", title:"Mansão 2", price: 50.00, benefits:["Luxo máximo, área de lazer, garagem ampla"]},
    {id:"mansao3", title:"Mansão 3", price: 40.00, benefits:["Ambiente sofisticado, jardim, piscina"]},
    {id:"mansao4", title:"Mansão 4", price: 50.00, benefits:["Localização premium, espaço amplo, segurança reforçada"]},
    {id:"mansao5", title:"Mansão 5", price: 30.00, benefits:["Conforto, garagem, decoração moderna"]},
    {id:"mansao6", title:"Mansão 6", price: 45.00, benefits:["Estilo exclusivo, área de entretenimento, piscina"]},
  ];

  // Contêineres para cada categoria
  const packsVipContainer = document.getElementById('packs-vip');
  const packsVehiclesContainer = document.getElementById('packs-vehicles');
  const packsMansionsContainer = document.getElementById('packs-mansions');
  const modalOverlay = document.getElementById('modal-overlay');
  const closeModalBtn = document.getElementById('close-modal');
  const purchaseForm = document.getElementById('purchase-form');
  const selectedPackInfo = document.getElementById('selected-pack-info');
  const purchasedSection = document.getElementById('purchased-section');
  const purchasedList = document.getElementById('purchased-list');

  let selectedPack = null;

  // Função para criar cartão de produto
  function createPackCard(pack) {
    const packCard = document.createElement('article');
    packCard.className = 'pack-card';

    const titleEl = document.createElement('h3');
    titleEl.className = 'pack-title';
    titleEl.textContent = pack.title;

    const priceEl = document.createElement('p');
    priceEl.className = 'pack-price';
    priceEl.textContent = `R$ ${pack.price.toFixed(2)}`;

    const benefitsEl = document.createElement('ul');
    benefitsEl.className = 'pack-benefits';
    pack.benefits.forEach(b => {
      const li = document.createElement('li');
      li.textContent = "• " + b;
      benefitsEl.appendChild(li);
    });

    const btnBuy = document.createElement('button');
    btnBuy.className = 'btn-buy';
    btnBuy.textContent = 'Comprar';
    btnBuy.addEventListener('click', () => openModal(pack));

    packCard.appendChild(titleEl);
    packCard.appendChild(priceEl);
    packCard.appendChild(benefitsEl);
    packCard.appendChild(btnBuy);

    return packCard;
  }

  // Renderizar todas as categorias
  function renderAllPacks() {
    vipPacks.forEach(pack => {
      packsVipContainer.appendChild(createPackCard(pack));
    });
    vehiclePacks.forEach(pack => {
      packsVehiclesContainer.appendChild(createPackCard(pack));
    });
    mansionPacks.forEach(pack => {
      packsMansionsContainer.appendChild(createPackCard(pack));
    });
  }

  // Abrir modal com as infos do pacote selecionado
  function openModal(pack) {
    selectedPack = pack;
    selectedPackInfo.textContent = `Você está comprando: ${pack.title} por R$ ${pack.price.toFixed(2)}`;
    purchaseForm.reset();
    modalOverlay.classList.add('active');
    document.getElementById('buyer-name').focus();
  }

  // Fechar modal
  function closeModal() {
    modalOverlay.classList.remove('active');
  }

  // Salvar compra no localStorage
  function savePurchase(purchaseData) {
    let purchases = JSON.parse(localStorage.getItem('vipPurchases')) || [];
    purchases.push(purchaseData);
    localStorage.setItem('vipPurchases', JSON.stringify(purchases));
  }

  // Carregar compras e mostrar na interface
  function loadPurchases() {
    let purchases = JSON.parse(localStorage.getItem('vipPurchases'));
    if (!purchases || purchases.length === 0) {
      purchasedSection.hidden = true;
      return;
    }
    purchasedSection.hidden = false;
    purchasedList.innerHTML = '';
    purchases.forEach((purchase, index) => {
      const li = document.createElement('li');
      li.textContent = `${purchase.date} - ${purchase.buyerName} comprou ${purchase.packTitle} por R$ ${purchase.price.toFixed(2)}`;
      purchasedList.appendChild(li);
    });
  }

  // Evento submit do formulário de compra
  purchaseForm.addEventListener('submit', (e) => {
    e.preventDefault();

    const buyerName = purchaseForm.buyerName.value.trim();
    const buyerEmail = purchaseForm.buyerEmail.value.trim();
    if (!buyerName || !buyerEmail) {
      alert('Por favor, preencha todos os campos.');
      return;
    }
    if (!selectedPack) {
      alert('Pacote não selecionado.');
      return;
    }

    // Simula confirmação de compra
    alert(`Compra confirmada!\n\nNome: ${buyerName}\nItem: ${selectedPack.title}\nValor: R$ ${selectedPack.price.toFixed(2)}`);

    // Salva no localStorage
    const purchaseData = {
      buyerName,
      buyerEmail,
      packId: selectedPack.id,
      packTitle: selectedPack.title,
      price: selectedPack.price,
      date: new Date().toLocaleString()
    };
    savePurchase(purchaseData);
    loadPurchases();
    closeModal();
  });

  closeModalBtn.addEventListener('click', closeModal);
  modalOverlay.addEventListener('click', (e) => {
    if (e.target === modalOverlay) closeModal();
  });

  // Inicializa a loja
  renderAllPacks();
  loadPurchases();
</script>
</body>
</html>

