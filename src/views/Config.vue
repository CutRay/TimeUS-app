<template lang="pug">
v-row(no-gutters justify="center")  
  v-responsive(max-width="598" width="375")
    v-container.pa-0
      v-list
        v-list-item-group(color="light-green")
          v-list-item(
            @click="$refs.email.open()"
            max-width="598")
            v-list-item-icon
              v-icon $emailOutline
            v-list-item-content
              v-list-item-title メールアドレス変更
          v-list-item(
            @click="$refs.password.open()"
            max-width="598")
            v-list-item-icon
              v-icon $lockOutline
            v-list-item-content
              v-list-item-title パスワード変更
          v-list-item(
            @click="$refs.logout.open()"
            max-width="598")
            v-list-item-icon
              v-icon $logout
            v-list-item-content
              v-list-item-title ログアウト
          v-divider
          v-list-item(
            @click="$refs.withdrawal.open()"
            max-width="598")
            v-list-item-icon
              v-icon $exit
            v-list-item-content
              v-list-item-title 退会する
      confirm-dialog(
        ref="logout"
        title="ログアウトしますか？" text="再度ログインする際にはメールアドレスとパスワードが必要になります")
      confirm-dialog(
        ref="withdrawal"
        title="退会しますか？" text="退会した場合今までのデータは全て削除され、復元できなくなります")
      email-dialog(
        ref="email"
        @ok="sendEmail($event)"
        title="新規メールアドレス")
      password-dialog(
        ref="password"
        @ok="sendPassword($event)"
        title="新規パスワード")
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'
import ConfirmDialog from '@/components/dialogs/ConfirmDialog.vue'
import EmailDialog from '@/components/dialogs/EmailDialog.vue'
import PasswordDialog from '@/components/dialogs/PasswordDialog.vue'
export default defineComponent({
  components: { ConfirmDialog, EmailDialog, PasswordDialog },
  setup() {
    return {
      sendEmail(email: string) {
        console.log(email)
      },
      sendPassword(password: string) {
        console.log(password)
      },
    }
  },
})
</script>
