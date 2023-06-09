<template>
    <!-- NAVIGATION BAR-->
    <div
        class="top-0 z-50 bg-gradient-to-b from-[#CA8A04] from-0% to-slate-600 to-30% text-yellow-300 lg:sticky sm:bg-gradient-to-r sm:from-[#CA8A04] sm:from-0% sm:to-slate-600 sm:to-30%">
        <nav class="flex flex-col items-center justify-between py-4 pl-5 pr-8 text-yellow-300 sm:flex-row">
            <div class="h-12 w-12">
                <img src="https://files.cults3d.com/uploaders/13740918/illustration-file/b9d534b2-00d9-44b6-b659-d828e13668ba/Dragon%204.jpg"
                    class="rounded-3xl" alt="Dragon-logo" />
            </div>
            <ul class="flex flex-wrap sm:flex-row flex-wrap items-center justify-center">
                <li class="px-4 hover:underline"><a href="#game-modes">Game Modes</a></li>
                <li class="px-4 hover:underline"><a href="#characters">Characters</a></li>
                <li class="px-4 hover:underline"><a href="#stages">Stages</a></li>
                <NuxtLink to="/buy">
                    <li class="px-4 hover:underline transiton rounded-lg py-2 text-white duration-300 hover:bg-yellow-600">
                        Buy</li>
                </NuxtLink>
            </ul>
        </nav>
    </div>

    <!--MAIN TITLE-->
    <div class="flex justify-around bg-gray-950 py-5">
        <img src="/img/characters/scorpion.png" class="hidden h-40 w-32 sm:block" alt="ScorpionIcon" />
        <img src="/img/logo.png" class="w-32 sm:w-64 self-center" alt="MK_Logo" />
        <img src="/img/characters/sub-zero.png" class="hidden h-44 w-32 sm:block" alt="SubZero_Icon" />
    </div>
</template>