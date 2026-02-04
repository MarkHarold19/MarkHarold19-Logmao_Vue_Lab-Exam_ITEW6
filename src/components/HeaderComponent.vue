<template>
    <header class="header">
      <h1 class="logo">{{ title }}</h1>
  
      <nav class="nav">
        <router-link to="/" class="link" active-class="active">
          Home
        </router-link>
        <router-link to="/students" class="link" active-class="active">
          Students
        </router-link>
      </nav>
    </header>
</template>
  

<script>
export default {
  name: 'HeaderComponent',
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>
.header {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: linear-gradient(135deg, #42b883, #35495e);
  color: white;
  padding: 1.2rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.15);
}

.logo {
  font-size: 1.6rem;
  font-weight: 700;
  letter-spacing: 0.5px;
}

.nav {
  display: flex;
  gap: 1.5rem;
}

.link {
  color: rgba(255, 255, 255, 0.85);
  text-decoration: none;
  font-weight: 600;
  position: relative;
  padding-bottom: 4px;
  transition: color 0.3s ease;
}

.link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  width: 0;
  height: 2px;
  background: white;
  transition: width 0.3s ease;
}

.link:hover::after {
  width: 100%;
}

.link:hover {
  color: white;
}

.active {
  color: white;
}

.active::after {
  width: 100%;
}

/* Responsive */
@media (max-width: 600px) {
  .header {
    flex-direction: column;
    gap: 0.8rem;
  }
}
</style>