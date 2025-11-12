# 活动管理系统文档

## 更新日期
2025-11-09

## 🎯 系统概述

为York Region Caring Lions Club管理后台添加了完整的活动管理系统（Events Management），管理员可以通过后台界面轻松创建、编辑、删除和管理所有活动信息。

---

## 📋 功能特性

### ✅ 核心功能

#### 1️⃣ **活动CRUD操作**
- ✅ **Create** - 创建新活动
- ✅ **Read** - 查看活动列表
- ✅ **Update** - 编辑现有活动
- ✅ **Delete** - 删除活动

#### 2️⃣ **双语支持**
- ✅ 英文标题和描述
- ✅ 中文标题和描述
- ✅ 完整的中英文内容管理

#### 3️⃣ **活动状态管理**
- ✅ Upcoming（即将举行）
- ✅ Ongoing（进行中）
- ✅ Completed（已完成）
- ✅ Cancelled（已取消）

#### 4️⃣ **特色活动标记**
- ✅ Featured Event（特色活动）标记
- ✅ 在活动列表中显示星标

#### 5️⃣ **数据导出**
- ✅ 一键导出CSV文件
- ✅ 包含所有活动信息

---

## 🗄️ 数据库表结构

### Events Table Schema

| 字段名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `id` | text | 唯一活动ID | ✅ |
| `title_en` | text | 英文标题 | ✅ |
| `title_zh` | text | 中文标题 | ✅ |
| `description_en` | rich_text | 英文描述 | ✅ |
| `description_zh` | rich_text | 中文描述 | ✅ |
| `event_date` | datetime | 活动日期 (YYYY-MM-DD) | ✅ |
| `event_time` | text | 活动时间 (如: 10:00 AM - 4:00 PM) | ✅ |
| `location` | text | 活动地点/场所 | ✅ |
| `status` | text | 活动状态 (upcoming/ongoing/completed/cancelled) | ✅ |
| `is_featured` | bool | 是否为特色活动 | ✅ |
| `image_url` | text | 活动图片URL | ❌ |
| `registration_url` | text | 报名链接 | ❌ |
| `created_at` | datetime | 创建时间（自动） | 自动 |
| `updated_at` | datetime | 更新时间（自动） | 自动 |

---

## 🖥️ 管理后台界面

### 访问路径
```
URL: /admin.html
导航: Admin Dashboard → Events 标签
```

### 界面布局

#### 1️⃣ **活动列表视图**
```
┌─────────────────────────────────────────────────────────┐
│  Events Management                    [Add New] [Export]│
├─────────────────────────────────────────────────────────┤
│ Date    │ Title (EN/ZH) │ Location │ Time │ Status │...│
├─────────────────────────────────────────────────────────┤
│ Nov 23  │ Winter Food   │ Markham  │10 AM │Upcoming│★  │
│         │ 冬季食物募捐   │ Civic    │-4 PM │        │   │
├─────────────────────────────────────────────────────────┤
│ Nov 30  │ Youth Lead... │ Virtual  │2 PM  │Upcoming│   │
│         │ 青年领导力...  │ (Zoom)   │-5 PM │        │   │
└─────────────────────────────────────────────────────────┘
```

#### 2️⃣ **活动编辑器（模态框）**
```
┌─────────────────────────────────────────────────────────┐
│  Add New Event / Edit Event                          [X]│
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Title (English) *          Title (Chinese) *          │
│  [________________]         [________________]         │
│                                                         │
│  Description (English) *                                │
│  [_________________________________________________]   │
│                                                         │
│  Description (Chinese) *                                │
│  [_________________________________________________]   │
│                                                         │
│  Event Date *         Event Time *                      │
│  [2025-11-23]        [10:00 AM - 4:00 PM]             │
│                                                         │
│  Location *                                             │
│  [Markham Civic Centre, 101 Town Centre Blvd]         │
│                                                         │
│  Status *            Featured *      Image URL          │
│  [Upcoming ▼]       [No ▼]          [https://...]     │
│                                                         │
│  Registration URL (Optional)                            │
│  [https://...]                                         │
│                                                         │
│                                     [Cancel] [Save]    │
└─────────────────────────────────────────────────────────┘
```

---

## 📝 使用说明

### 创建新活动

#### 步骤1：登录管理后台
```
1. 访问 /admin.html
2. 用户名: admin
3. 密码: CaringLions@YR2025!Secure
4. 点击 Login
```

#### 步骤2：进入活动管理
```
1. 点击顶部导航的 "Events" 标签
2. 查看当前所有活动列表
```

