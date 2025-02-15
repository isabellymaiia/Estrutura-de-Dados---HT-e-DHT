# Distributed Hash Table (DHT) em C++

## Sobre o Projeto
Este projeto implementa uma **Distributed Hash Table (DHT)** utilizando C++. A DHT é uma estrutura distribuída que permite armazenar e buscar informações de forma descentralizada e eficiente. Neste projeto, a DHT armazena registros de alunos, associando cada aluno a um **RA (Registro Acadêmico)** e distribuindo os dados entre diferentes nós de uma rede simulada.

Cada nó possui um identificador e armazena os alunos de acordo com seu RA. Quando um aluno é inserido, o sistema encontra o nó responsável por armazenar esse registro. O mesmo acontece para operações de busca e remoção.



## 🛠 Principais Funcionalidades
- **Inserção de alunos na DHT**  
  - Os alunos são distribuídos entre diferentes nós com base no RA.
  - O sistema encontra automaticamente o nó correto para armazenar um novo aluno.

- **Busca de alunos pelo RA**  
  - O usuário pode digitar um RA e verificar se o aluno está armazenado.
  - Se o aluno existir, o sistema retorna o nome e o nó onde ele está armazenado.
  - Se o aluno não existir, o sistema informa que ele não foi encontrado.

- **Remoção de alunos pelo RA**  
  - O usuário pode remover um aluno informando seu RA.
  - O sistema encontra o nó onde o aluno está armazenado e o remove.
  - Se o aluno não existir, o sistema informa que ele não foi encontrado.

- **Exibição do estado atual da DHT**  
  - O sistema imprime todos os nós e quais alunos estão armazenados em cada um.


## Casos de Teste

### **1️. Inserção e listagem de alunos**
**Objetivo:** Garantir que um aluno inserido apareça na lista de alunos armazenados.  

**Passos:**  
1. Inserir um aluno digitando o **nome** e o **RA**.
2. O sistema deve armazenar o aluno no nó correto.
3. Exibir a lista de alunos cadastrados após a inserção.

**Entrada:**  

```
Digite o nome do aluno: Isa Digite o RA do aluno: 550
```
**Saída esperada:**  
```
Aluno Isa (RA: 550) inserido no nó 2000

Lista de alunos cadastrados: 
No 500 armazenando: [450 -> Pedro] [400 -> Joao] 
No 4000 armazenando: [3500 -> Maria] 
No 7000 armazenando: [6200 -> Lucas] 
No 2000 armazenando: [550 -> Isa]
```

### **2️. Busca de um aluno existente**
**Objetivo:** Garantir que um aluno existente pode ser encontrado pelo RA.  

**Passos:**  
1. Buscar um aluno digitando um **RA já armazenado**.
2. O sistema deve exibir o nome do aluno e o nó onde ele está armazenado.

**Entrada:**  
```
Digite o RA do aluno que deseja buscar: 3500
```
**Saída esperada:**  
```
Aluno encontrado: Maria no nó 4000
```
### **3️. Busca de um aluno inexistente**
**Objetivo:** Garantir que o sistema informe corretamente quando um RA não está armazenado.  

**Passos:**  
1. Buscar um aluno digitando um **RA que não foi cadastrado**.
2. O sistema deve informar que o aluno não foi encontrado.

**Entrada:**
```
Digite o RA do aluno que deseja buscar: 9999
```

**Saída esperada:**  
```
Aluno não encontrado!
```
### **4️. Remoção de um aluno e listagem atualizada**
**Objetivo:** Garantir que um aluno seja removido corretamente e a lista atualizada.  

**Passos:**  
1. Remover um aluno digitando um **RA existente**.
2. O sistema deve confirmar a remoção.
3. Exibir a lista de alunos cadastrados após a remoção.

**Entrada:**  
```
Digite o RA do aluno que deseja remover: 3500
```

**Saída esperada:**  
```
Lista de alunos cadastrados após a remoção: 
No 500 armazenando: [450 -> Pedro] [400 -> Joao] 
No 7000 armazenando: [6200 -> Lucas] 
No 2000 armazenando: [550 -> Isa]
```

### **5️. Inserção de um aluno com RA já existente**
**Objetivo:** Testar se o sistema substitui um aluno ou mantém o primeiro ao tentar inserir um **RA duplicado**.  

**Passos:**  
1. Inserir um aluno com **RA 3500 (Maria)**.
2. Inserir outro aluno com **RA 3500 (João)**.
3. Buscar pelo RA 3500 e verificar qual aluno está armazenado.

**Entrada:**  
```
Digite o nome do aluno: Maria Digite o RA do aluno: 3500
Digite o nome do aluno: João Digite o RA do aluno: 3500
```
**Saída esperada:**  
```
Aluno Maria (RA: 3500) inserido no nó 4000 
Aluno João (RA: 3500) inserido no nó 4000 
Aviso: RA 3500 já existe.
```