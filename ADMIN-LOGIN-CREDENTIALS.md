# 管理后台登录凭证

## 🔐 登录信息

### 管理后台访问地址
```
URL: https://your-domain.com/admin.html
本地测试: /admin.html
```

### 登录凭证
```
用户名 (Username): admin
密码 (Password): CaringLions@YR2025!Secure
```

⚠️ **重要提示：这是强密码，请务必妥善保管！**

---

## 📋 快速访问指南

### 1. 打开管理后台
在浏览器中访问：`admin.html`

### 2. 输入登录凭证
- **用户名**: `admin`
- **密码**: `CaringLions@YR2025!Secure`

### 3. 点击登录
系统会自动跳转到管理仪表板

---

## 🎛️ 管理后台功能

### 数据管理
1. **联系提交 (Contact Submissions)**
   - 查看所有联系表单提交
   - 查看详细信息
   - 删除记录
   - 导出CSV

2. **志愿者申请 (Volunteer Applications)**
   - 查看所有志愿者申请
   - 查看详细信息（技能、可用时间等）
   - 删除记录
   - 导出CSV

3. **捐款记录 (Donation Intents)**
   - 查看所有捐款意向登记
   - 查看详细信息（金额、频率、支付方式）
   - 删除记录
   - 导出CSV

### 统计面板
- **总联系数** (Total Contacts)
- **总志愿者数** (Total Volunteers)
- **总捐款数** (Total Donations)
- 实时自动刷新（每30秒）

### 数据操作
- **查看详情** (View) - 完整信息模态框
- **删除记录** (Delete) - 软删除（标记为已删除）
- **CSV导出** - 一键导出所有数据到CSV文件

---

## 🔒 安全说明

### ⚠️ 重要安全提示

#### 当前实现
```javascript
// js/admin.js (第10-13行)
const ADMIN_CREDENTIALS = {
    username: 'admin',
    password: 'lions2025' // Change this in production!
};
```

#### 安全级别
- **级别**: 基础（适合开发/测试）
- **存储**: 本地localStorage（浏览器）
- **加密**: 无（明文密码）

#### ⚠️ 生产环境建议

**必须进行以下安全升级：**

1. **修改默认密码**
   ```javascript
   // 建议使用强密码
   password: 'LionsClub@2025!SecurePass#'
   ```

2. **实施后端认证**
   - 移除前端硬编码密码
   - 使用后端API验证
   - 实施JWT或Session机制

3. **添加密码加密**
   ```javascript
   // 使用bcrypt或类似库
   const hashedPassword = await bcrypt.hash(password, 10);
   ```

4. **实施HTTPS**
   - 确保所有通信加密
   - 防止中间人攻击

5. **添加多因素认证 (MFA)**
   - Google Authenticator
   - 短信验证码
   - 邮箱验证码

6. **实施访问日志**
   ```javascript
   // 记录所有登录尝试
   logLoginAttempt(username, success, ipAddress, timestamp);
   ```

7. **添加登录限制**
   ```javascript
   // 防止暴力破解
   - 失败3次后锁定15分钟
   - IP限制
   - CAPTCHA验证
   ```

---

## 🛠️ 修改密码教程

### 方法1：修改JavaScript文件（临时）

1. 打开文件：`js/admin.js`
2. 找到第12行：
   ```javascript
   password: 'lions2025' // Change this in production!
   ```
3. 修改为新密码：
   ```javascript
   password: 'YourNewSecurePassword123!'
   ```
4. 保存文件

### 方法2：实施后端认证（推荐）

```javascript
// 示例：使用后端API验证
async function login(username, password) {
    try {
        const response = await fetch('/api/admin/login', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({ username, password })
        });
        
        const data = await response.json();
        
        if (data.success) {
            localStorage.setItem('adminToken', data.token);
            showDashboard();
        } else {
            alert('Invalid credentials');
        }
    } catch (error) {
        console.error('Login error:', error);
        alert('Login failed. Please try again.');
    }
}
```

---

## 📊 使用场景

### 1. 查看新的联系提交
```
1. 登录管理后台
2. 默认显示"Contact Submissions"标签
3. 查看最新提交（按时间倒序）
4. 点击"View"查看完整信息
5. 处理完毕后可选择删除
```

