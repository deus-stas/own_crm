<template>
    <div>
        <a-card
            :extra="extra"
            style="width: 100%;"
            @click="goToDetails"
        >   
            <div class="flex gap-5">
                <div class="w-1/5 flex gap-4">
                    <img class="w-[120px] h-[80px] rounded-2xl" :src="object.picture" alt="">
                    <div>
                        <h6 class="font-bold text-2xl text-slate-900">{{ object.name }}, {{ object.distance_from_mkad.value + ' км' }}</h6>
                        <p class="text-xl mt-8 text-slate-600">{{ object.district_id.value }}</p>
                        <p class="text-xl mt-8 text-slate-600">{{ object.id + ' | ' + object.date_create.date }}</p>
                    </div>
                </div>
                <div class="w-1/6">
                    <p class="text-xl text-slate-600">{{ object.deal_view.value }}</p>
                    <p class="text-xl text-slate-600">{{ object.price.currency + " " +  object.price.formated}}</p>
                    <div class="flex gap-4 items-center">
                        <img :src="object.broker.picture" class="w-10 h-10 rounded-full" alt="">
                        <p class="text-xl text-slate-600">{{ object.broker.fio }}</p>
                    </div>
                    <div class="!border border-solid !border-slate-900 !text-slate-900 p-4">{{ object.actual_date.value }}</div>
                </div>
                <div class="w-1/6 text-xl">
                    {{ object.house_number.name }}: {{ object.house_number.value }} | {{ object.flat_area.name }} : {{ object.flat_area.value }} | {{ object.floors_count.name }}: {{ object.floors_count.value }} | {{ object.rooms_count.name }}: {{ object.rooms_count.value }}
                </div>
                <div class="w-1/6">
                    <p class="text-xl text-slate-600">{{ object.owners[0] ? object.owners[0].fio : '' }}</p>
                    <p class="text-xl text-slate-600">{{ object.owners[0] ? object.owners[0].phone : '' }}</p>
                    <p class="text-xl text-slate-600">{{ object.owners[0] ? object.owners[0].email : '' }}</p>
                </div>
                <div class="w-1/6">
                    {{ object.status.value }}
                </div>
                <div class="w-1/6">
                    <div class="flex gap-5 items-center">
                        <p v-if="object.upload_avito.value === 'Да'">
                            <img class="w-10 h-10" src="http://level-crm.deus.team//img/sprite.svg#icon-avito" alt="">
                        </p>
                        <p v-if="object.upload_domclick.value === 'Да'">
                            <img class="w-10 h-10" src="http://level-crm.deus.team//img/sprite.svg#icon-domclick" alt="">
                        </p>
                        <p v-if="object.upload_yandex.value === 'Да'">
                            <img class="w-10 h-10" src="http://level-crm.deus.team//img/sprite.svg#icon-yandex" alt="">
                        </p>
                        <p v-if="object.upload_cian.value === 'да'">
                            <img class="w-10 h-10" src="http://level-crm.deus.team//img/sprite.svg#icon-cian" alt="">
                        </p>
                    </div>
                </div>
            </div>
        </a-card>      
    </div>
</template>
<script setup>
    import { ref } from 'vue'
    import { useRoute, useRouter } from 'vue-router';
    const router = useRouter();
    const route = useRoute();

    const props = defineProps({
        object: Object,
    })

    const open = ref(false);

    const showModal = () => {
        open.value = true;
    };

    const goToDetails = () => {
        router.push('/objects/' + props.object.id);
    }
</script>