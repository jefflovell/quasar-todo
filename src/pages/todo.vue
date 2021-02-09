<template>
  <q-page class="bg-grey-3 column">

    <q-list
      class="bg-white"
      separator
      bordered>
      <!--
        Rendering a <label> tag (notice tag="label")
        so QCheckboxes will respond to clicks on QItems to
        change Toggle state.
      -->

      <q-item
        v-for="(task, index) in tasks"
        :key="task.title"
        @click="task.done = !task.done"
        clickable
        :class="{ 'done bg-blue-1' : task.done }"
        v-ripple>

        <q-item-section avatar>
          <q-checkbox
            v-model="task.done"
            class="no-pointer-events"
            color= "accent" />
        </q-item-section>

        <q-item-section>
          <q-item-label>{{task.title}}</q-item-label>
        </q-item-section>

        <q-item-section
          v-if="task.done"
          side>
          <q-btn
            @click.stop='deleteTask(index)'
            flat
            round
            color="primary"
            icon="delete" />
        </q-item-section>
      </q-item>

    </q-list>

    <div class="q-px-sm q-mt-sm">
      Your selection is: <strong>{{ }}</strong>
    </div>

  </q-page>
</template>

<script>
export default {
  data () {
    return {
      tasks: [
        {
          title: 'Dev App',
          done: false
        },
        {
          title: 'Debug App',
          done: false
        },
        {
          title: 'Deploy App',
          done: false
        }
      ]
    }
  },
  methods: {
    deleteTask (index) {
      this.$q.dialog({
        title: 'Confirm',
        message: 'Really delete?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.tasks.splice(index, 1)
      }).onOk(() => {
        // console.log('>>>> second OK catcher')
      }).onCancel(() => {
        // console.log('>>>> Cancel')
      }).onDismiss(() => {
        // console.log('I am triggered on both OK and Cancel')
      })
    }
  }
}
</script>

<style lang="scss">
  .done {
    .q-item__label {
      text-decoration: line-through;
      color: #aaa
    }
  }
</style>
