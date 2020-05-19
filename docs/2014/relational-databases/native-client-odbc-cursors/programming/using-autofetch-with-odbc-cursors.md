---
title: ODBC カーソルで Autofetch を使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a15cc12787f5a7d05699737772e7478d57b6f6e8
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705597"
---
# <a name="using-autofetch-with-odbc-cursors"></a>autofetch と ODBC カーソルの併用
  のインスタンスに接続している場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーでは、任意のサーバーカーソルの種類を使用するときに autofetch オプションがサポートされます。 Autofetch では、カーソルを開く**Sqlexecute**または**SQLExecDirect**関数にも、暗黙的な[sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) 関数があります。 バインドされたアプリケーション変数に、最初の行セットを構成する行がステートメント実行の一環として返されるので、ネットワーク経由でのサーバーとのやり取りが減少します。 Autofetch オプションが有効になっている場合、 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)はサポートされません。結果セットの列をプログラム変数にバインドする必要があります。  
  
 アプリケーションでは、ドライバー固有の SQL_SOPT_SS_CURSOR_OPTIONS ステートメント属性を SQL_CO_AF に設定することにより autofetch を要求します。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;のカーソルプログラミングの詳細](cursor-programming-details-odbc.md)  
  
  
