---
title: ALTER DATABASE 互換性レベル (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COMPATIBILITY_LEVEL_TSQL
- COMPATIBILITY_LEVEL
dev_langs:
- TSQL
helpviewer_keywords:
- 80 compatibility level
- ALTER DATABASE statement, compatibility levels
- 90 compatibility level
- compatibility levels [SQL Server]
- 100 compatibility level
- db compatibility level
- db compat level
ms.assetid: ca5fd220-d5ea-4182-8950-55d4101a86f6
author: CarlRabeler
ms.author: carlrab
manager: craigg'
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e08cc23d78be8f617d51bd6d8310eaef5aa1f0e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666600"
---
# <a name="alter-database-transact-sql-compatibility-level"></a>ALTER DATABASE (Transact-SQL) 互換性レベル
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

データベースの特定の動作に、指定したバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との互換性を設定します。 その他の ALTER DATABASE オプションについては、「[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)」を参照してください。  

構文表記規則の詳細については、「[Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)」を参照してください。
  
## <a name="syntax"></a>構文  
  
```  
ALTER DATABASE database_name   
SET COMPATIBILITY_LEVEL = { 150 | 140 | 130 | 120 | 110 | 100 | 90 }  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 変更するデータベースの名前を指定します。  
  
 COMPATIBILITY_LEVEL { 150 | 140 | 130 | 120 | 110 | 100 | 90 | 80 }  
 データベースの互換性の対象となる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを指定します。 次の互換性レベルの値を構成することができます (上で示したすべての互換性レベルをすべてのバージョンがサポートしているわけではありません)。  
  
|Product|データベース エンジンのバージョン|互換性レベルの指定|サポートされている互換性レベル値|  
|-------------|-----------------------------|-------------------------------------|------------------------------------------|  
|[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]|15|150|150, 140, 130, 120, 110, 100| 
|[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]|14|140|140, 130, 120, 110, 100|
|[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 論理サーバー|12|130|150, 140, 130, 120, 110, 100|  
|[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] マネージド インスタンス|12|130|150, 140, 130, 120, 110, 100|  
|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|13|130|130, 120, 110, 100|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|12|120|120, 110, 100|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|11|110|110, 100, 90|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|10.5|100|100, 90, 80|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|10|100|100, 90, 80|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|9|90|90, 80|  
|SQL Server 2000|8|80|80|  
  
> [!NOTE]  
> **2018 年 1 月**の時点で、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] で新しく作成されたデータベースの既定の互換性レベルは 140 です。 既存のデータベースに対してデータベースの互換性レベルは更新されません。 これは、お客様の独自の裁量にまかされます。 このため、お客様が最新の改善点を活用するために、最新の互換性レベルに移行することを強くお勧めします。
> 
> お使いのデータベース全体でデータベース互換性レベル 140 を活用するとき、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] の**カーディナリティ推定**モデル、データベース互換性レベル 110 へのマッピングを選択するのであれば、「[ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)」を参照してください。特にそのキーワード `LEGACY_CARDINALITY_ESTIMATION = ON` をご覧ください。
>  
> [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] における 2 つの互換性レベル間での、最も重要なクエリのパフォーマンスの違いを評価する方法の詳細については、「[Improved Query Performance with Compatibility Level 130 in Azure SQL Database](http://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/)」 (Azure SQL Database での互換性レベル 130 によるクエリ パフォーマンスの改善) を参照してください。 この記事では互換性レベル 130 と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を取り上げていますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] で 140 に移行する場合も同じ手法が適用されます。

次のクエリを実行して、接続先である [!INCLUDE[ssDE](../../includes/ssde-md.md)] のバージョンを特定します。  
  
```sql  
SELECT SERVERPROPERTY('ProductVersion');  
```  
  
> [!NOTE]  
> [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] では、互換性レベルに依存する機能がすべてサポートされているわけではありません。  

 現在の互換性レベルを特定するには、**sys.databases (Transact-SQL)** の [compatibility_level](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 列に対してクエリを実行します。  
  
```sql  
SELECT name, compatibility_level FROM sys.databases;  
```  
  
## <a name="remarks"></a>Remarks  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのインストールで、既定の互換性レベルは [!INCLUDE[ssDE](../../includes/ssde-md.md)] のバージョンに設定されます。 データベースはこのレベルに設定されますが、**model** データベースの互換性レベルがこれより低い場合は例外です。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータベースをアップグレードした場合、そのデータベースの互換性レベルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の該当するインスタンスに対して許可される最低レベル以上であれば、既存の互換性レベルが維持されます。 許可されるレベルより低い互換性レベルのデータベースをアップグレードするには、許可される最も下の互換性レベルにデータベースを自動的に設定します。 これはシステム データベースとユーザー データベースの両方に適用されます。   

[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] では、データベースを装着したか復元したとき、また、インプレース アップグレード後、以下の動作が予想されます。 
- アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。    
- アップグレード前のユーザー データベースの互換性レベルが 90 の場合、アップグレードされたデータベースの互換性レベルは 100 に設定されます。これは、[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] でサポートされている下限の互換性レベルです。    
- tempdb、model、msdb、および Resource データベースの互換性レベルは、アップグレード後に現在の互換性レベルに設定されます。  
- master システム データベースは、アップグレード前の互換性レベルを保持します。

`ALTER DATABASE` を使用し、データベースの互換性レベルを変更します。 データベースの新しい互換性レベル設定は `USE <database>` コマンドが発行されたときか、新しいログインがそのデータベースで既定のデータベース コンテキストとして処理されたときに有効になります。     
データベースの現在の互換性レベルを確認するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの **compatibility_level** 列をクエリします。  

> [!NOTE]  
> 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で作成され、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] RTM または Service Pack 1 にアップグレードされる[ディストリビューション データベース](../../relational-databases/replication/distribution-database.md)は、互換性レベルが 90 であり、その他のデータベースではサポートされません。 これはレプリケーションの機能には影響がありません。 新しいバージョンのサービス パックと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードすると、分散データベースの互換性レベルが増加し、**マスター** データベースの互換性レベルと一致します。

## <a name="compatibility-levels-and-sql-server-upgrades"></a>互換性レベルと SQL Server アップグレード  
データベース互換レベルは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のアップグレードを可能にし、それと同時に、アップグレード前と同じデータベース互換性レベルを維持することでデータベースに接続するアプリケーションの機能的な状態を維持するという点で、データベースの現代化支援に不可欠なツールです。 上位のデータベース互換性レベルでのみ利用できる拡張をアプリケーションが活用する必要がない限り、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] をアップグレードし、同時に前のデータベース互換性レベルを維持することは有効なアプローチです。 下位互換性で互換性レベルを使用する方法については、この記事の後半に出てくる「[旧バージョンとの互換性を維持するための互換性レベルの使用](#using-compatibility-level-for-backward-compatibility)」を参照してください。    

新しい開発作業の場合、あるいは新しい機能とクエリ オプティマイザー スペースで行われたパフォーマンス改善を既存のアプリケーションで使用する必要があるとき、データベース互換性レベルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で利用できる最新のレベルにアップグレードすることを計画し、その互換性レベルでアプリケーションが動作することを確認します。 データベース互換性レベルのアップグレードについては、この記事の後半に出てくる「[データベース互換性レベルのアップグレードのベスト プラクティス](#best-practices-for-upgrading-database-compatibility-level)」を参照してください。     

> [!TIP] 
> あるアプリケーションが特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンでテストされ、確認された場合、そのアプリケーションはその [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンのネイティブ データベース互換性レベルで暗黙的にテストされ、確認されたことになります。
> 
> そのため、データベース互換性レベルは、テストされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンに該当するデータベース互換性レベルを使用するとき、既存のアプリケーションの互換性を簡単に証明する方法となります。
>
> 互換性レベルの違いについては、この記事の後半に出てくるセクションを参照してください。 

アップグレード前に存在したデータベース互換性レベルとそのサポート可能なステータスを維持しながら、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] を最新バージョンにアップグレードするには、[Microsoft Data Migration Assistant](http://www.microsoft.com/download/details.aspx?id=53595) ツール (DMA) を使用し、データベースのアプリケーション コードの攻撃可能な領域に静的な機能検証を実行することをお勧めします。 DMA ツールの出力でエラーが見つからなければ、あるいは機能性に不足や非互換性がなければ、新しいターゲット バージョンでアプリケーションの機能が退化することはありません。 DMA ツールの詳細については、[こちら](http://blogs.msdn.microsoft.com/datamigration/dma)を参照してください。

> [!NOTE] 
> DMA は、レベル 100 以降のデータベース互換性レベルに対応しています。 ソース バージョンとしての [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] は除外されます。 

> [!IMPORTANT] 
> Microsoft では、最小限のテストをいくつか行い、アップグレードが成功し、さらに前のデータベース互換性レベルが維持されていることを確認することをお勧めしています。 自分のアプリケーションとシナリオでは何が「最小限のテスト」に相当するのかは、ご自身で判断してください。 

> [!NOTE] 
> Microsoft は、次の場合にクエリ プラン シェイプ保護を提供します。
> - 前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョン (ソース) が実行されていたハードウェアに相当するハードウェアで新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョン (ターゲット) が実行されるとき。 
> - ターゲット [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とソース [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の両方で同じ[サポートされているデータベース互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#remarks)が使用されるとき。 
> 
> 上の条件で発生する (ソース [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と比較したときの) クエリ プラン シェイプ退化は対処されます。 このような場合は、Microsoft カスタマー サポートにお問い合わせください。

## <a name="using-compatibility-level-for-backward-compatibility"></a>旧バージョンとの互換性を維持するための互換性レベルの使用  
*データベース互換性レベル*設定は、サーバー全体ではなく、指定したデータベースの動作にのみ影響します。 データベース互換性レベルでは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との部分的な下位互換性だけが保たれます。   

> [!TIP]
> "*データベース互換性レベル*" はデータベース レベルの設定なので、新しい [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] で実行しているアプリケーションが古いデータベース互換性レベルを使用している場合でも、アプリケーションを変更する必要なく、サーバー レベルの拡張機能を利用できます。
>
> これには、新しい[システム動的管理ビュー](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)や[拡張イベント](../../relational-databases/extended-events/extended-events.md)など、豊富な監視とトラブルシューティングに関する改善が含まれます。 また、[自動ソフト NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md#automatic-soft-numa) などのスケーラビリティの向上も含まれます。

互換モード 130 以降、機能に影響を与える新しいクエリ プランは、新しい互換性レベルにのみ意図的に追加されています。 これは、クエリ プランの変更によってパフォーマンスの低下から発生するためのアップグレード中に、リスクを最小限に抑えるために追加されました。   
アプリケーションの観点からは、新しい機能のいくつかを継承し、クエリ オプティマイザー スペースで行われたパフォーマンス改善を継承するために、ある時点で最新の互換性レベルにアップグレードすることは目的であり続けますが、それをコントロールされた方法で行います。 関連する互換性レベル設定によって制御される動作では、安全な移行補助として下位の互換性レベルを使用し、バージョンの違いに対処してください。 データベース互換性レベルのアップグレードで推奨されるワークフローなど、詳細については、この記事の後半に出てくる「[データベース互換性レベルのアップグレードのベスト プラクティス](#best-practices-for-upgrading-database-compatibility-level)」を参照してください。  
  
> [!IMPORTANT]
> 特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンで導入された機能が廃止されている場合、その機能は互換性レベルによって保護されません。 これは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] から削除された機能に当てはまります。
> 
> たとえば、`FASTFIRSTROW` ヒントは [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] で廃止され、`OPTION (FAST n )` ヒントに置き換えられました。 データベースの互換性レベルを 110 に設定すると、廃止されたヒントは復元されません。
> 廃止された機能の詳細については、「[SQL Server 2016 で廃止されたデータベース エンジンの機能](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)」、「[SQL Server 2014 で廃止されたデータベース エンジンの機能](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)」、「[SQL Server 2012 で廃止されたデータベース エンジンの機能](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)」、および「[SQL Server 2008 で廃止されたデータベース エンジンの機能](../../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)」を参照してください。

> [!IMPORTANT]
> 特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンで導入された重大な変更が、互換性レベルによって保護されない**可能性があります**。 これは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のバージョン間の動作変更に当てはまります。 [!INCLUDE[tsql](../../includes/tsql-md.md)] の動作は、通常、互換性レベルで保護されます。 ただし、変更または削除されたシステム オブジェクトは、互換性レベルで保護**されません**。
>
> 互換性レベルで**保護される**重大な変更の例としては、datetime データ型から datetime2 データ型への暗黙的な変換が挙げられます。 データベース互換性レベル 130 では、これらの変換が行われると小数ミリ秒を考慮することで精度が上がり、結果的に異なる変換値が生成されます。 以前の変換動作を復元するには、データベース互換性レベルを 120 以下に設定します。
>
> 互換性レベルで**保護されない**重大な変更の例としては、次のような内容が挙げられます。
> -  システム オブジェクトで変更された列名。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、sys.dm_os_sys_info 内の列 *single_pages_kb* の名前が *pages_kb* に変更されました。 互換性レベルに関係なく、クエリ `SELECT single_pages_kb FROM sys.dm_os_sys_info` によってエラー 207 (無効な列名) が生成されます。
> -  削除されたシステム オブジェクト。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、`sp_dboption` が削除されました。 互換性レベルに関係なく、ステートメント `EXEC sp_dboption 'AdventureWorks2016CTP3', 'autoshrink', 'FALSE';` はエラー 2812 (ストアド プロシージャ 'sp_dboption' が見つかりませんでした) を生成します。
>
> 重大な変更の詳細については、「[SQL Server 2017 におけるデータベース エンジン機能の重大な変更](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2017.md)」、「[SQL Server 2016 におけるデータベース エンジン機能の重大な変更](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)」、「[ SQL Server 2014 におけるデータベース エンジン機能の重大な変更](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)」、「[SQL Server 2012 におけるデータベース エンジン機能の重大な変更](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)、および[SQL Server 2008 におけるデータベース エンジン機能の重大な変更](../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)」を参照してください。
  
## <a name="best-practices-for-upgrading-database-compatibility-level"></a>データベース互換性レベルのアップグレードのベスト プラクティス 
互換性レベルをアップグレードする場合にお勧めするワークフローについては、「[データベース互換性モードの変更とクエリ ストアの使用](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md)」を参照してください。  

## <a name="compatibility-levels-and-stored-procedures"></a>互換性レベルとストアド プロシージャ  
 ストアド プロシージャを実行すると、そのストアド プロシージャが定義されているデータベースの現在の互換性レベルが使用されます。 データベースの互換性設定が変更された場合、そのデータベースのすべてのストアド プロシージャは、設定に合わせて自動的に再コンパイルされます。  

## <a name="differences-between-compatibility-level-140-and-level-150"></a>互換性レベル 140 と互換性レベル 150 との相違点  
このセクションでは、互換性レベル 150 で導入された新しい動作について説明します。

現在、データベース互換レベル 150 は [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] と [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] でプライベート プレビューとして提供されています。 このデータベース互換レベルは、データベース互換レベル 140 で導入されたものを超える、新世代のクエリ処理と関連付けられます。     

データベース互換レベル 150 で使用できるクエリ処理機能の詳細については、「[What's new in SQL Server 2019](../../sql-server/what-s-new-in-sql-server-ver15.md)」 (SQL Server 2019 の新機能) を参照してください。     

## <a name="differences-between-compatibility-level-130-and-level-140"></a>互換性レベル 130 と互換性レベル 140 との相違点  
このセクションでは、互換性レベル 140 で導入された新しい動作について説明します。

|130 以下の互換性レベルの設定|140 の互換性レベルの設定|  
|--------------------------------------------------|-----------------------------------------|  
|複数ステートメントのテーブル値関数を参照するステートメントのカーディナリティの推定値は、固定された行推定値を使用します。|複数ステートメントのテーブル値関数を参照する対象のステートメントのカーディナリティの推定値は、関数出力の実際のカーディナリティを使用します。  これは、複数ステートメントのテーブル値関数の**インターリーブ実行**によって有効にされます。|
|ディスクへのスピルを引き起こす不十分なメモリ許可サイズを要求するバッチモード クエリでは、連続実行において引き続き問題が発生する可能性があります。|ディスクへのスピルを引き起こす不十分なメモリ許可サイズを要求するバッチモード クエリでは、連続実行でのパフォーマンスが改善されている可能性があります。 これは**バッチ モード メモリ許可フィードバック**を介して有効になります。バッチ モード演算子に対してスピルが発生した場合、このフィードバックによりキャッシュ プランのメモリ許可サイズが更新されます。 |
|コンカレンシーの問題を引き起こす過度なメモリ許可サイズを要求するバッチモード クエリでは、連続実行において引き続き問題が発生する可能性があります。|コンカレンシーの問題を引き起こす過度なメモリ許可サイズを要求するバッチモード クエリでは、連続実行でのコンカレンシーが改善されている可能性があります。 これは**バッチ モード メモリ許可フィードバック**を介して有効になります。過度な容量が元々要求されている場合、このフィードバックによりキャッシュ プランのメモリ許可サイズが更新されます。|
|結合演算子を含むバッチモード クエリは、3 つの物理結合アルゴリズム (入れ子になったループ、ハッシュ結合、マージ結合) の対象となります。 カーディナリティの推定値が結合入力として適切でない場合は、不適切な結合アルゴリズムが選択される場合があります。 そのような事態になった場合は、パフォーマンスが低下し、キャッシュ プランが再コンパイルされるまで不適切な結合アルゴリズムが使用中のままとなります。|その他に**適応型結合**と呼ばれる結合演算子もあります。 カーディナリティの推定値が外部ビルドの結合入力として適切でない場合は、不適切な結合アルゴリズムが選択されることがあります。 このような事態が発生し、ステートメントが適応型結合の対象である場合は、小さな結合入力には入れ子になったループが使用され、大きな結合入力にはハッシュ結合が使用されます。これらの使用は再コンパイルを要求することなく動的に行われます。 |
|列ストア インデックスを参照する単純なプランは、バッチ モード実行の対象ではありません。 |列ストア インデックスを参照する単純なプランは、バッチ モード実行の対象であるプランを優先するために廃止されます。|
|`sp_execute_external_script` UDX 演算子は、行モードでのみ実行できます。|`sp_execute_external_script` UDX 演算子は、バッチ モードでの実行に適しています。|  
|複数ステートメントのテーブル値関数 (TVF) にはインターリーブ実行はありません。 |複数ステートメントの TVF のインターリーブ実行で、プランの品質を向上。|

SQL Server 2017 より前の SQL Server の初期のバージョンのトレース フラグ 4199 での修正プログラムは、既定で有効になりました。 互換モード 140 の場合。 トレース フラグ 4199 は、SQL Server 2017 の後にリリースされるクエリ オプティマイザーの新しい修正プログラムにも引き続き適用可能です。 トレース フラグ 4199 については、「[トレース フラグ 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md#4199)」を参照してください。  
  
## <a name="differences-between-compatibility-level-120-and-level-130"></a>レベル 120 とレベルの 130 の互換性の相違点  
このセクションでは、互換性レベル 130 で導入された新しい動作について説明します。   

|互換性レベル設定 120 以下|130 の互換性レベルの設定|  
|--------------------------------------------------|-----------------------------------------|  
|INSERT-SELECT ステートメント内の INSERT はシングル スレッドです。|INSERT-SELECT ステートメントの INSERT はマルチ スレッドであるか、並列プランを与えることができます。|  
|メモリ最適化テーブルに対するクエリでは、シングル スレッドを実行します。|メモリ最適化テーブルに対するクエリで、並列プランを利用できるようになりました。|  
|SQL 2014 のカーディナリティ推定機能 **CardinalityEstimationModelVersion="120"** が導入されました。|さらにカーディナリティの推定 (CE)、クエリから表示されるカーディナリティの推定モデルの 130 の改良点を計画します。 **CardinalityEstimationModelVersion="130"**| 
|列ストア インデックスで行モードがバッチ モードに変更:<br /><ul><li>列ストア インデックスを持つテーブルでの並べ替えが行モードでは <li>ウィンドウ関数の集計が `LAG` や `LEAD` などの行のモードで動作します。 <li>行のモードで運用されている複数の個別の句を持つ列ストア テーブルに対するクエリ <li>MAXDOP 1 または行モードで実行される直列プランで実行されているクエリ</li></ul>| 列ストア インデックスで行モードがバッチ モードに変更:<br /><ul><li>列ストア インデックスを持つテーブルでの並べ替えがバッチ モードです。 <li>ウィンドウ集計が `LAG` や `LEAD` などのバッチモードで動作します。 <li>複数の distinct 句で列ストア テーブルに対するクエリがバッチ モードで動作します。 <li>MAXDOP 1 または直列プランで実行されているクエリをバッチ モードで実行します。</li></ul>|  
|統計情報を自動的に更新できます。 | 統計情報を自動的に更新するロジックは、大規模なテーブルでより積極的に活用されます。  実際には、これにより、クエリに関するパフォーマンス上の問題 (新たに挿入された行に対してクエリが頻繁に実行されるが、それらの値を取り込むための統計情報の更新が行われていない) に顧客が遭遇するケースが減少します。 |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、トレース 2371 は既定ではオフになっています。 | [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] では、[トレース 2371](https://blogs.msdn.microsoft.com/psssql/2016/10/04/default-auto-statistics-update-threshold-change-for-sql-server-2016/) は既定では ON です。 トレース フラグ 2371 は、多くの行を含むテーブル内で、小さくても有用な行のサブセットをサンプリングするように自動統計更新ツールに指示します。 <br/> <br/> 1 つの改良点は、最近挿入された行をより多くサンプルに含めるというものです。 <br/> <br/> もう 1 つの改良点は、統計の更新プロセスが実行されている間に、クエリをブロックするのでなく、クエリが実行されるようにするというものです。 |  
|レベル 120 の場合、統計情報は*シングル* スレッド プロセスによってサンプリングされます。|レベル 130 の場合、統計情報は*マルチ*スレッド プロセスによってサンプリングされます。 |  
|253 の入力方向の外部キーは制限です。| 指定されたテーブルは、最大 10,000 個の入力方向の外部キーまたは類似の参照方法によって参照することができます。 制限については、「 [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md)」を参照してください。 |  
|非推奨の MD2、MD4、MD5、SHA、SHA1 のハッシュ アルゴリズムは許可されます。|SHA2_256 と SHA2_512 のハッシュ アルゴリズムのみが許可されます。|
||[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] では、一部のデータ型変換と一部の (大抵は一般的ではない) 操作に改良が加えられました。 詳細については、「[いくつかのデータ型と一般的でない操作を処理するときの SQL Server と Azure の SQL データベースの機能強化](https://support.microsoft.com/help/4010261/sql-server-2016-improvements-in-handling-some-data-types-and-uncommon)」をご覧ください。|
|STRING_SPLIT 関数は使用できません。|STRING_SPLIT 関数は、互換性レベル 130 以上で利用できます。 データベースの互換性レベルが 130 よりも低い場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は STRING_SPLIT 関数を見つけて実行することができません。|
  
[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] より前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の初期のバージョンのトレース フラグ 4199 での修正プログラムは、既定で有効になりました。 互換モードは 130 です。 トレース フラグ 4199 は、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] の後にリリースされる、クエリ オプティマイザーの新しい修正プログラムに対しても引き続き適用することができます。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] で古いクエリ オプティマイザーを使用するには、互換性レベル 110 を選択する必要があります。 トレース フラグ 4199 については、「[トレース フラグ 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md#4199)」を参照してください。  
  
## <a name="differences-between-lower-compatibility-levels-and-level-120"></a>レベル 120 とより低い互換性レベルとの相違点  
 ここでは、互換性レベル 120 に導入された新しい動作について説明します。  
  
|互換性レベル設定 110 以下|互換性レベル設定 120|  
|--------------------------------------------------|-----------------------------------------|  
|以前のクエリ オプティマイザーが使用されます。|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、クエリ プランを作成し最適化するコンポーネントに大幅な改良が加えられました。 この新しいクエリ オプティマイザー機能は、データベース互換性レベル 120 を使用している場合にのみ利用できます。 これらの改良点を利用するには、データベースの互換性レベル 120 を使用して新しいデータベース アプリケーションを開発する必要があります。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から移行されたアプリケーションについては、良好なパフォーマンスが維持されているか、またはパフォーマンスが向上していることを確認するために慎重にテストを実行する必要があります。 パフォーマンスが低下する場合は、データベースの互換性レベルを 110 以前に設定して、古いクエリ オプティマイザーの方法を使用することができます。<br /><br /> データベースの互換性レベル 120 に設定した場合は、最新のデータ ウェアハウスと OLTP ワークロード向けにチューニングされた新しいカーディナリティ推定機能が使用されます。 パフォーマンスの問題に関連してデータベースの互換性レベルを 110 に設定する前に、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] に関するトピック「[データベース エンジンの新機能](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md)」のクエリ プラン セクションに掲載されている推奨事項を参照してください。|  
|互換性レベルが 120 未満の場合、**日付**値を文字列値に変換すると、言語設定は無視されます。 この動作は **date** 型に固有の動作であることに注意してください。 以下の「例」の B を参照してください。|**日付**値を文字列値に変換するときに、言語設定は無視されません。|  
|`EXCEPT` 句の右側にある再帰参照によって、無限ループが作成されます。 この動作については、以下の「例」の C を参照してください。|`EXCEPT` 句の再帰参照によって、ANSI SQL 標準に準拠したエラーが生成されます。|  
|再帰共通テーブル式 (CTE) では重複する列名を使用できます。|再帰 CTE では、重複する列名を使用できません。|  
|無効化されたトリガーは、トリガーが変更されると有効になります。|トリガーを変更しても、トリガーの状態 (有効または無効) は変更されません。|  
|OUTPUT INTO テーブル句では、`IDENTITY_INSERT SETTING = OFF` が無視され、明示的な値を挿入できます。|`IDENTITY_INSERT` が OFF に設定されているときは、テーブルの ID 列に明示的な値を挿入できません。|  
|データベースの包含状態が PARTIAL に設定されている場合、`MERGE` ステートメントの `OUTPUT` 句にある `$action` フィールドを検証すると、照合順序のエラーが確認されることがあります。|`MERGE` ステートメントの `$action` 句によって返される値の照合順序は、サーバー照合順序ではなく、データベース照合順序です。また、照合順序の競合エラーは返されません。|  
|`SELECT INTO` ステートメントでは、常にシングル スレッドの挿入操作が作成されます。|`SELECT INTO` ステートメントでは、並列挿入操作を作成できます。 多数の行を挿入するときは、並列操作によってパフォーマンスを向上させることができます。|  
  
## <a name="differences-between-lower-compatibility-levels-and-levels-110-and-120"></a>レベル 120 とレベル 110 以下の互換性レベルの相違点  
 このセクションでは、互換性レベル 110 で導入された新しい動作について説明します。   このセクションはレベル 120 にも当てはまります。  
  
|100 以下に、互換性レベル設定|互換性レベル設定 110 以上|  
|--------------------------------------------------|--------------------------------------------------|  
|共通言語ランタイム (CLR) のデータベース オブジェクトは、CLR の Version 4 で実行されます。 ただし、CLR の Version 4 で導入されたいくつかの動作の変更が回避されます。 詳細については、[CLR 統合の新機能](../../relational-databases/clr-integration/clr-integration-what-s-new.md)に関するページを参照してください。|CLR のデータベース オブジェクトは、CLR の Version 4 で実行されます。|  
|XQuery 関数の **string-length** と **substring** は、各サロゲートを 2 つの文字としてカウントします。|XQuery 関数の **string-length** および **substring** は、各サロゲートを 1 つの文字としてカウントします。|  
|`PIVOT` は再帰共通テーブル式 (CTE) のクエリで許可されます。 ただし、グループごとに複数の行がある場合、クエリは誤った結果を返します。|`PIVOT` は再帰共通テーブル式 (CTE) のクエリで許可されません。 エラーが返されます。|  
|RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。|新素材は、RC4 または RC4_128 を使用して暗号化することはできません。 AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。|  
|**time** および **datetime2** データ型に対する `CAST` および `CONVERT` 操作の既定のスタイルは、いずれかの型が計算列の式で使用されている場合を除き、121 です。 計算列の場合、既定のスタイルは 0 です。 この動作は、計算列が作成されるとき、自動パラメーター化を含むクエリで使用されるとき、または制約の定義で使用されるときに、計算列に影響を与えます。<br /><br /> 以下の「例」の D では、スタイル 0 とスタイル 121 の違いを示します。 上記の動作については示しません。 日付および時刻のスタイルの詳細については、「[CAST および CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)」を参照してください。|互換性レベル 110 では、**time** および **datetime2** データ型に対する `CAST` および `CONVERT` 操作の既定のスタイルは常に 121 です。 クエリが古い動作に依存する場合は、110 より小さい互換性レベルを使用するか、または影響を受けるクエリで 0 スタイルを明示的に指定してください。<br /><br /> データベースを互換性レベル 110 にアップグレードしても、ディスクに格納されているユーザー データは変更されません。 このようなデータは手動で適切に修正する必要があります。 たとえば、`SELECT INTO` を使用して、前に説明した計算列の式を含むソースからテーブルを作成した場合は、計算列の定義自体ではなく、(スタイル 0 を使用する) データが格納されます。 このようなデータは、手動で更新してスタイル 121 に一致させる必要があります。|  
|パーティション ビューで参照されるリモート テーブルの **smalldatetime** 型の列は、**datetime** としてマップされます。 ローカル テーブルの対応する列 (選択リストの同じ順番にある列) は、**datetime** 型であることが必要です。|パーティション ビューで参照されるリモート テーブルの **smalldatetime** 型の列は、**smalldatetime** としてマップされます。 ローカル テーブルの対応する列 (選択リストの同じ順番にある列) は、**smalldatetime** 型であることが必要です。<br /><br /> 110 にアップグレードした後は、データ型の不一致により、分散パーティション ビューは失敗します。 この問題を解決するには、リモート テーブルでのデータ型を **datetime** に変更するか、またはローカル データベースの互換性レベルを 100 以下に設定します。|  
|`SOUNDEX` 関数では次のルールが実装されます。<br /><br /> 1) `SOUNDEX` コードの同じ数値が割り当てられている 2 つの子音の間に大文字の H または大文字の W がある場合、この H または W は無視されます。<br /><br /> 2) *character_expression* の最初の 2 文字に `SOUNDEX` コードの同じ数値が割り当てられている場合は、両方の文字が含まれます。 最初の 2 文字の場合を除き、並んでいる一連の子音に `SOUNDEX` コードの同じ数値が割り当てられている場合、最初の文字以外はすべて除外されます。|`SOUNDEX` 関数では次のルールが実装されます。<br /><br /> 1) `SOUNDEX` コードの同じ数値が割り当てられている 2 つの子音の間に大文字の H または大文字の W がある場合、右側の子音は無視されます。<br /><br /> 2) 並んでいる一連の子音に `SOUNDEX` コードの同じ数値が割り当てられている場合、最初の文字以外はすべて除外されます。<br /><br /> <br /><br /> その他のルールにより、`SOUNDEX` 関数で計算された値が、110 未満の互換性レベルで計算された値と異なる結果になる場合があります。 互換性レベル 110 へのアップグレード後に、`SOUNDEX` 関数を使用するインデックス、ヒープ、または CHECK 制約の再構築が必要になる場合があります。 詳細については、「[SOUNDEX &#40;Transact-SQL&#41](../../t-sql/functions/soundex-transact-sql.md)」を参照してください。|  
  
## <a name="differences-between-compatibility-level-90-and-level-100"></a>互換性レベル 90 とレベル 100 の相違点  
 このセクションでは、互換性レベル 100 で導入された新しい動作について説明します。  
  
|90 の互換性レベルの設定|互換性レベルの設定は 100|影響度|  
|----------------------------------------|-----------------------------------------|---------------------------|  
|複数ステートメントのテーブル値関数が作成されるとき、QUOTED_IDENTIFER 設定はセッション レベルの設定に関係なく常に ON に設定されます。|複数ステートメントのテーブル値関数が作成されるとき、QUOTED IDENTIFIER のセッション設定が受け入れられます。|Medium|  
|パーティション関数を作成または変更するとき、関数の **datetime** リテラルおよび **smalldatetime** リテラルは、言語設定が US_English であることを前提に評価されます。|パーティション関数の **datetime** リテラルおよび **smalldatetime** リテラルを評価する際、現在の言語設定が使用されます。|Medium|  
|`INSERT` および `SELECT INTO` ステートメントで `FOR BROWSE` 句は許可されます (ただし無視されます)。|`INSERT` および `SELECT INTO` ステートメントで `FOR BROWSE` 句は許可されません。|Medium|  
|`OUTPUT` 句でフルテキスト述語を使用できます。|`OUTPUT` 句でフルテキスト述語を使用できません。|Low|  
|`CREATE FULLTEXT STOPLIST`、`ALTER FULLTEXT STOPLIST`、および`DROP FULLTEXT STOPLIST` はサポートされていません。 システム ストップリストは、自動的に新しいフルテキスト インデックスに関連付けられます。|`CREATE FULLTEXT STOPLIST`、`ALTER FULLTEXT STOPLIST`、および`DROP FULLTEXT STOPLIST` はサポートされています。|Low|  
|`MERGE` は予約されたキーワードとして適用されません。|MERGE は完全に予約されたキーワードです。 `MERGE` ステートメントは、100 と 90 の両方の互換性レベルでサポートされます。|Low|  
|INSERT ステートメントの \<dml_table_source> 引数を使用すると、構文エラーが発生します。|入れ子になった INSERT、UPDATE、DELETE、または MERGE ステートメント内の OUTPUT 句の結果をキャプチャして、対象のテーブルまたはビューに挿入することができます。 そのためには、INSERT ステートメントの \<dml_table_source> 引数を使用します。|Low|
|`NOINDEX` が指定されていない場合、`DBCC CHECKDB` または `DBCC CHECKTABLE` は、1 つのテーブルまたはインデックス付きビューとそのすべての非クラスター化インデックスおよび XML インデックスについて、物理的な一貫性と論理的な一貫性の両方をチェックします。 空間インデックスはサポートされません。|`NOINDEX` が指定されていない場合、`DBCC CHECKDB` または `DBCC CHECKTABLE` は、1 つのテーブルとそのすべての非クラスター化インデックスについて、物理的な一貫性と論理的な一貫性の両方をチェックします。 ただし、XML インデックス、空間インデックス、およびインデックス付きビューでは、既定で物理的な一貫性のみがチェックされます。<br /><br /> `WITH EXTENDED_LOGICAL_CHECKS` が指定されている場合、インデックス付きビュー、XML インデックス、および空間インデックス (存在する場合) に対して論理チェックが実行されます。 既定では、論理的な一貫性のチェック前に物理的な一貫性がチェックされます。 `NOINDEX` も指定されている場合は、論理チェックのみが実行されます。|Low|  
|データ操作言語 (DML) ステートメントで OUTPUT 句を使用した場合、ステートメントの実行時に実行時エラーが発生すると、トランザクション全体が終了し、ロールバックされます。|データ操作言語 (DML) ステートメントで `OUTPUT` 句を使用した場合、ステートメントの実行時に実行時エラーが発生したときの動作は、`SET XACT_ABORT` 設定によって異なります。 `SET XACT_ABORT` が OFF の場合は、`OUTPUT` 句を使用している DML ステートメントでステートメント中断エラーが発生すると、ステートメントは終了しますが、バッチの実行は続行され、トランザクションはロールバックされません。 `SET XACT_ABORT` が ON の場合は、OUTPUT 句を使用している DML ステートメントで実行時エラーが発生すると、バッチが終了し、トランザクションはロールバックされます。|Low|  
|CUBE および ROLLUP は予約されたキーワードとして適用されません。|`CUBE` および `ROLLUP` は、GROUP BY 句内では予約されたキーワードです。|Low|  
|XML の **anyType** 型の要素には厳密な検証が適用されます。|**anyType** 型の要素には緩やかな検証が適用されます。 詳細については、「[ワイルドカード コンポーネントと内容検証](../../relational-databases/xml/wildcard-components-and-content-validation.md)」を参照してください。|Low|  
|特殊な属性 **xsi:nil** および **xsi:type** は、データ操作言語ステートメントでクエリまたは変更できません。<br /><br /> つまり、`/e/@xsi:nil` は失敗し、`/e/@*` では **xsi:nil** 属性と **xsi:type** 属性が無視されます。 ただし、`/e` の場合でも、`SELECT xmlCol` では `xsi:nil = "false"` との一貫性のために **xsi:nil** 属性と **xsi:type** 属性が返されます。|特殊な属性 **xsi:nil** および **xsi:type** は、標準属性として格納されるので、クエリも変更も可能です。<br /><br /> たとえば、クエリ `SELECT x.query('a/b/@*')` を実行すると、**xsi:nil** および **xsi:type** を含むすべての属性が返されます。 クエリでこれらの型を除外するには、`@*` を `@*[namespace-uri(.) != "`*insert xsi namespace uri*`"` に置き換え、`(local-name(.) = "type"` や `local-name(.) ="nil".` を避けてください。|Low|  
|XML 定数文字列値を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datetime 型に変換するユーザー定義関数は、"決定的" とマークされます。|XML 定数文字列値を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datetime 型に変換するユーザー定義関数は、"非決定的" とマークされます。|Low|  
|XML の union 型と list 型は、完全にはサポートされていません。|union 型と list 型は、完全にサポートされています (次の機能を含む)。<br /><br /> リストの和集合<br /><br /> 和集合の和集合<br /><br /> アトミック型のリスト<br /><br /> 和集合のリスト|Low|  
|xQuery メソッドに必要な SET オプションは、メソッドがビューまたはインライン テーブル値関数に含まれる場合に検証されません。|xQuery メソッドに必要な SET オプションは、メソッドがビューまたはインライン テーブル値関数に含まれる場合に検証されます。 メソッドの SET オプションが正しく設定されていない場合は、エラーが発生します。|Low|  
|行末文字 (復帰と改行) を含む XML 属性値は、XML 標準に従って正規化されません。 つまり、1 つの改行文字ではなく両方の文字が返されます。|行末文字 (復帰と改行) を含む XML 属性値は、XML 標準に従って正規化されます。 つまり、外部解析エンティティ (ドキュメント エンティティを含む) のすべての改行が、入力時に正規化されます。このとき、2 文字のシーケンス #xD #xA と、後ろに #xA がない #xD の両方について、1 つの #xA 文字に変換されます。<br /><br /> 行末文字を含む文字列値を転送するための属性を使用しているアプリケーションは、このような文字が送信されても受け取りません。 正規化処理を回避するには、XML 数字エンティティを使用してすべての行末文字をエンコードしてください。|Low|  
|列プロパティ `ROWGUIDCOL` および `IDENTITY` は、制約として不適切に指定される可能性があります。 たとえば、ステートメント `CREATE TABLE T (C1 int CONSTRAINT MyConstraint IDENTITY)` は実行されますが、制約名は保持されず、ユーザーはその制約にアクセスできません。|列プロパティ `ROWGUIDCOL` および `IDENTITY` は、制約として指定できません。 156 のエラーが返されます。|Low|  
|`UPDATE T1 SET @v = column_name = <expression>` などの双方向の代入を使用して列を更新すると、予期しない結果が生じる可能性があります。これは、ステートメントの実行時に、`WHER`E 句や `ON` 句などの他の句でステートメントの開始値ではなく変数の有効期限の値を使用できるためです。 これにより、述語の意味が行ごとに予期せず変化することがあります。<br /><br /> この動作は、互換性レベルが 90 に設定されている場合にのみ適用されます。|双方向の代入を使用して列を更新すると、予想どおりの結果が生じます。これは、ステートメントの実行時に、列のステートメントの開始値のみが利用されるためです。|Low|  
|以下の「例」の E を参照してください。|以下の「例」の F を参照してください。|Low|  
|ODBC 関数 {fn CONVERT()} では、言語の既定の日付形式が使用されます。 言語によっては、既定の形式が YDM の場合があります。この場合、CONVERT() を `{fn CURDATE()}` などの YMD 形式が想定されている他の関数と組み合わせて使用すると、変換エラーが発生する可能性があります。|ODBC 関数 `{fn CONVERT()}` では、ODBC データ型 SQL_TIMESTAMP、SQL_DATE、SQL_TIME、SQLDATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP への変換時にスタイル 121 (言語に依存しない YMD 形式) が使用されます。|Low|  
|DATEPART などの datetime 組み込み関数では、文字列入力値が有効な datetime リテラルである必要はありません。 たとえば、`SELECT DATEPART (year, '2007/05-30')` は正常にコンパイルされます。|`DATEPART` などの datetime 組み込み関数では、文字列入力値が有効な datetime リテラルである必要があります。 無効な datetime リテラルを使用すると、エラー 241 が返されます。|Low|  
  
## <a name="reserved-keywords"></a>予約済みキーワード  
 互換性設定では、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で予約されているキーワードも判別されます。 次の表は、各互換性レベルで使用される予約済みキーワードです。  
  
|互換性レベル設定|予約済みキーワード|  
|----------------------------------|-----------------------|  
|130|未定。|  
|120|[なし] :|  
|110|WITHIN GROUP、TRY_CONVERT、SEMANTICKEYPHRASETABLE、SEMANTICSIMILARITYDETAILSTABLE、SEMANTICSIMILARITYTABLE|  
|100|CUBE、MERGE、ROLLUP|  
|90|EXTERNAL、PIVOT、UNPIVOT、REVERT、TABLESAMPLE|  
  
 各互換性レベルの予約済みキーワードには、そのレベル以下で導入されるキーワードもすべて含まれています。 したがって、たとえばレベル 110 のアプリケーションの場合、上の表に一覧表示されているすべてのキーワードが予約されています。 それより下位の互換性レベルでは、レベル 100 のキーワードは有効なオブジェクト名ですが、そのキーワードに対応するレベル 110 の言語機能は使用できません。  
  
 キーワードはいったん導入されると、キーワードの予約が維持されます。 たとえば、互換性レベル 90 で導入された予約済みキーワード PIVOT は、レベル 100、110、および 120 でも予約済みとして扱われます。  
  
 互換性レベル設定でキーワードとして予約した識別子をアプリケーションで使用しようとすると、アプリケーションは失敗します。 この問題を回避するには、識別子をかっこ (**[]**) または引用符 (**""**) で囲みます。たとえば、識別子 **EXTERNAL** を使用しているアプリケーションを互換性レベル 90 にアップグレードするには、識別子を **[EXTERNAL]** または **"EXTERNAL"** のように変更します。  
  
 詳細については、「[予約済みキーワード &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-compatibility-level"></a>A. 互換性レベルを変更する  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの互換性レベルを `110,`[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] に変更します。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 110;  
GO  
```  
  
 次の例では、現在のデータベースの互換性レベルを返します。  
  
```sql  
SELECT name, compatibility_level   
FROM sys.databases   
WHERE name = db_name();  
```  
  
### <a name="b-ignoring--the-set-language-statement-except-under-compatibility-level-120"></a>B. 互換性レベルが 120 の場合を除き、SET LANGUAGE ステートメントを無視する  
 次のクエリでは、互換性レベルが 120 の場合を除き、SET LANGUAGE ステートメントは無視されます。  
  
```sql  
SET DATEFORMAT dmy;   
DECLARE @t2 date = '12/5/2011' ;  
SET LANGUAGE dutch;   
SELECT CONVERT(varchar(11), @t2, 106);   
  
-- Results when the compatibility level is less than 120.   
12 May 2011   
  
-- Results when the compatibility level is set to 120).  
12 mei 2011  
```  
  
### <a name="c"></a>C.  
 互換性レベルが 110 以下に設定されている場合、EXCEPT 句の右側にある再帰参照によって、無限ループが作成されます。  
  
```sql  
WITH   
cte AS (SELECT * FROM (VALUES (1),(2),(3)) v (a)),  
r   
AS (SELECT a FROM Table1  
UNION ALL  
(SELECT a FROM Table1 EXCEPT SELECT a FROM r) )   
SELECT a   
FROM r;  
  
```  
  
### <a name="d"></a>D.  
 次の例では、スタイル 0 とスタイル 121 の違いを示します。 日付および時刻のスタイルの詳細については、「[CAST および CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)」を参照してください。  
  
```sql  
CREATE TABLE t1 (c1 time(7), c2 datetime2);   
  
INSERT t1 (c1,c2) VALUES (GETDATE(), GETDATE());  
  
SELECT CONVERT(nvarchar(16),c1,0) AS TimeStyle0  
       ,CONVERT(nvarchar(16),c1,121)AS TimeStyle121  
       ,CONVERT(nvarchar(32),c2,0) AS Datetime2Style0  
       ,CONVERT(nvarchar(32),c2,121)AS Datetime2Style121  
FROM t1;  
  
-- Returns values such as the following.  
TimeStyle0       TimeStyle121       
Datetime2Style0      Datetime2Style121  
---------------- ----------------   
-------------------- --------------------------  
3:15PM           15:15:35.8100000   
Jun  7 2011  3:15PM  2011-06-07 15:15:35.8130000  
```  
  
### <a name="e"></a>E.  
 変数代入は、最上位レベルの UNION 演算子を含むステートメントで許可されていますが、予期しない結果が返されます。 たとえば、次のステートメントでは、2 つのテーブルの和集合からの列 `BusinessEntityID` の値がローカル変数 `@v` に割り当てられます。 定義上、SELECT ステートメントが複数の値を返した場合は、最後に返された値が変数に割り当てられます。 この場合は、最後の値が変数に正しく割り当てられますが、SELECT UNION ステートメントの結果セットも返されます。  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET compatibility_level = 110;  
GO  
USE AdventureWorks2012;  
GO  
DECLARE @v int;  
SELECT @v = BusinessEntityID FROM HumanResources.Employee  
UNION ALL  
SELECT @v = BusinessEntityID FROM HumanResources.EmployeeAddress;  
SELECT @v;  
```  
  
### <a name="f"></a>F.  
 変数代入は、最上位レベルの UNION 演算子を含むステートメントでは許可されていません。 10734 のエラーが返されます。 エラーを解決するには、次の例で示すようにクエリを書き直してください。  
  
```sql  
DECLARE @v int;  
SELECT @v = BusinessEntityID FROM   
    (SELECT BusinessEntityID FROM HumanResources.Employee  
     UNION ALL  
     SELECT BusinessEntityID FROM HumanResources.EmployeeAddress) AS Test;  
SELECT @v;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [予約済みキーワード &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlserver)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
 [データベースの互換性レベルの表示または変更](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) 
  
