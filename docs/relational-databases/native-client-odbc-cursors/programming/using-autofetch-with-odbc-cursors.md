---
title: Autofetch と ODBC カーソル |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b644ad10331acc03847c6914782e7df24a7bbb20
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67902431"
---
# <a name="using-autofetch-with-odbc-cursors"></a>autofetch と ODBC カーソルの併用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  インスタンスに接続されているときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、任意のサーバー カーソルの種類を使用する場合、autofetch オプションをサポートしています。 Autofetch では、 **SQLExecute**または**SQLExecDirect**カーソルを開く関数にも、暗黙の型は、 [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) 関数。 バインドされたアプリケーション変数に、最初の行セットを構成する行がステートメント実行の一環として返されるので、ネットワーク経由でのサーバーとのやり取りが減少します。 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)ときはサポートされていません、autofetch オプションが有効になります。 結果セットの列をプログラム変数にバインドする必要があります。  
  
 アプリケーションでは、ドライバー固有の SQL_SOPT_SS_CURSOR_OPTIONS ステートメント属性を SQL_CO_AF に設定することにより autofetch を要求します。  
  
## <a name="see-also"></a>関連項目  
 [カーソル プログラミングの詳細&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
