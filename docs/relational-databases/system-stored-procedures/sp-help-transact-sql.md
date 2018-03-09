---
title: "sp_help (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help
- sp_help_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help
ms.assetid: 913cd5d4-39a3-4a4b-a926-75ed32878884
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4df2325ef2da29b60ca4f1e7109dd73ff9530ea2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelp-transact-sql"></a>sp_help (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース オブジェクトに関する情報をレポート (任意のオブジェクトに一覧表示、 **sys.sysobjects**互換性ビュー)、ユーザー定義データ型、またはデータ型。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help [ [ @objname = ] 'name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@objname=**] **'***名前***'**  
 任意のオブジェクトの名前が、 **sysobjects**にすべてのユーザー定義データを入力または、 **systypes**テーブル。 *名前*は**nvarchar (**776**)**、既定値は NULL です。 データベース名は入力できません。  'Person.AddressType'、または [Person.AddressType] など、2 つまたは 3 つの部分名を区切る必要があります。   
   
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 返される結果セットが異なるかどうか*名前*を指定した場合とはどのようなデータベース オブジェクトを指定します。  
  
1.  場合**sp_help**が実行される引数なしで、現在のデータベース内に存在するすべての型のオブジェクトの概要情報が返されます。  
  
    |列名|データ型|Description|  
    |-----------------|---------------|-----------------|  
    |**名前**|**nvarchar (**128**)**|オブジェクト名です。|  
    |**[所有者]**|**nvarchar (**128**)**|オブジェクトの所有者です (これは、オブジェクトを所有するデータベース プリンシパルです。 既定値は、オブジェクトを含むスキーマの所有者です)。|  
    |**Object_type**|**nvarchar (**31**)**|オブジェクトの種類|  
  
2.  場合*名前*は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型またはユーザー定義データ型、 **sp_help**この結果セットを返します。  
  
    |列名|データ型|Description|  
    |-----------------|---------------|-----------------|  
    |**Type_name**|**nvarchar (**128**)**|データ型の名前です。|  
    |**Storage_type**|**nvarchar (**128**)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型名。|  
    |**[データ型]**|**smallint**|データ型の物理バイト数です。|  
    |**Prec**|**int**|有効桁数 (総桁数) です。|  
    |**[スケール]**|**int**|小数点の右側にある数字の数。|  
    |**NULL 値の使用**|**varchar (**35**)**|NULL 値を許すかどうかを示します。この値は Yes または No です。|  
    |**Default_name**|**nvarchar (**128**)**|このデータ型にバインドされた既定値の名前です。<br /><br /> NULL = 既定値がバインドされていません。|  
    |**Rule_name**|**nvarchar (**128**)**|このデータ型にバインドされたルールの名前です。<br /><br /> NULL = 既定値がバインドされていません。|  
    |**照合順序**|**sysname**|データ型の照合順序です。 データ型が文字型以外の場合は、NULL です。|  
  
