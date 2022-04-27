<template>
  <v-dialog max-width="600px">
    <v-btn flat slot="activator" color="grey">Sign In<v-icon>exit_to_app</v-icon></v-btn>
    <v-card>
  <!-- Popup dialog -->
      <v-card-title>
        <h2>Sign in to Dashboard</h2>
      </v-card-title>
      <v-card-text>
  <!-- Form with Validation -->
        <v-form
        ref="form"
        v-model="valid"
      >
          <v-text-field
          v-model="email"
          :rules="[v => !!v || 'Required Field.']"
          label="E-mail/UserName"
          prepend-icon="mdi-email-outline"       
          required
        ></v-text-field>
          <v-text-field
            v-model="password"
            :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[v => !!v || 'Password is required']"
            :type="show ? 'text' : 'password'"
            label="Password"
            prepend-icon="mdi-lock"
            hint="Minimum 8 Char"
            counter
            @click:append="show = !show"
            required
        ></v-text-field>
        <v-btn class="rounded-0" color="#000000" block dark >Login</v-btn>
                  <v-card-actions class="text--secondary">
                    <v-checkbox color="#000000" label="Remember me"></v-checkbox>
                    <v-spacer></v-spacer>
        <v-spacer></v-spacer>
                    No account? <a href="#" class="pl-2" style="color: #000000">Sign Up</a>
                  </v-card-actions>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data() {
    return {

    }
  }
}
</script>
