<template>
  <section class="footer-section">
    <div class="footer-text">
      <div class="main-message">Thanks for stopping by.</div>
      <div class="sub-message">Let’s get in touch!</div>
    </div>
    <div class="contact-icons">
      <a href="mailto:vivienjam@gmail.com" target="_blank" aria-label="Email">
        <i class="fas fa-envelope"></i>
      </a>
      <a href="https://linkedin.com/in/vivien-jamba" target="_blank" aria-label="LinkedIn">
        <i class="fab fa-linkedin"></i>
      </a>
    </div>
  </section>
</template>

<style scoped>
.footer-section {
  background-color: #16409c;
  color: white;
  padding: 4rem 2rem;
  text-align: center;
}

.footer-text {
  margin-bottom: 2rem;
}

.main-message {
  font-size: 3rem;
  font-weight: 700;
}

.sub-message {
  font-size: 1.5rem;
  font-weight: 400;
  margin-top: 0.5rem;
}

.contact-icons {
  display: flex;
  justify-content: center;
  gap: 2rem;
}

.contact-icons a {
  font-size: 2.2rem;
  color: white;
  transition: opacity 0.3s ease;
}

.contact-icons a:hover {
  opacity: 0.7;
}
</style>
