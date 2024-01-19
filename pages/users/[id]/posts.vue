<template>
    <div class="h-100 w-100">
        <div class="w-100 py-2 d-flex align-center flex-gap-10" @click="routerBack">
            <v-icon icon="mdi-arrow-left"></v-icon>
            <p class="text-h6">Back</p>
        </div>
        <div class="w-100 h-100 d-flex flex-column px-8 overflow-y-auto flex-gap-10">
            <v-card v-for="post in data.posts" :key="post.id" class="mx-auto w-100 elevation-16">
        <v-card-item>
          <v-card-title>
            {{ post.title }}
          </v-card-title>
          <v-card-subtitle>
            Reactions : {{ post.reactions }}
          </v-card-subtitle>
        </v-card-item>

        <v-card-text>
          {{ post.body }}
        </v-card-text>

        <v-card-subtitle>
            Tags : {{ post.tags.join() }}
        </v-card-subtitle>
      </v-card>
        </div>
    </div>
</template>

<script setup>

const router = useRouter()
const routerBack = () => {
    router.back()
}
const { id } = useRoute().params
const { data } = useFetch(`https://dummyjson.com/users/${id}/posts`)
</script>

<style>
.flex-gap-10 {
    gap: 10px;
}
</style>