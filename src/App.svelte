<script>
  import Header from './components/Header.svelte';
  import About from './components/About.svelte';
  import Product from './components/Product.svelte';
  import Footer from './components/Footer.svelte';
</script>

<div class="min-h-screen flex flex-col bg-stone-50 text-stone-900 antialiased font-sans">
  <Header />
  <main class="flex-grow">
    <About />
    <Product />
  </main>
  <Footer />
</div>
