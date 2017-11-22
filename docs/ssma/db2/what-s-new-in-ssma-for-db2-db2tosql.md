---
title: "SSMA for DB2 の新機能 (DB2ToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 09/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 1cc38f85-3caa-42d0-8c76-a380c1d15c67
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ff312fceaee24d32f23ff8135bcc18e09601ddf
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="whats-new-in-ssma-for-db2-db2tosql"></a>SSMA for DB2 の新機能 (DB2ToSQL)
このトピックでは、DB2 での変更の各リリース SSMA が一覧表示します。  

## <a name="ssma-v76"></a>SSMA v7.6
SSMA の DB2 の v7.6 リリースの品質、および変換のメトリックを向上する対象となる修正プログラムと SQL Server 2017 (パブリック プレビュー) のサポートが拡張されました。 Windows および Linux での SQL Server 2017 のサポートは、パブリック プレビューではの運用環境の移行は使用できません。

> [!IMPORTANT]
> SSMA v7.4 とそれ以降のバージョンでは、.Net 4.5.2 は、のインストール前提条件、およびツールの 32 ビット バージョンは廃止されました。

## <a name="ssma-v75"></a>SSMA v7.5
SSMA の DB2 の v7.5 リリースは、障碍の大きいアクセシビリティを確認するいくつかの機能強化で強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は、SSMA v7.5 をインストールするための事前必須コンポーネントです。 さらに、v7.4 から始まり、SSMA の 32 ビット バージョンは廃止されています。

## <a name="ssma-v74"></a>SSMA v7.4
SSMA の DB2 の v7.4 リリースには、次の変更が含まれています。
- **クエリのタイムアウト**オプションは、ソースとターゲットのスキーマ オブジェクトの検出中に使用できるようになりました。
![query timeout オプション](../media/query-timeout_red.png)

- 品質と変換のメトリックは、お客様のフィードバックに基づいて、対象となる修正プログラムが強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は、SSMA v7.4 をインストールするための事前必須コンポーネントです。 さらに、v7.4 から始まり、SSMA の 32 ビット バージョンは廃止されています。

## <a name="ssma-v73"></a>SSMA v7.3
SSMA の DB2 の v7.3 リリースには、次の変更が含まれています。
- 改善の品質、および変換のメトリックを対象となる修正プログラムがお客様のフィードバックに基づきます。
- SSMA 拡張性フレームワークが、次の項目を使用して公開します。
  - SQL Server Data Tools (SSDT) プロジェクトに機能をエクスポートします。
    -   SSMA から SSDT プロジェクトにスキーマ スクリプトをエクスポートできます。 スキーマ スクリプトを使用して、追加のスキーマ変更を加えるし、データベースを展開することができます。
![SSDT プロジェクト コマンドとして保存します。](../media/export-schema-scripts_red.png)
  - カスタム変換を実行するの SSMA で利用できるライブラリ。
    - これでカスタム構文変換および SSMA によって処理されなかったいた変換を処理できるコードを構築できます。
      - カスタムのコンバーターを作成する方法の手順については、このブログの投稿[変換機能を拡張する SQL Server Migration Assistant の](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)します。
      - この変換用のサンプル プロジェクトをダウンロードできる[ブログの投稿](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/)です。

## <a name="ssma-v72"></a>SSMA v7.2
SSMA の DB2 の v7.2 リリースには、次の変更が含まれています。
- 改善の品質、および変換のメトリックを対象となる修正プログラムがお客様のフィードバックに基づきます。
- 製品利用統計情報をお客様の問題をトラブルシューティングし、SSMA の換算率を向上させる優れたデータ ポイントを提供する拡張機能です。

## <a name="ssma-v71"></a>SSMA v7.1
SSMA for Access の v7.1 リリースには、次の変更が含まれています。
- Windows と Linux CTP1 では、SQL Server 2017 は、移行のサポート対象のターゲット プラットフォームではようになりました。 この機能は、technical preview ではあり、SQL の対象サーバーにスキーマとデータの移動を許可します。
- SSMA は、使用可能になるとすぐには、SSMA の最新バージョンをダウンロードする自動更新をサポートします。
- SSMA インストール可能なバイナリは、Windows インストーラー パッケージ ファイル (.msi) により配信されるようになりました。

**リソース**

[SQL Server Migration Assistant の変換機能を拡張します。](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[評価し、Microsoft 以外のデータ プラットフォームから SQL Server にデータを移行*(Oracle など) の*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>2016 年 5 月  
SSMA の DB2 の 2016 年 5 月リリースには、次の変更が含まれています。  

-  SQL Server 2016 のサポートを追加します。
-  SQL Server のメモリ内と hekaton の機能への DB2 のメモリ内と通常のテーブルの追加の変換です。
-  SQL Server ポリシー オブジェクト (行レベルのセキュリティを DB2) へのアクセス制御の DB2 の追加変換です。
-  SQL Server のテンポラル テーブルへの DB2 システムでバージョン管理されたテーブルの追加の変換です。
-  強化された DB2 パーサーおよび競合回避モジュール。
-  .Net 2.0 のインストーラーのチェックを削除します。
-  Db2 インストーラーから不要な *.dll を削除します。
-  [保存] プロジェクト"固定と SSMA コンソールの「プロジェクトを開く」コマンド。
-  SSMA コンソールの"securepassword"コマンドを固定します。
-  初期読み込みのためのオブジェクトのカウントを修正しました。
-  グローバル設定のバグを修正します。
  
## <a name="march-2016"></a>2016 年 3 月  
DB2 SSMA の 2016 年 3 月プレビューのリリースには、次の変更が含まれています。  
  
-  SQL Server 2016 への移行のサポートが追加されました。  
  
## <a name="january-2016"></a>2016 年 1 月  
DB2 SSMA の 2016 年 1 月メンテナンスのリリースには、次の変更が含まれています。  
  
-  標準的な関数の数のサポートを追加します。  
-  DB2 パーサー エラーを修正しました。  
-  固定 DB2 v9 zOS (RFC 5690920) をサポートします。  
-  固定 DB2 未解決の変換中にエラーの識別子。  
-  SSMA (RFC 5706203) するには、ログ メニュー項目を追加したビューです。  
-  追加された製品利用統計情報。
  
## <a name="november-2014"></a>2014 年 11 月  
SSMA の DB2 の 2014 年 11 月リリースでは、最初のリリースをでした。
