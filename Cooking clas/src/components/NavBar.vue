<script>
    export default{
        props:{
            courses: Array
        },
        computed:{
            savedCourses(){
                return this.courses.filter(course => course.isSaved === true)
            },
            amountSaved(){
                return this.savedCourses.length
            }
        }
    }
</script>
<template>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Wishlist</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavDarkDropdown" aria-controls="navbarNavDarkDropdown" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavDarkDropdown">
      <ul class="navbar-nav">
        <li class="nav-item dropdown">
          <button class="btn btn-dark dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false">
            {{amountSaved}}
          </button>
          <ul class="dropdown-menu dropdown-menu-dark">
            <li><a class="dropdown-item" :href="savedCourse" v-for="savedCourse in savedCourses" :key="savedCourse.id">{{savedCourse.title}}</a></li>
            <li> <span 
                v-if="savedCourses.length === 0" 
                class="dropdown-item"
            >
                No courses saved
            </span></li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</nav>
</template>