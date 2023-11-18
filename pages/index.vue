<template>
    <div>
      <v-card>
            <!-- Upmost App Bar -->
            <v-app-bar
                prominent
            >
            <v-app-bar-nav-icon icon="mdi-filter-cog-outline" variant="text" @click.stop="drawer = !drawer" />
                <v-app-bar-title>
                    Clash of Clans Time Calculator
                </v-app-bar-title>
                <v-spacer></v-spacer>
                <v-btn variant="outlined" class="mx-3">Sign In</v-btn>
                <v-btn variant="outlined" class="mx-3">Sign Up</v-btn>
            </v-app-bar>

            <!-- Left hand Drawer -->
            <v-navigation-drawer
                v-model="drawer"
                location="left"
            >
                <p>Hola</p>
            </v-navigation-drawer>
        </v-card>
        <v-main>
          <TH />
        </v-main>
    </div>
</template>

<script>
export default {
    data: () => ({
      drawer: true,
      group: null,
      divisionFactor: 1,
      items: [
        {
          title: 'Number of Builders', value: 'foo', icon: 'mdi mdi-home-circle-outline',
        },
      ],
    }),
}
</script>

<style scoped>

</style>