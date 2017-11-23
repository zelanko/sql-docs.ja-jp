---
title: "DROP INDEX (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_INDEX_TSQL
- DROP INDEX
dev_langs: TSQL
helpviewer_keywords:
- nonclustered indexes [SQL Server], removing
- MAXDOP index option, DROP INDEX statement
- index removal [SQL Server]
- spatial indexes [SQL Server], dropping
- removing indexes
- deleting indexes
- dropping indexes
- MOVE TO clause
- clustered indexes, removing
- indexes [SQL Server], dropping
- filtered indexes [SQL Server], dropping
- ONLINE option
- indexes [SQL Server], moving
- XML indexes [SQL Server], dropping
- DROP INDEX statement
ms.assetid: 2b1464c8-934c-405f-8ef7-2949346b5372
caps.latest.revision: "99"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 821782102f7c9c6014c3ec46c5e9f9223eca98a0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="drop-index-transact-sql"></a>DROP INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 つ以上のリレーショナル インデックス、空間インデックス、フィルター選択されたインデックス、または XML インデックスを現在のデータベースから削除します。 クラスター化インデックスを削除し、MOVE TO オプションを指定することによって、結果のテーブルを単一のトランザクションで別のファイル グループまたはパーティション構成に移動できます。  
  
 DROP INDEX ステートメントは、PRIMARY KEY 制約または UNIQUE 制約を定義することで作成されたインデックスには適用されません。 制約および対応するインデックスを削除する使用[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) DROP CONSTRAINT 句を使用します。  
  
> [!IMPORTANT]  
>  定義されている構文`<drop_backward_compatible_index>`の将来のバージョンで削除される予定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新規の開発作業ではこの構文を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、`<drop_relational_or_xml_index>` で指定されている構文を使用してください。 XML インデックスは、旧バージョンとの互換性のための構文を使用して削除することはできません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server (All options except filegroup and filestream apply to Azure SQL Database.)  
  
DROP INDEX [ IF EXISTS ]   
{ <drop_relational_or_xml_or_spatial_index> [ ,...n ]   
| <drop_backward_compatible_index> [ ,...n ]  
}  
  
<drop_relational_or_xml_or_spatial_index> ::=  
    index_name ON <object>   
    [ WITH ( <drop_clustered_index_option> [ ,...n ] ) ]  
  
<drop_backward_compatible_index> ::=  
    [ owner_name. ] table_or_view_name.index_name  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_or_view_name  
}  
  
<drop_clustered_index_option> ::=  
{  
    MAXDOP = max_degree_of_parallelism  
  | ONLINE = { ON | OFF }  
  | MOVE TO { partition_scheme_name ( column_name )   
            | filegroup_name  
            | "default"   
            }  
  [ FILESTREAM_ON { partition_scheme_name   
            | filestream_filegroup_name   
            | "default" } ]  
}  
```  
  
```  
-- Syntax for Azure SQL Database  
  
DROP INDEX  
{ <drop_relational_or_xml_or_spatial_index> [ ,...n ]   
}  
  
<drop_relational_or_xml_or_spatial_index> ::=   
    index_name ON <object>  
  
<object> ::=   
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_or_view_name  
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP INDEX index_name ON [ database_name . [schema_name ] . | schema_name . ] table_name  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、インデックスを削除します。  
  
 *index_name*  
 削除するインデックスの名前です。  
  
 *database_name*  
 データベースの名前です。  
  
 *schema_name*  
 テーブルまたはビューが属するスキーマの名前を指定します。  
  
 *table_or_view_name*  
 インデックスに関連付けられているテーブルまたはビューの名前を指定します。 空間インデックスはテーブルでのみサポートされます。  
  
 表示するには、インデックスのレポート オブジェクトを使用して、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビューです。  
  
 Windows Azure SQL データベースでは、database_name が現在のデータベースの場合、または database_name が tempdb で、object_name が # で始まる場合に、3 つの要素で構成された名前形式 database_name.[schema_name].object_name をサポートします。  
  
 \<drop_clustered_index_option >  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 クラスター化インデックス オプションを制御します。 これらのオプションは、他のインデックス型では使用できません。  
  
 MAXDOP = *max_degree_of_parallelism*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] (パフォーマンス レベル P2、P3 のみ)。  
  
 上書き、**並列処理の次数の最大**インデックス操作の実行中の構成オプション。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
