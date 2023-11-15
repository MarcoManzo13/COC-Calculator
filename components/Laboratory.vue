<template>
    <div>
        <v-card>
        <v-card-item>
          <v-card-text>
            <p style="font-weight: 700; font-size: x-large;" class="my-5">Laboratory Troops and Spells
                <button @click="toggleTableVisibility">
                    <v-icon v-if="showLaboratoryTable" icon="mdi mdi-menu-up"></v-icon>
                    <v-icon v-else icon="mdi mdi-menu-down"></v-icon>
                </button>
            </p>
            <v-lazy>
                <v-table v-if="showLaboratoryTable">
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
                    <tr v-for="Laboratory in currentLaboratory" :key="Laboratory.name">
                        <td>{{ Laboratory.name }}</td>
                        <td>{{ Laboratory.seconds }}</td>
                        <td>{{ Laboratory.minutes }}</td>
                        <td>{{ Laboratory.hours }}</td>
                        <td>{{ Laboratory.days }}</td>
                        <td>{{ Laboratory.price }}</td>
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
                showLaboratoryTable: false,
                Laboratory: {
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
                            name: 'Barbarian Level 6',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "1,400,000 Elixir",
                        },
                        {
                            name: 'Archer Level 6',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "2,000,000 Elixir",
                        },
                        {
                            name: 'Giant Level 6',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "2,000,000 Elixir",
                        },
                        {
                            name: 'Goblin Level 6',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "2,000,000 Elixir",
                        },
                        {
                            name: 'Wall Breaker Level 5',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "1,200,000 Elixir",
                        },
                        {
                            name: 'Balloon Level 6',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 3,
                            price: "2,750,000 Elixir",
                        },
                        {
                            name: 'Wizard Level 6',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "2,200,000 Elixir",
                        },
                        {
                            name: 'Healer Level 4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "2,700,000 Elixir",
                        },
                        {
                            name: 'Dragon Level 4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "3,000,000 Elixir",
                        },
                        {
                            name: 'P.E.K.K.A Level 4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "2,800,000 Elixir",
                        },
                        {
                            name: 'Baby Dragon Level 2',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "2,000,000 Elixir",
                        },
                        {
                            name: 'Minion Level 5',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "25,000 Dark Elixir",
                        },
                        {
                            name: 'Hog Rider Level 5',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "30,000 Dark Elixir",
                        },
                        {
                            name: 'Valkyrie Level 3',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 2,
                            price: "12,000 Dark Elixir",
                        },
                        {
                            name: 'Valkyrie Level 4',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 3,
                            price: "25,000 Dark Elixir",
                        },
                        {
                            name: 'Golem Level 3',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "20,000 Dark Elixir",
                        },
                        {
                            name: 'Golem Level 4',
                            seconds: 0,
                            minutes: 0,
                            hours: 18,
                            days: 3,
                            price: "30,000 Dark Elixir",
                        },
                        {
                            name: 'Witch Level 2',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 4,
                            price: "50,000 Dark Elixir",
                        },
                        {
                            name: 'Lava Hound Level 2',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 2,
                            price: "35,000 Dark Elixir",
                        },
                        {
                            name: 'Lightning Spell Level 6',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 4,
                            price: "1,500,000 Elixir",
                        },
                        {
                            name: 'Healing Spell Level 6',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 4,
                            price: "1,800,000 Elixir",
                        },
                        {
                            name: 'Freeze Spell Level 2',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "1,200,000 Elixir",
                        },
                        {
                            name: 'Posion Spell Level 3',
                            seconds: 0,
                            minutes: 0,
                            hours: 0,
                            days: 1,
                            price: "25,000 Dark Elixir",
                        },
                        {
                            name: 'Earthquake Spell Level 3',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "30,000 Dark Elixir",
                        },
                        {
                            name: 'Haste Spell Level 2',
                            seconds: 0,
                            minutes: 0,
                            hours: 12,
                            days: 1,
                            price: "20,000 Dark Elixir",
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
            currentLaboratory() {
                return this.Laboratory[`THLVL${this.THLevelMenu.slice(2)}`] || [];
            },
        },
        methods: {
            toggleTableVisibility() {
                this.showLaboratoryTable = !this.showLaboratoryTable;
            },
        },
    }
</script>

<style scoped>

</style>