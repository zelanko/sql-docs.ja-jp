---
title: SSMA for SAP ASE (SybaseToSQL) における新 |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d178cde4f921580c6c9953701d9e2101853400a2
ms.sourcegitcommit: e2a19dfac1b581237ef694071fbace4768bb6bf4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "40392588"
---
# <a name="whats-new-in-ssma-for-sap-ase-sybasetosql"></a>SSMA for SAP ASE (SybaseToSQL) の新機能新機能
この記事では、各リリースでの SAP ASE (旧称 SSMA for Sybase) の変更の SSMA が一覧表示します。 

## <a name="ssma-v79"></a>SSMA v7.9
SSMA の SAP ASE の v7.9 リリースには、次の変更が含まれています。
- 品質と変換のメトリックを向上させる対象となる修正します。
- データ型マッピングとプロジェクトの環境設定を変更するコマンドラインの SSMA でサポートします。
- 移行のサポートを SQL Server Integration Services (SSIS) を使用してデータ。 スキーマを変換した後を右クリック コンテキスト メニュー オプションを使用して、SSIS パッケージを作成することができます。
- SSMA で Azure SQL Database の接続ダイアログが、完全修飾サーバー名を指定することも変更されました。 SSMA の以前のバージョンで、Azure SQL Database のプレフィックスは、プロジェクト設定内で明示的に説明する必要があります。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v78"></a>SSMA v7.8
SSMA の SAP ASE の v7.8 リリースには、次の変更が含まれています。
- プロジェクトの設定で変更が強調表示されている型のマッピング。
- ユーザーがテレメトリを無効にする機能を提供します。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v77"></a>SSMA v7.7
SSMA の SAP ASE の v7.7 リリースには、次の変更が含まれています。
- 品質と変換のメトリックを向上させる修正プログラムを対象となる SAP ASE の SSMA が強化されました。
- SSMA for SAP ASE の 32 ビット バージョンは戻るには、要望に基づき、です。 (V7.4) より前の以前の実装と比較して、2 つのインストーラー パッケージがあるが、並行してインストールことはできません。 その結果がある場合、接続コンポーネントに基づいて最も適切なバージョンを選択する必要があります。 可能であれば、64 ビット バージョンを使用することをお勧めは常にします。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v76"></a>SSMA v7.6
SSMA の SAP ASE の v7.6 リリースには、次の変更が含まれています。
- SAP ASE の SSMA 品質と変換のメトリックを向上させる修正プログラムを対象となると SQL Server 2017 (パブリック プレビュー) のサポートが強化されました。 Windows および Linux 上の SQL Server 2017 のサポートはパブリック プレビュー段階と、運用環境の移行のない使用する必要があります。
- Sybase 関数の変換のサポートを提供する、SAP ASE の SSMA が更新されました。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストール前提条件、およびツールの 32 ビット バージョンは廃止されました。

## <a name="ssma-v75"></a>SSMA v7.5
SAP ASE の SSMA の v7.5 リリースには、次の変更が含まれています。
-   障碍を持つユーザーのアクセシビリティを確認します。 いくつかの機能強化で強化されています。
-   更新を作成または置換構文のサポートを提供します。

> [!IMPORTANT]
> .Net 4.5.2 は SSMA v7.5 をインストールするための前提条件です。 さらに、v7.4 以降では、SSMA の 32 ビット バージョンは中止されています。  

## <a name="ssma-v74"></a>SSMA v7.4
SSMA for Sybase の v7.4 リリースには、次の変更が含まれています。
- **クエリ タイムアウト**オプションは、ソースとターゲットのスキーマ オブジェクトの検出中に使用できるようになりました。
![query timeout オプション](../media/query-timeout_red.png)
- 品質と変換のメトリックは、お客様のフィードバックに基づいて、対象となる修正プログラムが強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は SSMA v7.4 をインストールするための前提条件です。 さらに、v7.4 以降では、SSMA の 32 ビット バージョンは中止されています。  

## <a name="ssma-v73"></a>SSMA v7.3
SSMA for Sybase の v7.3 リリースには、次の変更が含まれています。
- お客様からのフィードバックに基づいて対象となる修正プログラムで強化された品質と変換メトリック。
- SSMA 拡張性フレームワークは、次のものを使用して公開:
  - SQL Server Data Tools (SSDT) プロジェクトにエクスポートする機能。
    -   SSMA から SSDT プロジェクトにスキーマ スクリプトをエクスポートできます。 スキーマ スクリプトを使用して、追加のスキーマを変更して、データベースをデプロイすることができます。
![SSDT プロジェクト コマンドとして保存します。](../media/export-schema-scripts_red.png)
  - カスタム変換を実行するために、SSMA で使用できるライブラリ。
    - 構文のカスタム変換および変換 SSMA によって処理されなかった以前に対応するコードを作成します。
      - カスタムのコンバーターを作成する方法の手順については、このブログ投稿「[変換機能を拡張する SQL Server Migration Assistant の](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)します。
      - この変換用のサンプル プロジェクトをダウンロードできます[ブログの投稿](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/)します。

