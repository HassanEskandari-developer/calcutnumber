<template>
  <main
    class="w-full min-h-screen flex flex-col justify-center items-center bg-[#7dd3fc] gap-y-7"
  >
    <h2 class="text-[#134e4a] text-[25px] font-bold italic">
      Spill <br />
      Tittel
    </h2>
    <section
      class="w-[800px] h-[600px] flex justify-center items-center bg-white gap-x-4 rounded-[20px]"
    >
      <div class="w-1/2 flex flex-col gap-y-14 pl-10">
        <div class="num flex flex-col gap-y-3">
          <span class="text-[#134e4a] text-[20px] font-bold italic">Bill</span>
          <input type="number " placeholder="0" v-model="allMony" />
        </div>

        <div class="flex flex-col gap-y-5">
          <!-- ////////////////////// -->
          <span class="text-gray-400 text-[17px] font-bold italic"
            >Select Tip %</span
          >
          <div class="flex gap-x-5">
            <button
              class="w-24 h-12 bg-[#134e4a] text-white text-[20px] font-bold italic"
              @click="five(5)"
            >
              5%
            </button>
            <button
              class="w-24 h-12 bg-[#134e4a] text-white text-[20px] font-bold italic"
              @click="five(10)"
            >
              10%
            </button>
            <button
              class="w-24 h-12 bg-[#134e4a] text-white text-[20px] font-bold italic"
              @click="five(15)"
            >
              15%
            </button>
          </div>

          <!-- /////////////////////// -->
          <div class="flex gap-x-5">
            <button
              class="w-24 h-12 bg-[#134e4a] text-white text-[20px] font-bold italic"
              @click="five(25)"
            >
              25%
            </button>
            <button
              class="w-24 h-12 bg-[#134e4a] text-white text-[20px] font-bold italic"
              @click="five(50)"
            >
              50%
            </button>
            <input
              class="w-24 h-12 bg-white text-[#134e4a] text-[20px] font-bold italic"
              placeholder="COUSTOM"
              @change="costomButton"
              v-model="percent1"
              type="number"
            />
          </div>
        </div>
        <!-- ///////////////peple///////////////// -->
        <div class="flex flex-col gap-y-3">
          <span class="text-gray-400 text-[17px] font-bold italic"
            >Number Of People</span
          >
          <span class="border border-red-500 hidden">lorem2</span>
          <input type="number " placeholder="0" v-model="numberPeople" />
        </div>
      </div>

      <!-- //////////////////////////////result//////////////////////////////////////////////////// -->
      <div class="w-1/2 bg-[#134e4a] h-[400px] mr-4 rounded-[20px]">
        <div class="flex justify-between mt-5 p-6">
          <div>
            <h2 class="text-white text-[20px]">Tip Amount</h2>
            <span class="text-gray-400">/ person</span>
          </div>
          <span class="text-[#10b981] font-bold text-[35px]">${{calculatedTip}}</span>
        </div>
        <div class="flex justify-between p-6">
          <div>
            <h2 class="text-white text-[20px]">Total</h2>
            <span class="text-gray-400">/ person</span>
          </div>
          <span class="text-[#10b981] font-bold text-[35px]">${{calcuTotal}}</span>
        </div>
        <!-- /////////////////// -->
        <div class="flex justify-center items-center mt-14">
          <button
            class="font-bold w-[300px] rounded-[15px] h-12 bg-[#67e8f9] text-[25px] text-[#134e4a]"
            @click="resonButton"
          >
            reset
          </button>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      allMony: "",
      numberPeople: "",
      costomButton1: "",
      calculatedTip: '0.00',
      calcuTotal:'0.00',
      percent1:'',


    };
  },

  watch: {
    numberPeople: function (newVal) {
      if (this.numberPeople.length > 4) {
        // alert('adam bashhhhhhhhhh');
        this.numberPeople = newVal.slice(0, 4);
      }
    },
    percent1: function(percent){
            let btn = (+this.allMony * percent) / 100;
      let hesab1 = Math.floor(btn / this.numberPeople);
      this.calculatedTip=hesab1
      this.calcuTotal=hesab1*this.numberPeople
     
    }

  },

  methods: {
    five(percent) {
        this.percent1=percent
    //     let btn = (+this.allMony * percent) / 100;
    //   let hesab1 = Math.floor(btn / this.numberPeople);
    //   this.calculatedTip=hesab1
    //   this.calcuTotal=hesab1*this.numberPeople
     
    },

    resonButton() {
      this.numberPeople=''
      this.allMony=''
      this.calculatedTip='0.00'
      this.calcuTotal='0.00'
   
    },
  },
};
</script>

<style scoped>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}
</style>