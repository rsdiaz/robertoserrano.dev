<template>
  <div>
    <Animation />
    <TopAngle />
    <ResponsiveNav />
    <Header :title="title" :subtitle="subtitle" />
    <h1>Pagina contacto</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: 'Contacto',
      subtitle: 'Pagina de contacto',
    }
  },
}
</script>
