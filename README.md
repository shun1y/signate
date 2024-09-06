# SIGNATE Cup 2024

SIGNATE Cup 2024コンペのリポジトリ(https://signate.jp/competitions/1376)

### 最終結果
- public: 0.8327343
- private: 0.8347299 
- rank: 361/1226 (上位29%)
<img width="806" alt="image" src="https://github.com/user-attachments/assets/f387fcea-0a1e-4372-ac31-3b04bc7205cb">

### 総括
- 前処理を丁寧にし、欠損値を補完せず、質的データをlabel encordingしたcatboostが最も精度が高かった。
- 特徴量エンジニアリングでは意味のある指標の掛け合わせが精度向上に寄与した

### やったこと

- 前処理  
  - 単位を揃える  
  - 表記揺れの名寄せ修正
    - マスタを作成後、編集距離が最短のものに寄せる
  - 異常値の修正
  - 複数情報を持つカラムの分割
- 特徴量エンジニアリング
  - 量データ × 量データ
    - 正規化後、掛け合わせ  
  - 量データ × 質データ
    - 正規化とtarget encording後掛け合わせ
  - 質データ × 質データ
    - target encording後掛け合わせ
- 欠損値の補正 
  - 代表値の代入
  - 回帰代入法（GBDT）
- モデルの作成  
  - lightGBM
  - catboost
- モデルの評価
  - クロスバリデーションでAUCをみる
- モデルのパラメータチューニング
  -   GridSearch
- アンサンブル
  - 複数モデルの平均を取る  

### やれなかったこと
- 不均衡データへの適応

### 上位者の解法
bronze(https://resweater.hatenablog.com/entry/2024/09/03/202547?utm_source=substack&utm_medium=email)
