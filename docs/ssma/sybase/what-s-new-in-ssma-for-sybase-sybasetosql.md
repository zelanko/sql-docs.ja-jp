---
title: SSMA for SAP ASE (SybaseToSQL) の新機能 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
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
ms.openlocfilehash: 2411ca6b7d6b76b780ab1269376fb4f36d16f7e0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="whats-new-in-ssma-for-sap-ase-sybasetosql"></a>SSMA for SAP ASE (SybaseToSQL) の新機能
このトピックでは、SAP ASE (旧称 SSMA for Sybase) での変更の各リリース SSMA が一覧表示します。 

## <a name="ssma-v77"></a>SSMA v7.7
SSMA の SAP ASE v7.7 のリリースには、次の変更が含まれています。
- SAP ASE の SSMA は、品質、および変換のメトリックを向上する対象となる修正プログラムで強化されています。
- 一般的な要求に基づき、SAP ASE の SSMA の 32 ビット バージョンは戻されました。 (V7.4) より前の以前の実装と比較して、2 つのインストーラー パッケージがありますが、サイド バイ サイドでインストールできません。 その結果がある場合、接続コンポーネントに基づいて最も適切なバージョンを選択する必要があります。 可能であれば、64 ビット バージョンを使用することはお勧め常にします。

> [!IMPORTANT]
> SSMA v7.4 とそれ以降のバージョンでは、.Net 4.5.2 は、インストールの前提がします。

## <a name="ssma-v76"></a>SSMA v7.6
SSMA の SAP ASE v7.6 のリリースには、次の変更が含まれています。
- および SQL Server 2017 (パブリック プレビュー) のサポートの品質、および変換のメトリックを向上する対象となる修正プログラムと、SAP ASE の SSMA が強化されました。 Windows および Linux での SQL Server 2017 のサポートは、パブリック プレビューではの運用環境の移行は使用できません。
- Sybase 関数の変換のサポートを提供する SAP ASE の SSMA が更新されました。

> [!IMPORTANT]
> SSMA v7.4 とそれ以降のバージョンでは、.Net 4.5.2 は、のインストール前提条件、およびツールの 32 ビット バージョンは廃止されました。

## <a name="ssma-v75"></a>SSMA v7.5
SSMA の SAP ASE v7.5 のリリースには、次の変更が含まれています。
-   障碍の大きいアクセシビリティを確認するいくつかの機能強化で強化されています。
-   更新を作成または置換構文のサポートを提供します。

> [!IMPORTANT]
> .Net 4.5.2 は、SSMA v7.5 をインストールするための事前必須コンポーネントです。 さらに、v7.4 から始まり、SSMA の 32 ビット バージョンは廃止されています。  

## <a name="ssma-v74"></a>SSMA v7.4
Sybase 用 SSMA の v7.4 リリースには、次の変更が含まれています。
- **クエリのタイムアウト**オプションは、ソースとターゲットのスキーマ オブジェクトの検出中に使用できるようになりました。
![query timeout オプション](../media/query-timeout_red.png)
- 品質と変換のメトリックは、お客様のフィードバックに基づいて、対象となる修正プログラムが強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は、SSMA v7.4 をインストールするための事前必須コンポーネントです。 さらに、v7.4 から始まり、SSMA の 32 ビット バージョンは廃止されています。  

## <a name="ssma-v73"></a>SSMA v7.3
Sybase 用 SSMA の v7.3 リリースには、次の変更が含まれています。
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
SSMA の Sybase v7.2 のリリースには、次の変更が含まれています。
- 改善の品質、および変換のメトリックを対象となる修正プログラムがお客様のフィードバックに基づきます。
- 製品利用統計情報をお客様の問題をトラブルシューティングし、SSMA の換算率を向上させる優れたデータ ポイントを提供する拡張機能です。

## <a name="ssma-v71"></a>SSMA v7.1
SSMA for Access の v7.1 リリースには、次の変更が含まれています。
- Windows と Linux CTP1 では、SQL Server 2017 は、移行のサポート対象のターゲット プラットフォームではようになりました。 この機能は、technical preview では、SQL の対象サーバーにスキーマとデータの移動をサポートしています。
- SSMA は、使用可能になるとすぐには、SSMA の最新バージョンをダウンロードする自動更新をサポートします。
- SSMA インストール可能なバイナリは、Windows インストーラー パッケージ ファイル (.msi) により配信されるようになりました。

**リソース**

