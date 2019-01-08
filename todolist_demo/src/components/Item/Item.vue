<template>
    <li class="todo_item" 
        @mouseenter="dealShow(true)"
        @mouseleave="dealShow(false)"
        :style="{background: bgColor}">
        <label>
            <input class="checkbox" type="checkbox" v-model="todo.finished">
            <span>{{todo.title}}</span>
        </label>
        <button 
            v-if="isShowDelButton"
            @click="delItem"
        >删除</button>
    </li>
</template>

<script>
export default {
    name: "Item",
    data() {
        return {
            bgColor: "#fff",
            isShowDelButton: false
        }
    },
    props: {
        todo: Object,
        index: Number,
        delToDo: Function
    },
    methods: {
        // 鼠标进入和离开li
        dealShow(flag) {
            this.bgColor = flag ? "#ddd" : "#fff";
            this.isShowDelButton = flag
        },
        delItem() {
            if(window.confirm(`确定删除${this.todo.title}吗？`)) {
                this.delToDo(this.index)
            }
        }
    }
}
</script>

<style scoped>
    .todo_item {
        list-style: none;
        border: 1px solid #ebebeb;
        border-radius: 8px;
        width: 100%;
        height: 35px;
        margin: 20px 0;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: row;
    }
    .todo_item label {
        flex: 10;
        height: 100%;
        display: flex;
        justify-content: left;
        align-items: center;
    }
    .todo_item label .checkbox {
        margin-right: 15px;
    }
    .todo_item button {
        flex: 1;
        height: 80%;
        color: #fff;
        background-color: rgb(245, 106, 42);
        padding: 0px;
        border: none;
        border-radius: 8px;
    }
</style>
