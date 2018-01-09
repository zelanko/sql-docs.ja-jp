---
title: "データ ソースの名前と 64 ビット オペレーティング システム |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 762b02eccdbf10d984c36f3eaf4eb4ce8e602be1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>データ ソース名と 64 ビット オペレーティング システム
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  アプリケーションを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドして実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。  
  
## <a name="remarks"></a>解説  
 64 ビットの Windows オペレーティング システムには、2 つの odbcad32.exe ファイルがあります。  
  
-   %SystemRoot%\system32\odbcad32.exe は、64 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe は、64 ビット オペレーティング システムで実行される 32 ビット アプリケーションなど、32 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
