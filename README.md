<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Minhas Finanças</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@600;700;800&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="style.css">
</head>
<body>

<div class="app">

  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="brand">
      <span class="brand-icon">💠</span>
      <span class="brand-name">Minhas Finanças</span>
    </div>

    <nav class="nav">
      <button class="nav-item active" data-view="dashboard">
        <span class="nav-icon">📊</span> Painel
      </button>
      <button class="nav-item" data-view="renda-fixa">
        <span class="nav-icon">🏦</span> Renda Fixa
      </button>
      <button class="nav-item" data-view="renda-extra">
        <span class="nav-icon">💸</span> Renda Extra
      </button>
      <button class="nav-item" data-view="gastos">
        <span class="nav-icon">🧾</span> Gastos
      </button>
      <button class="nav-item" data-view="metas">
        <span class="nav-icon">🎯</span> Metas
      </button>
    </nav>

    <button class="btn-clear-data" id="clearDataBtn">🗑️ Limpar tudo</button>
  </aside>

  <!-- MAIN -->
  <main class="main">

    <!-- DASHBOARD -->
    <section class="view active" id="view-dashboard">
      <header class="view-header">
        <h1>Painel geral</h1>
        <p class="subtitle">Sua vida financeira, de um único lugar.</p>
      </header>

      <div class="cards-grid">
        <div class="card card-income">
          <span class="card-icon">🏦</span>
          <div>
            <p class="card-label">Renda fixa</p>
            <p class="card-value" id="cardRendaFixa">R$ 0,00</p>
          </div>
        </div>
        <div class="card card-extra">
          <span class="card-icon">💸</span>
          <div>
            <p class="card-label">Renda extra</p>
            <p class="card-value" id="cardRendaExtra">R$ 0,00</p>
          </div>
        </div>
        <div class="card card-expense">
          <span class="card-icon">🧾</span>
          <div>
            <p class="card-label">Gastos</p>
            <p class="card-value" id="cardGastos">R$ 0,00</p>
          </div>
        </div>
        <div class="card card-balance">
          <span class="card-icon">💰</span>
          <div>
            <p class="card-label">Saldo</p>
            <p class="card-value" id="cardSaldo">R$ 0,00</p>
          </div>
        </div>
      </div>

      <div class="panels-grid">
        <div class="panel">
          <h2>Entradas x Gastos (últimos 6 meses)</h2>
          <canvas id="chartBarras"></canvas>
        </div>
        <div class="panel">
          <h2>Gastos por categoria</h2>
          <canvas id="chartRosca"></canvas>
        </div>
      </div>

      <div class="panel">
        <h2>Últimas movimentações</h2>
        <div class="table-wrap">
          <table class="table" id="tabelaRecentes">
            <thead>
              <tr><th></th><th>Descrição</th><th>Categoria</th><th>Tipo</th><th>Data</th><th>Valor</th></tr>
            </thead>
            <tbody></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- RENDA FIXA -->
    <section class="view" id="view-renda-fixa">
      <header class="view-header">
        <h1>Renda fixa</h1>
        <p class="subtitle">Salário, aluguéis recebidos, aposentadoria e outras entradas recorrentes.</p>
      </header>
      <div class="form-panel">
        <form class="tx-form" data-type="renda_fixa">
          <div class="icon-picker" data-target="icon-renda-fixa">
            <button type="button" class="icon-current">🏦</button>
            <div class="icon-options"></div>
          </div>
          <input type="hidden" name="icon" id="icon-renda-fixa" value="🏦">
          <input type="text" name="descricao" placeholder="Descrição (ex: Salário)" required>
          <input type="text" name="categoria" placeholder="Categoria (ex: Trabalho)" required>
          <input type="number" name="valor" placeholder="Valor (R$)" step="0.01" min="0" required>
          <input type="date" name="data" required>
          <button type="submit" class="btn-primary">Adicionar</button>
        </form>
      </div>
      <div class="panel">
        <h2>Lançamentos de renda fixa</h2>
        <div class="table-wrap">
          <table class="table" id="tabela-renda_fixa">
            <thead><tr><th></th><th>Descrição</th><th>Categoria</th><th>Data</th><th>Valor</th><th></th></tr></thead>
            <tbody></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- RENDA EXTRA -->
    <section class="view" id="view-renda-extra">
      <header class="view-header">
        <h1>Renda extra</h1>
        <p class="subtitle">Freelas, vendas, bônus e qualquer dinheiro que não é fixo.</p>
      </header>
      <div class="form-panel">
        <form class="tx-form" data-type="renda_extra">
          <div class="icon-picker" data-target="icon-renda-extra">
            <button type="button" class="icon-current">💸</button>
            <div class="icon-options"></div>
          </div>
          <input type="hidden" name="icon" id="icon-renda-extra" value="💸">
          <input type="text" name="descricao" placeholder="Descrição (ex: Freela design)" required>
          <input type="text" name="categoria" placeholder="Categoria (ex: Freelance)" required>
          <input type="number" name="valor" placeholder="Valor (R$)" step="0.01" min="0" required>
          <input type="date" name="data" required>
          <button type="submit" class="btn-primary">Adicionar</button>
        </form>
      </div>
      <div class="panel">
        <h2>Lançamentos de renda extra</h2>
        <div class="table-wrap">
          <table class="table" id="tabela-renda_extra">
            <thead><tr><th></th><th>Descrição</th><th>Categoria</th><th>Data</th><th>Valor</th><th></th></tr></thead>
            <tbody></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- GASTOS -->
    <section class="view" id="view-gastos">
      <header class="view-header">
        <h1>Gastos</h1>
        <p class="subtitle">Tudo que sai do seu bolso, categorizado e com ícone.</p>
      </header>
      <div class="form-panel">
        <form class="tx-form" data-type="gasto">
          <div class="icon-picker" data-target="icon-gasto">
            <button type="button" class="icon-current">🧾</button>
            <div class="icon-options"></div>
          </div>
          <input type="hidden" name="icon" id="icon-gasto" value="🧾">
          <input type="text" name="descricao" placeholder="Descrição (ex: Supermercado)" required>
          <input type="text" name="categoria" placeholder="Categoria (ex: Alimentação)" required>
          <input type="number" name="valor" placeholder="Valor (R$)" step="0.01" min="0" required>
          <input type="date" name="data" required>
          <button type="submit" class="btn-primary">Adicionar</button>
        </form>
      </div>
      <div class="panel">
        <h2>Lançamentos de gastos</h2>
        <div class="table-wrap">
          <table class="table" id="tabela-gasto">
            <thead><tr><th></th><th>Descrição</th><th>Categoria</th><th>Data</th><th>Valor</th><th></th></tr></thead>
            <tbody></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- METAS -->
    <section class="view" id="view-metas">
      <header class="view-header">
        <h1>Metas</h1>
        <p class="subtitle">Defina objetivos e acompanhe o quanto falta para alcançá-los.</p>
      </header>
      <div class="form-panel">
        <form class="goal-form">
          <div class="icon-picker" data-target="icon-meta">
            <button type="button" class="icon-current">🎯</button>
            <div class="icon-options"></div>
          </div>
          <input type="hidden" name="icon" id="icon-meta" value="🎯">
          <input type="text" name="nome" placeholder="Nome da meta (ex: Viagem para o litoral)" required>
          <input type="number" name="alvo" placeholder="Valor alvo (R$)" step="0.01" min="0" required>
          <input type="number" name="atual" placeholder="Valor já guardado (R$)" step="0.01" min="0" value="0">
          <button type="submit" class="btn-primary">Criar meta</button>
        </form>
      </div>
      <div class="panel">
        <h2>Suas metas</h2>
        <div class="goals-grid" id="goalsGrid"></div>
      </div>
    </section>

  </main>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.4/dist/chart.umd.min.js"></script>
<script src="app.js"></script>
</body>
</html>
