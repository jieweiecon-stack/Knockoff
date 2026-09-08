# FAR-Knockoff 投稿与修改讨论记录

> 论文:*Factor-Adjusted Knockoff Inference for High-Dimensional Time Series*
> 作者:Jie Wei, Lan Gao, Yuan Ke, Yonghui Zhang
> 记录时间:2026 年 9 月 8 日

**涉及的附件文件**

| 文件 | 内容 |
|---|---|
| `AE_report1.pdf` | JOE 的 AE 意见,8 条主评 + 3 处 typo |
| `report__3_.pdf` | 审稿人 1(正面),3 条 major + 4 条 minor |
| `report_12_31_2025.pdf` | 审稿人 2(负面),约 15 条意见 |
| `FAR_Knockoff_Revision_2026-08-29_ReferencesWithin40Pages.pdf` | 8-29 修改稿,74 页 |
| `FAR_Knockoff_Revision_2026-09-07_AllBlack.pdf` | 9-07 修改稿 |
| `appendix_threshold_stability.tex` | 本次讨论产出的附录草稿 |

---

## 第 1 轮 — JOE 被拒后大改可以重投吗(一般性问题)

**问:** 如果 JOE 被拒,但是大改过,可以重投吗?

**答:** 要看拒稿信的具体措辞,分三种情况。

1. **Reject and resubmit(拒绝但邀请重投)** — 信里会有明确的鼓励性措辞,例如 "we would be willing to consider a substantially revised version as a new submission"。这种情况可以也应该重投;编辑实际上是在给机会,只是不想走正式的 R&R 流程(不占用修改轮次统计)。按新稿投,附详细 response letter。
2. **普通拒稿(plain reject)** — 多数期刊(含 Elsevier 系统下的 JOE)默认拒稿即终审,不接受同一篇论文重投,即使大改。硬投的常见结果是编辑部识别后直接 desk reject,并给编辑留下不好的印象。
3. **Desk reject** — 若理由是"不符合本刊范围/兴趣",大改也难改变判断;若理由是格式、篇幅、写作不清,有时改好后可以询问。

**最稳妥做法:**先给处理编辑发一封简短的 pre-submission inquiry(一两段),说明原稿编号、审稿人的核心批评、做了哪些实质性改动(新识别策略、新数据、新理论结果),问是否愿意作为新稿考虑。

**两点提醒:**重投时必须主动披露之前的投稿历史,隐瞒被发现后果严重;如果改动大到定理、数据、识别都换了,某种意义上已是新论文,更要在信里讲清新旧关系。

**期望收益判断:**除非上次拒稿意见明显偏"接近"(只有一个审稿人反对、编辑语气惋惜),否则改好后换一家同档次期刊通常比在原刊死磕划算。

---

## 第 2 轮 — 读过三份报告后的具体判断

**问:**(上传 AE 意见与两份审稿报告)你看下我修改的,可以重投 JOE 吗?

**答:不属于可以重投的情形。**

### 为什么

AE 开头写的是 "several fundamental limitations make the paper unsuitable for the Journal of Econometrics in its current form",没有任何邀请重投的措辞。更要紧的是 AE 的核心反对是**框架层面**而非执行层面:

- **Main Comment 1 和 5 其实是同一件事** — Fixed-X knockoff 的构造在数学上要求 $\{X_t\}$ 与 $\{\varepsilon_t\}$ 整体独立(strong exogeneity)。AE 明确指出 econometrics 里自然的设定是 $\varepsilon_t$ 关于 $\mathcal{F}_{t-1}=\sigma(X_1,\dots,X_{t-1},Y_1,\dots,Y_{t-1})$ 的鞅差,允许 $y_{t-1}$ 进入回归。
- **审稿人 2 的第一条问的是同一个问题**(能不能放 lagged dependent variable)。两人独立指向同一处,不是"再解释清楚一点"能解决的 — 在保留 Fixed-X 的前提下解决不了。

### 审稿人配置

审稿人 1 明显正面("interesting and well written",三条 major 都可改);审稿人 2 负面,用了 "not well written"、"contains incorrect and unclear statements"、"contribution minor"。一正一负 + AE 从框架上否定 = 标准 reject,不是 borderline。

