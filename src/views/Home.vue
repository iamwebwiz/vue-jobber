<template>
  <div class="home container">
    <div class="row my-5">
      <div class="col-12">
        <h1 class="text-left d-4">Vue Jobber</h1>
      </div>
    </div>

    <div class="row">
      <div class="col-12">
        <jobs-list></jobs-list>
      </div>
    </div>
  </div>
</template>

<script>
  import JobsList from "@/components/JobsList";

  export default {
    name: "Home",
    components: { JobsList }
  };
</script>
