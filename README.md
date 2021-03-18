# invoices-wirecard

API de cobranças Wirecard

  ---


## Index
- [Overview](#overview)
- [Autenticando](#autenticando)
- [Invoices](#invoices)
  - [Consultar invoice](#consultar-invoice)
  - [Listar todas as invoices](#listar-todas-as-invoices)
  - [Criar uma invoice](#criar-uma-invoice)
  
  
  ### Overview
  Esta API permite a criação de cobranças de forma simples e rápida, possibilitando o acesso ao link de pagamento e o envio da cobrança para o e-mail do customer.
  
  ### Autenticando
 
Authorization: Basic token:key

  ## Invoices
  ---
  ### Consultar Invoice
  
  ```PHP
  curl -X GET \
  https://api.moip.com.br/v2/invoices/INV-873BB9F8E21B \
  -H 'Authorization: Basic **********************************************************************************************==' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 28cbe671-9f6a-4475-adb1-ff255dc43ce2' \
  -H 'cache-control: no-cache' 
```

### Listar todas as invoices

```PHP
curl -X GET \
  https://api.moip.com.br/v2/invoices/ \
  -H 'Authorization: Basic **********************************************************************************************==' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: ee97282f-ed55-4f4b-879f-a7133d89a5cf' \
  -H 'cache-control: no-cache'
  ```
  
  ### Criar uma invoice
  
  ```PHP
  {
  "amount": {
    "currency": "BRL",
    "subtotals": {
      "shipping": 0
    }
  },
  "items": [
    {
      "product": "Descrição do pedido",
      "quantity": 1,
      "detail": "Mais info...",
      "price": 1000
    }
  ],
  "customer": {
    "email": "wirecard@moip.com.br"
  },
  "checkoutPreferences": {
    "fundingInstruments": {
      "suppressCreditCard": false,
      "suppressBoleto": false
    },
    "installments": []
  }
}
```

### Callback

```JSON
{
    "id": "INV-DB1B7C572036",
    "amount": {
        "total": 1000,
        "fees": 0,
        "refunds": 0,
        "liquid": 0,
        "otherReceivers": 0,
        "currency": "BRL",
        "subtotals": {
            "shipping": 0,
            "addition": 0,
            "discount": 0,
            "items": 1000
        }
    },
    "items": [
        {
            "product": "Descrição do pedido",
            "detail": "Mais info...",
            "price": 1000
        }
    ],
    "customer": {
        "email": "mario.dias@moip.com.br"
    },
    "receivers": [
        {
            "moipAccount": {
                "id": "MPA-SVOAZTTRR656",
                "fullname": "Mario Sergio Araujo Dias",
                "company": {
                    "name": null
                }
            }
        }
    ],
    "checkoutPreferences": {
        "fundingInstruments": {
            "suppressCreditCard": false,
            "suppressBoleto": false
        },
        "installments": []
    },
    "status": "SENT",
    "statusHistory": [
        {
            "status": "SENT",
            "createdAt": "2020-03-23T18:32:11-0300"
        }
    ],
    "createdAt": "2020-03-23T18:32:11-0300",
    "updatedAt": "2020-03-23T18:32:11-0300",
    "_links": {
        "self": {
            "href": "/invoice/INV-DB1B7C572036"
        },
        "checkout": {
            "pay": {
                "redirectHref": "https://checkout-new.moip.com.br?id=INV-DB1B7C572036&token=1a8f0774-f4bd-47f4-abc4-c696ab57ffda"
            }
        }
    }
}
```
  
  

