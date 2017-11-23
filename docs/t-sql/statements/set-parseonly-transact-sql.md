---
title: "[SET parseonly] (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSEONLY_TSQL
- SET_PARSEONLY_TSQL
- PARSEONLY
- SET PARSEONLY
dev_langs: TSQL
helpviewer_keywords:
- parsing [SQL Server], SET PARSEONLY statement
- checking syntax
- PARSEONLY option
- syntax [SQL Server], verifying
- verifying syntax
- SET PARSEONLY statement
ms.assetid: 514ab042-c53e-4d96-be71-fb08fcc6ef3c
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 107a70e458201f43d29b5a32885acce9a789acca
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-parseonly-transact-sql"></a>SET PARSEONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  各 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのコンパイルや実行を行わずに、ステートメントの構文をチェックし、エラーがあるときはエラー メッセージを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET PARSEONLY { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 SET PARSEONLY が ON の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではステートメントの解析だけが行われます。 SET PARSEONLY が OFF の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではステートメントがコンパイルされ実行されます。  
  
 SET PARSEONLY は、実行時ではなく解析時に設定されます。  
  
 PARSEONLY は、ストアド プロシージャやトリガーでは使わないでください。 OFFSETS オプションが ON でエラーがない場合は、SET PARSEONLY はオフセットを返します。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [セット オフセット &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-offsets-transact-sql.md)  
  
  
