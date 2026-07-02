---
name: "8d-report-processor"
description: "8D报告审核与翻译一体化工具，覆盖汽车供应链、消费电子、电子信息、LCD/OLED显示面板四大制造行业。支持两种模式：审核模式（逐条校验D1-D8合规性，识别缺失/逻辑/术语问题，输出Word整改报告）和翻译模式（中英互译，保留原文格式数据，输出标准外企译文）。用户上传8D文档要求审核或翻译时触发。"
---

# 8D报告审核与翻译一体化处理工具

## 技能描述

支持输入中文/英文8D文本，或上传PDF/Word/Powerpoint附件；覆盖四大制造行业：汽车供应链、消费电子、通用电子信息、LCD/OLED显示面板。

根据用户意图自动切换两种工作模式：

**审核模式**：严格按照行业8D标准D1-D8逐项校验，自动识别三类问题（信息缺失、逻辑漏洞、文本问题），逐条列出全部问题并附带修改建议，输出Word审核整改报告。

**翻译模式**：完成定稿后8D文档中英互译，内置全行业统一质量术语库，保留原文分段、数据、料号、表格、8D章节编号，输出规范外企标准译文。

## 触发条件与模式切换

### 审核模式触发

用户上传8D文档附件或粘贴全文，要求校验/审核/检查报告问题时触发。

关键词识别：审核、校验、检查、审查、review、audit、check、问题、整改、合规

### 翻译模式触发

用户发送修改完成的8D原文或上传定稿附件，要求翻译时触发。

关键词识别：翻译、中英互译、translate、英文版、中文版、译文

### 默认规则

若用户同时提及审核和翻译，或意图不明确，优先进入审核模式。审核完成后再询问用户是否需要翻译。

## 依赖MCP工具

File System 文件读取：解析PDF/Word/TXT/MD/PPT附件内8D完整内容

## 共享：四大制造行业术语库

### 1. 汽车供应链

**术语对照**：注塑 molding、冲压 stamping、线束 wire harness、气密泄漏 air leakage、尺寸超差 dimension out of tolerance、PFMEA、MSA、PPAP、工装 fixture、治具 jig、异响 abnormal noise、喷涂不良 coating defect

**审核重点**：注塑、冲压、喷涂、线束、焊接、气密、异响、尺寸超差、PPAP、FMEA、MSA、PFMEA、IQC/OQC/PQC。禁止混用电子面板类术语，出现术语错位标注为问题。

### 2. 消费电子（手机/平板/笔记本/穿戴设备）

**术语对照**：主板 main board、FPC flexible printed circuit、摄像头模组 camera module、点胶 dispensing、虚焊 cold solder joint、ESD electrostatic discharge、跌落测试 drop test、卡合间隙 assembly gap、电池鼓包 battery swelling

**审核重点**：主板、FPC、电池、摄像头模组、结构件、卡合间隙、按键失灵、充放电异常、外观划伤、点胶、焊盘短路、ESD静电、整机跌落测试。

### 3. 通用电子信息（PCB、电源、工控、连接器）

**术语对照**：PCB printed circuit board、短路 short circuit、开路 open circuit、锡珠 solder ball、元器件偏移 component shift、阻抗 impedance、EMC electromagnetic compatibility、连接器 connector、耐压测试 withstanding voltage test

**审核重点**：PCB短路/开路、虚焊、冷焊、锡珠、元器件偏移、阻抗不良、耐压失效、连接器插拔寿命、EMC电磁干扰。

### 4. LCD/OLED显示面板行业

**术语对照**：亮点 bright dot、暗点 dark dot、Mura 云斑、漏光 light leakage、残影 image retention、色度偏移 color shift、FOG bonding、COG 芯片绑定、偏光片 polarizer、背光模组 backlight module、切割崩边 cutting chipping、液晶气泡 liquid crystal bubble

**审核重点**：亮点、暗点、彩斑、Mura、漏光、偏光片褶皱、绑定不良、COG/FOG断线、残影、色度偏移、亮度不均、切割崩边、液晶气泡、背光模组异物。

---

## 模式一：审核校验模式

### 一、通用D1-D8强制校验标准（中英文通用，全行业统一）