> [!IMPORTANT]  
>  MAXDOP は、空間インデックスまたは XML インデックスには使用できません。  
  
 *max_degree_of_parallelism*を指定できます。  
  
 1  
 並列プラン生成を抑制します。  
  
 \>1  
 並列インデックス操作で使用される最大プロセッサ数を、指定した数に制限します。  
  
 0 (既定値)  
 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
> [!NOTE]  
>  並列インデックス操作はすべてのエディションで使用できない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」 (SQL Server 2016 のエディションとサポートされる機能) を参照してください。  
  
 ONLINE = ON |**OFF**  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 インデックス操作時に、基になるテーブルや関連するインデックスをクエリやデータ変更で使用できるかどうかを指定します。 既定値は OFF です。  
  
 ON  
 長期間のテーブル ロックは持続されません。 これにより、基となるテーブルに対してクエリや更新を続けることができます。  
  
 OFF  
 テーブル ロックが適用され、インデックス操作中はテーブルが利用できません。  
  
 クラスター化インデックスを削除するときには、ONLINE オプションだけを指定できます。 詳細については、「解説」を参照してください。  
  
> [!NOTE]  
>  オンラインでのインデックス操作は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[Editions and Supported Features for SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」 (SQL Server 2016 のエディションとサポートされる機能) を参照してください。  
  
 MOVE TO { *partition_scheme_name***(***column_name***)** | *filegroup_name*  |  **"**既定**"**  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]ファイル グループの名前として"default"をサポートします。  
  
 現在クラスター化インデックスのリーフ レベルにあるデータ行を移動する場所を指定します。 データは、ヒープの形式で新しい場所に移動されます。 新しい場所としてパーティション構成またはファイル グループを指定できますが、このパーティション構成やファイル グループはあらかじめ存在している必要があります。 MOVE TO は、インデックス付きビューまたは非クラスター化インデックスに対しては有効ではありません。 パーティション構成やファイル グループを指定しないと、結果のテーブルは、クラスター化インデックスに対して定義されているのと同じパーティション構成またはファイル グループに配置されます。  
  
 MOVE TO を使用してクラスター化インデックスを削除すると、ベース テーブル上の非クラスター化インデックスが再構築されますが、元のファイル グループまたはパーティション構成からは移動されません。 ベース テーブルを別のファイル グループやパーティション構成に移動しても、非クラスター化インデックスは、ベース テーブルの新しい場所 (ヒープ) に同時に移動されません。 したがって、以前に非クラスター化インデックスがクラスター化インデックスに対応した位置にあっても、ヒープとは対応しなくなる可能性があります。 パーティション インデックスの位置合わせの詳細については、次を参照してください。 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)です。  
  
 *partition_scheme_name* **(** *column_name* **)**  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 結果のテーブルのための場所として、パーティション構成を指定します。 パーティション構成する必要があります既に作成されているいずれかの操作を実行することによって[CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md)または[ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md)です。 場所を指定しないでテーブルをパーティション分割すると、テーブルは既存のクラスター化インデックスと同じパーティション構成に格納されます。  
  
 構成内の列名は、インデックス定義内の列に制限されません。 ベース テーブルの任意の列を指定できます。  
  
 *filegroup_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 結果のテーブルのための場所として、ファイル グループを指定します。 場所を指定しないでテーブルをパーティション分割すると、結果のテーブルはクラスター化インデックスと同じファイル グループに格納されます。 ファイル グループは既に存在している必要があります。  
  
 **"**既定**"**  
 結果のテーブルの既定の場所を指定します。  
  
