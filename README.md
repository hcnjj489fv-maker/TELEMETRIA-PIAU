[LEIA-ME.txt](https://github.com/user-attachments/files/34649810/LEIA-ME.txt)
RELATORIO DE VEICULOS E MOTORISTAS - PIAU Service
==================================================

O QUE FAZ
---------
Le os relatorios em PDF do rastreador e gera uma planilha Excel pronta (RELATORIO_FROTA.xlsx)
com painel, graficos, percursos, dias rodados/parados, alertas de velocidade e qualidade dos dados.
Nada e inventado: so entra o que esta nos PDFs.


COMO USAR (3 passos)
--------------------
1) Coloque os PDFs novos na pasta  pdf_veiculos
2) De dois cliques em  GERAR_RELATORIO.bat
   (na primeira vez ele instala 2 componentes e precisa de internet; leva 1 ou 2 minutos)
3) Abra  relatorio\RELATORIO_FROTA.xlsx  (a pasta abre sozinha no final)

Pode deixar os PDFs antigos na pasta: o sistema reconhece o que ja foi lido e nao repete.
O historico fica guardado em dados\frota.db - NUNCA apague esse arquivo.

Precisa do Python instalado (python.org/downloads, marcando "Add python.exe to PATH").


COMO COMPARTILHAR
-----------------
Envie o arquivo RELATORIO_FROTA.xlsx por WhatsApp ou e-mail. Quem recebe so precisa do Excel.
Se aparecer a barra amarela "Modo de Exibicao Protegido", clicar em "Habilitar Edicao".
Para mandar em PDF: abra a aba Painel > Arquivo > Exportar > Criar PDF (cabe em 1 pagina).
Cada vez que chegarem PDFs novos, rode o GERAR_RELATORIO.bat e envie o arquivo novo.
Se o Excel estiver com o relatorio aberto na hora de gerar, o novo sai com a data/hora no nome.


O QUE TEM NO EXCEL
------------------
Painel .......... escolha nas caixas amarelas o veiculo, o motorista e o periodo (De/Ate):
                  os 10 cartoes e os 4 graficos mudam sozinhos (sem macros).
Resumo .......... totais por veiculo e por motorista (todo o periodo)
Percursos ....... cada percurso: horarios, hodometro, km, velocidades
Dias ............ cada dia de cada veiculo: Rodou ou Parado
Alertas ......... velocidades acima do limite, com o local
Qualidade ....... inconsistencias detectadas e dados ausentes
Arquivos ........ PDFs lidos, erros e repetidos
Notas ........... como interpretar os numeros
Nas abas de tabela use as setinhas do cabecalho para filtrar e ordenar.


APELIDOS DOS VEICULOS
---------------------
Arquivo config\veiculos.csv (abra no Bloco de Notas), uma linha por carro:
   placa;apelido;modelo
   SGP-8E24;Caminhonete 401;TOYOTA HILUX
Carro novo: acrescente uma linha e rode o GERAR_RELATORIO.bat.

LIMITE DE VELOCIDADE
--------------------
Arquivo config\config.json, campo "limite_velocidade_kmh" (hoje 80). O limite nao vem do PDF.

MOTORISTA
---------
Vem da coluna "Motorista" do PDF. Se estiver vazia aparece "Motorista nao identificado".
(Opcional) escala manual: modelo em config\motoristas_exemplo.csv, salvar como motoristas.csv.


SE DER ERRO
-----------
"Python nao foi encontrado" ..... instale o Python marcando "Add python.exe to PATH".
PDF com erro .................... aparece na tela e na aba Arquivos; os dados ja importados
                                  ficam preservados. Mande o PDF e a mensagem para o Claude.
Windows bloqueou o arquivo ...... botao direito no .zip > Propriedades > marcar "Desbloquear".

PASTAS
------
pdf_veiculos\  PDFs (entrada)    dados\  historico (frota.db)    config\  configuracoes
relatorio\     Excel gerado      processador\  programa (nao mexer)


==================================================================
PAINEL ONLINE (GitHub Pages) - COM SENHA
==================================================================
Ao rodar GERAR_RELATORIO.bat, alem do Excel, e criada a pasta "publicar_online"
com UM arquivo: index.html (o painel, com os dados criptografados).

Na primeira vez o programa pede uma senha (minimo 8 caracteres) e guarda em config\senha.txt.
NAO compartilhe o arquivo senha.txt. Quem tiver a senha ve os dados da frota.

PUBLICAR PELA PRIMEIRA VEZ
1. Crie conta gratuita em github.com
2. Botao verde "New" (novo repositorio): nome painel-frota, marque Public, clique Create repository.
3. Clique em "uploading an existing file", arraste o index.html da pasta publicar_online, clique Commit changes.
4. Settings > Pages > Source: Deploy from a branch > Branch: main, pasta /(root) > Save.
5. Em ~1 minuto o link fica pronto: https://SEU-USUARIO.github.io/painel-frota/

ATUALIZAR (toda vez que chegar PDF novo)
1. Coloque os PDFs em pdf_veiculos e de duplo clique em GERAR_RELATORIO.bat.
2. No GitHub, abra o repositorio > Add file > Upload files > arraste o NOVO index.html (mesmo nome substitui o antigo).
3. Commit changes. Espere ~1 minuto e abra o link com Ctrl+F5.
O link NAO muda.
