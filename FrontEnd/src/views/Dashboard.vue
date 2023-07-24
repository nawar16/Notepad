<template>
    <PageComponent title="Dashboard">
      <div v-if="loading" class="flex justify-center">Loading...</div>
      <div
        v-else
        class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5 text-gray-700"
      >
        <div
          class="bg-white shadow-md p-3 text-center flex flex-col animate-fade-in-down order-1 lg:order-2"
          style="animation-delay: 0.1s"
        >
         
        </div>
        <div
          class="bg-white shadow-md p-3 text-center flex flex-col order-2 lg:order-4 animate-fade-in-down"
          style="animation-delay: 0.2s"
        >
          <h3 class="text-2xl font-semibold">Total Answers</h3>
          <div
            class="text-8xl pb-4 font-semibold flex-1 flex items-center justify-center"
          >
            {{ data.totalAnswers }}
          </div>
        </div>
        <div
          class="row-span-2 animate-fade-in-down order-3 lg:order-1 bg-white shadow-md p-4"
        >
       
       
         
        </div>
        <div
          class="bg-white shadow-md p-3 row-span-2 order-4 lg:order-3 animate-fade-in-down"
          style="animation-delay: 0.3s"
        >
          <div class="flex justify-between items-center mb-3 px-2">
            <h3 class="text-2xl font-semibold">Latest Answers</h3>
  
            <a
              href="javascript:void(0)"
              class="text-sm text-blue-500 hover:decoration-blue-500"
            >
              View all
            </a>
          </div>
  
          <div v-if="data.latestAnswers.length">
            <a
              href="#"
              v-for="answer of data.latestAnswers"
              :key="answer.id"
              class="block p-2 hover:bg-gray-100/90"
            >
            
              <small>
                Answer Made at:
                <i class="font-semibold">{{ answer.end_date }}</i>
              </small>
            </a>
          </div>
          <div v-else class="text-gray-600 text-center py-16">
            Your don't have answers yet
          </div>
        </div>
      </div>
    </PageComponent>
  </template>
  
  <script setup>
  import PageComponent from "../components/PageComponent.vue";
  import { computed } from "vue";
  import { useStore } from "vuex";
  
  const store = useStore();
  
  const loading = computed(() => store.state.dashboard.loading);
  const data = computed(() => store.state.dashboard.data);
  
  store.dispatch("getDashboardData");
  </script>
  
  <style scoped></style>
  