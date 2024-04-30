<template>
  <main class="min-h-screen">
    <AppHeader class="mb-12" title="Projects" :description="description" />
    <div class="space-y-4">
      <AppProjectCard
        v-for="(project, id) in projects"
        :key="id"
        :project="project"
      />
    </div>
  </main>
</template>

<script setup>
const description =
  "I’ve worked on tons of open source projects over the years but these are the ones that I’m most proud of. If you see something that piques your interest, check out the code and contribute if you have ideas for how it can be improved.";
useSeoMeta({
  title: "Projects | Xudong Guo",
  description,
});

const { data: projects } = await useAsyncData("projects-all", () =>
  queryContent("/projects").find()
);
</script>
