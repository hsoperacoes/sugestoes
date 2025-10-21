<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>HS • Portal de Sugestões & Reclamações</title>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css" rel="stylesheet" />
  <style>
    :root{
      --bg:#0b1220; --card:#121a2b; --muted:#8aa0bf; --txt:#e9eefc; --brand:#43b0ff;
      --radius:18px; --shadow:0 10px 30px rgba(17,25,40,.25);
    }
    *{box-sizing:border-box} html,body{height:100%}
    body{
      margin:0;font:500 16px/1.5 Inter,system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial;
      color:var(--txt);
      background:radial-gradient(1200px 600px at 85% -10%,#123,#0b1220),linear-gradient(60deg,#0b1220,#0a1020)
    }
    .wrap{max-width:1200px;margin:0 auto;padding:28px}
    header{display:flex;align-items:center;gap:16px;margin-bottom:22px}
    header .logo{
      width:44px;height:44px;border-radius:12px;
      background:linear-gradient(135deg,#58c1ff,transparent),#0f172a;
      display:grid;place-items:center;box-shadow:var(--shadow)
    }
    header h1{font-size:24px;margin:0}
    header small{color:var(--muted)}

    .panel{background:rgba(255,255,255,0.02);backdrop-filter:blur(2px);
      border:1px solid rgba(255,255,255,0.08);padding:18px;border-radius:16px;box-shadow:var(--shadow)}
    .row{display:grid;gap:16px}
    @media(min-width:900px){ .row.cols-2{grid-template-columns:1fr 1fr} }

    label{display:block;margin:8px 0 6px;color:var(--muted);font-size:14px}
    select,input[type=text],textarea{
      width:100%;background:#0e1626;border:1px solid #243149;border-radius:12px;
      padding:12px 14px;color:var(--txt);outline:none;transition:.2s
    }
    textarea{min-height:120px;resize:vertical}
    select:focus,input:focus,textarea:focus{border-color:#37548a;box-shadow:0 0 0 3px rgba(67,176,255,.18)}

    .cards{display:grid;gap:16px;margin-top:10px}
    @media(min-width:900px){ .cards{grid-template-columns:repeat(4,1fr)} }
    .card{background:var(--card);border:1px solid #1d2941;border-radius:var(--radius);
      padding:18px;box-shadow:var(--shadow);cursor:pointer;position:relative;overflow:hidden}
    .card:hover{transform:translateY(-2px);box-shadow:0 14px 34px rgba(17,25,40,.35)}
    .card i{font-size:22px;margin-right:10px;color:var(--brand)}
    .card h3{margin:0 0 6px;font-size:18px}

    .hidden{display:none !important}
    .actions{display:flex;gap:10px;margin-top:16px}
    .btn{border:0;border-radius:12px;padding:12px 16px;cursor:pointer;font-weight:600}
    .btn-primary{background:linear-gradient(135deg,#43b0ff,#3aa1ff);color:#07101f}
    .btn-ghost{background:#0e1626;border:1px solid #2b3a5b;color:var(--txt)}

    .gate{position:fixed;inset:0;background:rgba(7,12,22,.9);backdrop-filter:blur(4px);display:grid;place-items:center;z-index:40}
    .gate-card{width:min(560px,92vw);background:#0f1626;border:1px solid #2a3a5b;border-radius:18px;padding:22px;box-shadow:var(--shadow)}
    .gate h2{margin:0 0 8px}

    /* Loading overlay */
    .loading{position:fixed;inset:0;display:none;place-items:center;background:rgba(7,12,22,.72);backdrop-filter:blur(2px);z-index:50}
    .loading.show{display:grid}
    .spinner{width:54px;height:54px;border-radius:50%;border:6px solid rgba(255,255,255,.15);border-top-color:#43b0ff;animation:spin 1s linear infinite}
    @keyframes spin{to{transform:rotate(360deg)}}
  </style>
</head>
<body>
  <!-- Gate inicial: escolher filial e identificação -->
  <div id="gate" class="gate">
    <div class="gate-card">
      <h2>Escolha a filial</h2>
      <label for="g-filial">Filial</label>
      <select id="g-filial"></select>

      <div style="height:8px"></div>
      <label>Identificação</label>
      <div class="row">
        <label class="chip"><input type="radio" name="g-ident" value="nao" checked> Anônimo</label>
        <label class="chip"><input type="radio" name="g-ident" value="sim"> Quero me identificar</label>
      </div>

      <div id="g-func-wrap" class="hidden" style="margin-top:8px">
        <label for="g-func">Funcionário</label>
        <select id="g-func"></select>
      </div>

      <div class="actions" style="margin-top:14px">
        <button class="btn btn-primary" id="btn-entrar" onclick="entrarPortal()">Entrar</button>
      </div>
    </div>
  </div>

  <div class="wrap hidden" id="site">
    <header>
      <div class="logo"><i class="fa-solid fa-comments"></i></div>
      <div>
        <h1>Portal HS — Sugestões & Reclamações</h1>
        <small id="contexto">—</small>
      </div>
    </header>

    <section class="panel">
      <div class="cards">
        <div class="card" data-card="produto"><h3><i class="fa-solid fa-shirt"></i>Produto</h3></div>
        <div class="card" data-card="ferramentas"><h3><i class="fa-solid fa-screwdriver-wrench"></i>Ferramentas</h3></div>
        <div class="card" data-card="geral"><h3><i class="fa-solid fa-lightbulb"></i>Geral</h3></div>
        <div class="card" data-card="manutencoes"><h3><i class="fa-solid fa-toolbox"></i>Manutenções</h3></div>
      </div>

      <!-- FORM: Produto -->
      <form id="form-produto" class="hidden" onsubmit="return enviar(event,'produto')">
        <h3 style="margin:16px 0 8px">Produto</h3>
        <div class="row cols-2">
          <div>
            <label for="p-item">Referência / Item</label>
            <input id="p-item" type="text" placeholder="Ex.: 0241AX7EN" required>
          </div>
          <div>
            <label for="p-cor">Cor</label>
            <input id="p-cor" type="text" placeholder="Ex.: N10 (Preto)">
          </div>
        </div>
        <div class="row cols-2">
          <div>
            <label for="p-tam">Tamanho</label>
            <input id="p-tam" type="text" placeholder="PP / P / M / G / XG / …">
          </div>
          <div>
            <label for="p-msg">Observações</label>
            <input id="p-msg" type="text" placeholder="Qtd, urgência, vitrine, etc.">
          </div>
        </div>
        <div class="actions">
          <button class="btn btn-ghost" type="button" onclick="resetar()">Cancelar</button>
          <button class="btn btn-primary" type="submit">Enviar</button>
        </div>
      </form>

      <!-- FORM: Ferramentas -->
      <form id="form-ferramentas" class="hidden" onsubmit="return enviar(event,'ferramentas')">
        <h3 style="margin:16px 0 8px">Ferramentas</h3>
        <div class="row cols-2">
          <div>
            <label for="f-app">Ferramenta</label>
            <select id="f-app" required>
              <option value="" disabled selected>Selecione…</option>
              <option>Otto</option>
              <option>Indeva</option>
            </select>
          </div>
          <div>
            <label for="f-assunto">Assunto (opcional)</label>
            <input id="f-assunto" type="text" placeholder="Ex.: erro no login / sugestão de tela">
          </div>
        </div>
        <label for="f-msg">Mensagem</label>
        <textarea id="f-msg" placeholder="Descreva sua dúvida, reclamação ou sugestão" required></textarea>
        <div class="actions">
          <button class="btn btn-ghost" type="button" onclick="resetar()">Cancelar</button>
          <button class="btn btn-primary" type="submit">Enviar</button>
        </div>
      </form>

      <!-- FORM: Geral -->
      <form id="form-geral" class="hidden" onsubmit="return enviar(event,'geral')">
        <h3 style="margin:16px 0 8px">Geral</h3>
        <label for="g-msg">Mensagem</label>
        <textarea id="g-msg" placeholder="Escreva livremente" required></textarea>
        <div class="actions">
          <button class="btn btn-ghost" type="button" onclick="resetar()">Cancelar</button>
          <button class="btn btn-primary" type="submit">Enviar</button>
        </div>
      </form>

      <!-- FORM: Manutenções -->
      <form id="form-manutencoes" class="hidden" onsubmit="return enviar(event,'manutencoes')">
        <h3 style="margin:16px 0 8px">Manutenções</h3>
        <div class="row cols-2">
          <div>
            <label for="m-equip">Equipamento</label>
            <input id="m-equip" type="text" placeholder="Ex.: Busca Preço" required>
          </div>
          <div>
            <label for="m-tipo">Qual manutenção</label>
            <input id="m-tipo" type="text" placeholder="Ex.: Não está funcionando" required>
          </div>
        </div>
        <label for="m-obs">Observações</label>
        <textarea id="m-obs" placeholder="Descreva o que aconteceu (ex.: busca preço parou de funcionar.)" required></textarea>
        <div class="actions">
          <button class="btn btn-ghost" type="button" onclick="resetar()">Cancelar</button>
          <button class="btn btn-primary" type="submit">Enviar</button>
        </div>
      </form>
    </section>
  </div>

  <div id="loading" class="loading"><div class="spinner"></div></div>

  <script>
    // ======== CONFIG ========
    // use exatamente a URL do seu App Web publicada:
    const APP_URL = 'https://script.google.com/macros/s/AKfycbxu_jVaotWytMOQh4UCZetFZFOxgk5ePrOkaviDd-qKNPiu2_8BjCaNczAVZzaDwAbj/exec';

    const $ = s=>document.querySelector(s), show=el=>el.classList.remove('hidden'), hide=el=>el.classList.add('hidden');
    const L = {on:()=>document.getElementById('loading').classList.add('show'), off:()=>document.getElementById('loading').classList.remove('show')};

    let FILIAIS=[]; 
    let CONTEXTO={codigo:'',razao:'',ident:false,funcionario:''};

    // ======== API helpers ========
    async function apiGet(params){
      const url = APP_URL + '?' + new URLSearchParams(params).toString();
      const r = await fetch(url,{method:'GET'});
      if(!r.ok) throw new Error('Failed to fetch');
      return r.json();
    }
    async function apiPost(body){
      const r = await fetch(APP_URL,{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify(body)});
      if(!r.ok) throw new Error('Failed to fetch');
      return r.json();
    }

    // ======== Gate ========
    async function boot(){
      try{
        L.on();
        const {filiais} = await apiGet({fn:'getFiliais'});
        FILIAIS = filiais;
        const sel=$('#g-filial'); sel.innerHTML='';
        filiais.forEach(f=>{ const o=document.createElement('option'); o.value=f.codigo; o.textContent=f.razao; sel.appendChild(o) });
        await atualizarIdentGate();
        $('#g-filial').addEventListener('change', atualizarIdentGate);
        document.querySelectorAll('input[name="g-ident"]').forEach(r=>r.addEventListener('change', atualizarIdentGate));
      }catch(err){
        alert('Erro ao carregar filiais: '+err.message);
      }finally{ L.off(); }
    }

    async function atualizarIdentGate(){
      const codigo=$('#g-filial').value; 
      const ident=document.querySelector('input[name="g-ident"]:checked').value==='sim';
      const btn=$('#btn-entrar');
      btn.disabled=true;
      if(ident){
        L.on();
        try{
          const list = await apiGet({fn:'getFuncionarios', codigo});
          const sel=$('#g-func'); sel.innerHTML='';
          const def=document.createElement('option'); def.value=''; def.selected=true; def.disabled=true; def.textContent='Selecione seu nome…'; sel.appendChild(def);
          list.forEach(n=>{ const o=document.createElement('option'); o.textContent=n; sel.appendChild(o) });
          show($('#g-func-wrap'));
        }catch(err){ alert('Erro ao carregar funcionários: '+err.message) }
        finally{ L.off(); }
      } else { hide($('#g-func-wrap')) }
      btn.disabled=false;
    }

    function entrarPortal(){
      try{
        const ident = document.querySelector('input[name="g-ident"]:checked').value==='sim';
        if(ident && !$('#g-func').value){ alert('Selecione o funcionário.'); return }
        // agora codigo = nome da filial (vindo do cabeçalho)
        const sel=$('#g-filial');
        CONTEXTO.codigo = sel.value;
        CONTEXTO.razao  = sel.options[sel.selectedIndex]?.textContent || sel.value;
        CONTEXTO.ident = ident;
        CONTEXTO.funcionario = ident ? $('#g-func').value : '';
        $('#contexto').textContent = `${CONTEXTO.razao}${CONTEXTO.ident && CONTEXTO.funcionario? ' • '+CONTEXTO.funcionario : ''}`;

        // Remove completamente o gate do DOM
        const gate = document.getElementById('gate');
        if(gate){ gate.parentNode.removeChild(gate); }

        // Exibe o site
        show(document.getElementById('site'));

        // bind dos cards
        document.querySelectorAll('.card').forEach(c=>c.onclick=()=>{
          hide($('#form-produto')); hide($('#form-ferramentas')); hide($('#form-geral')); hide($('#form-manutencoes'));
          show($('#form-'+c.dataset.card));
          window.scrollTo({top:document.body.scrollHeight,behavior:'smooth'});
        });
      }catch(err){ alert('Erro ao entrar: '+err.message) }
    }

    // ======== Envio ========
    function resetar(){ hide($('#form-produto')); hide($('#form-ferramentas')); hide($('#form-geral')); hide($('#form-manutencoes')) }
    async function enviar(ev,tipo){
      ev.preventDefault();
      const payload={ action:'submitRegistro', tipo, ...CONTEXTO };
      if(tipo==='produto'){
        payload.item=$('#p-item').value.trim(); payload.cor=$('#p-cor').value.trim();
        payload.tamanho=$('#p-tam').value.trim(); payload.mensagem=$('#p-msg').value.trim();
      } else if(tipo==='ferramentas'){
        payload.subtipo=$('#f-app').value; payload.assunto=$('#f-assunto').value.trim(); payload.mensagem=$('#f-msg').value.trim();
      } else if(tipo==='geral'){
        payload.mensagem=$('#g-msg').value.trim();
      } else if(tipo==='manutencoes'){
        payload.equipamento=$('#m-equip').value.trim();
        payload.manutencao=$('#m-tipo').value.trim();
        payload.observacoes=$('#m-obs').value.trim();
      }
      try{ L.on(); await apiPost(payload); resetar(); ev.target.reset(); alert('Enviado!') }
      catch(err){ alert('Erro: '+err.message) }
      finally{ L.off(); }
      return false;
    }

    // start
    window.addEventListener('load', boot);
  </script>
</body>
</html>
