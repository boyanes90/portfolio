<template>
  <div class="ui container">
    <h3 style="text-align: left;">PORTFOLIO</h3>

    <div class="row" v-on:click="handleShowTable"
         style="border: 1px solid #ddd; text-align: left; margin: 0px; padding-top:7px; padding-bottom:5px; cursor: pointer">
      <span v-if="showTable" class="glyphicon glyphicon-chevron-up"
            style="padding-left: 10px; padding-right: 7px"></span>
      <span v-else class="glyphicon glyphicon-chevron-down" style="padding-left: 10px; padding-right: 7px"></span>EQUITIES
    </div>
    <div class="table-responsive">
      <vuetable v-show="showTable" ref="vuetable"
                api-url="https://vuetable.ratiw.net/api/users"
                :fields="fields" :css="css.table"
                pagination-path=""
                @vuetable:pagination-data="onPaginationData"
                detail-row-component="my-detail-row"
                @vuetable:cell-clicked="onCellClicked">

      </vuetable>
    </div>
    <vuetable-pagination-bootstrap ref="pagination" class="pull-right"
                                   @vuetable-pagination:change-page="onChangePage"></vuetable-pagination-bootstrap>
  </div>
</template>

<script>
  import Vuetable from 'vuetable-2/src/components/Vuetable'
  import Vue from 'vue'
  import VuetablePaginationBootstrap from './VuetablePaginationBootstrap'
  import CssConfig from './VuetableCssConfig.js'
  import DetailRow from './DetailRow'

  Vue.component('my-detail-row', DetailRow)

  export default {
    components: {
      Vuetable,
      VuetablePaginationBootstrap
    },
    data ()
  {
    return {
      fields: [
        {
          name: 'nickname',
          title: 'TICKER',
          titleClass: 'text-left',
          dataClass: 'text-left',
          callback: 'handleTiles'
        }, {
          name: 'nickname',
          title: 'BOOK VALUE',
          titleClass: 'text-right',
          dataClass: 'text-right'
        }, {
          name: 'nickname',
          title: 'MARKET VALUE',
          titleClass: 'text-right',
          dataClass: 'text-right'
        }, {
          name: 'nickname',
          title: '% OF PORTFOLIO',
          titleClass: 'text-right',
          dataClass: 'text-right'
        }, {
          name: 'nickname',
          title: 'TODAY RETURN',
          titleClass: 'text-right',
          dataClass: 'text-right'
        }, {
          name: 'nickname',
          title: '2017',
          titleClass: 'text-right',
          dataClass: 'text-right'
        }, {
          name: 'nickname',
          title: '2016',
          titleClass: 'text-right',
          dataClass: 'text-right'
        }, {
          name: 'nickname',
          title: 'SINCE INCEPTION',
          titleClass: 'text-right',
          dataClass: 'text-right'
        },
      ],
      css: CssConfig,
      showTable: true
    }
  }
  ,
  methods: {
    onPaginationData(paginationData)
    {
      this.$refs.pagination.setPaginationData(paginationData)
    }
  ,
    onChangePage(page)
    {
      this.$refs.vuetable.changePage(page)
    }
  ,
    handleShowTable()
    {
      this.$data.showTable = !this.$data.showTable;
    }
  ,
    handleTiles(value)
    {
      return '<span class="glyphicon glyphicon-chevron-down"></span>' + value
    }
  ,
    handleShowTiles(value)
    {
      console.log("handle tiles: ", value)
    }
  ,
    onCellClicked(data, field, event)
    {
      console.log('cellClicked: ', field.name)
      this.$refs.vuetable.toggleDetailRow(data.id)
    }
  }
  }
</script>
