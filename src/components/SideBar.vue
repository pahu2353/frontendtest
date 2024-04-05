<template>
    <div class="sidebar">
        <div class="header">
            History (Show Currently Clicked)
        </div>
        <div class="history">
            <li v-for="coordinate in coordinateHistory" :key="coordinate">
                {{ coordinate }}
            </li>
        </div>
    </div>
</template>

<script>
export default{
    props: {
        coordinateHistory: {
            type: Array,
        }
    },
}
</script>

<style>
.sidebar {
    background-color: var(--sidebar-background);
    color: var(--sidebar-header-text);
    border-radius: 0.5rem;
    width: 25rem;
    overflow: auto;
    max-height: calc(100vh - 10.5rem);
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
.history{
    list-style-type: ordered;
    overflow-y: auto;
    flex-grow: 1;
}


</style>