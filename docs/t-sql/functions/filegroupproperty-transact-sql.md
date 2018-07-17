---
title: FILEGROUPPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: afc112a5e07197ed8b0056a7daeddb55c0c418c9
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790152"
---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ファイル グループとプロパティ名が指定された場合に、ファイル グループ プロパティ値を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FILEGROUPPROPERTY ( filegroup_name , property )  
```  
  
## <a name="arguments"></a>引数  
 *filegroup_name*  
 指定されたプロパティ情報を返すファイル グループの名前を表す **sysname** データ型の式を指定します。  
  
 *property*  
 返される filegroup プロパティの名前を含む **varchar(128)** 型の式を指定します。 *プロパティ* これらの値のいずれかを指定することができます。  
  
|ReplTest1|[説明]|返される値|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|ファイル グループが読み取り専用であるかどうかを示します。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
|**IsUserDefinedFG**|ファイル グループはユーザー定義のファイル グループです。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
|**IsDefault**|ファイル グループは既定のファイル グループです。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 *filegroup_name* に対応する、 **名前** 内の列、 **sys.filegroups** カタログ ビューです。  
  
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
 [FILEGROUP_ID (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [メタデータ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
