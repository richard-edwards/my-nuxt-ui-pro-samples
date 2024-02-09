<script setup lang="ts">

const results = [
    {
      rank: 1,
      team: {
        team_name: 'Team 1',
        total_earnings: 100
      },
      picks: [
        { player_name: 'Player a1' },
        { player_name: 'Player a2' },
        { player_name: 'Player a3' },
        { player_name: 'Player a4' },
        { player_name: 'Player a5' },
        { player_name: 'Player a6' },
        { player_name: 'Player a7' },
        { player_name: 'Player a8' },
        { player_name: 'Player a9' },
        { player_name: 'Player a10' },
        { player_name: 'Player a11' },
        { player_name: 'Player a12' }
      ]
    },
    {
      rank: 2,
      team: {
        team_name: 'Team 2',
        total_earnings: 200
      },
      picks: [
        { player_name: 'Player b1' },
        { player_name: 'Player b2' },
        { player_name: 'Player b3' },
        { player_name: 'Player b4' },
        { player_name: 'Player b5' },
        { player_name: 'Player b6' },
        { player_name: 'Player b7' },
        { player_name: 'Player b8' },
        { player_name: 'Player b9' },
        { player_name: 'Player b10' },
        { player_name: 'Player b11' },
        { player_name: 'Player b12' }
      ]
    },
]
  const columns = [
    {
      key: 'rank',
      label: '#'
    },
    {
      key: 'name',
      label: 'Team Name'
    },
    {
      key: 'total',
      label: 'Total'
    },
    {
      key: 'p1',
      label: 'Pick 1'
    },
    {
      key: 'p2',
      label: 'Pick 2'
    },
    {
      key: 'p3',
      label: 'Pick 3'
    },
    {
      key: 'p4',
      label: 'Pick 4'
    },
    {
      key: 'p5',
      label: 'Pick 5'
    },
    {
      key: 'p6',
      label: 'Pick 6'
    },
    {
      key: 'p7',
      label: 'Pick 7'
    },
    {
      key: 'p8',
      label: 'Pick 8'
    },
    {
      key: 'p9',
      label: 'Pick 9'
    },
    {
      key: 'p10',
      label: 'Pick 10'
    },
    {
      key: 'p11',
      label: 'Pick 11'
    },
    {
      key: 'p12',
      label: 'Pick 12'
    }
  ]
</script>

<template>
  <UPage>
    <UTable
      :columns="columns"
      :rows="results">
      <template #rank-data="{ row }">
        {{ row.rank }}
      </template>
      <template #name-data="{ row }">
        {{ row.team.team_name }}
      </template>
      <template #total-data="{ row }">
        {{ row.team.total_earnings }}
      </template>
      <template v-for="(n, index) of 12" :key="index" #[`p${n}-data`]="{ row }">
        {{ row.picks[index].player_name }}
      </template>
    </UTable>
  </UPage>
</template>
