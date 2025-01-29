<template>
  <v-container max-width="700">
    <!-- Donnée de l'exercice -->
    <exercice3-donnee />
    <!-- Zone de travail pour l'exercice -->
    <div class="exe-zone">
      <h2>Zone d'exercice</h2>
      <v-card
        class="mx-auto my-6 pa-2"
        max-width="300"
      >
        <v-card-title>Liste de Pokémons</v-card-title>

        <!-- Affichage du message si la liste est vide -->
        <v-card-subtitle v-if="pokemons.length === 0" class="text-center">
          La liste est vide.
        </v-card-subtitle>

        <!-- Liste dynamique des Pokémons -->
        <v-list v-else>
          <v-list-item v-for="(pokemon, index) in pokemons" :key="index">
            <v-list-item-title>
              {{ pokemon }}
            </v-list-item-title>

            <!-- Bouton de suppression -->
            <template v-slot:append>
              <v-btn @click="removePokemon(index)"
                     icon="mdi-delete"
                     variant="text"
              ></v-btn>
            </template>
          </v-list-item>
        </v-list>
      </v-card>
    </div>
  </v-container>
</template>

<script setup>
import { ref } from "vue";
import Exercice3Donnee from "@/components/donnees/Exercice3Donnee.vue";

// Tableau réactif de noms de Pokémons
const pokemons = ref([
  "Pikachu",
  "Bulbizarre",
  "Salamèche",
  "Carapuce",
  "Rondoudou"
]);

/**
 * Fonction qui supprime le Pokémon à l'index donné.
 * @param {number} index - Index du Pokémon à supprimer.
 */
function removePokemon(index) {
  pokemons.value.splice(index, 1);
}
</script>
