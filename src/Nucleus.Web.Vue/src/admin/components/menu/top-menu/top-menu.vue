﻿<template>
    <v-toolbar color="blue darken-3" dense fixed clipped-left app dark>
        <v-toolbar-side-icon @click="drawerChanged"></v-toolbar-side-icon>
        <v-toolbar-title>
            <span class="title">Nucleus Vue</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-menu>
            <v-btn slot="activator" color="primary">
                {{authStore.getTokenData().sub}}
                <v-icon dark class="ml-3">arrow_drop_down</v-icon>
            </v-btn>

            <v-list>
                <v-list-tile @click="changePasswordDialogChanged(true)">
                    <v-icon>lock</v-icon>
                    <v-list-tile-title>{{$t('ChangePassword')}}</v-list-tile-title>
                </v-list-tile>
            </v-list>
        </v-menu>
        <v-menu>
            <v-btn slot="activator" color="primary">
                <img :src="require('@/assets/images/icons/flags/' + selectedLanguage.languageCode + '.png')" class="mr-2" />
                {{selectedLanguage.languageName}}
                <v-icon dark class="ml-3">arrow_drop_down</v-icon>
            </v-btn>

            <v-list>
                <v-list-tile @click="changeLanguage('en', 'English')">
                    <img src="@/assets/images/icons/flags/en.png" class="mr-2" />
                    <v-list-tile-title>English</v-list-tile-title>
                </v-list-tile>
                <v-list-tile @click="changeLanguage('tr', 'Türkçe')">
                    <img src="@/assets/images/icons/flags/tr.png" class="mr-2" />
                    <v-list-tile-title>Türkçe</v-list-tile-title>
                </v-list-tile>
            </v-list>
        </v-menu>
        <v-btn icon @click="logOut">
            <v-icon>exit_to_app</v-icon>
        </v-btn>

        <change-password :logOut="logOut"></change-password>
    </v-toolbar>
</template>

<script src="./top-menu.ts"></script>