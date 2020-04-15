---
title: 結果セットのメタデータ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b78cdeb4c8b3522f4677c0277401cd9395a36a5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300082"
---
# <a name="result-set-metadata"></a>結果セットのメタデータ
*メタデータ*は、他のデータを記述するデータです。 たとえば、結果セットのメタデータは、結果セット内の列数、列のデータ型、名前、精度、NULL 許容など、結果セットを記述します。  
  
 相互運用可能なアプリケーションでは、常に結果セット列のメタデータをチェックする必要があります。 結果セット内の列のメタデータは、カタログ関数によって返される列のメタデータと異なる場合があります。 たとえば、更新可能な列が、2 つのテーブルを結合して作成された結果セットに含まれているとします。 **SQLColumnPrivileges は**、ユーザーが列を更新できることを示す場合がありますが、列が結合の 「多い」側にある場合、結果セットのメタデータは更新されない場合があります。多くのデータ ソースは、結合の "一" 側の列を更新できますが、"多" 側では更新できません。 データ ソースは結果セットの作成中にデータ型を昇格させる可能性があるため、データ型も同じと見なすことはできません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [メタデータの使用方法](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol および SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
