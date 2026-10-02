# Metas da Loja

Painel para Fábio, Davy e Alice lançarem as vendas, com tudo consolidado numa planilha do Google Drive.

## O que tem aqui
- `index.html`: o painel (celular e computador). Arquivos de apoio: `manifest.webmanifest`, `icon.svg`, `icon-180.png`, `icon-192.png`, `icon-512.png`.
- `Code.gs`: o script que liga o painel à planilha.

## Parte 1: a planilha (10 minutos, uma vez só)
1. No Google Drive, crie uma planilha nova (nome sugerido: Metas da Loja).
2. Menu **Extensões > Apps Script**. Apague o conteúdo e cole o `Code.gs` inteiro.
3. Nas duas primeiras linhas de código, troque `CODIGO_EQUIPE` (código dos vendedores) e `CODIGO_GESTOR` (só seu).
4. Na barra de cima, escolha a função **setup** e clique em **Executar**. Autorize quando o Google pedir (aparece "app não verificado": Avançado > Acessar). Isso cria as abas Consolidado, Fábio, Davy, Alice, Vendas e Etapa.
5. **Implantar > Nova implantação > App da Web**. Em "Executar como" deixe **Eu**; em "Quem tem acesso" escolha **Qualquer pessoa**. Implante e copie o endereço que termina em `/exec`.

## Parte 2: o painel
1. Abra o `index.html` num editor de texto e cole o endereço na linha `var API_URL = '';`, entre as aspas.
2. Publique de um destes jeitos e mande o link para a equipe:
   - **GitHub Pages**: crie um repositório, envie todos os arquivos desta pasta (menos `Code.gs`, se preferir), vá em Settings > Pages e escolha a branch main. O link sai como `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.
   - **Netlify Drop** (`app.netlify.com/drop`): arraste a pasta e ele devolve um link.
3. No celular: abra o link e use "Adicionar à Tela de Início" (Safari no iPhone, Chrome no Android).

## Uso no dia a dia
- **Gestor** (entra com o código do gestor): aba Etapa para preencher a meta do mês (loja) e todas as etapas (primeiro dia, dias úteis e meta prevista da loja em cada uma); aba Resumo para o consolidado; uma aba por vendedor.
- **Vendedor** (entra com o código da equipe e escolhe o nome): vê quanto falta hoje, quanto precisa vender por dia depois, e lança as vendas.
- Na **planilha**: aba Consolidado (soma da loja e vendas por dia), uma aba por vendedor (meta do dia e falta no dia) e a aba Vendas com todos os lançamentos.
- Novo vendedor: acrescente o nome na aba Etapa da planilha, a partir da linha 6 (coluna A), e salve as metas pelo painel.

## Meta do mês e etapas
- **Meta do mês** (aparelhos e acessórios, da loja toda): valor de referência que você preenche. Ela não muda a meta das etapas. O painel mostra quanto já foi vendido e quanto falta para ela.
- **Etapas**: cada uma tem primeiro dia, dias úteis e a meta **por vendedor** (igual para quem tem meta). São valores absolutos, preenchidos por você.
- **Meta do dia** dentro da etapa: no primeiro dia, meta ÷ dias úteis. Do segundo dia em diante, (meta − vendido até o dia anterior) ÷ dias úteis que restam, contando o dia. Dia que passou sem venda aumenta a meta dos seguintes; dia futuro usa o ritmo de hoje.
- **Entre etapas**: o que faltou (ou sobrou) numa etapa já encerrada é somado (ou abatido) na meta cadastrada da etapa seguinte. A etapa só conta como encerrada depois do último dia dela.

## Atualizando o Code.gs (uma vez, ao receber a versão com meta do mês)
1. No Apps Script, copie as suas duas linhas de código (`CODIGO_EQUIPE` e `CODIGO_GESTOR`) para algum lugar.
2. Apague tudo, cole o `Code.gs` novo e coloque de volta os seus dois códigos.
3. **Implantar > Gerenciar implantações > lápis > Versão: Nova versão > Implantar.** O endereço continua o mesmo.
4. A aba Etapa da planilha é convertida sozinha na primeira vez que o painel carregar (a etapa atual vira a Etapa 1, com a mesma meta por vendedor). Depois, abra a aba Etapa do painel, preencha a meta do mês e as demais etapas e salve.

## Segurança
Quem tiver o link e o código da equipe consegue ver e lançar vendas. Troque o código quando alguém sair da equipe (edite no Apps Script e crie uma nova versão da implantação).
