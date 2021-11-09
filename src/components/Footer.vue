<template>
    <th scope="row" colspan="2">Total productos</th>
        <td>{{CantidadTotal}}</td>
        <td>
            <button class="btn btn-danger btn-sm" id="vaciar-carrito" @click="vaciar">
                vaciar todo
            </button>
        </td>
    <td class="font-weight-bold">$ <span>{{totalPrecio}}</span></td>
</template>

<script>
import { computed } from '@vue/reactivity'
import { useStore } from 'vuex'
export default {
    name: 'Footer',
    setup(){
        const store = useStore();

        const CantidadTotal = computed(()=> store.getters.totalCantidad);

        const totalPrecio = computed(()=> store.getters.totalPrecio);
        //entre llaves porque es algo que se ejecuta no que retorna
        const vaciar = () => {store.commit('vaciarCarrito')}

        return {CantidadTotal, totalPrecio,vaciar};
    }
}
</script>

