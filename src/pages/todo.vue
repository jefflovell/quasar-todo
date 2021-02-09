<template>
  <q-page class="bg-grey-3 column">
    <div class="q-pa-md">
    <div class="q-gutter-sm">
    <q-list class="bg-white">
      <!--
        Rendering a <label> tag (notice tag="label")
        so QCheckboxes will respond to clicks on QItems to
        change Toggle state.
      -->

      <q-item v-ripple>
        <q-item-section avatar>
          <q-checkbox
            v-model="color"
            val="teal"
            color="teal" />
        </q-item-section>
        <q-item-section>
          <q-item-label>Teal</q-item-label>
        </q-item-section>
      </q-item>

    </q-list>
    </div>

    <div class="q-px-sm q-mt-sm">
      Your selection is: <strong>{{ color }}</strong>
    </div>
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
  }
}
</script>
