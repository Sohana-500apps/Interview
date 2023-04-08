<template>
   <!-- start of showing Interview in the table -->
    <div class="overflow-auto">
        <table class="table-auto w-full">
          <thead>
            <tr>
              <th class="px-4 py-2">Candidate Name</th>
              <th class="px-4 py-2">Type</th>
              <th class="px-4 py-2">Max Time Allowed</th>
              <th class="px-4 py-2">Due Date</th>
              <th class="px-4 py-2">Difficulty leave</th>
              <th class="px-4 py-2">Description</th>
              <th class="px-4 py-2">Questions</th>
              <th class="px-4 py-2">Instructions</th>  
              <th class="px-4 py-2">Multile Attempts Allowed</th>
              <th class="px-4 py-2">Status</th>
              <th class="px-4 py-2">Last Modified Date</th>
              <th class="px-4 py-2">Delete Action</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(interview,index) in InterviewUrlData" :key="interview">
              <td class="border px-4 py-2">{{interview.name}}</td>
              <td class="border px-4 py-2">{{interview.type}}</td>
              <td class="border px-4 py-2">{{interview.max_time_allowed}}</td>
              <td class="border px-4 py-2">{{interview.due_date}}</td>
              <td class="border px-4 py-2">{{interview.difficulty_level}}</td>
              <td class="border px-4 py-2">{{interview.questions}}</td>
                <td class="border px-4 py-2">{{interview.multiple_attempts_allowed}}</td>
                <td class="border px-4 py-2">{{interview.instructions}}</td>
               <td class="border px-4 py-2">{{interview.status}}</td>
              <td class="border px-4 py-2">{{interview.owner_id}}</td>
                <td class="border px-4 py-2">{{interview.last_modified_date}}</td>
                <td class="border px-4 py-2">
                  <CollectionInterviewDelete  @delete="deleteInterview(interview)"/>
                </td>
            </tr>
          </tbody>
        </table>
      </div>
       <!-- End of showing Interview in the table -->
</template>
<script setup lang="ts">
//Defining the schema of Fieldschema
interface InterviewSchema{
    name:string,
  type:string,
  max_time_allowed:number,
  due_date:string,
  difficulty_level:string,
  questions:object,
  multiple_attempts_allowed:number,
  instructions:object,
  status:number,
  owner_id:string,
  last_modified_date:string
}
// Getting the props of InterviewData
let props = defineProps<{ InterviewUrlData:InterviewSchema }>()
const emits = defineEmits(['edit','delete']);
//Emitting the delete and pass it in the main
const deleteInterview=(interview)=>{
  emits('delete',interview)
}
</script>