### 2. 管理志愿者申请
```
1. 点击"Volunteer Applications"标签
2. 查看所有志愿者申请
3. 点击"View"查看详细信息：
   - 个人信息
   - 联系方式
   - 技能和兴趣
   - 可用时间
   - 紧急联系人
4. 导出CSV进行批量处理
```

### 3. 追踪捐款意向
```
1. 点击"Donation Intents"标签
2. 查看所有捐款意向登记
3. 点击"View"查看详细信息：
   - 捐款金额
   - 捐款频率
   - 首选支付方式
   - 匿名意愿
   - 税务收据需求
4. 联系捐款者完成支付
```

### 4. 导出数据报告
```
1. 在任意数据标签页
2. 点击"Export CSV"按钮
3. 自动下载CSV文件
4. 用Excel或Google Sheets打开
5. 进行数据分析和报告
```

---

## 🔄 自动刷新

管理后台每30秒自动刷新数据，确保实时性。

```javascript
// js/admin.js
setInterval(() => {
    loadAllData();
}, 30000); // 30秒刷新一次
```

**如需修改刷新频率：**
- 修改 `30000` 为其他值（单位：毫秒）
- 例如：`60000` = 1分钟

---

## 📱 移动端访问

管理后台支持响应式设计，可在移动设备上访问：

**移动端优化：**
- ✅ 触摸友好的按钮大小
- ✅ 横向滚动表格
- ✅ 自适应布局
- ✅ 优化的模态框

---

## 🆘 常见问题

### Q1: 忘记密码怎么办？
```
A: 当前版本密码硬编码在js/admin.js中

解决方案：
1. 打开js/admin.js文件
2. 查看第12行的password值
3. 或者直接修改为新密码
```

### Q2: 登录后自动退出？
```
A: 登录状态存储在localStorage中

可能原因：
1. 浏览器清除了localStorage
2. 使用无痕/隐私模式
3. 浏览器设置阻止了localStorage

解决方案：
- 使用正常浏览模式
- 允许网站存储数据
```

### Q3: 数据不更新？
```
A: 检查API连接

解决方案：
1. 打开浏览器开发者工具 (F12)
2. 查看Console标签的错误信息
3. 查看Network标签的API请求
4. 确认API端点正常工作
```

### Q4: 无法删除记录？
```
A: 删除是软删除（标记为deleted=true）

说明：
- 记录不会物理删除
- 只是标记为已删除
- 前端不再显示
- 数据库中仍保留
```

---

## 📞 技术支持

如需帮助或有安全疑虑，请联系：

**CCBONLINE Inc.**  
📧 Email: support@ccbonline.ca  
🌐 Website: www.ccbonline.ca

---

## 🔐 密码策略建议

### 强密码要求
- ✅ 至少12个字符
- ✅ 包含大写字母 (A-Z)
- ✅ 包含小写字母 (a-z)
- ✅ 包含数字 (0-9)
- ✅ 包含特殊字符 (!@#$%^&*)
- ✅ 避免常见单词
- ✅ 避免个人信息

### 示例强密码
```
❌ 弱密码: admin, password, 123456, lions
✅ 强密码: LionsClub@2025!Secure#Pass
```

---

## 📝 维护清单

### 定期维护任务

**每周：**
- [ ] 检查新的联系提交
- [ ] 回复志愿者申请
- [ ] 跟进捐款意向

**每月：**
- [ ] 导出数据备份
- [ ] 清理已处理的记录
- [ ] 审查登录日志（实施后）

**每季度：**
- [ ] 修改管理员密码
- [ ] 审核系统安全性
- [ ] 更新系统文档

---

## 🎯 快速参考

### 登录凭证（再次强调）
```
URL: /admin.html
用户名: admin
密码: lions2025
```

### 常用功能快捷键
- `Contacts` 标签 - 联系提交
- `Volunteers` 标签 - 志愿者申请
- `Donations` 标签 - 捐款记录
- `Logout` 按钮 - 安全登出

### 数据操作
- 👁️ `View` - 查看详情
- 🗑️ `Delete` - 删除记录
- 📥 `Export CSV` - 导出数据

---

**文档创建日期**: 2025-11-09  
**版本**: 1.0  
**状态**: 生产就绪  

⚠️ **请务必在生产环境中修改默认密码！**

🔒 **安全提示：此文档包含敏感信息，请妥善保管，不要公开分享！**
