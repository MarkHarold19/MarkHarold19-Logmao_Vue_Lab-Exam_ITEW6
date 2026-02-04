<template>
    <div class="student">
    <h2>{{ name }}</h2>
    <p class="badge">{{ course }}</p>
    <p class="student-number">Student No: {{ studentNumber }}</p>
    <p>Year: {{ year }}</p>
  
  
    <button @click="toggleDetails">
      {{ showDetails ? 'Hide Details' : 'Show Details' }}
    </button>
  
    <div v-if="showDetails">
      <p>Email: {{ email }}</p>
      <p>Phone: {{ phone }}</p>
    </div>
  </div>
  
  </template>
  
  <script>
  export default {
    name: 'StudentComponent',
    props: {
      studentNumber: {
        type: String,
        required: true
      },
      name: {
        type: String,
        required: true
      },
      course: {
        type: String,
        required: true
      },
      year: {
        type: Number,
        required: true
      },
      email: {
        type: String,
        required: true
      },
      phone: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        showDetails: false
      }
    },
    methods: {
      toggleDetails() {
        this.showDetails = !this.showDetails
      }
    }
  }
  </script>
  
  <style scoped>
  .student {
    border: 1px solid #ddd;
    padding: 1rem;
    margin: 1rem 0;
  }
  button {
    background-color: #42b983;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    cursor: pointer;
  }
  button:hover {
    background-color: #369870;
  }
  .badge {
    display: inline-block;
    background: #eef6f3;
    color: #42b883;
    padding: 0.25rem 0.75rem;
    border-radius: 12px;
    font-size: 0.8rem;
    margin-bottom: 0.5rem;
  }
  
  .student-number {
    color: #777;
    font-size: 0.85rem;
  }
  </style>