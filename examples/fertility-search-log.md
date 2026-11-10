# 示例：分娩创伤与后续生育——检索段记录

真实案例的检索部分节选，展示本 Skill 各环节的实际运转。完整工作流（含筛选、阅读、写作）见 `research-topic-audit` 的案例文件。

## 检索方案要点

- **研究对象**：有分娩及产后创伤性健康经历的女性
- **核心关系**：创伤经历 → 后续生育（意愿 / 间隔 / 再次活产分层处理）
- **种子文献**：3 篇（登记队列、质性研究、理论综述各一）
- **通道**：AI 独立扩展（通道 A）＋ 独立平台补检（通道 B）
- **停止规则**：连续两轮补检无新增高相关文献

## 执行记录

- 双通道独立扩展后合并，按 DOI / 题名+年份去重，形成约 100 篇候选池；
- 中文补检：生成并迭代中文关键词，经平台内检索 + 网页定位 + 人工权限下载组合完成，共 23 条中文候选；
- 全文状态分流：23 条中文候选取得 19 份 PDF、4 份 CAJ；CAJ 标记为「受限格式」，不冒充可机读全文；
- 最终语料 108 篇中，18 篇仅有摘要 / CAJ / 封闭页面——人工复核确认边际增量有限，**记录理由后停止追索**，没有为凑齐规模强制下载。

## 评测结论（按四类检查）

| 检查 | 结果 |
| --- | --- |
| 数据覆盖 | 中英文双通道有实质产出；未声称中文检索饱和（平台与格式分流困难已声明） |
| 召回效果 | 种子文献全部在池；补检两轮后收敛 |
| 元数据完整性 | 每条候选有稳定标识符；43 条写作引文单独建台账（离线解析 ≠ 联网核验，「未执行」如实标注） |
| 可定位性 | 每条候选可回溯到渠道与检索词 |

## 这个案例暴露过的坑

1. 「有附件」不等于「可全文阅读」：部分 PDF 文本层异常、CAJ 无法机读，文件存在不能计入阅读量；
2. 摘要初筛把登记终点（未再次活产）误读为心理构念（意愿下降）——问题虽在阅读阶段暴露，但根源是检索与入库时没有按结果阶段分层标注，下游继承了错位的构念；
3. 单一插件承诺「自动获取全部中文全文」，实测覆盖不成立，改为关键词迭代 + 平台检索 + 人工权限的组合方案。

## 一轮可以复跑的补检

2026 年 11 月 4 日在 Europe PMC Search API 复跑。范围是英文分娩经历与再次生育研究的检索演示。这一轮只用 Europe PMC 试验检索词并核验书目。上面的历史数量与这次试跑分开记录。

### 检索台账节选

| 编号 | 日期 | 来源与访问方式 | 实际检索式 | 显示命中 | 实际查看 | 新增记录与说明 |
| --- | --- | --- | --- | ---: | --- | --- |
| Q01 | 2026-11-04 | [Europe PMC Search API](https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=TITLE_ABS%3A%22traumatic+birth%22+AND+TITLE_ABS%3A%22future+reproduction%22&resultType=lite&pageSize=10&format=json) | `TITLE_ABS:"traumatic birth" AND TITLE_ABS:"future reproduction"` | 1 | 首批第 1–1 条，共 1 条 | 1 条，初始主题检索 |
| Q02 | 2026-11-04 | [Europe PMC Search API](https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=%28TITLE_ABS%3A%22traumatic+birth%22+OR+TITLE_ABS%3A%22childbirth+experience%22%29+AND+%28TITLE_ABS%3A%22future+reproduction%22+OR+TITLE_ABS%3A%22subsequent+birth%22+OR+TITLE_ABS%3A%22subsequent+births%22%29&resultType=lite&pageSize=10&format=json) | `(TITLE_ABS:"traumatic birth" OR TITLE_ABS:"childbirth experience") AND (TITLE_ABS:"future reproduction" OR TITLE_ABS:"subsequent birth" OR TITLE_ABS:"subsequent births")` | 7 | 首批第 1–7 条，共 7 条 | 6 条，较 Q01 新增的唯一题录，仍待判断相关性 |
| Q03 | 2026-11-04 | [Europe PMC Search API](https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID%3A36894202+AND+SRC%3AMED&resultType=lite&pageSize=10&format=json) | `EXT_ID:36894202 AND SRC:MED` | 1 | 首批第 1–1 条，共 1 条 | 已知条目核查，单列，不计主题检索增量 |
| D01 | 2026-11-04 | [Europe PMC Search API](https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID%3A36894202+AND+SRC%3AMED+AND+TITLE_ABS%3A%22traumatic+birth%22&resultType=lite&pageSize=10&format=json) | `EXT_ID:36894202 AND SRC:MED AND TITLE_ABS:"traumatic birth"` | 0 | 空结果 | 已知条目核查，单列，不计主题检索增量 |
| D02 | 2026-11-04 | [Europe PMC Search API](https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID%3A36894202+AND+SRC%3AMED+AND+TITLE_ABS%3A%22future+reproduction%22&resultType=lite&pageSize=10&format=json) | `EXT_ID:36894202 AND SRC:MED AND TITLE_ABS:"future reproduction"` | 0 | 空结果 | 已知条目核查，单列，不计主题检索增量 |
| D03 | 2026-11-04 | [Europe PMC Search API](https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID%3A36894202+AND+SRC%3AMED+AND+TITLE_ABS%3A%22childbirth+experience%22+AND+TITLE_ABS%3A%22subsequent+birth%22&resultType=lite&pageSize=10&format=json) | `EXT_ID:36894202 AND SRC:MED AND TITLE_ABS:"childbirth experience" AND TITLE_ABS:"subsequent birth"` | 1 | 首批第 1–1 条，共 1 条 | 已知条目核查，单列，不计主题检索增量 |

各次请求均使用 `resultType=lite`、`pageSize=10`，查看返回的全部题录，未加年份过滤。增量按 Q01、Q02 的顺序用来源代码和条目编号去重。

**一次漏检诊断。** 用 PMID 36894202 查证，芬兰队列论文已被收录（Q03）。在这条已知记录上单独测试，两个原短语都未命中（D01、D02），而「childbirth experience」和「subsequent birth」同时命中（D03）。因此把这两种表述补入 Q02。候选清单记 Q02 为发现路径、Q03 和 D01–D03 为核验记录。新增题录仍需逐条筛选。

### 候选清单节选

| 作品编号 | 题名、作者、年份、出处 | 类型与结果 | 标识符 | 发现记录 | 书目核验 | 全文与可机读情况 | 版本 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| W01 | Does a traumatic birth experience have an impact on future reproduction? · Gottvall、Waldenström · 2002 · BJOG | 经验研究，后续出生及间隔 | [PMID 11950179](https://pubmed.ncbi.nlm.nih.gov/11950179/) · DOI 10.1111/j.1471-0528.2002.01200.x | Q01、Q02 | Europe PMC 题录已核对 | 本轮未获取全文，可机读情况未验证 | 同一作品在两次检索中出现 |
| W02 | Effect of the maternal childbirth experience on a subsequent birth · Joensuu 等 · 2023 · BMJ Open | 经验研究，再次出生 | [PMID 36894202](https://pubmed.ncbi.nlm.nih.gov/36894202/) · DOI 10.1136/bmjopen-2022-069918 | Q02 | Q03 确认索引收录，D01–D03 排查漏检 | 本轮未获取全文，可机读情况未验证 | 未检查其他版本 |

**停止原因。** 本轮到完成这次检索式对照为止。未做中文库检索、社会科学数据库补检或引文追踪，结果仅作流程演示。
