# páginas para iPhone — V1 (grátis, sem Mac)

Como funciona: o **GitHub** compila o app numa máquina Mac na nuvem e entrega um arquivo `paginas.ipa` **sem assinatura**. Depois, no seu PC, o **Sideloadly** assina esse arquivo com o **seu Apple ID grátis** e instala no iPhone por cabo.

Limites da conta grátis da Apple (não dá para evitar): o app **para de abrir a cada 7 dias** e precisa ser reinstalado pelo Sideloadly (seus dados ficam), no máximo **3 apps** assim ao mesmo tempo e uns 10 identificadores novos por semana. Sem notificações push da Apple.

Dentro do app é a mesma v0.9 (estante modular, metas, lixeira, etc.).

---

## PARTE A — Gerar o arquivo .ipa no GitHub (uma vez, uns 20 minutos)
1. Entre no **github.com** com a sua conta.
2. Clique no **+** (canto superior direito) → **New repository**. Nome: `paginas-ios`. Pode ser **Private**. Clique em **Create repository**.
   - Dica: máquinas Mac gastam 10 vezes mais minutos do plano grátis. Em repositório **Private** dá para uns 20 builds por mês; em **Public** não há limite. O que fica público é só o código, nunca os seus dados.
3. Descompacte este zip no computador. Na página do repositório vazio, clique em **uploading an existing file** e arraste as pastas `www` e `assets` e os arquivos `package.json`, `capacitor.config.json` e `build-ipa.yml`. Clique em **Commit changes**.
4. Crie o arquivo que manda o GitHub compilar:
   - **Add file → Create new file**.
   - No nome, escreva exatamente: `.github/workflows/build-ipa.yml`
   - Abra o `build-ipa.yml` do zip no VS Code, copie tudo e cole na caixa do GitHub.
   - **Commit changes**.
5. Aba **Actions** → **Gerar IPA (iPhone)**. Se pedir, clique em *I understand my workflows, go ahead and enable them*. A bolinha amarela significa que está compilando (10 a 15 minutos). Quando ficar **verde ✓**, terminou. Se não começar sozinho: **Run workflow**.
6. Abra a execução verde, role até **Artifacts** e clique em **paginas-ipa**. Descompacte o zip baixado: dentro está o **paginas.ipa**.

## PARTE B — Preparar o PC (uma vez)
1. Baixe o **Sideloadly** em **sideloadly.io** (versão Windows) e instale.
2. No Windows, o Sideloadly precisa do **iTunes** e do **iCloud** instalados a partir do **site da Apple** (não da Microsoft Store). Se faltar algo, ele avisa na tela.
3. Tenha o **cabo USB** do iPhone.

## PARTE C — Preparar o iPhone (uma vez)
1. Conecte o iPhone ao PC. Toque em **Confiar** neste computador e digite o código.
2. Ative o **Modo de Desenvolvedor**: *Ajustes → Privacidade e Segurança → Modo de Desenvolvedor*, ligue e reinicie o iPhone. Se a opção não aparecer, tente a Parte D uma vez (ela aparece depois da primeira tentativa de instalar) e volte aqui.
3. Use um **Apple ID grátis com verificação em duas etapas**. Opcional: crie um Apple ID só para isso, para não misturar com o seu principal.

## PARTE D — Instalar o app
1. Abra o **Sideloadly** com o iPhone conectado. Ele aparece em *Device*.
2. Arraste o **paginas.ipa** para a janela.
3. Digite o seu **Apple ID** e clique em **Start**. Digite a senha e o código de verificação que chegar no iPhone.
4. Espere aparecer **Done**.
5. No iPhone: *Ajustes → Geral → VPN e Gerenciamento de Dispositivo* → toque no seu Apple ID → **Confiar**.
6. Abra o app **páginas** pelo ícone.

## PARTE E — Manter funcionando
- **A cada 7 dias** (marque no calendário o dia 6): conecte o iPhone, abra o Sideloadly, arraste o **mesmo paginas.ipa** e clique em Start de novo. Como é o mesmo app, **seus livros e dados continuam**.
- **Backup:** em *Configurações → Seus dados → Exportar*, de vez em quando. Se você apagar o ícone do app, os dados somem.
- **Atualizar o app:** no GitHub, abra a pasta `www`, use **Add file → Upload files** e envie o `index.html` novo (substitui o antigo). O GitHub compila de novo; baixe o novo `.ipa` e instale por cima pelo Sideloadly.
- **Alternativa ao Sideloadly:** o **AltStore** (altstore.io) renova sozinho a cada 7 dias enquanto o PC estiver ligado na mesma rede Wi-Fi. Funciona com o mesmo `.ipa`.

## Lembretes de leitura
O app agenda avisos no próprio iPhone (até uns 57 por vez; o iOS aceita 64). Ao ligar, o iPhone pede permissão. A expectativa é que cheguem com o app fechado, mas **não pude testar isso aqui**.

## Se algo der errado
- **Bolinha vermelha ✗ no GitHub:** abra a execução, clique no passo marcado em vermelho e copie as últimas linhas da mensagem. Me envie que eu corrijo. A primeira compilação num Mac novo pode precisar de um ajuste.
- **“ERRO: não encontrei o arquivo index.html”:** envie a pasta `www` do zip para o repositório.
- **“Maximum App ID limit reached” no Sideloadly:** é o limite semanal da Apple; espere ou use outro Apple ID.
- **O Sideloadly diz que o Bundle ID já existe:** em *Advanced Options* troque o Bundle ID por algo seu, como `com.seunome.paginas`. Atenção: isso cria um app separado, com dados novos.
- **“Desenvolvedor não confiável” ao abrir:** faça o passo D5.
- **O app abre cortado perto do entalhe:** me diga o modelo do iPhone que eu ajusto.

## Observação
Nunca digite a senha do seu Apple ID em outro lugar que não o Sideloadly/AltStore oficiais. Este projeto não usa nenhuma conta paga e não publica nada na App Store.
