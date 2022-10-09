<script setup lang="ts">
import { Linha } from "@/views/components";
import { onMounted, Ref, ref } from "vue";

const expanded: Ref<boolean> = ref(false);

const linhas = [
  {
    id: 1,
    nome: "Nome 01",
    idade: 1,
  },
  {
    id: 2,
    nome: "Nome 02",
    idade: 2,
  },
  {
    id: 3,
    nome: "Nome 03",
    idade: 3,
  },
  {
    id: 4,
    nome: "Nome 04",
    idade: 4,
  },
  {
    id: 5,
    nome: "Nome 05",
    idade: 5,
  },
];

onMounted(() => {
  const teste: NodeListOf<HTMLElement> = document.querySelectorAll<HTMLElement>(
    "[class='q-item__section column q-item__section--side justify-center q-focusable relative-position cursor-pointer']"
  );

  teste.forEach((item) => {
    item.style.display = "none";
  });
});
</script>

<template>
  <q-list bordered class="q-ma-md">
    <q-item>
      <q-item-section>
        <div class="row">
          <div class="col-1">
            <q-toggle v-model="expanded" />
          </div>
          <div class="col-1">Id</div>
          <div class="col">Nome</div>
          <div class="col-1">Idade</div>
        </div>
      </q-item-section>
    </q-item>

    <linha
      v-for="linha in linhas"
      :key="linha.id"
      :id="linha.id"
      :nome="linha.nome"
      :idade="linha.idade"
    ></linha>
  </q-list>
</template>

<style scoped lang="scss"></style>
