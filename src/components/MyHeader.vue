<template>
    <div class="header">
        <div class="header-logo">
            <img src="../assets/logosvg.svg">
        </div>
        <div class="header-links">
            <router-link class="link" to="/">Форма</router-link>
            <router-link class="link" to="/info">Превью</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MyHeader'
}

</script>

<style scoped>
.header {
    display: flex;
    align-items: center;
    width: 1366px;
    height: 76px;
    margin: 0 auto;
    border-bottom: 1px solid rgba(17, 17, 17, 0.1);
}

.header-logo {
    padding: 24px 0 24px 92px;
}

.header-links {
    margin-left: 473px;
}

.link {
    color: rgba(17, 17, 17, 0.48);
    text-decoration: none;
    margin-right: 24px;
}
</style>