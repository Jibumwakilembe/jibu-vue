<script setup>
import Hero from "@/components/Hero.vue";
import HomeCard from "@/components/HomeCard.vue";
import JobListiing from "@/components/JobListing.vue";
</script>

<template>
  <Hero />
  <HomeCard />
  <JobListiing :limit="6" :showButton="true" />
</template>
