<template>
    <div class="footer">
        <div class="total-box">
            <input type="checkbox"
                v-model="isCheck"
            >
            <span>已完成{{finishedCount}}件 / 总计{{todos.length}}件</span>
        </div>
        <button @click="delFinishedToDo">清除已完成任务</button>
        
    </div>
</template>

<script>
export default {
    name: "Footer",
    props: {
        todos: Array,
        selectedAll: Function,
        delFinishedToDo: Function
    },
    computed:{
        finishedCount() {
            return this.todos.reduce((total, todo) => total + (todo.finished ? 1 : 0), 0 )
        },
        isCheck:{
            // 取值
            get() {
                return this.finishedCount === this.todos.length && this.todos.length > 0;
            },
            // 设置属性里的值
            set(value) {
                this.selectedAll(value)
            }
        }
    }
}
</script>

<style scoped>
    .footer {
        width: 820px;
        height: 60px;
        margin: 20px auto;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: row;
        background-color: #fff;
    }
    .footer .total-box {
        flex: 7;
        display: flex;
        justify-content: left;
        align-items: center;
        background-color: #fff;
    }
    .footer .total-box input {
        margin-right: 20px;
    }
    .footer button {
        flex: 1;
        padding: 10px;
        color: #fff;
        border-radius: 8px;
        background-color: orange;
        border: none;
    }
    .footer button:hover {
        background-color: rgb(245, 106, 42);
    }
</style>