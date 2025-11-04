# 🏋️‍♂️ Sistema de Reserva de Aulas — Ed's Gym

**Descrição:**  
O **Sistema de Reserva de Aulas da Ed's Gym** é uma aplicação web voltada para academias, estúdios de yoga, pilates ou crossfit.  
Permite que administradores cadastrem o cronograma de aulas e que os membros reservem suas vagas de forma simples, organizada e segura.

---

## 🚀 Funcionalidades Principais

### 👥 Perfis de Usuário
- **Administrador da Academia:** cadastra tipos e horários de aulas, define número de vagas e gerencia reservas.  
- **Membro (Aluno):** visualiza o cronograma, realiza reservas e gerencia suas inscrições.  
- **Administrador do Sistema:** responsável pela manutenção geral e suporte à plataforma.

### ⚙️ Lógica de Negócio

- **Tipos de Aula:** criados pelo administrador (ex: *Spinning, Yoga, Crossfit*).  
- **Aulas Agendadas:** instâncias de cada tipo de aula, com data, horário e número de vagas (ex: *Spinning - Terça 18h - 20 vagas*).  
- **Reservas:** relacionamento *Many-to-Many* entre `Membro` e `AulaAgendada`, com controle transacional de vagas e fila de espera.

---

## 📋 Requisitos Funcionais (RFs)

| Código | Descrição |
|:------:|:-----------|
| **RF-01** | O Admin da Academia deve cadastrar **AulasAgendadas** (ex: *Spinning Terça 18h - 20 Vagas*). |
| **RF-02** | O Membro deve poder **Reservar** um lugar, respeitando o limite de vagas. |
| **RF-03** | Se a aula estiver lotada, o Membro pode entrar em uma **Fila de Espera**. |
| **RF-04** | O Membro pode **Cancelar** sua reserva. |
| **RF-05** | Ao cancelar, o sistema **reserva automaticamente** a vaga para o próximo da fila. |

---

## 🧩 Requisitos Não Funcionais (RNFs)

| Código | Descrição |
|:------:|:-----------|
| **RNF-01** | **Integridade/Concorrência:** uso de *Lock Otimista* no contador de vagas (controle transacional). |
| **RNF-02** | **Confiabilidade/Assincronismo:** a lógica da fila de espera deve ser **assíncrona**, disparando um job que reserva a vaga e envia e-mail de confirmação. |

---

## 🧠 Regras de Negócio (Resumo)

1. Ao criar uma reserva:
   - Verificar `vagas_disponiveis > 0`;
   - Se houver vagas → decrementar contador e confirmar reserva;
   - Se não houver → adicionar o membro à **FilaDeEspera**.
2. Ao cancelar:
   - Liberar uma vaga;
   - Disparar job assíncrono que aloca o próximo da fila;
   - Enviar notificação (e-mail) ao novo inscrito.
3. Cada operação é transacional para garantir consistência e evitar concorrência incorreta.

---

## 🛠️ Tecnologias Sugeridas

| Camada | Tecnologias |
|:-------|:-------------|
| **Back-end** | Java / Spring Boot / Node.js / NestJS / Python (FastAPI) |
| **Banco de Dados** | PostgreSQL / MySQL / MongoDB |
| **Front-end** | React / Vue / Angular |
| **Mensageria / Jobs** | RabbitMQ / Kafka / Celery / Redis Queue |
| **Autenticação** | JWT / OAuth2 |
| **Infraestrutura** | Docker / Kubernetes / CI-CD (GitHub Actions) |

---

## 🧪 Testes e Qualidade

- Testes unitários e de integração;
- Simulação de múltiplos acessos concorrentes;
- Verificação de integridade de vagas e funcionamento da fila.

---

## 💡 Roadmap Futuro

- [ ] Integração com pagamentos (reserva paga);  
- [ ] Notificações via WhatsApp ou Push;  
- [ ] Painel analítico de frequência e ocupação;  
- [ ] Aplicativo mobile da Ed's Gym.  

---

## 🏢 Sobre a Ed's Gym

Desenvolvido pela **Ed's Gym Tech Team**, dedicada à inovação e eficiência no gerenciamento de academias e estúdios.

📧 **Contato:** suporte@edsgym.com  
🌐 **Website:** [https://www.edsgym.com](https://www.edsgym.com)

---

## 📜 Licença

Este projeto é distribuído sob a licença **MIT**.  
Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.

---
