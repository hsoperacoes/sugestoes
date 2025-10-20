<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>HS • Portal de Sugestões & Reclamações</title>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css" rel="stylesheet" />
  <style>
    :root{
      --bg:#0b1220;          /* fundo escuro elegante */
      --card:#121a2b;        /* cards */
      --muted:#8aa0bf;       /* textos secundários */
      --txt:#e9eefc;         /* textos */
      --brand:#43b0ff;       /* azul marca */
      --ok:#22c55e;          /* verde */
      --warn:#f59e0b;        /* laranja */
      --danger:#ef4444;      /* vermelho */
      --radius:18px;
      --shadow:0 10px 30px rgba(17,25,40,.25);
    }
    *{box-sizing:border-box} html,body{height:100%}
    body{margin:0;font:500 16px/1.5 Inter,system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial;color:var(--txt);background:radial-gradient(1200px 600px at 85% -10%,#123,#0b1220),linear-gradient(60deg,#0b1220,#0a1020)}

    .wrap{max-width:1200px;margin:0 auto;padding:28px}
    header{display:flex;align-items:center;gap:16px;margin-bottom:22px}
    header .logo{width:44px;height:44px;border-radius:12px;background:linear-gradient(135deg,#58c1ff,transparent),#0f172a;display:grid;place-items:center;color:#00223b;box-shadow:var(--shadow)}
    header h1{font-size:24px;margin:0}
    header small{color:var(--muted)}

    .panel{background:rgba(255,255,255,0.02);backdrop-filter:blur(2px);border:1px solid rgba(255,255,255,0.08);padding:18px;border-radius:16px;box-shadow:var(--shadow)}
    .row{display:grid;gap:16px}
    @media(min-width:900px){ .row.cols-2{grid-template-columns:1fr 1fr} }

    label{display:block;margin:8px 0 6px;color:var(--muted);font-size:14px}
    select,input[type=text],input[type=password],textarea{width:100%;background:#0e1626;border:1px solid #243149;border-radius:12px;padding:12px 14px;color:var(--txt);outline:none;transition:.2s}
    textarea{min-height:120px;resize:vertical}
    select:focus,input:focus,textarea:focus{border-color:#37548a;box-shadow:0 0 0 3px rgba(67,176,255,.18)}

    .chips{display:flex;flex-wrap:wrap;gap:8px}
    .chip{background:#0f1a2d;border:1px solid #2a3b5f;border-radius:999px;padding:8px 12px;display:flex;gap:8px;align-items:center}
    .chip button{background:transparent;border:0;color:#9fb4d7;cursor:pointer}

    .cards{display:grid;gap:16px;margin-top:10px}
    @media(min-width:900px){ .cards{grid-template-columns:repeat(3,1fr)} }
    .card{background:var(--card);border:1px solid #1d2941;border-radius:var(--radius);padding:18px;box-shadow:var(--shadow);cursor:pointer;position:relative;overflow:hidden}
    .card:hover{transform:translateY(-2px);box-shadow:0 14px 34px rgba(17,25,40,.35)}
    .card i{font-size:22px;margin-right:10px;color:var(--brand)}
    .card h3{margin:0 0 6px;font-size:18px}
    .card p{margin:0;color:var(--muted);font-size:14px}

    .hidden{display:none}
    .actions{display:flex;gap:10px;margin-top:16px}
    .btn{border:0;border-radius:12px;padding:12px 16px;cursor:pointer;font-weight:600}
    .btn-primary{background:linear-gradient(135deg,#43b0ff,#3aa1ff);color:#07101f}
    .btn-ghost{background:#0e1626;border:1px solid #2b3a5b;color:var(--txt)}
    .note{font-size:13px;color:var(--muted)}

    details.config{margin-top:28px}
    details.config summary{list-style:none;cursor:pointer;background:#0f1626;border:1px solid #293755;padding:14px 16px;border-radius:12px}
    details.config[open] summary{border-bottom-left-radius:0;border-bottom-right-radius:0}
    .config-body{border:1px solid #293755;border-top:0;padding:16px;border-bottom-left-radius:12px;border-bottom-right-radius:12px;background:#0f1626}

    .toast{position:fixed;right:18px;bottom:18px;background:#0f1a2d;border:1px solid #2a3b5f;padding:12px 14px;border-radius:12px;box-shadow:var(--shadow);display:none}
    .toast.show{display:block}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="logo"><i class="fa-solid fa-comments"></i></div>
      <div>
        <h1>Portal HS — Sugestões & Reclamações</h1>
        <small>Envie ideias, reporte problemas ou peça mercadorias. Respeite as regras da empresa.</small>
      </div>
    </header>

    <!-- Seleção de Filial e Identificação -->
    <section class="panel">
      <div class="row cols-2">
        <div>
          <label for="filial">Selecione a filial</label>
          <select id="filial"></select>
          <div class="note" id="filialNote">Carregando filiais…</div>
        </div>
        <div>
          <label>Identificação</label>
          <div class="row">
            <label class="chip"><input type="radio" name="ident" value="nao" checked> Anônimo</label>
            <label class="chip"><input type="radio" name="ident" value="sim"> Quero me identificar</label>
          </div>
          <div id="boxFuncionario" class="hidden" style="margin-top:8px">
            <label for="funcionario">Escolha seu nome</label>
            <select id="funcionario"></select>
          </div>
        </div>
      </div>

      <div class="cards">
        <div class="card" data-card="produto">
          <h3><i class="fa-solid fa-shirt"></i>Produto</h3>
          <p>Peça mercadoria que está faltando na loja.</p>
        </div>
        <div class="card" data-card="ferramentas">
          <h3><i class="fa-solid fa-screwdriver-wrench"></i>Ferramentas</h3>
          <p>Otto, Indeva — dúvidas, reclamações ou sugestões.</p>
        </div>
        <div class="card" data-card="geral">
          <h3><i class="fa-solid fa-lightbulb"></i>Geral</h3>
          <p>Outros temas: sugestões e observações em geral.</p>
        </div>
      </div>

      <!-- FORM: Produto -->
      <form id="form-produto" class="hidden" onsubmit="return enviar(event,'produto')">
        <h3 style="margin:16px 0 8px">Solicitação de Produto</h3>
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
          <button class="btn btn-primary" type="submit">Enviar pedido</button>
        </div>
      </form>

      <!-- FORM: Ferramentas -->
      <form id="form-ferramentas" class="hidden" onsubmit="return enviar(event,'ferramentas')">
        <h3 style="margin:16px 0 8px">Ferramentas • Dúvidas / Reclamações</h3>
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
        <h3 style="margin:16px 0 8px">Sugestões / Reclamações Gerais</h3>
        <label for="g-msg">Mensagem</label>
        <textarea id="g-msg" placeholder="Escreva livremente" required></textarea>
        <div class="actions">
          <button class="btn btn-ghost" type="button" onclick="resetar()">Cancelar</button>
          <button class="btn btn-primary" type="submit">Enviar</button>
        </div>
      </form>
    </section>

    <!-- Configuração (somente gerente) -->
    <details class="config">
      <summary><strong>Configuração (Gerente)</strong> — adicionar/remover funcionários da filial</summary>
      <div class="config-body">
        <div class="row cols-2">
          <div>
            <label for="adm-cod">Código da filial</label>
            <input id="adm-cod" type="text" placeholder="Ex.: 293">
          </div>
          <div>
            <label for="adm-senha">Senha</label>
            <input id="adm-senha" type="password" placeholder="Senha de gerente">
          </div>
        </div>
        <div class="actions">
          <button class="btn btn-primary" onclick="entrarGerencia()"><i class="fa-solid fa-lock-open"></i> Entrar</button>
        </div>

        <div id="gerencia" class="hidden" style="margin-top:14px">
          <div class="row cols-2">
            <div>
              <label>Filial</label>
              <div id="adm-razao" class="chip">—</div>
            </div>
            <div>
              <label for="adm-novasenha">Alterar senha (opcional)</label>
              <input id="adm-novasenha" type="password" placeholder="Nova senha (deixe em branco para manter)">
            </div>
          </div>

          <label>Funcionários</label>
          <div id="adm-funcs" class="chips"></div>

          <div class="row cols-2" style="margin-top:10px">
            <input id="adm-nome" type="text" placeholder="Nome do funcionário">
            <div class="actions">
              <button class="btn btn-ghost" type="button" onclick="addChip()"><i class="fa-solid fa-plus"></i> Adicionar</button>
              <button class="btn btn-primary" type="button" onclick="salvarGerencia()"><i class="fa-solid fa-floppy-disk"></i> Salvar alterações</button>
            </div>
          </div>
        </div>
      </div>
    </details>
  </div>

  <div id="toast" class="toast"></div>

  <script>
    // ======== Helpers UI ========
    const $ = sel => document.querySelector(sel)
    const toast = (msg, ms=2200) => { const t=$('#toast'); t.textContent=msg; t.classList.add('show'); setTimeout(()=>t.classList.remove('show'), ms) }
    const show = el => el.classList.remove('hidden'); const hide = el => el.classList.add('hidden')

    // ======== Estado ========
    let FILIAIS = []   // {codigo, razao}
    let AUTENTICADO = null // {codigo, razao}

    // ======== Inicialização ========
    function init(){
      google.script.run.withSuccessHandler(({filiais})=>{
        FILIAIS = filiais
        const sel = $('#filial'); sel.innerHTML = ''
        filiais.forEach(f=>{ const o=document.createElement('option'); o.value=f.codigo; o.textContent=`${f.razao} — ${f.codigo}`; sel.appendChild(o) })
        $('#filialNote').textContent = 'Selecione a filial acima.'
        carregarFuncionarios() // para o caso de a pessoa marcar identificação
      }).getFiliais()
    }

    // Atualiza lista de funcionários quando muda filial ou quando seleciona identificação
    function carregarFuncionarios(){
      const codigo = $('#filial').value
      const ident = document.querySelector('input[name="ident"]:checked').value
      if(ident==='sim'){
        google.script.run.withSuccessHandler(list=>{
          const sel=$('#funcionario'); sel.innerHTML='';
          const def=document.createElement('option'); def.value=''; def.disabled=true; def.selected=true; def.textContent='Selecione seu nome…'; sel.appendChild(def)
          list.forEach(n=>{ const o=document.createElement('option'); o.textContent=n; sel.appendChild(o) })
          show($('#boxFuncionario'))
        }).getFuncionarios(codigo)
      } else { hide($('#boxFuncionario')) }
    }

    document.addEventListener('change', (e)=>{
      if(e.target.id==='filial' || (e.target.name==='ident')) carregarFuncionarios()
    })

    // Abre cards / forms
    document.querySelectorAll('.card').forEach(c=>c.addEventListener('click',()=>{
      hide($('#form-produto')); hide($('#form-ferramentas')); hide($('#form-geral'))
      const id = c.dataset.card
      show($('#form-'+id))
      window.scrollTo({top:document.body.scrollHeight, behavior:'smooth'})
    }))

    function resetar(){ hide($('#form-produto')); hide($('#form-ferramentas')); hide($('#form-geral')) }

    // Enviar
    function enviar(ev, tipo){
      ev.preventDefault()
      const codigo = $('#filial').value
      const razao = (FILIAIS.find(f=>f.codigo===codigo)||{}).razao || ''
      const ident = document.querySelector('input[name="ident"]:checked').value==='sim'
      const funcionario = ident ? $('#funcionario').value : ''

      let data = { tipo, codigo, razao, ident, funcionario }
      if(tipo==='produto'){
        data.item = $('#p-item').value.trim(); data.cor=$('#p-cor').value.trim(); data.tamanho=$('#p-tam').value.trim(); data.mensagem=$('#p-msg').value.trim()
      } else if(tipo==='ferramentas'){
        data.subtipo=$('#f-app').value; data.assunto=$('#f-assunto').value.trim(); data.mensagem=$('#f-msg').value.trim()
      } else if(tipo==='geral'){
        data.mensagem=$('#g-msg').value.trim()
      }

      google.script.run.withSuccessHandler(()=>{
        toast('Enviado com sucesso!')
        resetar();
        document.querySelector('form#form-'+tipo).reset()
      }).withFailureHandler(err=>toast('Erro: '+err.message)).submitRegistro(data)
      return false
    }

    // ======== Gerência ========
    function entrarGerencia(){
      const cod=$('#adm-cod').value.trim(), senha=$('#adm-senha').value
      if(!cod||!senha){ toast('Informe código e senha.'); return }
      google.script.run.withSuccessHandler(res=>{
        AUTENTICADO = res
        $('#adm-razao').textContent = `${res.razao} — ${res.codigo}`
        const box=$('#adm-funcs'); box.innerHTML=''
        res.funcionarios.forEach(n=>criarChip(n))
        show($('#gerencia'))
        toast('Acesso concedido.')
      }).withFailureHandler(err=>toast('Acesso negado: '+err.message)).authManager(cod,senha)
    }

    function criarChip(nome){
      const box=$('#adm-funcs'); const el=document.createElement('span'); el.className='chip'; el.innerHTML=`<span>${nome}</span> <button title="remover">✕</button>`
      el.querySelector('button').onclick=()=>el.remove(); box.appendChild(el)
    }

    function addChip(){ const v=$('#adm-nome').value.trim(); if(!v) return; criarChip(v); $('#adm-nome').value=''; $('#adm-nome').focus() }

    function salvarGerencia(){
      if(!AUTENTICADO){ toast('Entre com sua senha primeiro.'); return }
      const nomes=[...document.querySelectorAll('#adm-funcs .chip span:first-child')].map(s=>s.textContent)
      const novaSenha=$('#adm-novasenha').value.trim()
      google.script.run.withSuccessHandler(()=>{ toast('Configuração salva.') }).withFailureHandler(err=>toast('Erro ao salvar: '+err.message)).updateFuncionarios(AUTENTICADO.codigo, $('#adm-senha').value, nomes, novaSenha||null)
    }

    // Boot
    window.addEventListener('load', init)
  </script>
</body>
</html>
