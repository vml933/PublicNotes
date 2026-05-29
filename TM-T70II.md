# Printer Status Detection — C# Sample Reference

## SDK

1. Download **[EPSON OPOS ADK for .NET](https://download-center.epson.com/softwares/?device_id=TM-T70II&os=WIN1164&language=zh-TW&region=TW)**.
2. Unzip the file, examples at Sample\E.

---

## The detection event

| Mechanism | Handler method | Fires when | What to inspect |
|---|---|---|---|
| **StatusUpdateEvent** | `OnStatusUpdateEvent(object source, StatusUpdateEventArgs e)` | Device state changes (paper, cover, power) | `e.Status` |

The event must be wired up first: `AddStatusUpdateEvent(m_Printer)`.

---

## Status conditions → `OnStatusUpdateEvent` switch on `e.Status`

**File:** `CSharp/Printer/PrinterSample_Step11/FrameStep11.cs` — method `OnStatusUpdateEvent` at **line 1504**, switch block **lines 1514–1533**.

| Condition | Constant (`e.Status ==`) | Line |
|---|---|---|
| **Paper-roll NEAR-END** | `PosPrinter.StatusReceiptNearEmpty` | 1530 |
| **Paper-roll EMPTY** | `PosPrinter.StatusReceiptEmpty` | 1521 |
| Paper OK | `PosPrinter.StatusReceiptPaperOK` | 1529 |
| **Cover OPEN** | `PosPrinter.StatusCoverOpen` | 1517 |
| Cover closed (OK) | `PosPrinter.StatusCoverOK` | 1525 |
