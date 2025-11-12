# 🚀 Quick Start: Dynamic Events System

**For**: Administrators and Users  
**Purpose**: Get started with the new dynamic events system in 5 minutes  
**Date**: 2025-11-11

---

## 📖 What Changed?

### Before
Events were **hardcoded in HTML** → Required developer to edit files

### Now
Events are **loaded from database** → Anyone can update through admin panel!

---

## 👥 For Website Visitors

### What You'll See

1. **Visit** `/events.html`
2. **Loading** (1-2 seconds):
   ```
   ⟳ Loading upcoming events...
   ```

3. **Events Appear** automatically:
   ```
   ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
   │ ⭐ 23 NOV   │ │  30 NOV     │ │  07 DEC     │
   │   2025      │ │   2025      │ │   2025      │
   │             │ │             │ │             │
   │ Winter Food │ │ Youth       │ │ First-Aid   │
   │ Drive       │ │ Leadership  │ │ Course      │
   │             │ │ Workshop    │ │             │
   │ [Register]  │ │ [Register]  │ │ [Register]  │
   └─────────────┘ └─────────────┘ └─────────────┘
   ```

4. **Featured Events** have ⭐ gold star badge

5. **Switch Language** → Everything translates (EN ↔ 中文)

### If No Events
```
┌──────────────────────────────┐
│      📅 (calendar icon)      │
│                              │
│    No Upcoming Events        │
│        暂无活动              │
│                              │
│  [Contact Us Button]         │
└──────────────────────────────┘
```

### If Error Occurs
```
┌──────────────────────────────┐
│      ⚠️ (warning icon)       │
│                              │
│  Unable to Load Events       │
│   无法加载活动信息           │
│                              │
│  [🔄 Try Again Button]       │
└──────────────────────────────┘
```

---

## 🔐 For Administrators

### Step 1: Login to Admin Panel

1. Open browser and go to: **`/admin.html`**
2. Enter credentials:
   - **Username**: `admin`
   - **Password**: `CaringLions@YR2025!Secure`
3. Click "Login"

---

### Step 2: Navigate to Events

1. You'll see dashboard with 4 sections:
   ```
   [Members] [Contacts] [Donations] [Events]
   ```
2. Click **[Events]** button

---

### Step 3: View Existing Events

You'll see a table like this:
```
┌─────────┬──────────────────┬─────────────┬────────────┬─────────┬──────────┬─────────┐
│  Date   │  Title (EN/ZH)   │  Location   │    Time    │ Status  │ Featured │ Actions │
├─────────┼──────────────────┼─────────────┼────────────┼─────────┼──────────┼─────────┤
│ 11/23   │ Winter Food      │ Markham     │ 10AM-4PM   │upcoming │ ★        │ [Edit]  │
│         │ Drive            │ Civic Ctr   │            │         │          │ [Delete]│
│         │ 冬季食物募捐     │             │            │         │          │         │
├─────────┼──────────────────┼─────────────┼────────────┼─────────┼──────────┼─────────┤
│ 11/30   │ Youth            │ Virtual     │ 2PM-5PM    │upcoming │ -        │ [Edit]  │
│         │ Leadership       │ (Zoom)      │            │         │          │ [Delete]│
│         │ 青年领导力       │             │            │         │          │         │
└─────────┴──────────────────┴─────────────┴────────────┴─────────┴──────────┴─────────┘
```

---

### Step 4: Add New Event

1. Click **[+ Add New Event]** button (top right)

2. Fill out the form:

   **Basic Information**:
   ```
   Title (English) *     [____________________]
   Title (Chinese) *     [____________________]
   
   Description (EN) *    [____________________]
                        [____________________]
   
   Description (ZH) *    [____________________]
                        [____________________]
   ```

   **Date & Location**:
   ```
   Event Date *          [2025-12-15] (calendar picker)
   Event Time *          [10:00 AM - 4:00 PM]
   Location *            [Markham Community Centre]
   ```

   **Settings**:
   ```
   Status *              [Upcoming ▼]
                         Options: Upcoming, Ongoing, Completed, Cancelled
   
   Featured Event        [No ▼]
                         Options: No, Yes - Show on Homepage
   ```

   **Optional**:
   ```
   Event Image URL       [https://example.com/image.jpg]
   Registration URL      [https://forms.google.com/...]
   ```

3. Click **[Save Event]** button

4. You'll see success message: "Event created successfully!"

---

### Step 5: View on Website

1. Open new tab
2. Go to: **`/events.html`**
3. **Your new event appears immediately!** 🎉

---

### Step 6: Edit Existing Event

1. Find event in table
2. Click **[Edit]** button
3. Modal opens with pre-filled form
4. Change any fields you want
5. Click **[Save Event]**
6. Success! Changes appear on website instantly

---

### Step 7: Delete Event

