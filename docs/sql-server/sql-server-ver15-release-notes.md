---
title: SQL Server 2019 リリース ノート | Microsoft Docs
ms.date: 12/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 9e717104c2bc75bd056aa513566e12db6bd5c2b8
ms.sourcegitcommit: a13256f484eee2f52c812646cc989eb0ce6cf6aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/25/2019
ms.locfileid: "56802388"
---
# <a name="sql-server-2019-preview-release-notes"></a>SQL Server 2019 プレビュー リリース ノート
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Community Technology Preview (CTP) リリースに関する制限事項と既知の問題について説明します。 関連情報については、次を参照してください。
- [SQL Server 2019 の新機能](../sql-server/what-s-new-in-sql-server-ver15.md)

> [!NOTE]
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のプレビュー リリースは、次期リリースの機能を体験していただく目的で提供されるものです。 運用環境向けとしては、サポートもライセンスもされません。 次のシナリオは明示的に非サポートとなっています。
>
> - 古いバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] とのサイド バイ サイド インストール
> - SQL Server の既存のインスタンスを任意のバージョンからアップグレード

**[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] をお試しください**
- [![Evaluation Center からダウンロードする](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] をダウンロードして Windows にインストールする](https://go.microsoft.com/fwlink/?LinkID=862101)
- [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md)、[SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)、および [Ubuntu](../linux/quickstart-install-connect-ubuntu.md) の Linux にインストールする。
- [Docker で SQL Server 2019 を実行する](../linux/quickstart-install-connect-docker.md)。

## <a name="ctp-22-december-2018"></a>CTP 2.2 (2018 年 12 月)
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2 は、[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] の最新のパブリック リリースです。

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2 は評価版としてのみ使用可能です。 他のエディションは提供されません。 CTP 2.2 のサポートの説明は、ご利用のインストール メディアの `license_Eval.rtf` にあります。

限定的なサポートは、次のいずれかの場所で提供される場合があります。

- フォーラム
  - [SQL Server フィードバック](https://aka.ms/sqlfeedback)
  - [SQL Server の概要](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted)
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [SQL Server のドキュメント](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- または、[#sqlhelp](https://twitter.com/search?q=%23sqlhelp) を付けて [@SQLServer](https://twitter.com/SQLServer) にツイートしてください

### <a name="documentation-ctp-22"></a>ドキュメント (CTP 2.2)

- **問題およびユーザーへの影響**:SQL Server 2019 (15.x) のドキュメントは制限されており、コンテンツは [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] ドキュメント セットに付属しています。 記事の中で SQL Server 2019 (15.x) に固有のコンテンツは、**適用対象**で言及されています。

- **問題およびユーザーへの影響**: [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドキュメントはバージョンによってフィルター処理できます。 各ドキュメント ページの左上にあるコントロールを使用し、要件に応じてフィルター処理してください。 

- **問題およびユーザーへの影響**:SQL Server 2019 (15.x) には、オフライン コンテンツがありません。

### <a name="hardware-and-software-requirements"></a>ハードウェアとソフトウェアの要件

- **問題およびユーザーへの影響**:ハードウェア要件とソフトウェア要件は現在レビュー段階であり、製品リリース用の最終版ではありません。

  - **ハードウェア**
    - [Windows - プロセッサ、メモリ、およびオペレーティング システムの要件](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux - システム要件](../linux/sql-server-linux-setup.md#system)
  - **ソフトウェア**
    - Windows Server 2016 以降。 その他の要件については、[SQL Server のインストール要件](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)に関する記事をご覧ください
    - Microsoft .NET Framework 4.6.2。 [ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=53344)から入手できます。
    - Linux については、[サポートされている Linux プラットフォーム](../linux/sql-server-linux-setup.md#supportedplatforms)に関する記事をご覧ください

### <a name="updated-compiler"></a>更新されたコンパイラ

- **問題およびユーザーへの影響**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] は更新されたコンパイラで構築されています。 コンパイラの更新の結果、CTP 2.1 には浮動小数点数の結果と他の変換シナリオで、前のバージョンとは異なる値が返される場合があるという既知の問題がありました。 CTP 2.2 には、影響のあるシナリオで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の前のバージョンと同じ結果が返されるようにする作業が含まれています。 CTP 2.2 リリースでは、もう問題は解決されたと考えています。 [!INCLUDE[ss2017](../includes/sssqlv14-md.md)] と比較した結果に異常がある場合、[[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] チーム](http://aka.ms/sqlfeedback)にすぐに報告してください。

- **回避策**:なし

- **適用対象**:SQL Server 2019 CTP 2.2、CTP 2.1

### <a name="sql-server-integration-services-ssis-page-deployment-after-switching-db-to-single-user-mode-and-then-switching-back"></a>DB をシングル ユーザー モードに切り替えてから再び元のモードに切り替えた後での SQL Server Integration Services (SSIS) ページの配置

- **問題およびユーザーへの影響**:SSISDB をシングル ユーザー モードから再びマルチ ユーザー モードに切り替えた後、パッケージを配置すると、次のエラーが報告される場合があります。

  `Cannot continue the execution because the session is in the kill state.`

- **回避策**:SQL Server のインスタンスを停止し、再起動してから、SSISDB をマルチ ユーザー モードに切り替えます。

- **適用対象**:SQL Server 2019 プレビュー CTP 2.2、CTP 2.1

### <a name="utf-8-collations"></a>UTF-8 対応の照合順序

- **問題およびユーザーへの影響**:UTF-8 対応の照合順序は、他の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 機能とは併用できない場合があります。 UTF-8 は、次の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 機能が使用されている場合にはサポートされません。

  - Linked Server
  - インメモリ OLTP
  - PolyBase 用の外部テーブル

  > [!Note]
  > Azure Data Studio および SQL Server Data Tools (SSDT) では、UTF-8 対応の照合順序を選択するための UI は現在のところサポートされていません。 最新バージョンの [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) では、UTF-8 対応の照合順序を UI で選択することができます。
 
- **回避策**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP には回避策はありません。

- **適用対象**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2、CTP 2.1、CTP 2.0。

### <a name="sql-graph"></a>SQL Graph

- **問題およびユーザーへの影響**:DacFx に依存しているツール (インポート/エクスポートなど) は、新しいグラフ機能 (エッジ制約や DML マージ) には対応していません。 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でのスクリプト記述は機能しない可能性があります。

- **回避策**:[!INCLUDE[tsql](../includes/tsql-md.md)] スクリプトを記述し、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] または SQLCMD を使用して、それらをサーバーに対して実行する場合は機能します。 エッジ制約を作成したり、新しいマージ DML 構文を使用したり、あるいはグラフ オブジェクトに基づく派生テーブル/ビューを作成したりするデータベース オブジェクトについては、エクスポートやインポートは機能しません。 このようなオブジェクトは、[!INCLUDE[tsql](../includes/tsql-md.md)] スクリプトを使用して、データベース内に手動で作成する必要があります。 

- **適用対象**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2、CTP 2.1、2.0。

### <a name="always-encrypted-with-secure-enclaves"></a>セキュア エンクレーブを使用する Always Encrypted

- **問題およびユーザーへの影響**:高度な計算では、いくつかのパフォーマンスの最適化が保留になっており、機能が制限 (インデックス作成がないなど) されていて、現在は既定で無効になっています。

- **回避策**:高度な計算を有効にするには、`DBCC traceon(127,-1)` を実行します。 詳細については、[高度な計算の有効化](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave)に関する記事をご覧ください。

- **適用対象**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2、CTP 2.1、2.0。

## <a name="ctp-21-october-2018"></a>CTP 2.1 (2018 年 10 月)

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 は、[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] の以前のパブリック リリースです。

### <a name="udf-inlining"></a>UDF のインライン化

- **問題およびユーザーへの影響**:インライン化されたユーザー定義関数の呼び出しを入れ子にすると、セキュリティが正しく検証されないというやっかいで特殊なケース シナリオがあります。
  
- **回避策**:そのような UDF については、`INLINE = OFF` 設定を使用して UDF のインライン化を無効にします。

- **適用対象**:SQL Server 2019 CTP 2.1

### <a name="sql-server-integration-service---fuzzy-lookup-transformation"></a>SQL Server Integration Service - あいまい参照変換

- **問題およびユーザーへの影響**:インデックスを再利用するようにあいまい参照変換が設定されている場合、そのあいまい参照変換は失敗し、次のエラーが返されます。

  `The specified delimiters do not match the delimiters used to build the pre-existing match index "...". This error occurs when the delimiters used to tokenize fields do not match. This can have unknown effects on the matching behavior or results.`

- **回避策**:なし

- **その他の情報**:なし  

- **適用対象**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP2.1

### <a name="lightweight-query-profiling-infrastructure"></a>軽量クエリ プロファイリング インフラストラクチャ

- **問題およびユーザーへの影響**:コマンド `ALTER DATABASE SCOPED CONFIGURATION SET LIGHTWEIGHT_QUERY_PROFILING = ON` を実行すると構文エラーが返されます。 このコマンドの実行に依存するシナリオはすべて失敗します。

  > [!NOTE]
  > 現時点では、軽量クエリ プロファイリング インフラストラクチャ (LWP) を個別のデータベース レベルで制御することはできません。すべてのデータベースについて既定で有効になります。 LWP の詳細については、「[SQL Server 2019 の新機能](../sql-server/what-s-new-in-sql-server-ver15.md)」を参照してください。

- **回避策**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP には回避策はありません。

- **適用対象**:[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 および CTP 2.0。

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
