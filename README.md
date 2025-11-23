# ✨ Diário de Inspirações

## 📖 Descrição do projeto:
O **Diário de Inspirações** é um agente de autoconhecimento criado no AI Foundry do Microsoft Azure.  
Ele conduz o usuário em um registro diário de inspiração, filtrando se a origem veio de um **filme, série, música, livro ou situação cotidiana**.  
Com base nas respostas, o agente gera um **texto curto, poético e reflexivo**, que amplia a capacidade de enxergar diferentes perspectivas e estimula a criatividade.  

O texto é enviado **imediatamente por e-mail** para o usuário, criando um diário digital de inspirações que pode ser revisitado no futuro.

---
## 🎯 Objetivos:
- Incentivar o hábito diário de reflexão e criatividade;  
- Registrar frases, situações e sentimentos que marcaram o dia;  
- Construir um acervo pessoal de inspirações para revisitar e se inspirar novamente.

---
## 🔄 Fluxo do agente:

<img width="1586" height="712" alt="Página inicial do Agente" src="https://github.com/user-attachments/assets/eb28cb5f-7b63-475f-a35e-4d4402810164" />  

O funcionamento do **Diário de Inspirações** segue um fluxo simples e estruturado, garantindo que cada interação se transforme em um registro reflexivo:

1. **Origem da inspiração**  
   O agente pergunta se a inspiração veio de um **filme, série, música, livro ou situação cotidiana**.  

2. **Detalhamento da inspiração**  
   - Se for mídia (livro, série, filme ou música) → o agente solicita a **frase que marcou**.  
   - Se for situação cotidiana → o agente pede para descrever a **situação vivida**.  

3. **Sentimento despertado**  
   O usuário resume em poucas palavras o **sentimento** gerado pela inspiração.  

4. **Reflexão adicional**  
   O agente pergunta se há alguma **reflexão complementar**, incentivando o usuário a expandir o pensamento.  

5. **Geração do texto poético**  
   Com base nas respostas, o agente cria um **texto curto, poético e reflexivo**, que amplia perspectivas e estimula a criatividade.  

6. **Envio automático por e‑mail**  
   O texto gerado é enviado imediatamente para o endereço de e‑mail configurado, criando um **diário digital de inspirações** que pode ser revisitado no futuro.  

---

## ⚙️ Instruções do Agente (O Prompt utilizado):
- Você é um agente chamado Diário de Inspirações.
- Sua função é guiar o usuário em um registro diário de inspiração e transformá-lo em um texto curto e reflexivo.
- Seja acolhedor e curioso, mantendo um tom humano e empático.
- Conduza a interação passo a passo, filtrando a origem da inspiração.
- Ao final, compile as respostas em um texto reflexivo breve e poético.
- O texto deve ampliar a capacidade de enxergar diferentes perspectivas e estimular a criatividade.
- Envie o texto por e-mail imediatamente após a interação para nagela**@****.com. 

### Fluxo de perguntas:
1. Pergunte: “Sua inspiração de hoje veio de um filme, série, música, livro ou de uma situação cotidiana?”
2. Se for filme, série, música ou livro:
    - Pergunte: “Qual foi a frase que te marcou?”
3. Se for situação cotidiana:
    - Pergunte: “Qual foi a situação que te inspirou?”
4. Pergunte: “Resuma brevemente o que essa frase ou situação fez você sentir.”
5. Pergunte: “Há alguma reflexão que você gostaria de compartilhar sobre isso?”
6. Compile todas as respostas em um texto reflexivo que:
    - Cite a fonte (frase ou situação).
    - Expresse o sentimento relatado.
    - Acrescente uma reflexão que amplie o olhar, como se fosse um conselho ou insight.
      
---
## 🛠️ Etapas do desenvolvimento:
Para o funcionamento do agente, foi necessário definir o modelo de linguagem a ser utilizado.  
Na sessão de *catálogo de modelos*, escolhi o **GPT‑4o‑mini** por ser leve e rápido, oferecendo um equilíbrio ideal entre criatividade, eficiência e baixo custo. Essa escolha garantiu que o agente pudesse responder de forma ágil e consistente, sem perder a capacidade de gerar reflexões criativas.

<img width="700" height="auto" alt="Escolha do modelo de linguagem" src="https://github.com/user-attachments/assets/da97cb86-6714-42a5-b0cb-a8d581be38ef" />  

A região escolhida foi a *East US 2*, por garantir disponibilidade do modelo. Após testes em outras regiões, essa se mostrou a mais estável e adequada para o funcionamento do agente.  

