# 演示记录与功能覆盖

## 2026-11-10 编号导览补充

新增 `18-current-main-raw.png`：当天从用户已打开的 OrganoidAnalysisDeveloper 窗口获取的未导入图像状态截图。新增 19–22 四张橙色编号导览，分别对应主界面、Charts、Clustering 和分割结果，并在 README 中逐号解释。

19 以 18 为底图，20 以 04 为底图，21 以 09 为底图，22 以 03 为底图。采用内置图像编辑工具，不是重新运行软件得到的新结果；存在局部文字、曲线或图像细节重绘风险，故仅用于说明区域位置，不能作为原始测量或显微图像证据。原图全部保留并链接。

编辑提示要求：保留完整布局，仅加橙色矩形框及数字圆标；主界面 1–9、Charts 1–7、聚类 1–8、结果页 1–6，编号含义见 README。未修改软件代码和数据。

## 来源与结果

- 日期：2026-11-05；程序：`dist_release_2_21/OrganoidAnalysis/OrganoidAnalysis.exe`。
- 输入：`Sample_Data` 中 3 张 TIFF；登录由用户本人完成。
- 截图：`docs/images/01` 至 `17`，均为真实桌面操作截图。
- 本次未修改生产代码、发布 GitHub 仓库或上传数据。
- 目的为操作说明，不是算法精度、性能或生物学结论验证。

运行参数：Threshold 0.50、Batch Size 16、Edge Sigma 2.0、Edge Min 0.05、Edge Max 0.10、Min Area 100、Concurrent 2。启用 Overlay、ID Labeled、Properties (Excel)、Segmentation、Crop。

| 图片 | 对象数 |
| --- | ---: |
| Stitched[ZProj[Bright Field]]_C2_1_001.tif | 126 |
| 大-P2-3D-7d-4X.tif | 241 |
| 小-P2-3D-14d-4X-1.tif | 215 |

合计 582；界面报告 8.30 秒。对象数已通过汇总 Excel 与明细工作簿非空计数核对。

所选目录为 `readme_demo_20261105/native_results`，实际结果位于 `readme_demo_20261105/native_results_1`。截图 03 的第 4 个输入是为预览重新导入的 overlay，不参与上述三图分割统计。

明细工作簿有 13 个指标工作表：Area、Axis Major Length、Axis Minor Length、Centroid、Eccentricity、Equivalent Diameter Area、Euler Number、Extent、Feret Diameter Max、Orientation、Perimeter、Perimeter Crofton、Solidity。界面整理后显示 582 对象、3 图片、12 数值特征；Centroid 不是普通标量特征。

## 验证范围

| 功能 | 状态 | 证据 |
| --- | --- | --- |
| 文件夹导入、追加导入 | 已操作 | 01、03 |
| 三图批量分割 | 完成 | 02、两个 Excel |
| Overlay / ID 输出 | 文件存在 | label_image 中 6 个 TIFF |
| 对象与统计目录 | 已检查 | Analysis_result、seg、Histograms |
| 叠加分布与 X 范围 | 已绘图 | 04，Area 0–5000 |
| 合并分布 | 已绘图 | 05 |
| 箱线、小提琴图 | 已绘图 | 06、10 |
| 图片级柱状、折线图 | 已绘图 | 07、11 |
| 单图形态聚类 | 完成 | 08，K=3，5/66/55 |
| 联合形态聚类 | 完成 | 09，K=3，219/340/23 |
| 人工移动对象 | 完成 | 12，调整后 220/339/23 |
| 全类别统计导出 | 完成 | 13，实际文件已检查 |
| EfficientNetB3 聚类 | 完成 | 14，K=3，246/87/249 |
| 比例尺标定 | 只进入模式并取消 | 16，无可靠比例尺数值 |
| 区域框选、恢复全图 | 已操作 | 17，未重新分析区域 |
| 图层 PNG/TIFF 导出 | 只展示菜单 | 15，未执行保存 |
| Charts PNG 导出 | 按钮可见 | 未执行保存 |
| 指定类别组合导出 | 入口存在 | 未执行 |
| Slider / Split / Grid 与结果配对 | 未验证成功 | 不作为测试通过宣传 |
| 账户、授权与项目管理 | 不在范围内 | 未测试安全与权限管理 |

聚类导出目录：`readme_demo_20261105/cluster_export/Cluster Analysis`，含 3 个类别明细工作簿、参数图与一个汇总工作簿。导出发生在人工调整形态聚类之后、重新运行图像特征聚类之前。人工移动仅为操作演示，不是标签校验。

## 发布前注意事项

1. 输出目录追加后缀后，完成提示与实际路径不一致，结果层未自动显示。建议统一实际输出路径、提示和图层加载。
2. 图表中文标签缺字体，聚类窗口部分控件拥挤。截图保留真实界面，没有伪造修复效果。
3. X range 设置显示范围，不过滤 Excel 数据；当前源代码对各图片分别生成直方图分箱，统一坐标不等于统一分箱。
4. 分布图为计数，对象量不同应考虑归一化；合并分布不等于图片等权。
5. 正式下载地址、平台信息、联系人与许可证仍待发布者确认；文档打包不代表已经公开发布。

## 文档交付说明

根目录 README.md 是用户版入口，图片为相对路径，可随目录上传。原有 README 已备份为 `docs/README.previous-20261105.md`，不纳入用户图文上传包。上传包仅包含 README、本记录及 17 张截图，不含软件运行包、账户文件或原始实验数据。
