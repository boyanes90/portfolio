<style>
  .blue {
    border-top: .2em solid #ffffff
  }
</style>

<template>
  <vuetable ref="vuetable"
            api-url="https://vuetable.ratiw.net/api/users"
            :fields="fields" :css="css.table"
  ></vuetable>
</template>

<script>
  import Vuetable from 'vuetable-2/src/components/Vuetable'
  import CssConfig from './VuetableCssConfig.js'

  export default {
    components: {
      Vuetable
    },
    data () {
    return {
      fields: [
        'name', 'email', 'birthdate',
        {
          name: 'birthdate',
        },
        {
          name: 'nickname',
        },
        {
          name: 'gender',
        },
        {
          name: 'salary',
        }
      ],
      css: CssConfig
    }
  }
  }
</script>
