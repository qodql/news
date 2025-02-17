<template>
  <footer class="footer">
    <div class="footer-content">
      <p>&copy; {{ currentYear }} All rights reserved.</p>
      <div class="footer-social">
        <a href="#" aria-label="Facebook" class="social-link">Facebook</a>
        <a href="#" aria-label="Twitter" class="social-link">Twitter</a>
        <a href="#" aria-label="Instagram" class="social-link">Instagram</a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterView",
  computed: {
    currentYear() {
      return new Date().getFullYear();
    }
  }
};
</script>

<style lang="scss">
.footer {
  max-width: 480px;
  margin: 60px auto;
  background-color: #007BFF;
  color: #fff;
  padding: 20px;
  text-align: center;
  font-size: 14px;
  .footer-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
  }
  .footer-social {
    display: flex;
    gap: 15px;
    .social-link {
      color: #ECECEC;
      text-decoration: none;
      &:hover {
        color: #fff;
      }
    }
  }
}
</style>
