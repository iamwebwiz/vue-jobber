<template>
  <div>
    <div class="accordion" id="accordionExample">
      <div
        class="card my-2 text-left border rounded"
        v-for="(job, index) in jobs"
        :key="index"
      >
        <div class="card-header" :id="`heading${index}`">
          <h2 class="mb-0">
            <button
              class="btn btn-link collapsed"
              type="button"
              data-toggle="collapse"
              :data-target="`#collapse${index}`"
              aria-expanded="false"
              :aria-controls="`collapse${index}`"
            >
              {{ job.jobtitle }}
            </button>
          </h2>
        </div>

        <div
          :id="`collapse${index}`"
          class="collapse"
          :aria-labelledby="`heading${index}`"
          data-parent="#accordionExample"
        >
          <div class="card-body">
            <div class="media">
              <img
                src="http://lorempixel.com/60/60/business"
                class="mr-3 rounded"
                :alt="job.jobtitle"
              />
              <div class="media-body">
                <a :href="job.joburl"
                  ><h5 class="mt-0">{{ job.jobtitle }}</h5></a
                >
                <p><strong>Company:</strong> {{ job.companyname }}</p>
                <p><strong>Date:</strong> {{ job.date }}</p>
                <h6><strong>Description</strong></h6>
                <p>{{ job.jobdescription }}</p>
              </div>
              <a href="#" class="btn btn-primary px-auto">Apply for this job</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "JobsList",
    data() {
      return {
        jobs: []
      };
    },
    mounted() {
      this.fetchJobs();
    },
    methods: {
      fetchJobs() {
        fetch("/jobs.json")
          .then(res => res.json())
          .then(jobs => {
            this.jobs = jobs;
          })
          .catch(err => console.log(err));
      }
    }
  };
</script>
