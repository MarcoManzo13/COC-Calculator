<template>
    <div>
        <v-card>
        <v-card-item>
          <v-card-text>
            <p style="font-weight: 700; font-size: x-large;" class="my-5">Traps
                <button @click="toggleTableVisibility">
                    <v-icon v-if="showTrapsTable" icon="mdi mdi-menu-up"></v-icon>
                    <v-icon v-else icon="mdi mdi-menu-down"></v-icon>
                </button>
            </p>
            <v-card-text v-if="showTrapsTable">
                <p style="font-size: large; font-style: italic;">
                    Total time until the Traps are completely upgraded: 
                    <span style="font-weight: 700;">
                        {{ getTimer() }}
                    </span>
                </p>
            </v-card-text>
            <v-lazy>
                <v-table v-if="showTrapsTable">
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
                    <tr v-for="traps in currentTraps" :key="traps.name">
                        <td>{{ traps.name }}</td>
                        <td>{{ traps.seconds }}</td>
                        <td>{{ traps.minutes }}</td>
                        <td>{{ traps.hours }}</td>
                        <td>{{ traps.days }}</td>
                        <td>{{ traps.price }}</td>
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
                showTrapsTable: false,
                Traps: {
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
                            name: 'Bomb Level 6 x1',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "500,000 Gold",
                        },
                        {
                            name: 'Bomb Level 6 x2',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "500,000 Gold",
                        },
                        {
                            name: 'Bomb Level 6 x3',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "500,000 Gold",
                        },
                        {
                            name: 'Bomb Level 6 x4',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "500,000 Gold",
                        },
                        {
                            name: 'Bomb Level 6 x5',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "500,000 Gold",
                        },
                        {
                            name: 'Bomb Level 6 x6',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "500,000 Gold",
                        },
                        {
                            name: 'Spring Trap Level 4 x1',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "800,000 Gold",
                        },
                        {
                            name: 'Spring Trap Level 4 x2',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "800,000 Gold",
                        },
                        {
                            name: 'Spring Trap Level 4 x3',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "800,000 Gold",
                        },
                        {
                            name: 'Spring Trap Level 4 x4',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "800,000 Gold",
                        },
                        {
                            name: 'Spring Trap Level 4 x5',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "800,000 Gold",
                        },
                        {
                            name: 'Spring Trap Level 4 x6',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "800,000 Gold",
                        },
                        {
                            name: 'Air Bomb Level 4 x1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "600,000 Gold",
                        },
                        {
                            name: 'Air Bomb Level 4 x2',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "600,000 Gold",
                        },
                        {
                            name: 'Air Bomb Level 4 x3',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "600,000 Gold",
                        },
                        {
                            name: 'Air Bomb Level 4 x4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "600,000 Gold",
                        },
                        {
                            name: 'Giant Bomb (Build) x4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "12,500 Gold",
                        },
                        {
                            name: 'Giant Bomb Level 2 x4',
                            seconds: 0,
                            minutes: 0,
                            hours: 6,
                            days: 0,
                            price: "75,000 Gold",
                        },
                        {
                            name: 'Giant Bomb Level 3 x4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "600,000 Gold",
                        },
                        {
                            name: 'Seeking Air Mine (Build) x3',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "15,000 Gold",
                        },
                        {
                            name: 'Seeking Air Mine (Build) x4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "1,000,000 Gold",
                        },
                        {
                            name: 'Seeking Air Mine Level 2 x3',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "15,000 Gold",
                        },
                        {
                            name: 'Seeking Air Mine Level 2 x4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "1,000,000 Gold",
                        },
                        {
                            name: 'Seeking Air Mine Level 2 x1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "1,000,000 Gold",
                        },
                        {
                            name: 'Seeking Air Mine Level 2 x2',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "1,000,000 Gold",
                        },
                        {
                            name: 'Skeleton Trap Level 3 x1',
                            seconds: 0,
                            minutes: 0,
                            hours: 20,
                            days: 0,
                            price: "900,000 Gold",
                        },
                        {
                            name: 'Skeleton Trap Level 3 x2',
                            seconds: 0,
                            minutes: 0,
                            hours: 20,
                            days: 0,
                            price: "900,000 Gold",
                        },
                    ],
                }
            }
        },
        props: {
            THLevelMenu: String,
            THLevels: Array,
        },
        computed: {
            currentTraps() {
                return this.Traps[`THLVL${this.THLevelMenu.slice(2)}`] || [];
            },
        },
        methods: {
            toggleTableVisibility() {
                this.showTrapsTable = !this.showTrapsTable;
                this.$emit('timerUpdatedTraps', this.getTimer());
            },
            
            sumProperty(propertyName) {
                return this.currentTraps.reduce((total, trap) => total + trap[propertyName], 0);
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

                this.$emit('timerUpdatedTraps', timer);

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