### 一个战术观察

审稿人 2 引了 Chudik-Kapetanios-Pesaran (2018)、Sharifvaghefi (2025, *Econometric Reviews*)、Fan-Lv-Sharifvaghefi-Uematsu 的 IPAD,还专门抱怨模拟里没放 IPAD。指向性很强,之后投计量类期刊大概率还会碰到同一人。两个含义:必须把 IPAD 补进模拟;关于 IPAD 的那句描述("idiosyncratic errors cannot exhibit correlation in either the cross section or over time")他说写错了,要么改掉要么给出精确出处页码。

### 真该改的硬伤

- $S\subset\tilde{S}_0$ vs $S_0\subset\tilde{S}$ — 审稿人 2 和 AE 都独立判定是笔误。两位读者在同一处卡住,说明第 11 页那段的逻辑呈现是坏的,不只是印刷错误。
- **Assumption 7** — 审稿人 2 说 "does not appear to be a well-formulated assumption"。一个 beta-min 条件写成"超过随机阈值的信号个数要大于另一个随机量",确实不成立地陈述了。
- **Section 5.2 没有时间相依设计** — 全文卖点是处理 serial dependence,主模拟里却没有相应设计。
- **$\gamma=1/5$、$\xi$、$\lambda$、$m$、$\ell_T$ 的选择** — AE 第 8 点单列"太多 tuning parameter 且不知道怎么选",审稿人 2 也问了三次。

### 两条路

- **路线 A(保守,推荐)** — 不动框架,吸收审稿人 1 的全部意见 + 审稿人 2 的技术性意见 + AE 的 typo 类意见,转投对 Fixed-X 假设不那么敏感的期刊:JBES、*Journal of Financial Econometrics*(债券风险溢价应用加分)、JASA T&M、*Statistica Sinica*、*Journal of Time Series Analysis*。新版本必须**主动明确**把 strong exogeneity 写进 limitation,不要藏。
- **路线 B(野心版)** — 真去解决 MDS 误差 + 允许滞后因变量。做成了是更强的论文,但 12–18 个月工作量,未必做得成。

---

## 第 3 轮 — 再问一次能否重投 JOE

**问:** 可以重投 JOE 吗?

**答:不建议,严格来说是不能。**

- AE 那句 "in its current form" 容易被误读成"改好就行",但它不是邀请重投的措辞。真的邀请会明确写 "we would be willing to consider a substantially revised version as a new submission",或给一个 reject-and-resubmit 标签。三份材料里没有。
- JOE 的拒稿是终审,Elsevier 系统会记录稿件历史。重投大概率被识别后 desk reject。
- 就算流程允许,内容也过不去。AE 否定的是框架本身:只要还用 Fixed-X,$\{X_t\}$ 与 $\{\varepsilon_t\}$ 整体独立这条就绕不过去。把审稿人 2 的十几条技术意见全改完,AE 的第 1、5 点依然原封不动。这是"大改救不回"的那类拒稿 — 大改的定义得是换构造,而换了构造就是另一篇论文。

**唯一值得考虑重回 JOE 的情形:**真做出了 MDS 误差下的版本,允许滞后因变量,定理重证。那时已不是这篇稿子,可作为新论文投,cover letter 说明与前稿关系。

**现实做法:**转投。JBES 或 *Journal of Financial Econometrics*(后者尤其,债券风险溢价应用是加分项,对 Fixed-X 的容忍度比 JOE 高)。转投前补掉四项:Assumption 7、第 11 页 $S\subset\tilde S_0$ 笔误、5.2 缺时间相依设计、IPAD 对比。

---

## 第 4 轮 — 审阅 9-07 修改稿(此时已转投 JBES,收到新的负面意见)

**问:**(上传 9-07 稿,并粘贴 JBES 审稿人与 AE 的新意见)

> 主要程序结合了若干熟悉的组件:PCA 因子调整、基于残差的序列误差协方差估计、预白化、样本分割、Fixed-X knockoff 构造。每个成分在现有文献中都已确立。论文的贡献因此主要是现有想法的综合,而非根本性的新推断框架……
>
> AE:两位审稿人和我都不清楚这项工作的关键方法论新意。建议作者澄清组合的关键挑战(为什么这个组合是非平凡的);否则这项工作看起来只是现有方法的简单整合。

