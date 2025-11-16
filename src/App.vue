<script setup lang="ts">
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import SalesChart from '@/components/SalesChart.vue'
</script>

<template>
  <div class="min-h-screen bg-background p-8">
    <div class="max-w-7xl mx-auto space-y-8">
      <div class="space-y-2">
        <h1 class="text-4xl font-bold">Komunite Dashboard</h1>
        <p class="text-muted-foreground">Vue + Vite + Tailwind + shadcn-vue</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <Card>
          <CardHeader>
            <CardTitle>Total Users</CardTitle>
            <CardDescription>Active community members</CardDescription>
          </CardHeader>
          <CardContent>
            <div class="text-3xl font-bold">1,234</div>
          </CardContent>
        </Card>

        <Card>
          <CardHeader>
            <CardTitle>Posts</CardTitle>
            <CardDescription>Published this month</CardDescription>
          </CardHeader>
          <CardContent>
            <div class="text-3xl font-bold">456</div>
          </CardContent>
        </Card>

        <Card>
          <CardHeader>
            <CardTitle>Engagement</CardTitle>
            <CardDescription>Average per post</CardDescription>
          </CardHeader>
          <CardContent>
            <div class="text-3xl font-bold">89%</div>
          </CardContent>
        </Card>

        <Card>
          <CardHeader>
            <CardTitle>Sales Overview</CardTitle>
            <CardDescription>Last 7 days performance</CardDescription>
          </CardHeader>
          <CardContent>
            <SalesChart />
          </CardContent>
        </Card>
      </div>

      <Card>
        <CardHeader>
          <CardTitle>Quick Actions</CardTitle>
          <CardDescription>Common tasks and operations</CardDescription>
        </CardHeader>
        <CardContent class="flex gap-2">
          <Button>Create Post</Button>
          <Button variant="secondary">View Analytics</Button>
          <Button variant="outline">Settings</Button>
        </CardContent>
      </Card>
    </div>
  </div>
</template>