## <a name="ssma-v72"></a>SSMA v7.2
SSMA for Sybase の v7.2 リリースには、次の変更が含まれています。
- お客様からのフィードバックに基づいて対象となる修正プログラムで強化された品質と変換メトリック。
- 顧客の問題をトラブルシューティングし、SSMA のコンバージョン率を向上させるより良いデータ ポイントを提供するテレメトリの機能強化。

## <a name="ssma-v71"></a>SSMA v7.1
SSMA for Access の v7.1 リリースには、次の変更が含まれています。
- Windows と Linux CTP1 で SQL Server 2017 は、移行のサポートされているターゲット プラットフォームではようになりました。 この機能は、technical preview では、SQL の対象サーバーにスキーマとデータの移動をサポートしています。
- SSMA は、使用可能になるとすぐには、SSMA の最新バージョンをダウンロードする自動更新をサポートします。
- SSMA のインストール可能なバイナリは、Windows インストーラー パッケージ ファイル (.msi) が配信されるようになりました。

**リソース**

[SQL Server Migration Assistant の変換機能を拡張します。](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[評価し、Microsoft 以外のデータ プラットフォームから SQL Server にデータを移行 *(Oracle など) を含む*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>2016 年 5 月  
SSMA for Sybase の 2016 年 5 月リリースには、次の変更が含まれています。  

-  SQL Server 2016 のサポートが追加されました。
-  .Net 2.0 のインストーラーのチェックを削除します。
-  更新された拡張機能パックの依存関係から .Net 3.5 を .Net 4.0 にします。
-  プロジェクト"保存"固定と SSMA コンソールの「プロジェクトを開く」コマンド。
-  SSMA コンソールの"securepassword"コマンドを修正しました。
-  オブジェクトの初期読み込みのカウントを修正しました。
-  グローバル設定でバグを修正しました。

## <a name="march-2016"></a>2016 年 3 月  
Sybase の SSMA の 2016 年 3 月のプレビュー リリースには、次の変更が含まれています。  
  
-  SQL Server 2016 への移行のサポートが追加されました。  
  
## <a name="january-2016"></a>2016 年 1 月  
Sybase の SSMA の 2016 年 1 月のメンテナンス リリースには、次の変更が含まれています。  
  
-  追加の表示 メニュー項目をログ、SSMA (RFC 5706203) にします。  
-  追加された製品利用統計情報。 
  
## <a name="july-2014"></a>2014 年 7 月  
SSMA for Sybase の 2014 年 7 月リリースには、次の変更が含まれています。  
  
-  Azure SQL DB コード変換の改善。  
-  拡張機能パックの機能を Azure SQL DB をサポートするスキーマに移動します。  
-  追加のパフォーマンスの向上は、10 k を超えるデータベースのオブジェクトをテストします。  
-  多数のオブジェクトを処理するための追加の UI 機能強化。  
-  (したがって、これらは、変換で無視されます)、「既知」の LOB スキーマを強調表示する機能が追加されました。  
-  変換速度の向上を追加します。  
-  オブジェクト カウントを UI に表示する機能が追加されました。 
-  25% 以上削減レポート サイズ。  
-  未解析のコンス トラクターに対して改善されたエラー メッセージ。  
  
## <a name="april-2014"></a>2014 年 4 月  
SSMA for Sybase の 2014 年 4 月リリースには、次の変更が含まれています。  
  
-   MS SQL Server 2014 のサポートが追加されました。  
-   Azure への変換に関するバグを固定します。  
-   IE 10 で非表示レポート ページに関するバグを固定します。  
  
## <a name="january-2012"></a>2012 年 1 月  
SSMA for Sybase の 2012 年 1 月リリースには、次の変更が含まれています。  
  
-   ロールバックのトリガーの変換のサポートが追加されました。  
-   に変換するための修正プログラムの提供@ROWCOUNTおよび @@ERROR同じ SET ステートメントでします。  
  
## <a name="july-2011"></a>2011 年 7 月  
SSMA for Sybase の 2011 年 7 月リリースには、次の変更が含まれています。  
  
-   レポート データの移行中にエラーを改善しました。  
  
## <a name="april-2011"></a>2011 年 4 月  
SSMA for Sybase の 2011 年 4 月リリースには、次の変更が含まれています。  
  
-   "SSMA for Sybase"製品の統合は、サポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali"と Azure SQL。  
-   接続してへの移行のサポートが追加されました[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]"Denali"  
-   変換し、Sybase データベースを Azure SQL に移行するための新機能を追加します。  
-   データの並列移行のサポート、強化されたクライアント側のデータ移行エンジン。  
-   強化されたデータの移行とパフォーマンスを単純な一括復旧モデルが記録されます。  
-   適切に変換し、SQL Server の大文字小文字を区別する、大文字小文字を区別の Sybase データベースを移行できるようになりました。  
-   Sybase ASE 非 ANSI の join ステートメントを SQL Server の ANSI の join ステートメントの変換のサポートが追加されましたが削除、および UPDATE ステートメントに拡張されています。  
-   Sybase ASE ODBC プロバイダーとの Sybase ASE ADO.Net プロバイダーを使用して Sybase ASE サーバーに接続するための他の接続オプションが用意されています。  
-   依存関係と呼ばれる別のデータベースの削除**SysDB**、Sybase エミュレーション関数を (拡張機能パックの一部としてインストール) を格納します。  
-   SSMA を Sybase 拡張機能パックをインストールする機能が追加されました[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスター。  
-   SSMA (v4.0 および v4.2) の以前のバージョンで作成されたプロジェクトの下位互換性を追加します。  
-   SSMA (v4.0 および v4.2) の以前のバージョンでの SSMA for Sybase v5.0 製品サイド バイ サイド (SxS) をインストールする機能が追加されました。  
  
## <a name="july-2010"></a>2010 年 7 月  
SSMA for Sybase の 2010 年 7 月リリースには、次の変更が含まれています。  
  
-   SQL Server 2008 R2 への移行のサポートが追加されました。  
-   コマンドラインの実行用の新しい SSMA コンソール アプリケーションを追加します。  
-   サーバー側とクライアント側のデータ移行のエンジンの両方を使用してデータ移行のサポートが追加されました。  
-   データ移行で「カスタム選択」ステートメントのサポートが追加されました。  
-   Sybase ASE 15.0.3 と 15.5 からの移行のサポートが追加されました。  
  
## <a name="june-2008"></a>2008 年 6 月  
SSMA for Sybase の 2008 年 6 月リリースには、次の変更が含まれています。  
  
-   追加された SSMA テスト担当者、データベース オブジェクトの変換と SSMA によって行われたデータの移行を自動的にテストします。 SSMA のすべての移行手順が完了したら後、は、SSMA Tester を使用して、変換されたオブジェクトが同じように動作し、すべてのデータが適切に転送されることを確認します。  
-   以前 SQL 変換の追加。 一時テーブル (およびその他のオブジェクト) に、ユーザーがここで指定できます変換で使用するには、各ソース プロシージャの宣言。  
-   オブジェクトへの変換に追加された機能強化:  
    -   変換の変更を結合します。  
    -   集計と非集計せずしなくて/グループ by 句。  
    -   SELECT INTO ステートメントで IDENTITY 関数。  
    -   クラスター化制約とデータだけでロックのインデックス。  
    -   SELECT INTO で作成された一時テーブル。  
    -   制約/一時テーブルのインデックスを作成します。  
    -   新しい[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008 datetime 型がサポートされています。  
    -   Sybase 15.0 の接続とデータ型のサポート。  
  
## <a name="may-2007"></a>2007 年 5 月  
SSMA for Sybase の 2007 年 5 月リリースには、次の変更が含まれています。  
  
-   プロジェクトを保存するときに高速化データベースのコンテンツを読み込む機能が追加されました。  
-   SQL Server でのユーザーが入力したコメントのサポートを追加では、SQL モードが書式設定されます。  
-   オブジェクトへの変換で追加された機能を強化します。  
  
このリリースのヘルプ ファイルが更新されませんでした。 詳細については、この記事の後半で、ドキュメントのノートのセクションを参照してください。  
  
## <a name="november-2006"></a>2006 年 11 月  
SSMA for Sybase の 2006 年 11 月リリースには、次の変更が含まれています。  
  
-   新しいグローバル設定を追加するには。  
    -   エディターのウィンドウで行番号を表示できます。  
    -   重複するオブジェクトの置き換えを確認する SSMA を構成したり、スキーマの変換中に重複するオブジェクトを置き換えますかできます。  
-   SSMA で、次の状況を処理する方法を構成できる新しい変換オプションを追加するには。  
    -   バイナリ文字列を含む、CAST または CONVERT ステートメント。  
    -   等しいかどうかの式の null 値を確認します。  
    -   プロキシのテーブル。  
    -   RAISERROR のユーザー メッセージ エラー番号。  
    -   未解決の識別子を含むステートメントを更新します。  
-   SSMA が外部にある日付を処理する方法を指定することができます、新しい移行オプションが追加、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日付範囲。  
-   追加、**書式設定された SQL**の設定、 **SQL**が読みやすくするためのコードを書式設定 タブ。  
-   バグの修正プログラムを含む:  
    -   SSMA は、テーブルのロック今すぐに変換します*テーブル*IN {SHARED |。それに続くに TABLOCK、または TABLOCKX ヒントを追加して排他} のモード ステートメントでは、テーブルでのクエリを選択します。  
    -   バイナリ型は文字式で使用すると、必要なキャストが追加されました。  
    -   メモリとパフォーマンスが向上します。  
  
## <a name="july-2006"></a>2006 年 7 月  
SSMA for Sybase は、2006 年 7 月のリリースが初回のリリースでした。  
  
## <a name="see-also"></a>参照  
[Ssma for Sybase 作業の開始&#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
