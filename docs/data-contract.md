# 合成资料约定

资料用于本地业务流程演练，字段仅记录事实来源，不预先裁定业务结果。

- `products.csv`：商店商品规格及生命周期。字段为 `product_id, design_id, format, price, first_sale, show_id, replacement_id`。
- `stock_events.csv`：补货、盘点、跨点调拨和展期结转。字段为 `event_id, product_id, location, event_date, event_type, quantity, batch_id`。
- `sales_events.csv`：销售、退货、赠送、取消订单与退款事实。字段为 `event_id, product_id, location, event_date, event_type, quantity, order_ref`。
- `display_and_supply.csv`：陈列暴露、供货时间和采购约定。字段为 `product_id, location, visible_from, visible_to, display_level, supplier, min_order, lead_days, unit_cost`。
- `artist_terms.csv`：艺术家分成按商品类型和批次适用。字段为 `term_id, artist_key, design_id, product_format, rate, valid_from, valid_to, basis`。

空字段表示事实尚未提供，`pending`、`review`、`hold` 等状态表示来源记录尚未形成最终确认。不同来源以事件日期或有效期表达的时间含义不相同，调用方应结合表名和字段解释；不能仅因编号相同就假定两条记录可合并。金额以资料中记载的名义单位表示，没有统一换算或预先扣除退款。
