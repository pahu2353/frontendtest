<template>
    <div class="sidebar">
        <!-- using a flexbox to allow users pick between all clicked history and current clicked -->
        <div class="header">
            History
        </div>
        <div class="clicked">

        </div>
    </div>
</template>

<script>

</script>

<style>
.sidebar {
    background-color: var(--sidebar-background);
    color: var(--sidebar-header-text);
    border-radius: 0.5rem;
    width: 20rem;
}
.header{
    background-color: var(--sidebar-header-background); 
    border-radius: 0.5rem 0.5rem 0 0;
    font-weight: bold;

    /* center text vertically and horizontally */
    display: flex;
    text-align: center;
    justify-content: center;
    align-items: center;

    /* size and placing on page */
    height: 4rem;
    gap: 1rem;
}


</style>