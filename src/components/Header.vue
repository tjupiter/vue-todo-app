<template>
    <header>
        <h1 class="py-3 text-4xl font-bold">{{title}}</h1>
    </header>
</template>

<script>


export default {
    name: 'Header',
    props: {
        title: String,
    }
}
</script>
