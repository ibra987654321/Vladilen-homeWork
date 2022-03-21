<template>
<data-form @add="addBlock"></data-form>
  <div class="card card-w70">
    <div v-if="blocks.length">
      <component
          v-for="block in blocks"
          :key="block.id"
          :is="block.type"
          v-bind="{value: block.value}"
      ></component>
    </div>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import dataForm from "@/components/FormGetData/DataForm";
import avatar from "@/components/Elements/avatar";
import title from "@/components/Elements/title";
import text from "@/components/Elements/text";
import subtitle from "@/components/Elements/subtitle";
export default {
  name: "PageHeader",
  components: {
    dataForm,
    avatar,
    title,
    text,
    subtitle
  },
  data() {
    return {
      blocks: []
    }
  },
  methods: {
    addBlock(params) {
      this.blocks.push(params)
    }
  }
}
</script>

<style scoped>

</style>
