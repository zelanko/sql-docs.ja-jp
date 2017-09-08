---
title: "FILEGROUPPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILEGROUPPROPERTY_TSQL
- FILEGROUPPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], property values
- FILEGROUPPROPERTY function
- viewing filegroup properties
- displaying filegroup properties
ms.assetid: b3a930e6-df05-4034-929c-f681f5f6fc6e
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 050ec0b7c3fdc9146a25b1b1f372ee4928d80c09
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ファイル グループとプロパティ名が指定された場合に、ファイル グループ プロパティ値を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FILEGROUPPROPERTY ( filegroup_name , property )  
```  
  
## <a name="arguments"></a>引数  
 *filegroup_name*  
 型の式は、 **sysname**を名前付きプロパティの情報を返す対象のファイル グループの名前を表します。  
  
 *プロパティ*  
 型の式は、 **varchar (128)**を返すファイル グループ プロパティの名前が含まれています。 *プロパティ*これらの値のいずれかになります。  
  
|値|Description|返される値|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|ファイル グループが読み取り専用であるかどうかを示します。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
|**IsUserDefinedFG**|ファイル グループはユーザー定義のファイル グループです。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
|**IsDefault**|ファイル グループは既定のファイル グループです。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 *filegroup_name*に対応する、**名前**内の列、 **sys.filegroups**カタログ ビューです。  
  
## <a name="examples"></a>使用例  
 次の例では、`IsDefault` データベースのプライマリ ファイル グループに対する [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] プロパティの設定値を返します。  
  
```  
  
SELECT FILEGROUPPROPERTY('PRIMARY', 'IsDefault') AS 'Default Filegroup';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Default Filegroup   
---------------------   
1  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [FILEGROUP_ID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
