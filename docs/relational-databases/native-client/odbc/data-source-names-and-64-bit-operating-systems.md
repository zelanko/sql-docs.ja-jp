---
title: データ ソース名と 64 ビット オペレーティング システム。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 961f4e2f5a4c08dd39a2b274ceac1b87f84e0391
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67913232"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>データ ソース名と 64 ビット オペレーティング システム
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  アプリケーションを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドして実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。  
  
## <a name="remarks"></a>コメント  
 64 ビットの Windows オペレーティング システムには、2 つの odbcad32.exe ファイルがあります。  
  
-   %SystemRoot%\system32\odbcad32.exe は、64 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe は、64 ビット オペレーティング システムで実行される 32 ビット アプリケーションなど、32 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。  
  
## <a name="see-also"></a>関連項目  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
