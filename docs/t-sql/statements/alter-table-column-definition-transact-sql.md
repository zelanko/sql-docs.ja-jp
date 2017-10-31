---
title: "column_definition (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_definition
- column_definition_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column_definition
- ALTER TABLE statement
- column properties [SQL Server]
- column definitions [SQL Server]
ms.assetid: a1742649-ca29-4d9b-9975-661cdbf18f78
caps.latest.revision: 78
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c63dcea3473198ded46ebf84053fa9d8b36330f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-table-columndefinition-transact-sql"></a>ALTER TABLE column_definition (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  使用してテーブルに追加される列のプロパティを指定[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
column_name <data_type>  
[ FILESTREAM ]  
[ COLLATE collation_name ]   
[ NULL | NOT NULL ]  
[   
    [ CONSTRAINT constraint_name ] DEFAULT constant_expression [ WITH VALUES ]   
    | IDENTITY [ ( seed , increment ) ] [ NOT FOR REPLICATION ]   
]  
[ ROWGUIDCOL ]   
[ SPARSE ]   
[ ENCRYPTED WITH  
  ( COLUMN_ENCRYPTION_KEY = key_name ,  
      ENCRYPTION_TYPE = { DETERMINISTIC | RANDOMIZED } ,   
      ALGORITHM =  'AEAD_AES_256_CBC_HMAC_SHA_256'   
  ) ]  
