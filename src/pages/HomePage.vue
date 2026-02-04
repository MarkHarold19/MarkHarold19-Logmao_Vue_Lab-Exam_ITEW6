<template>
  <div class="home">
    <section class="hero">
      <h1>Student Management System</h1>

      <router-link to="/students" class="btn">
        View Students
      </router-link>
    </section>

    <section class="features">
      <div class="feature-card">
        <h3>Courses</h3>
        <p>Students are enrolled in real academic programs.</p>
      </div>

      <div class="feature-card">
        <h3>Student Profiles</h3>
        <p>View detailed student information dynamically.</p>
      </div>

      <div class="feature-card">
        <h3>Fast & Modern</h3>
        <p>Built with Vue and client-side routing.</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'HomePage'
}
</script>

<style scoped>
.home {
  min-height: 79.3vh;
  background: linear-gradient(135deg, #42b883, #35495e);
  color: white;
  padding: 3rem 1rem;
}

.hero {
  text-align: center;
  margin-bottom: 4rem;
}

.hero h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.hero p {
  max-width: 500px;
  margin: auto;
  opacity: 0.9;
}

.btn {
  display: inline-block;
  margin-top: 2rem;
  background: white;
  color: #42b883;
  padding: 0.8rem 1.8rem;
  border-radius: 30px;
  text-decoration: none;
  font-weight: 700;
  transition: all 0.3s ease;
}

.btn:hover {
  transform: scale(1.05);
  background: #f1f1f1;
}

.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;
  max-width: 1000px;
  margin: auto;
}

.feature-card {
  background: rgba(255, 255, 255, 0.15);
  padding: 1.5rem;
  border-radius: 16px;
  text-align: center;
  backdrop-filter: blur(10px);
}
</style>