---
name: arbitration-reading
description: "Use when: a new arbitration case file arrives and needs structured pre-hearing review. Generates case reading notes with the 'three-layer five-element' method, extracts key facts and disputed issues."
version: 1.0.0
author: BINBIN
license: MIT
metadata:
  hermes:
    tags: [arbitration, case-review, pre-hearing, fact-extraction]
    related_skills: [arbitration-review]
---

# 仲裁-阅卷 · 庭前阅卷与争议焦点提炼

> 每个案件的第一步。三层五要素法系统梳理案卷，为庭审和裁决打好基础。

## Overview

本Skill在收到新案卷材料后执行系统化阅卷。基于"三层五要素"阅卷法，按程序信息、实体信息、待核实问题三个层次逐层梳理，产出标准化的阅卷笔录。

核心定位：🔵 AI自动填充已知信息 → 🟢 AI标注待核事项 → 🔴 人确认争议焦点和事实认定方向

## When to Use

| 触发信号 | 场景 |
|---------|------|
| "帮我看一下这个案子" | 收到新案卷，需要快速掌握核心事实 |
| "做一个阅卷笔录" | 庭前准备阶段，标准化阅卷 |
| 阅卷.skill 被 经纬.skill 链式调用 | meta-skill编排时自动触发 |

不适用场景：案件已开庭（此时应走裁决.skill 或 校核.skill）/ 仅需查一个法律问题而非全案梳理

## AI/Human 分工

🔵 AI自动：填写当事人信息、程序节点、合同要素、时间轴初排
🟢 AI建议：标出待核实事项、证据矛盾点、可能的法律争点
🔴 人决定：确认争议焦点、补充事实细节、决定是否需要鉴定

## Execution Flow

### Step 1：输入案件材料

用户提供：仲裁申请书、答辩书、证据目录、合同文件等。AI从对话或Feishu获取。

### Step 2：三层梳理

第一层 — 程序性信息：
- 当事人信息与主体资格
- 仲裁请求与答辩意见
- 仲裁协议效力与管辖
- 已进行的程序节点（保全、鉴定等）

第二层 — 实体性信息：
- 合同签订与履行时间轴
- 无争议事实清单
- 争议事项清单（事实/法律/程序）
- 证据目录与证明内容对照表

第三层 — 待核实问题：
- 事实不清需庭审核实
- 证据矛盾需庭审质证
- 法律关系需释明
- 可能需要鉴定/审计事项

### Step 3：输出阅卷笔录

```
═══════════════════════════════════════════
阅卷笔录
═══════════════════════════════════════════

📋 案件信息：[案号] [案由] [仲裁庭]

🔵 程序信息
- 当事人：[申请人] vs [被申请人]
- 仲裁请求：[摘要]
- 管辖：[有效/待核实]

🟢 实体信息
- 时间轴：[关键节点列表]
- 无争议事实：[__项]
- 争议焦点：[初步归纳]

🔴 待核实问题
1. [庭审核实事项]
2. [证据矛盾点]
3. [需释明的法律问题]

💡 建议方向：[1-3条办案建议]
```

## References

| 文件 | 内容 |
|------|------|
| references/three-layer-method.md | "三层五要素"阅卷法详细指南 |
| references/case-examples.md | 案例一~三精析（管辖权/主体/范围） |

## Common Pitfalls

1. 跳过程序审查直接看实体：先确认管辖权和主体资格，再进入实体分析
2. 争议焦点归纳过宽：遵循"范围越小越好"原则，不直接将仲裁请求作为焦点
3. 遗漏待核实问题：第三层是庭审准备的关键，不能跳过

## Verification Checklist

- [ ] 仲裁协议效力已审查
- [ ] 当事人主体资格已确认
- [ ] 时间轴已梳理
- [ ] 争议焦点已初步归纳
- [ ] 待核实问题清单已列出
