<script setup lang="ts">
import type { ChartConfig } from '@/components/ui/chart'
import { VisAxis, VisStackedBar, VisXYContainer } from '@unovis/vue'
import {
  ChartContainer,
  ChartCrosshair,
  ChartTooltip,
  ChartTooltipContent,
  componentToString,
} from '@/components/ui/chart'

const chartData = [
  { date: new Date('2024-11-10'), sales: 186 },
  { date: new Date('2024-11-11'), sales: 305 },
  { date: new Date('2024-11-12'), sales: 237 },
  { date: new Date('2024-11-13'), sales: 273 },
  { date: new Date('2024-11-14'), sales: 209 },
  { date: new Date('2024-11-15'), sales: 214 },
  { date: new Date('2024-11-16'), sales: 190 },
]

type Data = typeof chartData[number]

const chartConfig = {
  sales: {
    label: 'Sales',
    color: 'hsl(var(--primary))',
  },
} satisfies ChartConfig

const formatDate = (d: number | Date) => {
  const date = new Date(d)
  return date.toLocaleDateString('en-US', {
    weekday: 'short',
    month: 'short',
    day: 'numeric'
  })
}
</script>

<template>
  <ChartContainer :config="chartConfig" class="h-[200px] w-full">
    <VisXYContainer :data="chartData">
      <VisStackedBar
        :x="(d: Data) => d.date"
        :y="(d: Data) => [d.sales]"
        :color="chartConfig.sales.color"
        :bar-min-width="8"
        :bar-max-width="20"
        :bar-padding="0"
        :rounded-corners="2"
      />
      <VisAxis
        type="x"
        :x="(d: Data) => d.date"
        :tick-format="(d: number) => {
          const date = new Date(d)
          return date.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })
        }"
      />
      <VisAxis type="y" />
      <ChartTooltip />
      <ChartCrosshair
        :template="componentToString(chartConfig, ChartTooltipContent, { labelFormatter: formatDate })"
        :color="[chartConfig.sales.color]"
      />
    </VisXYContainer>
  </ChartContainer>
</template>
