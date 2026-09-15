<template>
  <footer class="footer">

    <!-- Logo -->
    <div class="logo">
      Vitrine
    </div>

    <!-- Links -->
    <nav class="footer-links">
      <a href="#">About</a>
      <a href="#">Contact</a>
      <a href="#">Terms</a>
      <a href="#">Privacy</a>
      <a href="#">GitHub</a>
    </nav>

    <!-- Copyright -->
    <div class="copyright">
      © 2026 Vitrine. All rights reserved.
    </div>

  </footer>
</template>

<script>
export default {
  name: "FooterBar"
};
</script>

<style scoped>
.footer {
  width: 100%;
  height: 56px;
  min-height: 56px;

  display: flex;
  align-items: center;

  padding: 0 28px;
  margin-top: 20px;

  background-color: #f8f9fc;
  border-top: 1px solid #e5e7eb;

  font-family: Arial, sans-serif;

  box-sizing: border-box;
}

/* Logo */

.logo {
  font-size: 18px;
  font-weight: 700;

  color: #111827;

  position: absolute;
  left: 28px;
}

/* Links */

.footer-links {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);

  display: flex;
  align-items: center;

  gap: 24px;
}

.footer-links a {
  color: #374151;

  font-size: 14px;

  text-decoration: underline;

  transition: color 0.2s;
}

.footer-links a:hover {
  color: #111827;
}

/* Copyright */

.copyright {
  margin-left: auto;

  color: #4b5563;

  font-size: 14px;

  white-space: nowrap;
}
</style>