🧾 Lista de Tarefas — Versão 06

Projeto desenvolvido com Spring Boot (Backend) e Vue.js (Frontend)

👤 Autor: Hugo de Oliveira Nunes

🐛 Problema identificado

Durante os testes iniciais, o frontend não exibia os títulos das tarefas corretamente.

Motivo encontrado: o backend bloqueava as requisições do Vue.js por falta de configuração de CORS, impedindo o carregamento dos dados iniciais (seed).

🔧 Solução Implementada
🖥️ Backend (Spring Boot)

Foi adicionada uma configuração global de CORS para permitir a comunicação com o frontend em localhost:5173:

@Configuration
public class WebConfig {
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                        .allowedOrigins("http://localhost:5173")
                        .allowedMethods("GET", "POST", "PUT", "DELETE");
            }
        };
    }
}


✅ Com isso, o frontend passou a se conectar normalmente ao backend, sem erros de CORS.

💻 Frontend (Vue.js)

O componente responsável pela exibição das tarefas foi ajustado para mostrar corretamente os títulos:

<span v-if="tarefaEditandoId !== tarefa.id">
  {{ tarefa.titulo }}
</span>


✅ Agora os títulos são renderizados normalmente e a lista de tarefas está funcional.

🚀 Como Executar o Projeto
🔹 Back-end

Abra o projeto no seu IDE (por exemplo, IntelliJ ou Eclipse).

Execute a classe principal ApiApplication.java.

A API estará disponível em:
👉 http://localhost:8088/api

🔹 Front-end

Acesse a pasta do projeto Vue.js.

Instale as dependências:

npm install


Inicie o servidor:

npm run dev


Acesse no navegador:
👉 http://localhost:5173

📋 Funcionalidades Atuais

📝 Listar tarefas

➕ Adicionar novas tarefas

✏️ Editar título das tarefas

✅ Marcar como concluídas

❌ Remover tarefas

🔗 Comunicação frontend ↔ backend totalmente funcional

📦 Considerações Finais

✔️ Aplicação 100% funcional após correção do CORS
✔️ Dados carregando corretamente no frontend
✔️ Projeto finalizado e pronto para entrega individual
