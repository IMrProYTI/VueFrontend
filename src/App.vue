<template>
  <UApp>
    <div class="container m-auto space-y-4 my-8">
      <div class="flex space-x-2">
        <h1 class="w-fit">Учётные записи</h1>
        <UButton icon="i-heroicons:plus" />
      </div>
      <InfoPanel>Для указания нескольких меток для одной пары логин/пароль используйте разделитель ;</InfoPanel>
      <UTable :columns="columns" :data="data" class="flex-1" />
    </div>
  </UApp>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import type { TableColumn } from '@nuxt/ui';


interface IAccounts {
  label: string
  type: 'LOCAL' | 'LDAP'
  login: string
  password: string | null
}


const columns: TableColumn<IAccounts>[] = [
  {
    accessorKey: 'label',
    header: "Метка"
  },
  {
    accessorKey: 'type',
    header: "Тип записи"
  },
  {
    accessorKey: 'login',
    header: "Логин"
  },
  {
    accessorKey: 'password',
    header: "Пароль"
  }
];

const data = ref<IAccounts[]>([]);
</script>
