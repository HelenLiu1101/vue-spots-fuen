<template>
    <select class="form-select" @change="changeHandler" v-model="theSort">
        <option value="spotId">景點編號升冪</option>
        <option value="-spotId">景點編號降冪</option>
        <option value="spotTitle">景點名稱升冪</option>
        <option value="-spotTitle">景點名稱降冪</option>
    </select>
</template>
    
<script setup>
import { reactive, ref } from 'vue'
const theSort = ref("spotId")
const sortItem = reactive({
    "type": "asc",
    "by": "spotId"
})
const emit = defineEmits(["sortChange"])
const changeHandler = () => {
    sortItem.type = theSort.value.startsWith('-') ? "desc" : "asc";
    sortItem.by = theSort.value.replace(/^-/, '');
    console.log(sortItem);
    emit("sortChange", sortItem)
}

</script>
    
<style></style>