---
title: "SSMA for MySQL (MySQLToSql) の新機能 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 09/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 1451a0b0-6713-4d0c-954f-ea3d8fce1d31
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a435479b9cad332215b1f44f7d881f5055b2fefd
ms.openlocfilehash: f895aee684d353451c263b136547c2c6ed7d976d
ms.contentlocale: ja-jp
ms.lasthandoff: 11/08/2017

---
# <a name="whats-new-in-ssma-for-mysql-mysqltosql"></a>SSMA for MySQL (MySQLToSql) の新機能
このトピックでは、MySQL での変更の各リリース SSMA が一覧表示します。 

## <a name="ssma-v76"></a>SSMA v7.6
品質と変換のメトリックを向上する対象となる修正プログラムと SQL Server 2017 (パブリック プレビュー) のサポートの SSMA for MySQL の v7.6 リリースが拡張されました。 Windows および Linux での SQL Server 2017 のサポートは、パブリック プレビューではの運用環境の移行は使用できません。

> [!IMPORTANT]
> SSMA v7.4 とそれ以降のバージョンでは、.Net 4.5.2 は、のインストール前提条件、およびツールの 32 ビット バージョンは廃止されました。

## <a name="ssma-v75"></a>SSMA v7.5
SSMA の MySQL の v7.5 リリースは、障碍の大きいアクセシビリティを確認するいくつかの機能強化で強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は、SSMA v7.5 をインストールするための事前必須コンポーネントです。 さらに、v7.4 から始まり、SSMA の 32 ビット バージョンは廃止されています。

## <a name="ssma-v74"></a>SSMA v7.4
SSMA の MySQL v7.4 のリリースには、次の変更が含まれています。
- **クエリのタイムアウト**オプションは、ソースとターゲットのスキーマ オブジェクトの検出中に使用できるようになりました。
![query timeout オプション](../media/query-timeout_red.png)
- 品質と変換のメトリックは、お客様のフィードバックに基づいて、対象となる修正プログラムが強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は、SSMA v7.4 をインストールするための事前必須コンポーネントです。 さらに、v7.4 から始まり、SSMA の 32 ビット バージョンは廃止されています。 

## <a name="ssma-v73"></a>SSMA v7.3
SSMA の MySQL v7.3 のリリースには、次の変更が含まれています。
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
SSMA の MySQL v7.2 のリリースには、次の変更が含まれています。
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
MySQL SSMA の 2016 年 5 月のリリースには、次の変更が含まれています: です。

-  SQL Server 2016 のサポートを追加します。
-  強化されたパーサーとの競合回避モジュール。
-  .Net 2.0 のインストーラーのチェックを削除します。
-  更新された拡張機能パックの依存関係から .Net 3.5 を .Net 4.0 です。
-  MySql の既定の固定 BigInt typemapping です。
-  [保存] プロジェクト"固定と SSMA コンソールの「プロジェクトを開く」コマンド。
-  SSMA コンソールの"securepassword"コマンドを固定します。
-  初期読み込みのためのオブジェクトのカウントを修正しました。
-  固定 MsSql オブジェクトをロードします。
-  グローバル設定のバグを修正します。
 
## <a name="march-2016"></a>2016 年 3 月  
MySQL の SSMA の 2016 年 3 月のプレビュー リリースには、次の変更が含まれています。  
  
-  SQL Server 2016 への移行のサポートが追加されました。 
  
## <a name="january-2016"></a>2016 年 1 月  
MySQL SSMA の 2016 年 1 月メンテナンスのリリースには、次の変更が含まれています。  
  
-  SSMA (RFC 5706203) するには、ログ メニュー項目を追加したビューです。  
-  追加された製品利用統計情報。  
  
## <a name="july-2014"></a>2014 年 7 月  
SSMA の MySQL の 2014 年 7 月リリースには、次の変更が含まれています。  
  