用户自己列出六条新意主张,请求核对。

### 逐条核对结果

| # | 主张 | 判定 |
|---|---|---|
| 1 | 去掉 sure screening,建立 screening 误差如何传导到 FDR 与 power,sure screening 作为特例 | **准确,已在文中**,但被低估 |
| 2 | 用估计的协方差白化,给出对 FDR 有效的充分条件,该误差受 screening 影响 | **准确** |
| 3 | PCA 提升 power;理论上证明因子个数低估损害 power consistency | **过度宣称**,无对应命题 |
| 4 | TSKI 靠 e-value 汇总子样本,可能保守 | **会反噬**,建议删除 |
| 5 | coupling 充分统计量得分 vs Fan 2025 coupling 原始数据 | **准确,严重低估** |
| 6 | 放松高斯假设 → GARCH、厚尾 | **准确**,但陈述方式不对 |

**第 1 条细节:** 第 24 页 "How screening enters the FDR guarantee" 把三条通道分清楚:$\delta^{scr}_{NT}$ 加性进入、over-selection 放大 $K_{NT}$ 从而恶化 $\omega_{NT}$ 和 $\epsilon^{cov}_{NT}$、under-selection 同时产生 $R_{\text{miss}}$ 和 $\epsilon^{mean}_{NT}$。然后 "Under sure screening, $R_{\text{miss}} = \epsilon^{mean}_{NT} = 0$",并用 $\min_{j\in S_0}|\beta^M_j|\ge \xi + a_{NT}$ 把 sure screening 收成特例。Power 端 Theorem 4.5 给 $1-E(\pi_{NT})$。

**第 1、2 条不该分开列。**合起来才是真正的方法论新意:时间序列下白化是必需的 → 白化需要 $\hat\Sigma_\varepsilon$ → 需要残差 → 高维下残差需要先筛选 → **白化误差是选择误差的函数**。这是文献里不存在的闭环:Fan et al. (2020a) 不白化;Barber-Candès 没有 nuisance 协方差;ARK 假定时间独立不需白化。$R_{\text{miss}}$ 就是闭环的那个量。**这是 "why nontrivial" 的最好答案。**

**第 3 条细节:** 文中有的是 (a) 恒等式 $X^\dagger_{\tilde S}\beta_{\tilde S}=\breve F\breve\Lambda'_{\tilde S}\beta_{\tilde S}+\breve U_{\tilde S}\beta_{\tilde S}$ 说明因子误差不破坏 null-swap;(b) $r_{U,NT}$ 经 (C.21)–(C.22) 进入 $\chi_{NT}$,Assumption 4 要求 $\chi_{NT}=O_p(\lambda_{NT})$;(c) 附录 Tables 14/15 模拟显示 $\hat r=2$ 比 $\hat r=4$ 伤 power 更多。**但没有命题陈述这个不对称性。**写 "derive theoretically" 会坐实 overclaiming。

补法很干净:低估 $r$ 时遗漏的共同成分以 $O(1)$ 量级留在 $\hat U$,$r_{U,NT}$ 不趋零,$\chi_{NT}\gg\lambda_{NT}$,Assumption 4 失效,power consistency 崩;高估 $r$ 只是多耗自由度、恶化 rate,不产生不消失的偏差。**写成 Proposition,两页纸,同时回答审稿人 1 的 major 3。**

**第 4 条细节:** 旧版 Related Work 写 "its tuning and data splitting can reduce power",新版删了;第 28 页现在写 "TSKI has low power in these factor designs under the specified tuning; **this is not evidence of an intrinsic weakness**"。不能一边在 response 说 TSKI 保守,一边在正文声明这不构成对方内在弱点。且竞争者保守不是自己的新意,e-BH 保守性是已知结论。唯一站得住的说法是正面的:不需要在时间维度切分子样本,用完整变换样本做推断。

