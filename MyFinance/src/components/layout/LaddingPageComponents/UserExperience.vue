<script setup>

import UserCard from '@/components/ui/UserCard.vue'

</script>

<template>
    <div class="user__content">
        <h1 class="user__title">O que nossos usuários dizem</h1>
        <div class="user__comment">
            <UserCard
                description="&#34Excelente ferramenta para controle financeiro. Mudou completamente minha relação com dinheiro.&#34"
                name="Ana Silva" occupation="Empresária"
                image="https://images.unsplash.com/photo-1659353219716-699803846194?q=80&w=2531&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" />
            <UserCard description="&#34Interface intuitiva e relatórios muito úteis. Recomendo para todos!&#34"
                name="Carlos Santos" occupation="Engenheiro"
                image="https://images.unsplash.com/photo-1650398119372-9e23168b219b?q=80&w=2370&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" />
            <UserCard description="&#34Finalmente consegui organizar minhas finanças de forma eficiente.&#34"
                name="Marina Costa" occupation="Advogada"
                image="https://images.unsplash.com/photo-1666717716011-11772efecc92?q=80&w=2487&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" />
        </div>
    </div>
</template>

<style scoped>
.user__content {
    min-height: 50vh;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    background-color: var(--color-light);
    margin: 4em;
    padding: clamp(1.5em, 1vw, 3em);
    border-radius: 24px;
    box-shadow: 4px 4px 18px rgba(150, 150, 150, 0.15);
    gap: 1.5em;
}

.user__comment {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

@media (max-width: 884px) and (max-height: 1280px) {

    .user__content {
        margin: 2.5em;
        gap: 1em;
    }

    .user__comment {
        flex-direction: column;
        gap: 3em;
    }
}
</style>