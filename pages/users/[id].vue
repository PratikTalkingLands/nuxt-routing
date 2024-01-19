<template>
    <div class="h-100 w-100">
        <div class="h-100 w-100 d-flex justify-center ma-3">
            <v-row>
                <v-col cols="3" class="">
                    <v-card class="bg-grey-lighten-2">
                        <div class="d-flex flex-column h-50 flex-gap-20 ma-8">
                            <div>
                                <v-avatar>
                                    <v-img :src="data.image" :lazy-src="data.image" alt="image"></v-img>
                                </v-avatar>
                                <p class="text-body-1 font-weight-bold my-1">{{ data.firstName }}</p>
                                <div class="d-flex flex-gap-10">
                                    <v-icon size="small" icon="mdi-email"></v-icon>
                                    <p>{{ data.email }}</p>
                                </div>
                                <div class="d-flex flex-gap-10">
                                    <v-icon size="small" icon="mdi-phone"></v-icon>
                                    <p>{{ data.phone }}</p>
                                </div>
                            </div>

                            <div class="d-flex flex-column flex-gap-20">
                                <v-btn variant="outlined"
                                :to="{
                                    name: 'users-id-posts',
                                    params: { id: data.id },
                                }">POSTS</v-btn>
                                <v-btn variant="outlined"
                                :to="{
                                    name: 'users-id-todos',
                                    params: { id: data.id },
                                }">TODOS</v-btn>
                                <v-btn variant="outlined"
                                :to="{
                                    name: 'users-id-cart',
                                    params: { id: data.id },
                                }">CART</v-btn>
                            </div>

                        </div>
                    </v-card>
                </v-col>
                <v-col cols="9" class="pr-10 h-100 w-100 bg-white">
                    <v-card class="bg-grey-lighten-2 mx-1 h-100 bg-white pa-6">
                       <NuxtPage :user="data"/>
                    </v-card>
                </v-col>
            </v-row>
        </div>
    </div>
</template>

<script setup>
const { id } = useRoute().params

const { data } = useFetch(`https://dummyjson.com/users/${id}`)
</script>

<style>
.flex-gap-20 {
    gap: 20px;
}

.flex-gap-10 {
    gap: 10px;
}
</style>