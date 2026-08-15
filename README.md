# 卒業研究：チラシ掲載商品を起点としたレシピ探索支援

## 日本語

### 現在の研究題目（暫定）

チラシ掲載商品を起点とし、ユーザ嗜好・制約を考慮したレシピ探索支援システムの提案と評価

題目中の「制約」に含める具体項目は検討中です。苦手食材、希望調理時間、料理カテゴリなどについて、チラシ、楽天レシピAPIおよびユーザ入力から利用できる情報を確認したうえで確定します。

### 研究概要

本研究では、チラシに掲載された商品販売情報と、楽天レシピAPIから取得したレシピ材料情報を対応付け、ユーザの嗜好・制約を考慮したレシピ候補と提示理由を示すことで、チラシ掲載商品を起点としたレシピ探索を支援するシステムを検討します。

研究の中心は、システムが唯一の正解レシピを決定することではありません。ユーザが、チラシ掲載商品を使える候補を探し、自身の条件を確認し、複数の候補を比較して、納得できるレシピを選択する過程を支援することです。候補生成や順位付けは、この探索支援を実現するための手段として用います。

現在の方法では、次の処理を想定しています。

1. 採用したチラシPDF内の埋め込み画像を直接抽出し、商品、販売枠、区画、価格、販売期間、販売条件、注意書きなどの関係を保った商品販売情報を構造化する。
2. チラシ商品名と楽天レシピAPI由来の材料名を、共通材料名へ正規化する。
3. チラシ商品とレシピ材料を対応付ける。
4. 対応付け結果に基づいて、チラシ掲載商品を利用できるレシピ候補を生成する。
5. ユーザの嗜好・制約を反映し、説明可能な候補生成・順位付けを行う。
6. 同一のチラシおよび同一の固定レシピ集合を用いる手動探索UIと提案システムを比較する。

### 評価の観点

現時点では、次の三つの観点から評価する予定です。

- 商品販売情報の構造化、対応付けおよび候補生成の成立性：チラシから各項目と項目間の関係をどの程度正確に再現し、商品名・材料名を正規化して対応付け、どの範囲の商品について妥当なレシピ候補を生成できるか。
- 客観的な探索効率：手動探索UIと比較して、レシピ決定までの時間や検索・閲覧等の操作量を減らせるか。
- 主観的な探索支援効果：主観的作業負荷、探しやすさ、条件適合感、チラシ商品との関係の理解、選択への納得感を改善できるか。

第一の観点は、次の三段階を一つの技術的なResearch Questionとして扱います。

1. 商品販売情報の抽出・関係構造化
2. チラシ商品名とレシピ材料名の正規化・対応付け
3. 妥当なレシピ候補の生成

研究題目、Research Question、評価指標および研究範囲は現時点の暫定版であり、原資料の再確認、処理フローの具体化、予備評価・予備実験、指導教員との確認により更新する可能性があります。

### このリポジトリの役割

本リポジトリは、卒業研究の概要と、公開可能であることを確認した成果物を掲載するための公開リポジトリです。楽天ウェブサービスへ登録するアプリケーションの公開窓口としても使用しています。

コードや技術文書は、内容、秘密情報の有無、利用条件および権利関係を確認したうえで追加します。前処理、正規化、実験準備および分析に関する内部作業は、公開範囲を分けて管理します。本リポジトリには、公開してよいことを確認した内容だけを反映します。

### 公開しない情報

- APIキー、アクセストークン、パスワードなどの認証情報
- APIから取得した生のレスポンスや累積データ
- 再配布の可否を確認していないチラシPDFや画像
- 正規化辞書の全件データ
- 個人を特定できる実験参加者情報や実験データ
- 内部の作業資料、分析資料および生のログ

これらの情報は、本リポジトリへ保存せず、利用条件、公開範囲および個人情報の取扱いに応じて別の場所で管理します。

### 現在の状態

