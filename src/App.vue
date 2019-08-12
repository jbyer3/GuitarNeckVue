<template>
  <body>
    <h1>this is my guitar thing</h1>

    <div class="guitar">
      <div class="string firstString">
        <div v-for="note in stringSix" v-bind:key="note.id" class="fret">{{note.name}}</div>
      </div>
      <div class="string secondString">
        <div v-for="note in stringFive" v-bind:key="note.id" class="fret">{{note.name}}</div>
      </div>
      <div class="string thirdString">
        <div v-for="note in stringFour" v-bind:key="note.id" class="fret">{{note.name}}</div>
      </div>
      <div class="string fourthString">
        <div v-for="note in stringThree" v-bind:key="note.id" class="fret">{{note.name}}</div>
      </div>
      <div class="string fifthString">
        <div v-for="note in stringTwo" v-bind:key="note.id" class="fret">{{note.name}}</div>
      </div>
      <div class="string sixthString">
        <div v-for="note in stringOne" v-bind:key="note.id" class="fret">{{note.name}}</div>
      </div>
      <div class="string fretCount">
        <div class="fretCounter"></div>
        <div class="fretCounter">1</div>
        <div class="fretCounter">2</div>
        <div class="fretCounter">3</div>
        <div class="fretCounter">4</div>
        <div class="fretCounter">5</div>
        <div class="fretCounter">6</div>
        <div class="fretCounter">7</div>
        <div class="fretCounter">8</div>
        <div class="fretCounter">9</div>
        <div class="fretCounter">10</div>
        <div class="fretCounter">11</div>
        <div class="fretCounter">12</div>
        <div class="fretCounter">13</div>
        <div class="fretCounter">14</div>
        <div class="fretCounter">15</div>
      </div>
    </div>
  </body>
</template>

<script>

export default {
  name: 'app',
  components: {
    // HelloWorld
  },
  data () {
    return {
      stringSix : [
        {name: "E", id: 61},
        {name: "F", id: 62},
        {name: "Gb", id: 63},  
        {name: "G", id: 64},
        {name: "Ab", id: 65},
        {name: "A", id: 66},
        {name: "Bb", id: 67},
        {name: "B", id: 68},
        {name: "C", id: 69},
        {name: "Db", id: 610},
        {name: "D", id: 611},
        {name: "Eb", id: 612},
        {name: "E", id: 613},
        {name: "F", id: 614},
        {name: "Gb", id: 615},
        {name: "G", id: 616},
      ],
      stringFive : [
        {name: "A", id: 51},
        {name: "Bb", id: 52},
        {name: "B", id: 53},  
        {name: "C", id: 54},
        {name: "Db", id: 55},
        {name: "D", id: 56},
        {name: "Eb", id: 57},
        {name: "E", id: 58},
        {name: "F", id: 59},
        {name: "Gb", id: 510},
        {name: "G", id: 511},
        {name: "Ab", id: 512},
        {name: "A", id: 513},
        {name: "Bb", id: 514},
        {name: "B", id: 515},
        {name: "C", id: 516},
      ],
      stringFour : [
        {name: "D", id: 41},
        {name: "Eb", id: 42},
        {name: "E", id: 43},  
        {name: "F", id: 44},
        {name: "Gb", id: 45},
        {name: "G", id: 46},
        {name: "Ab", id: 47},
        {name: "A", id: 48},
        {name: "Bb", id: 49},
        {name: "B", id: 410},
        {name: "C", id: 411},
        {name: "Db", id: 412},
        {name: "D", id: 413},
        {name: "Eb", id: 414},
        {name: "E", id: 415},
        {name: "F", id: 416},
      ],
      stringThree : [
        {name: "G", id: 31},
        {name: "Ab", id: 32},
        {name: "A", id: 33},  
        {name: "Bb", id: 34},
        {name: "B", id: 35},
        {name: "C", id: 36},
        {name: "Db", id: 37},
        {name: "D", id: 38},
        {name: "Eb", id: 39},
        {name: "E", id: 310},
        {name: "F", id: 311},
        {name: "Gb", id: 312},
        {name: "G", id: 313},
        {name: "Ab", id: 314},
        {name: "A", id: 315},
        {name: "Bb", id: 316},
      ],
      stringTwo : [
        {name: "B", id: 21},
        {name: "C", id: 22},
        {name: "Db", id: 23},  
        {name: "D", id: 24},
        {name: "Eb", id: 25},
        {name: "E", id: 26},
        {name: "F", id: 27},
        {name: "Gb", id: 28},
        {name: "G", id: 29},
        {name: "Ab", id: 210},
        {name: "A", id: 211},
        {name: "Bb", id: 212},
        {name: "B", id: 213},
        {name: "C", id: 214},
        {name: "Db", id: 215},
        {name: "D", id: 216},
      ],
      stringOne : [
        {name: "E", id: 11},
        {name: "F", id: 12},
        {name: "Gb", id: 13},  
        {name: "G", id: 14},
        {name: "Ab", id: 15},
        {name: "A", id: 16},
        {name: "Bb", id: 17},
        {name: "B", id: 18},
        {name: "C", id: 19},
        {name: "Db", id: 110},
        {name: "D", id: 111},
        {name: "Eb", id: 112},
        {name: "E", id: 113},
        {name: "F", id: 114},
        {name: "Gb", id: 115},
        {name: "G", id: 116},
      ],
    }
  },
  methods: {

  },
  computed: {

  }
}

const frets = document.getElementsByClassName('fret');
const fretArray = Array.from(frets);
const selectedNotes = new Set;

fretArray.forEach(fret => {
  fret.addEventListener('click', highlight);
});

function highlight() {
  fretArray.forEach(fret => {
    if(fret.dataset.notevalue === this.dataset.notevalue){
      if(!fret.classList.contains('selected')){
        fret.classList.add('selected');
        selectedNotes.add(this.dataset.notevalue);
      } else {
        fret.classList.remove('selected');
        selectedNotes.delete(this.dataset.notevalue);
      }
    }
  });
}

console.log(frets)
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  background: #e5e4d4;
  font-size: 24px;
  line-height: 1.4;
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
};

h1 {
  display: inline-block;
}

.fret {
  border: 1px solid black;
  display: flex;
  flex: 1;
  align-items: center;
  justify-content: center;
  background:rgb(214, 242, 131);
  width: 30px;
}

.guitar {
  display: flex;
  flex-direction: column;
  width: 90vw;
  min-height: 30vh;
  /* min-width: 800px; */
}

.string {
  display: flex;
  height: 20%;
}

.fret:first-of-type {
  border-right: 2px solid red;
  border-top: none;
  border-left: none;
  border-bottom: none;
  /* background: inherit; */
}

.fretCount .fretCounter {
  background: inherit;
  border: none;
  display: flex;
  flex: 1;
  align-items: center;
  justify-content: center;
}

.selected {
  background: red;
}
</style>