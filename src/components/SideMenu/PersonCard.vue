<template>
    <div class="person">
        <div class="person__photo">
            <img
                :src="person.picture"
                alt="photo"
            />
        </div>
        <div class="person__info">
            <div class="person__info-header">
                <div class="person__info-name">
                    <b>{{ person.name }} ({{ person.age }})</b> 
                </div>
                <div class="person__info-email">
                    <a :href="'mailto:' + person.email">
                        <Mail class="mail-icon"/> 
                    </a>
                </div>
            </div>
            <div class="person__info-registrated">
                <b>Дата регистрации:</b><br>
                {{ formatedDate }}
            </div>
            <div class="person__info-about"><b>О себе: </b>{{ person.about }}</div>
        </div>
    </div>
</template>

<script>
import Mail from "@/assets/icons/mail.svg";

export default {
    components: {
        Mail,
    },
    props: {
        person: {
            type: Object,
            default: null,
        },
    },
    computed: {
        formatedDate() {
            const [ year, month, day, time ] = this.person.registered.split(/-|T/);
            return `${day}.${month}.${year} в ${time}`;
        },
    },
};
</script>

<style scoped>
.person {
    display: grid;
    grid-template-columns: 50px 1fr;
    grid-gap: 8px;
}

.person__photo img {
    height: 50px;
    width: 50px;
    border-radius: 50%;
}

.person__info {
    display: grid;
    grid-gap: 8px;
}

.person__info-header {
    padding: 0 10px;
    background-color: #FFCCFF;
    border-radius: 10px;
    height: 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.mail-icon {
    height: 20px;
}

.person__info-registrated {
    padding: 5px 10px;
    background-color: #CCCCFF;
    border-radius: 10px;
}

.person__info-about {
    padding: 5px 10px;
    background-color: #FFCCCC;
    border-radius: 10px;
}

</style>
