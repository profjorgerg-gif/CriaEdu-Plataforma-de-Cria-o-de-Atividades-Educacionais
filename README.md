# CriaEdu — Plataforma de Criação de Atividades Educacionais (PCAE)

Protótipo para criar, organizar e adaptar atividades: exercícios, provas, trabalhos, estudos de caso, Recuperação Paralela (RP), Regime de Atendimento Domiciliar (RAD) e atividades adaptadas para alunos PCD.

## O que já funciona (v0.15)

- **Novo modelo de documento (aprovado em 23/10/2026)**: cabeçalho em grade com rótulos acima dos dados, quadro de nota ao lado de Aluno e Assinatura, Observações no padrão "Título – texto", título sem linha repetida, questão com faixa "QUESTÃO n · pontos", parágrafos com recuo de 1,25 cm, dados no formato "item: valor" em tabela automática, código da atividade no rodapé de cada página e numeração no canto superior direito. Moldura opcional (Cabeçalho › Blocos › Moldura na página).
- **Documentos no padrão ABNT (NBR 14724)**: uma única fonte (Arial ou Times New Roman, escolhida em Modelos e diretrizes), texto em 12 pt com espaçamento 1,5 e justificado, cabeçalho, tabelas e notas em 10–11 pt, margens de 3 cm (superior e esquerda) e 2 cm (inferior e direita), páginas numeradas no canto superior direito.
- **Impressão e PDF corrigidos**: quebras de página respeitadas (folhas de cálculo sempre em página própria), sem páginas em branco no final e sem linhas cortadas no PDF por aluno.
- **Assinatura do aluno** no cabeçalho (campo que pode ser marcado ou desmarcado).
- **Folhas de cálculo** nas questões de cálculo: cada folha em página própria, com o cabeçalho da 1ª página, o título FOLHA DE CÁLCULO e o restante da página em branco.
- **Novos critérios** criados direto na lista de escolha, com 10 sugestões prontas.
- **Página de entrada**: no padrão das plataformas do CEDUP (verde e dourado), com acesso exclusivo para professores pela conta Google e a opção de usar sem entrar (dados só no navegador).
- **Nuvem (Firebase)**: login com Google e salvamento automático no Firestore. Cada professor tem um espaço próprio e só ele acessa (regras em `firestore.rules`). Na primeira entrada, os dados que já estão no navegador são enviados para a nuvem. Sem configuração, a plataforma continua funcionando só no navegador.
- **Correção com o assistente que você já usa (Claude, ChatGPT ou Gemini)**: a plataforma monta as instruções com o gabarito de cada código e o formato da resposta; você copia, cola no chat e anexa as entregas (há um .zip com as fotos renomeadas pelo código do aluno, por lote). O assistente devolve a correção em um arquivo .zip (um .json por aluno, nomeado pelo código, e um consolidado); você baixa e envia o .zip na plataforma, que associa cada resultado ao aluno. Se o assistente não gerar arquivos, dá para colar a resposta em texto: notas, respostas por questão e feedbacks são preenchidos para revisão. Não precisa de chave de API.
- **Uma atividade por aluno**: cada aluno escolhido recebe o próprio arquivo, com código individual (ex.: `PRV-2026-0006-03`) e nome do arquivo no padrão `código_NOME_DO_ALUNO`. Com vários alunos, os arquivos Word ou PDF vêm juntos em um .zip; também é possível gerar um arquivo único com todos.
- **Versões diferentes por aluno**: embaralhar a ordem das questões (com opção de manter questões na posição), embaralhar alternativas e afirmativas, e sortear questões e valores de cálculo diferentes para cada aluno. A versão do professor traz o gabarito individual de cada código.
- **Gerador automático de questões**: múltipla escolha, verdadeiro ou falso, afirmativas (I, II, III com "Apenas I e II…") e cálculo (com ou sem alternativas), com gabarito e resolução automáticos. Temas: regimes de caixa e competência, DRE e CMV, imobilizado e depreciação, PECLD, princípios e NBC, fluxo de caixa, capital de giro e liquidez, juros, custos e ponto de equilíbrio, gestão de pessoas (turnover e absenteísmo). O nível segue a dificuldade da atividade.
- **Correção**: importa o .zip baixado do Classroom (ou fotos/PDFs), associa cada arquivo ao aluno pelo nome, código ou matrícula, e permite corrigir marcando as respostas, pelo assistente de IA (copiar e colar) ou, opcionalmente, pela API da Anthropic. Calcula a nota de 0 a 10, gera o feedback objetivo para copiar e enviar ao aluno e exporta as notas (.csv).
- **Modalidade da atividade**: Trimestral, Semestral, RAD ou Adaptada. Define os períodos do título (1º–3º TRI ou 1º–2º SEM), acrescenta "– RAD" ou "– ADAPTADA" na caixa de título e serve de filtro no banco.
- **Cabeçalho no modelo da escola**: faixa oficial (brasão, identificação e logotipo do CEDUP), caixa de título (ex.: PROVA PR1 1º TRI 2026), aluno, matrícula, disciplina, professor, curso, data, turma, prazo, código, quadro de nota, critérios para a prova e termo de desistência.
- **Modelos de cabeçalho prontos**: Prova com nota no gabarito, Prova com quadro de nota, Recuperação Paralela, 2ª chamada com entrega pelo Classroom, Atividade/trabalho, RAD e Tabela compacta. Podem ser duplicados e editados.
- **Escolhas por atividade**: no editor, o professor marca ou desmarca cada campo, bloco e critério só daquela atividade, e pode gravar as escolhas no modelo.
- **Word com imagens**: o arquivo .doc é gerado em formato MHTML, que leva a faixa embutida.
- **Código de identificação** automático para cada atividade (ex.: `PRV-2026-0007`): prefixo pelo tipo (EXE, PRV, TRB, CAS, RP, RAD), ano e número sequencial. Cópias e adaptações recebem código novo e guardam o código de origem.
- **Turma por PDF**: importa o PDF "Estudantes da Turma" do sistema da escola e extrai o código e o nome da turma, os nomes dos alunos e as matrículas. Permite conferir antes de criar, atualizar uma turma existente (pela matrícula) e incluir ou remover alunos manualmente.
- **Atividade por aluno**: no editor, escolha a turma e marque os alunos. A versão do aluno sai com uma cópia por aluno, cada uma com nome, nº de chamada, matrícula, prazo de entrega e código. A versão do professor lista os alunos com espaço para a nota.
- **Cadastros**: disciplinas, turmas, conteúdos e objetivos de aprendizagem.
- **Editor de atividades**: tipo, nível de dificuldade, orientações, questões (dissertativa, múltipla escolha, V/F, cálculo, situação prática), gabarito, pontuação por questão e critérios de avaliação, com conferência do total 10,0.
- **Adaptações**: TEA, TDAH, dislexia, discalculia, deficiência intelectual, síndrome de Down, baixa visão, surdez, deficiência física, altas habilidades e "outra condição". Cada perfil ajusta a formatação da versão do aluno e gera um plano de adaptação na versão do professor.
- **Versões aluno e professor** com o cabeçalho da escola.
- **Exportação**: Word (.doc), PDF (pela janela de impressão) e texto para Classroom/e-mail.
- **Banco de atividades**: pesquisa, filtros, reutilizar e adaptar.
- **Modelos e diretrizes**: cabeçalho, logotipo, diretrizes de elaboração e avaliação, modelos por tipo de atividade e modelos próprios.
- **Backup**: exportar/importar .json.

