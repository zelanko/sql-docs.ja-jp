---
title: sp_tableoption (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tableoption_TSQL
- sp_tableoption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tableoption
ms.assetid: 0a57462c-1057-4c7d-bce3-852cc898341d
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 15c3c9716adefbb95d24c9528dce8607678998c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096059"
---
# <a name="sptableoption-transact-sql"></a>sp_tableoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  オプションのユーザー定義テーブルの値を設定します。 sp_tableoption は、のテーブルの行内での動作を制御するために使用できます**varchar (max)** 、 **nvarchar (max)** 、 **varbinary (max)** 、 **xml**、**テキスト**、 **ntext**、**イメージ**、または大きなユーザー定義型列。  
  
> [!IMPORTANT]  
>  text in row 機能は、将来のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では削除される予定です。 大きな値データを格納するをお勧めを使用すること、 **varchar (max)** 、 **nvarchar (max)** と**varbinary (max)** データ型。  
  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_tableoption [ @TableNamePattern = ] 'table'   
     , [ @OptionName = ] 'option_name'   
     ,[ @OptionValue =] 'value'  
```  
  
## <a name="arguments"></a>引数  
 [ @TableNamePattern =] '*テーブル*'  
 ユーザー定義のデータベース テーブルの修飾付きまたは修飾なしの名前です。 データベース名も含めてフル パスで指定した場合は、そのデータベース名は現在のデータベース名である必要があります。 同時には複数のテーブルのテーブル オプションを設定できません。 *テーブル*は**nvarchar (776)** 、既定値はありません。  
  
 [ @OptionName =] '*option_name*'  
 テーブル オプション名を指定します。 *option_name*は**varchar (35)** NULL の既定値はありません。 *option_name*値は次のいずれかを指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|一括読み込みでテーブル ロック|無効である場合 (既定)、ユーザー定義テーブル上で行ロックを取得するための一括読み込み処理が行われます。 有効な場合、一括更新ロックを取得するユーザー定義テーブルの一括読み込み処理が発生します。|  
|行ロックを挿入します。|サポートされていません。<br /><br /> このオプションはロックの動作に影響を与えません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既存のスクリプトおよびプロシージャの互換性のためだけに含まれています。|  
|行のテキスト|OFF または 0 (無効、既定値)、現在の動作は変更されませんし、行内 BLOB はありません。<br /><br /> 指定した場合と@OptionValueon (有効) または 24 ~ 7,000 の新しい整数値**テキスト**、 **ntext**、または**イメージ**文字列は、データ行に直接格納されます。 すべての既存の BLOB (バイナリ ラージ オブジェクト:**テキスト**、 **ntext**、または**イメージ**データ)、BLOB 値が更新されたときに、text in row 形式に変更されます。 詳細については、「解説」を参照してください。|  
|large value types out of row|1 = **varchar (max)** 、 **nvarchar (max)** 、 **varbinary (max)** 、 **xml**され、テーブル内の大きなユーザー定義型 (UDT) 列が格納されますルートに 16 バイトのポインターと共に、行の出力。<br /><br /> 0 = **varchar (max)** 、 **nvarchar (max)** 、 **varbinary (max)** 、 **xml**および大きな UDT 値は、上限に達するまで、データ行に直接格納されます8,000 バイトのと、レコードの値に収まる限りです。 値がレコードに収まらない場合には、ポインターが行内に格納され、残りは行外の LOB ストレージ領域に格納されます。 0 が既定値です。<br /><br /> 大きなユーザー定義型 (UDT) の適用対象: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 <br /><br /> TEXTIMAGE_ON オプションを使用して[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)ラージ データ型の記憶域の場所を指定します。 |  
|Vardecimal ストレージ形式|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> TRUE、ON、または 1 の場合、指定されたテーブルでは vardecimal ストレージ形式が有効です。 FALSE、OFF、または 0 と、テーブルは vardecimal ストレージ形式が無効です。 データベースは vardecimal ストレージ形式を使用して有効になっている場合にのみ、Vardecimal ストレージ形式を有効にすることができます[sp_db_vardecimal_storage_format](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)します。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、 **vardecimal**ストレージ形式が非推奨とされます。 代わりに行の圧縮を使用してください。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。 0 が既定値です。|  
  
 [ @OptionValue =] '*値*'  
 かどうか、 *option_name*が有効 (TRUE、ON、または 1) か無効 (FALSE、OFF、または 0)。 *値*は**varchar (12)** 、既定値はありません。 *値*は大文字と小文字が区別されません。  
  
 text in row オプションの有効値は、0、ON、OFF、または 24 ～ 7,000 の整数です。 ときに*値*は ON、制限の既定値は 256 バイトです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) またはエラーの数 (失敗)  
  
## <a name="remarks"></a>コメント  
 sp_tableoption は、ユーザー定義テーブルのオプション値を設定するためにのみ使用できます。 テーブル プロパティを表示するには、OBJECTPROPERTY を使用します。  
  
 sp_tableoption の text in row オプションを有効または無効にできるのは、テーブルにテキスト列が含まれている場合だけです。 テーブルには、テキスト列がない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーが発生します。  
  
 Text in row オプションが有効にすると、 @OptionValue BLOB の行に格納される最大サイズを指定するパラメーターを使用します。 既定値は 256 バイトですが、値の範囲は 24 ~ 7,000 バイト。  
  
 **テキスト**、 **ntext**、または**イメージ**文字列は、次の条件に該当する場合、データ行に格納されます。  
  
-   行内テキストが有効になっているとします。  
  
-   文字列の長さがで指定された制限よりも短い @OptionValue  
  
-   データ行に十分な使用可能領域がある。  
  
 読み取りと書き込みの BLOB 文字列は、データ行に格納されている、ときに、**テキスト**、 **ntext**、または**イメージ**ほど高速の読み取りまたは書き込みの文字やバイナリ文字列で文字列を指定できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 読み取りまたは書き込みの BLOB 文字列を別のページにアクセスすることはありません。  
  
 場合、**テキスト**、 **ntext**、または**イメージ**文字列が指定された制限または行で使用可能な領域を超える、ポインターが代わりの行に格納されます。 それでも、行に BLOB 文字列を格納するための条件が適用されます。ポインターを格納するデータ行に十分な領域が必要があります。  
  
 BLOB 文字列やテーブルの行に格納されているポインターが可変長の文字列に同様に扱われます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文字列またはポインターを格納するために必要なバイト数のみを使用します。  
  
 行のテキストを有効にするとすぐに、既存の BLOB 文字列は変換されません。 文字列は、それらが更新されたときに初めて変換されます。 同様に、ときにテキストが in row オプションの制限値を増やすと、**テキスト**、 **ntext**、または**イメージ**新しい制限に準拠するデータ行には既に文字列は変換されません時間まで更新されます。  
  
> [!NOTE]  
>  text in row オプションを無効にする、またはオプションの制限値を小さくした場合は、BLOB を変換する必要があります。したがって、変換される BLOB 文字列の数によっては、処理に時間がかかる場合があります。 テーブルは、変換処理中にロックされています。  
  
 テーブル変数を返す関数を含む、テーブル変数は、in row オプションが 256 のインライン上限の既定値で有効になっているテキストを自動的に持ちます。 このオプションを変更することはできません。  
  
 Text in row オプションは、TEXTPTR、WRITETEXT、UPDATETEXT、および READTEXT 関数をサポートします。 ユーザーは、パーツの SUBSTRING() 関数を使用して BLOB を読み取ることができますが、行内テキスト ポインターが別の期間およびその他のテキスト ポインターからの数の制限があることを忘れないでください。  
  
 テーブルを vardecimal ストレージ形式から通常の decimal ストレージ形式に戻すには、データベースを単純復旧モードにする必要があります。 復旧モードを変更すると、バックアップに必要なログ チェーンが途切れてしまいます。したがって、テーブルから vardecimal ストレージ形式を削除した後で、データベースの完全バックアップを作成する必要があります。  
  
 既存の LOB データ型列 (text、ntext、または image) を小さな規模の大きな値の型 (varchar (max)、nvarchar (max)、または varbinary(max))、およびほとんどのステートメントはいない環境内で大きな値型の列の参照を検討してくださいに変換する場合変更する**large_value_types_out_of_row**に**1**最適なパフォーマンスを向上させます。 ときに、 **large_value_types_out_of_row**オプションの値を変更すると、既存の varchar (max)、nvarchar (max)、varbinary (max)、および xml 値はすぐに変換されません。 文字列のストレージは、後で文字列が更新されたときに変更されます。 テーブルに挿入される新しい値は、有効なテーブル オプションに従って格納されます。 即時の結果を得るには、いずれか、データのコピーを作成しを変更した後、テーブルを再作成し、 **large_value_types_out_of_row**設定またはそれ自体に各小規模から中に値型の列を更新できるようにの記憶域、文字列が有効なテーブル オプションを使用して変更されます。 更新または再作成の後でテーブルのインデックスを再構築し、テーブルを圧縮することを検討します。 
    
  
## <a name="permissions"></a>アクセス許可  
 Sp_tableoption を実行するには、テーブルに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-storing-xml-data-out-of-the-row"></a>A. XML データの行外への格納  
 次の例では、ことを指定します、 **xml**内のデータ、`HumanResources.JobCandidate`テーブル行外に格納します。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'HumanResources.JobCandidate', 'large value types out of row', 1;  
```  
  
### <a name="b-enabling-vardecimal-storage-format-on-a-table"></a>B. テーブルで vardecimal ストレージ形式を有効にします。  
 次の例では、変更、`Production.WorkOrderRouting`を格納するテーブル、`decimal`のデータ型の`vardecimal`ストレージ形式です。  

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
  
## <a name="see-also"></a>関連項目  
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
