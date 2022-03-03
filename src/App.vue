<template>
  <div id="app">
    <h1>{{ titulo }}</h1>
    <table class="flex-table">
      <thead>
        <tr>
          <th>Setor</th>
          <th>Mesa</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="setor in setores" :key="setor.nome">
          <td>
            <div class="setor">
              <font-awesome-icon :icon="['fas', 'arrows-up-down-left-right']" />
              <p>{{ setor.nome }}</p>
            </div>
          </td>
          <td>
            <div v-for="mesa in mesas" :key="mesa.mesa">
              <template v-if="mesa.setor === setor.nome">
                <template v-if="mesa.status === 'd'">
                  <button style="background-color: green">
                    {{ mesa.mesa }}
                  </button>
                </template>
                <template v-if="mesa.status === 'o'">
                  <button style="background-color: red">{{ mesa.mesa }}</button>
                </template>
              </template>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "Teste",
      setores: [{ nome: "Dentro" }, { nome: "Fora" }],
      mesas: [
        { mesa: 1, status: "d", setor: "Dentro" },
        { mesa: 2, status: "o", setor: "Dentro" },
        { mesa: 3, status: "d", setor: "Dentro" },
        { mesa: 4, status: "d", setor: "Dentro" },
        { mesa: 1, status: "o", setor: "Fora" },
        { mesa: 2, status: "d", setor: "Fora" },
        { mesa: 3, status: "d", setor: "Fora" },
      ],
    };
  },
};
</script>

<style>
.flex-table {
  display: flex;
  flex-direction: column;
  border: 1px solid #ccc;
  background: #fff;
}
.flex-table thead {
  color: #fff;
  background: #C5831A;
}

.flex-table thead tr,
.flex-table tbody tr {
  display: flex;
}
.flex-table tbody tr + tr {
  border-top: 1px solid #ccc;
}

.flex-table thead tr th,
.flex-table tbody tr td {
  display: flex;
  flex: 1;
  padding: 0.5em;
}

.flex-table button {
  margin: 5px 5px;
  display: inline-block;
  font-weight: 400;
  text-align: center;
  vertical-align: middle;
  user-select: none;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  border-radius: 0.25rem;
  transition: all 60ms ease-in;
  border: 1px solid #ccc;
  color: #ffffff;
  cursor: pointer;
}

.setor {
  display: flex;
  align-items: center;
  gap: 10px;
}
</style>