[SQL Server Migration Assistant の変換機能を拡張します。](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[評価し、Microsoft 以外のデータ プラットフォームから SQL Server にデータを移行 *(Oracle など) の*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>2016 年 5 月  
Sybase SSMA の 2016 年 5 月のリリースには、次の変更が含まれています。  

-  SQL Server 2016 のサポートを追加します。
-  .Net 2.0 のインストーラーのチェックを削除します。
-  更新された拡張機能パックの依存関係から .Net 3.5 を .Net 4.0 です。
-  [保存] プロジェクト"固定と SSMA コンソールの「プロジェクトを開く」コマンド。
-  SSMA コンソールの"securepassword"コマンドを固定します。
-  初期読み込みのためのオブジェクトのカウントを修正しました。
-  グローバル設定のバグを修正します。

## <a name="march-2016"></a>2016 年 3 月  
Sybase 用 SSMA の 2016 年 3 月のプレビュー リリースには、次の変更が含まれています。  
  
-  SQL Server 2016 への移行のサポートが追加されました。  
  
## <a name="january-2016"></a>2016 年 1 月  
Sybase SSMA の 2016 年 1 月メンテナンスのリリースには、次の変更が含まれています。  
  
-  SSMA (RFC 5706203) するには、ログ メニュー項目を追加したビューです。  
-  追加された製品利用統計情報。 
  
## <a name="july-2014"></a>2014 年 7 月  
Sybase SSMA の 2014 年 7 月のリリースには、次の変更が含まれています。  
  
-  Azure SQL DB コードの変換が向上します。  
-  Azure SQL DB をサポートするためにスキーマに拡張機能パックの機能を移動します。  
-  追加されたパフォーマンスの向上は、10 k 個以上のデータベースのオブジェクトをテストします。  
-  多数のオブジェクトを処理するための追加の UI 機能強化。  
-  (したがって、変換で無視する) に「既知」の LOB スキーマを強調表示する機能が追加されました。  
-  変換速度の向上を追加します。  
-  UI 内のオブジェクト数を表示する機能が追加されました。 
-  25% 以上のレポート サイズ。  
-  未解析のコンス トラクターに対して改善されたエラー メッセージ。  
  
## <a name="april-2014"></a>2014 年 4 月  
Sybase 用 SSMA の 2014 年 4 月リリースには、次の変更が含まれています。  
  
-   MS SQL Server 2014 のサポートが追加されました。  
-   Azure への変換に関する修正されたバグはします。  
-   IE 10 で非表示レポート ページに関する修正されたバグはします。  
  
## <a name="january-2012"></a>2012 年 1 月  
Sybase SSMA の 2012 年 1 月のリリースには、次の変更が含まれています。  
  
-   ロールバック トリガー変換のサポートを追加します。  
-   に変換するための修正プログラムの提供@ROWCOUNTおよび @@ERROR同じ SET ステートメントでします。  
  
## <a name="july-2011"></a>2011 年 7 月  
Sybase SSMA の 2011 年 7 月のリリースには、次の変更が含まれています。  
  
-   エラー報告データの移行中の強化。  
  
## <a name="april-2011"></a>2011 年 4 月  
Sybase 用 SSMA の 2011 年 4 月リリースには、次の変更が含まれています。  
  
-   "SSMA Sybase"製品の統合をサポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali"と Azure SQL です。  
-   接続してへの移行のサポートが追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]"Denali"  
-   変換し、Azure SQL への Sybase データベースを移行する新機能を追加します。  
-   強化されたクライアント側のデータ移行エンジン、データの並列移行をサポートします。  
-   強化されたデータの移行とパフォーマンスを単純な一括ログ復旧モデルに記録します。  
-   正しく変換し、SQL Server の大文字小文字を区別する大文字小文字を区別の Sybase データベースを移行する機能が追加されました。  
-   削除し、UPDATE ステートメントの join ステートメントを SQL Server の ANSI Sybase ASE 非 ANSI 結合ステートメントの変換サポートの追加が拡張されました。  
-   Sybase ASE ODBC プロバイダー、および Sybase ASE ADO.Net プロバイダー Sybase ASE サーバーに接続するための他の接続オプションが用意されています。  
-   呼ばれる独立したデータベースへの依存関係を削除**SysDB**、Sybase エミュレーション関数 (拡張機能パックの一部としてインストールされている) が含まれています。  
-   SSMA Sybase 拡張機能パックにインストールする機能が追加されました[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]クラスター。  
-   SSMA (v4.0 および v4.2) の以前のバージョンで作成されたプロジェクトの下位互換性を追加します。  
-   SSMA (v4.0 および v4.2) の旧バージョンと SSMA for Sybase v5.0 製品サイド バイ サイド (SxS) をインストールする機能が追加されました。  
  
## <a name="july-2010"></a>2010 年 7 月  
Sybase SSMA の 2010 年 7 月のリリースには、次の変更が含まれています。  
  
-   SQL Server 2008 R2 への移行のサポートが追加されました。  
-   コマンドラインの実行用の新しい SSMA コンソール アプリケーションを追加します。  
-   サーバー側とクライアント側のデータ移行のエンジンの両方を使用してデータ移行のサポートを追加します。  
-   データの移行で"Custom SELECT"ステートメントのサポートを追加します。  
-   Sybase ASE 15.0.3 と 15.5 からの移行のサポートが追加されました。  
  
## <a name="june-2008"></a>2008 年 6 月  
Sybase 用 SSMA の 2008 年 6 月リリースには、次の変更が含まれています。  
  
-   追加された SSMA テスト担当者、自動的にデータベース オブジェクトへの変換と SSMA によって行われたデータの移行をテストします。 SSMA のすべての移行手順が完了したら後、は、SSMA Tester を使用して、変換したオブジェクトが同じように動作し、すべてのデータが正常に転送されることを確認してください。  
-   追加前 SQL 変換します。 一時テーブル (およびその他のオブジェクト) に、ユーザーがここで指定できます変換で使用するには、各ソース プロシージャを宣言します。  
-   オブジェクトへの変換に追加された機能強化:  
    -   変換の変更を結合します。  
    -   集計と非集計せずを持つ/グループ by 句。  
    -   SELECT INTO ステートメントを使用して IDENTITY 関数。  
    -   クラスター化制約、およびデータだけでロックのインデックス。  
    -   SELECT INTO で作成された一時テーブルです。  
    -   制約/一時テーブルのインデックスを作成します。  
    -   新しい[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2008 datetime 型がサポートされています。  
    -   Sybase 15.0 接続とデータ型のサポート。  
  
## <a name="may-2007"></a>2007 年 5 月  
Sybase SSMA の 2007 年 5 月のリリースには、次の変更が含まれています。  
  
-   データベースの内容を読み込みも高速、プロジェクトを保存するときに機能が追加されました。  
-   SQL Server のユーザーが入力したコメントのサポートを追加では、SQL モードが書式設定されます。  
-   オブジェクトへの変換に追加された機能強化。  
  
ヘルプ ファイルは、このリリースでは更新されませんでした。 詳細については、このトピックの後半のドキュメントのノートのセクションを参照してください。  
  
## <a name="november-2006"></a>2006 年 11 月  
Sybase SSMA の 2006 年 11 月のリリースには、次の変更が含まれています。  
  
-   新しいグローバル設定を追加します。  
    -   エディター ウィンドウ内の行番号の表示にすることもできます。  
    -   SSMA 重複するオブジェクトを交換を要求するメッセージを構成したりできますかは、スキーマの変換中に重複するオブジェクトを置き換えます。  
-   SSMA で、次の状況を処理する方法を構成できる新しい変換オプションを追加します。  
    -   バイナリ文字列を含む、CAST または CONVERT ステートメント。  
    -   等値式の null 値を確認します。  
    -   プロキシ テーブル。  
    -   RAISERROR のユーザー メッセージ エラー番号。  
    -   未解決の識別子を含むステートメントを更新します。  
-   SSMA が外側にある日付を処理する方法を指定できる新しい移行オプションを追加、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]日付範囲にします。  
-   追加、**フォーマット SQL**の設定、 **SQL**が読みやすくするためのコードを書式設定 タブ。  
-   以下のもののバグ修正:  
    -   SSMA は、ロック テーブル今すぐに変換します*テーブル*IN {SHARED |。後続するか、TABLOCK、TABLOCKX ヒントを追加することによって排他的} のモード ステートメントは、テーブルでのクエリを選択します。  
    -   Binary データ型は文字式で使用すると、必要なキャストは追加されました。  
    -   メモリとパフォーマンスが向上します。  
  
## <a name="july-2006"></a>2006 年 7 月  
SSMA for Sybase は、2006 年 7 月のリリースが初回のリリースでした。  
  
## <a name="see-also"></a>参照  
[入門 SSMA for Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
