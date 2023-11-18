<template>
    <div>
        <v-card>
        <v-card-item>
          <v-card-text>
            <p style="font-weight: 700; font-size: x-large;" class="my-5">Heroes
                <button @click="toggleTableVisibility">
                    <v-icon v-if="showHeroesTable" icon="mdi mdi-menu-up"></v-icon>
                    <v-icon v-else icon="mdi mdi-menu-down"></v-icon>
                </button>
            </p>
            <v-card-text v-if="showHeroesTable">
                <p style="font-size: large; font-style: italic;">
                    Total time until the Heroes are completely upgraded: 
                    <span style="font-weight: 700;">
                        {{ getTimer() }}
                    </span>
                </p>
            </v-card-text>
            <v-lazy>
                <v-table v-if="showHeroesTable">
                  <thead>
                    <tr>
                      <th class="text-left" style="font-weight: 700; color: #000;">Name</th>
                      <th class="text-left" style="font-weight: 700; color: #000;">Seconds</th>
                      <th class="text-left" style="font-weight: 700; color: #000;">Minutes</th>
                      <th class="text-left" style="font-weight: 700; color: #000;">Hours</th>
                      <th class="text-left" style="font-weight: 700; color: #000;">Days</th>
                      <th class="text-left" style="font-weight: 700; color: #000;">Price</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="heroes in currentHeroes" :key="heroes.name">
                        <td>{{ heroes.name }}</td>
                        <td>{{ heroes.seconds }}</td>
                        <td>{{ heroes.minutes }}</td>
                        <td>{{ heroes.hours }}</td>
                        <td>{{ heroes.days }}</td>
                        <td>{{ heroes.price }}</td>
                    </tr>
                  </tbody>
                </v-table>
            </v-lazy>
          </v-card-text>
        </v-card-item>
      </v-card>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                showHeroesTable: false,
                Heroes: {
                    THLVL1: [
                        {
                            name: 'Cannon (Build)',
                            seconds: 10,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "250 Gold",
                        },
                    ],
                    THLVL9: [
                        {
                            name: 'Barbarian King Level 11',
                            seconds: 0,
                            minutes: 0,
                            hours: 22,
                            days: 0,
                            price: "17,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 12',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "19,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 13',
                            seconds: 0,
                            minutes: 0,
                            hours: 8,
                            days: 1,
                            price: "21,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 14',
                            seconds: 0,
                            minutes: 0,
                            hours: 16,
                            days: 1,
                            price: "23,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 15',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "25,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 16',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "27,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 17',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "29,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 18',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "31,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 19',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "33,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 20',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "35,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 21',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "37,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 22',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "39,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 23',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "41,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 24',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "43,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 25',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "45,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 26',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "47,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 27',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "49,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 28',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "51,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 29',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "53,000 Dark Elixir",
                        },
                        {
                            name: 'Barbarian King Level 30',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 4,
                            price: "55,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 11',
                            seconds: 0,
                            minutes: 0,
                            hours: 22,
                            days: 0,
                            price: "22,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 12',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "24,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 13',
                            seconds: 0,
                            minutes: 0,
                            hours: 8,
                            days: 1,
                            price: "26,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 14',
                            seconds: 0,
                            minutes: 0,
                            hours: 16,
                            days: 1,
                            price: "28,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 15',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "30,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 16',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "32,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 17',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "34,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 18',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "36,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 19',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "38,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 20',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "40,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 21',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "42,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 22',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "44,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 23',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "46,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 24',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "48,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 25',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "50,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 26',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "52,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 27',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "54,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 28',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "56,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 29',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "58,000 Dark Elixir",
                        },
                        {
                            name: 'Archer Queen Level 30',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 4,
                            price: "60,000 Dark Elixir",
                        },
                    ],
                },
            };
        },
        props: {
            THLevelMenu: String,
            THLevels: Array,
        },
        computed: {
            currentHeroes() {
                return this.Heroes[`THLVL${this.THLevelMenu.slice(2)}`] || [];
            },
        },
        methods: {
            toggleTableVisibility() {
                this.showHeroesTable = !this.showHeroesTable;
                this.$emit('timerUpdatedHeroes', this.getTimer());
            },
            
            sumProperty(propertyName) {
                return this.currentHeroes.reduce((total, hero) => total + hero[propertyName], 0);
            },
        
            getTimer() {
                let totalSeconds = this.sumProperty('seconds') + this.sumProperty('minutes') * 60 + this.sumProperty('hours') * 3600 + this.sumProperty('days') * 86400;
                
                const days = Math.floor(totalSeconds / 86400);
                totalSeconds -= days * 86400;
                
                const hours = Math.floor(totalSeconds / 3600);
                totalSeconds -= hours * 3600;
                
                const minutes = Math.floor(totalSeconds / 60);
                const seconds = totalSeconds % 60;
            
                const timer = `${days} Days ${hours} Hours ${minutes} Minutes ${seconds} Seconds`;

                this.$emit('timerUpdatedHeroes', timer);

                return timer;
            },
        },
        mounted() {
            this.getTimer();
            const timerInterval  = setInterval(() => {
                this.getTimer();
            }, 1000);
        },
        beforeDestroy() {
            clearInterval(timerInterval);
        },
    }
</script>

<style scoped>

</style>