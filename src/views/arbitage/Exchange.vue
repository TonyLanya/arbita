<template>
  <div>
    <v-container grid-list-xl fluid pt-2>
      <v-layout row wrap>
        <v-flex xs4 v-for="(card, index) in cards" :key="index">
          <draggable :options="{group: 'card'}">
            <v-card>
              <v-card-actions>
                <v-btn fab small color="primary" @click="addCard()">
                  <v-icon>add</v-icon>
                </v-btn>
                <v-btn fab small color="error" @click="removeCard()">
                  <v-icon>remove</v-icon>
                </v-btn>
              </v-card-actions>
              <v-card-text>
                <h1>This is card {{ index }}.</h1>
                <v-text-field name="input-1" v-model="card.text" label="Test Text"></v-text-field>
              </v-card-text>
            </v-card>
          </draggable>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  data() {
    return {
      cards: [
        {
          text: ""
        }
      ]
    };
  },
  mounted() {},
  methods: {
    addCard() {
      this.cards.push({});
    },
    removeCard(index) {
      if (this.cards.length == 1) {
        this.$toast.warn({
          title: "Info",
          message: "Can't remove it"
        });
        return;
      }
      this.cards.splice(index, 1);
    }
  },
  components: {
    draggable
  }
};
</script>