<template>
    <div class="sidebar">
        <div class="header">
            <p>History (<span class="toggle" @click="toggleCurrent">{{ showCurrent ? 'Hide Currently Clicked' : 'Show Currently Clicked' }}</span>)</p>
        </div>

        <div class="body">
            <div class="history">
                <h4>History:</h4>
                <li v-for="coordinate in coordinateHistory" :key="coordinate">
                    {{ coordinate }}
                </li>
            </div>
            <div class="current" v-if="showCurrent">
                <h4>Currently Clicked:</h4>
                <li v-for="coordinate in Array.from(currentlyClicked)" :key="coordinate">
                    {{ coordinate }}
                </li>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    props: {
        coordinateHistory: {
            type: Array,
        },
        currentlyClicked: {
            type: Set,
            default: () => new Set(), // default empty set value to prevent issues with iterating through undefined
        }
    },
    data(){
        return{
            showCurrent: false,
        }
    },
    methods: {
        toggleCurrent(){
            this.showCurrent = !this.showCurrent;
        }
    }
}
</script>

<style>
.sidebar {
    background-color: var(--sidebar-background);
    color: var(--sidebar-header-text);
    border-radius: 0.5rem;
    width: 25rem;
    overflow: auto;
    height: 100%;
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

.body{
    display: flex;
    flex-direction: row;
    text-align: center; 
    height: 100%;
}

.history, .current {
    list-style-type: ordered;
    flex-grow: 1;
    height: 100%;
}

.toggle:hover {
    cursor: pointer;
    color: var(--background-colour);
}

</style>