<template>
  <main class="pagina-detalhes">
    <template v-if="anuncio">
      <nav class="breadcrumbs" aria-label="Navegação estrutural">
        <RouterLink :to="{ name: 'home' }">Início</RouterLink><span>›</span>
        <span>Roupas</span><span>›</span><span>{{ anuncio.categoria }}</span><span>›</span>
        <strong>{{ anuncio.nomeDoItem }}</strong>
      </nav>

      <div class="layout-produto">
        <div class="coluna-galeria">
          <section class="galeria">
            <div class="imagem-principal" :class="temaDoProduto(anuncio.id + fotoSelecionada)">
              <svg class="icone-produto" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2" aria-hidden="true">
                <path d="M6 2 3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"/><path d="M3 6h18"/><path d="M16 10a4 4 0 0 1-8 0"/>
              </svg>
              <div class="selo-autenticidade"><span>✓</span> Autenticidade verificada</div>
              <button class="favorito" :class="{ ativo: favorito }" :aria-label="favorito ? 'Remover dos favoritos' : 'Adicionar aos favoritos'" @click="favorito = !favorito">{{ favorito ? '♥' : '♡' }}</button>
              <span class="contador-fotos">▣ Foto {{ fotoSelecionada }} de 4</span>
            </div>
            <div class="miniaturas" aria-label="Galeria de fotos">
              <button v-for="foto in 4" :key="foto" class="miniatura" :class="[{ ativa: fotoSelecionada === foto }, temaDoProduto(anuncio.id + foto)]" :aria-label="`Exibir foto ${foto}`" @click="fotoSelecionada = foto">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2" aria-hidden="true"><path d="M6 2 3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"/><path d="M3 6h18"/></svg>
              </button>
            </div>
          </section>

          <section class="card garantias">
            <h2><span class="icone-circular escuro">✓</span> Proteção e Garantia Vitrine</h2>
            <div class="garantias-grid">
              <article><span class="icone-circular">▣</span><div><h3>Compra segura</h3><p>O pagamento só é liberado após o recebimento e a validação da peça.</p></div></article>
              <article><span class="icone-circular">↻</span><div><h3>7 dias para devolução</h3><p>Não serviu ou não era o esperado? Solicite a devolução pela plataforma.</p></div></article>
              <article><span class="icone-circular">◇</span><div><h3>Envio rastreado</h3><p>Acompanhe o pedido desde a postagem até a entrega.</p></div></article>
            </div>
          </section>
        </div>

        <aside class="coluna-compra">
          <section class="card compra-card">
            <div class="linha-superior"><span>{{ anuncio.categoria }}</span><span class="peca-unica"><i></i> Peça única</span></div>
            <h1>{{ anuncio.nomeDoItem }}</h1>
            <div class="preco-box">
              <strong>{{ precoFormatado }}</strong>
              <p>em até <b>3x de {{ parcelaFormatada }}</b> sem juros</p>
              <p class="pix">▣ {{ pixFormatado }} no PIX (5% de desconto)</p>
            </div>
            <div class="atributos">
              <div><span>Tamanho</span><strong>{{ anuncio.tamanho }}</strong></div>
              <div><span>Condição</span><strong>{{ anuncio.condicao }}</strong></div>
              <div><span>Cor</span><strong>{{ anuncio.cor }}</strong></div>
              <div><span>Composição</span><strong>{{ anuncio.composicao }}</strong></div>
            </div>
            <button class="botao principal">▣ Comprar agora</button>
            <div class="acoes-secundarias"><button class="botao secundario">＋ Sacola</button><button class="botao secundario">◇ Fazer oferta</button></div>
            <form class="frete" @submit.prevent="calcularFrete">
              <label for="cep">⌖ Calcular frete e prazo</label>
              <div><input id="cep" v-model="cep" maxlength="9" inputmode="numeric" placeholder="00000-000" @input="formatarCep"><button type="submit">Calcular</button></div>
              <p v-if="erroCep" class="erro-cep">Informe um CEP válido.</p>
              <div v-if="freteCalculado" class="resultado-frete"><span>◇ Envio econômico (3 a 5 dias)</span><strong>R$ 14,90</strong></div>
            </form>
          </section>

          <section class="card vendedor-card">
            <div class="vendedor-topo">
              <div class="avatar">LM<span>✓</span></div>
              <div class="vendedor-nome"><h2>Lucas Martins <small>Verificado</small></h2><p>★ <b>4,9</b> (84 vendas concluídas)</p></div>
              <button>Ver perfil</button>
            </div>
            <div class="dados-vendedor"><span>⚡ Envia em até 24h úteis</span><span>⌖ {{ anuncio.endereco }}</span></div>
            <button class="botao secundario contato">◇ Conversar com Lucas</button>
          </section>

          <section class="card sobre-card">
            <h2>Sobre esta peça</h2><p>{{ anuncio.descricao }}</p>
            <div class="detalhes-lista">
              <span><b>Categoria</b>{{ anuncio.categoria }}</span><span><b>Tamanho</b>{{ anuncio.tamanho }}</span>
              <span><b>Condição</b>{{ anuncio.condicao }}</span><span><b>Localização</b>{{ anuncio.endereco }}</span>
            </div>
            <div class="tags"><span>#modacircular</span><span>#vitrine</span><span>#seminovo</span></div>
          </section>
        </aside>
      </div>

      <section class="relacionados">
        <div class="titulo-secao"><div><span>Curadoria Vitrine</span><h2>Você também pode gostar</h2></div><RouterLink :to="{ name: 'home' }">Ver todos os anúncios →</RouterLink></div>
        <div class="relacionados-grid">
          <RouterLink v-for="item in anunciosRelacionados" :key="item.id" class="produto-relacionado" :to="{ name: 'detalhes-anuncio', params: { id: item.id } }">
            <div class="imagem-relacionada" :class="temaDoProduto(item.id)"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2"><path d="M6 2 3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"/><path d="M3 6h18"/></svg><span>Tam. {{ item.tamanho }}</span></div>
            <div class="produto-info"><small>{{ item.categoria }}</small><h3>{{ item.nomeDoItem }}</h3><strong>{{ formatarMoeda(item.preco) }}</strong><p>{{ item.condicao }}</p></div>
          </RouterLink>
        </div>
      </section>
    </template>

    <section v-else class="nao-encontrado"><h1>Anúncio não encontrado</h1><p>O produto informado não está disponível.</p><RouterLink :to="{ name: 'home' }">Ver outros anúncios</RouterLink></section>
  </main>
