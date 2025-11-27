<script>
  window.mermaidConfig = {
    gantt: {
      axisFormat: '%Y/%m/%d'
    },
    // 此設定強制 Mermaid 使用英文語系，以防止環境自動添加「年」「月」「日」等中文字
    startOnLoad: true,
    securityLevel: 'loose',
    theme: 'default',
    fontFamily: 'sans-serif',
    flowchart: {
      use=strict: true,
    }
  };
</script>

```mermaid
gantt
    dateFormat  YYYY-MM-DD
    title       硬體專案開發甘特圖 (以台灣工作日計算)
    axisFormat  %Y/%m/%d
    excludes    weekends

    section 專案階段
    EVT (80工作天) :done, evt, 2025-11-24, 2026-03-25
    DVT (80工作天) :active, dvt, after evt, 2026-07-21
    PVT (77工作天) :pvt, after dvt, 2026-11-09

    section 重要里程碑
    專案啟動 :milestone, m1, 2025-11-24, 0d
    EVT 完成 :milestone, m2, after evt, 0d
    DVT 完成 :milestone, m3, after dvt, 0d
    PVT 完成 (專案結束) :milestone, m4, after pvt, 0d
