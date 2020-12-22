<template>
    <div class="ccc">
        <h1>{{title}}</h1>
        <ul v-for="subject in subjects" :key=subject.id class="timeline">
            <li>
                <div v-if="subject.image != ''" class="timeline-image">
                    <img :src="require('@/assets/events/'+subject.image)" alt="" class="rounded-circle" />
                </div>
                
                <div class="timeline-panel">
                    <div class="timeline-heading">{{subject.name}}</div>
                    <div v-if="subject.subheading" class="timeline-subheading"></div>
                    <div class="timeline-body"></div>
                </div>
            </li>
        </ul>


        
    </div>
</template>

<script>
export default {
    props: {
        title:String,
        subjects: Array
    }
}
</script>

<style lang="scss" scoped>
.ccc{
    margin-bottom:1000px;
}
</style>