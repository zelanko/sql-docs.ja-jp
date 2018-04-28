---
title: JDBC 4.3、JDBC ドライバーのコンプライアンス対応を |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a943388e1a1a44eb377e9eaa6268733e31c4ef9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3 JDBC Driver のコンプライアンス
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  SQL Server 用 Microsoft JDBC Driver 6.4 より前のバージョンは Java Database Connectivity API 4.2 仕様に準拠しています。 このセクションでは、6.4 リリースより前のバージョンは適用されません。  
  
 現時点では、SQL Server 用 Microsoft JDBC Driver 6.4 は Java 9 の互換性のあるが、その Java データベース接続 API 4.3 仕様を完全に準拠します。 新しく JDBC 4.3 の場合は、Api が導入されたサポートされていない場合、ドライバーによってのドライバーには、SQLFeatureNotSupportedException がスローされます。