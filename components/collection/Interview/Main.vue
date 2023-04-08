<template>
    <div>
         <!-- start of Interview Field -->
        <div class="p-[50px] flex divide-y-2 border-y">
            <h1>Mock Interview</h1>
          <!-- start of add button -->
          <div class="ml-[56rem]">
            <button class="flex bg-slate-100" @click="openInterview">
            <PlusIcon class="h-6 w-6"/>
            <p class="ml-3">Add Mock Details</p>
            </button>
            <!-- End of add button -->
            <CollectionInterviewAdd v-if="isInterview" @cancel="isInterview=false"  @save="saveInterviewForm"/>
        </div>
        <!-- end of Interview field -->
        </div>
       <!-- start of showing the candidate Interview -->
        <div class="text-center" v-if="!isInterview">
            <h1 class="text-3xl">Candidate Interview</h1>
            <div>
                <CollectionInterviewList :InterviewUrlData="InterviewUrlData"/>
            </div>
        </div>
        <!-- End of showing the candidate Interview -->
    </div>
</template>
<script setup lang="ts">
//importing the HeroIcon and  useAuthLazyFetch
import { PlusIcon } from "@heroicons/vue/24/outline"
import {useAuthLazyFetch}  from "../../../composables/useAuthLazyFetch"

//Define the schema of InterviewUrl
interface InterviewUrl{
    InterViewUrl:string,
    url:string
}
// Get the props of Interviewurl and url
const props = withDefaults(defineProps<InterviewUrl>(), {
    InterViewUrl: "",
    url:""
})


//Showing the dynamic Interview in the table
const getInterviewUrl = async () => {
    try {
    const { data: InterviewData }= await useAuthLazyFetch(props.InterViewUrl, []);
    return InterviewData;
  } catch (error) {
    console.error("Error fetching tag URL", error);
    return null;
  }
}
const InterviewUrlData = await getInterviewUrl();

const isInterview=ref(false)

////opening the  Interview model
const openInterview=()=>{
    isInterview.value=!isInterview.value
}

// saving the  Interview model
const saveInterviewForm=(addInterviewForm :any)=>{

useAuthLazyFetchPost(`${props.url}/`, {
    body: {
     name:addInterviewForm.name,
     type:addInterviewForm.type,
     max_time_allowed: addInterviewForm.maxTime,
    due_date: addInterviewForm.dueDate,
    difficulty_level:addInterviewForm.difficulty_level,
    description: addInterviewForm.description,
    questions:addInterviewForm.questions,
    multiple_attempts_allowed: addInterviewForm.multipleAttempts,
    instructions: addInterviewForm.instructions,
    status: addInterviewForm.status,
    owner_id: "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    last_modified_date: addInterviewForm.lastModified
    }
  });
}


</script>