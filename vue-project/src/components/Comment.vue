<script setup>
import { ref, onMounted } from 'vue'
import { supabase } from '../lib/supabaseClient'

const comment = ref([])

async function getComment() {
  const { data } = await supabase.from('comment').select()
  comment.value = data
}

onMounted(() => {
  getComment()
})
</script>

<template>
  <ul>
    <li v-for="comment in comment" :key="comment.id">{{ comment.name }}</li>
  </ul>
</template>