<template>
    <div class="header">
            <input class="input" type="text" 
                placeholder="请输入今天的任务，按回车键确认"
                v-model="title"
                @keyup.enter="addItem"
            >
    </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            title: ""
        }
    },
    props: {
        addToDo: Function
    },
    methods: {
        addItem() {
            // 1.1 判断是否合理
            const title = this.title.trim();
            if(!title) {
                alert("输入的内容不能为空");
                return;
            }
            // 1.2 生成todo对象
            const todo = {title, finished: false};
            // 1.3 调用方法
            this.addToDo(todo);
            // 1.4 清空输入方法
            this.title = '';
        }
    }

}
</script>

<style scoped>
    .input {
        width: 800px;
        height: 40px;
        margin: 15px 0;
        padding-left: 20px;
        background-color: #ebebeb;
        outline: none;
        border: 1px solid #ebebeb;
        border-radius: 8px;
    }
</style>


