<template>
    <v-container>
    <v-row><!-- row คือแถว 1 แถวมี 12 column--><!---->
        <v-col cols="12">
        <LoginForm/>
        </v-col>
    </v-row>
    </v-container>
</template>

<script>
import LoginForm from "../components/Login.vue"
export default{
    components: {
        LoginForm
    }
}
</script>

<style>
</style>
