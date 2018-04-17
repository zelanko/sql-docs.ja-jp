---
title: SQL Server XML 一括読み込みオブジェクト モデル (SQLXML 4.0) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b3b3798be063dd586d74cf4f44d72a48c5f39ccf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a>SQL Server XML 一括読み込みオブジェクト モデル (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQLXMLBulkLoad オブジェクトの XML 一括読み込みオブジェクト モデルが構成されます。 このオブジェクトでは、次のメソッドとプロパティがサポートされます。  
  
## <a name="methods"></a>メソッド  
 Execute  
 パラメーターとして渡されるスキーマ ファイルとデータ ファイル (またはストリーム) を使用して、データの一括読み込みを行います。  
  
## <a name="properties"></a>プロパティ  
 一括読み込み  
 一括読み込みを実行するかどうかを指定します。 このプロパティを (後に続く SchemaGen、SGDropTables、および SGUseID プロパティを参照してください)、スキーマだけを生成し、一括読み込みを行わない場合に便利です。 このプロパティはブール値をとります。 このプロパティを TRUE に設定すると、XML 一括読み込みが行われます。 FALSE に設定すると、XML 一括読み込みは行われません。  
  
 既定値は TRUE です。  
  
 CheckConstraints  
 一括読み込みで列にデータを挿入するときに、列に指定されている制約 (列間の主キー/外部キーのリレーションシップによる制約など) をチェックするかどうかを指定します。 このプロパティはブール値をとります。  
  
 このプロパティを TRUE に設定すると、XML 一括読み込みで挿入される値ごとに制約がチェックされ、制約違反があるとエラーが発生します。  
  
> [!NOTE]  
>  このプロパティを FALSE のままにして、する必要があります**ALTER TABLE**ターゲット テーブルに対する権限。 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
 既定値は FALSE です。 FALSE に設定した場合、XML 一括読み込みでは挿入操作中、制約が無視されます。 現在の実装では、マッピング スキーマの主キーと外部キーのリレーションシップの順序でテーブルを定義する必要があります。 つまり、主キーが設定されているテーブルは、外部キーが設定されている対応テーブルよりも前に定義する必要があります。このように定義しない場合、XML 一括読み込みは失敗します。  
  
 ID 配布が実行されている場合は、このオプションは適用されず、制約チェックはオンのままになる点に注意してください。 これに該当するのは、親が ID フィールドで、その値が生成時に子に指定されるリレーションシップが定義されており、かつ `KeepIdentity=False` の場合です。  
  
 ConnectionCommand  
 XML 一括読み込みする必要がありますを使用する既存の接続オブジェクト (たとえば、ADO または ICommand コマンド オブジェクト) を識別します。 ConnectionString プロパティを使用して接続文字列を指定する代わりに、ConnectionCommand プロパティを使用することができます。 ConnectionCommand を使用する場合、トランザクションのプロパティを TRUE に設定する必要があります。  
  
 ConnectionString および ConnectionCommand プロパティの両方を使用する場合、XML 一括読み込みは、最後の指定したプロパティを使用します。  
  
 既定値は NULL になります。  
  
 SubQueries  
 データベース インスタンスへの接続の確立に必要な情報を提供する OLE DB 接続文字列を指定します。 ConnectionString および ConnectionCommand プロパティの両方を使用する場合、XML 一括読み込みは、最後の指定したプロパティを使用します。  
  
 既定値は NULL になります。  
  
 ErrorLogFile  
 XML 一括読み込みでエラーとメッセージを記録するログ ファイル名を指定します。 既定値は空文字列で、この場合ログは記録されません。  
  
 FireTriggers  
 一括読み込み操作中に、対象テーブルに定義されているトリガーを起動するかどうかを指定します。 既定値は FALSE です。  
  
 TRUE に設定した場合は、挿入操作中、トリガーが通常どおり起動されます。  
  
> [!NOTE]  
>  このプロパティを FALSE のままにして、する必要があります**ALTER TABLE**ターゲット テーブルに対する権限。 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
 ID 配布が実行されている場合は、このオプションは適用されず、トリガーはオンのままになる点に注意してください。 これに該当するのは、親が ID フィールドで、その値が生成時に子に指定されるリレーションシップが定義されており、かつ `KeepIdentity=False` の場合です。  
  
 ForceTableLock  
 XML 一括読み込みでデータをコピーするテーブルを、一括読み込み中にロックするかどうかを指定します。 このプロパティはブール値をとります。 このプロパティを TRUE に設定すると、XML 一括読み込み中、テーブルはロックされます。 FALSE に設定すると、XML 一括読み込みでテーブルにレコードが挿入されるときに、毎回テーブルがロックされます。  
  
 既定値は FALSE です。  
  
 IgnoreDuplicateKeys  
 キー列に挿入される値が重複している場合の動作を指定します。 このプロパティが TRUE に設定されている状態で、キー列に挿入されるレコードの値が重複している場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではそのレコードは挿入されません。 しかし、その後に続くレコードは挿入されるので、一括読み込み操作は失敗しません。 このプロパティを FALSE に設定すると、キー列に挿入される値が重複している場合、一括読み込みは失敗します。  
  
 IgnoreDuplicateKeys プロパティが TRUE に設定されている場合、テーブルに挿入されるレコードごとに COMMIT ステートメントが発行されます。 このため、パフォーマンスが低下します。 プロパティは、のみとトランザクションのプロパティが FALSE に設定、ファイルを使用して、トランザクションの動作は実装されているために、TRUE に設定できます。  
  
 既定値は FALSE です。  
  
 KeepIdentity  
 ソース ファイルにある ID 型列値の取り扱い方法を指定します。 このプロパティはブール値をとります。 このプロパティを TRUE に設定すると、XML 一括読み込みでは、ソース ファイルで指定されている値が ID 列に割り当てられます。 このプロパティを FALSE に設定すると、一括読み込み操作では、ソースで指定されている ID 列値は無視されます。 この場合、ID 列値は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって割り当てられます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で生成される値が ID 列に格納される場合に、一括読み込みでこの列を参照する外部キー列も読み込まれる場合、一括読み込みではこれらの ID 値が外部キー列に適切に割り当てられます。  
  
 このプロパティの値は、一括読み込みの対象となるすべての列に適用されます。 既定値は TRUE です。  
  
> [!NOTE]  
>  このプロパティを TRUE のままにして、する必要があります**ALTER TABLE**ターゲット テーブルに対する権限。 この権限がない場合は、値を FALSE に設定する必要があります。 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
 KeepNulls  
 列に対応する属性または子要素が XML ドキュメントに見つからない場合に、その列に使用する値を指定します。 このプロパティはブール値をとります。 このプロパティを TRUE に設定すると、XML 一括読み込みでは列に NULL 値が割り当てられます。 サーバーで列の既定値が設定されている場合でも、その既定値は割り当てられません。 このプロパティの値は、一括読み込みの対象となるすべての列に適用されます。  
  
 既定値は FALSE です。  
  
 SchemaGen  
 一括読み込み操作の前に、必要なテーブルを作成するかどうかを指定します。 このプロパティはブール値をとります。 このプロパティを TRUE に設定すると、マッピング スキーマで指定されているテーブルが作成されます (データベースは存在している必要があります)。 1 つ以上のテーブルは、データベースに既に存在する場合、SGDropTables プロパティはこれらの既存のテーブルを削除して再作成するかどうかを判断します。  
  
 SchemaGen プロパティの既定値は FALSE です。 SchemaGen では、新しく作成されたテーブルの主キー制約は作成されません。 SchemaGen は、ただし、一致を検索できる場合、データベースに FOREIGN KEY 制約を作成、 **sql:relationship**と**sql:key-フィールド**マッピング スキーマで注釈とかどうかのキー フィールドには1 つの列です。  
  
 SchemaGen プロパティを TRUE に設定する場合は、XML 一括読み込みでは、次に注意してください。  
  
-   要素名と属性名から、必要なテーブルを作成します。 このため、スキーマでは要素と属性に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の予約語を使用しないでください。  
  
-   返します。 オーバーフロー データを使用して指定された任意の列を、 [sql:overflow-フィールド](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)で[xml データ型](../../../t-sql/xml/xml-transact-sql.md)形式です。  
  
 SGDropTables  
 既存のテーブルを削除し、再作成するかどうかを指定します。 SchemaGen プロパティが TRUE に設定されている場合は、このプロパティを使用します。 SGDropTables が FALSE の場合は、既存のテーブルは保持されます。 このプロパティが TRUE の場合、既存のテーブルは削除され再作成されます。  
  
 既定値は FALSE です。  
  
 SGUseID  
 指定するかどうか、マッピング スキーマで属性として識別された**id**型は、テーブルの作成時に PRIMARY KEY 制約の作成で使用できます。 SchemaGen プロパティが TRUE に設定されている場合は、このプロパティを使用します。 SchemaGen ユーティリティが、対象の属性を使用して SGUseID が TRUE の場合は、 **dt:type ="id"**が主キー列として指定され、テーブルを作成する際に、適切な主キー制約を追加します。  
  
 既定値は FALSE です。  
  
 TempFilePath  
 XML 一括読み込みで、読み込んだデータ用の一時ファイルを作成するファイル パスを指定します。 このプロパティは、Transaction プロパティを TRUE に設定した場合にのみ有用です。確認する必要があります、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML 一括読み込みに使用されるアカウントは、このパスにアクセスします。 このプロパティを設定しない場合、XML 一括読み込みでは、TEMP 環境変数で指定された場所に一時ファイルが格納されます。  
  
 トランザクション  
 一括読み込みをトランザクションとして実行するよう指定します。この場合、一括読み込みが失敗するとロールバックが実行されます。 このプロパティはブール値をとります。 このプロパティを TRUE に設定すると、一括読み込みはトランザクション コンテキストで実行されます。 TempFilePath プロパティは、トランザクションが TRUE に設定されている場合にのみ便利です。  
  
> [!NOTE]  
>  バイナリ データを読み込んでいる場合 (など、マップされる bin.hex、bin.base64 XML データ型を binary のイメージ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型)、トランザクションのプロパティを FALSE に設定する必要があります。  
  
 既定値は FALSE です。  
  
 XMLFragment  
 ソース データが XML フラグメントであるかどうかを指定します。 XML フラグメントとは、最上位 (ルート) 要素のない、単一の XML ドキュメントです。 このプロパティはブール値をとります。 ソース ファイルに XML フラグメントが含まれている場合は、このプロパティを TRUE に設定する必要があります。  
  
 既定値は FALSE です。  
  
  
