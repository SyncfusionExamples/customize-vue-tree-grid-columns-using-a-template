<template>
  <ejs-treegrid :dataSource="data" childMapping="Children" :allowPaging="true"
    :treeColumnIndex="0" :height='450' :rowHeight="83">
    <e-columns>
      <e-column field='EmpID' headerText='Employee ID' width='180'></e-column>
      <e-column headerText="Image" width="120" :template="'imageTemplate'"></e-column>
      <e-column :headerTemplate="'iconTemplate'" :template="'nameTemplate'"></e-column>
      <e-column :headerTemplate="'iconTemplate2'" :template="'addrTemplate'" width='350'></e-column>
      <e-column field='DOB' :headerTemplate="'iconTemplate3'" format='yMd'></e-column>
    </e-columns>
    <template v-slot:addrTemplate="{data}">
      <div style="display:inline-block;">
        <div>{{data.Address}}, {{data.Country}}</div>
        <div class="e-column-data">{{data.Contact}}</div>
      </div>
    </template>
    <template v-slot:imageTemplate="{data}">
      <img :src="'https://ej2.syncfusion.com/vue/demos/source/tree-grid/images/'+ data.FullName + '.png'"
          alt="data.FullName"/>
    </template>
    <template v-slot:nameTemplate="{data}">
      <div style="font-size: 14px;">
        {{data.Name}}
        <p class="e-column-data">{{data.Designation}}</p>
      </div>
    </template>
    <template v-slot:iconTemplate>
      <div>
        <span class="e-icons e-people e-font-icon" style="font-size: 15px;"></span>
        <span class="e-headerText" style="padding-left: 10px;">Employee Name</span>
      </div>
    </template>
    <template v-slot:iconTemplate2>
      <div>
        <span class="e-icons e-location e-font-icon" style="font-size: 15px;"></span>
        <span class="e-headerText" style="padding-left: 10px;">Employee Address</span>
      </div>
    </template>
    <template v-slot:iconTemplate3>
      <div>
        <span class="e-icons e-day" style="font-size: 15px;"></span>
        <span class="e-headerText" style="padding-left: 10px;">DOB</span>
      </div>
    </template>
  </ejs-treegrid>
</template>
<script>
import { TreeGridComponent, ColumnsDirective, ColumnDirective, Page } from "@syncfusion/ej2-vue-treegrid";
import {employeeData} from './data.js';

export default{
  name: 'App',
  components: {
    'ejs-treegrid': TreeGridComponent,
    'e-columns': ColumnsDirective,
    'e-column': ColumnDirective
  },
  data: () => {
    return {
      data: employeeData
    }
  },
  provide:{
    treegrid: [Page]
  }
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-treegrid/styles/material.css";
  #app{
    max-width: 80%;
  }
  .e-font-icon{
    vertical-align: middle;
  }
  .e-column-data{
    font-size: 9px;
    padding-top: 15px;
  }
</style>