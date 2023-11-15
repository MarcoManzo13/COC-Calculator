<template>
    <div>
        <v-card>
            <v-card-item>
                <v-card-title>
                    <select v-model="THLevelMenu">
                        <option v-for="level in THLevels" :key="level">{{ `TH${level}` }}</option>
                    </select>
                </v-card-title>
            </v-card-item>
        </v-card>
      <DefensiveBuildings :THLevelMenu="THLevelMenu" :THLevels="THLevels"/>
      <v-divider />
      <ResourceBuildings :THLevelMenu="THLevelMenu" :THLevels="THLevels"/>
      <v-divider/>
      <ArmyBuildings :THLevelMenu="THLevelMenu" :THLevels="THLevels"/>
      <v-divider/>
      <Heroes :THLevelMenu="THLevelMenu" :THLevels="THLevels"/>
    </div>
</template>
  
<script>
export default {
  data() {
    return {
        THLevelMenu: 'TH1',
        THLevels: Array.from({ length: 15 }, (_, i) => i + 1),
    }
  }
};
</script>

<style scoped>

</style>