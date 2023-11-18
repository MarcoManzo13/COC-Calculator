<template>
    <div>
        <v-card>
            <v-card-item>
                <v-card-title>
                    <select v-model="THLevelMenu" style="width: 100%; border: solid black 0.1em; text-align: center; font-size: larger; font-weight: 700; border-radius: 50px;">
                        <option v-for="level in THLevels" :key="level">{{ `TH${level}` }}</option>
                    </select>
                </v-card-title>
            </v-card-item>
            <v-divider/>
            <v-card-item>
                <v-card-text>
                    <p>Total time across all buildings: {{ trapsTimerValue }}</p>
                </v-card-text>
            </v-card-item>
        </v-card>
        <v-divider />
      <DefensiveBuildings :THLevelMenu="THLevelMenu" :THLevels="THLevels" @timerUpdatedDefensiveBuildings="updateDefensiveBuildingsTimer"/>
      <v-divider />
      <ResourceBuildings :THLevelMenu="THLevelMenu" :THLevels="THLevels" @timerUpdatedResourcesBuildings="updateResourcesBuildingsTimer"/>
      <v-divider/>
      <ArmyBuildings :THLevelMenu="THLevelMenu" :THLevels="THLevels" @timerUpdatedArmyBuildings="updateArmyBuildingsTimer"/>
      <v-divider/>
      <Heroes :THLevelMenu="THLevelMenu" :THLevels="THLevels" @timerUpdatedHeroes="updateHeroesTimer"/>
      <v-divider />
      <Laboratory :THLevelMenu="THLevelMenu" :THLevels="THLevels" @timerUpdatedLaboratory="updateLaboratoyTimer"/>
      <v-divider />
      <Traps :THLevelMenu="THLevelMenu" :THLevels="THLevels" @timerUpdatedTraps="updateTrapsTimer"/>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            THLevelMenu: 'TH9',
            THLevels: Array.from({ length: 15 }, (_, i) => i + 1),
            defensiveBuildingsTimerValue: '',
            resourcesBuildingsTimerValue: '',
            armyBuildingsTimerValue: '',
            heroTimerValue: '',
            laboratoryTimerValue: '',
            trapsTimerValue: '',
        };
    },
    methods: {
        updateDefensiveBuildingsTimer(newDefensiveBuildingsTimerValue) {
            this.defensiveBuildingsTimerValue = newDefensiveBuildingsTimerValue;
        },
        updateResourcesBuildingsTimer(newResourcesBuildingsTimerValue) {
            this.resourcesBuildingsTimerValue = newResourcesBuildingsTimerValue;
        },
        updateArmyBuildingsTimer(newArmyBuildingsTimerValue) {
            this.armyBuildingsTimerValue = newArmyBuildingsTimerValue;
        },
        updateHeroesTimer(newHeroTimerValue) {
            this.heroTimerValue = newHeroTimerValue;
        },
        updateLaboratoyTimer(newLaboratoryTimerValue) {
            this.laboratoryTimerValue = newLaboratoryTimerValue;
        },
        updateTrapsTimer(newTrapsTimerValue) {
            this.trapsTimerValue = newTrapsTimerValue;
        },
    },
};
</script>

<style scoped>

</style>