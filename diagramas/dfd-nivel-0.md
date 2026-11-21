# DFD Nivel 0 - Chapa Games

## Descrição

O Diagrama de Fluxo de Dados (DFD) nível 0 apresenta os principais processos do sistema Chapa Games, demonstrando a comunicação entre os usuários, os processos e os depósitos de dados.

## Diagrama

```mermaid
flowchart TB
    C[Cliente]
    A[Administrador]

    P1((1.0 Consultar catálogo))
    P2((2.0 Gerenciar jogos))
    P3((3.0 Gerenciar carrinho))
    P4((4.0 Finalizar pedido))

    D1[(D1 - Jogos)]
    D2[(D2 - Pedidos)]
    D3[(D3 - Itens dos pedidos)]

    C -->|Solicita catálogo| P1
    P1 -->|Consulta jogos| D1
    D1 -->|Dados dos jogos| P1
    P1 -->|Catálogo disponível| C

    A -->|Cadastro e alterações| P2
    P2 -->|Consulta e atualização| D1
    D1 -->|Dados dos jogos| P2
    P2 -->|Resultado do gerenciamento| A

    C -->|Seleciona jogos e quantidades| P3
    P3 -->|Consulta preços| D1
    D1 -->|Dados dos produtos| P3
    P3 -->|Carrinho e total| C

    C -->|Confirma compra| P4
    P4 -->|Consulta produtos| D1
    D1 -->|Dados dos jogos| P4
    P4 -->|Registra pedido| D2
    P4 -->|Registra itens| D3
    P4 -->|Confirmação ou erro| C
```

## Dicionário de Dados

O dicionário de dados apresenta os principais elementos utilizados pelo sistema.

| Item | Campos principais | Tipo |
|---|---|---|
| Jogo | id, nome, preço, disponibilidade | Inteiro, texto, decimal e booleano |
| Catálogo | Lista de jogos disponíveis | Coleção de jogos |
| Carrinho | id, lista de itens, valor total | Inteiro, coleção e decimal |
| ItemCarrinho | id_jogo, quantidade, preço | Inteiro e decimal |
| Pedido | id_pedido, data, valor_total, status | Inteiro, data, decimal e texto |
| ItemPedido | id_jogo, quantidade, preço_unitário | Inteiro e decimal |
| DadosPedido | Itens, quantidades e informações da compra | Objeto JSON |
| RespostaPedido | sucesso, mensagem e dados do pedido | Booleano, texto e objeto JSON |

## Considerações

O DFD e o dicionário de dados ajudam a documentar o funcionamento do Chapa Games, facilitando a compreensão dos processos e a organização das informações utilizadas pelo sistema.

Os campos e processos devem ser conferidos com a implementação efetiva do projeto.
