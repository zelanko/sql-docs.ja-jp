---
title: "ドライバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b2c7299dbbb9cce2f3c97344df33acf27d89c39f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="drivers"></a>ドライバー
*ドライバー*ライブラリには、ODBC API の関数を実装します。 それぞれが特定の DBMS に固有たとえば、Oracle 用のドライバーは Informix DBMS のデータに直接アクセスできません。 ドライバーは、基になる Dbms 以外の機能を公開します。データベース管理システムでサポートされていない機能を実装する必要はありません。 たとえば、外部結合、し、どちらも、基になる DBMS がサポートされていない場合は、ドライバーを必要があります。 主な例外は、Xbase などのスタンドアロン データベース エンジンがない Dbms 用のドライバーが、少なくとも SQL の最小量をサポートするデータベース エンジンを実装する必要があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバーでの処理](../../odbc/reference/driver-tasks.md)  
  
-   [ドライバーのアーキテクチャ](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft 提供の ODBC ドライバー](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
