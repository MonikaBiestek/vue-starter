<template>
    <div>
        <div class="header"><h2>Witaj {{ username }}!</h2><button class="button button-outline" @click="$emit('logout')">Wyloguj</button> </div>
    </div>
</template>

<script>
    export default {
        props: ['username']
    }
</script>
<style>
.header {
  display: flex;
}

.header h2 {
  flex-grow: 1;
}
.header button {
margin-right: 100px;
}
</style>

