# 🗺️ MLIT Geospatial Data Challenge (2nd) – 13th Place Solution

SIGNATE主催  
**「第2回 国土交通省 地理空間情報データチャレンジ」13位解法まとめ**  
(MLIT Geospatial Data Challenge – 13th place solution)

---

## 📌 概要

本リポジトリは、SIGNATE主催  
**「第2回 国土交通省 地理空間情報データチャレンジ」** において  
**13位を獲得した解法・分析内容**をまとめたものです。

地価公示・駅情報・学校・人口メッシュなど  
複数の地理空間データを統合し、

> **不動産価格（売買価格）の予測精度向上**

を目的とした機械学習モデルを構築しました。

---

## 🏆 コンペティション情報

- 主催：SIGNATE × 国土交通省
- コンペ名：第2回 国土交通省 地理空間情報データチャレンジ
- 最終順位：**13th place**
- 評価指標：**MAPE**

---

## 📊 使用データ

主に以下のデータを利用しました：

- 物件データ（配布された train / test）
- 地価公示データ（L01 / L02）
- 駅データ（S12：駅位置・乗降客数）
- 学校データ（P29）
- 人口メッシュ（1km メッシュ）
- 建物・物件属性データ

※ 生データはコンペ規約に従い、本リポジトリには含めていません。

---

## 🛠️ 特徴量エンジニアリング

本解法の中心となる工夫点です。

- **平米単価を用いたターゲット変換**
- **専有面積の欠損値・外れ値を簡易モデルで補完**
- **タグ情報に対して価値情報を付与**
- **最近傍探索による地価・駅・学校特徴量**
- **特徴量同士の四則演算による派生特徴量作成**
- **高額物件の挙動を考慮した特徴量設計**

---

## 🤖 モデル

以下のモデルを使用し、アンサンブルを行いました。

- LightGBM
- XGBoost
- CatBoost

各モデルのOOF予測を用いて  
**スタッキングによるアンサンブル**を実施しています。

---

## 📈 結果

- 単一モデルよりもアンサンブルにより安定した精度を達成
- **Public LB：17位 / Private LB：13位**

---

## 📁 ディレクトリ構成
.
├── notebooks/        # 分析・実験用ノートブック
├── data/             # train/testデータや国土数値情報データ、前処理後のデータ格納先
├── models/           # 学習後のモデル格納先
├── oof/              # OOF予測結果
├── submissions/      # 提出ファイル
├── README.md

## 🚀 実行環境

Python 3.10

numpy / pandas / scikit-learn

lightgbm / xgboost / catboost

geopandas / shapely / scipy

## 📝 注意事項

データはコンペ規約により公開していません

再現にはSIGNATE公式データが必要です

## 🙋‍♂️ Author

GitHub: @NakamuraRio

University: Kanazawa Institute of Technology

Interest: Data Science / Geospatial Analysis / Machine Learning
