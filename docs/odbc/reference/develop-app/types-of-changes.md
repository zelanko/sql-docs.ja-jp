---
title: "変更の種類 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a494595625d264159fbb39db03818d50ed97876
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="types-of-changes"></a>変更の種類
ODBC 3 では、3 種類の変更が行われます。*x* (および ODBC の任意のバージョン)。 これらの各は異なる方法で旧バージョンとの互換性に影響され、別の方法で処理されます。 これらの変更は、次の表で説明します。  
  
|変更の種類|Description|  
|--------------------|-----------------|  
|新しい機能|これらは、ODBC 3 に新しく追加された機能です。*x*行外のバインディングまたは記述子などです。 アプリケーションおよびドライバーだけでなく、ドライバー マネージャーがバージョン 3 の場合にのみ実装されて*.x*なので、これらの下位互換性を試みたはありません。|  
|重複する機能|これらは、ODBC 2 内に存在する機能*.x*と ODBC 3 *。x*それぞれに異なる方法で実装されます。 関数は、 **SQLAllocHandle**と**SQLAllocStmt**例があります。 これらの旧バージョンと互換性の問題し、その他の重複する機能は、ドライバー マネージャーのマッピングによって処理されるほとんどの場合。|  
|動作の変更|これらは、ODBC 2 では異なる方法で処理される機能*.x*と ODBC 3 *。x*です。 Datetime **#define**例に示します。 これらの機能は、ODBC 3 によって処理されます。*x*環境属性の設定に基づいてドライバー。 (を参照してください[動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)詳細についてはします)。|