> [!NOTE]  
>  ここでは、default はキーワードではありません。 既定のファイル グループの識別子を指定し、移動先のように区切る必要があります**"**既定**"**または MOVE TO **[**既定**]**です。 場合**"**既定**"** QUOTED_IDENTIFIER オプションは必ず on に、現在のセッションを指定します。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
 FILESTREAM_ON { *partition_scheme_name* | *filestream_filegroup_name* | **"**既定**"** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 現在クラスター化インデックスのリーフ レベルに格納されている FILESTREAM テーブルを移動する場所を指定します。 データは、ヒープの形式で新しい場所に移動されます。 新しい場所としてパーティション構成またはファイル グループを指定できますが、このパーティション構成やファイル グループはあらかじめ存在している必要があります。 FILESTREAM ON は、インデックス付きビューまたは非クラスター化インデックスに対しては無効です。 パーティション構成が指定されていない場合、データは、クラスター化インデックスに定義されていたものと同じパーティション構成に格納されます。  
  
 *partition_scheme_name*  
 FILESTREAM データのパーティション構成を指定します。 パーティション構成する必要があります既に作成されているいずれかの操作を実行することによって[CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md)または[ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md)です。 場所を指定しないでテーブルをパーティション分割すると、テーブルは既存のクラスター化インデックスと同じパーティション構成に格納されます。  
  
 MOVE TO にパーティション構成を指定する場合は、FILESTREAM ON にも同じパーティション構成を使用する必要があります。  
  
 *filestream_filegroup_name*  
 FILESTREAM データの FILESTREAM ファイル グループを指定します。 位置を指定せず、テーブルがパーティション分割されていない場合、データは既定の FILESTREAM ファイル グループに含められます。  
  
 **"**既定**"**  
 FILESTREAM データの既定の位置を指定します。  
  
> [!NOTE]  
>  ここでは、default はキーワードではありません。 既定のファイル グループの識別子を指定し、移動先のように区切る必要があります**"**既定**"**または MOVE TO **[**既定**]**です。 "default" を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON である必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
## <a name="remarks"></a>解説  
 非クラスター化インデックスを削除すると、インデックス定義がメタデータから削除され、インデックス データ ページ (B ツリー) がデータベース ファイルから削除されます。 クラスター化インデックスを削除すると、インデックス定義がメタデータから削除され、クラスター化インデックスのリーフ レベルに格納されたデータ行は、結果の順序付けられていないテーブル (ヒープ) に格納されます。 それまでインデックスが使用していたすべての領域は解放されます。 この領域は、任意のデータベース オブジェクトに使用できます。  
  
 インデックスが格納されているファイル グループがオフラインであるか読み取り専用に設定されている場合には、インデックスを削除することはできません。  
  
 インデックス付きビューのクラスター化インデックスを削除すると、同じビューのすべての非クラスター化インデックスと自動作成された統計情報が自動的に削除されます。 手動で作成した統計情報は削除されません。  
  
 構文*table_or_view_name***.***index_name*の旧バージョンとの互換性を維持します。 XML インデックスまたは空間インデックスは、旧バージョンとの互換性のための構文を使用して削除することはできません。  
  
 128 以上のエクステントを持つインデックスを削除すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]は、トランザクションがコミットされるまで実際のページの割り当て解除と関連するロックを遅らせます。  
  
 新しい FILL FACTOR 値を適用したり、一括読み取りの後でデータを再構成するためなどに、インデックスを削除し、作り直して、再構成または再構築することがあります。 使用して、これを行うには[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)特にクラスター化インデックスの方が効率的です。 ALTER INDEX REBUILD は、非クラスター化インデックスを再構築するオーバーヘッドをなくすために最適化されています。  
  
## <a name="using-options-with-drop-index"></a>DROP INDEX でのオプションの使用  
 クラスター化インデックスを削除する際に、MAXDOP、ONLINE、および MOVE TO インデックス オプションを設定できます。  
  
 MOVE TO は、単一のトランザクションでクラスター化インデックスを削除し、結果のテーブルを別のファイル グループまたはパーティション構成に移動するために使用します。  
  
 ONLINE = ON を指定すると、基となるデータや関連する非クラスター化インデックスに対するクエリと変更は、DROP INDEX トランザクションによってブロックされません。 オンラインでは、一度に 1 つのクラスター化インデックスしか削除できません。 ONLINE オプションの詳細については、次を参照してください。 [CREATE INDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-index-transact-sql.md).  
  
 オンライン インデックスをビューには無効かがある場合、クラスター化インデックスを削除することはできません**テキスト**、 **ntext**、**イメージ**、 **varchar (max)**、**nvarchar (max)**、 **varbinary (max)**、または**xml**列がリーフ レベルのデータ行にします。  
  
 ONLINE = ON オプションおよび MOVE TO オプションを使用するには、追加の一時ディスク領域が必要です。  
  
 インデックスを削除すると、結果として得られるヒープが表示され、 **sys.indexes**カタログ ビュー内の NULL で、**名前**列です。 テーブル名を表示するには、参加**sys.indexes**で**sys.tables**で**object_id**です。 クエリの例については、例 D を参照してください。  
  
 [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] 以降を実行するマルチプロセッサ コンピューターでは、他のクエリと同様に、クラスター化インデックスの削除に関連するスキャン操作や並べ替え操作の実行に、DROP INDEX がより多くのプロセッサを使用する場合があります。 MAXDOP インデックス オプションを指定すると、DROP INDEX ステートメントの実行に使用されるプロセッサ数を手動で構成できます。 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
 クラスター化インデックスを削除する場合、パーティション構成を変更しない限り、対応するヒープ パーティションでデータ圧縮設定が維持されます。 パーティション構成を変更すると、すべてのパーティションが圧縮されていない状態に再構築されます (DATA_COMPRESSION = NONE)。 クラスター化インデックスを削除し、パーティション構成を変更するには、次の 2 つの手順を実行します。  
  