Com as instruções e objetivos definidos, configurei uma **ação de envio de e‑mails**, conectando e habilitando o Outlook para que o agente pudesse encaminhar automaticamente os diários criados. Para isso, foi criada uma *ação do Aplicativo Lógico*, responsável por disparar os e‑mails assim que o texto reflexivo é gerado.  

<img width="1512" height="846" alt="Adicionar ação do arquivo lógico" src="https://github.com/user-attachments/assets/cbceed2b-575d-4b28-a2a3-9d9f496ea487" />  

Essa integração tornou o fluxo contínuo: inspiração → reflexão → envio imediato.  

<img width="1508" height="850" alt="Invocar ferramenta de envio de e-mail" src="https://github.com/user-attachments/assets/a7909a77-a59d-44fc-9a59-504eeda2984b" />  

Desta forma, a ferramenta passou a ficar disponível na tela inicial de configuração do Agente:

<img width="603" height="638" alt="Ação de envio de e-mail inserida" src="https://github.com/user-attachments/assets/e8edb610-43d5-45e6-8c17-789ecd5c75fb" />

Por fim, ajustei os parâmetros de **Temperatura** e **Top‑P**, fundamentais para controlar o estilo das respostas do agente.  

<img width="433" height="241" alt="Temperatura e Top P" src="https://github.com/user-attachments/assets/683abcab-2533-4920-ab8b-3276a74ffd5c" />  

- **Temperatura (0.7):** define o nível de criatividade e aleatoriedade. Um valor muito baixo deixaria o texto previsível e repetitivo; muito alto poderia gerar respostas incoerentes. O valor 0.7 foi escolhido como ponto de equilíbrio, permitindo reflexões criativas sem perder clareza.  
- **Top‑P (0.9):** controla a diversidade do vocabulário, limitando a probabilidade acumulada das palavras escolhidas. Com 0.9, o agente consegue variar a linguagem e trazer metáforas interessantes, sem se dispersar demais.  

Essa combinação (Temperatura 0.7 e Top‑P 0.9) garante que o *Diário de Inspirações* produza textos curtos, poéticos e consistentes, capazes de surpreender o usuário com novas perspectivas, mas sempre mantendo coerência e profundidade.

---

## 🖼️ Prints de execução:
Após as etapas de desenvolvimento, o agente foi testado no *Playground*:  

<img width="1050" height="312" alt="Interação 1" src="https://github.com/user-attachments/assets/e073777a-6505-4e83-b039-6c5047ba5eba" />  
<img width="1058" height="305" alt="Interação 2" src="https://github.com/user-attachments/assets/a1f33347-1fdf-4457-bcf5-7ce4ce4606dd" />  
<img width="1055" height="313" alt="Interação 3" src="https://github.com/user-attachments/assets/3778a388-e11d-4b8f-a730-74ded53bcde2" />  
<img width="1037" height="317" alt="Interação 4" src="https://github.com/user-attachments/assets/9ff84bde-d538-4733-bd5e-2943382d9309" />  
<img width="1051" height="236" alt="Interação 5" src="https://github.com/user-attachments/assets/3b01b03d-b3ba-4785-a725-57a089eeac1c" />  

Com base nas interações realizadas, o Diário de Inspirações gerado pelo agente foi automaticamente encaminhado para o endereço de e‑mail definido nas instruções. Abaixo está o registro do e‑mail recebido:  

<img width="1546" height="436" alt="E-mail recebido" src="https://github.com/user-attachments/assets/dd738de8-0575-47d2-8333-d397f3cd2b59" />

---
##  🚀 Conclusão e próximos passos

Criei o *Diário de Inspirações* tentando aliar o uso da Inteligência Artificial à criatividade e ao autoconhecimento.  
Seu impacto vai além da automação: ele incentiva o hábito de reflexão diária, ajuda a reconhecer momentos significativos do cotidiano e constrói um acervo pessoal de memórias e aprendizados.

### 📌 Possibilidades futuras
Este projeto pode ser expandido com novas funcionalidades, como:
- Integração com calendários para organizar as inspirações por data;
- Exportação automática em formato PDF ou Markdown para criar um livro de reflexões;
- Análise de sentimentos ao longo do tempo, revelando padrões emocionais;
- Integração com aplicativos de notas ou redes sociais para compartilhar inspirações.

---

## 🔗 Referências
- [Microsoft Foundry](https://ai.azure.com)  
- [Azure Logic Apps](https://learn.microsoft.com/azure/logic-apps/)

---

## 📧 Contato:
  * [LinkedIn](https://www.linkedin.com/in/nagelamartins/)
  * [GitHub](https://github.com/nagelamartins)
  * [E-mail](mailto:nagela.msouza@gmail.com)

*Obrigada pela visita! 💛*












