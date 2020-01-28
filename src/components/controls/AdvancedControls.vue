<template>
  <div class="d-flex flex-row justify-content-between w-25">
    <div class="d-flex flex-column justify-content-between" style="min-width: 180px">
      <div class="d-flex flex-column justify-content-start">
        <p>Выберите набор:</p>
        <b-form-select v-model="set" :options="sets" size="sm" class="w-90"></b-form-select>
      </div>
      <div class="d-flex flex-column justify-content-end">
        <p>Название набора:</p>
        <b-form-input v-model="MyName" placeholder="Название" size="sm" class="w-90"></b-form-input>
      </div>
    </div>
    <div class="d-flex flex-column justify-content-between">
      <b-button disabled pill variant="primary">Disabled</b-button>
      <b-button pill variant="primary">Прокрутить</b-button>
      <div class="d-flex flex-row justify-content-between">
        <div class="d-flex flex-column">
          <p>Reels</p>
          <b-form-select v-model="reelsCount" :options="OneToEight" size="sm" class="w-90"></b-form-select>
        </div>
        <div class="d-flex flex-column">
          <p>Slots</p>
          <b-form-select v-model="slotsCount" :options="OneToEight" size="sm" class="w-90"></b-form-select>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AdvancedControls",
  data() {
    return {
      set: null,
      MyName: null,
      reelsCount: 3,
      slotsCount: 8,
      sets: [
        { value: null, text: "Выберите набор" },
        { value: "first", text: "Первый набор" },
        { value: "second", text: "Второй рабор" }
      ],
      OneToEight: [1, 2, 3, 4, 5, 6, 7, 8]
    };
  }
};
</script>

<style scoped>
  button, p {
    margin: 5px 10px;
  }
</style>
