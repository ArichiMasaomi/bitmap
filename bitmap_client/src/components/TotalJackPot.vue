<script>
import {mapState} from "vuex";
import {formatEther} from "ethers";
import {calculate_virus_to_profit} from "@/utils";

export default {
  name: "TotalJackPot",
  methods: {formatEther},
  computed: {
    ...mapState(['players']),
    value: {
      get() {
        let result = 0;
        for (let i = 0; i < this.players.length; i++) {
          result += this.players[i].init_virus;
        }


        const profit = calculate_virus_to_profit(result);
        const res = Math.floor(Number(profit) * 0.88).toString()
        console.log("TotalJackPot", res);
        return res;

      },

    }
  }
}
</script>

<template>
  <p style="color: #ff961b">{{ formatEther(value) }}</p>
</template>

<style scoped>

</style>