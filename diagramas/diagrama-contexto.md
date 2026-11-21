# Diagrama de Contexto - Chapa Games

O sistema Chapa Games possui dois usuários externos:
Cliente e Administrador.

```mermaid
flowchart LR
    C[Cliente] -->|Consulta jogos e envia pedido| S((Chapa Games))
    S -->|Catálogo, total e confirmação| C
    A[Administrador] -->|Dados e solicitações de gerenciamento| S
    S -->|Informações dos jogos e pedidos| A
'''
