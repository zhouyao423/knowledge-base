---
date: {{date}}
week: {{week_number}}
tags: [weekly-review, routine, synthesis]
status: complete
---

# 每周回顾 - 第{{week_number}}周 ({{date_range}})

## 📊 本周概览

**主题焦点**:
-

**整体评价**: ⭐⭐⭐⭐⭐ (1-5)

**能量趋势**: 📈📉➡️

---

## 🎯 目标达成

### 本周目标回顾
- [ ] {{goal_1}}
- [ ] {{goal_2}}
- [ ] {{goal_3}}

**完成率**: {{completion_rate}}%

### 意外收获
-

### 主要挑战
-

---

## 📈 各领域进展

### 💼 工作/项目
**活跃项目**:
- {{#each active_projects}}
  - [[{{name}}]]: {{status}} ({{progress}}%)
{{/each}}

**新启动**:
-

**已完成**:
-

### 🏗️ 个人成长
**学习重点**:
-

**技能提升**:
-

**阅读/课程**:
-

### 🏥 健康生活
**运动情况**:
- 频率: {{exercise_frequency}}
- 类型: {{exercise_types}}

**睡眠质量**:
- 平均: {{sleep_hours}}小时
- 评价: {{sleep_quality}}

**饮食习惯**:
-

### 🤝 社交关系
**重要连接**:
-

**社交活动**:
-

---

## 💡 洞察与反思

### 本周关键洞察
1.
2.
3.

### 模式识别
**时间使用模式**:
-

**能量波动规律**:
-

**注意力高峰时段**:
-

### 需要调整的地方
-

---

## 📝 收件箱与系统

### 收件箱处理
**处理项目数**: {{processed_count}}
**剩余项目**: {{remaining_count}}
**处理效率**: {{efficiency_rating}}

### 系统维护
- [ ] 清理孤立文件
- [ ] 更新项目状态
- [ ] 整理附件文件夹
- [ ] 备份重要数据

---

## 🎯 下周计划

### 核心目标 (1-3个)
1.
2.
3.

### 重点任务
**周一**:
**周二**:
**周三**:
**周四**:
**周五**:

### 时间分配预判
- 项目工作: {{project_time_hours}}小时
- 学习成长: {{learning_time_hours}}小时
- 健康运动: {{health_time_hours}}小时
- 社交休闲: {{social_time_hours}}小时

---

## 🔄 系统优化

### 流程改进
**本周尝试的新方法**:
-

**效果评估**:
-

**下周继续实验**:
-

### 工具优化
**新发现的工具**:
-

**需要改进的工具**:
-

---

## 📊 数据统计

### 创作产出
- 新建笔记: {{new_notes_count}}篇
- 完成项目: {{completed_projects_count}}个
- 处理收件箱: {{inbox_processed_count}}项

### 时间记录
**专注时间**: {{focus_hours}}小时
**会议时间**: {{meeting_hours}}小时
**学习时间**: {{learning_hours}}小时

### Git 活动
- 提交次数: {{git_commits_count}}次
- 推送次数: {{git_pushes_count}}次

---

## 🙏 感恩与庆祝

### 本周值得庆祝的事
1.
2.
3.

### 感激的人/事
-

---

## 🔗 相关链接

{{#if weekly_notes}}
- {{#each weekly_notes}}
  - [[{{this}}]]
  {{/each}}
{{/if}}

{{#if project_updates}}
### 项目更新
- {{#each project_updates}}
  - [[{{project}}]]: {{update}}
  {{/each}}
{{/if}}

---

## 📋 下周提醒事项

- [ ] {{reminder_1}}
- [ ] {{reminder_2}}
- [ ] {{reminder_3}}

---
*创建时间: {{timestamp}}*
*回顾模板 v1.0*