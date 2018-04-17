---
title: ドライバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 96e2052feaeef1a7b752afc8f2b81babe820e08a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="drivers"></a>ドライバー
*ドライバー*ライブラリには、ODBC API の関数を実装します。 それぞれが特定の DBMS に固有たとえば、Oracle 用のドライバーは Informix DBMS のデータに直接アクセスできません。 ドライバーは、基になる Dbms 以外の機能を公開します。データベース管理システムでサポートされていない機能を実装する必要はありません。 たとえば、外部結合、し、どちらも、基になる DBMS がサポートされていない場合は、ドライバーを必要があります。 主な例外は、Xbase などのスタンドアロン データベース エンジンがない Dbms 用のドライバーが、少なくとも SQL の最小量をサポートするデータベース エンジンを実装する必要があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバーでの処理](../../odbc/reference/driver-tasks.md)  
  
-   [ドライバーのアーキテクチャ](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft 提供の ODBC ドライバー](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
