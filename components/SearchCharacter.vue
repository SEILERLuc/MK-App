<template>
    <input type="text" v-model="input" placeholder="Search your character..." />
    <div class="item fruit" v-for="character in filteredList()" :key="character.name">
        <p>{{ character.name }}</p>
    </div>
    <div class="item error" v-if="input && !filteredList().length">
        <p>No results found!</p>
    </div>
</template>

<script setup>
let input = ref("");

const fruits = ["apple", "banana", "orange"];
const characters = [
    {
        name: 'Scorpion',
        img: '/img/characters/scorpion.png',
    },
    {
        name: 'Sub-Zero',
        img: '/img/characters/sub-zero.png'
    },
    {
        name: 'Shang-Tsung',
        img: '/img/characters/shang-tsung.png'
    },
    {
        name: 'Mileena',
        img: '/img/characters/mileena.png'
    },
    {
        name: 'Kitana',
        img: '/img/characters/kitana.png'
    },
    {
        name: 'D\'Vorah',
        img: '/img/characters/d-vorah.png'
    },
    {
        name: 'Shao Kahn',
        img: '/img/characters/shao-kahn.png'
    },
    {
        name: 'Noob Saibot',
        img: '/img/characters/noob-saibot.png'
    },
    {
        name: 'Lui Kang',
        img: '/img/characters/lui-kang.png'
    },
    {
        name: 'Frost',
        img: '/img/characters/frost.png'
    },
]

function filteredList() {
    return characters.filter((character) =>
        character.name.toLowerCase().includes(input.value.toLowerCase())
    );
}
</script>