
<script>
import { store } from '../store';
export default {
    name: 'Search',
    props: ['archetypes'],
    data(){
        return {
            store
        }
    }
}
</script>


<template>
    <section>
        <select @change="$emit('ricerca')" v-model="store.searchKey">
            <option value="">Selezione archetipo</option>
            <option v-for="arc in archetypes">{{ arc.archetype_name }}</option>
        </select>
    </section>
</template>

<style lang="scss" scoped></style>