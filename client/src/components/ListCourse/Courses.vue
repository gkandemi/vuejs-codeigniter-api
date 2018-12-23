<template>
  <div class="row">
    <div class="col-md-8 offset-2 mt-5">
      <table v-if="courses.length > 0" class="table table-hover table-dark table-striped border-dark border shadow-lg">
        <thead>
        <th>#id</th>
        <th>Kursun Adı</th>
        <th>Kupon Kodu</th>
        <th>Ücreti</th>
        <th>İşlem</th>
        </thead>
        <tbody>
          <Course v-for="course in courses" :key="course.id" :course="course" />
        </tbody>
      </table>
      <div v-else class="alert alert-primary border-0">
        Henüz eklenmiş bir kurs bulunmamaktadır.
      </div>
      <router-link
        to="/yeni"
        tag="button"
        class="btn-dark btn text-info float-right">
        Yeni Ekle
      </router-link>
    </div>
  </div>
</template>

<script>
  import Course from "./Course"
  export default {
    components : {
      Course
    },
    computed : {
      courses(){
        return this.$store.getters.getCourses
      }
    }
  }
</script>