</template>

<script>
import { anuncios } from '@/data/anuncios'

export default {
  name: 'DetalhesAnuncioView',
  data() {
    return { favorito: false, fotoSelecionada: 1, cep: '', erroCep: false, freteCalculado: false }
  },
  computed: {
    anuncio() { return anuncios.find(item => item.id === Number(this.$route.params.id)) },
    precoFormatado() { return this.anuncio ? this.formatarMoeda(this.anuncio.preco) : '' },
    parcelaFormatada() { return this.anuncio ? this.formatarMoeda(this.anuncio.preco / 3) : '' },
    pixFormatado() { return this.anuncio ? this.formatarMoeda(this.anuncio.preco * 0.95) : '' },
    anunciosRelacionados() { return anuncios.filter(item => item.id !== Number(this.$route.params.id)).slice(0, 4) }
  },
  watch: {
    '$route.params.id'() { this.fotoSelecionada = 1; this.favorito = false }
  },
  methods: {
    formatarMoeda(valor) { return new Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' }).format(valor) },
    temaDoProduto(id) { return `tema-${(id % 4) + 1}` },
    formatarCep() {
      const numeros = this.cep.replace(/\D/g, '').slice(0, 8)
      this.cep = numeros.length > 5 ? `${numeros.slice(0, 5)}-${numeros.slice(5)}` : numeros
      this.erroCep = false; this.freteCalculado = false
    },
    calcularFrete() {
      const valido = this.cep.replace(/\D/g, '').length === 8
      this.erroCep = !valido; this.freteCalculado = valido
    }
  }
}
</script>

<style scoped>
* { box-sizing: border-box; }
.pagina-detalhes { width: 100%; max-width: 1280px; margin: 0 auto; padding: 18px 24px 80px; color: #121c2a; font-family: Inter, Arial, sans-serif; text-align: left; }
.breadcrumbs { display: flex; align-items: center; gap: 7px; min-width: 0; padding: 10px 0 18px; color: #687181; font-size: 14px; white-space: nowrap; overflow: hidden; }.breadcrumbs a { color: inherit; text-decoration: none; }.breadcrumbs a:hover { color: #212b3a; }.breadcrumbs strong { overflow: hidden; color: #121c2a; text-overflow: ellipsis; }
.layout-produto { display: grid; grid-template-columns: minmax(0, 7fr) minmax(380px, 5fr); gap: 24px; align-items: start; }.coluna-galeria, .coluna-compra { display: flex; flex-direction: column; gap: 24px; }
.imagem-principal { position: relative; display: flex; width: 100%; aspect-ratio: 4 / 5; align-items: center; justify-content: center; overflow: hidden; border-radius: 12px; color: #718096; }.tema-1 { background: linear-gradient(145deg, #e9edf3, #cbd5e1); }.tema-2 { background: linear-gradient(145deg, #ece8e1, #d4c9ba); }.tema-3 { background: linear-gradient(145deg, #e5ebed, #bdcbd0); }.tema-4 { background: linear-gradient(145deg, #eeeaf0, #d2c7d6); }.icone-produto { width: 23%; max-width: 150px; opacity: .65; }
.selo-autenticidade { position: absolute; top: 24px; left: 24px; display: flex; align-items: center; gap: 7px; padding: 8px 12px; border-radius: 999px; background: rgba(255,255,255,.9); box-shadow: 0 2px 10px rgba(0,0,0,.07); font-size: 12px; font-weight: 700; letter-spacing: .04em; text-transform: uppercase; }.selo-autenticidade span { display: grid; width: 19px; height: 19px; place-items: center; border-radius: 50%; background: #212b3a; color: #fff; }.favorito { position: absolute; top: 24px; right: 24px; display: grid; width: 42px; height: 42px; place-items: center; border: 0; border-radius: 50%; background: rgba(255,255,255,.92); color: #212b3a; box-shadow: 0 2px 10px rgba(0,0,0,.08); cursor: pointer; font-size: 25px; }.favorito.ativo { color: #ba1a1a; }.contador-fotos { position: absolute; right: 24px; bottom: 24px; padding: 7px 12px; border-radius: 999px; background: rgba(33,43,58,.82); color: #fff; font-size: 12px; font-weight: 600; }
.miniaturas { display: grid; grid-template-columns: repeat(4, 1fr); gap: 12px; margin-top: 12px; }.miniatura { display: grid; aspect-ratio: 1; place-items: center; border: 2px solid transparent; border-radius: 8px; color: #718096; cursor: pointer; opacity: .62; }.miniatura:hover, .miniatura.ativa { opacity: 1; }.miniatura.ativa { border-color: #374151; }.miniatura svg { width: 29%; }
.card { border-radius: 12px; background: #fff; box-shadow: 0 2px 10px rgba(18,28,42,.06); }.garantias { padding: 24px; }.garantias h2, .sobre-card h2 { display: flex; align-items: center; gap: 8px; margin: 0 0 20px; font-size: 20px; }.icone-circular { display: grid; width: 32px; height: 32px; flex-shrink: 0; place-items: center; border-radius: 50%; background: #dee9fc; font-weight: 700; }.icone-circular.escuro { width: 24px; height: 24px; background: #212b3a; color: #fff; font-size: 13px; }.garantias-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }.garantias article { display: flex; align-items: flex-start; gap: 12px; }.garantias h3 { margin: 1px 0 5px; font-size: 14px; }.garantias p { margin: 0; color: #616b79; font-size: 13px; line-height: 1.45; }
.compra-card { display: flex; flex-direction: column; gap: 20px; padding: 24px; }.linha-superior { display: flex; align-items: center; justify-content: space-between; gap: 12px; color: #585f6c; font-size: 12px; font-weight: 700; letter-spacing: .08em; text-transform: uppercase; }.peca-unica { display: flex; align-items: center; gap: 6px; padding: 5px 8px; border-radius: 999px; background: #dee9fc; color: #444b57; letter-spacing: 0; text-transform: none; }.peca-unica i { width: 7px; height: 7px; border-radius: 50%; background: #212b3a; }.compra-card h1 { margin: -7px 0 0; font-size: 32px; line-height: 1.2; letter-spacing: -.02em; }
.preco-box { padding: 20px; border-radius: 8px; background: #eff4ff; }.preco-box > strong { display: block; margin-bottom: 12px; font-size: 42px; line-height: 1; }.preco-box p { margin: 6px 0 0; font-size: 14px; }.preco-box .pix { color: #374151; font-weight: 600; }.atributos { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }.atributos div { display: flex; min-height: 75px; flex-direction: column; justify-content: center; padding: 12px; border-radius: 8px; background: #eff4ff; }.atributos span { margin-bottom: 4px; color: #687181; font-size: 11px; font-weight: 700; text-transform: uppercase; }.atributos strong { font-size: 15px; line-height: 1.25; }
.botao { border: 0; border-radius: 8px; cursor: pointer; font-weight: 700; }.principal { height: 50px; background: #212b3a; color: #fff; font-size: 17px; }.principal:hover { background: #374151; }.acoes-secundarias { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }.secundario { min-height: 44px; background: #dee9fc; color: #212b3a; font-size: 15px; }.secundario:hover { background: #d2def2; }
.frete { display: flex; flex-direction: column; gap: 10px; padding: 20px; border-radius: 8px; background: #eff4ff; }.frete label { font-size: 15px; font-weight: 700; }.frete > div { display: flex; gap: 8px; }.frete input { width: 100%; min-width: 0; padding: 11px 12px; border: 1px solid transparent; border-radius: 7px; outline: none; font-size: 15px; }.frete input:focus { border-color: #374151; }.frete button { padding: 0 18px; border: 0; border-radius: 7px; background: #212b3a; color: #fff; cursor: pointer; font-weight: 700; }.frete .erro-cep { margin: 0; color: #ba1a1a; font-size: 12px; }.frete .resultado-frete { align-items: center; justify-content: space-between; padding-top: 5px; color: #374151; font-size: 13px; }
.vendedor-card, .sobre-card { padding: 24px; }.vendedor-topo { display: flex; align-items: center; gap: 12px; }.avatar { position: relative; display: grid; width: 56px; height: 56px; flex-shrink: 0; place-items: center; border-radius: 50%; background: #374151; color: #fff; font-weight: 800; }.avatar span { position: absolute; right: -2px; bottom: -1px; display: grid; width: 18px; height: 18px; place-items: center; border: 2px solid #fff; border-radius: 50%; background: #dce2f3; color: #212b3a; font-size: 10px; }.vendedor-nome { min-width: 0; flex: 1; }.vendedor-topo h2 { margin: 0 0 5px; font-size: 17px; }.vendedor-topo h2 small { padding: 3px 6px; border-radius: 999px; background: #dee9fc; font-size: 10px; }.vendedor-topo p { margin: 0; color: #687181; font-size: 13px; }.vendedor-topo > button { padding: 7px 10px; border: 0; border-radius: 7px; background: #dee9fc; cursor: pointer; font-size: 12px; font-weight: 700; }.dados-vendedor { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin: 20px 0; color: #687181; font-size: 13px; line-height: 1.4; }.contato { width: 100%; }
.sobre-card > p { margin: 0 0 20px; color: #475569; line-height: 1.65; }.detalhes-lista { display: grid; grid-template-columns: 1fr 1fr; gap: 1px; overflow: hidden; border-radius: 8px; background: #dce2f3; }.detalhes-lista span { display: flex; flex-direction: column; gap: 5px; padding: 12px; background: #eff4ff; color: #475569; font-size: 13px; }.detalhes-lista b { color: #687181; font-size: 10px; text-transform: uppercase; }.tags { display: flex; flex-wrap: wrap; gap: 7px; margin-top: 18px; }.tags span { padding: 6px 10px; border-radius: 999px; background: #e6eeff; color: #56606d; font-size: 11px; font-weight: 600; }
.relacionados { margin-top: 56px; }.titulo-secao { display: flex; align-items: end; justify-content: space-between; gap: 20px; margin-bottom: 24px; }.titulo-secao span { color: #585f6c; font-size: 11px; font-weight: 800; letter-spacing: .09em; text-transform: uppercase; }.titulo-secao h2 { margin: 5px 0 0; font-size: 30px; }.titulo-secao a { color: #212b3a; font-size: 14px; font-weight: 700; text-decoration: none; }.relacionados-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 24px; }.produto-relacionado { overflow: hidden; border-radius: 12px; background: #fff; box-shadow: 0 2px 10px rgba(18,28,42,.06); color: inherit; text-decoration: none; transition: transform .2s; }.produto-relacionado:hover { transform: translateY(-3px); }.imagem-relacionada { position: relative; display: grid; aspect-ratio: 3 / 4; place-items: center; color: #718096; }.imagem-relacionada svg { width: 28%; }.imagem-relacionada span { position: absolute; bottom: 12px; left: 12px; padding: 5px 8px; border-radius: 999px; background: rgba(255,255,255,.9); font-size: 11px; font-weight: 700; }.produto-info { display: grid; grid-template-columns: 1fr auto; gap: 5px 10px; padding: 16px; }.produto-info small, .produto-info h3 { grid-column: 1 / -1; }.produto-info small { color: #687181; font-size: 10px; font-weight: 700; text-transform: uppercase; }.produto-info h3 { overflow: hidden; margin: 0 0 7px; font-size: 14px; text-overflow: ellipsis; white-space: nowrap; }.produto-info strong { font-size: 17px; }.produto-info p { margin: 2px 0 0; color: #687181; font-size: 11px; }
.nao-encontrado { padding: 100px 24px; text-align: center; }.nao-encontrado h1 { font-size: 32px; }.nao-encontrado p { color: #687181; }.nao-encontrado a { color: #212b3a; font-weight: 700; }
@media (max-width: 960px) { .layout-produto { grid-template-columns: 1fr; }.imagem-principal { max-height: 700px; }.relacionados-grid { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 620px) { .pagina-detalhes { padding: 12px 16px 56px; }.breadcrumbs span:nth-of-type(2), .breadcrumbs span:nth-of-type(3) { display: none; }.selo-autenticidade { top: 14px; left: 14px; font-size: 9px; }.favorito { top: 14px; right: 14px; }.contador-fotos { right: 14px; bottom: 14px; }.garantias-grid { grid-template-columns: 1fr; }.compra-card h1 { font-size: 27px; }.preco-box > strong { font-size: 35px; }.dados-vendedor { grid-template-columns: 1fr; }.titulo-secao { align-items: flex-start; flex-direction: column; }.titulo-secao h2 { font-size: 25px; }.relacionados-grid { gap: 12px; }.produto-info { grid-template-columns: 1fr; }.produto-info p { display: none; } }
</style>
