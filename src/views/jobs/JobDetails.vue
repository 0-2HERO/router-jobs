<template>
<div v-if="jobs">

  <h1> {{ jobs.title }}</h1>
  <p>The Job id is {{ id }}</p>
  <p> {{ jobs.details }}</p>
</div>
<div v-else>
    <p>Loading Job details...</p>
</div>
</template>

<script>
export default {
    props: [ 'id'],
    data() {
        return {
            jobs: null
        }
    },
    mounted() {
    fetch('http://localhost:3000/jobs/' + this.id)
   .then(res => res.json())
   .then(data => this.jobs = data)
   .catch(err => console.log(err.message))
    }
    /* data() {
        return {
            id: this.$route.params.id
        }
    } */
}
</script>

<style>

</style>