---
title: SSMA for DB2 の新機能新機能 (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 09/22/2018
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1cc38f85-3caa-42d0-8c76-a380c1d15c67
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8b72d53f001654a085b8d2b5d01e203fd1b29ebe
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52400325"
---
# <a name="whats-new-in-ssma-for-db2-db2tosql"></a>SSMA for DB2 の新機能新機能 (DB2ToSQL)
この記事では、各リリースで変更を DB2 の SSMA が一覧表示します。  

## <a name="ssma-v710"></a>SSMA v7.10
DB2 用の SSMA v7.10 リリースには、次の変更が含まれています。
- 対象となる修正プログラムが追加のセキュリティとプライバシーの保護をグローバル要件の変更を満たすために提供するように設計します。
- BEGIN と END ブロックの型変換の修正。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v79"></a>SSMA v7.9
DB2 用の SSMA v7.9 リリースには、次の変更が含まれています。
- 品質と変換のメトリックを向上させる対象となる修正します。
- データ型マッピングとプロジェクトの環境設定を変更するコマンドラインの SSMA でサポートします。
- 移行のサポートを SQL Server Integration Services (SSIS) を使用してデータ。 スキーマを変換した後を右クリック コンテキスト メニュー オプションを使用して、SSIS パッケージを作成することができます。
- SSMA で Azure SQL Database の接続ダイアログが、完全修飾サーバー名を指定することも変更されました。 SSMA の以前のバージョンで、Azure SQL Database のプレフィックスは、プロジェクト設定内で明示的に説明する必要があります。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v78"></a>SSMA v7.8
DB2 用の SSMA v7.8 リリースには、次の変更が含まれています。
- プロジェクトの設定で変更が強調表示されている型のマッピング。
- ユーザーがテレメトリを無効にする機能を提供します。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v77"></a>SSMA v7.7
DB2 用の SSMA v7.7 リリースには、次の変更が含まれています。
- SSMA for DB2 は、品質と変換のメトリックを向上させる対象となる修正プログラムで拡張されています。
- SSMA for DB2 の 32 ビット バージョンは戻るには、要望に基づき、です。 (V7.4) より前の以前の実装と比較して、2 つのインストーラー パッケージがあるが、並行してインストールことはできません。 その結果がある場合、接続コンポーネントに基づいて最も適切なバージョンを選択する必要があります。 可能であれば、64 ビット バージョンを使用することをお勧めは常にします。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v76"></a>SSMA v7.6
DB2 用の SSMA v7.6 リリース品質と変換のメトリックを向上させる修正プログラムを対象となると SQL Server 2017 (パブリック プレビュー) のサポートが強化されました。 Windows および Linux 上の SQL Server 2017 のサポートはパブリック プレビューであり、運用環境の移行のために使用しないでください。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストール前提条件、およびツールの 32 ビット バージョンは廃止されました。

## <a name="ssma-v75"></a>SSMA v7.5
障碍を持つユーザーのアクセシビリティを確認します。 いくつかの機能強化の SSMA for DB2 の v7.5 リリースが強化されました。

> [!IMPORTANT]
> .Net 4.5.2 は SSMA v7.5 をインストールするための前提条件です。 さらに、v7.4 以降では、SSMA の 32 ビット バージョンは中止されています。

## <a name="ssma-v74"></a>SSMA v7.4
DB2 用の SSMA v7.4 リリースには、次の変更が含まれています。
- **クエリ タイムアウト**オプションは、ソースとターゲットのスキーマ オブジェクトの検出中に使用できるようになりました。
![query timeout オプション](../media/query-timeout_red.png)

- 品質と変換のメトリックは、お客様のフィードバックに基づいて、対象となる修正プログラムが強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は SSMA v7.4 をインストールするための前提条件です。 さらに、v7.4 以降では、SSMA の 32 ビット バージョンは中止されています。

## <a name="ssma-v73"></a>SSMA v7.3
DB2 用の SSMA v7.3 リリースには、次の変更が含まれています。
- お客様からのフィードバックに基づいて対象となる修正プログラムで強化された品質と変換メトリック。
- SSMA 拡張性フレームワークは、次のものを使用して公開:
  - SQL Server Data Tools (SSDT) プロジェクトにエクスポートする機能。
    -   SSMA から SSDT プロジェクトにスキーマ スクリプトをエクスポートできます。 スキーマ スクリプトを使用して、追加のスキーマを変更して、データベースをデプロイすることができます。
![SSDT プロジェクト コマンドとして保存します。](../media/export-schema-scripts_red.png)
  - カスタム変換を実行するために、SSMA で使用できるライブラリ。
    - 構文のカスタム変換および変換 SSMA によって処理されなかった以前に対応するコードを作成します。
      - カスタムのコンバーターを作成する方法の手順については、このブログ投稿「[変換機能を拡張する SQL Server Migration Assistant の](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)します。
      - これからの変換のサンプル プロジェクトをダウンロード[ブログの投稿](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/)します。

## <a name="ssma-v72"></a>SSMA v7.2
DB2 用の SSMA v7.2 リリースには、次の変更が含まれています。
- お客様からのフィードバックに基づいて対象となる修正プログラムで強化された品質と変換メトリック。
- 顧客の問題をトラブルシューティングし、SSMA のコンバージョン率を向上させるより良いデータ ポイントを提供するテレメトリの機能強化。

## <a name="ssma-v71"></a>SSMA v7.1
SSMA for Access の v7.1 リリースには、次の変更が含まれています。
- Windows と Linux CTP1 で SQL Server 2017 は、移行のサポートされているターゲット プラットフォームではようになりました。 この機能は、technical preview ではあり、対象の SQL サーバーにスキーマとデータの移動を許可します。
- SSMA は、使用可能になるとすぐには、SSMA の最新バージョンをダウンロードする自動更新をサポートします。
- SSMA のインストール可能なバイナリは、Windows インストーラー パッケージ ファイル (.msi) が配信されるようになりました。

**リソース**

[SQL Server Migration Assistant の変換機能を拡張します。](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[評価し、Microsoft 以外のデータ プラットフォームから SQL Server にデータを移行 *(Oracle など) を含む*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>2016 年 5 月  
DB2 用の SSMA の 2016 年 5 月リリースには、次の変更が含まれています。  

-  SQL Server 2016 のサポートが追加されました。
-  SQL Server のメモリ内と hekaton の機能への DB2 のメモリ内と通常のテーブルの追加の変換。
-  DB2 のアクセス制御の SQL Server ポリシー オブジェクト (DB2 に行レベルのセキュリティ) への追加の変換。
-  SQL Server のテンポラル テーブルへの DB2 システムでバージョン管理されたテーブルの追加の変換。
-  強化された DB2 パーサーと競合回避モジュール。
-  .Net 2.0 のインストーラーのチェックを削除します。
-  不要な *.dll Db2 インストーラーから削除されます。
-  プロジェクト"保存"固定と SSMA コンソールの「プロジェクトを開く」コマンド。
-  SSMA コンソールの"securepassword"コマンドを修正しました。
-  オブジェクトの初期読み込みのカウントを修正しました。
-  グローバル設定でバグを修正しました。
  
## <a name="march-2016"></a>2016 年 3 月  
DB2 用の SSMA の 2016 年 3 月プレビュー リリースには、次の変更が含まれています。  
  
-  SQL Server 2016 への移行のサポートが追加されました。  
  
## <a name="january-2016"></a>2016 年 1 月  
DB2 用の SSMA の 2016 年 1 月メンテナンス リリースには、次の変更が含まれています。  
  
-  さまざまな標準的な関数のサポートが追加されました。  
-  DB2 パーサー エラーを修正しました。  
-  固定 DB2 v9 zOS (RFC 5690920) をサポートします。  
-  固定の DB2 未解決の変換中にエラーの識別子。  
-  追加の表示 メニュー項目をログ、SSMA (RFC 5706203) にします。  
-  追加された製品利用統計情報。
  
## <a name="november-2014"></a>2014 年 11 月  
DB2 用の SSMA の 2014 年 11 月リリースは、最初のリリースでした。