-  Azure SQL DB コードの変換が向上します。 
-  拡張機能パックの機能は、Azure SQL DB をサポートするために、スキーマに移動します。  
-  パフォーマンスの向上は、10 k 個以上のデータベースのオブジェクトをテストします。  
-  多数のオブジェクトを処理するための UI の機能強化。  
-  (したがって、変換で無視する) の「既知」の LOB スキーマの強調表示します。  
-  速度の向上を変換します。  
-  UI 内のオブジェクトの数を表示します。  
-  25% 以上のレポート サイズの縮小します。  
-  未解析のコンス トラクターに対して改善されたエラー メッセージ。  
  
## <a name="april-2014"></a>2014 年 4 月  
SSMA の MySQL の 2011 年 7 月リリースには、次の変更が含まれています。  
  
-  MS SQL Server 2014 のサポートが追加されました。  
-  Azure への変換に関する修正されたバグ  
-  IE 10 で非表示レポート ページに関する修正されたバグはします。  
  
## <a name="july-2011"></a>2011 年 7 月  
SSMA の MySQL の 2011 年 7 月リリースには、次の変更が含まれています。  
  
-   制限の変換のサポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]"Denali"のオフセットします。  
-   エラー報告データの移行中の強化。  
  
## <a name="april-2011"></a>2011 年 4 月  
SSMA の MySQL の 2011 年 4 月リリースには、次の変更が含まれています。  
  
-   1 つの"SSMA の MySQL"、サポートのインストール可能[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali"と Azure SQL です。  
-   接続できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]"Denali"  
-   強化されたクライアント側のデータ移行エンジン、データの並列移行をサポートします。  
-   強化されたデータの移行とパフォーマンスを単純な一括ログ復旧モデルに記録します。  
-   MySQL コンソールのバージョンの SSMA では、旧バージョンとの互換性をサポートします。 SSMA v5.0 以前のバージョンで作成されたプロジェクトを開くことができます。  
-   SSMA for MySQL v5.0 製品であることには、SSMA 製品の以前のバージョンとサイド バイ サイド (SxS) がインストールされています。  
  
## <a name="july-2010"></a>2010 年 7 月  
SSMA の MySQL の 2010 年 7 月リリースには、次の機能が含まれています。  
  
1.  **ユーザー インターフェイスの機能強化:**  
  
    -   'SQL モード' MySQL データベースのオブジェクト タブ  
    -   MySQL データベース オブジェクトの [設定] タブ  
    -   MySQL テーブルの 'データ' タブ  
    -   変換と移行」ページで、更新されたプロジェクトの設定  
    -   テーブル レベルで [データ移行の設定]  
  
2.  **MySQL および SQL Server への接続の機能強化:**  
  
    -   MySQL の SSL 接続  
    -   SQL Server で暗号化された接続  
  
3.  **MySQL Metabase Explorer の機能強化:**  
  
    -   すべての MySQL データベース オブジェクトと、それぞれのタブを読み込んでいます。  
  
4.  **オブジェクトへの変換の機能強化:**  
  
    -   MySQL メタベース オブジェクト – プロシージャ、関数、ビュー、トリガー、およびステートメントの変換。  
    -   テーブルの空間データ型の制限付きサポートします。  
    -   MySQL 関数を SQL Server ストアド プロシージャに変換するオプション  
    -   オブジェクトへの変換中に SQL モードと文字セットのマッピングを適用するオプション  
  
5.  **データ移行の機能強化:**  
  
    -   サーバー側とクライアント側のデータ移行のエンジンの両方を使用してデータ移行のサポート  
    -   空間データの移行のサポート  
    -   カスタムの SQL テーブルのデータの移行  
  
6.  **SSMA MySQL コンソール for:**  
  
    -   SSMA for MySQL のコンソール機能のサポート  
    -   スクリプト レベルのインターフェイスのサポート  
  
## <a name="january-2010"></a>2010 年 1 月  
MySQL SSMA の 2010 年 1 月のリリースでは、最初のリリースをでした。 次の機能が含まれています。  
  
-   両方への移行のサポートが追加のオンプレミス SQL Server および Azure SQL します。  
  
-   **機能のスナップショット:**スキーマとデータの移行の MySQL テーブル/インデックス/の制約。

