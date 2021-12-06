 <template>
  <BContainer>
    <bank-table :banks="banks" @remove="remove($event)" @update="edit($event)"/>
    <BModal v-model="modalShow" lazy hide-footer hide-header>
      <bank-update :bank="updating" @input="update($event)" @cancel="cancelEdit()"/>
    </BModal>
  </BContainer>
</template>

<script>

</script>

<style scoped>

</style>
