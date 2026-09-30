# PROMPT: Landing Page Interativa com Canvas + GSAP ScrollTrigger (Image Sequence)

Você é um desenvolvedor frontend especialista em animações interativas, performance web, GSAP e Tailwind CSS. 
Sua tarefa é criar uma Landing Page moderna, fluida e com acabamento de alta conversão, onde a rolagem da página controla o avanço de uma sequência de frames (estilo Apple AirPods / scrollytelling), sincronizada com textos e seções que aparecem por cima.

---

### 1. ESTRUTURA E REQUISITOS TÉCNICOS

1. **Stack Técnica:**
   - HTML5, Tailwind CSS, JavaScript moderno (ES6+).
   - **GSAP 3** e **ScrollTrigger** (via CDN ou imports padrão do projeto).
   - Renderização dos frames em elemento `<canvas>` com contexto 2D (`requestAnimationFrame` e interpolação para suavidade máxima).

2. **Lógica de Pré-carregamento (Image Sequence Preloader):**
   - Tenho uma sequência de frames extraídos de vídeo.
   - Padrão do caminho dos arquivos: `[Exemplo: /frames/frame_0001.webp até /frames/frame_0240.webp]`
   - Total de frames: `[Exemplo: 240 frames]`
   - Deve conter uma tela de loading inicial (spinner ou barra percentual) que só libera a navegação quando uma quantidade mínima (ou todos) os primeiros frames estiverem em cache na memória, evitando tela preta ou flickers no scroll.

3. **Mecanismo de ScrollTrigger no Canvas:**
   - O `<canvas>` deve ficar em um container com posição `sticky top-0 w-full h-screen` (ou `fixed`), ocupando 100vw e 100vh com `object-fit: cover` matemático desenhado no context do canvas, preservando o aspect ratio sem distorcer.
   - A altura da seção de scroll (track) deve ter tamanho suficiente (ex: `h-[400vh]` a `h-[600vh]`) para que o usuário sinta uma rolagem gradual e confortável enquanto o frame atual é calculado:
     `currentFrame = Math.floor(progress * (totalFrames - 1))`.
   - O canvas só deve redesenhar quando o índice do frame realmente mudar para economizar CPU/GPU.

4. **Sincronização dos Textos e Seções (Overlays):**
   - Sobrepostos ao canvas com `z-10`, distribua os blocos de conteúdo da página com transições suaves (fade in, slide up, fade out) amarradas aos checkpoints do scroll.
   - Conforme o usuário rola:
     - **0% a 25%:** [Ex: Título principal e proposta de valor inicial somem suavemente].
     - **25% a 55%:** [Ex: Destaque do problema ou primeiro recurso chave surge no centro/lateral].
     - **55% a 80%:** [Ex: Benefícios detalhados ou estatísticas entram em foco].
     - **80% a 100%:** [Ex: Chamada para ação final (CTA) ganha destaque com botão de conversão].

5. **Responsividade e Otimização:**
   - Ajuste dinâmico de `window.devicePixelRatio` para telas Retina sem sobrecarregar a GPU.
   - Garantir que no mobile o scroll seja suave (`touch-action` adequado, sem pular frames).

---

### 2. CONTEÚDO E COPY DA PÁGINA

Use o seguinte conteúdo fornecido para compor a página:

- **Título / Hero:** [Insira seu Título Principal e Subtítulo aqui]
- **Seção 1 (Recursos / Apresentação):** [Insira o texto ou tópicos do bloco 1]
- **Seção 2 (Diferenciais / Métricas):** [Insira o texto ou tópicos do bloco 2]
- **Chamada Final (CTA):** [Insira o texto do CTA final e para onde o botão direciona, ex: WhatsApp, Checkout ou Cadastro]
- **Cores & Estilo Visual:** [Ex: Tema dark mode, preto profundo `#0a0a0a`, detalhes em neon/azul, tipografia limpa como Inter ou Montserrat]

---

### 3. O QUE ESPERO COMO ENTREGA

- Código modular, limpo e pronto para rodar.
- Arquivo HTML com o Canvas, CSS Tailwind configurado e o script GSAP estruturado.
- Comentários claros indicando exatamente onde alterar o caminho das imagens, a quantidade total de frames e os textos caso eu precise ajustar depois.