1.  クラスター化インデックスを削除します。  
  
2.  圧縮オプションを指定する ALTER TABLE ... REBUILD ... オプションを使用して、テーブルを変更します。  
  
OFFLINE でクラスター化インデックスを削除すると、クラスター化インデックスの上位レベルだけが削除されます。そのため、操作はとても高速です。 クラスター化インデックスがオンラインで削除されるとき[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]手順 1. と手順 2. の 1 回は、2 つの時刻をヒープ再構築します。 データ圧縮に関する詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
## <a name="xml-indexes"></a>XML インデックス  
 AnXML インデックスを削除するときに、オプションを指定することはできません。 また、使用することはできません、 *table_or_view_name***.***index_name*構文です。 プライマリ XML インデックスを削除すると、関連するすべてのセカンダリ XML インデックスが自動的に削除されます。 詳細については、「[XML インデックス &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)」をご覧ください。  
  
## <a name="spatial-indexes"></a>空間インデックス  
 空間インデックスはテーブルでのみサポートされます。 空間インデックスを削除するオプションを指定または使用ができません**.***index_name*です。 正しい構文は次のとおりです。  
  
 DROP INDEX *spatial_index_name* ON *spatial_table_name*です。  
  
 空間インデックスについての詳細については、次を参照してください。[空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)です。  
  
## <a name="permissions"></a>Permissions  
 少なくとも、DROP INDEX を実行するには、テーブルまたはビューに対する ALTER 権限が必要です。 この権限は、固定サーバー ロール **sysadmin** と、固定データベース ロール **db_ddladmin** および **db_owner** に既定で許可されています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-an-index"></a>A. インデックスを削除する  
 次の例は、インデックスを削除`IX_ProductVendor_VendorID`上、`ProductVendor`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
DROP INDEX IX_ProductVendor_BusinessEntityID   
    ON Purchasing.ProductVendor;  
GO  
```  
  
### <a name="b-dropping-multiple-indexes"></a>B. 複数のインデックスを削除する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースから、単一のトランザクションで 2 つのインデックスを削除します。  
  
```  
DROP INDEX  
    IX_PurchaseOrderHeader_EmployeeID ON Purchasing.PurchaseOrderHeader,  
    IX_Address_StateProvinceID ON Person.Address;  
GO  
```  
  
### <a name="c-dropping-a-clustered-index-online-and-setting-the-maxdop-option"></a>C. クラスター化インデックスをオンラインで削除し、MAXDOP オプションを設定する  
 次の例では、`ONLINE` オプションに `ON` を設定し、`MAXDOP` オプションに `8` を設定してクラスター化インデックスを削除します。 MOVE TO オプションは指定していないため、結果のテーブルは、インデックスと同じファイル グループに格納されます。 この例を使用して、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
```  
DROP INDEX AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate   
    ON Production.BillOfMaterials WITH (ONLINE = ON, MAXDOP = 2);  