3.  場合*名前*以外のデータ型では、データベース オブジェクトである**sp_help**設定でも追加の結果セットを指定したオブジェクトの型に基づくこの結果を返します。  
  
    |列名|データ型|Description|  
    |-----------------|---------------|-----------------|  
    |**名前**|**nvarchar (**128**)**|テーブル名|  
    |**[所有者]**|**nvarchar (**128**)**|テーブルの所有者|  
    |**型**|**nvarchar (**31**)**|テーブルの種類です。|  
    |**Created_datetime**|**datetime**|テーブルの作成日です。|  
  
     指定すると、データベース オブジェクトによって**sp_help**の結果セットを返します。  
  
     場合*名前*がシステム テーブル、ユーザー テーブルまたはビュー、 **sp_help**次の結果セットを返します。 ただし、ビューに対しては、データ ファイルがファイル グループ内のどこに配置されているかを表す結果セットは返されません。  
  
    -   列オブジェクトに関して次の結果セットが返されます。  
  
        |列名|データ型|Description|  
        |-----------------|---------------|-----------------|  
        |**Column_name**|**nvarchar (**128**)**|列名|  
        |**型**|**nvarchar (**128**)**|列のデータ型です。|  
        |**計算**|**varchar (**35**)**|計算列かどうかを示します。この値は Yes または No です。|  
        |**[データ型]**|**int**|列のバイト数です。<br /><br /> 注: 列のデータ型が大きな値の型 (**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**)、値は-1 として表示されます。|  
        |**Prec**|**char (**5**)**|列の有効桁数です。|  
        |**[スケール]**|**char (**5**)**|列の小数点以下桁数です。|  
        |**NULL 値の使用**|**varchar (**35**)**|列内で NULL 値を許すかどうかを示します。この値は Yes または No です。|  
        |**TrimTrailingBlanks**|**varchar (**35**)**|後続の空白を切り捨てます。 Yes または No を返します。|  
        |**FixedLenNullInSource**|**varchar (**35**)**|これは旧バージョンとの互換性のためにだけ用意されています。|  
        |**照合順序**|**sysname**|列の照合順序です。 文字型以外の場合は NULL です。|  
  
    -   ID 列に関して次の結果セットが返されます。  
  
        |列名|データ型|Description|  
        |-----------------|---------------|-----------------|  
        |**Identity**|**nvarchar (**128**)**|ID として宣言されている列名です。|  
        |**シード**|**numeric**|ID 列の開始値です。|  
        |**Increment**|**numeric**|この列の値に対して使用する増分です。|  
        |**[レプリケーションでは使用しない]**|**int**|IDENTITY プロパティは、レプリケーションのログイン時に適用されませんなど**sqlrepl**テーブルにデータを挿入します。<br /><br /> 1 = True<br /><br /> 0 = False|  
  
    -   列に関して次の結果セットが返されます。  
  
        |列名|データ型|Description|  
        |-----------------|---------------|-----------------|  
        |**RowGuidCol**|**sysname**|一意なグローバル識別子列の名前です。|  
  
    -   ファイル グループに関して次の結果セットが返されます。  
  
        |列名|データ型|Description|  
        |-----------------|---------------|-----------------|  
        |**Data_located_on_filegroup**|**nvarchar (**128**)**|データが属いるファイルグループ (プライマリ、セカンダリ、またはトランザクション ログ)。|  
  
    -   インデックスに関して次の結果セットが返されます。  
  
        |列名|データ型|Description|  
        |-----------------|---------------|-----------------|  
        |**index_name**|**sysname**|インデックスの名前。|  
        |**Index_description**|**varchar (**210**)**|インデックスの説明です。|  
        |**index_keys**|**nvarchar (**2078**)**|インデックス作成対象の列名です。 xVelocity メモリ最適化列ストア インデックスに対して NULL を返します。|  
  
    -   制約に関して次の結果セットが返されます。  
  
        |列名|データ型|Description|  
        |-----------------|---------------|-----------------|  
        |**constraint_type**|**nvarchar (**146**)**|制約の種類です。|  
        |**constraint_name**|**nvarchar (**128**)**|制約の名前です。|  
        |**delete_action**|**nvarchar (**9**)**|DELETE 操作が NO_ACTION、CASCADE、SET_NULL、SET_DEFAULT、該当なし、のどれであるかを示します。<br /><br /> ただし、FOREIGN KEY 制約にだけ適用されます。|  
        |**update_action**|**nvarchar (**9**)**|UPDATE 操作が、NO_ACTION、CASCADE、SET_NULL、SET_DEFAULT、N/A のどれであるかを示します。<br /><br /> ただし、FOREIGN KEY 制約にだけ適用されます。|  
        |**status_enabled**|**varchar (**8**)**|制約が有効であるかどうかを示します。この値は Enabled、Disabled、N/A のいずれかです。<br /><br /> ただし、CHECK および FOREIGN KEY 制約にだけ適用されます。|  
        |**status_for_replication**|**varchar (**19**)**|制約がレプリケーションを対象とするのかどうかを示します。<br /><br /> ただし、CHECK および FOREIGN KEY 制約にだけ適用されます。|  
        |**constraint_keys**|**nvarchar (**2078**)**|制約を構成する列の名前です。デフォルトおよびルールの場合は、デフォルトまたはルールを定義するテキストです。|  
  
    -   参照元のオブジェクトに関して次の結果セットが返されます。  
  
        |列名|データ型|Description|  
        |-----------------|---------------|-----------------|  
        |**によって参照されるテーブル**|**nvarchar (**516**)**|テーブルを参照するその他のデータベース オブジェクトを示します。|  
  
    -   ストアド プロシージャ、関数、または拡張ストアド プロシージャに関して次の結果セットが返されます。  
  
        |列名|データ型|Description|  
        |-----------------|---------------|-----------------|  
        |**Parameter_name**|**nvarchar (**128**)**|ストアド プロシージャ パラメーター名です。|  
        |**型**|**nvarchar (**128**)**|ストアド プロシージャ パラメーターのデータ型です。|  
        |**[データ型]**|**smallint**|最大物理記憶容量 (バイト数) です。|  
        |**Prec**|**int**|有効桁数または総桁数です。|  
        |**[スケール]**|**int**|小数点より右側の桁数です。|  
        |**Param_order**|**smallint**|パラメーターの順番です。|  
  
## <a name="remarks"></a>解説  
 **Sp_help**プロシージャは、現在のデータベースのみでオブジェクトを検索します。  
  
 ときに*名前*が指定されていない**sp_help**オブジェクト名、所有者、およびオブジェクトの種類、現在のデータベース内のすべてのオブジェクトを表示します。 **sp_helptrigger**トリガーに関する情報を提供します。  
  
 **sp_help**公開並べ替え可能なインデックス列だけです。 したがって、XML インデックスまたは空間インデックスに関する情報公開されません。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。 ユーザーに対する権限が必要に少なくとも 1 つ*objname*です。 列の制約キー、既定値、またはルールを表示するには、テーブルに対する VIEW DEFINITION 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-information-about-all-objects"></a>A. すべてのオブジェクトに関する情報を返す  
 次の例では、各オブジェクトに関する情報を一覧表示、`master`データベース。  
  
```  
USE master;  
GO  
EXEC sp_help;  
GO  
```  
  
### <a name="b-returning-information-about-a-single-object"></a>B. 特定のオブジェクトに関する情報を返す  
 次の例では、に関する情報を表示、`Person`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help 'Person.Person';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpindex &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)   
 [sp_helprotec &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sp_helpuser &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sysobjects および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-sysobjects-transact-sql.md)  
  
  
