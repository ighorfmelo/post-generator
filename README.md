# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)

## Flow criado no Zenvia

{
  "alias": "Perif",
  "description": "",
  "steps": [
    {
      "id": "step07",
      "type": "whatsappEvent",
      "properties": {
        "timeUnit": "minute",
        "expirationInMinutes": ""
      },
      "variables": {
        "answer": "payload"
      }
    },
    {
      "id": "step0",
      "type": "sendWhatsAppActivity",
      "label": "Boas vindas",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Seja bem vindo ao Perif"
          }
        },
        {
          "type": "text/plain",
          "payload": {
            "text": "Gostaríamos de ajuda-lo a deslanchar seu pequeno negocio e vamos te ajudar com a sua identidade visual."
          }
        }
      ]
    },
    {
      "id": "step012",
      "type": "sendWhatsAppActivity",
      "label": "Sem produto",
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Entendi. Para usufruir do _*Perif*_ é necessário ter uma foto do seu produto, mas podemos ajudar você a encontrar o melhor caminho para empreender e então voltar a entrar em contato conosco."
          }
        }
      ]
    },
    {
      "id": "idEventoInicial",
      "type": "whatsappEvent",
      "label": "Evento inicial",
      "properties": {
        "startEvent": "true",
        "appId": "whatsapp_chatbot",
        "appType": "chatbot",
        "timeUnit": "minute",
        "sessionExpirationInMinutes": "1"
      },
      "variables": {
        "whatsappFrom": "'fortunate-heart'"
      },
      "conditions": [
        {
          "type": "channelSourceCondition",
          "values": [
            "fortunate-heart"
          ]
        }
      ]
    },
    {
      "id": "step06",
      "type": "sendWhatsAppActivity",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "application/vnd.zenvia.v1.interactive.button+json",
          "payload": {
            "json": {
              "buttons": [
                {
                  "id": "SIM",
                  "title": "Sim"
                },
                {
                  "id": "NÃO",
                  "title": "Não"
                }
              ],
              "footer": "",
              "body": "Para começar, precisamos entender seu atual cenário. Sobre seu empreendimento, você já tem um negocio em andamento?"
            }
          }
        }
      ]
    },
    {
      "id": "step03",
      "type": "branch",
      "label": "Já possui negocio?"
    },
    {
      "id": "step04",
      "type": "sendWhatsAppActivity",
      "label": "Instrução",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Que legal, então podemos seguir para a criação da sua identidade visual. Vou te ajudar com algumas instruções:"
          }
        },
        {
          "type": "text/plain",
          "payload": {
            "text": "Precisamos que você tenha uma foto nítida do seu produto principal, para isso:\n1º: Posicione sua imagem em um fundo neutro (evite lugares com mais informações além do seu produto)\n2º: Capriche na iluminação para que a arte fique o mais profissional possível\n"
          }
        }
      ]
    },
    {
      "id": "step010",
      "type": "sendWhatsAppActivity",
      "label": "Só ideia",
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Certo. Como nosso serviço é voltado para a criação da identidade visual através de imagens do produto, não vamos conseguir trabalhar juntos nesse primeiro momento. "
          }
        },
        {
          "type": "text/plain",
          "payload": {
            "text": "O que podemos fazer nesse momento é te direcionar para alguns conteúdos que vão te ajudar a entender melhor esse momento de iniciar seu negócio."
          }
        }
      ]
    },
    {
      "id": "step08",
      "type": "branch",
      "label": "Possui produto?"
    },
    {
      "id": "idEventoFinal",
      "type": "endEvent",
      "label": "label 3",
      "properties": {
        "endEvent": "true"
      }
    },
    {
      "id": "step09",
      "type": "whatsappEvent",
      "variables": {
        "answer": "payload"
      }
    },
    {
      "id": "step05",
      "type": "sendWhatsAppActivity",
      "label": "Tem produto?",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "application/vnd.zenvia.v1.interactive.button+json",
          "payload": {
            "json": {
              "buttons": [
                {
                  "id": "ideia",
                  "title": "Tenho apenas a ideia"
                },
                {
                  "id": "Sim",
                  "title": "Já tenho o produto"
                },
                {
                  "id": "não",
                  "title": "Ainda não decidi"
                }
              ],
              "footer": "",
              "body": "Certo, preciso entender o quanto você já planejou seu negocio.\nJá possui o produto que deseja vender?"
            }
          }
        }
      ]
    },
    {
      "id": "step013",
      "type": "branch",
      "label": "Quer ajuda?"
    },
    {
      "id": "step014",
      "type": "sendWhatsAppActivity",
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "O SEBRAE (Serviço Brasileiro de Apoio às Micro e Pequenas Empresas) é um dos mais importantes portais de auxilio aos que desejam iniciar ou aprimorar seu negócio.\n\nEles oferecem um curso básico para quem quer ou acabou de começar seu empreendimento."
          }
        },
        {
          "type": "text/plain",
          "payload": {
            "text": "https://sebrae.com.br/sites/PortalSebrae/cursosonline/aprender-a-empreender,b070b8a6a28bb610VgnVCM1000004c00210aRCRD"
          }
        }
      ]
    },
    {
      "id": "step015",
      "type": "sendWhatsAppActivity",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "application/vnd.zenvia.v1.interactive.button+json",
          "payload": {
            "json": {
              "footer": "",
              "body": "Aceita indicação de conteúdo para iniciar seu negócio?",
              "buttons": [
                {
                  "id": "sim",
                  "title": "Sim"
                },
                {
                  "id": "não",
                  "title": "Encerrar sessão"
                }
              ]
            }
          }
        }
      ]
    },
    {
      "id": "step016",
      "type": "whatsappEvent",
      "variables": {
        "answer": "payload"
      }
    },
    {
      "id": "step011",
      "type": "sendWhatsAppActivity",
      "label": "Agradecimento",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Obrigada por entrar em contato conosco, espero que tenha tido uma boa experiencia com o _*Perif*_. Ficaremos felizes em ajudar sempre que necessário."
          }
        },
        {
          "type": "application/vnd.zenvia.v1.interactive.button+json",
          "payload": {
            "json": {
              "footer": "",
              "body": "Poderia responder uma pesquisa de satisfação? São apenas duas perguntinhas.",
              "buttons": [
                {
                  "id": "sim",
                  "title": "Sim"
                },
                {
                  "id": "não",
                  "title": "Não"
                }
              ],
              "header": {
                "type": "text",
                "text": "Antes de ir embora..."
              }
            }
          }
        }
      ]
    },
    {
      "id": "step017",
      "type": "whatsappEvent",
      "variables": {
        "answer": "payload"
      }
    },
    {
      "id": "step02",
      "type": "branch",
      "label": "pesquisa de satisfação"
    },
    {
      "id": "step018",
      "type": "sendWhatsAppActivity",
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "De 0 a 10, qual seu nível de satisfação com o nosso atendimento?"
          }
        }
      ]
    },
    {
      "id": "step019",
      "type": "sendWhatsAppActivity",
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "_*Perif*_ agradece seu contato."
          }
        }
      ]
    },
    {
      "id": "step020",
      "type": "whatsappEvent",
      "properties": {
        "timeUnit": "minute",
        "expirationInMinutes": ""
      },
      "variables": {
        "anwser": "payload"
      }
    },
    {
      "id": "step021",
      "type": "sendWhatsAppActivity",
      "label": "Melhorias",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Tem algum conteúdo que gostaria de ver por aqui? Se sim, qual?"
          }
        }
      ]
    },
    {
      "id": "step022",
      "type": "whatsappEvent",
      "variables": {
        "answer": "payload"
      }
    },
    {
      "id": "step023",
      "type": "sendWhatsAppActivity",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Outro conteúdo importante para quem está iniciando, também do SEBRAE, é sobre como precificar seus produtos"
          }
        },
        {
          "type": "text/plain",
          "payload": {
            "text": "https://www.sebrae.com.br/sites/PortalSebrae/artigos/calculadora-do-sebrae-aprenda-a-precificar-e-venda-no-marketplace,5f87f30b5eda0810VgnVCM100000d701210aRCRD"
          }
        }
      ]
    },
    {
      "id": "step025",
      "type": "sendWhatsAppActivity",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "application/vnd.zenvia.v1.interactive.button+json",
          "payload": {
            "json": {
              "footer": "",
              "body": "Curtiu?",
              "buttons": [
                {
                  "id": "sim",
                  "title": "Sim"
                },
                {
                  "id": "não",
                  "title": "Não"
                }
              ]
            }
          }
        }
      ]
    },
    {
      "id": "step026",
      "type": "whatsappEvent",
      "variables": {
        "answer": "payload"
      }
    },
    {
      "id": "step024",
      "type": "sendWhatsAppActivity",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Para criar a identidade visual do seu produto, você precisará seguir os passos a seguir:\n\n1º - Acesse o link: *https://post-generator-alpha.vercel.app/*\n2º - Informar o nome e preço do seu produto\n3º - Anexar a imagem do produto\n\nE pronto, já pode compartilhar com a galera."
          }
        }
      ]
    },
    {
      "id": "step027",
      "type": "sendWhatsAppActivity",
      "properties": {
        "from": "#{session['whatsappFrom']}"
      },
      "contents": [
        {
          "type": "text/plain",
          "payload": {
            "text": "Além disso, disponibilizamos alguns conteúdos para auxiliar no sucesso do seu negócio."
          }
        }
      ]
    }
  ],
  "connections": [
    {
      "from": "step0",
      "to": "step06"
    },
    {
      "from": "step03",
      "to": "step04",
      "label": "SIM",
      "conditions": [
        {
          "type": "keywordCondition",
          "values": [
            "Sim"
          ]
        }
      ]
    },
    {
      "from": "step06",
      "to": "step09"
    },
    {
      "from": "step07",
      "to": "step08"
    },
    {
      "from": "step05",
      "to": "step07"
    },
    {
      "from": "step09",
      "to": "step03"
    },
    {
      "from": "step03",
      "to": "step05",
      "label": "NÃO",
      "conditions": [
        {
          "type": "keywordCondition",
          "values": [
            "Não",
            "nao"
          ]
        }
      ]
    },
    {
      "from": "idEventoInicial",
      "to": "step0"
    },
    {
      "from": "step08",
      "to": "step012",
      "label": "Não",
      "conditions": [
        {
          "type": "keywordCondition",
          "values": [
            "Não",
            "nao"
          ]
        }
      ]
    },
    {
      "from": "step08",
      "to": "step010",
      "label": "ideia",
      "conditions": [
        {
          "type": "keywordCondition",
          "values": [
            "ideia"
          ]
        }
      ]
    },
    {
      "from": "step08",
      "to": "step04",
      "label": "Sim",
      "isDefault": true
    },
    {
      "from": "step012",
      "to": "step015"
    },
    {
      "from": "step015",
      "to": "step016"
    },
    {
      "from": "step010",
      "to": "step015"
    },
    {
      "from": "step016",
      "to": "step013"
    },
    {
      "from": "step011",
      "to": "step017"
    },
    {
      "from": "step013",
      "to": "step014",
      "label": "sim",
      "conditions": [
        {
          "type": "keywordCondition",
          "values": [
            "sim"
          ]
        }
      ]
    },
    {
      "from": "step013",
      "to": "step011",
      "label": "não",
      "isDefault": true
    },
    {
      "from": "step017",
      "to": "step02"
    },
    {
      "from": "step02",
      "to": "step018",
      "label": "sim",
      "conditions": [
        {
          "type": "keywordCondition",
          "values": [
            "sim"
          ]
        }
      ]
    },
    {
      "from": "step02",
      "to": "step019",
      "label": "não",
      "conditions": [
        {
          "type": "keywordCondition",
          "values": [
            "não",
            "nao"
          ]
        }
      ]
    },
    {
      "from": "step019",
      "to": "idEventoFinal"
    },
    {
      "from": "step018",
      "to": "step020"
    },
    {
      "from": "step020",
      "to": "step021"
    },
    {
      "from": "step021",
      "to": "step022"
    },
    {
      "from": "step022",
      "to": "step019"
    },
    {
      "from": "step014",
      "to": "step023"
    },
    {
      "from": "step023",
      "to": "step025"
    },
    {
      "from": "step025",
      "to": "step026"
    },
    {
      "from": "step026",
      "to": "step011"
    },
    {
      "from": "step04",
      "to": "step024"
    },
    {
      "from": "step024",
      "to": "step027"
    },
    {
      "from": "step027",
      "to": "step015"
    }
  ],
  "defaultConversationalChannel": "WHATSAPP"
}