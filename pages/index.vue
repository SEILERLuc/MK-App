<template>
  <div>
    <!--PAGE CONTENT-->
    <div class="bg-slate-800 px-6 pt-14 text-yellow-50">
      <div class="px-[15%] sm:px-[30%] my-4">

        <h3 class="w-auto px-8 py-4 text-center font-extrabold uppercase text-yellow-400">History</h3>

        <!--HISTORY-->
        <div class="text-center">
          <div class="inline-block flex-col pb-10 text-justify italic">
            <p class="indent-5 lg:indent-10">Mortal Kombat (communément abrégé MK) est une série de jeux vidéo de
              combat.
              La série se veut concurrente de la franchise Street Fighter de Capcom.</p>
            <p class="pt-3 indent-5 lg:indent-10">Le premier jeu est vendu en 1992 sur bornes d'arcade, un an après la
              sortie de Street Fighter II: The World Warrior. Il est suivi par quatorze jeux (onze jeux principaux et
              trois spin-offs) dont le dernier, Mortal Kombat 11, sort en 2019.</p>
            <p class="pt-3 indent-5 lg:indent-10">La série est caractérisée par des graphismes réalistes et une violence
              brutale et sanglante, dont la marque de fabrique sont les Fatalities, séquences sanglantes de torture de
              l'adversaire vaincu.</p>
            <p class="pt-3 indent-5 lg:indent-10">La lettre K est souvent utilisée dans la série pour orthographier des
              mots normalement écrits avec un «C» dur, par exemple dans le mot Combat devenu Kombat. Les débuts de la
              série sont très populaires dans les bornes d'arcade.</p>
            <p class="pt-3 indent-5 lg:indent-10">Un nouvel opus est annoncé pour la rentrée, le 19 septembre 2023, et
              s'appellera Mortal Kombat 1.</p>
          </div>
        </div>

        <!--GAME MODES-->
        <h3 id="game-modes" class="w-auto px-8 py-4 text-center font-extrabold uppercase text-yellow-400">
          Game Modes</h3>

        <div class="text-center">
          <div class="inline-block flex-col pb-10 text-justify italic">
            <p class="indent-5 lg:indent-10">Généralement, deux joueurs s'affrontent après avoir choisi un personnage,
              et une arène. Le combat est composé de 2 rounds (3 si égalité des joueurs). Le premier arrivé à 2 round
              gagné remporte le combat.</p>
            <p class="pt-3 indent-5 lg:indent-10">Le jeu propose également plusieurs autres modes de jeu, mais surtout
              un mode histoire. Il existe les tours, qui permettent de remporter des éléments cosmétiques.</p>
          </div>
        </div>

        <!--CHARACTERS-->
        <h3 id="characters" class="w-auto px-8 py-4 text-center font-extrabold uppercase text-yellow-400">Characters</h3>

        <div class="text-center">
          <div class="inline-block flex-col pb-20 text-justify italic">
            <p class="indent-5 lg:indent-10">Il propose également un nombre de personnages jouables important. Certains
              sont jouables directement, d'autres sont contenus dans des packs (DLC) qui arrivent généralement quelques
              mois après la sortie.</p>
            <p class="pt-3 indent-5 lg:indent-10">Voici une liste des personnages principaux du dernier jeu, Mortal Kombat
              11.</p>
          </div>
        </div>
      </div>

      <div class="my-4">
        <!--SEARCH BAR---CHARACTER-->
        <h2 class="w-auto px-8 py-4 text-center font-extrabold text-yellow-400">Search your character</h2>

        <div class="mb-8 flex flex-col justify-center items-center">
          <input type="text" v-model="input" class="h-8 w-40 sm:w-64 mb-8 rounded pl-3 text-black text-sm"
            placeholder="Search your character..." />

          <div class="flex flex-wrap justify-center px-4">
            <div v-for="character in filteredList()">
              <CharacterCard :character="character" />
            </div>
            <div v-if="input && !filteredList().length">
              <p>No results found!</p>
            </div>
          </div>
        </div>
      </div>

      <!--MAPS-->
      <h3 id="stages" class="w-auto px-8 py-4 text-center font-extrabold uppercase text-yellow-400">Stages</h3>

      <div class="flex flex-wrap justify-center px-4">
        <div v-for="stage in stages"
          class="m-2 flex flex-col flex-wrap items-center rounded-md bg-zinc-400 bg-gradient-to-t from-[#d53325] to-neutral-950 p-2 duration-300 hover:scale-110">
          <StageCard :stage="stage" />
        </div>
      </div>

      <!--BUYING BUTTON-->
      <div class="text-center">
        <NuxtLink to="/buy">
          <button
            class="transiton place- mb-10 mt-8 rounded-lg bg-yellow-600 px-4 py-2 text-white duration-300 hover:bg-blue-700">Buy
            the game</button>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup>
