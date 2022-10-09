<script setup lang="ts">
import { Ref, ref } from "vue";

const props = defineProps({
  id: Number,
  nome: String,
  idade: Number,
});

const expanded: Ref<boolean> = ref(false);

const deleteItem = (event: Event) => {
  event.stopPropagation();
  console.log("Delete");
};

const saveItem = (event: Event) => {
  event.stopPropagation();
  console.log("save");
};
</script>

<template>
  <q-separator></q-separator>
  <q-expansion-item v-model="expanded" group="linha">
    <template v-slot:header>
      <q-item-section>
        <div class="row">
          <div class="col-1">
            <q-icon
              name="expand_more"
              size="24px"
              @click="expanded = false"
              v-if="!expanded"
            />
            <q-icon
              name="expand_less"
              size="24px"
              @click="expanded = true"
              v-if="expanded"
            />
          </div>
          <div class="col-1">{{ props.id }}</div>
          <div class="col">{{ props.nome }}</div>
          <div class="col-1">{{ props.idade }}</div>
        </div>
      </q-item-section>

      <q-item-section side>
        <div class="row items-center">
          <q-btn
            flat
            round
            icon="delete"
            size="sm"
            @click="deleteItem($event)"
          />
          <q-btn flat round icon="save" size="sm" @click="saveItem($event)" />
        </div>
      </q-item-section>
    </template>

    <q-separator></q-separator>

    <q-card bordered class="q-ma-sm">
      <q-card-section>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quidem, eius
        reprehenderit eos corrupti commodi magni quaerat ex numquam, dolorum
        officiis modi facere maiores architecto suscipit iste eveniet doloribus
        ullam aliquid.
      </q-card-section>
    </q-card>
  </q-expansion-item>
</template>

<style scoped lang="scss"></style>
