<template>
    <div>
        <v-card>
        <v-card-item>
          <v-card-text>
            <p style="font-weight: 700; font-size: x-large;" class="my-5">Army Buildings
                <button @click="toggleTableVisibility">
                    <v-icon v-if="showArmyBuildingsTable" icon="mdi mdi-menu-up"></v-icon>
                    <v-icon v-else icon="mdi mdi-menu-down"></v-icon>
                </button>
            </p>
            <v-table v-if="showArmyBuildingsTable">
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
                <tr v-for="armyBuilding in currentArmyBuildings" :key="armyBuilding.name">
                    <td>{{ armyBuilding.name }}</td>
                    <td>{{ armyBuilding.seconds }}</td>
                    <td>{{ armyBuilding.minutes }}</td>
                    <td>{{ armyBuilding.hours }}</td>
                    <td>{{ armyBuilding.days }}</td>
                    <td>{{ armyBuilding.price }}</td>
                </tr>
              </tbody>
            </v-table>
          </v-card-text>
        </v-card-item>
      </v-card>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                showArmyBuildingsTable: false,
                ArmyBuildings: {
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
                            name: 'Army Camp Level 7 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "1,500,000 Elixir",
                        },
                        {
                            name: 'Army Camp Level 7 #2',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "1,500,000 Elixir",
                        },
                        {
                            name: 'Army Camp Level 7 #3',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "1,500,000 Elixir",
                        },
                        {
                            name: 'Army Camp Level 7 #4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "1,500,000 Elixir",
                        },
                        {
                            name: 'Barracks Level 11 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 4,
                            price: "2,600,000 Elixir",
                        },
                        {
                            name: 'Dark Barracks Level 5 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 3,
                            price: "2,200,000 Elixir",
                        },
                        {
                            name: 'Dark Barracks Level 6 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 4,
                            price: "2,900,000 Elixir",
                        },
                        {
                            name: 'Laboratory Level 7 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "800,000 Elixir",
                        },
                        {
                            name: 'Spell Factory Level 4 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 3,
                            price: "1,200,000 Elixir",
                        },
                        {
                            name: 'Dark Spell Factory Level 3 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "600,000 Elixir",
                        },
                        {
                            name: 'Dark Spell Factory Level 4 #1',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 4,
                            price: "1,200,000 Elixir",
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
            currentArmyBuildings() {
                return this.ArmyBuildings[`THLVL${this.THLevelMenu.slice(2)}`] || [];
            },
        },
        methods: {
            toggleTableVisibility() {
                this.showArmyBuildingsTable = !this.showArmyBuildingsTable;
            },
        },
    }
</script>

<style scoped>

</style>