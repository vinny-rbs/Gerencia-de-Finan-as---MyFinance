<script setup>
import { ref } from 'vue'
import FlatField from '@/components/actions/fields/FlatField.vue'
import PrimaryButton from '@/components/actions/buttons/PrimaryButton.vue'
import DefaultNotification from '@/components/ui/DefaultNotification.vue';

//Codigos do modal de notificacao
const notificationMessage = ref('');
const showNotification = ref(false);

const hideNotification = () => {
    showNotification.value = false;
};

//Codigos da Transacao
const emit = defineEmits(['nova-transacao'])

const descricao = ref('')
const valor = ref(null)
const data = ref('')
const tipo = ref('')
const categoria = ref('')

function adicionarTransacao() {
    if (!valor.value || !data.value || !tipo.value || !categoria.value) {
        notificationMessage.value = "Por favor, preencha todos os campos.";
        showNotification.value = true;
        setTimeout(hideNotification, 3000);
        return
    }

    emit('nova-transacao', {
        descricao: descricao.value,
        valor: Number(valor.value),
        data: data.value,
        tipo: tipo.value,
        categoria: categoria.value
    })

    descricao.value = ''
    valor.value = null
    data.value = ''
    tipo.value = ''
    categoria.value = ''
}

</script>

<template>
    <div class="transacoes-container">
        <form @submit.prevent="adicionarTransacao" class="formulario">
            <FlatField v-model="tipo" info="Tipo de Transação" tag="select">
                <template #adicional>
                    <option value="" selected disabled>Tipo</option>
                    <option value="receita">Receita</option>
                    <option value="despesa">Despesa</option>
                </template>
            </FlatField>
            <FlatField v-model.number="valor" info="Valor (R$)" tag="input" type="number" placeholder="R$ 0,00" />
            <FlatField v-model="categoria" info="Categorias" tag="select">
                <template #adicional>
                    <option value="" selected disabled>Categorias</option>
                    <option value="alimentacao">Alimentação</option>
                    <option value="transporte">Transporte</option>
                    <option value="moradia">Moradia</option>
                    <option value="educacao">Educação</option>
                    <option value="lazer">Lazer</option>
                    <option value="saude">Saúde</option>
                    <option value="investimento">Investimentos</option>
                    <option value="salario">Salário</option>
                    <option value="outros">Outros</option>
                </template>
            </FlatField>
            <FlatField v-model="data" info="Data" tag="input" type="date" />
            <FlatField v-model="descricao" info="Descrição" tag="textarea" placeholder="Digite sua mensagem aqui..." />
            <PrimaryButton label="Adicionar" />
        </form>
    </div>
    <DefaultNotification :message="notificationMessage" :visible="showNotification"
        @update:visible="showNotification = $event" />
</template>

<style scoped>
.transacoes-container {
    width: 100%;
    min-height: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    gap: 1em;
    background: var(--color-light);
    border-radius: 12px;

    & h2 {
        font-size: 1.25rem;
        color: var(--color-dark-purble);
    }
}

.formulario {
    display: flex;
    flex-direction: column;
    gap: 1rem;

    & button {
        margin-top: 1em;
    }
}
</style>