**第 5 条细节:** 只在附录 C 出现("Only the $2\kappa$-dimensional sufficient score is coupled, not the original $T\times N$ data array"),正文几乎看不见。分量比想的大:coupling 维度从 $T\times N$ 降到 $2\kappa$,这才是为什么在序列相关下只需三阶矩就能用 Cattaneo-Masini-Underwood (2025) 的鞅 Yurinskii,并给出 $K_{NT}=o\{(T/\ln T)^{1/5}\}$。**一个不依赖 $N$ 的可检验 rate condition,是审稿人能立刻抓住的硬通货。**

提醒:Lan Gao 是 ARK 的共同作者,对比必须写得大方,同时这也是资产。

**第 6 条细节:** 改成因果链才有力 — Fixed-X 在时序下必须白化 → 白化把问题推到误差过程的分布形式 → 而误差过程恰是宏观金融数据最不听话的地方。所以鞅 coupling 不是"额外放松一个假设",而是白化这一步在真实数据上成立的唯一走法。

### AE 真正在问什么

"simple integration" 的潜台词是:**描述了"组合了什么",没有描述"naive 地组合会坏在哪里"。**六条现在全是"我们做了 X"的形式,没有"直接做 X 会失败,因为 Y"的形式。

**四个失败点(稿子里四个都有对应处理,只是从没这样组织):**

- **(A) 筛选 → 白化的反馈环。** 白化需要 $\hat\Sigma_\varepsilon$,需要残差,高维下需要先筛选。选择误差与 nuisance 估计误差不再独立,前者决定后者。Theorem 2.2 是闭环的定理。
- **(B) 白化 → exchangeability 失效。** Fixed-X 可交换性是设计矩阵的精确代数性质;用 $\hat\Sigma_\varepsilon^{-1/2}$ 变换后设计矩阵变成随机且估计的,精确可交换性没了。修复:条件化在实现设计 $\mathcal G$ 上,只处理 $2\kappa$ 维得分的条件分布。**这不是风格选择,是被逼的。**
- **(C) PCA 与白化不可交换。** 对原始数据做 PCA 与对白化后数据做 PCA 给出不同因子空间,必须用 weighted PCA;再加双正交约束 $V'\breve U=0$、$V'\breve F=0$。别人不需要处理,因为别人不白化。
- **(D) 序列相关 → 分布近似。** 得分是相关项之和,需鞅 coupling;能走通是因为维度已降到 $2\kappa$。

**连起来念:这不是四个模块并联,是一条链,每一环都打破了下一环的成立条件。**

### 具体修改方案

1. **加 §1.1 "Contributions and Technical Challenges"**(约 1.5 页),四个编号条目,统一句式:
   > *Naive approach*: 直接对原始设计做 Fixed-X,再用 Newey-West 白化。
   > *Why it fails*: 白化矩阵是估计的,精确可交换性不再成立;而 $\hat\Sigma_\varepsilon$ 依赖第一步筛选的残差,误差不独立。
   > *Our fix*: 条件化在实现设计上,对 $2\kappa$ 维充分得分做分析。
   > *Result*: Theorem 2.2 显式给出含 $R_{\text{miss}}$ 的 $\omega_{NT}$;Theorem 4.4 给出 FDR $\le q+o(1)$。
2. **补因子个数的 Proposition。**投入产出比最高。
3. **加 comparison table** — 行是 FarmSelect / IPAD / ARK / TSKI / Fixed-X / FAR-Knockoff,列是四个挑战 (A)(B)(C)(D)。
4. **把 coupling 从附录提到正文**,加一小段 "Relation to ARK"。
5. **收回过度对冲的语气。**摘要 "In the simulation designs examined... relative to the implemented competitors",正文 "this is not evidence of an intrinsic weakness" — 一篇被质疑没新意的稿子通篇这种语气会强化"作者自己也不确定贡献是什么"。FDR 控制是定理,不是模拟观察。
6. **Experiment 1 仍是 $\varepsilon_t$ 时间独立的**(第 28 页 "Notably, $\varepsilon_t$ is temporally independent in this experiment")。这次不只是挑刺,而是新意认知问题 — 主打卖点是序列相关而主模拟没有,读者会得出"白化没做任何事"的结论。**做 ablation:去掉白化、去掉 PCA、两个都去掉,看 FDR 和 power 各崩到什么程度。**审稿人说"每个成分都是现成的",最有说服力的回答是"少任何一个方法就坏了,这是数据"。

