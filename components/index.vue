<template>
    <!--
      这里的dom节点你可以使用你熟悉的element-ui中的组件代替，
      由于我这个demo小项目用的是vant不是element这里就直接用原生的dom
      自己在使用的时候可以稍作改动
    -->
    <div class="list">
        <div @click.prevent="handleClick">
            <a :href="model.linkUrl">{{ model.name }}</a>
        </div>
        <div v-show="reveal" v-if="isDispaly" style="margin-left:20px;">
            <list-menu v-for="item in model.children" :key="item.id" :model="item" />
        </div>
    </div>
</template>

<script>
export default {
	name: "listMenu",
    props: ["model"],
    components: {
    },
    data () {
	    return {
		    reveal: false
	    };
    },

    mounted() {
    },

    methods: {
	    handleClick() {
		    if (this.isDispaly) {
			    this.reveal = !this.reveal;
		    }
	    }
    },

    computed: {
	    isDispaly() {
		    return this.model.children && this.model.children.length;
	    }
    },
}
</script>
<style lang="scss" scoped>
</style>
