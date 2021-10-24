<template>
<div id='rpgGame' class='game-maker'>
  <div id='display' class='container pt-5'>
      <h3 class='text-white font-weight-bold'>Display Area</h3>
      <div class="card mb-3 rounded-3" style='background: #313031;'>
          <div class="row g-0 px-2">
              <div class="col-md-3 d-flex justify-content-center align-items-center">
                  <div class='col-12 border border-white border-5 rounded-3 img-fit'>
                      <img v-bind:src="getUrl" class="img-fluid rounded-start" alt="...">
                      
                  </div> 
                  
              </div>
              <div class="col-md-9 text-white">
                  <div class="card-body px-2">
                      <div class="border border-white border-4 rounded-3 px-3 py-1">
                          <h5 class="card-title">Name : {{ name }}</h5>
                          <h5 class="card-title">Class : {{ selectedClass }}</h5>
                          <h5 class="card-title">Gender : {{ gender }}</h5>
                          <h5 class="card-title m-0">Traits : {{ trait }}</h5>
                      </div>
                      
                      <div class='mt-2 border border-white border-4 rounded-3 px-3 py-1'>
                          <h5 class="card-title">Strength : {{ getStrength }}</h5>
                          <h5 class="card-title">Agility : {{ getAgility }}</h5>
                          <h5 class="card-title">Resilience : {{ resilience }}</h5>
                          <h5 class="card-title">Wisdom : {{ wisdom }}</h5>
                          <h5 class="card-title m-0">Luck : {{ getLuck }}</h5>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>

    <div id='input' class='container py-5'>
        <h3 class='text-white font-weight-bold'>Input Area</h3>

        <div class="mb-3 row">
            <label for="inputName" class="col-sm-1 col-form-label text-white">Name</label>
            <div class="col-sm-3">
                <input type="text" class="form-control" id="inputName" v-model="name">
            </div>
        </div>

        <div class="mb-3 row">
            <label for="inputName" class="col-sm-1 col-form-label text-white">Gender</label>
            <div class="col-sm-3 mt-2">
                <div class="form-check form-check-inline">
                    <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" value="Male" v-model="gender">
                    <label class="form-check-label text-white" for="inlineRadio1">Male</label>
                </div>
                <div class="form-check form-check-inline">
                    <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" value="Female" v-model="gender">
                    <label class="form-check-label text-white" for="inlineRadio2">Female</label>
                </div>
            </div>
        </div>

        <div class="mb-3 row">
            <label for="inputName" class="col-sm-1 col-form-label text-white">Class</label>
            <div class="col-sm-3">
                <select class="form-select" aria-label="Default select example" v-model="selectedClass">
                    <option>Hero</option>
                    <option>Warrior</option>
                    <option>Mage</option>
                </select>
            </div>
        </div>

        <div class="mb-3 row">
            <label for="inputName" class="col-sm-1 col-form-label text-white">Traits</label>
            <div class="col-sm-3">
                <select class="form-select" aria-label="Default select example" v-model="trait">
                    <option>Everyman</option>
                    <option>Bat out of hell</option>
                    <option>Brave</option>
                    <option>Lucky devil</option>
                    <option>Tomboy</option>
                </select>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
  name: 'display',
  data(){
    return {
      urls:{
        Male:{
          Hero: "https://recursionist.io/img/dashboard/lessons/quickstart/male-hero.png",
          Warrior: "https://recursionist.io/img/dashboard/lessons/quickstart/male-warrior.png",
          Mage: "https://recursionist.io/img/dashboard/lessons/quickstart/male-mage.png",
        },
        Female:{
          Hero: "https://recursionist.io/img/dashboard/lessons/quickstart/female-hero.png",
          Warrior: "https://recursionist.io/img/dashboard/lessons/quickstart/female-warrior.png",
          Mage: "https://recursionist.io/img/dashboard/lessons/quickstart/female-mage.png"
        }
      },
      name: '',
      gender: 'Male',
      selectedClass: 'Mage',
      trait: 'Everyman',
      strength: 10,
      agility: 10,
      resilience: 10,
      wisdom: 10,
      luck: 10
    }
  },
  computed: {
    getUrl(){
      return this.urls[this.gender][this.selectedClass]
    },
    
    getStrength(){
      if(this.selectedClass === "Hero" && this.trait === "Brave") return this.strength * 1.1
      else if(this.gender === "Female" && this.trait === "Tomboy") return this.strength * 1.1
      else return 10
    },

    getAgility(){
      if(this.trait === "Bat out of hell") return this.agility * 1.4
      else if(this.selectedClass === "Hero" && this.trait === "Brave") return this.agility * 1.1
      else if(this.gender === "Female" && this.trait === "Tomboy") return this.strength * 1.1
      else return 10
    },

    getLuck(){
      if(this.gender === "Male" && this.trait === "Lucky devil") return this.luck * 1.5
      else if(this.selectedClass === "Hero" && this.trait === "Brave") return this.luck * 1.2
      else return 10
    }

  }
}
</script>

<style>
@import "../css/styles.css";
</style>