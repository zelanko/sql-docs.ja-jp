---
title: 変更の種類 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac92c6d40ea9ead6b8875e3338bb740b4bdf8523
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473177"
---
# <a name="types-of-changes"></a>変更の種類
次の 3 つの種類の変更は、ODBC 3 で行われます。*x* (および ODBC の任意のバージョン)。 これらの異なる方法で旧バージョンとの互換性に影響し、さまざまな方法で処理されます。 これらの変更は、次の表で説明します。  
  
|変更の種類|説明|  
|--------------------|-----------------|  
|新しい機能|これらは、ODBC 3 に新しく追加された機能です。*x*、アウトオブ ライン バインドまたは記述子など。 アプリケーションおよびドライバーだけでなく、ドライバー マネージャーがバージョン 3 の場合にのみ、これらは実装 *.x*ので、しようとしてこれらの旧バージョンと互換性があることはありません。|  
|重複する機能|これらは、ODBC 2 内に存在する機能 *.x*および ODBC 3 *。x*がそれぞれ異なる方法で実装されます。 関数は、 **SQLAllocHandle**と**SQLAllocStmt**例があります。 これらの旧バージョンとの互換性の問題し、重複しているその他の機能は、ドライバー マネージャーのマッピングによって処理されるほとんどの場合。|  
|動作の変更|これらは、ODBC 2 に異なる方法で処理される機能 *.x*および ODBC 3 *。x*します。 Datetime **#define**例を示します。 これらの機能は、ODBC 3 によって処理されます。*x*環境属性の設定に基づいて、ドライバー。 (を参照してください[動作が変更される](../../../odbc/reference/develop-app/behavioral-changes.md)詳細についてはします)。|