---

## 第 5 轮 — 我们的 coupling 相对 Fan 他们的有优势吗

**问:** 可以说我们 coupling sufficient stat 得分的理论,比 Fan 他们的 coupling 更有理论优势或一般性吗?这个我拿不准。

**答:可以 claim,但要挑轴。两条轴上占优且能量化,第三条轴上 ARK 严格更一般。**

### 能站住的三点

1. **被 coupling 对象的维度。**最硬的一条。Yurinskii 型 coupling 误差随被耦合向量维度 $d$ 恶化。你耦合 $\zeta = T^{-1/2}U'\varepsilon^\dagger \in \mathbb R^{2\kappa}$;data-level 耦合 $T\times N$ 数据阵。**兑现是 $K_{NT} = o\{(T/\ln T)^{1/5}\}$ 不出现 $N$。**
2. **最小性(sufficiency),最优雅但完全没卖。**Lemma 4.1:给定 $\mathcal G$,factor-adjusted Lasso 及其 knockoff 统计量对误差过程的依赖**只通过** $\zeta$。所以耦合 $\zeta$ 是 lossless 的 — 没有近似任何程序看不见的东西。形式很干净:*我们耦合的恰好是程序作为其函数的那个对象,不多不少*。data-level coupling 必然近似大量与最终统计量无关的信息,那部分误差是白付的。
3. **序列相关下的可行性。**正因对象低维,才能用 Cattaneo-Masini-Underwood (2025) 鞅 Yurinskii,只要三阶矩、predictable weights 和条件二次变差控制。**这是"为什么 score-level 是唯一可行路线"的答案。**

### 不能站住的一点(最要命)

**Lemma 4.1 的充分性是架构特定的。**它成立是因为 $W$ 是 augmented Lasso 路线下得分的函数。换成随机森林重要性或任何非 Lasso 统计量,$2\kappa$ 维得分不再充分,整条路线塌掉。而 **ARK 的 data-level coupling 对 $W$ 不可知** — 任何可测统计量自动继承结论。**这是 ARK 严格更一般的地方。**

还有一层:近似的东西根本不同。ARK 在 Model-X 世界近似**生成 knockoff 用的协变量法则**;你在 Fixed-X 世界条件化掉设计,协变量法则不进入,近似的是**误差/得分的法则**。不在同一根轴上,说谁"更好"是范畴错误。而且你为条件化付了代价:$T>2\kappa+r$、严格外生性。

### 建议:主动交代成本

Assumption C.3(threshold stability)是 coupling 路线的代价 — coupling 扰动不连续阈值,需控制阈值附近 $2\Delta_{NT}$ 带内的 null 统计量。**主动写出来。**任何 coupling 路线都有某种版本,先说显得可信;等审稿人发现,前面所有优势陈述都打折。

### 建议措辞(可直接改)

> Relative to the data-level coupling used in approximate Model-X knockoffs (Fan et al., 2025a), our argument couples a different and much smaller object. Lemma 4.1 shows that, conditional on the realized design, the factor-adjusted Lasso statistics depend on the error process only through the $2\kappa$-dimensional score $\zeta$. Coupling $\zeta$ is therefore lossless for this statistic class: nothing the procedure can see is approximated away. Because the coupled dimension is $2\kappa$ rather than the $T\times N$ array, the coupling error is governed by the screened model size, which yields the primitive rate $K_{NT}=o\{(T/\ln T)^{1/5}\}$, free of $N$, and makes a martingale coupling available under serial dependence with only third moments. The two routes are complementary rather than nested. Data-level coupling applies to arbitrary knockoff statistics, whereas our reduction is tied to the score-measurable statistics in Lemma 4.1; conversely, conditioning on the design removes any need to model the covariate law, at the cost of $T>2\kappa+r$ and the Fixed-X design requirements. The price of the coupling step is Assumption C.3, which is not needed in the Gaussian case.

因为 Lan Gao 在 ARK 署名,AE 读到这样一个把边界划清、主动承认对方一般性的段落,会认为这是**权威定位**而非自我推销。

