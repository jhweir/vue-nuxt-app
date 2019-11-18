<template>
    <div id="container">
        {{ newBranch.title }}
        <!--<h1>Branch title: {{newBranch.title}}</h1>-->
        <!--<button @click="getBranch">Console log branch</button>-->
    </div>
</template>

<script>
import branchData from '~/data/branches.json'

export default {
    name: 'branch-a',
    data() {
        return {
            branches: branchData,
            newBranch: []
        }
    },
    created() {
        var branch = this.branches.filter(function (obj) { 
            return obj.id == 1; 
        });
        console.log(branch);
        this.newBranch = branch;
    },
    /*methods: {
        getBranch: function() {
            var branch = this.branches.filter(function (obj) { 
                return obj.id == 1; 
            });
            console.log(branch);
            this.newBranch = branch;
        }
    },*/
    head() {
        return {
            title: "Branch page",
            meta: [
                {
                hid: '...',
                name: '...',
                content: '...'
                }
            ]
        }
    }
}
</script>

<style>
#container{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>