[ MASKED WITH ( FUNCTION = ' mask_function ') ]  
[ <column_constraint> [ ...n ] ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
        [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
[ CONSTRAINT constraint_name ]   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH FILLFACTOR = fillfactor    
          | WITH ( < index_option > [ , ...n ] )   
        ]   
        [ ON { partition_scheme_name ( partition_column_name )   
            | filegroup | "default" } ]  
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
  | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
}  
```  
  
## <a name="arguments"></a>引数  
 *column_name*  
 変更、追加、または削除する列の名前を指定します。 *column_name* 1 ~ 128 文字で構成できます。 新しい列の場合、timestamp データ型で作成された*column_name*を省略できます。 ない場合は*column_name*が指定されて、**タイムスタンプ**データ型の列、名前**タイムスタンプ**を使用します。  
  
 [ *type_schema_name***です。** *type_name*  
 追加する列のデータ型と、それが属するスキーマを指定します。  
  
 *type_name*を指定できます。  
  
-   A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型。  
  
-   別名データ型に基づいて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型。 このデータ型をテーブル定義で使用するには、先に CREATE TYPE を使って作成しておく必要があります。  
  
-   A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]ユーザー定義型とそれが属するスキーマ。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ユーザー定義型をテーブル定義で使用するには、先に CREATE TYPE を使って作成しておく必要があります。  
  
 場合*type_schema_name*が指定されていない、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]参照*type_name*次の順序で。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データ型  
  
-   現在のデータベースにおける現在のユーザーの既定のスキーマ  
  
-   現在のデータベースの **dbo** スキーマ。  
  
*有効桁数 (precision)*  
 指定されるデータ型の有効桁数です。 有効桁数値の詳細については、次を参照してください[有効桁数、小数点以下桁数、および長さ &#40;。TRANSACT-SQL と #41 です。](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
*scale*  
 指定されるデータ型の小数点以下桁数です。 有効な小数点以下桁数値の詳細については、次を参照してください[有効桁数、小数点以下桁数、および長さ &#40;。TRANSACT-SQL と #41 です。](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
**max**  
 のみ適用され、 **varchar**、 **nvarchar**、および**varbinary**データ型。 これらは 2^31 バイトの文字とバイナリ データ、および 2^30 バイトの Unicode データを格納するときに使用されます。  
  
**コンテンツ**  
 指定の各インスタンス、 **xml**のデータ型の*column_name*複数のトップレベル要素を含めることができます。 コンテンツにのみ適用、 **xml**データ型し、する場合にのみ指定できます*xml_schema_collection*も指定されています。 指定しない場合は、CONTENT が既定の動作になります。  
  
DOCUMENT  
 指定の各インスタンス、 **xml**のデータ型の*column_name* 1 つだけの最上位要素を含めることができます。 ドキュメントにのみ適用、 **xml**データ型し、する場合にのみ指定できます*xml_schema_collection*も指定されています。  
  
 *xml_schema_collection*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 のみ適用され、 **xml**型と XML スキーマ コレクションの関連付けのデータ型。 入力する前に、 **xml**列をスキーマ、スキーマ必要があります最初に作成するデータベースを使用して[CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)です。  
  
FILESTREAM  
 必要に応じて列に対して FILESTREAM ストレージ属性を指定します、 *type_name*の**varbinary (max)**です。  
  
 列がテーブルである必要がありますも列に対して FILESTREAM を指定すると、 **uniqueidentifier** ROWGUIDCOL 属性を持つデータ型です。 この列では、null 値は許可されず、UNIQUE または PRIMARY KEY 単一列制約を持つ必要があります。 データが挿入されるときにアプリケーションまたは NEWID () 関数を使用する既定の制約のいずれか、列の GUID 値を指定する必要があります。  
  
 テーブルに FILESTREAM 列が定義されているときは、ROWGUIDCOL 列を削除したり関連する制約を変更したりすることはできません。 ROWGUIDCOL 列は、最後の FILESTREAM 列が削除された後でのみ削除できます。  
  
 列に対して FILESTREAM ストレージ属性を指定した場合、この列のすべての値がファイル システム上の FILESTREAM データ コンテナーに格納されます。  
  
 列の定義を使用する方法を示す例を次を参照してください。 [FILESTREAM & #40 です。SQL Server &#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
COLLATE *collation_name*  
 列の照合順序を指定します。 照合順序を指定しない場合、データベースの既定の照合順序が列に割り当てられます。 照合順序名には、Windows 照合順序名または SQL 照合順序名のいずれかを指定できます。 一覧および詳細については、次を参照してください。 [Windows 照合順序名 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/windows-collation-name-transact-sql.md)と[SQL Server 照合順序名 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 COLLATE 句は、のみの列の照合順序を指定するために使用できます、 **char**、 **varchar**、 **nchar**、および**nvarchar**データ型.  
  
 COLLATE 句の詳細については、次を参照してください。 [COLLATE & #40 です。TRANSACT-SQL と #41 です。](~/t-sql/statements/collations.md).  
  
 NULL | NOT NULL  
 列で NULL 値を許すかどうかを示します。 NULL は厳密には制約ではありませんが、NOT NULL と同じように指定することができます。  
  
[制約*constraint_name* ]  
 DEFAULT 値の定義の開始を指定します。 旧バージョンとの互換性を維持する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]制約の名前は、既定値に割り当てることができます。 *constraint_name*の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md),、名前に番号記号を開始できません点が異なります (#)。 場合*constraint_name*が指定されていない、システムによって生成された名前が、DEFAULT 定義に割り当てられます。  
  
DEFAULT  
 列の既定値を指定するキーワードです。 DEFAULT 定義を使用すると、既存のデータ行に新しい列の値を設定できます。 既定の定義に適用できません**タイムスタンプ**列、または IDENTITY プロパティを持つ列。 型から暗黙的な変換をサポートする必要がある場合は、ユーザー定義型列の既定値を指定すると、 *constant_expression*ユーザー定義型です。  
  
*constant_expression*  
 リテラル値、NULL 値、または列の既定値として使用されるシステム関数です。 定義されている列と組み合わせて使用する場合、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]ユーザー定義型、型の実装はから暗黙的な変換をサポートする必要があります、 *constant_expression*ユーザー定義型です。  
  
WITH VALUES  
 既定の指定された値を指定する*constant_expression*は既存の行に追加された新しい列に格納します。 追加される列で NULL 値が許容される場合、WITH VALUES を指定すると、既存の行に追加される新しい列には既定値が格納されます。 NULL 値が許容される列に対して WITH VALUES を指定しない場合は、既存の行の新しい列には NULL 値が格納されます。 新しい列で NULL 値が許容されない場合は、WITH VALUES の指定に関係なく、新しい行に既定値が格納されます。  
  
IDENTITY  
 新しい列が id 列であることを指定します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]列の一意な増分値を提供します。 既存のテーブルに ID 列を追加すると、テーブルの既存の行にシード値と増分値を持つ識別番号が追加されます。 行の更新順序は保証されません。 識別番号は、新しく追加された行に対しても生成されます。  
  
 ID 列は通常、PRIMARY KEY 制約と組み合わせて使用し、テーブルの一意な行識別子 (ROWID) の役割を果たします。 ID プロパティに割り当てることができます、 **tinyint**、 **smallint**、 **int**、 **bigint**、 **decimal(p,0)**、または**numeric(p,0)**列です。 ID 列は 1 つのテーブルにつき 1 つだけ作成できます。 DEFAULT キーワードとバインドされている既定値は、ID 列で使用できません。 seed と increment は両方指定するか、どちらも指定しないでください。 どちらも指定しない場合、既定値は (1,1) になります。  
  
> [!NOTE]  
>  既存のテーブル列を変更して IDENTITY プロパティを追加することはできません。  
  
 パブリッシュされたテーブルへの ID 列の追加はサポートされていません。これは、列をサブスクライバーにレプリケートするときに集約できなくなる可能性があるためです。 パブリッシャーの ID 列の値は、影響を受けるテーブルの行が物理的に格納されている順序に依存します。 サブスクライバー側では行は別の方法で格納される場合があるため、ID 列の値は同じ行で異なる可能性があります。  
  
 明示的に挿入する値を許可することで、列の IDENTITY プロパティを無効にする[SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md)です。  
  
*シード*  
 テーブルに読み込まれる先頭行で使用される値を指定します。  
  
*増分値*  
 読み込まれている前の行の ID 値に加算される増分値を指定します。  
  
NOT FOR REPLICATION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 IDENTITY プロパティに対して指定できます。 IDENTITY プロパティに対してこの句を指定した場合、レプリケーション エージェントが挿入操作を実行するとき ID 列の値は増加しません。  
  
ROWGUIDCOL  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 列が、行グローバル一意識別子列であることを指定します。 ROWGUIDCOL にのみ割り当てることができます、 **uniqueidentifier**列、および 1 つだけ**uniqueidentifier** ROWGUIDCOL 列として 1 つのテーブルの列を指定することができます。 ROWGUIDCOL は、ユーザー定義データ型の列には割り当てできません。  
  
 ROWGUIDCOL では、列に格納される値の一意性は設定されません。 また、テーブルに新しい行を挿入しても値は自動的に生成されません。 各列に一意な値を生成するには、INSERT ステートメントで NEWID 関数を使用するか、列の既定値として NEWID 関数を指定します。 詳細については、次を参照してください。 [NEWID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/newid-transact-sql.md)と[INSERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/insert-transact-sql.md).  
  
SPARSE  
 列がスパース列であることを示します。 スパース列のストレージは NULL 値用に最適化されます。 スパース列を NOT NULL として指定することはできません。 追加の制限とスパース列の詳細については、次を参照してください。[スパース列を使用する](../../relational-databases/tables/use-sparse-columns.md)です。  
  
\<column_constraint >  
 列の制約の引数の定義を参照してください。 [column_constraint & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-column-constraint-transact-sql.md).  
  
 使用して暗号化  
 使用して暗号化列を指定します、 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)機能します。  
  
 COLUMN_ENCRYPTION_KEY = *key_name*  
 列の暗号化キーを指定します。 詳細については、次を参照してください。 [CREATE COLUMN ENCRYPTION KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-column-encryption-key-transact-sql.md).  
  
ENCRYPTION_TYPE = {決定的 |ランダム化}  
 **確定的な暗号化** は常に任意のプレーン テキストを指定した値の場合は、同じ暗号化された値を生成するメソッドを使用します。 確定的な暗号化を使用すると、グループ化、および暗号化された値に基づいて、等しいかどうかの結合を使用して、テーブルへの参加の等値比較を使用して検索をできますも確認するには、暗号化された列のパターンについては、暗号化された値を推測する承認されていないユーザーを許可することができます。 確定的に暗号化された列に 2 つのテーブルを結合すると、両方の列が同じ列の暗号化キーを使用して暗号化されている場合にのみ可能なです。 明確な暗号化では、バイナリ 2 文字型の列の並べ替え順序を持つ列の照合順序を使用する必要があります。  
  
 **暗号化をランダム化** は低い予測可能な方法でデータを暗号化するためのメソッドを使用します。 ランダムな暗号化より安全になりますが、により、等しいかどうかの検索、グループ化、および暗号化された列を結合します。 ランダムな暗号化を使用して列のインデックスを付けることはできません。  
  
 検索パラメーターまたは政府の ID 番号など、グループ化のパラメーターとなる列には、確定的な暗号化を使用します。 ランダムな暗号化を使用して、クレジット カード番号などのデータ、これが、他のレコードとグループ化されたかテーブル、およびこれは検索されませんの (トランザクションの数) などの他の列を使用して、関心のある暗号化された列を含む行を検索するために参加するために使用します。  
  
 列は、該当するデータ型である必要があります。  
  
アルゴリズム  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
必要があります**'AEAD_AES_256_CBC_HMAC_SHA_256'**です。  
  
 機能の制約を含むの詳細については、次を参照してください。 [Always Encrypted & #40";"データベース エンジン"&"#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)です。  
  
   
追加マスクで (関数 = ' *mask_function* ')  
 **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 動的なデータのマスクを指定します。 *mask_function*適切なパラメーターを使用してマスク関数の名前を指定します。 次の関数を使用できます。  
  
-   default()  
  
-   email()  
  
-   partial()  
  
-   random()  
  
 関数パラメーターの場合は、次を参照してください。[動的データ マスク](../../relational-databases/security/dynamic-data-masking.md)です。  
  
## <a name="remarks"></a>解説  
 持つ列が追加された場合、 **uniqueidentifier**データ型を定義することで、既定値を NEWID() 関数を使用して、テーブル内の既存の各行の新しい列で一意の識別子の値を指定します。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]列定義の既定、IDENTITY、ROWGUIDCOL または列制約を指定するための順序は強制されません。  
  
 列の追加によりデータ行のサイズが 8,060 バイトを超える場合、ALTER TABLE ステートメントは失敗します。  
  
## <a name="examples"></a>使用例  
 例については、次を参照してください。 [ALTER TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  

