---
title: Dbmslpcn.dll 共有メモリの ConnectionValidSharedMemory 関数 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9eb72ca108c6f4d01626d75f5dc3ad8e8354fad1
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39537092"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>dbmslpcn.dll 共有メモリの ConnectionValidSharedMemory 関数
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  関数は、SQL Server の共有メモリがインストールされ、アクティブであるかどうかを判断します。  
  
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
  
 無効です。 0 を返します。それ以外の場合、0 以外の値を返します。  
  
  
