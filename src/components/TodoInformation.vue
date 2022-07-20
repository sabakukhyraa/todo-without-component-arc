<template>

    <div class="counter">
        <div>
        <small class="green">Tamamlanan: {{ completedCount }}</small>
        <small class="red">Tamamlanmamış: {{ uncompletedCount }}</small>
        </div>
        <small>Şuanda {{ itemCount }} TODO var.</small>
        
    </div>        

</template>

<script>
    export default {
        props: ["itemCount", "completedCount", "uncompletedCount"]
    }
</script>