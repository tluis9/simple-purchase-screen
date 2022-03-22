<template>
  <v-app id="inspire">
    <v-content>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar class="header-card pt-4">
                <v-toolbar-title class="card-title">
                  Formulário<br /> 
                  para compra de <br />
                  <b style="font-weight:900;">
                    Pacote de Adesivos
                  </b>
                  </v-toolbar-title>
                <v-spacer></v-spacer>
                <img src="@/assets/box.png" alt="box" title="box">
              </v-toolbar>
              <v-card-text>
                <v-container fluid>
                  <h3 class="pb-2">
                    Quais adesivos:
                  </h3>
                  <v-checkbox 
                    v-model="checkbox.angular"
                    label="Angular"
                    color="#2f3675"
                    hide-details
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkbox.vue"
                    label="Vue"
                    color="#2f3675"
                    hide-details
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkbox.react"
                    label="React"
                    color="#2f3675"
                    hide-details
                  ></v-checkbox>
                </v-container>
                <v-container>
                  <h3>
                    Quantos adesivos de cada?
                  </h3>
                  <div class="btn-purchase d-inline-block">
                    <v-btn 
                      icon
                      @click="handleAddSticker"
                    >
                      <v-icon>
                        mdi-plus
                      </v-icon>
                    </v-btn>
                  </div>
                  <div style="width:40%" class="d-inline-block">
                    <v-text-field
                      v-model="stickersAmount"
                      readonly
                      dense
                      number
                      outlined
                      class="justify-center align-center centered-input"
                      hide-details
                    ></v-text-field>
                  </div>
                  <div class="btn-purchase d-inline-block">
                    <v-btn 
                      icon 
                      @click="handleRemoveSticker"
                    >
                      <v-icon>
                        mdi-minus
                      </v-icon>
                    </v-btn>
                  </div>
                </v-container>
                <v-container>
                  <h3 class="pb-2">
                    Observações:
                  </h3>
                  <textarea 
                    class="textarea" 
                    placeholder="Alguma dúvida? Recado?"
                  ></textarea>
                </v-container>
              </v-card-text>
              <v-card-actions
                style="background:#dde3e8;"
                class="pa-3"
              >
                <v-spacer></v-spacer>
                <div class="btn-purchase d-inline-block">
                  <v-btn>Enviar</v-btn>
                </div>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "PurchaseScreen",
  data: () => ({
    checkbox: {
      vue: false,
      angular: false,
      react: false
    },
    stickersAmount: 0,
    textNote: '',
    objectToApi: {}
  }),
  methods: {
    handleRemoveSticker() {
      if (this.stickersAmount > 1) this.stickersAmount -= 1
    },
    handleAddSticker() {
      if (this.stickersAmount > 99999) return
      this.stickersAmount += 1
    }
  }
};
</script>

<style scoped>
.header-card{
  height: 130px;
  border-radius: 10% 14% 173% 130% / 0% 0% 191% 105%;
  overflow: hidden;
  background-color: #2f3675;
}

.header-card img{
  width: 105px;
  height: 105px;
}

.card-title{
  color: #FFFFFF;
  font-weight: 100;
  font-size: 20px;
}

.btn-purchase button{
  background-color:#2f3675 !important;
  color: #FFFFFF;
  border-radius: 6px;
}

.textarea {
  background-color: #dce3e8;
  color: #666666;
  padding: 1em;
  border-radius: 10px;
  border: 2px solid #2f3675;
  outline: none;
  font-family: "Heebo", sans-serif;
  font-weight: 500;
  font-size: 16px;
  line-height: 1.4;
  width: 100%;
  height: 100px;
  transition: all 0.2s;
  resize:none;
}

.textarea:hover {
  cursor: pointer;
  background-color: #eeeeee;
}

.textarea:focus {
  cursor: text;
  color: #333333;
  background-color: white;
  border-color: #333333;
}


@media (max-width: 1200px)
{
  .card-title{
    color: #FFFFFF;
    font-weight: 100;
    font-size: 15.5px;
  }
}
</style>
