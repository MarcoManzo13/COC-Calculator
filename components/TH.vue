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
                    <p style="font-size:x-large; font-weight: 700;">Total time for all buildings: {{ totalTimer }}</p>
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
    computed: {
        totalTimer() {
            let totalDays = 0;
            let totalHours = 0;
            let totalMinutes = 0;
            let totalSeconds = 0;
            
            totalDays += parseInt(this.defensiveBuildingsTimerValue.split(' ')[0]);
            totalHours += parseInt(this.defensiveBuildingsTimerValue.split(' ')[2]);
            totalMinutes += parseInt(this.defensiveBuildingsTimerValue.split(' ')[4]);
            totalSeconds += parseInt(this.defensiveBuildingsTimerValue.split(' ')[6]);
            
            totalDays += parseInt(this.resourcesBuildingsTimerValue.split(' ')[0]);
            totalHours += parseInt(this.resourcesBuildingsTimerValue.split(' ')[2]);
            totalMinutes += parseInt(this.resourcesBuildingsTimerValue.split(' ')[4]);
            totalSeconds += parseInt(this.resourcesBuildingsTimerValue.split(' ')[6]);

            totalDays += parseInt(this.armyBuildingsTimerValue.split(' ')[0]);
            totalHours += parseInt(this.armyBuildingsTimerValue.split(' ')[2]);
            totalMinutes += parseInt(this.armyBuildingsTimerValue.split(' ')[4]);
            totalSeconds += parseInt(this.armyBuildingsTimerValue.split(' ')[6]);
        
            totalDays += parseInt(this.heroTimerValue.split(' ')[0]);
            totalHours += parseInt(this.heroTimerValue.split(' ')[2]);
            totalMinutes += parseInt(this.heroTimerValue.split(' ')[4]);
            totalSeconds += parseInt(this.heroTimerValue.split(' ')[6]);
        
            totalDays += parseInt(this.laboratoryTimerValue.split(' ')[0]);
            totalHours += parseInt(this.laboratoryTimerValue.split(' ')[2]);
            totalMinutes += parseInt(this.laboratoryTimerValue.split(' ')[4]);
            totalSeconds += parseInt(this.laboratoryTimerValue.split(' ')[6]);
        
            totalDays += parseInt(this.trapsTimerValue.split(' ')[0]);
            totalHours += parseInt(this.trapsTimerValue.split(' ')[2]);
            totalMinutes += parseInt(this.trapsTimerValue.split(' ')[4]);
            totalSeconds += parseInt(this.trapsTimerValue.split(' ')[6]);

            // Handle seconds overflow
            while (totalSeconds >= 60) {
              totalSeconds -= 60;
              totalMinutes++;
            }
        
            // Handle minutes overflow
            while (totalMinutes >= 60) {
              totalMinutes -= 60;
              totalHours++;
            }
        
            // Handle hours overflow
            while (totalHours >= 24) {
              totalHours -= 24;
              totalDays++;
            }
        
            return `${totalDays} Days ${totalHours} Hours ${totalMinutes} Minutes ${totalSeconds} Seconds`;
        }
    },
};
</script>

<style scoped>

</style>