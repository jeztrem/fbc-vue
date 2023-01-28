<script setup lang="ts">
import { ref } from 'vue'
import Modal from '../components/Modal.vue'
import beliefJson from "../assets/beliefs.json";

const showModal = ref(false);
const verseText = ref<string>();
const verseRef = ref<string>();

class Verse {
  Reference: string;
  Text: string;

  constructor(reference: string, text: string) {
    this.Reference = reference;
    this.Text = text;
  }
}

class Section {

  Text: string;
  Verses: Verse[];

  constructor() {
    this.Verses = new Array<Verse>();
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
  <div class="container-fluid" id="home">
    <div class="fs-2 text-center pt-3">FBC BELIEFS</div>
  </div>
  <div class="container-fluid">
    <div v-for="belief in beliefJson">
      <div class="fs-4 mx-3">{{ belief.Topic }}</div>
      <div class="container-fluid mb-4">
        <div v-for="section in belief.Section">
          <p class="mx-5 px-2 pt-3">{{ section.Text }}</p>
          <div class="container-xxl">
            <div class="verse-grid mx-5">
              <div v-for="verse in section.Verses">
                <button class="btn btn-outline-secondary text-center fs-6  " style="width: 100%;"
                  @click="showModal = true, verseRef = verse.Reference, verseText = verse.Text">
                  {{ verse.Reference }}
                </button>
              </div>
            </div>
          </div>
        </div>
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

<style>
@media (max-width: 575.98px) {
  .verse-grid {
    display: grid;
    row-gap: 0.25rem;
    column-gap: 0.25rem;
    grid-template-columns: 1fr;
  }
}

@media (min-width: 576px) and (max-width: 767.98px) {
  .verse-grid {
    display: grid;
    row-gap: 0.25rem;
    column-gap: 0.25rem;
    grid-template-columns: 1fr 1fr;
  }
}

@media (min-width: 768px) and (max-width: 991.98px) {
  .verse-grid {
    display: grid;
    row-gap: 0.25rem;
    column-gap: 0.25rem;
    grid-template-columns: 1fr 1fr 1fr;
  }
}

@media (min-width: 992px) {
  .verse-grid {
    display: grid;
    row-gap: 0.25rem;
    column-gap: 0.25rem;
    grid-template-columns: 1fr 1fr 1fr 1fr;
  }
}
</style>