<script setup>
    import { defineProps, defineEmits } from 'vue';

    const props = defineProps({
        number1: Number,
        number2: Number,
        operation: String,
    }); 

const emits = defineEmits(['updateNumber1', 'updateNumber2', 'updateOperation']);
</script>
<template>
    <div class="row mb-3">
        <div class="col-md-4">
            <input
                type="number"
                :value="number1"
                @input="$emit('updateNumber1', +$event.target.value)"
                class="form-control"
                placeholder="Digite o primeiro número"
            />
        </div>
    
        <div class="col-md-4">
            <select
                :value="operation"
                @change="$emit('updateOperation', $event.target.value)"
                class="form-select"
            >
                <option value="add">Adição (+)</option>
                <option value="subtract">Subtração (-)</option>
                <option value="multiply">Multiplicação (*)</option>
                <option value="divide">Divisão (/)</option>
            </select>
        </div>
    
        <div class="col-md-4">
        <input
            type="number"
            :value="number2"
            @input="$emit('updateNumber2', +$event.target.value)"
            class="form-control"
            placeholder="Digite o segundo número"
        />
        </div>
    </div>
</template>