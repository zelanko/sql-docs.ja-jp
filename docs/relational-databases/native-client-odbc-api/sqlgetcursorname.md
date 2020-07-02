---
title: Sqlgetカーソル名 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4f91ebce4c21f5b53a467a65e3b1728161ef8996
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789200"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  アプリケーションでカーソル名が指定されていない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーによって、カーソルの生成時にアプリケーション用に1つが生成されます。 アプリケーションでは、 **Sqlgetcursor name**を使用して、位置指定の UPDATE および DELETE ステートメントのドライバーで定義されたカーソル名を取得できます。 アプリケーションでは、位置指定データ操作ステートメントを利用するために**SQLSetCursorName**を呼び出す必要はありません。  
  
## <a name="see-also"></a>関連項目  
 [Sqlgetカーソル名関数](https://go.microsoft.com/fwlink/?LinkId=59349)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
