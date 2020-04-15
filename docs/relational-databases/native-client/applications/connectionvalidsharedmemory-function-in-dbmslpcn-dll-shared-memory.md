---
title: を指定します。
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f3bb097965563afb458b4529676d1e9967e4899
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303890"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>dbmslpcn.dll 共有メモリの ConnectionValidSharedMemory 関数
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  この関数は、SQL Server 共有メモリがインストールされ、アクティブになっているかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>パラメーター  
 *サーバー名*  
  
-   タイプ: **\*文字**  
  
-   SQL サーバーの名前。  
  
## <a name="return-value"></a>戻り値  
 タイプ:**ブール**  
  
 無効な場合は 0 を返します。else はゼロ以外を返します。  
  
  
