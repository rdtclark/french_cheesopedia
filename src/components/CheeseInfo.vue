<template>


<div v-if="cheese" class="cheese-info-container">
    
<button class="btn" @click="modalAction()">More Info</button>

    <div v-if="modal" class="modal">
        <div class="container">
            <h3>{{ cheese.fields.cheese }}</h3>
            <p>{{ cheese.fields.id }}</p>
            <p>{{ cheese.fields.milk }}</p>         
          <button @click="modalAction()" class="close-button" id="close-button">Close</button>
        </div>
    </div>

</div>

</template>

<script>
export default {
    name: "cheese-info",
    props: ["cheese"],
    data(){
        return {
            modal: false
        }
    },
    methods: {
        modalAction() {
            if (this.modal == false) {
                this.modal = true
            } else {
                this.modal = false
            }
        }
    }
}
</script>

<style>

.modal {
  display: block;
  width: 800px;
  max-width: 100%;
  height: 400px;
  max-height: 100%;
  position: fixed;
  z-index: 100;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  
  /* If known, negative margins are probably better (less chance of blurry text). */
  /* margin: -200px 0 0 -200px; */
  
  background: white;
  box-shadow: 0 0 60px 10px rgba(0, 0, 0, 0.9);
  border-radius: 25px;
  border: 2px solid #73AD21;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 50; 
  background: rgba(0, 0, 0, 0.6);
}

.modal .close-button {
  position: absolute;
  z-index: 1;
  
  top: 10px;
  
  /* needs to look OK with or without scrollbar */
  right: 20px;
  
  border: 0;
  background: black;
  color: white;
  padding: 5px 10px;
  font-size: 1.3rem;
}

</style>