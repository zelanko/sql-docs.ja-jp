---
title: ODBC カーソルと autofetch オプションを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8012ca4635d10c9f120258754099df1435ffc187
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-autofetch-with-odbc-cursors"></a>autofetch と ODBC カーソルの併用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  インスタンスに接続しているときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、どの種類のサーバー カーソルを使用する場合、autofetch オプションをサポートしています。 Autofetch で、 **SQLExecute**または**SQLExecDirect** 、カーソルをオープンする関数も暗黙的な[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) 関数です。 バインドされたアプリケーション変数に、最初の行セットを構成する行がステートメント実行の一環として返されるので、ネットワーク経由でのサーバーとのやり取りが減少します。 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)ときはサポートされていません、autofetch オプションが有効です。 結果セットの列をプログラム変数にバインドする必要があります。  
  
 アプリケーションでは、ドライバー固有の SQL_SOPT_SS_CURSOR_OPTIONS ステートメント属性を SQL_CO_AF に設定することにより autofetch を要求します。  
  
## <a name="see-also"></a>参照  
 [カーソル プログラミングの詳細&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
