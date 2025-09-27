## UML Diagram

```mermaid
classDiagram
    User "1" --> "0..*" Order
    Order "1" --> "1..*" OrderItem
    OrderItem "0..*" --> "1" Product
    User "1" --> "0..1" Cart
    Cart "1" --> "0..*" Product

    class User {
      +id: int
      +name: string
      +email: string
      +password_hash: string
      +is_admin: bool
      +register()
      +login()
      +update_profile()
    }

    class Product {
      +id: int
      +name: string
      +description: string
      +price: float
      +stock_quantity: int
      +add_product()
      +update_product()
      +remove_product()
    }

    class Order {
      +id: int
      +user_id: int
      +total_value: float
      +status: string
      +created_at: datetime
      +create_order()
      +cancel_order()
      +get_order_details()
    }

    class OrderItem {
      +id: int
      +order_id: int
      +product_id: int
      +quantity: int
      +unit_price: float
      +add_item()
      +update_quantity()
      +remove_item()
    }

    class Cart {
      +id: int
      +user_id: int
      +add_to_cart(product, quantity)
      +remove_from_cart(product)
      +checkout()
    }
```



```mermaid
usecaseDiagram
actor "Usuário" as User
actor "Vendedor" as Seller
actor "Gerente" as Manager
actor "Dono" as Owner
actor "Administrador" as Admin
actor "Sistema" as System

User --> (Cadastrar cliente)
User --> (Consultar dados cadastrais)
User --> (Atualizar dados cadastrais)
User --> (Excluir cliente)

User --> (Cadastrar medicamento)
User --> (Consultar medicamentos)
User --> (Atualizar medicamento)
User --> (Excluir medicamento)
User --> (Cadastrar medicamento com tarja)
User --> (Registrar venda)
User --> (Aplicar descontos automáticos)
User --> (Receber alerta de baixo estoque)
User --> (Verificar validade de medicamentos)
User --> (Registrar formas de pagamento)
User --> (Emitir nota fiscal)
User --> (Gerar relatório de vendas)
User --> (Gerar relatório de estoque)
User --> (Registrar venda de controlados com receita)
User --> (Validar quantidade máxima de controlados)
User --> (Gerar relatório de medicamentos controlados)

Admin --> (Definir papéis e permissões)

Seller --> (Registrar vendas)

Manager --> (Gerenciar estoque)
Manager --> (Aprovar descontos especiais)

Owner --> (Acessar relatórios financeiros)
Owner --> (Alterar permissões)

System --> (Bloquear ações sem permissão)
```