## Arquivos do repositório

| Arquivo | Para que serve |
|---|---|
| `index.html` | A plataforma completa |
| `firebase-config.js` | Configuração do projeto Firebase (preenchida no passo 2.5) |
| `firestore.rules` | Regras de segurança do banco (coladas no console, passo 2.4) |
| `README.md` | Este roteiro |

## Implantação para testes reais

### Parte 1 — GitHub (repositório e site)

1. Em github.com, clique em **New** (novo repositório).
   - Nome: `CriaEdu`
   - Visibilidade: **Public** (no plano gratuito, o GitHub Pages exige repositório público; só o código fica público, os dados ficam no Firebase)
   - Marque **Add a README file** e clique em **Create repository**.
2. No repositório: **Add file → Upload files** → arraste `index.html`, `firebase-config.js`, `firestore.rules` e `README.md` → **Commit changes**.
3. **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main` e pasta `/ (root)` → **Save**.
4. Aguarde 1 a 2 minutos. O endereço será `https://SEU-USUARIO.github.io/CriaEdu/`. Abra e confira se a plataforma carrega (ainda sem nuvem).

### Parte 2 — Firebase (console)

1. Em console.firebase.google.com, clique em **Criar um projeto**.
   - Nome: `criaedu-pcae` (ou outro)
   - Google Analytics: pode **desativar**
   - Clique em **Criar projeto**. O plano gratuito (Spark) atende aos testes.
