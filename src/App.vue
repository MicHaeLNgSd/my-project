<script>
import axios from 'axios';
 
 export default {
    data() {
        return {
            students: [],
            newmark: '',
            newgroup: '',
            newisDonePr: '',
            newname: '',
            piece: '',
            search: '',
            name:'',
            group:'',
            isDonePr:'',
            
            student: { "name": "", isDonePr: false, group: "RPZ 19 1/9" },
            editedStudent: { "name": "", isDonePr: false, group: "" },

            convertorData: [],

            editingId:'',
        }
    },
    mounted: function () {
        axios.get("http://34.82.81.113:3000/students").then((res) => {
            console.log(res.data);
            this.students = res.data;
        });
    },
    }
</script>

<template>
    <table class="text-left table-auto shadow-md rounded-lg">
        <tr v-for="item in students"  v-bind:key="item._id" :class="search != '' ? (item.name.includes(search) ? 'selected' : 'unselected') : 'unselected2'"> 
            <td>
                <p >{{item.name}}</p>
            </td>
            <td>
                <input  type="checkbox" v-model="item.isDonePr">
            </td>
            <td>
                <p>{{item.group}}</p>
            </td>
        </tr>
    </table>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
