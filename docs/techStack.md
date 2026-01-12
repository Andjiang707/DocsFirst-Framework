# 🛠 Tech Stack & Implementation Guide

## 1. 技術棧選型 (Tech Stack)

| Category | Technology | Version | Justification |
| --- | --- | --- | --- |
| **Framework** | **React** | **v18+** | 穩定且生態系豐富。 |
| **Build Tool** | **Vite** | **Latest** | 極速開發體驗。 |
| **Styling** | **Tailwind CSS** | **v3.4+** | 快速切版，無需切換檔案。 |
| **State** | **Zustand** | **Latest** | 比 Redux 更輕量，適合小型 App。 |
| **Audio** | **use-sound** | **Latest** | 處理 React 中的音效播放。 |

---

## 2. 關鍵實作規範 (The Rules)

### 2.1 狀態管理 (Zustand)
為避免 AI 寫出過度複雜的 Context 或 Redux，請嚴格遵守以下 Zustand 寫法：

```typescript
// store/useTimerStore.ts
import { create } from 'zustand'

interface TimerState {
  timeLeft: number
  isActive: boolean
  start: () => void
  pause: () => void
  reset: () => void
}

export const useTimerStore = create<TimerState>((set) => ({
  timeLeft: 25 * 60,
  isActive: false,
  start: () => set({ isActive: true }),
  pause: () => set({ isActive: false }),
  reset: () => set({ isActive: false, timeLeft: 25 * 60 }),
}))
```

### 2.2 音效處理 (use-sound)
請使用 `use-sound` hook 來處理音效，**不要**直接使用 HTML5 `Audio` 物件，以避免 React Lifecycle 問題。

```typescript
import useSound from 'use-sound';
import boopSfx from '../../sounds/boop.mp3';

const BoopButton = () => {
  const [play] = useSound(boopSfx);
  return <button onClick={play}>Boop!</button>;
};
```

### 2.3 樣式規範 (Tailwind)
- 禁止使用 CSS Modules 或 styled-components。
- 顏色請使用 Tailwind 預設的 `slate` 色系作為黑白主調。
- **RWD**: Mobile First，使用 `md:` 前綴定義桌面版樣式。

## 3. 版本鎖定 (Version Locking)
為確保相容性，初始化 `package.json` 時請明確指定：
- `react`: "^18.2.0"
- `react-dom`: "^18.2.0"
- `zustand`: "^4.5.0"
