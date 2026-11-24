# 展览商店选品、缺货需求与跨展期补货

本项目保存视觉艺术机构日常业务分析使用的合成演练资料，样例不代表真实机构、作品、交易或研究结论。

## 资料

- `products.csv`：商店商品规格及生命周期。字段为 `product_id, design_id, format, price, first_sale, show_id, replacement_id`。
- `stock_events.csv`：补货、盘点、跨点调拨和展期结转。字段为 `event_id, product_id, location, event_date, event_type, quantity, batch_id`。
- `sales_events.csv`：销售、退货、赠送、取消订单与退款事实。字段为 `event_id, product_id, location, event_date, event_type, quantity, order_ref`。
- `display_and_supply.csv`：陈列暴露、供货时间和采购约定。字段为 `product_id, location, visible_from, visible_to, display_level, supplier, min_order, lead_days, unit_cost`。
- `artist_terms.csv`：艺术家分成按商品类型和批次适用。字段为 `term_id, artist_key, design_id, product_format, rate, valid_from, valid_to, basis`。

记录之间通过 `*_id`、`*_key` 或 `*_ref` 字段关联。日期采用 ISO 格式；空值表示来源未提供该事实，不代表数值为零。不同来源的统计范围和状态以 `docs/data-contract.md` 为准。样例中保留了待确认、取消、缺失和版本变化等原始情况，不包含预先计算的分析结论。

## 运行

需要 Python 3.11 或更高版本，无第三方依赖。运行 `python3 -m unittest discover -s tests -v` 可检查资料编码、字段和记录结构。
