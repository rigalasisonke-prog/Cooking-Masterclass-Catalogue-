<script>
import NavBar from './NavBar.vue';

export default{
        components:{
            NavBar
        },
        data(){
            return{
                courses: [
                        {
                            id: 1,
                            title: "Mastering Italian Pasta",
                            price: 299,
                            skill_level: "Beginner",
                            isSaved: false,
                            img: "https://online.tut.ac.za/hubfs/TUT_Exec%20chef%20blog.jpg"
                        },
                        {
                            id: 2,
                            title: "Sushi Rolling Essentials",
                            price: 350,
                            skill_level: "Intermediate",
                            isSaved: true,
                            img: "https://www.silwood.co.za/wp-content/uploads/2024/03/silwood-school-of-cookery-chefs-in-training.jpg"
                        },
                        {
                            id: 3,
                            title: "French Pastry Techniques",
                            price: 420,
                            skill_level: "Advanced",
                            isSaved: true,
                            img: "https://www.expatcapetown.com/images/cookingclasses-2.jpg"
                        },
                        {
                            id: 4,
                            title: "Vegan Cooking Fundamentals",
                            price: 250,
                            skill_level: "Beginner",
                            isSaved: false,
                            img: "https://olivebranchcooking.co.za/wp-content/uploads/2024/02/Chef-Margy-1229x1536.jpg"
                        }
                    ]
                }
            },
            methods:{
                    toggleSave(courseID){
                        const courseToSave = this.courses.find(course => course.id === courseID)
                        if (courseToSave) {
                            courseToSave.isSaved = !courseToSave.isSaved
                        }
                    }
            }
        }
</script>
<template>
    <div class="container">
        <NavBar :courses="courses"/>
        <hr>
        </div>
        <div class="cards">
        <div class="card" style="width: 18rem;" v-for="course in courses" :key="course.id">
            <img :src="course.img" class="card-img-top" :alt="course.id">
            <div class="card-body">
                <h5 class="card-title">{{course.title}}</h5>
                <p class="card-text">{{course.price}}</p>
                <p class="card-text">{{course.skill_level}}</p>
                <a href="#" :class="['btn', course.isSaved?'btn-success' : 'btn-danger']" @click="toggleSave(course.id)">{{ course.isSaved ? 'course saved' : 'save course' }}</a>
            </div>
        </div>
    </div>

</template>
<style></style> 