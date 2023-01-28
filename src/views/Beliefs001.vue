<script setup lang="ts">
import { ref } from 'vue'
import Modal from '../components/Modal.vue'
import beliefJson from "../assets/verses.json";

const showModal = ref(false);
const verseText = ref("original");
const verseRef = ref("original");

class Verse {
  Reference: string;
  Text: string;

  constructor(reference: string, text: string) {
    this.Reference = reference;
    this.Text = text;
  }
}

class VerseGroup {
  Verses: Verse[];

  constructor() {
    this.Verses = [];
  }
}

class Section {

  Text: string;
  VerseGroup: VerseGroup;

  constructor() {
    this.VerseGroup = new VerseGroup();
    this.Text = "";
  }
}

class Belief {

  Topic: string;
  Sections: Section[];

  constructor() {
    this.Sections = new Array<Section>();
    this.Topic = "";
  }
}


</script>

<template>
  <div class="w3-content w3-container">
    <div class="row" v-for="verse in beliefJson">
      <div class="col-sm-6 my-1">
        <button class="btn btn-outline-secondary col-12"
          @click="verseRef = verse.Reference, showModal = true, verseText = verse.Text">
          {{ verse.Reference }}
        </button>
      </div>
    </div>
  </div>

  <Teleport to="body">
    <modal :show="showModal" @close="showModal = false;">
      <template #header>
        <h4>{{ verseRef }}</h4>
      </template>
      <template #body>
        <h5>{{ verseText }}</h5>
      </template>
    </modal>
  </Teleport>
</template>

<!-- <style>
@media (min-width: 1024px) {
  .fbc {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style> -->