// src/components/Header.vue
<template>
  <header class="header">
    <nav class="nav">
      <h1>Safqatic</h1>
      <ul>
        <li><a href="#">Accueil</a></li>
        <li><a href="#">Appels d'Offres</a></li>
        <li><a href="#">Connexion</a></li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
.header {
  background: #007bff;
  color: white;
  padding: 10px;
  text-align: center;
}
.nav ul {
  list-style: none;
  padding: 0;
  display: flex;
  justify-content: center;
  gap: 20px;
}
.nav a {
  color: white;
  text-decoration: none;
}
</style>

// src/components/OfferList.vue
<template>
  <section class="offers">
    <h2>Appels d'Offres Récents</h2>
    <ul>
      <li v-for="offer in offers" :key="offer.id">
        <h3>{{ offer.title }}</h3>
        <p>{{ offer.description }}</p>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      offers: [
        { id: 1, title: "Marché Informatique", description: "Achat de matériel..." },
        { id: 2, title: "Projet BTP", description: "Construction d’un bâtiment..." }
      ]
    };
  }
};
</script>

<style scoped>
.offers {
  padding: 20px;
  text-align: center;
}
.offers ul {
  list-style: none;
  padding: 0;
}
.offers li {
  background: #f4f4f4;
  margin: 10px 0;
  padding: 15px;
  border-radius: 5px;
}
</style>

// src/components/Footer.vue
<template>
  <footer class="footer">
    <p>&copy; 2025 Safqatic. Tous droits réservés.</p>
  </footer>
</template>

<style scoped>
.footer {
  background: #333;
  color: white;
  text-align: center;
  padding: 10px;
  position: fixed;
  bottom: 0;
  width: 100%;
}
</style>

// src/App.vue
<template>
  <div>
    <Header />
    <OfferList />
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Header,
    Footer
  }
};
</script>
