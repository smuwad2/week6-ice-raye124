<script>
    export default { 
        data() {
            return {
                // Add code here
                id: "demo1",
                blueBoth: true
            }
        },
        methods: { 
   			// Add code here
            changeColor() {
                this.blueBoth = !this.blueBoth
            }
		}
    }
</script>

<template>
    
    <!-- Modify code here -->
    <div class="container">
        <!-- Use v-bind:class="{'className' : isActive}"-->
        <div v-bind:id="id" class="m-2" v-bind:class="{'blueBox' : blueBoth, 'redBox' : !blueBoth}">
            div ID : {{id}} 
        </div>
        <button type="button" @click="changeColor()" v-bind:class="{'btn btn-primary' : blueBoth, 'btn btn-danger': !blueBoth}">Change Color</button>
    </div>

</template>

<style scoped>
    .redBox {
        background-color: red;
    }
    .blueBox {
        background-color: blue;
    }
    #demo1 {
        color: white;
    }
</style>