#### 步骤3：创建新活动
```
1. 点击 "Add New Event" 按钮
2. 填写活动信息：
   
   必填项：
   - Title (English): 英文活动标题
   - Title (Chinese): 中文活动标题
   - Description (English): 英文活动描述
   - Description (Chinese): 中文活动描述
   - Event Date: 活动日期（使用日期选择器）
   - Event Time: 活动时间（如: 10:00 AM - 4:00 PM）
   - Location: 活动地点
   - Status: 活动状态（默认Upcoming）
   
   可选项：
   - Featured: 是否为特色活动
   - Image URL: 活动图片链接
   - Registration URL: 报名链接

3. 点击 "Save Event" 保存
```

#### 示例数据
```
英文标题: Winter Food Drive
中文标题: 冬季食物募捐

英文描述: Help us collect non-perishable food items for families in need during the winter months.
中文描述: 帮助我们在冬季为有需要的家庭收集非易腐食品。

活动日期: 2025-11-23
活动时间: 10:00 AM - 4:00 PM
地点: Markham Civic Centre, 101 Town Centre Blvd
状态: Upcoming
特色活动: Yes
```

### 编辑现有活动

```
1. 在活动列表中找到要编辑的活动
2. 点击该活动右侧的 "Edit" 按钮
3. 修改任何需要更新的信息
4. 点击 "Save Event" 保存更改
```

### 删除活动

```
1. 在活动列表中找到要删除的活动
2. 点击该活动右侧的 "Delete" 按钮（垃圾桶图标）
3. 在确认对话框中点击 "OK" 确认删除
```

**注意**：删除是软删除（标记为deleted=true），数据仍保留在数据库中。

### 导出活动数据

```
1. 在Events标签页
2. 点击 "Export CSV" 按钮
3. 浏览器会自动下载events.csv文件
4. 可用Excel或Google Sheets打开
```

---

## 🔄 活动状态说明

### Upcoming（即将举行）
- **说明**：活动尚未开始
- **显示**：在events.html首页显示
- **颜色**：蓝色徽章
- **用途**：默认新创建的活动状态

### Ongoing（进行中）
- **说明**：活动正在进行
- **显示**：在events.html显示（可选）
- **颜色**：绿色徽章
- **用途**：多日活动或长期项目

### Completed（已完成）
- **说明**：活动已结束
- **显示**：不在首页显示（可在存档查看）
- **颜色**：灰色徽章
- **用途**：活动结束后标记

### Cancelled（已取消）
- **说明**：活动已取消
- **显示**：不显示或标注取消
- **颜色**：红色徽章
- **用途**：因故取消的活动

---

## 🎯 前端events.html集成

### 当前状态
events.html当前使用**静态HTML硬编码**的活动信息。

### 未来升级（可选）
将events.html改为动态从API读取活动数据：

```javascript
// events.html 底部添加
<script>
async function loadEvents() {
    try {
        const response = await fetch('tables/events?status=upcoming&limit=10&sort=event_date');
        const data = await response.json();
        
        if (data.data && data.data.length > 0) {
            const eventsGrid = document.querySelector('.events-grid');
            eventsGrid.innerHTML = data.data.map(event => `
                <div class="event-card">
                    <div class="event-date">
                        <span class="date-day">${new Date(event.event_date).getDate()}</span>
                        <span class="date-month">
                            <span class="en">${new Date(event.event_date).toLocaleDateString('en-US', {month: 'short'}).toUpperCase()}</span>
                            <span class="zh" style="display: none;">${new Date(event.event_date).getMonth() + 1}月</span>
                        </span>
                        <span class="date-year">${new Date(event.event_date).getFullYear()}</span>
                    </div>
                    <div class="event-content">
                        <h3 class="event-title">
                            <span class="en">${event.title_en}</span>
                            <span class="zh" style="display: none;">${event.title_zh}</span>
                        </h3>
                        <p class="event-description">
                            <span class="en">${event.description_en}</span>
                            <span class="zh" style="display: none;">${event.description_zh}</span>
                        </p>
                        <div class="event-meta">
                            <span><i class="fas fa-map-marker-alt"></i> ${event.location}</span>
                            <span><i class="fas fa-clock"></i> ${event.event_time}</span>
                        </div>
                        <a href="${event.registration_url || 'contact.html'}" class="btn btn-small">
                            <span class="en">Register Now</span>
                            <span class="zh" style="display: none;">立即报名</span>
                        </a>
                    </div>
                </div>
            `).join('');
        }
    } catch (error) {
        console.error('Error loading events:', error);
    }
}

// 页面加载时调用
document.addEventListener('DOMContentLoaded', loadEvents);
</script>
```

---

## 📊 API端点

### 获取活动列表
```http
GET /tables/events?limit=100&sort=event_date

查询参数：
- limit: 返回数量（默认100）
- sort: 排序字段（event_date, -event_date）
- status: 筛选状态（upcoming, ongoing, completed, cancelled）
- page: 页码

响应：
{
  "data": [...],
  "total": 6,
  "page": 1,
  "limit": 100
}
```

