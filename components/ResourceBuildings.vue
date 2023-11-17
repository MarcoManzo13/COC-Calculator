<template>
    <div>
        <v-card>
        <v-card-item>
          <v-card-text>
            <p style="font-weight: 700; font-size: x-large;" class="my-5">Resource Buildings
                <button @click="toggleTableVisibility">
                    <v-icon v-if="showResourcesBuildingsTable" icon="mdi mdi-menu-up"></v-icon>
                    <v-icon v-else icon="mdi mdi-menu-down"></v-icon>
                </button>
            </p>
            <v-card-text v-if="showResourcesBuildingsTable">
                <p style="font-size: large; font-style: italic;">Total time until the Resources Buildings are completely upgraded: <span style="font-weight: 700;">{{ getTimer() }}</span></p>
            </v-card-text>
            <v-lazy>
                <v-table v-if="showResourcesBuildingsTable">
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
                    <tr v-for="resourcesBuilding in currentResourcesBuildings" :key="resourcesBuilding.name">
                        <td>{{ resourcesBuilding.name }}</td>
                        <td>{{ resourcesBuilding.seconds }}</td>
                        <td>{{ resourcesBuilding.minutes }}</td>
                        <td>{{ resourcesBuilding.hours }}</td>
                        <td>{{ resourcesBuilding.days }}</td>
                        <td>{{ resourcesBuilding.price }}</td>
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
                showResourcesBuildingsTable: false,
                ResourcesBuildings: {
                    THLVL1: [
                        {
                            name: 'Yes (Build)',
                            seconds: 10,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "250 Gold",
                        },
                    ],
                    THLVL9: [
                        {
                            name: 'Town Hall To Level 10 #1',
                            seconds: 10,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "3,500,000 Gold",
                        },
                        {
                            name: 'Gold Mine (Build) #7',
                            seconds: 10,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "150 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 2 #7',
                            seconds: 0,
                            minutes: 1,
                            hours: 0,
                            days: 0,
                            price: "300 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 3 #7',
                            seconds: 0,
                            minutes: 4,
                            hours: 0,
                            days: 0,
                            price: "700 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 4 #7',
                            seconds: 0,
                            minutes: 10,
                            hours: 0,
                            days: 0,
                            price: "1,400 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 5 #7',
                            seconds: 0,
                            minutes: 40,
                            hours: 0,
                            days: 0,
                            price: "3,000 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 6 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 3,
                            days: 0,
                            price: "7,000 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 7 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 6,
                            days: 0,
                            price: "14,000 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 8 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 8,
                            days: 0,
                            price: "28,000 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 9 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 10,
                            days: 0,
                            price: "56,000 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 10 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 0,
                            price: "75,000 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 11 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 16,
                            days: 0,
                            price: "100,000 Elixir",
                        },
                        {
                            name: 'Gold Mine Level 12 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 20,
                            days: 0,
                            price: "200,000 Elixir",
                        },
                        {
                            name: 'Elixir Collector (Build) #7',
                            seconds: 10,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "150 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 2 #7',
                            seconds: 0,
                            minutes: 1,
                            hours: 0,
                            days: 0,
                            price: "300 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 3 #7',
                            seconds: 0,
                            minutes: 4,
                            hours: 0,
                            days: 0,
                            price: "700 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 4 #7',
                            seconds: 0,
                            minutes: 10,
                            hours: 0,
                            days: 0,
                            price: "1,400 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 5 #7',
                            seconds: 0,
                            minutes: 40,
                            hours: 0,
                            days: 0,
                            price: "3,000 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 6 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 3,
                            days: 0,
                            price: "7,000 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 7 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 6,
                            days: 0,
                            price: "14,000 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 8 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 8,
                            days: 0,
                            price: "28,000 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 9 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 10,
                            days: 0,
                            price: "56,000 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 10 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 0,
                            price: "75,000 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 11 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 16,
                            days: 0,
                            price: "100,000 Gold",
                        },
                        {
                            name: 'Elixir Collector Level 12 #7',
                            seconds: 0,
                            minutes: 0,
                            hours: 20,
                            days: 0,
                            price: "200,000 Gold",
                        },
                        {
                            name: 'Dark Elixir Drill (Build) #3',
                            seconds: 0,
                            minutes: 0,
                            hours: 6,
                            days: 0,
                            price: "500,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 2 #3',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 0,
                            price: "700,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 3 #3',
                            seconds: 0,
                            minutes: 0,
                            hours: 18,
                            days: 0,
                            price: "900,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 4 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "1,200,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 4 #2',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "1,200,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 4 #3',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "1,200,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 5 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "1,500,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 5 #2',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "1,500,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 5 #3',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "1,500,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 6 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "1,800,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 6 #2',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "1,800,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Drill Level 6 #3',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "1,800,000 Elixir",
                        },
                        {
                            name: 'Gold Storage (Build) #4',
                            seconds: 10,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "300 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 2 #4',
                            seconds: 0,
                            minutes: 5,
                            hours: 0,
                            days: 0,
                            price: "750 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 3 #4',
                            seconds: 0,
                            minutes: 20,
                            hours: 0,
                            days: 0,
                            price: "1,500 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 4 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 1,
                            days: 0,
                            price: "3,000 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 5 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 2,
                            days: 0,
                            price: "6,000 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 6 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 3,
                            days: 0,
                            price: "12,000 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 7 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 4,
                            days: 0,
                            price: "25,000 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 8 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 5,
                            days: 0,
                            price: "50,000 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 9 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 8,
                            days: 0,
                            price: "100,000 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 10 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 0,
                            price: "250,000 Elixir",
                        },
                        {
                            name: 'Gold Storage Level 11 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 16,
                            days: 0,
                            price: "500,000 Elixir",
                        },
                        {
                            name: 'Elixir Storage (Build) #4',
                            seconds: 10,
                            minutes: 0,
                            hours: 0,
                            days: 0,
                            price: "300 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 2 #4',
                            seconds: 0,
                            minutes: 5,
                            hours: 0,
                            days: 0,
                            price: "750 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 3 #4',
                            seconds: 0,
                            minutes: 20,
                            hours: 0,
                            days: 0,
                            price: "1,500 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 4 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 1,
                            days: 0,
                            price: "3,000 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 5 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 2,
                            days: 0,
                            price: "6,000 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 6 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 3,
                            days: 0,
                            price: "12,000 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 7 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 4,
                            days: 0,
                            price: "25,000 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 8 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 5,
                            days: 0,
                            price: "50,000 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 9 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 8,
                            days: 0,
                            price: "100,000 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 10 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 0,
                            price: "250,000 Gold",
                        },
                        {
                            name: 'Elixir Storage Level 11 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 16,
                            days: 0,
                            price: "500,000 Gold",
                        },
                        {
                            name: 'Dark Elixir Storage Level 5 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "2,000,000 Elixir",
                        },
                        {
                            name: 'Dark Elixir Storage Level 6 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "3,000,000 Elixir",
                        },
                        {
                            name: 'Clan Castle Level 5 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "2,500,000 Elixir",
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
            currentResourcesBuildings() {
                return this.ResourcesBuildings[`THLVL${this.THLevelMenu.slice(2)}`] || [];
            },
        },
        methods: {
            toggleTableVisibility() {
                this.showResourcesBuildingsTable = !this.showResourcesBuildingsTable;
            },

            sumProperty(propertyName) {
                return this.currentResourcesBuildings.reduce((total, ResourcesBuilding) => total + ResourcesBuilding[propertyName], 0);
            },
        
            getTimer() {
                let totalSeconds = this.sumProperty('seconds') + this.sumProperty('minutes') * 60 + this.sumProperty('hours') * 3600 + this.sumProperty('days') * 86400;
                
                const days = Math.floor(totalSeconds / 86400);
                totalSeconds -= days * 86400;
                
                const hours = Math.floor(totalSeconds / 3600);
                totalSeconds -= hours * 3600;
                
                const minutes = Math.floor(totalSeconds / 60);
                const seconds = totalSeconds % 60;
            
                return `${days} Days ${hours} Hours ${minutes} Minutes ${seconds} Seconds`;
            },
        
            displayTimer() {
                return this.getTimer();
            },
        },
    }
</script>

<style lang="scss" scoped>

</style>