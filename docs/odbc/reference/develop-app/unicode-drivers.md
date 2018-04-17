---
title: Unicode ドライバー |Microsoft ドキュメント
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
- Unicode [ODBC], drivers
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: afa94d02f8bfabe8b8c94ac99be76b304ff8bd4f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="unicode-drivers"></a>Unicode のドライバー
ドライバーが、ANSI、Unicode ドライバーにするかどうかは、データ ソースの種類に完全に依存します。 データ ソースは、Unicode データをサポートする場合、ドライバーは、Unicode ドライバーをする必要があります。 データ ソースは、ANSI データのみをサポートする場合、ドライバーに ANSI ドライバーしておきます。  
  
 Unicode のドライバーをエクスポートする必要があります**SQLConnectW**ドライバー マネージャーによって、Unicode のドライバーとして認識されるようにします。  
  
 Unicode ドライバーには、Unicode 関数がそのまま使用する必要があります (のサフィックスを持つ*W*) し、Unicode データを格納します。 ANSI 関数も使用できますが、必須ではありません。 (ドライバー マネージャーが、ANSI 関数呼び出しを渡しません、 *A*ドライバーをドライバーが関数呼び出し、サフィックスと、パスなしの ANSI に変換するサフィックスです)。  
  
 Unicode ドライバーは、Unicode または ANSI のいずれかで、アプリケーションのバインドによって結果セットを返すできる必要があります。 アプリケーションは、SQL_C_CHAR にバインドした場合、Unicode ドライバーは SQL_WCHAR データを SQL_CHAR に変換する必要があります。 ドライバー マネージャーは、ANSI ドライバーの SQL_C_CHAR に SQL_C_WCHAR がマップされますが、Unicode のドライバーのマッピングは行われません。  
  
> [!NOTE]  
>  ドライバーの種類を決定するとき、ドライバー マネージャーが呼び出す**SQLSetConnectAttr**し、接続時に SQL_ATTR_ANSI_APP 属性を設定します。 SQL_ATTR_ANSI_APP は SQL_AA_TRUE に設定する場合は、アプリケーションは、ANSI Api を使用して、および Unicode を使用している場合 SQL_AA_FALSE の値に設定されます。 ドライバーも、アプリケーションの種類に基づく動作の違いに優れているため、この属性を使用します。 属性をアプリケーションで、直接設定することはできずではサポートされていません**SQLGetConnectAttr**です。 場合は、ドライバーは、ANSI と Unicode の両方のアプリケーションの同じ動作を示します、この属性の SQL_ERROR を返します。 ドライバーは SQL_SUCCESS を返します、ドライバー マネージャーは、接続プールが使用するときに、ANSI と Unicode の接続を分割します。
