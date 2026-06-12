<template>
  <div class="flex h-screen w-full bg-[#F3F4F6] text-[#111827] font-sans overflow-hidden">
    <!-- Sidebar Navigation -->
    <aside class="w-64 bg-[#1F2937] text-gray-300 flex flex-col border-r border-gray-700">
      <div class="p-6 flex items-center space-x-3 border-b border-gray-700 bg-[#111827]">
        <div class="w-8 h-8 bg-blue-600 rounded flex items-center justify-center">
          <span class="text-white font-bold">AC</span>
        </div>
        <span class="text-white font-semibold text-lg tracking-tight">会计档案管理系统</span>
      </div>
      <nav class="flex-1 py-4 text-sm">
        <div class="px-4 py-2 text-xs font-bold text-gray-500 uppercase tracking-wider">基础管理</div>
        <button @click="currentView = '档案查询'" :class="['flex w-full items-center px-6 py-2 transition-colors', currentView === '档案查询' ? 'bg-blue-700 text-white border-r-4 border-blue-400' : 'hover:bg-gray-800']"><span class="mr-3">{{ currentView === '档案查询' ? '■' : '□' }}</span> 档案查询</button>
        <a href="#" class="flex items-center px-6 py-2 hover:bg-gray-800 transition-colors"><span class="mr-3">□</span> 凭证移交</a>
        <button @click="currentView = '账簿登记'" :class="['flex w-full items-center px-6 py-2 transition-colors', currentView === '账簿登记' ? 'bg-blue-700 text-white border-r-4 border-blue-400' : 'hover:bg-gray-800']"><span class="mr-3">{{ currentView === '账簿登记' ? '■' : '□' }}</span> 账簿登记</button>
        <div class="px-4 py-4 text-xs font-bold text-gray-500 uppercase tracking-wider">高级管理</div>
        <a href="#" class="flex items-center px-6 py-2 hover:bg-gray-800 transition-colors"><span class="mr-3">□</span> 审计监督</a>
        <a href="#" class="flex items-center px-6 py-2 hover:bg-gray-800 transition-colors"><span class="mr-3">□</span> 销毁管理</a>
        <a href="#" class="flex items-center px-6 py-2 hover:bg-gray-800 transition-colors"><span class="mr-3">□</span> 权限配置</a>
      </nav>
      <div class="p-4 border-t border-gray-700 text-xs flex justify-between items-center">
        <span>版本 v2.4.0</span>
        <span class="text-green-400">● 在线</span>
      </div>
    </aside>

    <!-- Main Content Area -->
    <main class="flex-1 flex flex-col h-full">
      <!-- Header Bar -->
      <header class="h-14 bg-white border-b border-gray-200 flex items-center justify-between px-6 shadow-sm">
        <div class="flex items-center space-x-4">
          <span class="text-gray-400">首页 / {{ currentView }}</span>
        </div>
      </header>

      <!-- Content Container -->
      <div class="p-6 flex-1 flex flex-row space-x-6 overflow-hidden">
        <!-- Main Content -->
        <div class="flex-1 flex flex-col space-y-4 overflow-hidden">
          
          <!-- View: 档案查询 -->
          <div v-if="currentView === '档案查询'" class="flex-1 flex flex-col space-y-4 overflow-hidden">
            <!-- Stats -->
            <div class="grid grid-cols-4 gap-4">
              <div class="bg-white border border-gray-200 p-4 shadow-sm rounded">
                <div class="text-xs text-gray-500 uppercase">档案总数</div>
                <div class="text-2xl font-mono font-bold text-gray-800">142,850</div>
              </div>
              <div class="bg-white border border-gray-200 p-4 shadow-sm rounded">
                <div class="text-xs text-gray-500 uppercase">待审核</div>
                <div class="text-2xl font-mono font-bold text-orange-600">128</div>
              </div>
              <div class="bg-white border border-gray-200 p-4 shadow-sm rounded">
                <div class="text-xs text-gray-500 uppercase">存储空间</div>
                <div class="text-2xl font-mono font-bold text-gray-800">64.2%</div>
              </div>
              <div class="bg-white border border-gray-200 p-4 shadow-sm rounded">
                <div class="text-xs text-gray-500 uppercase">借阅次数</div>
                <div class="text-2xl font-mono font-bold text-gray-800">1,024</div>
              </div>
            </div>
            <!-- Data Grid (Archive Query) -->
            <div class="bg-white border border-gray-200 flex-1 overflow-hidden shadow-sm flex flex-col rounded">
                <table class="w-full text-xs text-left">
                  <thead class="bg-gray-50 border-b border-gray-200 text-gray-600 font-bold uppercase">
                    <tr><th class="p-3">档案编号</th><th class="p-3">摘要</th><th class="p-3">状态</th></tr>
                  </thead>
                  <tbody class="divide-y divide-gray-100 overflow-y-auto">
                    <tr class="hover:bg-blue-50 transition-colors cursor-pointer">
                      <td class="p-3 font-mono font-bold">AR-20231201-001</td>
                      <td class="p-3">购进办公设备一批及相关配件支付费用</td>
                      <td class="p-3"><span class="bg-green-100 text-green-700 px-2 py-0.5 rounded-full text-[10px] font-bold">已归档</span></td>
                    </tr>
                  </tbody>
                </table>
            </div>
          </div>

          <!-- View: 账簿登记 -->
          <div v-if="currentView === '账簿登记'" class="flex-1 flex flex-col overflow-hidden bg-white border border-gray-200 rounded shadow-sm">
             <!-- Header -->
             <div class="p-4 border-b border-gray-100 flex items-center justify-between">
                <h2 class="font-bold text-gray-700 text-sm">账簿登记表</h2>
                <button class="bg-blue-600 text-white text-xs px-4 py-1.5 rounded font-medium hover:bg-blue-700">+ 新增登记</button>
             </div>
             <!-- Data Grid -->
             <div class="flex-1 overflow-y-auto">
                <table class="w-full text-xs text-left">
                  <thead class="bg-gray-50 border-b border-gray-200 text-gray-600 font-bold uppercase sticky top-0">
                    <tr>
                      <th class="p-3">账簿名称</th><th class="p-3">类型</th><th class="p-3">登记日期</th><th class="p-3">状态</th><th class="p-3">经办人</th>
                    </tr>
                  </thead>
                  <tbody class="divide-y divide-gray-100">
                    <tr v-for="i in 5" :key="i" class="hover:bg-blue-50 transition-colors cursor-pointer">
                      <td class="p-3 font-semibold text-gray-800">2024年度现金日记账-0{{i}}</td>
                      <td class="p-3 text-gray-600">日记账</td>
                      <td class="p-3">2024-05-1{{i}}</td>
                      <td class="p-3"><span :class="['px-2 py-0.5 rounded-full text-[10px] font-bold', i % 2 === 0 ? 'bg-blue-100 text-blue-700' : 'bg-gray-100 text-gray-700']">{{ i % 2 === 0 ? '已登记' : '登记中' }}</span></td>
                      <td class="p-3">管理员</td>
                    </tr>
                  </tbody>
                </table>
             </div>
             <!-- Pagination Footer -->
             <footer class="border-t border-gray-100 bg-gray-50 px-4 py-3 flex items-center justify-between text-xs rounded-b">
               <div class="text-gray-500">显示第 1 至 5 条，共 50 条记录</div>
               <div class="flex space-x-1">
                 <button class="px-2 py-1 border border-gray-300 rounded bg-white hover:bg-gray-50 text-gray-400">上一页</button>
                 <button class="px-2 py-1 border border-blue-600 rounded bg-blue-600 text-white font-bold">1</button>
                 <button class="px-2 py-1 border border-gray-300 rounded bg-white hover:bg-gray-50">2</button>
                 <button class="px-2 py-1 border border-gray-300 rounded bg-white hover:bg-gray-50">3</button>
                 <span class="px-2 py-1 text-gray-400">...</span>
                 <button class="px-2 py-1 border border-gray-300 rounded bg-white hover:bg-gray-50">10</button>
                 <button class="px-2 py-1 border border-gray-300 rounded bg-white hover:bg-gray-50 text-gray-400">下一页</button>
               </div>
             </footer>
          </div>
        
        </div>

        <!-- Right Side Activities Panel -->
        <aside v-if="currentView !== '账簿登记'" class="w-80 bg-white border border-gray-200 rounded shadow-sm flex flex-col">
           <div class="p-4 border-b border-gray-100 font-bold text-gray-700 text-sm">最近活动</div>
           <div class="flex-1 p-4 space-y-4 overflow-y-auto">
              <!-- Activities -->
              <div class="flex items-center p-3 rounded-lg hover:bg-gray-50 border border-gray-100 transition">
                 <div class="w-8 h-8 rounded-full bg-blue-50 flex items-center justify-center mr-3 text-lg">📁</div>
                 <div>
                    <div class="text-xs font-bold text-gray-800">档案 #12345 归档</div>
                    <div class="text-[10px] text-gray-500">2分钟前</div>
                 </div>
              </div>
           </div>
        </aside>
      </div>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
const currentView = ref('档案查询');
</script>
