---
title: Drivers |Microsoft Docs
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
ms.openlocfilehash: 6460410488186c94713d859bf2912f2844ca2736
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915431"
---
# <a name="drivers"></a>ドライバー
*ドライバー*は、ODBC API の関数を実装するライブラリです。 各は特定の DBMS に固有です。たとえば、Oracle のドライバーは、Informix DBMS のデータに直接アクセスすることはできません。 ドライバーは、基になる Dbms の機能を公開します。DBMS でサポートされていない機能を実装する必要はありません。 たとえば、基になる DBMS が外部結合をサポートしていない場合、どちらの場合もドライバーは必要ありません。 唯一の重要な例外は、Xbase などのスタンドアロンデータベースエンジンを搭載していない Dbms のドライバーは、少なくとも最小量の SQL をサポートするデータベースエンジンを実装する必要があることです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバーでの処理](../../odbc/reference/driver-tasks.md)  
  
-   [ドライバーのアーキテクチャ](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft 提供の ODBC ドライバー](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
