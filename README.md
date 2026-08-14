<div align="center">

<img src="./assets/header.svg" alt="Arthur Honorato — Desenvolvimento, Tecnologia, Projetos" width="100%">

<br>

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=19&pause=1200&color=7FB3E0&center=true&vCenter=true&width=620&height=42&lines=Aplica%C3%A7%C3%B5es+completas%2C+do+banco+%C3%A0+interface;React+%C2%B7+TypeScript+%C2%B7+Supabase+%C2%B7+Three.js;Seguran%C3%A7a+e+performance+n%C3%A3o+s%C3%A3o+etapa+final" alt="">

</div>

## Sobre

Escrevo código porque gosto — e porque é assim que fico bom no assunto.

Na prática isso virou o hábito de levar projetos até o fim, não até o ponto em
que funcionam na minha máquina. Um app só está pronto quando tem autenticação
de verdade, quando os dados de uma pessoa não vazam para outra, quando abre
rápido no celular de alguém e quando existe teste segurando o que já foi
consertado uma vez.

Aprendo construindo. Escolho um problema que eu mesmo teria, e vou até esbarrar
nas partes difíceis: modelagem de dados, política de acesso no banco, peso do
bundle, estado assíncrono. Foi assim que aprendi Row Level Security, e foi
assim que descobri que um `manualChunks` mal colocado pode triplicar o primeiro
acesso de um site.

Hoje trabalho principalmente com **React + TypeScript no front** e **Supabase
no back** — Postgres, autenticação e Edge Functions.

<div align="center">

<img src="./assets/stack.svg" alt="Camadas de uma aplicação: interface, domínio, repositório e Postgres com RLS" width="420">

<!--
  ESPAÇO PARA GIF
  Solte um arquivo em assets/anime.gif e troque a linha acima por:
  <img src="./assets/anime.gif" alt="" width="420">
-->

</div>

## Atualmente

- **Construindo** — THealth, acompanhamento de saúde com o corpo em 3D no
  centro da tela.
- **Aprendendo** — Three.js e React Three Fiber a fundo: enquadramento de
  câmera, degradação de qualidade e orçamento de frame.
- **Explorando** — Deno nas Edge Functions do Supabase, e o que muda quando o
  mesmo código precisa rodar em Deno e em Node.

## Tecnologias

**Frontend**

