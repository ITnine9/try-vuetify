<template>
<v-card
    class="mx-auto"
    max-width="400"
    tile
  >
    <v-list>
        <v-subheader>REPORTS</v-subheader>
        <v-list-item v-for="item in list" :key="item.id">
            <v-list-item-content class="d-flex flex-row">
                <v-list-item-title>{{ item.type }}</v-list-item-title>
            </v-list-item-content>

            <v-list-item-icon>
                <v-icon class="mdi mdi-close-circle d-block" @click="delItem(item.id)"></v-icon>
            </v-list-item-icon>
        </v-list-item>
    </v-list>
    
</v-card>
</template>
<script>
export default {
    name: 'selectedList',
    props: ['list'],
    data() {
        return {

        }
    },
    methods: {
        delItem(id) {
            this.$emit('delItem', id);
        }
    }
}

</script>
<style scoped>

</style>