import { debounce } from '~/composables/utils'
//import { charactersAPI } from '~/characters'

const characters = [
  {
    name: 'Scorpion',
    img: '/img/characters/scorpion.png',
    gender: 'male',
    description: 'Hanzo Hasashi, better known as Scorpion, is a resurrected ninja in the Mortal Kombat fighting game series as well as the mascot of the games. He is one of the very few original characters debuting in the first Mortal Kombat arcade game. He holds the distinction, along with Raiden and Sub-Zero (in one form or another), of appearing in every generation of Mortal Kombat games as a playable character.'
  },
  {
    name: 'Sub Zero',
    img: '/img/characters/sub-zero.png',
    gender: 'male',
    description: 'Kuai Liang, Grandmaster (of the Lin Kuei), and formerly known as Tundra and briefly as the cyborg LK-52O, is the Grandmaster of the Lin Kuei assassin clan in the Mortal Kombat fighting game series.'
  },
  {
    name: 'Shang Tsung',
    img: '/img/characters/shang-tsung.png',
    gender: 'male',
    description: 'Shang Tsung is a character in the Mortal Kombat fighting game series. A powerful, soul stealing sorcerer, Shang Tsung is a celebrated villain of the series and serves as the host for the traditional Mortal Kombat tournament. He serves as a major antagonist to the franchise, often serving as the secondary antagonist of the franchise alongside Quan Chi.'
  },
  {
    name: 'Mileena',
    img: '/img/characters/mileena.png',
    gender: 'female',
    description: 'Mileena is a character in the Mortal Kombat fighting game series. A genetic experiment created by the sorcerer Shang Tsung, she is one of the adopted daughters of the Outworld Emperor Shao Kahn and one of his personal enforcers. She has served as an antagonist throughout the series.'
  },
  {
    name: 'Kitana',
    img: '/img/characters/kitana.png',
    gender: 'female',
    description: 'Kitana is a character in the Mortal Kombat fighting game series who made her debut in Mortal Kombat II.'
  },
  {
    name: 'D\'Vorah',
    img: '/img/characters/d-vorah.png',
    gender: 'female',
    description: 'D\'Vorah is a character in the Mortal Kombat fighting game series. A treacherous Kytinn, D\'Vorah has rose amongst the ranks in the Outworld Empire before the revelations of her true allegiances to some of the major antagonists of the franchise.'
  },
  {
    name: 'Shao Kahn',
    img: '/img/characters/shao-kahn.png',
    gender: 'female',
    description: 'Shao Kahn is a character in the Mortal Kombat fighting game series. A powerful tyrant of the Outworld throne, he is one of the most celebrated villains in not only the fighting game genre, but the video game genre as a whole. He serves as the main antagonist of the franchise alongside Shinnok.'
  },
  {
    name: 'Noob Saibot',
    img: '/img/characters/noob-saibot.png',
    gender: 'male',
    description: 'Noob Saibot, once known as Bi-Han and the Elder Sub-Zero, is a Lin Kuei assassin turned wraith in the Mortal Kombat fighting game series.'
  },
  {
    name: 'Lui Kang',
    img: '/img/characters/lui-kang.png',
    gender: 'male',
    description: 'Liu Kang is a character in the Mortal Kombat fighting game series. An honorable Shaolin Monk, he become the reigning and undisputed champion of the Mortal Kombat Tournament and has remained one of the most recognizable and memorable characters in the series alongside the likes of Raiden, Johnny Cage, Sub-Zero, and Scorpion. He serves as the protagonist of the series in many instances.'
  },
  {
    name: 'Frost',
    img: '/img/characters/frost.png',
    gender: 'female',
    description: 'Frost is a female Lin Kuei warrior in the Mortal Kombat fighting game series, who made her debut in Mortal Kombat: Deadly Alliance.'
  },
]
console.log(characters)

const stages = [
  {
    name: 'Sea Of Blood',
    img: '/img/stages/sea-of-blood.png'
  },
  {
    name: 'Fire Garden',
    img: '/img/stages/fire-garden.png'
  },
  {
    name: 'Goro\'s Lair',
    img: '/img/stages/goros-lair.png'
  },
  {
    name: 'Dead Pool',
    img: '/img/stages/dead-pool.png'
  },
  {
    name: 'Chaotian Age',
    img: '/img/stages/chaotian-age.png'
  },
  {
    name: 'Kharon\'s Ship',
    img: '/img/stages/kharons-ship.png'
  }
]
console.log(stages)

let input = ref("");

function filteredList() {
  return characters.filter((character) =>
    character.name.toLowerCase().includes(input.value.toLowerCase())
  );
}

let message = ref("")

function filtered() {
  console.log(message.value)

  return characters.filter((character) =>
    character.name.toLowerCase().includes(message.value.toLowerCase())
  );
}

</script>

<style>
html {
  scroll-behavior: smooth;
}
</style>