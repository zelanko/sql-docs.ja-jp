---
title: ドライバー |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c8b40641be3db34fc6929edecdd5dd923700957
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294185"
---
# <a name="drivers"></a>ドライバー
*ドライバーは、ODBC* API で関数を実装するライブラリです。 各々は特定の DBMS に固有のものです。たとえば、Oracle 用のドライバーは、Informix DBMS 内のデータに直接アクセスできません。 ドライバーは、基になる DBMS の機能を公開します。DBMS でサポートされていない機能を実装する必要はありません。 たとえば、基になる DBMS が外部結合をサポートしていない場合、ドライバーはどちらもサポートしないでください。 この唯一の例外は、Xbase などのスタンドアロン データベース エンジンを持たない DBMS 用のドライバーは、少なくとも最小限の SQL をサポートするデータベース エンジンを実装する必要があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ドライバーでの処理](../../odbc/reference/driver-tasks.md)  
  
-   [ドライバーのアーキテクチャ](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft 提供の ODBC ドライバー](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
