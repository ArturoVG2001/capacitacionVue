<script setup>
//const props = defineProps(['title', 'id', 'body', 'colorText']);
//console.log(props.title);

//const emit = defineEmits(['cambiarFavoritoNombre']);

defineProps({
    title: String,
    id:Number,
    body: {
        type:String,
        default:'Sin descripcion',
    },
    cambiarFavorito: Function,
});

</script>

<template>
    <div class="card">
        <div class="card-body" :class="`text-${colorText}`">
            <h5 class="card-tittle">{{id}} - {{ title }}</h5>
            <p>{{ body }}</p>
            <button @click="cambiarFavorito(title)" class="btn btn-outline-primary">Favorito</button>
        </div>
    </div>
</template>