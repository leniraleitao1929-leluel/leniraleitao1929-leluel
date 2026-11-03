<p align="center"><a href="../README.md">← Voltar ao perfil</a></p>

# VozClara · Tato Digital

**Dar voz ao que os olhos não veem.**

[Abrir a app](https://tatodigital.lovable.app) · Estudo de caso · Protótipo funcional · Lisboa, 2026

Uma app para pessoas cegas e com baixa visão que diz a **cor da roupa**, lê **cartas e rótulos** com a câmara, descreve o que está à frente, diz **onde a pessoa está** e lê documentos em voz alta para estudar. Criada por Lenira Leitão e testada pela irmã, que é cega.

| 2 semanas | 53 | 145 | 0 € |
|:-:|:-:|:-:|:-:|
| de construção | versões publicadas | testes automáticos | por mês |

---

## O problema: pequenas tarefas que ainda dependem de outra pessoa

A irmã da Lenira é cega. Para saber de que cor são as meias do bebé, se uma carta é uma conta para pagar ou em que rua está, precisa muitas vezes de alguém por perto. Há apps para isto, mas quase todas estão em inglês ou em português do Brasil, pedem várias instalações ou tornam-se complicadas para quem não tem à vontade com tecnologia.

O objetivo da VozClara é uma app só, em português de Portugal, que se usa com a voz ou com poucos botões grandes, fala com calma e funciona num telemóvel Android comum.

> «O mais importante são as cores. A minha irmã fica sempre à espera de alguém por perto para saber a cor das coisas, das roupas do bebé, das meias.» — Lenira

---

## O que faz: duas partes, para duas necessidades

A VozClara fica simples para quem só quer ouvir os seus papéis. Quem estuda tem uma área à parte, o Tato Digital, com o botão Estudos.

### VozClara · o dia a dia

| Função | O que faz | Exemplo |
|---|---|---|
| **Cores e luz** | Diz a cor da peça que a pessoa segura ao centro da câmara, as várias cores de uma peça e onde estão, e se a luz está acesa. | «Que cor é esta meia?» |
| **Ler agora** | Lê cartas, embalagens, prazos de validade e ementas com a câmara. Primeiro no telemóvel, sem internet, e com a IA quando é preciso mais certeza. | «Lê isto para mim.» |
| **Descrever** | Diz o que está à frente da câmara, com posições e possíveis perigos, e que notas e moedas a pessoa tem na mão. | «Que nota é esta?» |
| **Onde estou** | Diz a rua e o número mais próximos e permite partilhar a localização com a família. | «Onde é que eu estou?» |
| **Documentos** | Abre PDFs e fotografias de cartas, guarda-os e lê-os em voz alta, parágrafo a parágrafo, retomando onde parou. | «Continuar a ouvir.» |
| **Botão Falar** | Percebe pedidos ditos com as palavras de cada pessoa e faz logo a ação, sem ter de decorar comandos. | «Que horas são?» |

### Tato Digital · os estudos

| Função | O que faz | Exemplo |
|---|---|---|
| **Cadernos de estudo** | Organiza os PDFs por disciplina, como Direito ou Biologia, com a percentagem já ouvida de cada um. | «Abrir o caderno de Direito.» |
| **Onde é que eu parei?** | Volta ao último documento e continua a ler do mesmo sítio. | «Onde é que eu parei?» |
| **Resumos e perguntas** | Explica a matéria em linguagem simples, responde a perguntas sobre o documento e faz testes para rever. | «Criar resumo.» |

---

## Por dentro: o que acontece quando se pergunta «que cor é esta?»

Cada passo tem um plano B, porque quem não vê não pode ficar sem resposta.

1. **Ouvir o pedido** *(telemóvel · reconhecimento de voz)*: o próprio Chrome transforma a voz em texto. A app procura a ideia principal da frase («cor», «meia») e, se não perceber, pergunta à IA o que a pessoa quer.
2. **Ver a peça** *(telemóvel · câmara)*: abre a câmara, acende a lanterna se houver pouca luz, tira cinco imagens seguidas e uma fotografia nítida. Se a imagem estiver desfocada ou só mostrar a mão, diz como corrigir.
3. **Uma primeira resposta, sem internet** *(telemóvel · cálculo de cores)*: olha só para o centro da imagem, corrige o tom amarelado da luz de casa, tira a cor da pele e vota entre as cinco imagens para não se enganar com uma imagem tremida.
4. **Confirmar com a IA** *(servidor · IA Gemini)*: envia a fotografia à IA da Google, que percebe melhor a luz e as sombras. Se ela demorar mais de 5 segundos, a app diz já a cor do telemóvel e avisa «Já pode baixar o objeto». A IA confirma depois.
5. **Dizer a resposta com calma** *(telemóvel · voz)*: fala com a voz do Google, a um ritmo tranquilo. Se essa voz falhar ou ficar muda, entra uma voz de reserva da própria app, que funciona sem internet.

---

## Como foi feita: as ferramentas, explicadas sem jargão

Quase tudo é gratuito ou corre no próprio telemóvel.

### Construir e publicar

| Ferramenta | Para que serve |
|---|---|
| **Lovable** · construtor de apps web | Criou a primeira versão a partir de descrições escritas e é onde a app fica publicada, em tatodigital.lovable.app. |
| **GitHub** · arquivo do código | Guarda todo o código e o histórico de cada alteração, com uma explicação do porquê. |
| **Claude Code** · assistente de programação com IA | Escreveu e corrigiu o código a partir dos pedidos e dos testes, sempre em português, e correu os testes automáticos antes de cada envio. |

### A app por dentro

| Ferramenta | Para que serve |
|---|---|
| **React, TanStack Start, TypeScript e Tailwind** | A base dos ecrãs, botões e navegação. A app abre no Chrome e pode ser instalada no ecrã principal como uma app normal. |
| **Lovable Cloud (Supabase)** · contas e base de dados | Guarda as contas e os documentos de cada pessoa. Regras de segurança na base de dados garantem que cada pessoa só vê os seus documentos. |
| **Voz e microfone do Chrome** · Web Speech API | A voz que lê e o reconhecimento do que a pessoa diz vêm do próprio telemóvel, sem custo. |
| **Voz de reserva** · eSpeak, através do meSpeak | Uma voz dentro da app que funciona sem internet e só entra quando a voz do telemóvel falha. |
| **Leitura de texto no telemóvel** · Tesseract.js (OCR) | Reconhece as letras de uma fotografia no próprio telemóvel, sem enviar a imagem para lado nenhum. |
| **IA Gemini, da Google** · plano gratuito | Descreve o que está à frente, reconhece notas, lê textos difíceis, confirma as cores e percebe pedidos de voz menos comuns. |
| **Cálculo de cores** · escrito para esta app | Compara cada cor com uma paleta de nomes em português, corrige a luz amarela de casa e ignora a pele da mão. |
| **OpenStreetMap e BigDataCloud** · mapas gratuitos | Transformam a posição do GPS numa morada falada: rua, número, bairro e cidade. |

### Testar antes de publicar

| Ferramenta | Para que serve |
|---|---|
| **Vitest** · testes automáticos | 145 testes verificam as partes sensíveis, por exemplo: «a frase lê isto para mim não pode ser entendida como parar». |
| **Playwright** · browser automático | Abre a app como um telemóvel, cria uma conta, carrega nos botões, simula a voz e o microfone e confirma o que a app diz. |
| **axe** · verificador de acessibilidade | Procura problemas para quem usa leitor de ecrã ou vê pouco: botões sem nome, contraste fraco, títulos fora de ordem. |

---

## Testado com quem usa: o que foi encontrado e como ficou resolvido

A maior parte das melhorias veio de usar a app na rua e em casa, com TalkBack ligado.

| Problema | Solução |
|---|---|
| A voz do telemóvel deixava de falar de um dia para o outro e a app ficava muda. | Uma voz de reserva dentro da app, que entra sozinha quando a do telemóvel falha. |
| A voz era rápida demais, até para ouvir as instruções. | Ritmo mais calmo por omissão, com «devagar» e «um pouco mais rápida» à escolha. |
| O preto não era reconhecido e a app dizia várias cores ao mesmo tempo. | Olhar só para a peça na mão, corrigir a luz de casa, ignorar a pele e confirmar com a IA. |
| Um objeto preto aparecia como «cinzento claro»: a câmara estava a ver um dedo desfocado. | A app percebe quando a imagem está desfocada ou só mostra a mão e diz como segurar a peça. |
| Esperar até 30 segundos pela IA com a peça na mão. | Resposta do telemóvel em poucos segundos, com «Já pode baixar o objeto», e a IA a confirmar depois. |
| Com o TalkBack ligado, ouviam-se duas vozes ao mesmo tempo nos documentos. | A voz de reserva cala-se assim que a voz do telemóvel começa, mesmo que comece tarde. |
| O botão Falar só percebia frases decoradas e respondia sempre «não percebi». | Percebe frases do dia a dia e, quando não percebe, pede ajuda à IA antes de desistir. |
| Ecrãs pretos e textos longos cansam quem vê pouco. | Azul escuro com dourado, letras grandes, menos texto por ecrã e a área de estudos separada. |

---

## Em números (de 16 a 29 de outubro de 2026)

| | |
|---|---|
| Versões no histórico do GitHub | **53** |
| Linhas de código da app | **11 800** |
| Testes automáticos a passar | **145** |
| Custo mensal em servidores e IA | **0 €** |

---

## Com franqueza: limites atuais

- A IA gratuita da Google às vezes demora ou está sobrecarregada. Nesses momentos fica a resposta do telemóvel, que é menos certa.
- Sem a IA, as cores ainda falham com várias peças juntas ou com pouca luz.
- Depende da voz do Chrome no Android, que varia de telemóvel para telemóvel.
- Foi testada por uma pessoa. Ainda não há dados de um grupo maior de utilizadores.

## Próximos passos

- Testar com 5 a 10 pessoas cegas e com baixa visão, em parceria com uma associação como a ACAPO.
- Gravar um vídeo curto da app a ser usada no dia a dia.
- Uma versão para a Play Store, com acesso direto à voz e à câmara do telemóvel.
- Na área de estudos: resumos curtos, médios ou detalhados e anotações por voz.

---

## O meu papel

A ideia, as decisões de produto, os testes no dia a dia com a minha irmã e a direção de cada correção foram meus. O código foi escrito com ferramentas de IA (Lovable e Claude Code), a partir dos meus pedidos e do que a minha irmã sentiu ao usar a app.

Aprendi a transformar uma necessidade real em requisitos claros, a testar com quem usa, a explicar um problema com provas (capturas, registos de voz) e a decidir o que mudar sem estragar o que já funciona.

*Para a minha irmã, que testou cada versão.*