本研究は進行中です。研究管理基盤と公開・非公開リポジトリの初期構成を整備し、現在はRQ1のうち、商品販売情報の抽出・関係構造化を評価するための、人間が原画像に照らして確認・確定する参照データの作成方法を具体化しています。その後、既に収集している文献を起点として先行研究を整理する予定です。

未確認の実装内容や実験結果は、本リポジトリ上で確定事項として扱いません。

本リポジトリは卒業研究のために作成したものであり、楽天の公式リポジトリまたは公式プロジェクトではありません。

---

## English

### Current research title (provisional)

Proposal and Evaluation of a Recipe Exploration Support System Based on Flyer-Listed Products and User Preferences and Constraints

The specific constraints covered by the title are still under review. Candidate conditions include disliked ingredients, preferred cooking time, and recipe categories. They will be finalized after confirming which information can be obtained from flyers, the Rakuten Recipe API, and user input.

### Project overview

This research investigates a system that supports recipe exploration from products listed in retail flyers. The system links structured flyer sales information with recipe ingredient information obtained through the Rakuten Recipe API, and presents recipe candidates and explanations that reflect explicit user preferences and constraints.

The goal is not to have the system determine a single correct recipe. Instead, it is to support users as they find recipes that can use flyer-listed products, check whether candidates satisfy their conditions, compare alternatives, and make a satisfactory choice. Candidate generation and ranking are used as means of supporting this exploration and selection process.

The current method is expected to include the following steps:

1. Directly extract embedded images from selected flyer PDFs and structure sales information while preserving relationships among products, sales frames, sections, prices, sales periods, conditions, and notes.
2. Normalize flyer product names and Rakuten Recipe API ingredient names to shared ingredient names.
3. Match flyer products with recipe ingredients.
4. Generate recipe candidates that can use the matched flyer-listed products.
5. Generate and rank explainable candidates based on explicit user preferences and constraints.
6. Compare the proposed system with a manual exploration interface using the same flyers and the same fixed recipe dataset.

### Evaluation perspectives

The current evaluation plan has three main perspectives:

- Feasibility of structuring flyer sales information, matching, and candidate generation: how accurately the system can reproduce fields and relationships from flyers, normalize and match product and ingredient names, and generate valid recipe candidates for flyer-listed products.
- Objective exploration efficiency: whether the proposed system reduces decision time and search or browsing operations compared with the manual exploration interface.
- Subjective exploration-support effects: whether it improves perceived workload, ease of exploration, perceived fit with user conditions, understanding of flyer-product relationships, and satisfaction with the final choice.

The first perspective is treated as one technical research question with three internal stages:

1. Extraction and relational structuring of flyer sales information
2. Normalization and matching of flyer product names and recipe ingredient names
3. Generation of valid recipe candidates

The research title, research questions, evaluation measures, and scope are provisional and may be updated after source verification, method refinement, preliminary technical evaluation, pilot testing, and consultation with the academic supervisor.

### Purpose of this repository

This public repository presents an overview of the graduation research project and materials confirmed to be suitable for publication. It also serves as the public application page registered for use of Rakuten Web Service.

Code and technical documentation will be added only after reviewing their content, absence of secrets, applicable terms, and publication rights. Internal work related to preprocessing, normalization, experiment preparation, and analysis is managed separately according to its publication scope. Only content confirmed to be suitable for public release is included here.

### Information not published

- API keys, access tokens, passwords, and other credentials
- Raw API responses and accumulated API data
- Flyer PDFs or images whose redistribution status has not been confirmed
- The complete normalization dictionary
- Identifying participant information and experimental data
- Internal working documents, analysis materials, and raw logs

These materials are not stored in this repository. They are managed separately according to their terms of use, publication scope, and personal-data requirements.

### Current status

This research is in progress. The initial research-management structure and the public and private repositories have been prepared. Current work focuses on designing human-verified reference data for evaluating the first stage of RQ1: extraction and relational structuring of flyer sales information. The next planned step is to organize prior work starting from the literature already collected.

Unverified implementation details and experimental results are not presented in this repository as established facts.

This repository was created for a graduation research project and is not an official Rakuten repository or project.
