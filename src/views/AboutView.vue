<script setup>
import MainMenu from "@/components/MainMenu.vue";
</script>

<template>
  <body>
    <header><MainMenu /></header>
    <main class="about">
      <h1>Sobre o API News</h1>
      <p>
        Bem-vindo ao nosso Aplicativo de Notícias Vue/Vite, seu destino único
        para se manter atualizado com as últimas notícias de todo o mundo.
        Alimentado pela robusta API de Notícias, nosso aplicativo oferece uma
        experiência perfeita para navegar, descobrir e ler artigos de notícias
        sem esforço.
      </p>

      <h3>Recursos:</h3>
      <ol>
        <li>
          <strong>Listagem de Notícias:</strong> Explore uma ampla gama de
          artigos de notícias categorizados por temas como tecnologia, esportes,
          política, entretenimento e muito mais.
        </li>
        <li>
          <strong>Interface de Usuário Interativa:</strong> Nossa interface
          intuitiva garante uma navegação suave, permitindo que você encontre
          facilmente as notícias que mais lhe interessam.
        </li>
        <li>
          <strong>Abrir Artigos em Nova Aba:</strong> Abra facilmente qualquer
          artigo de interesse em uma nova aba do navegador para uma leitura mais
          aprofundada sem perder o controle de sua sessão de navegação.
        </li>
        <li>
          <strong>Funcionalidade de Busca:</strong> Utilize nosso poderoso
          recurso de busca para encontrar artigos de notícias ou tópicos
          específicos com facilidade, garantindo que você se mantenha informado
          sobre assuntos que despertam seu interesse.
        </li>
        <li>
          <strong>Design Responsivo:</strong> Esteja você acessando nosso
          aplicativo em seu desktop, tablet ou dispositivo móvel, nosso design
          responsivo garante uma experiência de navegação perfeita e agradável
          em todas as plataformas.
        </li>
      </ol>

      <h3>Como Funciona:</h3>
      <p>
        Nosso aplicativo Vue/Vite busca dados de notícias em tempo real da API
        de Notícias, fornecendo informações atualizadas de fontes confiáveis em
        todo o mundo. A integração do Vue.js e Vite garante um desempenho
        eficiente e um desenvolvimento rápido, permitindo que entreguemos uma
        experiência de usuário rápida e dinâmica.
      </p>
    </main>
  </body>
</template>

<style scoped>
.about {
  padding: 24px 20%;
  margin: 40px 0;
}

h1 {
  font-size: 2.5em;
}

h1,
h3,
strong {
  font-weight: bold;
}
</style>
