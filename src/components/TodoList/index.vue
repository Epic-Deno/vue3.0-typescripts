<!--
 * @Description: KEEP CALM AND MAKE EPIC SHIT - PONY ZHANG
 * @Version: 2.0
 * @Autor: PONY ZHANG
 * @Date: 2020-11-08 22:01:32
 * @LastEditors: PONY ZHANG
 * @LastEditTime: 2021-01-08 18:36:51
-->
<template>
  <div>
      <h1>TodoList</h1>
      <todo-item
        v-for="item in todoList"
        :key="item.id"
        :todoItem="item"
        @removeTodo="removeTodo"
        @setStatus="setStatus"
        @setDoing="setDoing"
      ></todo-item>
  </div>
</template>

<script lang="ts">
import { IUseTodo, useTodo } from '@/hooks'
import { ITodo } from '@/typings'
import { defineComponent, onMounted, PropType, reactive } from 'vue'
import TodoItem from './Item.vue'
interface CardList {
    title: string,
    icon: string,
    price: number,
    up: boolean,
    mon: string,
    percent: string,
}
interface Todo {
    growCardList: CardList
}
export default defineComponent({
    name:'TodoList',
    props: {
        todoList: Array as PropType<ITodo[]>,
    },
    components: {
        TodoItem
    },
    setup(props) {
        const { removeTodo,setStatus,setDoing }: IUseTodo = useTodo();
        const data =  reactive({
            growCardList: [] as CardList[]
        })
        return {
            removeTodo,
            setStatus,
            setDoing,
        }
    },
})
</script>

<style>

</style>