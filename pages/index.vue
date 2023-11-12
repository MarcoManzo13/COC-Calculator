<template>
    <div>
      <v-card>
            <v-app-bar
                prominent
            >
            <v-app-bar-nav-icon icon="mdi-filter-cog-outline" variant="text" @click.stop="drawer = !drawer" />
                <v-app-bar-title>
                    Clash of Clans Calculator
                </v-app-bar-title>
                <v-spacer></v-spacer>
                <v-btn variant="outlined" class="mx-3">Sign In</v-btn>
                <v-btn variant="outlined" class="mx-3">Sign Up</v-btn>
            </v-app-bar>
            <v-navigation-drawer
                v-model="drawer"
                location="left"
            >
                <p class="d-flex text-center justify-left ma-5" style="font-size: x-large;">Filters</p>
                <v-list
                    :items="items"
                ></v-list>
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
      drawer: false,
      group: null,
      items: [
        {
          title: 'Foo',
          value: 'foo',
          icon: 'mdi-home',
        },
        {
          title: 'Bar',
          value: 'bar',
          icon: 'mdi-home',
        },
        {
          title: 'Fizz',
          value: 'fizz',
          icon: 'mdi-home',
        },
        {
          title: 'Buzz',
          value: 'buzz',
          icon: 'mdi-home',
        },
      ],
    }),
}
</script>

<style scoped>

</style>