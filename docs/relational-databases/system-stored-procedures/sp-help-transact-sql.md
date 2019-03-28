---
title: sp_help (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help
- sp_help_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help
ms.assetid: 913cd5d4-39a3-4a4b-a926-75ed32878884
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f5e514307e1427cea0ea1bb4d75e7bf0806fd516
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537114"
---
# <a name="sphelp-transact-sql"></a>sp_help (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース オブジェクトに関する情報をレポート (で表示されている任意のオブジェクト、 **sys.sysobjects**互換性ビュー)、ユーザー定義データ型、またはデータ型。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help [ [ @objname = ] 'name' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @objname = ] 'name'` 任意のオブジェクトの名前は、 **sysobjects**に任意のユーザー定義データ型、または、 **systypes**テーブル。 *名前*は**nvarchar (** 776 **)**、既定値は NULL です。 データベース名は受け付けられません。  'Person.AddressType' や [Person.AddressType] など、2 つまたは 3 つの部分名を区切る必要があります。   
   
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 返される結果セットが異なるかどうか*名前*を指定した場合とはどのデータベース オブジェクトを指定します。  
  
1.  場合**sp_help**が実行される、引数なしで、現在のデータベース内に存在するすべての型のオブジェクトの概要情報が返されます。  
  
    |列名|データ型|説明|  
    |-----------------|---------------|-----------------|  
    |**名前**|**nvarchar(** 128 **)**|オブジェクト名です。|  
    |**[所有者]**|**nvarchar(** 128 **)**|オブジェクトの所有者 (これはオブジェクトを所有するデータベース プリンシパルです。 既定値、オブジェクトを含むスキーマの所有者です。)|  
    |**Object_type**|**nvarchar(** 31 **)**|オブジェクトの種類|  
  
2.  場合*名前*は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型またはユーザー定義データ型、 **sp_help**この結果セットを返します。  
  
    |列名|データ型|説明|  
    |-----------------|---------------|-----------------|  
    |**Type_name**|**nvarchar(** 128 **)**|データ型の名前。|  
    |**Storage_type**|**nvarchar(** 128 **)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型名。|  
    |**Length**|**smallint**|(バイト単位) でのデータ型の物理的な長さ。|  
    |**prec**|**int**|有効桁数 (総桁数) です。|  
    |**Scale**|**int**|小数点の右側にある数字の数。|  
    |**NULL 値の使用**|**varchar(** 35 **)**|NULL 値を許容するかどうかを示します。はいまたはいいえです。|  
    |**Default_name**|**nvarchar(** 128 **)**|このデータ型にバインドされた既定値の名前です。<br /><br /> NULL = No デフォルトをバインドします。|  
    |**規則の名前**|**nvarchar(** 128 **)**|このデータ型にバインドされたルールの名前です。<br /><br /> NULL = No デフォルトをバインドします。|  
    |**[照合順序]**|**sysname**|データ型の照合順序。 NULL 以外の文字データ型を表します。|  
  
3.  場合*名前*以外のデータ型では、任意のデータベース オブジェクトは、 **sp_help**この結果に指定したオブジェクトの種類に基づいて、設定済みでも追加の結果セットを返します。  
  
    |列名|データ型|説明|  
    |-----------------|---------------|-----------------|  
    |**名前**|**nvarchar(** 128 **)**|テーブル名|  
    |**[所有者]**|**nvarchar(** 128 **)**|テーブルの所有者|  
    |**型**|**nvarchar(** 31 **)**|テーブルの種類です。|  
    |**Created_datetime**|**datetime**|テーブルの作成日|  
  
     指定すると、データベース オブジェクトによって**sp_help**追加の結果セットが返されます。  
  
     場合*名前*がシステム テーブル、ユーザー テーブルまたはビュー、 **sp_help**次の結果セットが返されます。 ただし、ビューに対しては、データ ファイルがファイル グループ内のどこに配置されているかを表す結果セットは返されません。  
  
    -   列オブジェクトに関して次の結果セットが返されます。  
  
        |列名|データ型|説明|  
        |-----------------|---------------|-----------------|  
        |**Column_name**|**nvarchar(** 128 **)**|列の名前。|  
        |**型**|**nvarchar(** 128 **)**|列のデータを入力します。|  
        |**計算**|**varchar(** 35 **)**|列内の値が計算されているかどうかを示します。はいまたはいいえです。|  
        |**Length**|**int**|列の長さ (バイト単位)。<br /><br /> 注:列のデータ型が大きな値の型 (**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**)、値は-1 として表示されます。|  
        |**prec**|**char(** 5 **)**|列の有効桁数。|  
        |**Scale**|**char(** 5 **)**|列の小数点以下桁数です。|  
        |**NULL 値の使用**|**varchar(** 35 **)**|列で NULL 値を許容するかどうかを示します。はいまたはいいえです。|  
        |**TrimTrailingBlanks**|**varchar(** 35 **)**|末尾の空白をトリミングします。 はいまたは no を返します。|  
        |**FixedLenNullInSource**|**varchar(** 35 **)**|これは旧バージョンとの互換性のためにだけ用意されています。|  
        |**[照合順序]**|**sysname**|列の照合順序です。 非文字データ型の場合は NULL です。|  
  
    -   Id 列の追加の結果セットが返されます。  
  
        |列名|データ型|説明|  
        |-----------------|---------------|-----------------|  
        |**[ID]**|**nvarchar(** 128 **)**|データ型が id として宣言されている列の名前。|  
        |**シード**|**numeric**|Id 列の値を開始しています。|  
        |**Increment**|**numeric**|この列の値を使用する増分値です。|  
        |**[レプリケーションでは使用しない]**|**int**|IDENTITY プロパティは、レプリケーションのログイン時に適用されませんなど**sqlrepl**テーブルにデータを挿入します。<br /><br /> 1 = True<br /><br /> 0 = False|  
  
    -   列の追加の結果セットが返されます。  
  
        |列名|データ型|説明|  
        |-----------------|---------------|-----------------|  
        |**RowGuidCol**|**sysname**|一意なグローバル識別子列の名前です。|  
  
    -   ファイル グループに追加の結果セットが返されます。  
  
        |列名|データ型|説明|  
        |-----------------|---------------|-----------------|  
        |**Data_located_on_filegroup**|**nvarchar(** 128 **)**|データが配置されているファイル グループ:プライマリ、セカンダリ、またはトランザクション ログ|  
  
    -   インデックスの追加の結果セットが返されます。  
  
        |列名|データ型|説明|  
        |-----------------|---------------|-----------------|  
        |**index_name**|**sysname**|インデックスの名前。|  
        |**Index_description**|**varchar(** 210 **)**|インデックスの説明です。|  
        |**index_keys**|**nvarchar(** 2078 **)**|インデックスが作成されている列の名前。 XVelocity メモリ、NULL を返しますには、列ストア インデックスが最適化されています。|  
  
    -   制約に関して次の結果セットが返されます。  
  
        |列名|データ型|説明|  
        |-----------------|---------------|-----------------|  
        |**constraint_type**|**nvarchar(** 146 **)**|制約の型。|  
        |**constraint_name**|**nvarchar(** 128 **)**|制約の名前。|  
        |**delete_action**|**nvarchar(** 9 **)**|削除操作があるかを示します。NO_ACTION、CASCADE、SET_、SET_DEFAULT、または該当なし。<br /><br /> ただし、FOREIGN KEY 制約にだけ適用されます。|  
        |**update_action**|**nvarchar(** 9 **)**|UPDATE 操作が次のいずれかであることを示します。NO_ACTION、CASCADE、SET_、SET_DEFAULT、または該当なし。<br /><br /> ただし、FOREIGN KEY 制約にだけ適用されます。|  
        |**status_enabled**|**varchar(** 8 **)**|制約が有効かどうかを示します。有効、無効、または該当なし。<br /><br /> CHECK および FOREIGN KEY 制約にのみ適用されます。|  
        |**status_for_replication**|**varchar(** 19 **)**|制約がレプリケーションを対象とするのかどうかを示します。<br /><br /> CHECK および FOREIGN KEY 制約にのみ適用されます。|  
        |**constraint_keys**|**nvarchar(** 2078 **)**|制約を構成する列の名前です。デフォルトおよびルールの場合は、デフォルトまたはルールを定義するテキストです。|  
  
    -   参照先のオブジェクトに追加の結果セットが返されます。  
  
        |列名|データ型|説明|  
        |-----------------|---------------|-----------------|  
        |**によって参照されるテーブル**|**nvarchar(** 516 **)**|テーブルを参照する他のデータベース オブジェクトを識別します。|  
  
    -   ストアド プロシージャ、関数、または拡張ストアド プロシージャに関して次の結果セットが返されます。  
  
        |列名|データ型|説明|  
        |-----------------|---------------|-----------------|  
        |**Parameter_name**|**nvarchar(** 128 **)**|ストアド プロシージャ パラメーターの名前。|  
        |**型**|**nvarchar(** 128 **)**|ストアド プロシージャのパラメーターのデータ型。|  
        |**Length**|**smallint**|最大物理記憶域の長さ (バイト単位)。|  
        |**prec**|**int**|桁数または有効桁数の合計数。|  
        |**Scale**|**int**|小数点の右側にある数字の数。|  
        |**Param_order**|**smallint**|パラメーターの順番です。|  
  
## <a name="remarks"></a>コメント  
 **Sp_help**プロシージャは、現在のデータベースのみでオブジェクトを検索します。  
  
 ときに*名前*が指定されていない**sp_help**名、所有者、および現在のデータベース内のすべてのオブジェクトのオブジェクトの種類のオブジェクトを表示します。 **sp_helptrigger**トリガーに関する情報を提供します。  
  
 **sp_help**は順序付け可能なインデックス列だけを公開します。 したがって、これは公開されません XML インデックスまたは空間インデックスに関する情報。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。 ユーザーに対する権限が必要に少なくとも 1 つ*objname*します。 列の制約キー、既定値、またはルールを表示するには、テーブルに対する VIEW DEFINITION 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-information-about-all-objects"></a>A. すべてのオブジェクトに関する情報を返す  
 次の例では、各オブジェクトに関する情報を一覧表示、`master`データベース。  
  
```  
USE master;  
GO  
EXEC sp_help;  
GO  
```  
  
### <a name="b-returning-information-about-a-single-object"></a>B. 1 つのオブジェクトに関する情報を返す  
 次の例では、に関する情報を表示、`Person`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help 'Person.Person';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpindex &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)   
 [sp_helprotect &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sp_helpuser &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sysobjects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysobjects-transact-sql.md)  
  
  
