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
              <q-item-label caption v-text="item.description" />
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
export default {
  name: 'PageTodo',
  data () {
    return {
      tasks: [
        { id: 1, name: 'Go to store', description: 'Go to Walmart and grab an oil can', completed: false },
        { id: 2, name: 'Jog at stadium', description: 'Start the exercise week, if possible...', completed: false },
        { id: 3, name: 'Buy some eggs', description: 'We have to eat some proteins sometimes, haven\'t we?', completed: false },
        { id: 4, name: 'Get the car', description: 'If it is fixed, go to Moe\'s car office', completed: false },
        { id: 5, name: 'Go to university', description: 'Study to test', completed: false },
      ]
    }
  }
}
</script>
