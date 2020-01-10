<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
const { graphql, buildSchema } = require('graphql')

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted () {
    this.init()
  },
  methods: {
    init () {
      const schema = buildSchema(`
        type Query {
          hello: String
        }
      `)
      const root = {
        hello: () => 'hello graphQL'
      }
      graphql(schema, '{ hello }', root).then(response => {
        console.log(response)
      })
    }
  }
}
</script>