---

## 第 6 轮 — 核实 ARK 是否也有类似假设且做了低层验证

**问:** 我们论文里有 knockoff threshold stability 的 ad hoc 假设,但 Gao Lan 告诉我他们 2025 年的文章也有类似假设,而那个假设做了 distributional 的 low-level verification,帮我确认下?

**答:确认了,Gao Lan 说得对,而且这个信息比想象中更有用。**(核查了 AoS 发表版原文,非依赖记忆)

### ARK 里对应的假设是 Condition 5

$$(\log p)^{1/\gamma}\sup_{t\in(0,\,G^{-1}(c_1qa_n/p)]}\frac{G(t-b_n)-G(t+b_n)}{G(t)}\to 0$$

其中 $b_n$ 是 Condition 1 的 coupling 精度,$G(t)$ 是 null 统计量尾函数。这就是"落在阈值附近宽度 $b_n$ 的带内的 null 质量必须相对可忽略"。论文自述该比值与生存分析的风险率函数密切相关,当风险率函数足够光滑、在相关区间大致有界时成立;并明确说它对 coupling 精度 $b_n$ 施加了重要限制。机制与动机与我们的 C.3 完全一致。

**顺带:**我们的 C.3 同时承担了 ARK 的 **Condition 4**(null 指示函数弱相依,即 $\mathrm{Var}(\sum_{j\in H_0}\mathbf 1(\tilde W_j>t))$ 的界)和 **Condition 5** 两件事。$\tilde N^\star_{2\Delta}(t)/M^\star(t)$ 比值界对应 Condition 5,$e_{NT}$ 计数界对应稀疏尾情形。可在文中点明,说明 C.3 并不比对方多要什么。

### 低层验证确实做了,两次

- **Lemma 8**(附录 A.2):在 Condition 9、10 下,对 marginal correlation 统计量验证 Condition 5,取 $b_n=\Delta_n$。
- **Lemma 14**(附录 A.3):在 Condition 6、10、11–13 下,对 debiased-Lasso RCD 统计量验证 Condition 5。

配套的 Condition 4 分别由 Lemma 7、Lemma 13 验证。

**但验证是靠什么换来的:**ARK 在 Section 3.2 假定 $X\sim N(0,\Sigma)$,并明确说明高斯分布假设主要就是为了验证 Conditions 4 和 5;若直接假定这两个条件,高斯假设可去掉。Condition 9 要求 $\Sigma^{-1}$ 和 $\Sigma$ 稀疏,正是为了控制 null 指示函数间的相依。

### 这对我们意味着什么

**坏消息:**读过 ARK 的审稿人可以问"人家验证了,你为什么不验证"。

**好消息:我们的结构其实比 ARK 更适合做这个验证,因为我们的参照法则本来就是精确高斯的。**$P_{D^\star}=N(D,\Xi)$ 是协方差匹配的高斯法则,$W^\star$ 是把 $D+\zeta^\star$ 送进同一 Lasso 映射得到的。条件化设计后 $\zeta^\star\mid\mathcal G\sim N(0,\Xi)$ 是**构造出来的**,不是假设出来的。而 ARK 必须**假设协变量高斯**才能到达可做反集中的地方。

**正确说法:**

> ARK 需要通过对协变量分布施加高斯性来验证其 Condition 5;在我们的条件化设计框架下,参照法则 $P_{D^\star}$ 按构造即为高斯,因此同一验证不需要对数据施加任何额外分布假设。

**具体做法:**$\Xi$ 最小特征值已由 Assumption 4 界离零,$W_j^\star$ 是高斯向量 $D+\zeta^\star$ 的分段仿射函数。在活跃集局部稳定的事件上映射局部仿射,$|W_j^\star|$ 有上界密度,带宽 $2\Delta_{NT}$ 的带内概率是 $O(\Delta_{NT})$;再对 $j\le\kappa$ 联合控制,配合 $v_{NT}\Delta_{NT}\to0$ 得到 C.3 两个界。技术难点是 Lasso 映射的不可微点,以及计数版本需跨 $j$ 的相依控制。

---

## 第 7 轮 — 评价"增加 Proposition"的建议