GO  
```  
  
### <a name="d-dropping-a-clustered-index-online-and-moving-the-table-to-a-new-filegroup"></a>D. クラスター化インデックスをオンラインで削除し、テーブルを新しいファイル グループに移動する  
 次の例では、クラスター化インデックスをオンラインで削除し、 `NewGroup` 句を使用することで、結果のテーブル (ヒープ) をファイル グループ `MOVE TO` に移動します。 移動の前後で `sys.indexes`、 `sys.tables`、および `sys.filegroups` カタログ ビューを参照し、ファイル グループ内のインデックスとテーブルの配置を確認します。 (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]インデックス IF EXISTS の DROP 構文を使用することができます)。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
--Create a clustered index on the PRIMARY filegroup if the index does not exist.  
CREATE UNIQUE CLUSTERED INDEX  
    AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate   
        ON Production.BillOfMaterials (ProductAssemblyID, ComponentID,   
        StartDate)  
    ON 'PRIMARY';  
GO  
-- Verify filegroup location of the clustered index.  
SELECT t.name AS [Table Name], i.name AS [Index Name], i.type_desc,  
    i.data_space_id, f.name AS [Filegroup Name]  
FROM sys.indexes AS i  
    JOIN sys.filegroups AS f ON i.data_space_id = f.data_space_id  
    JOIN sys.tables as t ON i.object_id = t.object_id  
        AND i.object_id = OBJECT_ID(N'Production.BillOfMaterials','U')  
GO  
--Create filegroup NewGroup if it does not exist.  
IF NOT EXISTS (SELECT name FROM sys.filegroups  
                WHERE name = N'NewGroup')  
    BEGIN  
    ALTER DATABASE AdventureWorks2012  
        ADD FILEGROUP NewGroup;  
    ALTER DATABASE AdventureWorks2012  
        ADD FILE (NAME = File1,  
            FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\File1.ndf')  
        TO FILEGROUP NewGroup;  
    END  
GO  
--Verify new filegroup  
SELECT * from sys.filegroups;  
GO  
-- Drop the clustered index and move the BillOfMaterials table to  
-- the Newgroup filegroup.  
-- Set ONLINE = OFF to execute this example on editions other than Enterprise Edition.  
DROP INDEX AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate   
    ON Production.BillOfMaterials   
    WITH (ONLINE = ON, MOVE TO NewGroup);  
GO  
-- Verify filegroup location of the moved table.  
SELECT t.name AS [Table Name], i.name AS [Index Name], i.type_desc,  
    i.data_space_id, f.name AS [Filegroup Name]  
FROM sys.indexes AS i  
    JOIN sys.filegroups AS f ON i.data_space_id = f.data_space_id  
    JOIN sys.tables as t ON i.object_id = t.object_id  
        AND i.object_id = OBJECT_ID(N'Production.BillOfMaterials','U');  
GO  
```  
  
### <a name="e-dropping-a-primary-key-constraint-online"></a>E. PRIMARY KEY 制約をオンラインで削除する  
 PRIMARY KEY 制約や UNIQUE 制約の結果作成されたインデックスは、DROP INDEX で削除することができません。 そのようなインデックスは、ALTER TABLE DROP CONSTRAINT ステートメントを使用して削除します。 詳細については、次を参照してください。 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)です。  
  
 次の例では、制約を削除することで、PRIMARY KEY 制約によるクラスター化インデックスを削除します。 `ProductCostHistory`テーブルに FOREIGN KEY 制約がありません。 FOREIGN KEY 制約がある場合には、まずそれを削除する必要があります。  
  
```  
-- Set ONLINE = OFF to execute this example on editions other than Enterprise Edition.  
ALTER TABLE Production.TransactionHistoryArchive  
DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID  
WITH (ONLINE = ON);  
```  
  
### <a name="f-dropping-an-xml-index"></a>F. XML インデックスを削除する  
 次の例では、XML インデックスを削除で、`ProductModel`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
DROP INDEX PXML_ProductModel_CatalogDescription   
    ON Production.ProductModel;  
```  
  
### <a name="g-dropping-a-clustered-index-on-a-filestream-table"></a>G. FILESTREAM テーブルのクラスター化インデックスを削除する  
 次の例では、クラスター化インデックスをオンラインで削除し、`MyPartitionScheme` 句と `MOVE TO` 句の両方を使用して、結果のテーブル (ヒープ) と FILESTREAM データを `FILESTREAM ON` パーティション構成に移動します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
DROP INDEX PK_MyClusteredIndex   
    ON dbo.MyTable   
    WITH (MOVE TO MyPartitionScheme,  
          FILESTREAM_ON MyPartitionScheme);  
GO  
```  

  
## <a name="see-also"></a>参照  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [空間インデックス &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [XML インデックス &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-index-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.filegroups &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sp_spaceused &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)  
  
  


