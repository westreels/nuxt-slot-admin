<template>
  <div>
    <v-app-bar app dark >
      <v-app-bar-nav-icon
              @click="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-toolbar-title>
        <nuxt-link no-prefetch to="/admin" tag="span" class="pointer font-podkova-bold " >
          NetGame
        </nuxt-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn text exact
               class="font-podkova-bold "
               v-for="link in links"
               :key="link.title" :to="link.url"
        >
          <v-icon left color="deep-orange darken-2">{{link.icon}}</v-icon>
          {{link.title}}
        </v-btn>
        <v-btn text exact
               class="font-podkova-bold"
               @click="logout"
               no-prefetch
        >
          <v-icon left color="deep-orange darken-2">mdi-logout</v-icon>
          LOGOUT
        </v-btn>
      </v-toolbar-items>
    </v-app-bar>
    <v-navigation-drawer app temporary
                         v-model="drawer" class="grey darken-4" color="deep-orange darken-2">
      <v-container>
        <v-layout class="mt-5 mb-5" wrap>
          <v-btn
                  class="deep-orange darken-2 justify-start display_block mb-5 font-podkova-bold"
                  dark
                  exact
                  no-prefetch
                  to="/admin">
            <v-icon left color="white">mdi-bank</v-icon>
            Main
          </v-btn>
          <v-btn
                  class="deep-orange darken-2 justify-start display_block mb-5 font-podkova-bold"
                  dark
                  exact
                  no-prefetch
                  to="/admin/category">
            <v-icon left color="white">mdi-checkbox-multiple-blank</v-icon>
            Category
          </v-btn>
          <v-btn
                  class="deep-orange darken-2 justify-start display_block mb-5 font-podkova-bold"
                  dark
                  exact
                  no-prefetch
                  to="/admin/seo">
            <v-icon left color="white">mdi-message-draw</v-icon>
            SEO
          </v-btn>
          <v-btn
                  class="deep-orange darken-2 justify-start display_block mb-5 font-podkova-bold"
                  dark
                  no-prefetch
                  to="/admin/settings">
            <v-icon left color="white">mdi-message-draw</v-icon>
            Settings
          </v-btn>
          <v-btn
                  class="deep-orange darken-2 justify-start display_block mb-5 font-podkova-bold"
                  dark
                  no-prefetch
                  to="/admin/static-pages">
            <v-icon left color="white">mdi-checkbox-multiple-blank</v-icon>
            Static Pages
          </v-btn>
          <v-btn
                  class="deep-orange darken-2 justify-start display_block mb-5 font-podkova-bold"
                  dark
                  no-prefetch
                  to="/admin/options">
            <v-icon left color="white">mdi-share-variant</v-icon>
            Options
          </v-btn>
          <v-menu
                  transition="slide-y-transition"
                  bottom
                  no-prefetch
                  class="d-block"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                      class="deep-orange darken-2 justify-start display_block font-podkova-bold"
                      dark
                      v-bind="attrs"
                      v-on="on"
              >
                <v-icon left>mdi-folder-multiple-outline</v-icon>
                Casino
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                      no-prefetch
                      class="font-podkova-bold"
                      v-for="(item, i) in casinoPage"
                      :key="i" :to="item.link"
              >
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-menu
                  transition="slide-y-transition"
                  bottom
                  no-prefetch
                  class="d-block"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                      class="deep-orange mt-5 darken-2 justify-start display_block font-podkova-bold"
                      dark
                      v-bind="attrs"
                      v-on="on"
              >
                <v-icon left>mdi-folder-multiple-outline</v-icon>
                Blog
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                      no-prefetch
                      class="font-podkova-bold"
                      v-for="(item, i) in blogPage"
                      :key="i" :to="item.link"
              >
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-menu
                  transition="slide-y-transition"
                  bottom
                  no-prefetch
                  class="d-block"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                      class="deep-orange mt-5 darken-2 justify-start display_block font-podkova-bold"
                      dark
                      v-bind="attrs"
                      v-on="on"
              >
                <v-icon left>mdi-folder-multiple-outline</v-icon>
                Vendors
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                      no-prefetch
                      class="font-podkova-bold"
                      v-for="(item, i) in vendorsPage"
                      :key="i" :to="item.link"
              >
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-menu
                  transition="slide-y-transition"
                  bottom
                  no-prefetch
                  class="d-block"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                      class="deep-orange mt-5 darken-2 justify-start display_block font-podkova-bold"
                      dark
                      v-bind="attrs"
                      v-on="on"
              >
                <v-icon left>mdi-folder-multiple-outline</v-icon>
                Payments
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                      no-prefetch
                      class="font-podkova-bold"
                      v-for="(item, i) in paymentsPage"
                      :key="i" :to="item.link"
              >
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-menu
                  transition="slide-y-transition"
                  bottom
                  no-prefetch
                  class="d-block"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                      class="deep-orange mt-5 darken-2 justify-start display_block font-podkova-bold"
                      dark
                      v-bind="attrs"
                      v-on="on"
              >
                <v-icon left>mdi-folder-multiple-outline</v-icon>
                Slots
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                      no-prefetch
                      class="font-podkova-bold"
                      v-for="(item, i) in slotsPage"
                      :key="i" :to="item.link"
              >
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-menu
                  transition="slide-y-transition"
                  bottom
                  no-prefetch
                  class="d-block"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                      class="deep-orange mt-5 darken-2 justify-start display_block font-podkova-bold"
                      dark
                      v-bind="attrs"
                      v-on="on"
              >
                <v-icon left>mdi-folder-multiple-outline</v-icon>
                Bonuses
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                      no-prefetch
                      class="font-podkova-bold"
                      v-for="(item, i) in bonusesPage"
                      :key="i" :to="item.link"
              >
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-menu
                  transition="slide-y-transition"
                  bottom
                  no-prefetch
                  class="d-block"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                      class="deep-orange mt-5 darken-2 justify-start display_block font-podkova-bold"
                      dark
                      v-bind="attrs"
                      v-on="on"
              >
                <v-icon left>mdi-folder-multiple-outline</v-icon>
                News
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                      no-prefetch
                      class="font-podkova-bold"
                      v-for="(item, i) in newsPage"
                      :key="i" :to="item.link"
              >
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          <v-menu
                  transition="slide-y-transition"
                  bottom
                  no-prefetch
                  class="d-block"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                      class="deep-orange mt-5 darken-2 justify-start display_block font-podkova-bold"
                      dark
                      v-bind="attrs"
                      v-on="on"
              >
                <v-icon left>mdi-folder-multiple-outline</v-icon>
                Interview
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                      no-prefetch
                      class="font-podkova-bold"
                      v-for="(item, i) in interviewPage"
                      :key="i" :to="item.link"
              >
                <v-list-item-title>
                  {{ item.title }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </v-layout>
        <v-layout class="justify-space-around mt-3 align-center">
          <v-btn class="deep-orange darken-2 display_block justify-start" color="deep-orange darken-2 font-podkova-bold"
                 @click="logout">
            <v-icon left color="white">mdi-logout</v-icon>
            Logout
          </v-btn>
        </v-layout>
      </v-container>
    </v-navigation-drawer>
  </div>
</template>

<script>
    export default {
        name: "AdminMenu",
        data(){
            return {
                drawer: false,
                links: [
                    {title:'MAIN', url:'/admin', icon:'mdi-bank'},
                    {title:'CATEGORY', url:'/admin/category', icon:'mdi-checkbox-multiple-blank'},
                    {title:'SETTINGS', url:'/admin/settings', icon:'mdi-message-draw'},
                    {title:'STATIC PAGES', url:'/admin/static-pages', icon:'mdi-checkbox-multiple-blank'},
                    {title:'OPTIONS', url:'/admin/options', icon:'mdi-share-variant'},
                    {title:'CASINO', url:'/admin/casino', icon:'mdi-cash-usd'},
                    {title:'BLOG', url:'/admin/blog', icon:'mdi-blogger'},
                    {title:'VENDORS', url:'/admin/vendor', icon:'mdi-android-studio'},
                    {title:'PAYMENTS', url:'/admin/payment', icon:'mdi-cash'},
                    {title:'SLOTS', url:'/admin/slot', icon:'mdi-gamepad-variant'},
                    {title:'BONUSES', url:'/admin/bonus', icon:'mdi-cake'},
                    {title:'NEWS', url:'/admin/news', icon:'mdi-blogger'},
                    {title:'INTERVIEW', url:'/admin/interview', icon:'mdi-blogger'},
                ],
                casinoPage: [
                    { title: 'All casino', link: '/admin/casino' },
                    { title: 'Add casino', link: '/admin/casino/add' }
                ],
                blogPage: [
                    { title: 'All blog', link: '/admin/blog' },
                    { title: 'Add blog', link: '/admin/blog/add' }
                ],
                vendorsPage: [
                    { title: 'All vendors', link: '/admin/vendor' },
                    { title: 'Add vendors', link: '/admin/vendor/add' }
                ],
                paymentsPage: [
                    { title: 'All payments', link: '/admin/payment' },
                    { title: 'Add payments', link: '/admin/payment/add' }
                ],
                slotsPage: [
                    { title: 'All slots', link: '/admin/slot' },
                    { title: 'Add slots', link: '/admin/slot/add' }
                ],
                bonusesPage: [
                    { title: 'All bonuses', link: '/admin/bonus' },
                    { title: 'Add bonus', link: '/admin/bonus/add' }
                ],
                newsPage: [
                    { title: 'All news', link: '/admin/news' },
                    { title: 'Add news', link: '/admin/news/add' }
                ],
                interviewPage: [
                    { title: 'All interview', link: '/admin/interview' },
                    { title: 'Add interview', link: '/admin/interview/add' }
                ],
            }
        },
        methods: {
            async logout(){
                const user = this.$store.getters['user/getUser']
                const data = {
                  session: user.session,
                  id: user.id,
                }
                await this.$store.dispatch('user/logout', data)
                const currentUser = this.$store.getters['user/getUser']
                if(!currentUser.login) this.$router.push('/')
            }
        },
    }
</script>

<style scoped>
  .border {
    border: 1px solid red;
  }
  .display_block {
    width:100%;
  }
</style>
