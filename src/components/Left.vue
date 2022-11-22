<template>
    <div class="left">
        <h3>Left组件 --- count is: {{ count }}</h3>
        <button @click="add">count+1</button>
    </div>
</template>

<script>

export default {

    // props: ['left_count'],

    data() {
        return {
            // count: this.left_count,
            count: 0
        }
    },

    methods: {
        add() {
            this.count++;
            // this.$emit('left_count_add', this.count);
        }
    },

    mounted() {

    }

}

</script>

<style lang="less" scoped>
.left {
    float: left;
    background-color: aqua;
    padding: 5px 0px 20px 20px;
    font-weight: bolder;
    width: 48%;
}

/deep/ h5 {
    color: red;
}
</style>