<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
      status: ["all","alive", "dead", "unknown"],
    };
  },
};
</script>

<template>
  <div class="container py-4">
    <div class="d-flex justify-content-between">
      <div>
        <select @change="$emit('filter')" v-model="store.selectedStatus">
          <option :value="curStatus" v-for="curStatus in status">
            {{ curStatus }}
          </option>
        </select>
      </div>

      <p>Mostrati {{ store.cardsList.length }} elementi</p>
    </div>
  </div>
</template>