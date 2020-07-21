---
title: VERSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
author: julieMSFT
ms.author: jrasnick
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 360ac0905f452bedd5eeaf4691ccbbf3baedb89e
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196996"
---
# <a name="version---transact-sql-metadata-functions"></a>Version - Transact SQL メタデータ関数
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

 アプライアンスで実行されている [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] または [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] のバージョンを返します。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>引数  
  
## <a name="general-remarks"></a>全般的な解説  
結果を返すには、テーブル名をこの関数の [FROM](../../t-sql/queries/from-transact-sql.md) 句で指定する必要があります。 クエリの結果セットの各行の結果の行が返されます。[TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) を使用して、返された行の数を制限します。  
  
## <a name="examples"></a>例  
次の例では、バージョン番号を返します。  
  
```  
SELECT VERSION();  
```  
  
## <a name="see-also"></a>参照 
[SESSION_ID &#40;Transact-SQL&#41;](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