2. **Criação → Authentication → Vamos começar** → aba **Método de login** → **Google** → **Ativar** → escolha o e-mail de suporte → **Salvar**.
3. Ainda em Authentication: **Configurações → Domínios autorizados → Adicionar domínio** → `SEU-USUARIO.github.io` → **Adicionar**.
4. **Criação → Firestore Database → Criar banco de dados**
   - Local: `southamerica-east1 (São Paulo)`
   - Modo: **produção**
   - Depois de criado, abra a aba **Regras**, apague o conteúdo, cole o conteúdo do arquivo `firestore.rules` e clique em **Publicar**.
5. **Configurações do projeto** (engrenagem) → **Geral** → em *Seus apps*, clique no ícone **Web `</>`**
   - Apelido: `CriaEdu` (não precisa marcar Firebase Hosting) → **Registrar app**
   - Copie os valores do `firebaseConfig` (apiKey, authDomain, projectId, storageBucket, messagingSenderId, appId).
6. No GitHub, abra `firebase-config.js` → ícone de lápis (**Edit**) → cole cada valor entre as aspas → **Commit changes**.

### Parte 3 — Primeiro teste

1. Abra `https://SEU-USUARIO.github.io/CriaEdu/` (se já estava aberto, recarregue com Ctrl+F5).
2. Clique em **Entrar com Google** (barra lateral ou aba *Backup e nuvem*) e escolha a sua conta.
3. Na primeira entrada, os dados deste navegador são enviados para a nuvem. A barra lateral passa a mostrar "Salvo na nuvem às …".
4. Teste em outro computador ou navegador: entre com a mesma conta e confira se as turmas e atividades aparecem.

### Se algo não funcionar

| Mensagem | O que fazer |
|---|---|
| "Este endereço não está autorizado no Firebase" | Parte 2, passo 3: adicione `SEU-USUARIO.github.io` nos domínios autorizados |
| "sem permissão (confira as regras do Firestore)" | Parte 2, passo 4: publique as regras do `firestore.rules` |
| Botão "Entrar com Google" não aparece | Confira se o `firebase-config.js` foi salvo com o `apiKey` preenchido e recarregue com Ctrl+F5 |
| A janela de login fecha sem entrar | Permita pop-ups para o endereço do GitHub Pages no navegador |

### Observações

- As fotos das entregas de correção não vão para a nuvem (ficam só na sessão); notas, correções e feedbacks vão.
- O Firebase Storage (para guardar fotos) e as Cloud Functions (para a IA sem chave no navegador) exigem o plano Blaze, com cobrança por uso. Ficam para a próxima etapa, se forem necessários.
- A leitura de PDF usa a biblioteca pdf.js (cdnjs), por isso a importação de turmas precisa de internet.

## Histórico de versões

Cada atualização é entregue em um .zip com data e hora no nome (ex.: `criaedu_2026-10-23_08h40.zip`). No GitHub, envie o conteúdo do zip por **Add file › Upload files** e use a mensagem de commit `Atualização AAAA-MM-DD HHhMM: descrição`.

| Versão | Data | Principais mudanças |
| --- | --- | --- |
| v0.15 | 23/10/2026 | Novo modelo de documento aprovado (cabeçalho em grade, tabela de dados, rodapé com código, moldura opcional) |
| v0.14 | 23/10/2026 | Folha de cálculo com a página em branco (sem pauta e sem "Resposta final") |
| v0.13 | 23/10/2026 | Padrão ABNT nos documentos; correção da impressão e do PDF |
| v0.12 | 23/10/2026 | Assinatura do aluno no cabeçalho |
| v0.11 | 23/10/2026 | Folhas de cálculo com cabeçalho; correção do PDF por aluno |
| v0.10 | 22/10/2026 | Criar critérios na lista de escolha e sugestões |
| v0.9 | 22/10/2026 | Página de entrada (só professores) |
| v0.8 | 22/10/2026 | Nuvem: login Google e Firestore |
| v0.5–v0.7 | 22/10/2026 | Gerador de questões, versões por aluno, correção com IA |
| v0.1–v0.4 | 22/10/2026 | Protótipo, turmas por PDF, cabeçalho da escola, modalidades |

## Próximas etapas (rumo à implantação)

| Etapa | Entrega |
|---|---|
| 1. Validação do protótipo | Uso real com 2 ou 3 turmas; ajustes no cabeçalho, modelos e fluxo de criação |
| 2. Modelos oficiais da escola | Importar os arquivos Word de provas, gabaritos e cabeçalhos usados hoje |
| 3. Firebase ✔ | Login com Google e dados no Firestore (feito na v0.8). Próximo: fotos no Storage e IA em Cloud Function (plano Blaze) |
| 4. Migração dos dados ✔ | Automática na primeira entrada com Google |
| 5. Exportação avançada | Word .docx nativo e PDF direto, sem a janela de impressão |
| 6. Classroom | Integração com a API do Google Classroom para publicar atividades |
