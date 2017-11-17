---
title: "@@LANGID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@LANGID'
- '@@LANGID_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- languages [SQL Server], current in use
- '@@LANGID function'
- current language in use
- ID for language in use
- local language IDs [SQL Server]
ms.assetid: 7a0fc089-2a48-4a81-9d78-2aaedb540d37
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 39d66c56a3cb0b21d8955dfe56dc5083472ec372
ms.contentlocale: ja-jp
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40langid-transact-sql"></a>& #x 40; & #x 40 です。LANGID (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在使用している言語のローカル言語識別子 (ID) を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@LANGID  
```  
  
## <a name="return-types"></a>戻り値の型  
 **smallint**  
  
## <a name="remarks"></a>解説  
 言語 ID 番号を含めて、言語設定に関する情報を表示するには実行**sp_helplanguage**パラメーターを指定します。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のセッションの言語を設定`Italian`、しを使用して`@@LANGID`してイタリア語の ID を返します。  
  
```  
SET LANGUAGE 'Italian'  
SELECT @@LANGID AS 'Language ID'  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Changed language setting to Italiano.  
Language ID  
-----------  
6            
```  
  
## <a name="see-also"></a>参照  
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [言語を設定する & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-language-transact-sql.md)   
 [sp_helplanguage & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)  
  
  

