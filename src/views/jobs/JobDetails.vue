<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <!-- <p>the job id is {{ $route.params.id }}</p> -->
    <p>the job id is {{ id }}</p>
    <p>{{ job.details }}</p>
  </div>
  <dir v-else>
    <p>loading job.....</p>
  </dir>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
      job: null,
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
</style>