D1 团队：缺少跨职能小组、成员职责、对接人 → 判定信息缺失

D2 问题描述：无5W2H、无不良批次/数量/不良现象，描述笼统 → 缺失+逻辑缺陷

D3 临时遏制：无隔离、分选、库存锁定动作，无执行时效、覆盖范围 → 内容缺失

D4 根因分析：未区分发生根因+流出逃逸根因；仅表面归因、无4M/5Why支撑；根因和故障无关联 → 严重逻辑漏洞

D5 永久改善：每条措施无法对应D4根因；仅写"加强管理"无具体动作、无责任人/期限 → 逻辑不匹配、内容空洞

D6 效果验证：无连续批次量化数据、短期无跟踪记录，无法证明改善有效 → 验证环节缺失

D7 预防再发：未更新SOP/检验标准/防错/培训，无横向展开计划 → 长效闭环缺失

D8 结案：无评审确认、经验沉淀记录，流程未闭环 → 结案信息缺失

### 二、分语言基础校验规则

1. 中文8D额外检查

- 大量模糊化口语，无量化数字；

- 零部件、不良类型、工位名称前后用词不统一；

- 无数据支撑，全为主观描述。

2. 英文8D额外检查

- 语法、时态、单复数、专业术语拼写错误；

- 行业标准词汇混用、错用；

- 长句混乱，海外客户SQE阅读不通顺；

- 章节英文标题不标准。

### 三、行业术语一致性校验要求

1. 报告内故障、物料、工艺术语必须统一，前后描述不一致判定为【术语混乱问题】；

2. 跨行业错用专业名词（面板Mura写在汽车零部件报告）直接标记并给出标准替换词汇；

3. 关键缺陷无行业标准定义，描述模糊，给出标准行业书面表述修改建议。

### 四、审核模式固定输出结构

1. 报告基础信息：识别所属行业、语言类型、整体合规评级（合格/部分整改/严重缺失）

2. 问题汇总总表：序号、所属D模块、问题类型（缺失/逻辑/语法术语）、问题原文说明

3. 分模块逐条修改建议：对应每条问题给出具体补充、改写方案，同步提供对应行业标准术语

4. 高频踩坑总结：各行业客户审核常驳回的同类问题提醒

### 五、审核模式输出约束

1. 仅输出审核问题与整改建议，不执行任何翻译操作；

2. 不编造8D内容，仅基于用户提供原文校验；

3. 不附其他无关内容；

4. 输出格式为Word文档。

---

## 模式二：翻译模式

### 一、固定8D章节标准英文标题，全程统一不可变动

D1 Establish Cross-functional Team

D2 Problem Description (5W2H)

D3 Implement & Verify Interim Containment Actions

D4 Determine & Verify Root Cause (Occurrence & Escape)

D5 Select & Verify Permanent Corrective Actions

D6 Implement Permanent Corrective Actions & Effect Validation

D7 Prevent Recurrence & System Optimization

D8 Team Recognition & Report Closure

### 二、通用翻译强制规则

1. 对应行业术语固定译法（见上方共享术语库），杜绝中式直译；英文采用制造业技术书面语态；

2. 完整保留所有数字、批次、料号、不良数量、时间节点；

3. 不新增、删减、修改原文业务逻辑、改善措施、验证数据；

4. 自动识别文档所属行业，全程统一整套行业词汇，前后翻译无冲突；

5. 若原文存在明显逻辑缺失、数据空白，会简单提示：建议先完成报告审核整改再翻译。

### 三、翻译模式输出约束

1. 仅输出完整翻译后的8D文档，按照用户上传的格式返回，无多余审核、打分、闲聊内容；

2. 保留报告内的图片和排版。

---

## 用户输入格式

### 审核模式

格式1：粘贴文本

8D报告原文：

此处粘贴完整中文/英文8D内容

格式2：上传附件

先上传PDF/Word/Powerpoint附件，再发送：请审核这份8D报告全部问题并给出修改意见

### 翻译模式

格式1：粘贴定稿文本

已修改完成的8D原文：

粘贴完整内容

格式2：上传定稿文档附件

上传PDF/Word/Powerpoint后发送：将这份已整改完毕的8D报告翻译成标准英文/中文版本