**问:** 别人建议在附录增加一个 Proposition(primitive sufficient conditions for threshold stability),用三个可解释条件推出 Assumption 6:(1) 理想 null statistics 在正阈值附近满足相对 anti-concentration;(2) null band counts 和 tail counts 条件于 $\mathcal G$ 后有足够集中性;(3) 足够多信号把随机 knockoff threshold 限定在有效区间。然后说明在条件高斯得分、设计良好、LCD statistics 密度受控时前两项成立,第三项由 signal abundance 保证。但不建议声称已像 ARK 那样完成全面验证,除非真证明了 Lasso LCD statistic 的条件 anti-concentration — 因为 Lasso 映射分段线性且零点可能有原子,比 debiased Lasso 麻烦。

**答:建议是好的,克制的判断也对。但两处要推一下。**

### 主要风险:三个条件可能被读成"用三个高层假设换一个高层假设"

- **第 3 条(信号充分性锁定阈值)** — 真正的 primitive,可从 Assumption 4 的 signal abundance 直接推出,不是假设。
- **第 2 条(band/tail counts 集中性)** — **也可以做成 primitive,而且应该做。**条件在 $\mathcal G$ 上、参照法则 $\zeta^\star\sim N(0,\Xi)$ 时,这是 ARK Condition 4 的对应物。ARK 用 $\Sigma^{-1}$ 稀疏性验证;我们可用 $\Xi$ 的特征值界替代。
- **第 1 条(相对 anti-concentration)** — 离 C.3 第一款太近。若仍是假设,整个 Proposition 就成了"假设反集中 ⟹ 阈值稳定",审稿人会觉得只是换了个名字。

**建议重组:把 (2)(3) 证出来,让 (1) 成为唯一剩余的高层条件。**陈述变成:

> 在条件高斯得分、设计正则性和信号充分性下,Assumption C.3 可归结为单一条件:LCD 统计量在 $t\ge v_{NT}\Delta_{NT}$ 上的条件密度受控。

这是**真的化简**而非重新打包。目标不是追平 ARK,是不显得随意。

### 关于原子,可以说得更准确

"Lasso 分段线性且零点可能有原子"方向对,但**原子本身其实不进入需要的区间**。

$W_j=|\hat\beta_j|-|\hat\beta_{j+\kappa}|$ 在 $j$ 为 null 时常两项同时为零,$W_j=0$ 有正质量。但 C.3 的 sup 取在 $t\ge v_{NT}\Delta_{NT}$ 上,带宽 $2\Delta_{NT}$,每个带左端点至少是 $(v_{NT}-2)\Delta_{NT}$。既然 $v_{NT}\to\infty$,**零点原子被排除在所有带之外**;$\hat S=\emptyset$ 的情形由 C.3 最后那句 $P\{G\ge v_{NT}\Delta_{NT}\text{ or }\hat S=\emptyset\}\to1$ 单独接住。

真正的困难是**零点右侧小非零值的堆积**:$\hat\beta_j=0$ 而 $\hat\beta_{j+\kappa}$ 取小非零值时 $W_j$ 落在 $0^+$ 附近,密度可能很大。

精确表述有两个好处:指出可行证明路径;**顺带说明我们的 C.3 在这点上比 ARK 的 Condition 5 设计得更好** — ARK 的 sup 取在 $(0,\,G^{-1}(c_1qa_n/p)]$ 上一直到零,我们用 $v_{NT}\Delta_{NT}$ 显式截掉了最难的那块。免费的分。

### 可选加码

想要"至少对某个统计量做到完整验证",捷径是**额外报告一个 debiased-Lasso (RCD) 版本的统计量**。ARK 的 Lemma 14 已对 RCD 做过验证,我们框架里换统计量只是换 $W$ 的构造,充分性归约(Lemma 4.1)不受影响。可以说:对 RCD 统计量 C.3 可完整验证;对默认 LCD 统计量归结为单一密度条件。

---

## 第 8 轮 — 产出附录草稿

**问:** 你在附录里加上我们讨论的类似的验证,以及和 ARK 的对比的内容。

**答:**产出 `appendix_threshold_stability.tex`(323 行)。结构:

