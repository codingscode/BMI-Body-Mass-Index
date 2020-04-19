<template>
     <div class="frame">
          <h1>Body Mass Index (BMI)</h1>
          <p>mass (pounds): </p>
          <input type="number" v-model="mass">
          <p>height (in): </p>
          <input type="number" v-model="height">
          <button  @click="visible">calculate</button>
          <div v-if="show">
               <div class="answer">{{bmi()}}</div>  <!-- v-once   -->
               <div class="conclusion">{{conclusion()}}</div>
               <button @click="doitagain">do it again</button>
          </div>
     </div>
</template>

<script>


export default {
     data() {
         return {
             mass: null,
             height: null,
             show: false,
             clica: 0,
             copia: null
         }
     },
     methods: {
         bmi(answer, m, h) {
           m = this.mass
           h = this.height
           answer = ((m*703)/(h**2)).toFixed(2)
           return answer 
         },
         visible() {
             this.show = true
         },
         conclusion() {
             if (this.bmi() > 25) {
                 return `You need to lose ${(this.mass - (25/703)*(this.height)**2).toFixed(2)} pounds`
             }
             else {
                 //return this.bmi()
                 return `You are in shape`
             }
             
         },
         doitagain() {
             this.show = false
             this.height = null
             this.mass = null
             if (this.bmi != this.bmi) {
                 this.bmi == null
             }
         }
     },
     computed: {
        //
     }
}

</script>
    
<style>
    .frame {
        width: 600px;
        height: 500px;
        background-color: rgb(255, 206, 116);
        margin: 15px;
        padding: 20px;
        border: solid 2px darkgreen;
        border-radius: 25px;
        display: flex;
        flex-direction: column;
        justify-content:inherit;
    }

    input {
        width: 150px;
        border-radius: 7px;
        border: solid 2px olive;

        padding-left: 8px;
        align-content: center;
    }

    p {
        color: white;
        font-weight:bolder;
        font-size: larger;
        font-family: Georgia, 'Times New Roman', Times, serif;
    }

    button {
        margin: 10px;
        width: 100px;
        height: 30px;
        background-color: rgba(37, 34, 197, 0.801);
        color: white;
        border: 1px solid rgb(177, 160, 160);
        border-radius: 15px;
        outline: none;
        
    }
     
    button:hover {
        background-color: rgba(106, 104, 236, 1); 
        color: white;
        border: 1px solid rgb(140, 119, 236);
    }

   
    .answer, .conclusion {
        background-color: white;
        width: 150px;
        height: 33px;
        align-content: center;
        border-radius: 12px;
        margin-top: 4px;

        align-content: center;
        justify-content: center;
        align-items: center;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;

        border: solid 2px rgb(27, 133, 27);
    }

    .conclusion {
        width: 300px;
    }    
</style>