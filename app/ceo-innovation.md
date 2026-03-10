# MeetFlow 核心功能提案：Line 行程智慧偵測引擎 (MVP)

[cite_start]作為 CEO，我親自參與了此項核心功能的邏輯開發，旨在解決使用者在通訊軟體與日曆工具之間資訊分散的痛點 [cite: 13, 25]。

## 1. 功能概述
[cite_start]本功能透過 Webhook 監聽通訊軟體（如 Line/Slack）的特定對話，當偵測到包含「時間」、「地點」或「動作」的關鍵字時，系統將自動提取資訊並推播同步請求 [cite: 27, 31]。

## 2. 核心邏輯 (CEO Logic Implementation)
```javascript
// 智慧辨識關鍵字邏輯雛形
function detectScheduleFromMessage(message) {
    const timeKeywords = ["明天", "下週", "下午", "點"];
    const actionKeywords = ["開會", "預約", "見面", "討論"];
    
    // 檢查訊息中是否包含時間與動作關鍵字
    const hasTime = timeKeywords.some(kw => message.includes(kw));
    const hasAction = actionKeywords.some(kw => message.includes(kw));

    if (hasTime && hasAction) {
        return {
            status: "detected",
            suggestion: "偵測到新的會議需求，是否一鍵同步至 MeetFlow 日曆？",
            originalMessage: message
        };
    }
    return { status: "none" };
}