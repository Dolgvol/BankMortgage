<template>
  <BForm @submit="submit">
    <BFormGroup
      label="Название банка"
    >
      <BInput v-model="form.name"/>
    </BFormGroup>

    <BFormGroup
      label="Процентная ставка в год"
    >
      <BInput v-model="form.rate"/>
    </BFormGroup>

    <BFormGroup
      label="Максимальный займ"
    >
      <BInput v-model="form.maxLoan"/>
    </BFormGroup>

    <BFormGroup
      label="Минимальный первый взнос"
    >
      <BInput v-model="form.minPayment"/>
    </BFormGroup>

    <BFormGroup
      label="Срок ссуды"
    >
      <BInput v-model="form.term"/>
    </BFormGroup>

    <BFormGroup>
      <BButton type="submit" variant="primary">Отправить</BButton>
      <BButton @click="cancel()">Отмена</BButton>
    </BFormGroup>
  </BForm>
</template>

<script>
export default {
  name: 'BankUpdate',
  props: {
    bank: Object
  },
  data () {
    return {
      form: {
        name: this.bank.name,
        rate: this.bank.rate,
        maxLoan: this.bank.maxLoan,
        minPayment: this.bank.minPayment,
        term: this.bank.term
      }
    }
  },
  methods: {
    submit (event) {
      event.preventDefault()
      this.$emit('input', { id: this.bank.id, data: this.form })
    },
    cancel () {
      this.$emit('cancel')
    }
  }
}
</script>