### 获取单个活动
```http
GET /tables/events/{event_id}

响应：
{
  "id": "xxx",
  "title_en": "Winter Food Drive",
  "title_zh": "冬季食物募捐",
  ...
}
```

### 创建活动
```http
POST /tables/events
Content-Type: application/json

{
  "title_en": "New Event",
  "title_zh": "新活动",
  "description_en": "...",
  "description_zh": "...",
  "event_date": "2025-12-01",
  "event_time": "10:00 AM - 4:00 PM",
  "location": "...",
  "status": "upcoming",
  "is_featured": false
}

响应：201 Created
```

### 更新活动
```http
PUT /tables/events/{event_id}
Content-Type: application/json

{全部字段...}

响应：200 OK
```

### 删除活动
```http
DELETE /tables/events/{event_id}

响应：204 No Content
```

---

## 🎨 界面设计

### 活动卡片样式
```css
/* 活动列表中的状态徽章 */
.status-badge.status-upcoming {
    background: #3b82f6;
    color: white;
}

.status-badge.status-ongoing {
    background: #10b981;
    color: white;
}

.status-badge.status-completed {
    background: #6b7280;
    color: white;
}

.status-badge.status-cancelled {
    background: #ef4444;
    color: white;
}

/* 特色活动星标 */
.status-badge.status-completed:contains("★") {
    background: #f59e0b;
}
```

---

## 📈 数据统计

### Dashboard统计卡片
```
┌───────────────────────┐
│   📅                  │
│   6                   │
│   Upcoming Events     │
└───────────────────────┘
```

显示即将举行的活动总数（status=upcoming）

---

## 🔧 技术实现

### 文件修改
```
修改：
- admin.html (添加Events标签页和编辑器)
- js/admin.js (添加Events管理功能)

新增：
- events table schema (数据库表结构)
- 6条初始活动数据
```

### 代码结构
```javascript
// js/admin.js

// 活动管理功能
- loadEvents()           // 加载活动列表
- openEventEditor()      // 打开编辑器（新建）
- editEvent(event)       // 编辑现有活动
- closeEventEditor()     // 关闭编辑器
- saveEvent()           // 保存活动（创建/更新）
- deleteEvent(id)       // 删除活动
- updateStats()         // 更新统计（含活动数）
```

---

## 🚀 未来增强功能

### 短期（推荐）
- [ ] 活动图片上传功能
- [ ] 活动报名人数统计
- [ ] 活动提醒通知
- [ ] 活动分类标签

### 中期
- [ ] events.html动态加载
- [ ] 活动日历视图
- [ ] 活动搜索筛选
- [ ] 批量操作（批量修改状态）

### 长期
- [ ] 活动报名表单集成
- [ ] 活动签到系统
- [ ] 活动照片相册
- [ ] 活动反馈收集

---

## 📝 使用示例

### 示例1：创建节日活动
```
标题: Christmas Charity Bazaar / 圣诞慈善义卖
描述: Join us for our annual Christmas bazaar...
      加入我们的年度圣诞义卖...
日期: 2025-12-20
时间: 10:00 AM - 6:00 PM
地点: Markham Pan Am Centre
状态: Upcoming
特色: Yes
```

### 示例2：创建线上活动
```
标题: Virtual Volunteer Training / 线上志愿者培训
描述: Online training session for new volunteers...
      为新志愿者举办的在线培训...
日期: 2025-11-15
时间: 7:00 PM - 9:00 PM
地点: Virtual Event (Zoom)
状态: Upcoming
特色: No
报名链接: https://zoom.us/j/xxxxx
```

---

## 🆘 常见问题

### Q1: 活动保存后前端网站没有更新？
```
A: 当前events.html使用静态HTML。

解决方案：
1. 手动更新events.html中的HTML代码
2. 或实施动态加载功能（见"前端集成"章节）
```

### Q2: 删除活动后还能看到？
```
A: 删除是软删除（标记deleted=true）

说明：
- 后台列表会自动隐藏已删除项
- 数据库中仍保留
- 如需彻底删除，需直接操作数据库
```

### Q3: 如何批量添加活动？
```
A: 使用CSV导入或API批量创建

方法1：CSV导入（需开发）
方法2：直接使用TableDataAdd工具
方法3：使用API批量POST
```

### Q4: 能否设置活动自动过期？
```
A: 当前需手动修改状态

未来改进：
可添加定时任务，自动将过期活动标记为completed
```

---

## 📞 技术支持

**CCBONLINE Inc.**  
📧 support@ccbonline.ca  
🌐 www.ccbonline.ca

---

**文档创建日期**: 2025-11-09  
**版本**: 1.0  
**状态**: ✅ 生产就绪

🎉 **活动管理系统已完整实施，可立即使用！**
