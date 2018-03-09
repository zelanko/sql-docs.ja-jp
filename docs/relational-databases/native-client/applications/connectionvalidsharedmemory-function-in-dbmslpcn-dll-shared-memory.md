---
title: "Dbmslpcn.dll 共有メモリで ConnectionValidSharedMemory 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 705177dd5243c0eb7619bf9fda723087e8d846d4
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Dbmslpcn.dll 共有メモリで ConnectionValidSharedMemory 関数
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  関数は、SQL Server の共有メモリがインストールされ、アクティブかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>パラメーター  
 *szServerName*  
  
-   型: **char\***  
  
-   SQL server の名前。  
  
## <a name="return-value"></a>戻り値  
 型: **BOOL**  
  
 無効です。 0 を返します。それ以外の場合は 0 以外を返します。  
  
  
