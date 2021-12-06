<template>
  <div>
    <div>
      <BButton size="sm" variant="primary" @click="create(item.id)" class="mr-2">
        + Добавить банк
      </BButton>
      <BTable striped hover :items="banks" :fields="fields">
        <template #cell(action)="{item}">
          <BButton size="sm" variant="success" @click="update(item.id)" class="mr-2">
            Редактировать
          </BButton>
          <BButton size="sm" variant="danger" @click="remove(item.id)" class="mr-2">
            Удалить
          </BButton>
        </template>
      </BTable>
    </div>
    <div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BankTable',
  props: {
    banks: Array
  },
  data () {
    return {
      fields: [
        {
          key: 'name',
          label: 'Название банка'
        },
        {
          key: 'rate',
          label: 'Процентная ставка в год (%)'
        },
        {
          key: 'maxLoan',
          label: 'Максимальный займ ($)'
        },
        {
          key: 'minPayment',
          label: 'Минимальный первый взнос ($)'
        },
        {
          key: 'term',
          label: 'Срок ссуды (мес)'
        },
        {
          key: 'action',
          label: 'Действие'
        }
      ]
    }
  },
  methods: {
    remove (id) {
      this.$emit('remove', id)
    },
    create () {
      this.$emit('create')
    },
    update (id) {
      this.$emit('update', id)
    }
  }
}
</script>
