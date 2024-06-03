Projeto EduDown:Educação Inclusiva para Todos - Chatbot com IA Gemini

📒 Descrição

O Projeto EduDown visa promover a inclusão social de pessoas com Síndrome de Down por meio da educação. O projeto desenvolve um chatbot com inteligência artificial (IA) utilizando a tecnologia Gemini da Google, para auxiliar educadores a entenderem a síndrome de Down e oferecerem suporte eficaz aos alunos com essa condição.

🤖 Tecnologias Utilizadas

IA Generativa: Google Gemini

Linguagem de Programação: Python

Processamento de Linguagem Natural (PLN): Para garantir a precisão e fluidez das interações com o chatbot

🧐 Processo de Criação

Pesquisa e Coleta de Dados: Reunião de informações abrangentes sobre a Síndrome de Down, incluindo aspectos médicos, pedagógicos, sociais e legais.

Desenvolvimento do Chatbot: Criação da estrutura do chatbot em Python e integração com a IA Gemini da Google.

Treinamento da IA: Alimentação da IA com a base de dados coletada, utilizando técnicas de PLN.

Testes e Aperfeiçoamento: Realização de testes com usuários reais para avaliar a usabilidade e eficácia do chatbot.

Divulgação e Implementação: Promoção do chatbot EduDown junto a instituições de ensino e entidades educacionais.

🚀 Resultados

Disseminação de informação: Oferecer informações precisas sobre a síndrome de Down para educadores.

Combate ao preconceito: Desmistificar a síndrome de Down e promover a compreensão e a empatia.

Capacitação de educadores: Fornecer ferramentas e estratégias eficazes para o ensino inclusivo.

Facilitação da inclusão: Auxiliar na construção de um ambiente escolar mais inclusivo.

💭 Reflexão

Criar algo com IA para este projeto foi um desafio emocionante! A complexidade da IA Gemini e o objetivo de garantir um conteúdo preciso e sensível para um tema como a Síndrome de Down exigiu pesquisa profunda e constante aprimoramento. O processo de treinamento da IA para responder a perguntas complexas de forma natural e útil foi um aprendizado constante. No entanto, a recompensa de oferecer uma ferramenta que pode ajudar educadores a entender e apoiar alunos com Síndrome de Down torna todo o esforço muito gratificante.

# Full Pilot Code:

import os
from langchain.llms import Gemini
from langchain.chains import ConversationChain
from langchain.memory import ConversationBufferMemory
from langchain.prompts import PromptTemplate

# Define o modelo de IA Gemini a ser usado
os.environ["GOOGLE_APPLICATION_CREDENTIALS"] = "path/to/your/credentials.json" # Substitua pelo caminho para seu arquivo de credenciais
llm = Gemini(model_name="gemini-pro")

# Define a estrutura do prompt para o chatbot
template = """Você é um chatbot que oferece informações precisas sobre a Síndrome de Down, auxiliando professores a entenderem melhor a condição e oferecerem suporte a alunos com a síndrome. 
Responda de forma clara e completa, com exemplos e linguagem acessível.
{history}
{question}"""

prompt = PromptTemplate(
    input_variables=["history", "question"],
    template=template,
)

# Define a memória do chatbot para manter o histórico de conversas
memory = ConversationBufferMemory()

# Cria a cadeia de conversa com a IA Gemini
conversation = ConversationChain(
    llm=llm,
    memory=memory,
    prompt=prompt,
)

# Loop principal do chatbot
while True:
    # Pede a entrada do usuário
    user_input = input("Usuário: ")

    # Se o usuário digitar "sair", encerra o chatbot
    if user_input.lower() == "sair":
        break

    # Processa a entrada do usuário com a cadeia de conversa
    response = conversation.run(user_input)

    # Imprime a resposta do chatbot
    print("Chatbot: " + response)
