<script setup lang="ts">
import { ref } from 'vue';
const isInterestCalculated=ref(false)
const principalAmount=ref(0)
const rateOfInterest=ref(0)
const startDate=ref(new Date())
const endDate=ref(new Date())
const interestToPaid=ref(0)
const totalAmountToPaid=ref(0)
function intializeDates(){
  const date= new Date();
  return `${date.getFullYear()}-${date.getMonth()+1}-${date.getDate()}`
}
</script>
<template>
  <div class="d-flex justify-center">
    <VCard elevation="2" width="700">
      <VCardItem>
        <VCardTitle class="text-h4">
          Interest Calculator
        </VCardTitle>
      </VCardItem>
      <VDivider/>
      <VCardText>
        <VRow>
          <VCol cols="12" lg="5" md="6" sm="12" class="mt-2 text-subtitle-1">
            <p>Principal Amount</p>
          </VCol>
          <VCol cols="12" lg="5" md="6" sm="12">
            <VTextField placeholder="enter amount value" density="compact"
            v-model="principalAmount">
            </VTextField>
          </VCol>
        </VRow>
        <VRow>
          <VCol cols="12" lg="5" md="6" sm="12" class="mt-2 text-subtitle-1">
            <p>Rate of Interest (%)</p>
          </VCol>
          <VCol cols="12" lg="5" md="6" sm="12">
            <VTextField placeholder="enter amount value" density="compact"
            v-model="rateOfInterest">
            </VTextField>
          </VCol>
        </VRow>
        
        <VRow>
          <VCol cols="12" lg="5" md="6" sm="12" class="mt-2 text-subtitle-1">
            <p>Start Date</p>
          </VCol>
          <VCol cols="12" lg="5" md="6" sm="12">
            <VMenu>
              <template v-slot:activator="{ props }">
                <VTextField v-bind="props" density="compact" placeholder="Select a date" :value="startDate"/>
              </template>
              <VDatePicker v-model="startDate" placeholder="Enter amount value" />
            </VMenu>
           
            <!-- <input type="date" placeholder="enter amount value" style="{border-color: #3675b4;}" v-model="startDate"/> -->
          </VCol>
        </VRow>
        <!-- {{ startDate }} -->
        <VRow>
          <VCol cols="12" lg="5" md="6" sm="12" class=" text-subtitle-1">
            <p>End Date</p>
          </VCol>
          <VCol cols="12" lg="5" md="6" sm="12">
            <input type="date" placeholder="enter amount value" v-model="endDate" />
          </VCol>
        </VRow>
        <VBtn color="success" class="my-2" @click="isInterestCalculated=true">
          Calculate
        </VBtn>
        <VRow v-if="isInterestCalculated">
          <VCol cols="12" lg="5" md="6" sm="12" class="mt-2 text-subtitle-1">
            <p>Total interest amount</p>
          </VCol>
          <VCol cols="12" lg="5" md="6" sm="12">
            <VTextField placeholder="enter amount value" density="compact"
            v-model="interestToPaid">
            </VTextField>
          </VCol>
        </VRow>
        <VRow v-if="isInterestCalculated">
          <VCol cols="12" lg="5" md="6" sm="12" class="mt-2 text-subtitle-1">
            <p>Total amount to be paid</p>
          </VCol>
          <VCol cols="12" lg="5" md="6" sm="12">
            <VTextField placeholder="enter amount value" density="compact"
            v-model="totalAmountToPaid">
            </VTextField>
          </VCol>
        </VRow>
      </VCardText>
    </VCard>
  </div>
</template>