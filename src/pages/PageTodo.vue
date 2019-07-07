<template>
  <q-page padding>
    <div class="row">
      <div class="col-6">
        <q-list bordered dark>
          <q-item-label dark header v-text="'Tasks to be done'" />

          <q-item
            dark
            v-for="item in tasks"
            :key="item.id"
            v-ripple
            clickable
            @click="item.completed = !item.completed"
          >
            <q-item-section side top>
              <q-checkbox dark v-model="item.completed" />
            </q-item-section>

            <q-item-section>
              <q-item-label v-text="item.name" />
              <q-item-label caption v-text="formatDate(item.dueDate)" />
            </q-item-section>
          </q-item>

        </q-list>
      </div>
    </div>
  </q-page>
</template>

<style>
</style>

<script>
import moment from 'moment'
export default {
  name: 'PageTodo',
  data () {
    return {
      tasks: [
        { id: 1, name: 'Go to store', dueDate: '2019-07-10', completed: false },
        { id: 2, name: 'Jog at stadium', dueDate: '2019-07-10', completed: false },
        { id: 3, name: 'Buy some eggs', dueDate: '2019-07-10', completed: false },
        { id: 4, name: 'Get the car', dueDate: '2019-07-10', completed: false },
        { id: 5, name: 'Go to university', dueDate: '2019-07-10', completed: false },
      ]
    }
  },
  methods: {
    formatDate: date => moment(date).format('DD/MM/YYYY')
  }
}
</script>
