<template>
  <div class="page">
    <h4>Thêm Liên hệ</h4>
    <ContactForm @submit:contact="addContact" />
    <p>{{ message }}</p>
  </div>
</template>

<script>
import ContactService from '@/services/contact.service'
import ContactForm from '../components/ContactForm.vue'
export default {
  components: {
    ContactForm
  },
  data() {
    return {
      message: ''
    }
  },
  methods: {
    async addContact(data) {
      try {
        await ContactService.create(data)
        this.message = 'Liên hệ được thêm thành công.'
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>
