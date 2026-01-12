# CLAUDE.md - AI Memory & Guidelines

## 📍 專案資訊
- **專案名稱**: FocusFlow (番茄鐘)
- **核心路徑**: `f:/GIT/DocsFirst-Framework`

## 🔨 常用指令
- `npm run dev`: 啟動開發伺服器
- `npm run build`: 建置生產版本
- `npm run lint`: 執行 ESLint 檢查

## ⚡️ Coding Style & 規範
1. **Docs-First**: 在修改程式碼前，先確認 `docs/prd.md` 與 `docs/techStack.md` 是否有對應規範。
2. **Functional Only**: 全面使用 React Functional Components 與 Hooks。
3. **TypeScript**: 所有檔案必須是 `.ts` 或 `.tsx`，嚴禁使用 `any`，必須定義 Interface。
4. **Tailwind**: 使用 Utility classes，不寫額外 CSS 檔案。
5. **Naming**:
   - Components: PascalCase (e.g., `TimerDisplay.tsx`)
   - Functions/Vars: camelCase (e.g., `handleStart`)
   - Constants: UPPER_SNAKE_CASE (e.g., `DEFAULT_TIME`)

## 🚫 禁止行為
- 禁止創建 `class` based components。
- 禁止引入未在 `techStack.md` 中列出的第三方套件。
- 禁止自行決定 UI 配色，需遵循 PRD 的黑白極簡規範。

## 🤖 AI Agent 角色定義

### Agent 1: Architect (架構師)
**職責**: 負責專案初始化與架構設計。
**Skills**:
- 根據 `prd.md` 與 `techStack.md` 生成完整的專案骨架 (Scaffold)。
- 定義資料夾結構、檔案命名規範。
- 建立 `package.json` 並鎖定版本。

**觸發時機**: 專案啟動時，或需要重構架構時。

### Agent 2: Feature Developer (功能開發者)
**職責**: 實作具體功能模組。
**Skills**:
- 根據 PRD 的功能需求，撰寫 React Components。
- 實作狀態管理 (Zustand)。
- 整合第三方套件 (如 use-sound)。

**觸發時機**: 開發新功能或修改現有功能時。

### Agent 3: Stylist (樣式工程師)
**職責**: 負責 UI/UX 實作與 RWD。
**Skills**:
- 使用 Tailwind CSS 實作設計稿。
- 確保 Mobile First 與響應式設計。
- 遵循 PRD 中的視覺規範 (如黑白極簡風格)。

**觸發時機**: 需要調整介面或優化視覺體驗時。

### Agent 4: Debugger (除錯專家)
**職責**: 修復 Bug 與效能優化。
**Skills**:
- 分析錯誤訊息與 Console Logs。
- 使用 TypeScript 型別檢查避免錯誤。
- 優化 React 渲染效能 (useMemo, useCallback)。

**觸發時機**: 出現錯誤或效能問題時。

## 🎯 Skills 技能庫

### Skill: Generate Scaffold
**描述**: 根據技術棧一次性生成完整專案結構。
**輸入**: `techStack.md`
**輸出**:
```
src/
├── components/
│   ├── TimerDisplay.tsx
│   └── ControlButtons.tsx
├── store/
│   └── useTimerStore.ts
├── hooks/
│   └── useTimer.ts
├── App.tsx
└── main.tsx
```

### Skill: Implement State Management
**描述**: 使用 Zustand 建立全域狀態。
**參考範例**: 見 `techStack.md` 第 2.1 節。
**禁止**: 使用 Redux 或 Context API。

### Skill: Apply Tailwind Styling
**描述**: 使用 Tailwind Utility Classes 實作樣式。
**規範**:
- Mobile First: 預設樣式為手機版，使用 `md:` 定義桌面版。
- 色系: 使用 `slate` 系列 (slate-50, slate-900)。
**禁止**: 撰寫自訂 CSS 檔案。

### Skill: Integrate Audio
**描述**: 使用 `use-sound` hook 處理音效。
**參考範例**: 見 `techStack.md` 第 2.2 節。
**禁止**: 直接使用 HTML5 Audio API。
