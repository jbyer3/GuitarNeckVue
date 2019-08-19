<template>
<body>
  <h1>this is my guitar thing</h1>

  <div class="guitar">
    <div v-for="string in strings" :key="string.stringId" @click="check(strings)" class="string">
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
  <h2>{{outputNotes()}}</h2>
  <div class="chord-inputs">
    <select v-model="selected1">
      <option
        v-for="note in circleOfFifths"
        :value="note.value"
        :key="note.id"
        @click="hilite(finalChord)"
      >{{note.text}}</option>
    </select>
    <select v-model="selected2">
      <option
        v-for="chord in chordOptions"
        :value="chord.value"
        :key="chord.id"
        @click="hilite(finalChord)"
      >{{chord.text}}</option>
    </select>
  </div>
  <span>Selected notes: {{ finalChord }}</span>

  <button>log notes</button>
</body>
</template>

<script>
// eslint-disable-next-line
import {
  Array,
  Note,
  Interval,
  Distance,
  Dictionary,
  Chord,
  Scale
} from "tonal";

export default {
  name: "app",
  components: {
    // HelloWorld
  },
  data() {
    return {
      chord: new Set(),
      strings: [
        {
          stringName: "stringOne",
          stringId: 1,
          notes: [
            { name: "E", isRoot: 0, isHighlighted: 0, id: 11 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 12 },
            { name: "Gb", altName: "F#", isRoot: 0, isHighlighted: 0, id: 13 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 14 },
            { name: "Ab", altName: "G#", isRoot: 0, isHighlighted: 0, id: 15 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 16 },
            { name: "Bb", altName: "A#", isRoot: 0, isHighlighted: 0, id: 17 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 18 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 19 },
            { name: "Db", altName: "C#", isRoot: 0, isHighlighted: 0, id: 110 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 111 },
            { name: "Eb", altName: "D#", isRoot: 0, isHighlighted: 0, id: 112 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 113 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 114 },
            { name: "Gb", altName: "G#", isRoot: 0, isHighlighted: 0, id: 115 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 116 }
          ]
        },
        {
          stringName: "stringTwo",
          stringId: 2,
          notes: [
            { name: "B", isRoot: 0, isHighlighted: 0, id: 21 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 22 },
            { name: "Db", altName: "C#", isRoot: 0, isHighlighted: 0, id: 23 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 24 },
            { name: "Eb", altName: "D#", isRoot: 0, isHighlighted: 0, id: 25 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 26 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 27 },
            { name: "Gb", altName: "F#", isRoot: 0, isHighlighted: 0, id: 28 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 29 },
            { name: "Ab", altName: "G#", isRoot: 0, isHighlighted: 0, id: 210 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 211 },
            { name: "Bb", altName: "A#", isRoot: 0, isHighlighted: 0, id: 212 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 213 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 214 },
            { name: "Db", altName: "C#", isRoot: 0, isHighlighted: 0, id: 215 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 216 }
          ]
        },
        {
          stringName: "stringThree",
          stringId: 3,
          notes: [
            { name: "G", isRoot: 0, isHighlighted: 0, id: 31 },
            { name: "Ab", altName: "G#", isRoot: 0, isHighlighted: 0, id: 32 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 33 },
            { name: "Bb", altName: "A#", isRoot: 0, isHighlighted: 0, id: 34 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 35 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 36 },
            { name: "Db", altName: "C#",isRoot: 0, isHighlighted: 0, id: 37 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 38 },
            { name: "Eb", altName: "D#", isRoot: 0, isHighlighted: 0, id: 39 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 310 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 311 },
            { name: "Gb", altName: "F#", isRoot: 0, isHighlighted: 0, id: 312 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 313 },
            { name: "Ab", altName: "G#", isRoot: 0, isHighlighted: 0, id: 314 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 315 },
            { name: "Bb", altName: "A#", isRoot: 0, isHighlighted: 0, id: 316 }
          ]
        },
        {
          stringName: "stringFour",
          stringId: 4,
          notes: [
            { name: "D", isRoot: 0, isHighlighted: 0, id: 41 },
            { name: "Eb", altName: "D#", isRoot: 0, isHighlighted: 0, id: 42 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 43 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 44 },
            { name: "Gb", altName: "F#", isRoot: 0, isHighlighted: 0, id: 45 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 46 },
            { name: "Ab", altName: "G#", isRoot: 0, isHighlighted: 0, id: 47 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 48 },
            { name: "Bb", altName: "A#", isRoot: 0, isHighlighted: 0, id: 49 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 410 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 411 },
            { name: "Db", altName: "C#", isRoot: 0, isHighlighted: 0, id: 412 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 413 },
            { name: "Eb", altName: "D#", isRoot: 0, isHighlighted: 0, id: 414 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 415 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 416 }
          ]
        },
        {
          stringName: "stringFive",
          stringId: 5,
          notes: [
            { name: "A", isRoot: 0, isHighlighted: 0, id: 51 },
            { name: "Bb", altName: "A#", isRoot: 0, isHighlighted: 0, id: 52 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 53 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 54 },
            { name: "Db", altName: "C#", isRoot: 0, isHighlighted: 0, id: 55 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 56 },
            { name: "Eb", altName: "D#", isRoot: 0, isHighlighted: 0, id: 57 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 58 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 59 },
            { name: "Gb", altName: "F#", isRoot: 0, isHighlighted: 0, id: 510 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 511 },
            { name: "Ab", altName: "G#", isRoot: 0, isHighlighted: 0, id: 512 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 513 },
            { name: "Bb", altName: "A#", isRoot: 0, isHighlighted: 0, id: 514 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 515 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 516 }
          ]
        },
        {
          stringName: "stringSix",
          stringId: 6,
          notes: [
            { name: "E", isRoot: 0, isHighlighted: 0, id: 61 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 62 },
            { name: "Gb", altName: "F#", isRoot: 0, isHighlighted: 0, id: 63 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 64 },
            { name: "Ab", altName: "G#", isRoot: 0, isHighlighted: 0, id: 65 },
            { name: "A", isRoot: 0, isHighlighted: 0, id: 66 },
            { name: "Bb", altName: "A#", isRoot: 0, isHighlighted: 0, id: 67 },
            { name: "B", isRoot: 0, isHighlighted: 0, id: 68 },
            { name: "C", isRoot: 0, isHighlighted: 0, id: 69 },
            { name: "Db", altName: "C#", isRoot: 0, isHighlighted: 0, id: 610 },
            { name: "D", isRoot: 0, isHighlighted: 0, id: 611 },
            { name: "Eb", altName: "D#", isRoot: 0, isHighlighted: 0, id: 612 },
            { name: "E", isRoot: 0, isHighlighted: 0, id: 613 },
            { name: "F", isRoot: 0, isHighlighted: 0, id: 614 },
            { name: "Gb", altName: "F#", isRoot: 0, isHighlighted: 0, id: 615 },
            { name: "G", isRoot: 0, isHighlighted: 0, id: 616 }
          ]
        }
      ],
      selected1: "",
      selected2: "",
      circleOfFifths: [
        { text: "C", value: "C", id: 1 },
        { text: "G", value: "G", id: 2 },
        { text: "D", value: "D", id: 3 },
        { text: "A", value: "A", id: 4 },
        { text: "E", value: "E", id: 5 },
        { text: "B", value: "B", id: 6 },
        { text: "Gb/F#", value: "Gb", id: 7 },
        { text: "Db/C#", value: "Db", id: 8 },
        { text: "Ab/G#", value: "Ab", id: 9 },
        { text: "Eb/D#", value: "Eb", id: 10 },
        { text: "Bb/A#", value: "Bb", id: 11 },
        { text: "F", value: "F", id: 12 }
      ],
      chordOptions: [
        { text: "Maj", value: "", id: 1 },
        { text: "Min", value: "m", id: 2 },
        { text: "Maj7", value: "Maj7", id: 3 },
        { text: "Min7", value: "m7", id: 4 },
        { text: "7", value: "7", id: 5 }
      ]
    };
  },
  methods: {
    // hilite works with dropdown boxes 
    hilite: function(finalChord) {
      const notes = [...finalChord];
      this.strings.forEach(string => {
        string.notes.forEach(note => {
          if(notes.includes(note.name) || notes.includes(note.altName)) {
            note.isHighlighted = 1;
          } else {
            note.isHighlighted = 0;
          }
          if(notes[0] === note.name || notes[0] === note.altName) {
            note.isRoot = 1;
          } else {
            note.isRoot = 0;
          }
        })
      })
    },

    // check runs the highlight function on a loop over all strings to check for other notes, again, only on clicks
    check: function(strings) {
      strings.forEach(string => {
        string.notes.forEach(note => {
          if (this.chord.has(note.name)) {
            note.isHighlighted = true;
          } else {
            note.isHighlighted = false;
          }
        });
      });
      this.outputNotes();
    },
    // highlight only takes a click event from the strings
    highlight: function(note) {
      console.log(note.name);
      if (note.isHighlighted == 0 || undefined) {
        note.isHighlighted = true;
        this.chord.add(note.name);
      } else {
        note.isHighlighted = false;
        this.chord.delete(note.name);
      }
    },

    // silliness to put clicked chords on the screen
    outputNotes: function() {
      // console.log(this.chord)
      const currentChord = [...this.chord];
      // console.log(`current chord is ${currentChord}`)
      if (currentChord.length === 0) {
        return "empty!";
      } else if (currentChord.length === 1) {
        return `one note! ${currentChord[0]}`;
      } else if (currentChord.length === 2) {
        console.log(Distance.interval(currentChord[0], currentChord[1]));
        return `two notes! ${currentChord[0]} and ${currentChord[1]}`;
      } else if (currentChord.length >= 3) {
        return `Chord!!! `;
      }
    }
  },
  computed: {
    finalChord: function() {
      const chord = `${this.selected1}${this.selected2}`;
      console.log(`chord is ${Chord.notes(chord)}`);
      return chord ? Chord.notes(chord) : "";
    }
  }
};
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