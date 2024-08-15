# Rodrigo_Nasciemento_ProjetoX
Aulas de engenharia de software 

# 1. Descrição do sistema

Sistema para clinica veterinaria Terra dos Pets


Autor: Rodrigo do Nascimento


1. Uma clínica veterinária atende apenas os animais: gatos e cachorros. 


2. Os clientes devem fazer um cadastro de si e dos animais. 


3. Os clientes devem informar as condições nas quais os animais chegam. 


4. Os clientes devem informar o tipo de ração que o animal come. 


5. O cliente deve informar hábitos do animal. 


6. Para cada animal é possível que mais de um veterinário o atenda. 


7. Os animais podem chegar e serem atendidos de acordo com uma agenda do dia. 


8. Cada animal atendido receberá uma ficha e um prontuário. 


9. Outros donos podem querer marcar horários de atendimento futuro. 


10. O atendimento gera uma receita para o animal. 


11. Quando um cliente chega na clínica veterinária ele é atendido por um atendente. 


12. O atendente deve verificar se existe agenda disponível com um veterinário. 


13. O atendente deve colocar o cliente e seu animal na fila de espera, se for o caso. 


14. O atendente deve levar o cliente e o animal até o veterinário. 


15. O veterinário deve realizar uma entrevista com o dono do animal. 


16. O resultado da entrevista deve ir para um formulário. 


17. O veterinário deverá examinar o animal e anotar em prontuário(ficha) suas observações. 


18. Dependendo da situação do animal este receberá uma receita.


19. Exibir a disponibilidade de horários em tempo real.


20. Organizar os clientes em uma fila de espera baseada na ordem de chegada ou na urgência do caso.


21. Armazenar todas as consultas realizadas, incluindo observações do veterinário, diagnósticos e tratamentos.


22. Gerar uma fila de espera caso não haja horários disponíveis.


23. Horário de atendimento das 7:00 as 18:00.


24. Emergências podem ser atendido após as 18:00.


Terra dos pets


---
# 2. Diagrama do banco de dados 

Tabela Clientes:


```mermaid
erDiagram
    CLIENTES {
        int id_cliente PK
        string nome
        string telefone
        string email
        string endereco
    }
    
    ANIMAIS {
        int id_animal PK
        int id_cliente FK
        string nome
        enum especie
        string raca
        int idade
        text condicao
        string tipo_racao
        text habitos
    }
    
    VETERINARIOS {
        int id_veterinario PK
        string nome
        string especialidade
    }
    
    ATENDENTES {
        int id_atendente PK
        string nome
    }
    
    CONSULTAS {
        int id_consulta PK
        int id_animal FK
        int id_veterinario FK
        datetime data_consulta
        time hora_inicio
        time hora_fim
        text motivo
        text diagnostico
        text tratamento
        text receita
    }
    
    PRONTUARIOS {
        int id_prontuario PK
        int id_animal FK
        int id_consulta FK
        text observacoes
    }
    
    AGENDAMENTOS {
        int id_agendamento PK
        int id_animal FK
        int id_veterinario FK
        datetime data_agendamento
        time hora
        enum status
    }
    
    FILA_ESPERA {
        int id_fila PK
        int id_animal FK
        int id_veterinario FK
        datetime data_entrada
        time hora_entrada
        enum prioridade
        enum status
    }
    
    CLIENTES ||--o{ ANIMAIS : possui
    ANIMAIS ||--o{ CONSULTAS : possui
    ANIMAIS ||--o{ PRONTUARIOS : possui
    ANIMAIS ||--o{ AGENDAMENTOS : agenda
    ANIMAIS ||--o{ FILA_ESPERA : entra_em
    VETERINARIOS ||--o{ CONSULTAS : realiza
    VETERINARIOS ||--o{ AGENDAMENTOS : participa
    VETERINARIOS ||--o{ FILA_ESPERA : participa
    CONSULTAS ||--o{ PRONTUARIOS : gera

```

![Diagrama do banco de dados ](https://github.com/rodrigoo034/Rodrigo_Nasciemento_projetoX/blob/main/imagens/der.png)

---
# 3. Diagrama de casos de uso

![Diagrama de casos de uso](https://github.com/rodrigoo034/Rodrigo_Nasciemento_projetoX/blob/main/imagens/casos%20de%20uso.png)

![Diagrama de casos de uso](https://github.com/rodrigoo034/Rodrigo_Nasciemento_projetoX/blob/main/imagens/pets1.png)

---
# 4. Principais telas do sistema

Colocar aqui a figura das telas do sistema

![]()

---
# 5. Arquitetura do sitema

Diagrama do sistema

![diagrama do sistema](https://github.com/rodrigoo034/Rodrigo_Nasciemento_projetoX/blob/main/imagens/Arquitetura%20do%20sitema.jpeg)