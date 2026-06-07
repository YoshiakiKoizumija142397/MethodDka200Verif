# MethodDka - 200-Digit Precision Polynomial Solver with Complex Residual Verification

[![JavaScript](https://shields.io)](https://mozilla.org)
[![Precision](https://shields.io)]()
[![Environment](https://shields.io)]()

本プロジェクトは、複素数多項式（代数方程式）のすべての根を同時に決定する**Durand-Kerner (DK) 法**（別名: MethodDka）の実装です。
一般的な64ビット環境の限界を遥かに超越した**「小数点以下200桁」**の極限の精度で計算を行い、さらに求まった解の理論的正当性をその場で証明する**「Horner法拡張型の自動検算（残差評価）システム」**を完全にローカル（オフライン）環境向けに統合・最適化した数値計算ソフトウェアのマスターリポジトリです。

---

## 🎯 開発目的と仕様要件 (Requirements Specification)

本システムは、以下の厳格な数値計算およびUI要件を満たすように設計されています。

1. **完全なローカル・スタンドアロン動作**
   * 外部ネットワーク（インターネット）への通信を一切行わず、セキュリティ制限（CORSエラー等）に干渉されない「ファイル分割構成」を採用。
   * 同一フォルダ内の `./decimal.js` から超高精度浮動小数点演算エンジンを安全にロードする。
2. **動的UIの完全性と堅牢性**
   * ユーザーが指定した最高次数 n に基づき、エラー（`TypeError` や変数の未初期化エラー）を一切起こさず、入力欄（\(a_n\) から a₀ まで）を100%確実に動的展開する。
3. **200桁多精度複素数演算の安定収束**
   * 最大反復ループ数を `800回`、収束判定の許容値を `1e-195` に設定。
   * 第8世代インテルプロセッサ（Windows 11）環境下のブラウザがハングアップ（フリーズ）しないよう、計算ステップごとの負荷バランスを極限まで最適化する。
4. **Horner法（複素数拡張版）による厳密な残差評価**
   * 計算完了直後、求まった各複素数解を元の多項式 P(z) にHorner法を用いて最速かつ丸め誤差を最小に抑えて代入。
   * 得られた実部残差、虚部残差、および複素絶対誤差を精密な指数表記（例: `1.2345e-196`）で出力し、数学的に正しく解けていることをユーザー自身が検証できるようにする。

---

## 📁 ディレクトリ構成 (Directory Structure)

手動アップロードおよびローカル検証を行うため、1つのフォルダ内に以下の構成を維持します。

```text
📁 MethodDka200/  (任意の検証用フォルダ)
├── 📄 MethodDkaVerif.html  (ローカルデバッグ・検証用メインコード)
├── 📄 index.html           (世界標準準拠・上記と同一内容の複製)
├── 📄 decimal.js          (公式高精度演算ライブラリ本体 - 別途配置)
└── 📄 README.md            (本仕様書)
```

### ⚠ 事前準備
同じフォルダに公式の [cdnjs(decimal.min.js)](https://cloudflare.com) のソースコードを丸ごとコピーした **`decimal.js`** を配置してください。

---

## 📋 動作環境 (Tested Environments)

- **OS:** Windows 11 (第8世代 Intel Core プロセッサ環境環境にて検証)
- **Browser:** Google Chrome / Microsoft Edge (開発者ツール Console にてエラー0を厳守)

---

## 📄 ライセンス (License)

This project is licensed under the MIT License.
