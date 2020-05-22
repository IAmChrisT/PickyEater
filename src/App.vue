<template>
  <div id="app">
		<GameCardsStack
			:cards="visibleCards"
			@cardAccepted="handleCardAccepted"
			@cardRejected="handleCardRejected"
			@cardSkipped="handleCardSkipped"
			@hideCard="removeCardFromDeck"
		/>
  </div>
</template>

<script>
import GameCardsStack from "./components/GameCardsStack";
import axios from "axios"

export default {
  name: "App",
  components: {
    GameCardsStack,
    axios
  },

  data() {

    let url = "maps.googleapis.com/maps/api/place/nearbysearch/json?location=52.5639745,-0.1409372&radius=1500&type=restaurant&keyword=cruise&key=AIzaSyDK-ZlG3tEsqG6-2H2-qYaEhjkIXvW8ETo"
   let config = {
      headers: {
        Access-Control-Allow-Origin: "*",
      }
    }

    axios.get(url, 
      .then(function (response) {
        // handle success
        console.log(response);
      })
      .catch(function (error) {
        // handle error
        console.log(JSON.stringify(error));
      })
      .finally(function () {
        // always executed
        console.log("completed api")
      });


          
    



    return {
      visibleCards: ["Chiquitos", "Bella Italia", "Frankie & Bennies"]
    };
  },


  methods: {
    handleCardAccepted() {
      console.log("handleCardAccepted");
    },
    handleCardRejected() {
      console.log("handleCardRejected");
    },
    handleCardSkipped() {
      console.log("handleCardSkipped");
    },
    removeCardFromDeck() {
      this.visibleCards.shift();
    }
  }
};
</script>

<style lang="scss">
@import "./styles/mixins.scss";

#app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    text-align: center;
    height: 60vh;
    display: flex;
    align-items: center;
    justify-items: center;
    width: calc(100vw - 16px);
}

#header {
 text-align: center;
  width: calc(100vw - 32px);
}
</style>
