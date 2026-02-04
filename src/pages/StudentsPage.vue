<template>
    <div class="students">
      <header class="header">
        <h1>Students</h1>
        <p class="subtitle">List of enrolled students</p>
        <span class="count">{{ students.length }} Students</span>
      </header>
  
      <p v-if="loading" class="status">Loading students...</p>
      <p v-if="error" class="error">{{ error }}</p>
  
      <div class="grid" v-if="!loading && !error">
        <StudentComponent
          v-for="student in students"
          :key="student.id"
          :name="student.name"
          :course="student.course"
          :year="student.year"
          :studentNumber="student.studentNumber"
          :email="student.email"
          :phone="student.phone"
        />
      </div>
    </div>
  </template>
  
  <script>
    import StudentComponent from '@/components/StudentComponent.vue'

    export default {
    name: 'StudentsPage',
    components: { StudentComponent },
    data() {
        return {
        students: [],
        loading: false,
        error: null,
        courses: [
            'Computer Science',
            'Information Technology',
            'Software Engineering',
            'Data Science',
            'Cybersecurity',
            'Artificial Intelligence'
        ]
        }
    },
    mounted() {
        this.fetchStudents()
    },
    methods: {
        getRandomCourse() {
        return this.courses[Math.floor(Math.random() * this.courses.length)]
        },
        getRandomYear() {
        return Math.floor(Math.random() * 4) + 1
        },
        generateStudentNumber(id) {
        return `2026-${String(id).padStart(4, '0')}`
        },
        async fetchStudents() {
        this.loading = true
        this.error = null

        try {
            const response = await fetch('https://jsonplaceholder.typicode.com/users')
            if (!response.ok) throw new Error('Failed to load students')

            const data = await response.json()

            // Enhance API data
            this.students = data.map(student => ({
            ...student,
            course: this.getRandomCourse(),
            year: this.getRandomYear(),
            studentNumber: this.generateStudentNumber(student.id),
            email: student.name.toLowerCase().replace(' ', '.') + '@example.com'
            }))
        } catch (err) {
            this.error = err.message
        } finally {
            this.loading = false
        }
        }
    }
    }
    </script>
  
  <style scoped>
    .students {
    max-width: 1200px;
    margin: auto;
    padding: 2.5rem 1.5rem;
    background: linear-gradient(to bottom, #f9fafb, #ffffff);
    min-height: 100vh;
    }

    .header {
    text-align: center;
    margin-bottom: 3rem;
    position: relative;
    }

    .header h1 {
    font-size: 2.8rem;
    color: #1f2937;
    margin-bottom: 0.5rem;
    }

    .subtitle {
    color: #6b7280;
    font-size: 1.1rem;
    }

    .count {
    display: inline-block;
    margin-top: 1rem;
    background: linear-gradient(135deg, #42b883, #369870);
    color: white;
    padding: 0.4rem 1.2rem;
    border-radius: 999px;
    font-size: 0.9rem;
    font-weight: 600;
    box-shadow: 0 4px 10px rgba(66, 184, 131, 0.3);
    }

    .status {
    text-align: center;
    color: #6b7280;
    font-size: 1.1rem;
    margin-top: 2rem;
    }

    .error {
    text-align: center;
    color: #dc2626;
    font-weight: 600;
    margin-top: 2rem;
    }

    .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    }

    .student {
    background: white;
    border-radius: 16px;
    padding: 1.8rem;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    position: relative;
    overflow: hidden;
    }

    .student::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    height: 5px;
    width: 100%;
    background: linear-gradient(90deg, #42b883, #35495e);
    }

    .student:hover {
    transform: translateY(-6px);
    box-shadow: 0 18px 35px rgba(0, 0, 0, 0.15);
    }

    .student-number {
    color: #6b7280;
    font-size: 0.85rem;
    margin-bottom: 0.75rem;
    }

    .student-name {
    font-size: 1.3rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    color: #1f2937;
    }
    
    .students {
    animation: fadeIn 0.6s ease-in-out;
    }

    @keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(10px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
    }
  </style>
  