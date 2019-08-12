<template>
<body>
  <h1>this is my guitar thing</h1>

  <div class="guitar">
    <div 
      v-for="string in strings" 
      :key="string.stringId"
      @click="check(strings)"
      class="string">
      <div
        v-for="note in string.notes"
        :key="note.id"
        @click="highlight(note)"
        :class="{selected: note.isHighlighted}"
        class="fret"
      >{{note.name}}</div> 
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
  name: "app",
  components: {
    // HelloWorld
  },
  data() {
    return {
      chord: new Set,
      strings: [
        {
          stringName: "stringSix",
          stringId: 6,
          notes: [
            { name: "E", isRoot: 0, isHighlighted: 0, id: 61 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 62 },
            { name: "Gb", isRoot: 0, isHighlighted: 0, id: 63 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 64 },
            { name: "Ab", isRoot: 0, isHighlighted: 0, id: 65 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 66 },
            { name: "Bb", isRoot: 0, isHighlighted: 0, id: 67 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 68 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 69 },
            { name: "Db", isRoot: 0, isHighlighted: 0, id: 610 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 611 },
            { name: "Eb", isRoot: 0, isHighlighted: 0, id: 612 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 613 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 614 },
            { name: "Gb", isRoot: 0, isHighlighted: 0, id: 615 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 616 }
          ]
        },
        {
          stringName: "stringFive",
          stringId: 5,
          notes: [
            { name: "A", isRoot: 0, isHighlighted: 0, id: 51 },
            { name: "Bb", isRoot: 0, isHighlighted: 0, id: 52 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 53 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 54 },
            { name: "Db", isRoot: 0, isHighlighted: 0, id: 55 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 56 },
            { name: "Eb", isRoot: 0, isHighlighted: 0, id: 57 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 58 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 59 },
            { name: "Gb", isRoot: 0, isHighlighted: 0, id: 510 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 511 },
            { name: "Ab", isRoot: 0, isHighlighted: 0, id: 512 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 513 },
            { name: "Bb", isRoot: 0, isHighlighted: 0, id: 514 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 515 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 516 }
          ]
        },
        {
          stringName: "stringFour",
          stringId: 4,
          notes: [
            { name: "D", isRoot: 0, isHighlighted: 0, id: 41 },
            { name: "Eb", isRoot: 0, isHighlighted: 0, id: 42 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 43 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 44 },
            { name: "Gb", isRoot: 0, isHighlighted: 0, id: 45 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 46 },
            { name: "Ab", isRoot: 0, isHighlighted: 0, id: 47 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 48 },
            { name: "Bb", isRoot: 0, isHighlighted: 0, id: 49 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 410 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 411 },
            { name: "Db", isRoot: 0, isHighlighted: 0, id: 412 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 413 },
            { name: "Eb", isRoot: 0, isHighlighted: 0, id: 414 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 415 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 416 }
          ]
        },
        {
          stringName: "stringThree",
          stringId: 3,
          notes: [
            { name: "G", isRoot: 0, isHighlighted: 0, id: 31 },
            { name: "Ab", isRoot: 0, isHighlighted: 0, id: 32 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 33 },
            { name: "Bb", isRoot: 0, isHighlighted: 0, id: 34 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 35 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 36 },
            { name: "Db", isRoot: 0, isHighlighted: 0, id: 37 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 38 },
            { name: "Eb", isRoot: 0, isHighlighted: 0, id: 39 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 310 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 311 },
            { name: "Gb", isRoot: 0, isHighlighted: 0, id: 312 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 313 },
            { name: "Ab", isRoot: 0, isHighlighted: 0, id: 314 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 315 },
            { name: "Bb", isRoot: 0, isHighlighted: 0, id: 316 }
          ]
        },
        {
          stringName: "stringTwo",
          stringId: 2,
          notes: [
            { name: "B", isRoot: 0, isHighlighted: 0, id: 21 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 22 },
            { name: "Db", isRoot: 0, isHighlighted: 0, id: 23 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 24 },
            { name: "Eb", isRoot: 0, isHighlighted: 0, id: 25 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 26 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 27 },
            { name: "Gb", isRoot: 0, isHighlighted: 0, id: 28 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 29 },
            { name: "Ab", isRoot: 0, isHighlighted: 0, id: 210 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 211 },
            { name: "Bb", isRoot: 0, isHighlighted: 0, id: 212 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 213 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 214 },
            { name: "Db", isRoot: 0, isHighlighted: 0, id: 215 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 216 }
          ]
        },
        {
          stringName: "stringOne",
          stringId: 1,
          notes: [
            { name: "E", isRoot: 0, isHighlighted: 0, id: 11 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 12 },
            { name: "Gb", isRoot: 0, isHighlighted: 0, id: 13 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 14 },
            { name: "Ab", isRoot: 0, isHighlighted: 0, id: 15 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 16 },
            { name: "Bb", isRoot: 0, isHighlighted: 0, id: 17 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 18 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 19 },
            { name: "Db", isRoot: 0, isHighlighted: 0, id: 110 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 111 },
            { name: "Eb", isRoot: 0, isHighlighted: 0, id: 112 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 113 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 114 },
            { name: "Gb", isRoot: 0, isHighlighted: 0, id: 115 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 116 }
          ]
        }
      ],
    };
  },
  methods: {
    check: function(strings){
      strings.forEach(string => {
        string.notes.forEach(note => {
            if(this.chord.has(note.name)){
              note.isHighlighted = true;
            } else {
              note.isHighlighted = false;
            }
          })
      })
    },
    highlight: function(note) {
      // chord = new Set;
      console.log(note)
      if (note.isHighlighted == 0 || undefined) {
        note.isHighlighted = true;
        this.chord.add(note.name);
      } else {
        note.isHighlighted = false;
        this.chord.delete(note.name);
      }
      console.log(this.chord)
    }
  },
  computed: {}
};

// const frets = document.getElementsByClassName('fret');
// const fretArray = Array.from(frets);
// const selectedNotes = new Set;

// fretArray.forEach(fret => {
//   fret.addEventListener('click', highlight);
// });

// function highlight() {
//   fretArray.forEach(fret => {
//     if(fret.dataset.notevalue === this.dataset.notevalue){
//       if(!fret.classList.contains('selected')){
//         fret.classList.add('selected');
//         selectedNotes.add(this.dataset.notevalue);
//       } else {
//         fret.classList.remove('selected');
//         selectedNotes.delete(this.dataset.notevalue);
//       }
//     }
//   });
// }

// console.log(frets)
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
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
}

h1 {
  display: inline-block;
}

.fret {
  border: 1px solid black;
  display: flex;
  flex: 1;
  align-items: center;
  justify-content: center;
  background: rgb(214, 242, 131);
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