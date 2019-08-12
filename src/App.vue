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
        {name: "E", isRoot: false, id: 61},
        {name: "F", isRoot: false, id: 62},
        {name: "Gb", isRoot: false, id: 63},  
        {name: "G", isRoot: false, id: 64},
        {name: "Ab", isRoot: false, id: 65},
        {name: "A", isRoot: false, id: 66},
        {name: "Bb", isRoot: false, id: 67},
        {name: "B", isRoot: false, id: 68},
        {name: "C", isRoot: false, id: 69},
        {name: "Db", isRoot: false, id: 610},
        {name: "D", isRoot: false, id: 611},
        {name: "Eb", isRoot: false, id: 612},
        {name: "E", isRoot: false, id: 613},
        {name: "F", isRoot: false, id: 614},
        {name: "Gb", isRoot: false, id: 615},
        {name: "G", isRoot: false, id: 616},
      ],
      stringFive : [
        {name: "A", isRoot: false, id: 51},
        {name: "Bb", isRoot: false, id: 52},
        {name: "B", isRoot: false, id: 53},  
        {name: "C", isRoot: false, id: 54},
        {name: "Db", isRoot: false, id: 55},
        {name: "D", isRoot: false, id: 56},
        {name: "Eb", isRoot: false, id: 57},
        {name: "E", isRoot: false, id: 58},
        {name: "F", isRoot: false, id: 59},
        {name: "Gb", isRoot: false, id: 510},
        {name: "G", isRoot: false, id: 511},
        {name: "Ab", isRoot: false, id: 512},
        {name: "A", isRoot: false, id: 513},
        {name: "Bb", isRoot: false, id: 514},
        {name: "B", isRoot: false, id: 515},
        {name: "C", isRoot: false, id: 516},
      ],
      stringFour : [
        {name: "D", isRoot: false, id: 41},
        {name: "Eb", isRoot: false, id: 42},
        {name: "E", isRoot: false, id: 43},  
        {name: "F", isRoot: false, id: 44},
        {name: "Gb", isRoot: false, id: 45},
        {name: "G", isRoot: false, id: 46},
        {name: "Ab", isRoot: false, id: 47},
        {name: "A", isRoot: false, id: 48},
        {name: "Bb", isRoot: false, id: 49},
        {name: "B", isRoot: false, id: 410},
        {name: "C", isRoot: false, id: 411},
        {name: "Db", isRoot: false, id: 412},
        {name: "D", isRoot: false, id: 413},
        {name: "Eb", isRoot: false, id: 414},
        {name: "E", isRoot: false, id: 415},
        {name: "F", isRoot: false, id: 416},
      ],
      stringThree : [
        {name: "G", isRoot: false, id: 31},
        {name: "Ab", isRoot: false, id: 32},
        {name: "A", isRoot: false, id: 33},  
        {name: "Bb", isRoot: false, id: 34},
        {name: "B", isRoot: false, id: 35},
        {name: "C", isRoot: false, id: 36},
        {name: "Db", isRoot: false, id: 37},
        {name: "D", isRoot: false, id: 38},
        {name: "Eb", isRoot: false, id: 39},
        {name: "E", isRoot: false, id: 310},
        {name: "F", isRoot: false, id: 311},
        {name: "Gb", isRoot: false, id: 312},
        {name: "G", isRoot: false, id: 313},
        {name: "Ab", isRoot: false, id: 314},
        {name: "A", isRoot: false, id: 315},
        {name: "Bb", isRoot: false, id: 316},
      ],
      stringTwo : [
        {name: "B", isRoot: false, id: 21},
        {name: "C", isRoot: false, id: 22},
        {name: "Db", isRoot: false, id: 23},  
        {name: "D", isRoot: false, id: 24},
        {name: "Eb", isRoot: false, id: 25},
        {name: "E", isRoot: false, id: 26},
        {name: "F", isRoot: false, id: 27},
        {name: "Gb", isRoot: false, id: 28},
        {name: "G", isRoot: false, id: 29},
        {name: "Ab", isRoot: false, id: 210},
        {name: "A", isRoot: false, id: 211},
        {name: "Bb", isRoot: false, id: 212},
        {name: "B", isRoot: false, id: 213},
        {name: "C", isRoot: false, id: 214},
        {name: "Db", isRoot: false, id: 215},
        {name: "D", isRoot: false, id: 216},
      ],
      stringOne : [
        {name: "E", isRoot: false, id: 11},
        {name: "F", isRoot: false, id: 12},
        {name: "Gb", isRoot: false, id: 13},  
        {name: "G", isRoot: false, id: 14},
        {name: "Ab", isRoot: false, id: 15},
        {name: "A", isRoot: false, id: 16},
        {name: "Bb", isRoot: false, id: 17},
        {name: "B", isRoot: false, id: 18},
        {name: "C", isRoot: false, id: 19},
        {name: "Db", isRoot: false, id: 110},
        {name: "D", isRoot: false, id: 111},
        {name: "Eb", isRoot: false, id: 112},
        {name: "E", isRoot: false, id: 113},
        {name: "F", isRoot: false, id: 114},
        {name: "Gb", isRoot: false, id: 115},
        {name: "G", isRoot: false, id: 116},
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