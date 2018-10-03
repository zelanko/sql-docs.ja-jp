---
title: ドライバー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e3996aafa0e4f5b389e4f46d5df3b22632daad9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47710040"
---
# <a name="drivers"></a>ドライバー
*ドライバー*ライブラリには、ODBC api 関数を実装します。 それぞれが特定の DBMS に固有たとえば、Oracle 用のドライバーは、Informix の DBMS のデータに直接アクセスできません。 ドライバーは、基になる Dbms 以外の機能を公開します。DBMS でサポートされていない機能を実装する必要はありません。 たとえば、外部結合し、どちらも、基になる DBMS がサポートされていない場合は、ドライバーを必要があります。 唯一のメジャーの例外は、Xbase などのスタンドアロン データベース エンジンがない Dbms 用のドライバーが少なくとも最小限の SQL をサポートするデータベース エンジンを実装する必要があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバーでの処理](../../odbc/reference/driver-tasks.md)  
  
-   [ドライバーのアーキテクチャ](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft 提供の ODBC ドライバー](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