- **三个 primitive 条件** PC1(相对 anti-concentration)、PC2(计数集中性)、PC3(阈值局部化)
- **Proposition** PC1–PC3 ⟹ Assumption C.3
- **Lemma C.x.2** 证 PC2
- **Remark C.x.1** 因子调整为何使弱相依条件可信
- **Lemma C.x.3** 证 PC3
- **Remark C.x.2** PC1 归结为条件密度界,并明确两处未闭合的缺口
- **Remark C.x.3** 与 ARK 的完整对比

### 三点需要注意的发现

1. **PC2 需要的不只是特征值界。**尝试仅从 Assumption 4 的特征值条件证明,走不通 — 对非对角元做 Cauchy–Schwarz 给出 $\kappa_0^{3/2}$,相对 $[\kappa_0\bar G]^2$ 太大。**这正是 ARK 施加精度矩阵稀疏性而非仅条件数界的原因。**所以 Lemma C.x.2 假设了对**得分**相关矩阵的弱相依条件。

   **这反而是个收获:**得分由 $\breve U_{\tilde S}$ 构造,共同成分已被 weighted PCA 和 (3.15) 移除,所以需要的弱相依性正是由因子调整提供的 — 在未调整设计上会直接失败。Remark C.x.1 写了这个论证,**它给 §1.1 的故事增加了第四个不可拆解的理由:PCA 不只是 power 装置,它是使 threshold-stability 路线可用的前提。**

2. **PC3 完全证出。**Lemma C.x.3 从 Assumption 4 的 signal abundance 加 Theorem 4.5 的机器推出,不需新假设。

3. **原子不是问题,而且要明说。**(3.18) 的 $\mathcal{W}$ 已按构造排除零,$I_{NT}$ 从 $v_{NT}\Delta_{NT}/2$ 起且 $v_{NT}\to\infty$,所以没有任何带碰到原子。真正困难是 $\hat\beta_j=0$ 而 $\hat\beta_{j+\kappa}$ 小时零点右侧的密度堆积。这样精确陈述比承认"原子是问题"好,并引出 ARK 的 Condition 5 取 sup 到原点而我们做了截断这一设计优势。

**净结果:**Assumption C.3 归结为 PC1 单条,而 Remark C.x.2 进一步把它归结为局部仿射事件上成立的条件密度界。两处缺口写成缺口:实现活跃集上的并集控制,以及零点收缩邻域。

**一处全局修改建议:**论文用 $\mathcal{G}$ 表示 sigma-field,用 $G$ 表示 (3.18) 的阈值。在这个附录里两者不断冲突,建议全文把阈值改名为 $\mathcal{T}$。

---

## 待办清单汇总

### 最高优先级

- [ ] 加 §1.1 "Contributions and Technical Challenges",四条 (A)(B)(C)(D),统一 naive/fails/fix/result 句式
- [ ] Experiment 1 主设计加入时间相依误差
- [ ] Ablation 实验:去白化 / 去 PCA / 两者都去
- [ ] 补因子个数低估损害 power consistency 的 Proposition

### 高优先级

- [ ] 插入 `appendix_threshold_stability.tex`,补 Lemma C.x.2、C.x.3 的完整证明
- [ ] 把 score-level coupling 从附录提到正文,加 "Relation to ARK" 段
- [ ] 加四挑战 × 六方法的 comparison table
- [ ] IPAD 进入模拟对比
- [ ] 全局把阈值 $G$ 改名为 $\mathcal{T}$

### 中优先级

- [ ] 从新意清单删除 TSKI 保守性,改为正面表述
- [ ] 收回摘要与正文的过度对冲语气
- [ ] $\gamma=1/5$ 给出理由
- [ ] tuning 参数($\xi$、$\lambda$、$m$、$\ell_T$)敏感性表
- [ ] 结论加 limitation 段(严格外生性)
- [ ] $\theta$ 作为 unrestricted nuisance 的表述与 Remark 4.1 连起来
- [ ] 实证部分补 rolling window 长度敏感性、选择随机性影响

### 可选

- [ ] 额外报告 debiased-Lasso (RCD) 统计量版本,以获得对某一统计量的完整 C.3 验证