1. Find event in table
2. Click **[🗑️ Delete]** (trash icon)
3. Confirm: "Are you sure you want to delete this event?"
4. Click "OK"
5. Event removed from table and website

---

## 💡 Tips & Tricks

### Featured Events
- **Use sparingly** - Only mark 1-2 most important events as featured
- **Gold star badge** appears on website
- **Special styling** - Border and shadow effect

### Event Status
- **Upcoming** - Shows on website (default for new events)
- **Ongoing** - Shows on website (for events happening now)
- **Completed** - Hidden from website (for past events)
- **Cancelled** - Hidden from website (for cancelled events)

### Registration URLs
- **External**: Use Google Forms, Eventbrite, etc.
  - Example: `https://forms.google.com/...`
  - Opens in new tab when clicked
- **Internal**: Use `/contact.html`
  - Visitors fill contact form
- **Leave empty**: Defaults to contact page

### Bilingual Content
- **Always fill both** English AND Chinese fields
- **Keep consistent** - Translate accurately
- **Test both languages** - Switch language on website to verify

---

## ⚙️ Technical Details

### How It Works

```
┌──────────────┐
│ Admin Panel  │ ← You add/edit event here
│ /admin.html  │
└──────┬───────┘
       │
       │ POST/PUT (saves to database)
       ↓
┌──────────────┐
│  Database    │ ← Events stored here
│ (events)     │
└──────┬───────┘
       │
       │ GET (retrieves events)
       ↓
┌──────────────┐
│ Public Page  │ ← Visitors see events here
│ /events.html │
└──────────────┘
```

### Files Involved
- **events.html** - Public events page (what visitors see)
- **admin.html** - Admin management panel (password protected)
- **js/events-dynamic.js** - JavaScript that loads events
- **tables/events** - Database API endpoint

---

## 🐛 Troubleshooting

### Problem: Events Not Loading

**Symptoms**: Spinning loader forever, no events appear

**Solutions**:
1. Refresh the page (Ctrl+R or Cmd+R)
2. Check internet connection
3. Try different browser
4. Contact technical support

---

### Problem: Can't Login to Admin

**Symptoms**: "Invalid credentials" error

**Solutions**:
1. Double-check username: `admin` (lowercase)
2. Check password: `CaringLions@YR2025!Secure` (case-sensitive!)
3. Try copy-pasting password to avoid typos
4. Contact technical support if forgotten

---

### Problem: Changes Not Appearing

**Symptoms**: Edited event, but website shows old info

**Solutions**:
1. Refresh website page (Ctrl+R or Cmd+R)
2. Clear browser cache (Ctrl+Shift+Del)
3. Try different browser or incognito mode
4. Wait 10 seconds and try again

---

### Problem: Language Not Switching

**Symptoms**: Clicked language button but content stays same

**Solutions**:
1. Click language button again
2. Refresh page
3. Check if you filled both EN and ZH fields in admin
4. Contact technical support

---

## 📞 Need Help?

### For Administrators
- **Admin Guide**: See `EVENTS-MANAGEMENT-SYSTEM.md` (11 KB)
- **Contact**: support@ccbonline.ca
- **Phone**: +1 (416) 832-8158

### For Developers
- **Technical Docs**: See `DYNAMIC-EVENTS-INTEGRATION.md` (20 KB)
- **Source Code**: `js/events-dynamic.js`
- **API**: `tables/events` endpoint

### For Users
- **Website**: love520.org
- **Contact**: love521org@gmail.com
- **Location**: 7181 Woodbine Ave, Markham, ON L3R 1A3

---

## 🎯 Quick Reference Card

### Admin Login
```
URL:      /admin.html
Username: admin
Password: CaringLions@YR2025!Secure
```

### Add Event Steps
```
1. Login → Click [Events]
2. Click [+ Add New Event]
3. Fill English + Chinese fields
4. Set date, time, location
5. Choose status (Upcoming)
6. Click [Save Event]
7. Done! ✅
```

### Edit Event Steps
```
1. Find event in table
2. Click [Edit]
3. Change any fields
4. Click [Save Event]
5. Done! ✅
```

### Delete Event Steps
```
1. Find event in table
2. Click [🗑️ Delete]
3. Confirm deletion
4. Done! ✅
```

---

## 🎉 You're Ready!

You now know how to:
✅ View events on the website  
✅ Login to admin panel  
✅ Add new events  
✅ Edit existing events  
✅ Delete old events  
✅ Use featured events  
✅ Troubleshoot common issues  

**Go ahead and try it out!** 🚀

---

*For detailed technical documentation, see:*
- **EVENTS-MANAGEMENT-SYSTEM.md** - Complete admin guide
- **DYNAMIC-EVENTS-INTEGRATION.md** - Technical implementation details
- **SESSION-SUMMARY.md** - Full session record

**Status**: ✅ Ready to use!
