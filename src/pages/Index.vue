<template>
  <q-page style="padding: 2em;">

    <q-jumbotron>
      <div class="q-display-3">Add new item</div>
      <div class="q-title q-mb-md">
        <q-field>
          <q-input v-model="title" float-label="Title"/>
        </q-field>
        <q-field>
          <q-input v-model="desc" float-label="Description"/>
        </q-field>
      </div>
      <q-btn v-on:click='add' color="primary" class="q-py-sm q-px-xl" icon="create" label="Create"/>
    </q-jumbotron>
    <div class="row gutter" style="margin-top: 2em;">
      <q-card v-for="(value, key) in items" :key="key" inline style="width: 100%; margin-top: 1em;">
        <q-card-title>
          {{ value.title }}
        </q-card-title>
        <q-card-separator/>
        <q-card-main>
          {{ value.desc }}
        </q-card-main>
        <q-card-actions>
          <q-btn v-on:click='remove(key)' color="red" class="q-py-sm q-px-xl" icon="delete" label="remove"/>
        </q-card-actions>
      </q-card>
    </div>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  data: function () {
    return {
      items: [
        { title: 'Title 1', desc: 'description 1' },
        { title: 'Title 2', desc: 'description 2' }
      ],
      title: '',
      desc: ''
    }
  },
  methods: {
    remove: function (id) {
      this.items.splice(id, 1)
    },
    add: function () {
      debugger
      if (!this.title.length || !this.desc.length) {
        return
      }
      this.items.push({
        title: this.title,
        desc: this.desc
      })
      this.title = ''
      this.desc = ''
    }
  }
}
</script>
