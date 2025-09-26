Presentaremos el siguiente desafío en formato [User Stories][1], a medida que avancemos en el curso, pasaremos a usar Jira como plataforma de gestión de proyectos.

# User stories (customer-focused)

### 1) Select a product by code

**As a** customer  
**I want** to enter a snack code  
**So that** the machine knows which item I’m buying

**Acceptance criteria**

- Given the machine is idle, when I enter a valid code for an in-stock snack, the machine displays the price and prompts for money.
    
- If the code doesn’t exist, I get “Invalid code” and stay idle.
    
- If the product is out of stock, I get “Out of stock” and stay idle.
    

---

### 2) Enforce CLP and accepted denominations

**As a** customer  
**I want** to insert only accepted CLP coins/bills  
**So that** the machine reliably counts my money

**Acceptance criteria**

- Accepted coins: 50, 100, 500.
    
- Accepted bills: 1000, 2000, 5000, 10000, 20000.
    
- Any other denomination is rejected and immediately returned; display “Unsupported denomination”.
    

---

### 3) Minimum purchase amount

**As a** customer  
**I want** the machine to enforce a minimum buy price (≥ 500 CLP)  
**So that** unreasonably cheap items aren’t sellable

**Acceptance criteria**

- If a product’s price < 500 CLP, it is not vendable; selecting it shows “Item below min price”.
    

---

### 4) Insert money after selecting

**As a** customer  
**I want** to insert money only after selecting a code  
**So that** the machine knows the target price and change needs

**Acceptance criteria**

- If I try to insert money without a selected code, the machine rejects the money with “Select an item first”.
    

---

### 5) Exact or insufficient funds

**As a** customer  
**I want** feedback as I insert money  
**So that** I know how much is still needed

**Acceptance criteria**

- The machine tracks and displays “Remaining: X CLP” until paid ≥ price.
    
- If I press cancel before reaching price, all inserted money is returned and state resets to idle.
    

---

### 6) Overpayment and change feasibility

**As a** customer  
**I want** the machine to check it can make change **before** vending  
**So that** I don’t lose money or get stuck

**Acceptance criteria**

- When inserted ≥ price and overpayment exists:
    
    - The machine computes if it **can** make the exact change from its current float (coins/bills).
        
    - If it **can**, it vends the snack, dispenses change, updates float/inventory, and resets to idle.
        
    - If it **cannot**, it **returns all inserted money** and shows “Cannot make change”; state resets to idle and the snack is **not** vended.
        

---

### 7) Exact payment (no change needed)

**As a** customer  
**I want** the snack to vend immediately when I pay the exact price

**Acceptance criteria**

- If inserted == price, vend snack, decrement stock, update float with inserted denominations, reset to idle.
    

---

### 8) Out-of-stock after selection

**As a** customer  
**I want** a safe failure if stock hits zero while I’m paying (race condition)

**Acceptance criteria**

- If stock becomes 0 before vend confirmation, the machine cancels the transaction and returns all inserted money.
    

---

### 9) Cancel at any time before vend

**As a** customer  
**I want** to cancel the transaction before vending  
**So that** I can get my money back

**Acceptance criteria**

- On cancel, the machine returns all inserted money (as inserted, not “best effort” change), clears the selected code, and resets.

[1]: https://es.wikipedia.org/wiki/Historias_de_usuario