<script>
export default {
    methods: {
        onChange(e) {
            this.$emit('change-fitler', e.target.value);
        }
    }
}
</script>
<template>
    <div class="filter">
        <p>Choose risk level:</p>
        <select @change="onChange" name="hazard" id="hazard">
            <option value="all">all</option>
            <option value="low">low</option>
            <option value="intermediate">intermediate</option>
            <option value="high">high</option>
        </select>
    </div>
</template>
<style scoped>
    .filter {
        display: flex;
        justify-content: flex-end;
        gap: 10px;
    }

    .filter > p {
        font-weight: 400;
    }
</style>