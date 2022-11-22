<template>
    <div class="root">
        <h1 ref="mine_h1_ref">App根组件</h1>
        <!-- 
            <component is="Left"></component>
            <component is="Right"></component> 
        -->
        <p>
            <button @click="show_left">展示Left组件</button> 
            &nbsp; &nbsp;
            <button @click="show_right">展示Right组件</button>
        </p>
        <!-- 下面为了保证 Left.vue 中 count 的值, 加了这么多方法, 其实 vue 作者已经考虑到这点了, 他们用一个 keep-alive 标签就解决了 -->
        <!-- <component :is="component_id" :left_count="left_count" @left_count_add="hold_count" /> -->

        <keep-alive include="Left,Right" exclude="Right" max="1000">
            <component :is="component_id" />
        </keep-alive>
    </div>
</template>

<script>
import Left from "@/components/Left.vue";
import Right from "@/components/Right.vue";

export default {

    components: {
        Left,
        Right
    },

    data() {
        return {
            component_id: '',
            // left_count: 0
        };
    },

    mounted() {

    },

    methods: {
        show_left() {
            this.component_id = 'Left';
        },
        show_right() {
            this.component_id = 'Right';
        },
        // hold_count(val) {
        //     this.left_count = val;
        // }
    },

    // 使用了 keep-alive 标签时, 才有下面两个生命周期函数!
    activated() {
        console.log('激活了组件', this.component_id);
    },

    deactivated() {
        console.log('缓存了组件', this.component_id);
    },
};
</script>

<style lang="less" scoped>
.root {
    padding: 5px 20px 260px 20px;
    background-color: #b9bdb0;
}
</style>