![React](https://img.shields.io/badge/React-0D1117?style=for-the-badge&logo=react&logoColor=7FB3E0)
![TypeScript](https://img.shields.io/badge/TypeScript-0D1117?style=for-the-badge&logo=typescript&logoColor=7FB3E0)
![Vite](https://img.shields.io/badge/Vite-0D1117?style=for-the-badge&logo=vite&logoColor=7FB3E0)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-0D1117?style=for-the-badge&logo=tailwindcss&logoColor=7FB3E0)
![Three.js](https://img.shields.io/badge/Three.js-0D1117?style=for-the-badge&logo=threedotjs&logoColor=7FB3E0)
![React Router](https://img.shields.io/badge/React_Router-0D1117?style=for-the-badge&logo=reactrouter&logoColor=7FB3E0)

**Dados e backend**

![Supabase](https://img.shields.io/badge/Supabase-0D1117?style=for-the-badge&logo=supabase&logoColor=3FB950)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-0D1117?style=for-the-badge&logo=postgresql&logoColor=7FB3E0)
![Deno](https://img.shields.io/badge/Deno-0D1117?style=for-the-badge&logo=deno&logoColor=7FB3E0)
![Node.js](https://img.shields.io/badge/Node.js-0D1117?style=for-the-badge&logo=nodedotjs&logoColor=3FB950)

**Qualidade**

![Vitest](https://img.shields.io/badge/Vitest-0D1117?style=for-the-badge&logo=vitest&logoColor=7FB3E0)
![Testing Library](https://img.shields.io/badge/Testing_Library-0D1117?style=for-the-badge&logo=testinglibrary&logoColor=7FB3E0)
![Zod](https://img.shields.io/badge/Zod-0D1117?style=for-the-badge&logo=zod&logoColor=7FB3E0)
![ESLint](https://img.shields.io/badge/ESLint-0D1117?style=for-the-badge&logo=eslint&logoColor=7FB3E0)

**Ferramentas**

![Git](https://img.shields.io/badge/Git-0D1117?style=for-the-badge&logo=git&logoColor=7FB3E0)
![Vercel](https://img.shields.io/badge/Vercel-0D1117?style=for-the-badge&logo=vercel&logoColor=E6EDF3)
![Netlify](https://img.shields.io/badge/Netlify-0D1117?style=for-the-badge&logo=netlify&logoColor=7FB3E0)

## Projetos

### THealth

Centro pessoal de saúde organizado em torno de uma **representação 3D
interativa do corpo**, em vez de uma parede de cards.

*O problema:* aplicativos de saúde transformam o corpo numa planilha. Peso,
medidas e treinos viram linhas, e você perde a noção de onde aquilo está
acontecendo. Aqui as medidas apontam para a figura, como numa prancha
anatômica — clicar numa região mostra o que foi registrado ali.

Registra corpo, treino, hidratação e alimentação. A estimativa nutricional a
partir de foto é feita por IA e sempre apresentada como **intervalo, nunca como
número exato** — e todo campo que o modelo não sabe volta vazio em vez de
plausível.

Algumas decisões que valeram o trabalho:

- **`user_id` nunca vem do cliente.** Coluna com `DEFAULT auth.uid()`, policy
  validando, e a camada de repositório descartando o campo de qualquer patch —
  três barreiras para o mesmo invariante.
- **A chave da IA nunca chega ao navegador.** Um único núcleo compartilhado
  roda em três hospedagens diferentes, e só ele lê a chave.
- **206 kB no primeiro acesso.** A cena 3D e os gráficos chegam sob demanda; o
  canvas para de desenhar quando a aba sai de vista.
- **91 testes**, herméticos por construção — a suíte não consegue escrever em
  produção nem por acidente.

`React 18` `TypeScript` `Vite` `Tailwind` `Three.js` `React Three Fiber`
`Supabase` `Postgres + RLS` `Edge Functions (Deno)` `Vitest`

<sub>Repositório privado.</sub>

### JobPilot

CRM pessoal para busca de emprego: empresas, contatos, funil de prospecção,
mensagens, follow-ups e análises.

*O problema:* procurar vaga vira uma planilha caótica. Você não lembra quem já
respondeu, quando cobrar de novo, nem o que já mandou para quem.

A decisão que define o projeto: **nada é automático no LinkedIn.** Sem scraping,
sem automação de navegador, sem guardar credencial. O app gera a mensagem e
você cola — e ele só marca como enviada quando *você* confirma. Um app que
dissesse "enviado" só porque copiou estaria mentindo para o próprio usuário.

- **Geração de mensagens 100% local e determinística** — três variações por
  contato, sem chamada a modelo de linguagem.
- **Importação do CSV oficial de conexões**, com correspondência em cascata
  (URL normalizada → e-mail → nome+empresa → aproximação) e resolução linha a
  linha. Aproximação por nome nunca é aplicada sozinha.
- **Leitura de currículo local** — PDF e DOCX no navegador, com OCR sob demanda
  e revisão obrigatória antes de gravar.
- **Exportação CSV protegida contra CSV injection**, e RLS restrito a
  `auth.uid()` em toda tabela.
- **51 testes** cobrindo a lógica determinística.

`React 19` `TypeScript (strict)` `Vite` `Tailwind` `Supabase` `TanStack Query`
`dnd-kit` `Recharts` `pdf.js` `Tesseract.js` `PWA` `Vitest`

## Como eu trabalho

- **Segredo não mora no cliente.** Chave de API vive no servidor. Se está no
  bundle, está público — não importa quão ofuscado.
- **O banco é a última linha de defesa.** Validação no formulário é
  conveniência. RLS é o que de fato separa os dados de duas pessoas.
- **Peso é decisão de produto.** Quantos kB alguém baixa para ver a primeira
  tela é escolha, não consequência.
- **A interface não pode mentir.** Estimativa vem rotulada como estimativa.
  Erro diz o que fazer. Nada finge ter acontecido.

## GitHub

<div align="center">

<img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=tueecode&theme=github_dark" alt="Resumo do perfil de tueecode" width="100%">

<img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=tueecode&theme=github_dark" alt="Linguagens por repositório" width="360">

<img src="https://raw.githubusercontent.com/tueecode/tueecode/output/snake-dark.svg" alt="Gráfico de contribuições animado" width="100%">

</div>

## Contato

<div align="center">

[![Email](https://img.shields.io/badge/Arthurbrghl@gmail.com-0D1117?style=for-the-badge&logo=gmail&logoColor=7FB3E0)](mailto:Arthurbrghl@gmail.com)
[![GitHub](https://img.shields.io/badge/@tueecode-0D1117?style=for-the-badge&logo=github&logoColor=E6EDF3)](https://github.com/tueecode)

<!-- Acrescente LinkedIn ou portfólio aqui quando quiser.
     O Simple Icons não serve mais o ícone do LinkedIn, então este badge é só texto:
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0D1117?style=for-the-badge&labelColor=0D1117&color=0D1117)](https://linkedin.com/in/SEU-USUARIO)
-->

</div>
