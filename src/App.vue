<template>
    <div id="app">
        <div class="office">
            <Map 
                @onSelect="personSelected"
            />
            <SideMenu
                @onClose="personSelected"
                :selectedPerson="selectedPerson"
            />
        </div>
    </div>
</template>

<script>
import Map from "./components/Map.vue";
import SideMenu from "./components/SideMenu.vue";
import people from "@/assets/data/people.json";

export default {
    name: "App",
    components: {
        Map,
        SideMenu,
    },
    data() {
        return {
            people: [],
            selectedPerson: {},
        }
    },
    created() {
        this.loadPeople();
    },
    computed: {
        isSelected() {
            return Object.keys(this.selectedPerson).length != 0;
        }
    },
    methods: {
        loadPeople() {
            this.people = people;
        },
        personSelected(personId) {
            if (personId) {
                this.selectedPerson = this.people.find((it) => it._id === +personId);
            } else {
               this.selectedPerson = {}; 
            }
        },
    }
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: #2c3e50;
    background-color: #fafafa;
    padding: 24px;
    box-sizing: border-box;
}

html,
body,
#app {
    height: 100%;
}

* {
    box-sizing: border-box;
}

h3 {
    margin-top: 0px;
}

.office {
    display: grid;
    grid-template-columns: 1fr 320px;
    border-radius: 6px;
    border: 1px solid #ccd8e4;
    height: 100%;
    background: white;
    max-width: 1500px;
    margin: 0 auto;
}
</style>
