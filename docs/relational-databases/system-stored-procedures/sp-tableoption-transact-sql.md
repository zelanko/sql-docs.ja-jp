---
title: sp_tableoption (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_tableoption_TSQL
- sp_tableoption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tableoption
ms.assetid: 0a57462c-1057-4c7d-bce3-852cc898341d
caps.latest.revision: 60
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 33027f15081102cca289923b858a4a960a1359e4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sptableoption-transact-sql"></a>sp_tableoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ユーザー定義テーブルのオプション値を設定します。 sp_tableoption を使用して、含むテーブルの行の動作を制御できます**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**、**テキスト**、 **ntext**、**イメージ**、または大きなユーザー定義型列です。  
  
> [!IMPORTANT]  
>  text in row 機能は、将来のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では削除される予定です。 大きな値のデータを格納することをお勧めを使用すること、 **varchar (max)**、 **nvarchar (max)** と**varbinary (max)** データ型。  
  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_tableoption [ @TableNamePattern = ] 'table'   
     , [ @OptionName = ] 'option_name'   
     ,[ @OptionValue =] 'value'  
```  
  
## <a name="arguments"></a>引数  
 [ @TableNamePattern =] '*テーブル*'  
 ユーザー定義データベース テーブルの修飾名または修飾されていない名前を指定します。 データベース名も含めてフル パスで指定した場合は、そのデータベース名は現在のデータベース名である必要があります。 複数のテーブルにはテーブル オプションを同時に設定できません。 *テーブル*は**nvarchar (776)**、既定値はありません。  
  
 [ @OptionName =] '*option_name*'  
 テーブル オプション名を指定します。 *option_name*は**varchar (35)** NULL の既定値はありません。 *option_name*値は次のいずれかになります。  
  
|値|Description|  
|-----------|-----------------|  
|table lock on bulk load|無効である場合 (既定)、ユーザー定義テーブル上で行ロックを取得するための一括読み込み処理が行われます。 有効である場合、ユーザー定義テーブル上で一括更新ロックを取得するための一括読み込み処理が行われます。|  
|insert row lock|サポートされていません。<br /><br /> このオプションはロックの動作に影響を与えません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と既存のスクリプトおよびプロシージャの互換性のためだけに用意されています。|  
|text in row|OFF または 0 (無効、つまり既定値) である場合は、現在の動作を変更せず、行内 BLOB はありません。<br /><br /> 指定した場合と@OptionValueon (有効) または 24 ~ 7,000、新しい整数値**テキスト**、 **ntext**、または**イメージ**文字列は、データ行に直接格納します。 すべての既存の BLOB (バイナリ ラージ オブジェクト:**テキスト**、 **ntext**、または**イメージ**データ)、BLOB 値が更新されたときに、text in row 形式に変更されます。 詳細については、「解説」を参照してください。|  
|large value types out of row|1 = **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**テーブル内の大きなユーザー定義型 (UDT) 列が格納されますルートに 16 バイトのポインターと共に、行はタイムアウトします。<br /><br /> 0 = **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**大きな UDT 値は、上限に達するまで、データ行に直接格納および8,000 バイトのと、値がレコードに収まる限りです。 値がレコードに収まらない場合には、ポインターが行内に格納され、残りは行外の LOB ストレージ領域に格納されます。 0 が既定値です。<br /><br /> 大きなユーザー定義型 (UDT) の適用対象: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 <br /><br /> TEXTIMAGE_ON のオプションを使用[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)ラージ データ型の記憶域の場所を指定します。 |  
|Vardecimal ストレージ形式|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> TRUE、ON、または 1 の場合、指定されたテーブルでは vardecimal ストレージ形式が有効です。 FALSE、OFF、または 0 の場合、そのテーブルでは vardecimal ストレージ形式が無効です。 データベースは vardecimal ストレージ形式を使用して有効になってが場合にのみ、Vardecimal ストレージ形式を有効にすることができます[sp_db_vardecimal_storage_format](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)です。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、 **vardecimal**ストレージ形式は推奨されなくなりました。 代わりに行の圧縮を使用してください。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。 0 が既定値です。|  
  
 [ @OptionValue =] '*値*'  
 かどうか、 *option_name*が有効 (TRUE、ON、または 1) か無効 (FALSE、OFF、または 0) です。 *値*は**varchar (12)**、既定値はありません。 *値*は大文字小文字を区別します。  
  
 text in row オプションの有効値は、0、ON、OFF、または 24 ～ 7,000 の整数です。 ときに*値*は ON、制限の既定値は 256 バイトです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を、失敗した場合はエラー番号をそれぞれ返します。  
  
## <a name="remarks"></a>解説  
 sp_tableoption は、ユーザー定義テーブルのオプション値を設定するためにのみ使用できます。 テーブル プロパティを表示するには、OBJECTPROPERTY を使用します。  
  
 sp_tableoption の text in row オプションを有効または無効にできるのは、テーブルにテキスト列が含まれている場合だけです。 テーブルには、テキスト列がない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でエラーが発生します。  
  
 Text in row オプションが有効にすると、 @OptionValue BLOB の行に格納される最大サイズを指定するパラメーターを使用します。 既定値は 256 バイトですが、24 ～ 7,000 バイトの値を指定できます。  
  
 **テキスト**、 **ntext**、または**イメージ**文字列は、次の条件に該当する場合、データ行に格納されます。  
  
-   text in row オプションが有効。  
  
-   文字列の長さがで指定された制限よりも短い @OptionValue  
  
-   データ行に十分な使用可能領域がある。  
  
 読み取りと書き込みの BLOB 文字列は、データ行に格納されている、ときに、**テキスト**、 **ntext**、または**イメージ**文字列を読み取りまたは書き込みの文字やバイナリ文字列と同じ速度で指定できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 読み取りまたは書き込みの BLOB 文字列を別のページにアクセスすることはありません。  
  
 場合、**テキスト**、 **ntext**、または**イメージ**文字列は、指定された制限または行で使用可能な領域を超える、ポインターが代わりに、行に格納します。 ただし、BLOB 文字列を行に格納する場合の条件は引き続き適用されます。ただし、データ行にはポインターを格納するのに十分な領域が必要です。  
  
 テーブル内の行に格納されている BLOB 文字列やポインターは、可変長文字列と同じように扱われます [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文字列またはポインターを格納するために必要なバイト数のみを使用します。  
  
 既存の BLOB 文字列は、text in row を有効にしても、直ちに変換されるわけではありません。 文字列は、それらが更新されたときに初めて変換されます。 同様に、いつ row オプションの制限内のテキストは大きくしても、**テキスト**、 **ntext**、または**イメージ**データ行には既に文字列は、新しい制限値に変換できません更新されるまでです。  
  
> [!NOTE]  
>  text in row オプションを無効にする、またはオプションの制限値を小さくした場合は、BLOB を変換する必要があります。したがって、変換される BLOB 文字列の数によっては、処理に時間がかかる場合があります。 変換処理中は、テーブルがロックされます。  
  
 テーブル変数を返す関数を含め、テーブル変数では、text in row オプションが、インラインの上限の既定値である 256 で自動的に有効になります。 このオプションは変更できません。  
  
 Text in row オプションは、TEXTPTR、WRITETEXT、UPDATETEXT、および READTEXT 関数をサポートしています。 ユーザーは、SUBSTRING() 関数を使用して BLOB の複数の部分を読み取ることができますが、行内テキスト ポインターの実行期間および数の制限値は、その他のテキスト ポインターとは異なることに注意する必要があります。  
  
 テーブルを vardecimal ストレージ形式から通常の decimal ストレージ形式に戻すには、データベースを単純復旧モードにする必要があります。 復旧モードを変更すると、バックアップに必要なログ チェーンが途切れてしまいます。したがって、テーブルから vardecimal ストレージ形式を削除した後で、データベースの完全バックアップを作成する必要があります。  
  
 変更する場合は既存の LOB データ型列 (text、ntext、または image) 小 ~ 中程度の大きな値型 (varchar (max)、nvarchar (max)、または varbinary(max))、およびほとんどのステートメントがない環境内で大きな値型の列の参照を検討してください。変更する**large_value_types_out_of_row**に**1**最適なパフォーマンスを確保します。 ときに、 **large_value_types_out_of_row**オプションの値を変更すると、既存の varchar (max)、nvarchar (max)、varbinary (max)、および xml 値はすぐに変換されません。 文字列のストレージは、後で文字列が更新されたときに変更されます。 テーブルに挿入される新しい値は、有効なテーブル オプションに従って格納されます。 即時の結果を得るには、いずれかのデータのコピーを作成し、再作成し、テーブルを変更した後、 **large_value_types_out_of_row**設定またはそれ自体に各小規模から中に大きな値型の列を更新できるようにの記憶域、文字列は有効でテーブル オプションを使用して変更されます。 更新または再作成の後でテーブルのインデックスを再構築し、テーブルを圧縮することを検討します。 
    
  
## <a name="permissions"></a>権限  
 sp_tableoption を実行するには、テーブルに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-storing-xml-data-out-of-the-row"></a>A. XML データの行外への格納  
 次の例を指定する、 **xml**内のデータ、`HumanResources.JobCandidate`行外のテーブルに格納します。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'HumanResources.JobCandidate', 'large value types out of row', 1;  
```  
  
### <a name="b-enabling-vardecimal-storage-format-on-a-table"></a>B. テーブルでの vardecimal ストレージ形式の有効化  
 次の例を変更、`Production.WorkOrderRouting`を格納するテーブル、`decimal`のデータ型の`vardecimal`ストレージ形式です。  

```sql  
USE master;  
GO  
-- The database must be enabled for vardecimal storage format  
-- before a table can be enabled for vardecimal storage format  
EXEC sp_db_vardecimal_storage_format 'AdventureWorks2012', 'ON';  
GO  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'Production.WorkOrderRouting',   
   'vardecimal storage format', 'ON';  
```  
  
## <a name="see-also"></a>参照  
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
