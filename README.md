# MethodDka - 200-Digit Precision Polynomial Solver with Complex Residual Verification

[![Project Status: Requirement Specified](https://shields.io)]()
[![Precision Requirement](https://shields.io)]()

本リポジトリは、複素数多項式のすべての根を同時に決定する**Durand-Kerner (DK) 法**（MethodDka）を用いた、小数点以下200桁の超高精度多項式解法およびHorner法拡張型自動検算システムの**「ソフトウェア開発要求仕様書」**です。

---

## 🎯 ソフトウェア要求定義 (Software Requirements Specification)

本システムの実装コード（将来開発される成果物）が満たすべき、数学的および数値計算的な厳格な要件は以下の通りです。

### 1. ランタイム環境要件 (Runtime Environment)
* **オフラインファースト構成:** ブラウザのローカルセキュリティ制限（CORSポリシー）に妨害されずオフラインで安定稼働するため、同一フォルダ内の `./decimal.js` から演算エンジンを静的ロードすること。
* **ターゲット:** Windows 11（第8世代インテルプロセッサ環境）上のモダンブラウザ環境でハングアップ（フリーズ）せずに動作すること。

### 2. コア演算アルゴリズム要件 (Core Math Algorithms)
* **解探索エンジン:** Durand-Kerner法（漸化式補正ループ数: 最大800回、収束条件: 10⁻¹⁹⁵）を採用し、複素数の根を同時に200桁まで追い込むこと。
* **自動検算エンジン:** 複素数拡張版Horner法（ホーナー法）を採用。求まった各解を元の多項式 P(z) に代入し、実部残差・虚部残差、および絶対誤差を精密な指数表記（例: `1.23e-196`）で自動出力すること。

### 3. UI/UX 展開要件 (User Interface)
* 入力された最高次数 n に対し、JavaScriptの変数未初期化エラーやスコープ競合を完全に排除し、\(a_n\) から a₀ までの係数入力欄を100%確実に動的自動展開すること。

---

## 📁 リポジトリ構成要件 (Repository Directory standard)

本プロジェクトは、仕様書と成果物を一元管理するため、以下の世界標準の構成を厳守します。

```text
📁 MethodDka200/
├── 📄 index.html      (開発要求仕様書・グラフィカルWebポータル)
├── 📄 README.md        (本仕様書・リポジトリ解説ドキュメント)
└── 📄 [decimal.js]     (※将来のデバッグ検証時に同階層に配置する高精度ライブラリ)
```

---

## 📋 動作環境 (Tested Environments)

- **OS:** Windows 11 (第8世代 Intel Core プロセッサ環境環境にて検証)
- **Browser:** Google Chrome / Microsoft Edge (開発者ツール Console にてエラー0を厳守)

---

## 📄 ライセンス (License)

This project is licensed under the MIT License.

---

## 👤 開発者情報 & 謝辞 (Developer Profile & Acknowledgments)

* **設計・開発責任者:** Yoshiaki Koizumi (小泉 嘉章)
* **公式GitHubリポジトリ:** [YoshiakiKoizumija142397](https://github.com)
* **活動拠点:** 日本、茨城県牛久市 (Ushiku city, Ibaraki pref, Japan)
* **公式サイト:** [https://jimdofree.com](https://jimdofree.com)

> ### 🙏 謝辞 (Acknowledgments)
> 本要求仕様書および数理設計は、**Microsoft Windows Copilot** と **Google Gemini** によって生成されました。ここに深く感謝申し上げます。
