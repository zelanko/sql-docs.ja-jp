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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2248077b8efed3ebf11f871603a6513d6b9f4a02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612570"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>データ ソース名と 64 ビット オペレーティング システム
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  アプリケーションを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドして実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。  
  
## <a name="remarks"></a>コメント  
 64 ビットの Windows オペレーティング システムには、2 つの odbcad32.exe ファイルがあります。  
  
-   %SystemRoot%\system32\odbcad32.exe は、64 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe は、64 ビット オペレーティング システムで実行される 32 ビット アプリケーションなど、32 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
