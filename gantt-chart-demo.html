<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>硬體產品開發專案甘特圖</title>
    <!-- 載入 Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* 使用 Inter 字體 */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f4f7f9;
        }
        /* 自定義甘特圖的日期單元格寬度 */
        .day-cell {
            width: 40px; /* 每個日期的固定寬度 */
            min-width: 40px;
            height: 60px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            font-size: 0.75rem;
            border-left: 1px solid #e5e7eb;
            user-select: none;
        }
        /* 專案名稱列的樣式 */
        .task-name-cell {
            width: 180px; /* 專案名稱的固定寬度 */
            min-width: 180px;
            padding: 0.5rem 1rem;
            display: flex;
            align-items: center;
            font-weight: 600;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            border-right: 1px solid #e5e7eb;
        }
        /* 任務行 (Row) 的樣式 */
        .task-row {
            display: flex;
            border-bottom: 1px solid #e5e7eb;
        }
        /* 甘特圖時間軸容器，使用 flex 實現橫向滾動 */
        #gantt-timeline {
            overflow-x: auto;
        }
        /* 任務條容器 */
        .gantt-bar-container {
            position: relative;
            height: 60px;
            display: flex;
            align-items: center;
        }
        /* 任務條本身的樣式 */
        .gantt-bar {
            position: absolute;
            height: 70%;
            border-radius: 0.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.1);
            transition: transform 0.2s, opacity 0.2s;
            cursor: pointer;
            display: flex;
            align-items: center;
            padding: 0 0.5rem;
            color: white;
            font-weight: 500;
            font-size: 0.875rem;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
            white-space: nowrap;
        }
        /* 任務條懸停效果 */
        .gantt-bar:hover {
            transform: translateY(-2px);
            opacity: 0.95;
        }
        /* 滾動條美化 (Webkit) */
        #gantt-timeline::-webkit-scrollbar {
            height: 10px;
        }
        #gantt-timeline::-webkit-scrollbar-thumb {
            background-color: #9ca3af;
            border-radius: 10px;
        }
        #gantt-timeline::-webkit-scrollbar-track {
            background-color: #e5e7eb;
        }
        /* 動作按鈕的樣式 */
        .action-btn {
            background: none;
            border: none;
            font-size: 1rem;
            cursor: pointer;
            padding: 0 0.3rem;
            transition: color 0.15s;
        }
        .delete-btn { color: #ef4444; } /* red-500 */
        .edit-btn { color: #3b82f6; } /* blue-500 */
        .save-btn { color: #10b981; } /* emerald-500 */
        .cancel-btn { color: #6b7280; } /* gray-500 */
    </style>
</head>
<body class="p-4 sm:p-8">
    <div class="max-w-7xl mx-auto bg-white shadow-xl rounded-xl p-4 sm:p-6 lg:p-8">
        <h1 class="text-3xl font-extrabold text-gray-800 mb-6 border-b pb-3">硬體產品開發專案甘特圖 (可編輯)</h1>
        <!-- 主要甘特圖容器 -->
        <div class="flex">
            <!-- 縱軸：任務名稱列表 -->
            <div id="task-list" class="flex-shrink-0 bg-gray-50 border-r border-gray-200 rounded-l-lg shadow-inner">
                <!-- 標題佔位符 -->
                <div class="task-name-cell font-bold text-gray-600 bg-gray-100 sticky top-0 z-10 rounded-tl-xl border-b border-gray-200">任務名稱 (縱軸)</div>
                <!-- 任務名稱將在這裡渲染 -->
            </div>
            <!-- 橫軸：日期時間軸與甘特圖區域 -->
            <div id="gantt-timeline" class="flex-grow rounded-r-lg">
                <!-- 橫軸：日期標題 -->
                <div id="date-header" class="flex sticky top-0 z-10 bg-white border-b border-gray-200">
                    <!-- 日期單元格將在這裡渲染 -->
                </div>
                <!-- 甘特圖內容區域 -->
                <div id="gantt-content">
                    <!-- 任務行內容將在這裡渲染 -->
                </div>
            </div>
        </div>
        <!-- 專案設定與任務管理區塊 -->
        <div class="mt-8 pt-6 border-t border-gray-200">
            <h2 class="text-xl font-semibold text-gray-700 mb-4">專案設定</h2>
            <div class="flex flex-col sm:flex-row sm:items-end gap-4 mb-6">
                <div class="flex flex-col">
                    <label for="projectStartDateInput" class="text-sm font-medium text-gray-700 mb-1">
                        設定專案起始日 (橫軸起點)
                    </label>
                    <input type="date" id="projectStartDateInput" class="px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500">
                </div>
                <!-- 專案資訊顯示區 -->
                <div id="project-info" class="text-gray-600"></div>
            </div>
            <!-- 任務管理介面 -->
            <h2 class="text-xl font-semibold text-gray-700 mb-4">任務管理 (新增 / 編輯 / 刪除)</h2>
            <!-- 新增任務表單 -->
            <div id="addTaskForm" class="bg-gray-50 p-4 rounded-lg shadow-inner mb-6">
                <h3 class="font-bold text-gray-700 mb-3 text-lg">新增任務</h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4">
                    <!-- 任務名稱 -->
                    <input type="text" id="newTaskName" placeholder="任務名稱 (必填)" class="col-span-1 md:col-span-4 px-3 py-2 border rounded-md" required>
                    <!-- 開始日期 -->
                    <div class="flex flex-col">
                        <label for="newTaskStartDate" class="text-xs text-gray-500 mb-1">開始日期</label>
                        <input type="date" id="newTaskStartDate" class="px-3 py-2 border rounded-md" required>
                    </div>
                    <!-- 持續天數 -->
                    <div class="flex flex-col">
                        <label for="newTaskDuration" class="text-xs text-gray-500 mb-1">持續天數 (天)</label>
                        <input type="number" id="newTaskDuration" min="1" value="5" class="px-3 py-2 border rounded-md" required>
                    </div>
                    <!-- 顏色選擇 (已移除中文描述) -->
                    <div class="flex flex-col">
                        <label for="newTaskColor" class="text-xs text-gray-500 mb-1">階段 / 顏色</label>
                        <select id="newTaskColor" class="px-3 py-2 border rounded-md">
                            <option value="bg-blue-600">Pre-EVT</option>
                            <option value="bg-purple-600">EVT</option>
                            <option value="bg-red-600" selected>DVT</option>
                            <option value="bg-yellow-600">PVT</option>
                            <option value="bg-green-600">MP</option>
                        </select>
                    </div>
                    <!-- 新增按鈕 -->
                    <button id="addTaskButton" class="col-span-1 sm:col-span-2 md:col-span-4 bg-indigo-600 text-white py-2 rounded-lg hover:bg-indigo-700 transition duration-150 shadow-md font-semibold">
                        新增任務到甘特圖
                    </button>
                </div>
            </div>
            <!-- 現有任務摘要列表 -->
            <div id="currentTasksList" class="bg-white border border-gray-200 rounded-lg shadow-sm">
                <div class="p-3 border-b bg-gray-50 font-bold text-gray-700">當前任務清單</div>
                <div id="tasksListContainer" class="max-h-60 overflow-y-auto">
                    <!-- 任務摘要將由 JS 渲染在這裡 -->
                </div>
            </div>
        </div>
    </div>
    <script>
        // --- 設定與資料 ---
        const CELL_WIDTH = 40; // 每個日期的單元格寬度 (px)
        const MS_PER_DAY = 1000 * 60 * 60 * 24;
        // 硬體產品開發階段的顏色配置 (已移除中文描述)
        const phaseColors = [
            { value: "bg-blue-600", label: "Pre-EVT" },
            { value: "bg-purple-600", label: "EVT" },
            { value: "bg-red-600", label: "DVT" },
            { value: "bg-yellow-600", label: "PVT" },
            { value: "bg-green-600", label: "MP" },
        ];
        // 專案任務資料 (縱軸內容) - 僅保留 EVT, DVT, PVT, MP 相關任務
        let tasks = [
            // 已移除 "產品規格定義與架構設計"
            { id: Date.now() + 2, name: "Pre-EVT 雛形製作", start: "2025-12-08", duration: 10, color: "bg-blue-600" },
            { id: Date.now() + 3, name: "EVT 樣品測試與驗證", start: "2025-12-20", duration: 15, color: "bg-purple-600" },
            { id: Date.now() + 4, name: "DVT 結構與可靠性測試", start: "2026-01-05", duration: 12, color: "bg-red-600" },
            { id: Date.now() + 5, name: "PVT 小批量試產準備", start: "2026-01-18", duration: 8, color: "bg-yellow-600" },
            { id: Date.now() + 6, name: "MP 大量生產導入", start: "2026-01-26", duration: 5, color: "bg-green-600" },
            // 已移除 "產品文件最終審核"
        ];
        // --- 日期處理輔助函式 (保持不變) ---
        function parseDate(dateString) {
            if (!dateString) return new Date();
            const [year, month, day] = dateString.split('-').map(Number);
            return new Date(Date.UTC(year, month - 1, day));
        }
        function daysBetween(date1, date2) {
            const start = Math.min(date1.getTime(), date2.getTime());
            const end = Math.max(date1.getTime(), date2.getTime());
            return Math.round(Math.abs(end - start) / MS_PER_DAY);
        }
        function signedDaysBetween(date1, date2) {
            return Math.round((date2.getTime() - date1.getTime()) / MS_PER_DAY);
        }
        function findEarliestTaskStart(tasks) {
            if (tasks.length === 0) {
                const today = new Date();
                today.setUTCHours(0, 0, 0, 0);
                return today;
            }
            let minDate = parseDate(tasks[0].start);
            tasks.forEach(task => {
                const taskStart = parseDate(task.start);
                if (taskStart < minDate) {
                    minDate = taskStart;
                }
            });
            return minDate;
        }
        function findLatestTaskEnd(tasks) {
            if (tasks.length === 0) {
                const today = new Date();
                today.setUTCHours(0, 0, 0, 0);
                return today;
            }
            let maxDate = parseDate(tasks[0].start); 
            tasks.forEach(task => {
                const taskStart = parseDate(task.start);
                const taskEnd = new Date(taskStart.getTime() + (task.duration - 1) * MS_PER_DAY);
                if (taskEnd > maxDate) {
                    maxDate = taskEnd;
                }
            });
            return new Date(maxDate.getTime() + MS_PER_DAY);
        }
        /**
         * 顏色選擇的 HTML 輔助函式 (已移除中文描述)
         */
        function generateColorOptions(selectedColor) {
            return phaseColors.map(c => 
                `<option value="${c.value}" ${c.value === selectedColor ? 'selected' : ''}>${c.label}</option>`
            ).join('');
        }
        // --- 任務管理函式 ---
        function addTask() {
            const nameInput = document.getElementById('newTaskName');
            const startDateInput = document.getElementById('newTaskStartDate');
            const durationInput = document.getElementById('newTaskDuration');
            const colorInput = document.getElementById('newTaskColor');
            const name = nameInput.value.trim();
            const start = startDateInput.value;
            const duration = parseInt(durationInput.value);
            const color = colorInput.value;
            if (!name) { alertModal("錯誤", "任務名稱不能為空。"); return; }
            if (!start) { alertModal("錯誤", "請設定任務的開始日期。"); return; }
            if (isNaN(duration) || duration < 1) { alertModal("錯誤", "持續天數必須大於 0。"); return; }
            const newTask = {
                id: Date.now(), 
                name: name,
                start: start,
                duration: duration,
                color: color,
            };
            tasks.push(newTask);
            nameInput.value = '';
            const defaultDate = document.getElementById('projectStartDateInput').value || new Date().toISOString().substring(0, 10);
            startDateInput.value = defaultDate; 
            initializeGanttChart();
        }
        function deleteTask(taskId) {
            tasks = tasks.filter(task => task.id !== taskId);
            initializeGanttChart();
        }
        function startEditTask(taskId) {
            const task = tasks.find(t => t.id === taskId);
            if (!task) return;
            const taskRow = document.getElementById(`task-row-${taskId}`);
            if (!taskRow) return;
            // 渲染內嵌編輯表單 (使用更新後的 generateColorOptions)
            taskRow.innerHTML = `
                <div class="flex flex-col sm:flex-row flex-grow gap-2 items-center p-2 w-full">
                    <input type="text" id="edit-name-${taskId}" value="${task.name}" class="p-1 border border-blue-300 rounded-md w-full sm:w-1/3 text-sm" placeholder="任務名稱">
                    <input type="date" id="edit-start-${taskId}" value="${task.start}" class="p-1 border rounded-md w-full sm:w-1/5 text-sm">
                    <input type="number" id="edit-duration-${taskId}" value="${task.duration}" min="1" class="p-1 border rounded-md w-full sm:w-[80px] text-sm">
                    <select id="edit-color-${taskId}" class="p-1 border rounded-md w-full sm:flex-grow text-sm">
                        ${generateColorOptions(task.color)}
                    </select>
                </div>
                <div class="flex space-x-2 flex-shrink-0 p-2">
                    <button class="action-btn save-btn" data-task-id="${taskId}" title="儲存變更">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path d="M7.707 10.707a1 1 0 01-1.414-1.414l3-3a1 1 0 011.414 0l3 3a1 1 0 01-1.414 1.414L10 8.414l-2.293 2.293z" /><path fill-rule="evenodd" d="M10 2a1 1 0 00-1 1v7a1 1 0 102 0V3a1 1 0 00-1-1z" clip-rule="evenodd" /></svg>
                    </button>
                    <button class="action-btn cancel-btn" data-task-id="${taskId}" title="取消編輯">
                         <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 011.414 1.414L11.414 10l4.293 4.293a1 1 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" /></svg>
                    </button>
                </div>
            `;
            // 附加儲存/取消事件
            taskRow.querySelector('.save-btn').addEventListener('click', () => saveTaskEdit(taskId));
            taskRow.querySelector('.cancel-btn').addEventListener('click', () => cancelEditTask());
        }
        function saveTaskEdit(taskId) {
            const nameInput = document.getElementById(`edit-name-${taskId}`);
            const startDateInput = document.getElementById(`edit-start-${taskId}`);
            const durationInput = document.getElementById(`edit-duration-${taskId}`);
            const colorInput = document.getElementById(`edit-color-${taskId}`);
            const name = nameInput.value.trim();
            const start = startDateInput.value;
            const duration = parseInt(durationInput.value);
            const color = colorInput.value;
            if (!name || !start || isNaN(duration) || duration < 1) {
                alertModal("編輯錯誤", "請確保任務名稱、開始日期及持續天數均有效。");
                return;
            }
            const taskIndex = tasks.findIndex(t => t.id === taskId);
            if (taskIndex === -1) return;
            tasks[taskIndex] = {
                ...tasks[taskIndex],
                name,
                start,
                duration,
                color
            };
            initializeGanttChart();
        }
        function cancelEditTask() {
            renderCurrentTasksList(); 
        }
        function renderCurrentTasksList() {
            const container = document.getElementById('tasksListContainer');
            container.innerHTML = '';   
            if (tasks.length === 0) {
                container.innerHTML = '<p class="p-3 text-gray-500 text-sm">目前沒有任務，請新增。</p>';
                return;
            }
            tasks.forEach((task, index) => {
                const taskElement = document.createElement('div');
                taskElement.id = `task-row-${task.id}`;
                taskElement.className = `flex items-center justify-between p-3 border-b ${index % 2 === 0 ? 'bg-white' : 'bg-gray-50'} min-h-[4rem]`;   
                // 找到對應的階段名稱來顯示
                const phase = phaseColors.find(c => c.value === task.color);
                // 這裡的 phaseLabel 已經在 phaseColors 中被簡化為只有縮寫
                const phaseLabel = phase ? phase.label : '未知階段';
                taskElement.innerHTML = `
                    <div class="flex flex-col sm:flex-row sm:items-center space-x-0 sm:space-x-2 truncate">
                        <div class="flex items-center space-x-2 flex-shrink-0">
                            <span class="w-2 h-2 rounded-full ${task.color}" title="${phaseLabel}"></span>
                            <span class="text-sm font-medium text-gray-800 truncate" title="${task.name}">${task.name}</span>
                        </div>
                        <span class="text-xs text-gray-500 ml-4 sm:ml-0">${task.start} / ${task.duration} 天</span>
                    </div>
                    <div class="flex space-x-1 flex-shrink-0">
                        <button class="action-btn edit-btn" data-task-id="${task.id}" title="編輯任務">
                            <!-- Edit Icon -->
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                              <path stroke-linecap="round" stroke-linejoin="round" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" />
                            </svg>
                        </button>
                        <button class="action-btn delete-btn" data-task-id="${task.id}" title="刪除任務">
                            <!-- Trash Can SVG Icon -->
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                              <path stroke-linecap="round" stroke-linejoin="round" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
                            </svg>
                        </button>
                    </div>
                `;
                container.appendChild(taskElement);
            });
            // 附加事件監聽器
            container.querySelectorAll('.edit-btn').forEach(button => {
                button.addEventListener('click', (e) => {
                    const taskId = parseInt(e.currentTarget.dataset.taskId);
                    startEditTask(taskId);
                });
            });
            container.querySelectorAll('.delete-btn').forEach(button => {
                button.addEventListener('click', (e) => {
                    const taskId = parseInt(e.currentTarget.dataset.taskId);
                    deleteTask(taskId);
                });
            });
        }
        // --- 渲染函式 (保持不變) ---
        function renderTimeAxis(startDate, totalDays) {
            const dateHeader = document.getElementById('date-header');
            dateHeader.innerHTML = '';
            dateHeader.style.minWidth = `${totalDays * CELL_WIDTH}px`;
            let currentDate = new Date(startDate.getTime());
            const today = new Date();
            today.setUTCHours(0, 0, 0, 0);
            for (let i = 0; i < totalDays; i++) {
                const isToday = daysBetween(currentDate, today) === 0;
                const isWeekend = currentDate.getUTCDay() === 0 || currentDate.getUTCDay() === 6;
                const dateDiv = document.createElement('div');
                dateDiv.className = `day-cell ${isWeekend ? 'bg-gray-100 text-gray-400' : 'bg-white text-gray-700'} ${isToday ? 'border-2 border-indigo-400 font-bold' : ''}`;
                dateDiv.innerHTML = `
                    <span class="text-[0.6rem]">${currentDate.getUTCMonth() + 1}/${currentDate.getUTCDate()}</span>
                    <span class="font-semibold">${currentDate.toLocaleDateString('zh-TW', { weekday: 'short' })}</span>
                `;
                dateHeader.appendChild(dateDiv);
                currentDate = new Date(currentDate.getTime() + MS_PER_DAY);
            }
        }
        function renderGanttContent(tasks, projectStartDate, totalDays) {
            const taskList = document.getElementById('task-list');
            const ganttContent = document.getElementById('gantt-content');
            ganttContent.innerHTML = '';
            ganttContent.style.minWidth = `${totalDays * CELL_WIDTH}px`;
            while (taskList.children.length > 1) { 
                taskList.removeChild(taskList.lastChild);
            }
            tasks.forEach((task, index) => {
                const taskStart = parseDate(task.start);
                const taskEnd = new Date(taskStart.getTime() + (task.duration - 1) * MS_PER_DAY);
                // 1. 渲染任務名稱 (縱軸)
                const nameCell = document.createElement('div');
                nameCell.className = `task-name-cell border-gray-200 ${index % 2 === 0 ? 'bg-white' : 'bg-gray-50'}`;
                nameCell.innerHTML = `<span class="truncate">${task.name}</span>`;
                taskList.appendChild(nameCell);
                // 2. 渲染任務條 (橫軸內容)
                const startOffsetDays = signedDaysBetween(projectStartDate, taskStart);
                const leftPosition = startOffsetDays * CELL_WIDTH;
                const barWidth = task.duration * CELL_WIDTH;
                const taskRowDiv = document.createElement('div');
                taskRowDiv.className = `task-row ${index % 2 === 0 ? 'bg-white' : 'bg-gray-50'}`;
                taskRowDiv.style.minWidth = `${totalDays * CELL_WIDTH}px`;
                const gridDiv = document.createElement('div');
                gridDiv.className = "flex w-full h-full";
                gridDiv.style.minWidth = `${totalDays * CELL_WIDTH}px`;
                for (let i = 0; i < totalDays; i++) {
                    const currentDate = new Date(projectStartDate.getTime() + i * MS_PER_DAY);
                    const isWeekend = currentDate.getUTCDay() === 0 || currentDate.getUTCDay() === 6;
                    const gridCell = document.createElement('div');
                    gridCell.className = `day-cell border-0 ${isWeekend ? 'bg-gray-100/50' : 'bg-white/50'}`;
                    gridDiv.appendChild(gridCell);
                }
                const barContainer = document.createElement('div');
                barContainer.className = "gantt-bar-container w-full absolute top-0 left-0";
                barContainer.style.width = `${totalDays * CELL_WIDTH}px`;
                const barDiv = document.createElement('div');
                barDiv.className = `gantt-bar ${task.color} hover:shadow-lg`;
                barDiv.style.left = `${leftPosition}px`;
                barDiv.style.width = `${barWidth}px`;
                barDiv.title = `任務: ${task.name}\n開始: ${task.start}\n持續: ${task.duration} 天\n結束: ${taskEnd.toISOString().substring(0, 10)}`;
                const visibleTaskName = task.name.substring(0, Math.floor(barWidth / 80) * 8) + (barWidth > 80 && task.name.length > 8 ? '...' : '');
                barDiv.textContent = visibleTaskName || '';
                barContainer.appendChild(barDiv);
                taskRowDiv.appendChild(gridDiv);
                taskRowDiv.appendChild(barContainer);
                ganttContent.appendChild(taskRowDiv);
            });
        }
        function initializeGanttChart() {
            const inputElement = document.getElementById('projectStartDateInput');
            const newTaskStartDateInput = document.getElementById('newTaskStartDate');
            if (tasks.length === 0) {
                const today = new Date();
                today.setUTCHours(0, 0, 0, 0);
                const isoDate = today.toISOString().substring(0, 10);
                inputElement.value = inputElement.value || isoDate;
                newTaskStartDateInput.value = newTaskStartDateInput.value || isoDate;
            } else {
                const defaultStartDate = findEarliestTaskStart(tasks);
                const isoDate = defaultStartDate.toISOString().substring(0, 10);
                inputElement.value = inputElement.value || isoDate;
                newTaskStartDateInput.value = newTaskStartDateInput.value || isoDate;
            }
            const projectStartDate = parseDate(inputElement.value);
            const maxTaskEndDate = findLatestTaskEnd(tasks);
            let chartEndDate = maxTaskEndDate;
            if (maxTaskEndDate.getTime() < projectStartDate.getTime()) {
                chartEndDate = new Date(projectStartDate.getTime() + MS_PER_DAY);
            }
            const totalDays = signedDaysBetween(projectStartDate, chartEndDate) + 1;
            renderTimeAxis(projectStartDate, totalDays);
            renderGanttContent(tasks, projectStartDate, totalDays);
            renderCurrentTasksList();
            document.getElementById('project-info').innerHTML = `
                圖表起始日: <span class="font-medium text-indigo-600">${projectStartDate.toISOString().substring(0, 10)}</span><br>
                圖表總天數: <span class="font-medium text-indigo-600">${totalDays}</span> 天<br>
                任務數量: <span class="font-medium text-indigo-600">${tasks.length}</span> 個
            `;
        }
        // 頁面載入完成後運行並註冊事件監聽器
        window.onload = () => {
            initializeGanttChart();   
            document.getElementById('projectStartDateInput').addEventListener('change', initializeGanttChart);
            document.getElementById('addTaskButton').addEventListener('click', addTask);
        };
        function alertModal(title, message) {
            console.warn(`[${title}]: ${message}`);
            const infoDiv = document.getElementById('project-info');
            infoDiv.innerHTML = `<span class="font-bold text-red-500">${title}: ${message}</span>`;
            setTimeout(() => { initializeGanttChart(); }, 3000);
        }
    </script>
</body>
</html>
