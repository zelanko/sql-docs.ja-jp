---
title: "@@TOTAL_ERRORS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_ERRORS'
- '@@TOTAL_ERRORS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@TOTAL_ERRORS function'
- total errors [SQL Server]
- errors [SQL Server], read/write
- number of disk read/write errors
- disks [SQL Server], errors
- write errors [SQL Server]
- read/write errors
ms.assetid: 09e62428-ee0e-4ef5-b969-da9d255f1199
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 65268d94ec7a12fd66587751ac9a93dc192be566
ms.contentlocale: ja-jp
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40totalerrors-transact-sql"></a>&#x40;&#x40;です。TOTAL_ERRORS (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動してから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で発生したディスクの書き込みエラーの数を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@TOTAL_ERRORS  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>解説  
 この関数によって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で発生したすべての書き込みエラーが返されるわけではありません。 致命的ではない書き込みエラーが発生した場合は、サーバー自身によって処理されることがあり、これはエラーとして扱われません。 いくつか含むレポートを表示する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]統計情報、エラーの合計数を含む実行**sp_monitor**です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のシステム上の日付と時刻において、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で発生したエラー数を示します。  
  
```  
SELECT @@TOTAL_ERRORS AS 'Errors', GETDATE() AS 'As of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Errors      As of                   
----------- ----------------------  
0           3/28/2003 12:32:11 PM   
```  
  
## <a name="see-also"></a>参照  
 [sp_monitor &#40;です。TRANSACT-SQL と&#41;です。](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [システム統計関数 &#40;です。TRANSACT-SQL と&#41;です。](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  

